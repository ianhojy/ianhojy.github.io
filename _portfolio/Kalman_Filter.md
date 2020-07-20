---
title: "Kalman Filter (Dynamic Regression) - Algo Trading"
excerpt: "Calculating optimal hedge for long-short mean-reversion strategy<br/><img src='/images/stock-market.jpg'>"
collection: portfolio
---

<i> Reference: Algorithmic Trading by Ernest P. Chan</i>

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import warnings
warnings.filterwarnings('ignore')
```

One noteworthy benefit of using the Kalman filter
to find $β$ is that not only do we obtain a dynamic hedge ratio between the two
assets, we also simultaneously obtain what we used to call “the moving average”
of the spread. This is because, as we mentioned, $β$ includes both the slope and
the intercept between $y$ and $x$. The best current estimate of the intercept is used
in place of the moving average of the spread. As a by-product, it also generates an estimate of the standard deviation of the forecast error of the observable variable, which we can use in place of the moving standard deviation of a Bollinger band.

### Reading Data


```python
cl = pd.read_csv('inputData_ETF.csv', header=None)
```


```python
x = cl[10].to_numpy()
y = cl[11].to_numpy()
```

### Plotting Cointegrated series


```python
plt.plot(x, label='EWA')
plt.plot(y, label='EWC')
plt.legend()
plt.show()
```


![png](/images/output_7_0.png)


### Allowing for dynamic offset
Constant term for the 'hidden' state

```python
x = np.append(np.expand_dims(x, axis=1), np.expand_dims(np.ones(len(x)), axis=1), axis=1)
```

### Modelling

What about $V_w$ and $V_e$? There is a method to estimate these variances from data called autocovariance least squares developed by Rajamani and Rawlings (2007, 2009).

But for simplicity,
we will follow Montana and assume $ω =
(δ/1−δ) * I$ where $δ$ is a parameter
between 0 and 1, and $I$ is a 2 × 2 identity matrix.

If $δ = 0$, this means $β(t) =
β(t − 1)$, which reduces the Kalman filter to ordinary least square regression
with a fi xed offset and slope. If $δ = 1$, this means the estimated $β$ will fluctuate
wildly based on the latest observation. The optimal $δ$, just like the optimal
lookback in a moving linear regression, can be obtained using training data.
With the benefi t of hindsight, we pick $δ = 0.0001$. With the same hindsight,
we also pick $V_e = 0.001$.

#### Initialization


```python
delta = 0.0001

yhat = np.full_like(y, np.nan, dtype=np.double)
e = np.full_like(y, np.nan, dtype=np.double)
Q = np.full_like(y, np.nan, dtype=np.double)

R = np.zeros((2,2))
P = np.zeros((2,2)) # R(t|t) = P(t)

beta = np.empty((len(x), 2))
beta[:] = np.nan

Vw = delta/(1-delta) * np.identity(2)
Ve = 0.001

beta[0] = 0.0
```

#### Iteration


```python
for t in range(len(y)):
    
    if t > 0:
        
        '''State Prediction'''
        beta[t] = beta[t-1]
        
        '''State Covariance Prediction'''
        R = P + Vw
    
    '''Measurement Prediction'''
    yhat[t] = x[t].dot(beta[t])
    
    '''Measurement Variance Prediction'''
    Q[t] = x[t] @ R @ x[t].transpose() + Ve
    
    '''Forecast Error'''
    e[t] = y[t] - yhat[t]
    
    '''Kalman Gain'''
    K = (R @ x[t].transpose()) / Q[t]
    
    '''State Update'''
    beta[t] += K * e[t]
    
    '''State Covariance Update'''
    P = R - (np.expand_dims(K, 1) @ np.expand_dims(x[t], 0) @ R)
    
```

#### Visualizations


```python
plt.plot(beta[1:, 0])
plt.title('SLOPE')
plt.show()
```


![png](/images/output_18_0.png)



```python
plt.plot(beta[:, 1])
plt.title('INTERCEPT')
plt.show()
```


![png](/images/output_19_0.png)



```python
plt.plot(e[2:], 'r', linewidth=0.2, label='e(t)')
plt.plot(np.sqrt(Q[2:]), 'b', label='sqrt(Q(t))')
plt.title('PREDICTION ERROR & STANDARD DEVIATION OF ERROR')
plt.legend()
plt.show()
```


![png](/images/output_20_0.png)


### Strategy Construction


```python
y2 = np.concatenate((np.expand_dims(x[:, 0], 1), np.expand_dims(y, 1)), axis=1)
```

The measurement prediction error $e(t)$ (previously called the forecast error for $y(t)$ given observation at t − 1) is none other than the deviation of the spread $EWC-EWA$ from its predicted mean value, and we will buy this spread when the deviation is very negative, and vice versa if it is very positive.


```python
longsEntry = e < -np.sqrt(Q) # a long position means we should buy EWC
longsExit = e > -np.sqrt(Q)
shortsEntry = e > np.sqrt(Q)
shortsExit = e < np.sqrt(Q)
```


```python
numUnitsLong = np.full_like(y, np.nan, dtype=np.double)
numUnitsShort = np.full_like(y, np.nan, dtype=np.double)
```


```python
numUnitsLong[0] = 0
numUnitsLong[longsEntry] = 1
numUnitsLong[longsExit] = 0

numUnitsShort[0] = 0
numUnitsShort[shortsEntry] = -1
numUnitsShort[shortsExit] = 0
```


```python
numUnits = numUnitsLong + numUnitsShort
```

#### Shares Allocation:
```
np.concatenate((-np.expand_dims(beta[:, 0], axis=1), 
                np.expand_dims(np.ones(len(beta)), axis=1))
```

#### Dollar Capital Allocation:
```
np.concatenate((-np.expand_dims(beta[:, 0], axis=1), 
                np.expand_dims(np.ones(len(beta)), axis=1))
                
                *
                
                y2
                
```

#### Dollar Capital in each ETF:
```
np.repeat(numUnits[:, np.newaxis], y2.shape[1], axis=1)

                *
                
np.concatenate((-np.expand_dims(beta[:, 0], axis=1), 
                np.expand_dims(np.ones(len(beta)), axis=1))
                
                *
                
                y2
                
```


```python
positions = np.multiply(np.multiply(np.repeat(numUnits[:, np.newaxis], y2.shape[1], axis=1), 
                                    np.concatenate((-np.expand_dims(beta[:, 0], axis=1), 
                                                     np.expand_dims(np.ones(len(beta)), axis=1)), axis=1)),
                        y2)
```

#### Daily P&L of Strategy


```python
pnl = np.sum(np.multiply(pd.DataFrame(positions).shift(1).fillna(0).to_numpy(),
                         pd.DataFrame(y2).pct_change().fillna(0).to_numpy()),
             axis=1)
```

`ret` is P&L divided by gross market value of portfolio


```python
ret = np.divide(pnl, 
                np.sum(abs(pd.DataFrame(positions).shift(1)).to_numpy(), axis=1))
```


```python
ret = np.nan_to_num(ret, nan=0)
```


```python
plt.plot(np.cumprod(ret+1)-1)
plt.title('CUMULATIVE COMPOUNDED RETURN')
plt.show()
print(f"APR = {round(np.prod(ret+1)**(252/len(ret))-1,3)}")
print(f"Sharpe = {round(np.sqrt(252) * np.mean(ret) / np.std(ret),3)}")
```


![png](/images/output_35_0.png)


    APR = 0.262
    Sharpe = 2.362

