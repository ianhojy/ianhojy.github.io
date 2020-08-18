---
title: "Product Detection using Convolutional Neural Networks & Transfer Learning"
excerpt: "Multi-Class Image Classification"
collection: portfolio
---

# Product Detection using CNN & Transfer Learning
-----

## Overview

This notebook will be looking at Transfer Learning architectures in the context of product detection for e-commerce sites. I will be exploring a variety of pre-trained architecures, and experimenting with variants of the model including model augmentation, model fine-tuning, as well as the effects of varying the extent of weight retraining.

In the models below, you will find the following key **variations**:
- ```Augmentation```:
    - This indicates that the model utilizes image augmentation using ```ImageDataGenerator``` to rotate, flip , resize images for more robust out-of-sample performance / regularization
- ```Fine Tune```:
    - This indicates that the model unfreezes specific layer blocks for retraining 
- ```Revamp```
    - This indicates that the model unfreezes all layers for retraining while retaining the pre-trained architecture
    
### Results

- In the final section, I present the product detection based on a test set with no labels. The results can be seen in the ```test_results``` folder, which contains aggregate images according to the model's predicted class. On a whole, the model seems to perform relatively well for a simple training purposes. As expected, classification for some classes perform significantly better than for other classes.

## Dependencies


```python
import os
import numpy as np
import random
import matplotlib.pyplot as plt
import pandas as pd

from sklearn.preprocessing import LabelEncoder
from sklearn.preprocessing import OneHotEncoder

from keras.models import Model
from keras.models import Sequential
from keras.models import save_model
from keras.models import load_model
from keras import optimizers
from keras.optimizers import RMSprop
from keras.optimizers import Adam
from keras.preprocessing.image import ImageDataGenerator
from keras.preprocessing.image import load_img
from keras.preprocessing.image import img_to_array
from keras.preprocessing.image import array_to_img
from keras.layers import InputLayer
from keras.layers import Conv2D
from keras.layers import MaxPooling2D
from keras.layers import Flatten
from keras.layers import Dense
from keras.layers import Dropout
from keras.layers import GlobalAveragePooling2D

from utils import update_progress
```

## 0. Data Processing

#### 0.1 Importing Data


```python
IMG_DIM = (150, 150)
```


```python
train_labels = list()
train_imgs = list()

bad_imgs = list()

train_root = 'data/train/train/'

ii = 0
finish = 42


for cat in os.listdir(train_root):
    
    if cat != '.DS_Store':
        
        for jpg in os.listdir(train_root + cat):

            path = train_root + cat + '/' + jpg

            try:

                train_imgs.append(img_to_array(load_img(
                        path, target_size=IMG_DIM)))       
                train_labels.append(str(int(cat)))

            except:

                bad_imgs.append(path)
    
    ii += 1
    update_progress(ii/finish)

```

#### 0.2 Scaling Data


```python
train_imgs = np.array(train_imgs)
train_imgs_scaled = train_imgs.astype('float32')
train_imgs_scaled /= 255
```

#### 0.3 One-Hot Encode Labels


```python
train_labels = [int(i) for i in train_labels]

enc = OneHotEncoder()
enc.fit(np.array(train_labels).reshape(-1, 1))

train_labels_enc = \
    enc.transform(np.array(train_labels).reshape(-1, 1)).toarray()
```

#### 0.4 Train-Val split


```python
val_prop = 0.1
```


```python
val_index = random.sample(range(1, len(train_imgs_scaled)), round(val_prop * len(train_imgs_scaled)))
train_index = [ii for ii in range(len(train_imgs_scaled)) if ii not in val_index]
random.shuffle(train_index)
```


```python
val_imgs_scaled = train_imgs_scaled[val_index]
train_imgs_scaled = train_imgs_scaled[train_index]
val_labels_enc = train_labels_enc[val_index] 
train_labels_enc = train_labels_enc[train_index]

print(val_imgs_scaled.shape)
print(train_imgs_scaled.shape)
print(val_labels_enc.shape)
print(train_labels_enc.shape)
```

#### 0.5 Saving Tensors


```python
np.save('model_data/train_imgs_scaled.npy', train_imgs_scaled)
np.save('model_data/val_imgs_scaled.npy', val_imgs_scaled)
np.save('model_data/train_labels_enc.npy', train_labels_enc)
np.save('model_data/val_labels_enc.npy', val_labels_enc)
```

#### 0.6 Loading saved Tensors (can avoid 1.1-1.5)


```python
val_imgs_scaled = np.load('model_data/val_imgs_scaled.npy')
train_imgs_scaled = np.load('model_data/train_imgs_scaled.npy')
val_labels_enc = np.load('model_data/val_labels_enc.npy')
train_labels_enc = np.load('model_data/train_labels_enc.npy')

print(val_imgs_scaled.shape)
print(train_imgs_scaled.shape)
print(val_labels_enc.shape)
print(train_labels_enc.shape)
```

## 1. Traditional CNN

### 1.1 CNN Model 1


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
model = Sequential()

model.add(Conv2D(64, kernel_size=(3, 3), activation='relu', 
                 input_shape=input_shape))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(32, kernel_size=(3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Flatten())
model.add(Dense(256, activation='relu'))
model.add(Dropout(0.3))
model.add(Dense(128, activation='relu'))
model.add(Dropout(0.3))
model.add(Dense(42, activation='sigmoid'))


model.compile(loss='categorical_crossentropy',
              optimizer=RMSprop(),
              metrics=['accuracy'])

model.summary()
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_1_1_noaug_epoch_" in mod]
if len(mod_list) == 0:
    model_1_1_noaug_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_1_1_noaug_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

history = model.fit(train_imgs_scaled, train_labels_enc,
                   validation_data=(val_imgs_scaled, val_labels_enc),
                   batch_size=BATCH_SIZE,
                   epochs=EPOCHS,
                   verbose=1)

model_1_1_noaug_epoch_count += 1
save_model(model, 'model_data/model_1_1_noaug_epoch_{}.h5'.format(model_1_1_noaug_epoch_count))
print('Total Epoch Count: ', model_1_1_noaug_epoch_count)
```

### 1.2 CNN Model 2


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
model = Sequential()

model.add(Conv2D(16, kernel_size=(3, 3), activation='relu', 
                 input_shape=input_shape))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(64, kernel_size=(3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(128, kernel_size=(3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(128, kernel_size=(3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Flatten())
model.add(Dense(512, activation='relu'))
model.add(Dropout(0.3))
model.add(Dense(512, activation='relu'))
model.add(Dropout(0.3))
model.add(Dense(42, activation='sigmoid'))


model.compile(loss='categorical_crossentropy',
              optimizer=optimizers.RMSprop(lr=2e-5),
              metrics=['accuracy'])

model.summary()
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_1_2_noaug_epoch_" in mod]
if len(mod_list) == 0:
    model_1_2_noaug_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_1_2_noaug_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

history = model.fit(train_imgs_scaled, train_labels_enc,
                   validation_data=(val_imgs_scaled, val_labels_enc),
                   batch_size=BATCH_SIZE,
                   epochs=EPOCHS,
                   verbose=1)

model_1_2_noaug_epoch_count += 1
save_model(model, 'model_data/model_1_2_noaug_epoch_{}.h5'.format(model_1_2_noaug_epoch_count))
print('Total Epoch Count: ', model_1_2_noaug_epoch_count)
```

## 2. Transfer-Learning Feature Extraction: VGG16

### 2.1 Without Augmentation, Without FineTune


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
# only run this once

from keras.applications import vgg16

vgg = vgg16.VGG16(include_top=False, weights='imagenet', 
                                     input_shape=input_shape)

output = vgg.layers[-1].output
output = Flatten() (output)
output = Dense(512, activation='relu') (output)
output = Dropout(0.3) (output)
output = Dense(512, activation='relu') (output)
output = Dropout(0.3) (output)
output = Dense(42, activation='sigmoid') (output)

model = Model(vgg.input, output)

model.trainable = True
for layer in vgg.layers:
    layer.trainable = False
    
fine_tuning = False
if fine_tuning:
    for layer in vgg.layers:
        if layer.name in ['block5_conv1', 'block4_conv1']:
            layer.trainable = True

            
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

print(model.summary())
pd.set_option('max_colwidth', -1)
layers = [(layer, layer.name, layer.trainable) for layer in model.layers]
pd.DataFrame(layers, columns=['Layer Type', 'Layer Name', 'Layer Trainable'])    
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_2_noaug_nofinetune_epoch_"in mod]
if len(mod_list) == 0:
    model_2_noaug_nofinetune_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_2_noaug_nofinetune_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

history = model.fit(train_imgs_scaled, train_labels_enc,
                   validation_data=(val_imgs_scaled, val_labels_enc),
                   batch_size=BATCH_SIZE,
                   epochs=EPOCHS,
                   verbose=1)

model_2_noaug_nofinetune_epoch_count += 1
save_model(model, 'model_data/model_2_noaug_nofinetune_epoch_{}.h5'.format(model_2_noaug_nofinetune_epoch_count))
print('Total Epoch Count: ', model_2_noaug_nofinetune_epoch_count)
```

### 2.3 Without Augmentation, With Fine-Tuning


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
# only run this once

from keras.applications import vgg16

vgg = vgg16.VGG16(include_top=False, weights='imagenet', 
                                     input_shape=input_shape)

output = vgg.layers[-1].output
output = Flatten() (output)
output = Dense(512, activation='relu') (output)
output = Dropout(0.3) (output)
output = Dense(512, activation='relu') (output)
output = Dropout(0.3) (output)
output = Dense(42, activation='sigmoid') (output)

model = Model(vgg.input, output)

model.trainable = True
for layer in vgg.layers:
    layer.trainable = False
    
fine_tuning = True
if fine_tuning:
    for layer in vgg.layers:
        if layer.name in ['block5_conv1', 'block4_conv1']:
            layer.trainable = True

            
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

print(model.summary())
pd.set_option('max_colwidth', -1)
layers = [(layer, layer.name, layer.trainable) for layer in model.layers]
pd.DataFrame(layers, columns=['Layer Type', 'Layer Name', 'Layer Trainable'])    
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_2_noaug_yesfinetune_epoch_"in mod]
if len(mod_list) == 0:
    model_2_noaug_yesfinetune_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_2_noaug_yesfinetune_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

history = model.fit(train_imgs_scaled, train_labels_enc,
                   validation_data=(val_imgs_scaled, val_labels_enc),
                   batch_size=BATCH_SIZE,
                   epochs=EPOCHS,
                   verbose=1)

model_2_noaug_yesfinetune_epoch_count += 1
save_model(model, 'model_data/model_2_noaug_yesfinetune_epoch_{}.h5'.format(model_2_noaug_yesfinetune_epoch_count))
print('Total Epoch Count: ', model_2_noaug_yesfinetune_epoch_count)
```

### 2.5 With Augmentation, With Revamp


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
# only run this once

from keras.applications import vgg16

vgg = vgg16.VGG16(include_top=False, weights='imagenet', 
                                     input_shape=input_shape)

output = vgg.layers[-1].output
# output = Flatten() (output)
output = GlobalAveragePooling2D() (output)
output = Dense(512, activation='relu') (output)
output = Dense(42, activation='sigmoid') (output)

model = Model(vgg.input, output)

model.trainable = True
for layer in vgg.layers:
    layer.trainable = True
    
fine_tuning = False
if fine_tuning:
    for layer in vgg.layers:
        if layer.name in ['block5_conv1', 'block4_conv1']:
            layer.trainable = True

            
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

print(model.summary())
pd.set_option('max_colwidth', -1)
layers = [(layer, layer.name, layer.trainable) for layer in model.layers]
pd.DataFrame(layers, columns=['Layer Type', 'Layer Name', 'Layer Trainable'])    
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_2_yesaug_yesrevamp_epoch_"in mod]
if len(mod_list) == 0:
    model_2_yesaug_yesrevamp_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_2_yesaug_yesrevamp_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 100
EPOCHS = 1


train_datagen = ImageDataGenerator(rescale=1, 
                                   rotation_range=20, 
                                   width_shift_range=0.1,
                                   height_shift_range=0.1, 
                                   horizontal_flip ='true')

train_generator = train_datagen.flow(train_imgs_scaled, 
                                     train_labels_enc, 
                                     shuffle=True, 
                                     batch_size=BATCH_SIZE, 
                                     seed=1)

val_datagen = ImageDataGenerator(rescale = 1)

val_generator = train_datagen.flow(val_imgs_scaled, 
                                   val_labels_enc, 
                                   shuffle=False, 
                                   batch_size=BATCH_SIZE, 
                                   seed=1)   

train_steps_per_epoch = train_imgs_scaled.shape[0] // BATCH_SIZE
val_steps_per_epoch = val_imgs_scaled.shape[0] // BATCH_SIZE


history = model.fit_generator(train_generator,
                              steps_per_epoch=train_steps_per_epoch,
                              validation_data=val_generator,
                              validation_steps=val_steps_per_epoch,
                              epochs=EPOCHS, 
                              verbose=1)

history = model.fit(train_imgs_scaled, train_labels_enc,
                   validation_data=(val_imgs_scaled, val_labels_enc),
                   batch_size=BATCH_SIZE,
                   epochs=EPOCHS,
                   verbose=1)

model_2_yesaug_yesrevamp_epoch_count += 1
save_model(model, 'model_data/model_2_yesaug_yesrevamp_epoch_{}.h5'.format(model_2_yesaug_yesrevamp_epoch_count))
print('Total Epoch Count: ', model_2_yesaug_yesrevamp_epoch_count)
```

## 3. Google's Inception V3 Model

### 3.1 Without Augmentation, Without Fine Tuning


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
from keras.applications.inception_v3 import InceptionV3

base_inception = InceptionV3(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(512, activation='relu')(out)
out = Dense(512, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = True
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = False
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()

```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_3_noaug_nofinetune_epoch_"in mod]
if len(mod_list) == 0:
    model_3_noaug_nofinetune_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_3_noaug_nofinetune_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

history = model.fit(train_imgs_scaled, train_labels_enc,
                   validation_data=(val_imgs_scaled, val_labels_enc),
                   batch_size=BATCH_SIZE,
                   epochs=EPOCHS,
                   verbose=1)

model_3_noaug_nofinetune_epoch_count += 1
save_model(model, 'model_data/model_3_noaug_nofinetune_epoch_{}.h5'.format(model_3_noaug_nofinetune_epoch_count))
print('Total Epoch Count: ', model_3_noaug_nofinetune_epoch_count)
```

#### 3.1.2 Testing Trained Models


```python
version = 1
model_name = 'model_3_noaug_nofinetune_epoch_{}.h5'.format(version)
test = load_model('model_data/' + model_name)
result = test.predict(val_imgs_scaled)
```


```python
for j in np.arange(10) / 10:
    count = 0
    denom = 0
    for i in range(len(val_imgs_scaled)):
        if result[i].max() > j:
            denom += 1
            if np.argmax(result[i]) == np.argmax(val_labels_enc[i]):
                count += 1
    print(j, round(denom/len(val_imgs_scaled), 3), round(count/denom, 3))
```

### 3.2 With Augmentation, Without FineTune


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
from keras.applications.inception_v3 import InceptionV3

base_inception = InceptionV3(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(512, activation='relu')(out)
out = Dense(512, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = True
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = False
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()

```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_3_yesaug_nofinetune_epoch_"in mod]
if len(mod_list) == 0:
    model_3_yesaug_nofinetune_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_3_yesaug_nofinetune_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

train_datagen = ImageDataGenerator(rescale=1, 
                                   rotation_range=20, 
                                   width_shift_range=0.1,
                                   height_shift_range=0.1, 
                                   horizontal_flip ='true')

train_generator = train_datagen.flow(train_imgs_scaled, 
                                     train_labels_enc, 
                                     shuffle=True, 
                                     batch_size=BATCH_SIZE, 
                                     seed=1)

val_datagen = ImageDataGenerator(rescale = 1)

val_generator = train_datagen.flow(val_imgs_scaled, 
                                   val_labels_enc, 
                                   shuffle=False, 
                                   batch_size=BATCH_SIZE, 
                                   seed=1)   


train_steps_per_epoch = train_imgs_scaled.shape[0] // BATCH_SIZE
val_steps_per_epoch = val_imgs_scaled.shape[0] // BATCH_SIZE


history = model.fit_generator(train_generator,
                              steps_per_epoch=train_steps_per_epoch,
                              validation_data=val_generator,
                              validation_steps=val_steps_per_epoch,
                              epochs=EPOCHS, 
                              verbose=1)

model_3_yesaug_nofinetune_epoch_count += 1
save_model(model, 'model_data/model_3_yesaug_nofinetune_epoch_{}.h5'.format(model_3_yesaug_nofinetune_epoch_count))
print('Total Epoch Count: ', model_3_yesaug_nofinetune_epoch_count)
```

### 3.3 Without Augmentation, With Fine Tuning


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
from keras.applications.inception_v3 import InceptionV3

base_inception = InceptionV3(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(512, activation='relu')(out)
out = Dense(512, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = True
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = False
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()

```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_3_noaug_yesfinetune_epoch_"in mod]
if len(mod_list) == 0:
    model_3_noaug_yesfinetune_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_3_noaug_yesfinetune_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

history = model.fit(train_imgs_scaled, train_labels_enc,
                   validation_data=(val_imgs_scaled, val_labels_enc),
                   batch_size=BATCH_SIZE,
                   epochs=EPOCHS,
                   verbose=1)

noaug_yesfinetune_epoch_count += 1
save_model(model, 'model_data/model_3_noaug_yesfinetune_epoch_{}.h5'.format(noaug_yesfinetune_epoch_count))
print('Total Epoch Count: ', noaug_yesfinetune_epoch_count)
```

#### 3.3.2 Testing Trained Models


```python
version = 1
model_name = 'model_3_noaug_yesfinetune_epoch_{}.h5'.format(version)
test = load_model('model_data/' + model_name)
result = test.predict(val_imgs_scaled)
```


```python
for j in np.arange(10) / 10:
    count = 0
    denom = 0
    for i in range(len(val_imgs_scaled)):
        if result[i].max() > j:
            denom += 1
            if np.argmax(result[i]) == np.argmax(val_labels_enc[i]):
                count += 1
    print(j, round(denom/len(val_imgs_scaled), 3), round(count/denom, 3))
```

### 3.4 With Augmentation, With FineTune


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
### ONLY RUN THIS CELL ONCE

from keras.applications.inception_v3 import InceptionV3

base_inception = InceptionV3(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(512, activation='relu')(out)
out = Dense(512, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = True
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = True
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_3_yesaug_yesfinetune_epoch_"in mod]
if len(mod_list) == 0:
    model_3_yesaug_yesfinetune_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_3_yesaug_yesfinetune_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

train_datagen = ImageDataGenerator(rescale=1, 
                                   rotation_range=20, 
                                   width_shift_range=0.1,
                                   height_shift_range=0.1, 
                                   horizontal_flip ='true')

train_generator = train_datagen.flow(train_imgs_scaled, 
                                     train_labels_enc, 
                                     shuffle=True, 
                                     batch_size=BATCH_SIZE, 
                                     seed=1)

val_datagen = ImageDataGenerator(rescale = 1)

val_generator = train_datagen.flow(val_imgs_scaled, 
                                   val_labels_enc, 
                                   shuffle=False, 
                                   batch_size=BATCH_SIZE, 
                                   seed=1)   


train_steps_per_epoch = train_imgs_scaled.shape[0] // BATCH_SIZE
val_steps_per_epoch = val_imgs_scaled.shape[0] // BATCH_SIZE


history = model.fit_generator(train_generator,
                              steps_per_epoch=train_steps_per_epoch,
                              validation_data=val_generator,
                              validation_steps=val_steps_per_epoch,
                              epochs=EPOCHS, 
                              verbose=1)

model_3_yesaug_yesfinetune_epoch_count += 1
save_model(model, 'model_data/model_3_yesaug_yesfinetune_epoch_{}.h5'.format(model_3_yesaug_yesfinetune_epoch_count))
print('Total Epoch Count: ', model_3_yesaug_yesfinetune_epoch_count)
```

#### 3.4.2 Testing Trained Models


```python
version = 2
model_name = 'model_3_yesaug_yesfinetune_epoch_{}.h5'.format(version)
test = load_model('model_data/' + model_name)
result = test.predict(val_imgs_scaled)
```


```python
for j in np.arange(10) / 10:
    count = 0
    denom = 0
    for i in range(len(val_imgs_scaled)):
        if result[i].max() > j:
            denom += 1
            if np.argmax(result[i]) == np.argmax(val_labels_enc[i]):
                count += 1
    print(j, round(denom/len(val_imgs_scaled), 3), round(count/denom, 3))
```

### 3.5 With Augmentation, With Revamp


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
### ONLY RUN THIS CELL ONCE

from keras.applications.inception_v3 import InceptionV3

base_inception = InceptionV3(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(512, activation='relu')(out)
out = Dense(512, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = False
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = False
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()
pd.set_option('max_colwidth', -1)
pd.options.display.max_rows = None
layers = [(layer, layer.name, layer.trainable) for layer in model.layers]
pd.DataFrame(layers, columns=['Layer Type', 'Layer Name', 'Layer Trainable'])    
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_3_yesaug_yesrevamp_epoch_"in mod]
if len(mod_list) == 0:
    model_3_yesaug_yesrevamp_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_3_yesaug_yesrevamp_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

train_datagen = ImageDataGenerator(rescale=1, 
                                   rotation_range=20, 
                                   width_shift_range=0.1,
                                   height_shift_range=0.1, 
                                   horizontal_flip ='true')

train_generator = train_datagen.flow(train_imgs_scaled, 
                                     train_labels_enc, 
                                     shuffle=True, 
                                     batch_size=BATCH_SIZE, 
                                     seed=1)

val_datagen = ImageDataGenerator(rescale = 1)

val_generator = train_datagen.flow(val_imgs_scaled, 
                                   val_labels_enc, 
                                   shuffle=False, 
                                   batch_size=BATCH_SIZE, 
                                   seed=1)   


train_steps_per_epoch = train_imgs_scaled.shape[0] // BATCH_SIZE
val_steps_per_epoch = val_imgs_scaled.shape[0] // BATCH_SIZE


history = model.fit_generator(train_generator,
                              steps_per_epoch=train_steps_per_epoch,
                              validation_data=val_generator,
                              validation_steps=val_steps_per_epoch,
                              epochs=EPOCHS, 
                              verbose=1)+


model_3_yesaug_yesrevamp_epoch_count += 1
save_model(model, 'model_data/model_3_yesaug_yesrevamp_epoch_{}.h5'.format(model_3_yesaug_yesrevamp_epoch_count))
print('Total Epoch Count: ', model_3_yesaug_yesrevamp_epoch_count)
```

#### 3.5.2 Testing Trained Models


```python
version = 2
model_name = 'model_3_yesaug_yesrevamp_epoch_{}.h5'.format(version)
test = load_model('model_data/' + model_name)
result = test.predict(val_imgs_scaled)
```


```python
pred = np.argmax(result, axis=1)
act = np.argmax(val_labels_enc, axis=1)

act_total_count = [0] * 42
correct_total_count = [0] * 42

for i in range(len(pred)):
    if max(result[i] > 0):
        act_total_count[act[i]] += 1
        if pred[i] == act[i]:
            correct_total_count[act[i]] += 1

print('Count: ', sum(act_total_count), '({}%)'.format(round(sum(act_total_count)*100/len(pred), 2)))
print('Overall Accuracy: ', round(sum(correct_total_count) / sum(act_total_count), 2))
print()
print('cat\t', 'accuracy')
for cat, prob in sorted(enumerate(list(map(lambda x: x[0]/x[1], list(zip(correct_total_count, act_total_count))))), key=lambda x:-x[1]):
    print(cat, '\t', round(prob, 2))
```


```python
for j in np.arange(10) / 10:
    count = 0
    denom = 0
    for i in range(len(val_imgs_scaled)):
        if result[i].max() > j:
            denom += 1
            if np.argmax(result[i]) == np.argmax(val_labels_enc[i]):
                count += 1
    print(j, round(denom/len(val_imgs_scaled), 3), round(count/denom, 3))
```

### 3.6 With Augmentation & Revamp BUT Different FullyConectedLayer & SGD


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
### ONLY RUN THIS CELL ONCE

from keras.optimizers import SGD
from keras.applications.inception_v3 import InceptionV3

base_inception = InceptionV3(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(1024, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = False
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = False
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(SGD(lr=0.0001, momentum=0.9), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()
pd.set_option('max_colwidth', -1)
pd.options.display.max_rows = None
layers = [(layer, layer.name, layer.trainable) for layer in model.layers]
pd.DataFrame(layers, columns=['Layer Type', 'Layer Name', 'Layer Trainable'])    
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_3_yesaug_yesrevamp_params2_epoch_"in mod]
if len(mod_list) == 0:
    model_3_yesaug_yesrevamp_params2_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_3_yesaug_yesrevamp_params2_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

train_datagen = ImageDataGenerator(rescale=1, 
                                   rotation_range=20, 
                                   width_shift_range=0.1,
                                   height_shift_range=0.1, 
                                   horizontal_flip ='true')

train_generator = train_datagen.flow(train_imgs_scaled, 
                                     train_labels_enc, 
                                     shuffle=True, 
                                     batch_size=BATCH_SIZE, 
                                     seed=1)

val_datagen = ImageDataGenerator(rescale = 1)

val_generator = train_datagen.flow(val_imgs_scaled, 
                                   val_labels_enc, 
                                   shuffle=False, 
                                   batch_size=BATCH_SIZE, 
                                   seed=1)   


train_steps_per_epoch = train_imgs_scaled.shape[0] // BATCH_SIZE
val_steps_per_epoch = val_imgs_scaled.shape[0] // BATCH_SIZE


history = model.fit_generator(train_generator,
                              steps_per_epoch=train_steps_per_epoch,
                              validation_data=val_generator,
                              validation_steps=val_steps_per_epoch,
                              epochs=EPOCHS, 
                              verbose=1)


model_3_yesaug_yesrevamp_params2_epoch_count += 1
save_model(model, 'model_data/model_3_yesaug_yesrevamp_params2_epoch_{}.h5'.format(model_3_yesaug_yesrevamp_params2_epoch_count))
print('Total Epoch Count: ', model_3_yesaug_yesrevamp_params2_epoch_count)
```

#### 3.6.2 Testing Trained Models

| epoch | accuracy |
| --- | --- |
| 1 | |
| 2 | |


```python
version = 2
model_name = 'model_3_yesaug_yesrevamp_params2_epoch_{}.h5'.format(version)
test = load_model('model_data/' + model_name)
result = test.predict(val_imgs_scaled)
```


```python
pred = np.argmax(result, axis=1)
act = np.argmax(val_labels_enc, axis=1)

act_total_count = [0] * 42
correct_total_count = [0] * 42

for i in range(len(pred)):
    if max(result[i] > 0):
        act_total_count[act[i]] += 1
        if pred[i] == act[i]:
            correct_total_count[act[i]] += 1

print('Count: ', sum(act_total_count), '({}%)'.format(round(sum(act_total_count)*100/len(pred), 2)))
print('Overall Accuracy: ', round(sum(correct_total_count) / sum(act_total_count), 2))
print()
print('cat\t', 'accuracy')
for cat, prob in sorted(enumerate(list(map(lambda x: x[0]/x[1], list(zip(correct_total_count, act_total_count))))), key=lambda x:-x[1]):
    print(cat, '\t', round(prob, 2))
```


```python
for j in np.arange(10) / 10:
    count = 0
    denom = 0
    for i in range(len(val_imgs_scaled)):
        if result[i].max() > j:
            denom += 1
            if np.argmax(result[i]) == np.argmax(val_labels_enc[i]):
                count += 1
    print(j, round(denom/len(val_imgs_scaled), 3), round(count/denom, 3))
```

## 4. mobilenet

### 4.1 With Augmentation, With Revamp


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
### ONLY RUN THIS CELL ONCE

from keras.applications import MobileNet

base_inception = MobileNet(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(512, activation='relu')(out)
out = Dense(512, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = False
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = False
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()
pd.set_option('max_colwidth', -1)
pd.options.display.max_rows = None
layers = [(layer, layer.name, layer.trainable) for layer in model.layers]
pd.DataFrame(layers, columns=['Layer Type', 'Layer Name', 'Layer Trainable'])    
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_4_yesaug_yesrevamp_epoch_"in mod]
if len(mod_list) == 0:
    model_4_yesaug_yesrevamp_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_4_yesaug_yesrevamp_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

train_datagen = ImageDataGenerator(rescale=1, 
                                   rotation_range=20, 
                                   width_shift_range=0.1,
                                   height_shift_range=0.1, 
                                   horizontal_flip ='true')

train_generator = train_datagen.flow(train_imgs_scaled, 
                                     train_labels_enc, 
                                     shuffle=True, 
                                     batch_size=BATCH_SIZE, 
                                     seed=1)

val_datagen = ImageDataGenerator(rescale = 1)

val_generator = train_datagen.flow(val_imgs_scaled, 
                                   val_labels_enc, 
                                   shuffle=False, 
                                   batch_size=1, 
                                   seed=1)   


train_steps_per_epoch = train_imgs_scaled.shape[0] // BATCH_SIZE
val_steps_per_epoch = val_imgs_scaled.shape[0] // BATCH_SIZE


history = model.fit_generator(train_generator,
                              steps_per_epoch=train_steps_per_epoch,
                              validation_data=val_generator,
                              validation_steps=val_steps_per_epoch,
                              epochs=EPOCHS, 
                              verbose=1)


model_4_yesaug_yesrevamp_epoch_count += 1
save_model(model, 'model_data/model_4_yesaug_yesrevamp_epoch_{}.h5'.format(model_4_yesaug_yesrevamp_epoch_count))
print('Total Epoch Count: ', model_4_yesaug_yesrevamp_epoch_count)
```

#### 4.1.2 Testing Trained Models


```python
version = 3
model_name = 'model_4_yesaug_yesrevamp_epoch_{}.h5'.format(version)
model = load_model('model_data/' + model_name)
result = model.predict(val_imgs_scaled)
```


```python
THRES = 0

pred = np.argmax(result, axis=1)
act = np.argmax(val_labels_enc, axis=1)

act_total_count = [0] * 42
correct_total_count = [0] * 42

for i in range(len(pred)):
    if max(result[i] > THRES):
        act_total_count[act[i]] += 1
        if pred[i] == act[i]:
            correct_total_count[act[i]] += 1

print('Count: ', sum(act_total_count), '({}%)'.format(round(sum(act_total_count)*100/len(pred), 3)))
print('Overall Accuracy: ', round(sum(correct_total_count) / sum(act_total_count), 3))
print()
print('cat\t', 'accuracy')
for cat, prob in sorted(enumerate(list(map(lambda x: x[0]/x[1], list(zip(correct_total_count, act_total_count))))), key=lambda x:-x[1]):
    print(cat, '\t', round(prob, 2))
```


```python
for j in np.arange(10) / 10:
    count = 0
    denom = 0
    for i in range(len(val_imgs_scaled)):
        if result[i].max() > j:
            denom += 1
            if np.argmax(result[i]) == np.argmax(val_labels_enc[i]):
                count += 1
    print(j, round(denom/len(val_imgs_scaled), 3), round(count/denom, 3))
```

## 5. RESNET50

### 5.1 With Augmentation, With Revamp


```python
input_shape = (IMG_DIM[0], IMG_DIM[1], 3)
print(input_shape)
```


```python
### ONLY RUN THIS CELL ONCE

from keras.applications import ResNet50

base_inception = ResNet50(weights='imagenet', include_top=False, 
                             input_shape=input_shape)
                             
out = base_inception.output
out = GlobalAveragePooling2D()(out)
out = Dense(512, activation='relu')(out)
out = Dense(512, activation='relu')(out)
predictions = Dense(42, activation='softmax')(out)

model = Model(inputs=base_inception.input, 
              outputs=predictions)

freeze_base = False
if freeze_base:
    for layer in base_inception.layers:
        layer.trainable = False

fine_tuning = False
if fine_tuning:
    unfreeze_list = [x.name for x in model.layers if 'batch_normalization' in x.name][-2:]
    unfreeze_list.append([x.name for x in model.layers if 'conv2d' in x.name][-1])
    for layer in base_inception.layers:
        if layer.name in unfreeze_list:
            layer.trainable = True
        
model.compile(Adam(lr=.0001), 
              loss='categorical_crossentropy', 
              metrics=['accuracy']) 

model.summary()
pd.options.display.max_colwidth = None
pd.options.display.max_rows = None
layers = [(layer, layer.name, layer.trainable) for layer in model.layers]
pd.DataFrame(layers, columns=['Layer Type', 'Layer Name', 'Layer Trainable'])    
```


```python
mod_list = [mod for mod in os.listdir('model_data') if "model_5_yesaug_yesrevamp_epoch_"in mod]
if len(mod_list) == 0:
    model_5_yesaug_yesrevamp_epoch_count = 0
else:
    model_name = max(mod_list)
    model = load_model('model_data/' + model_name)
    model_5_yesaug_yesrevamp_epoch_count = int(max(mod_list).split('epoch_')[1][0])
```


```python
BATCH_SIZE = 32
EPOCHS = 1

train_datagen = ImageDataGenerator(rescale=1, 
                                   rotation_range=20, 
                                   width_shift_range=0.1,
                                   height_shift_range=0.1, 
                                   horizontal_flip ='true')

train_generator = train_datagen.flow(train_imgs_scaled, 
                                     train_labels_enc, 
                                     shuffle=True, 
                                     batch_size=BATCH_SIZE, 
                                     seed=1)

val_datagen = ImageDataGenerator(rescale = 1)

val_generator = train_datagen.flow(val_imgs_scaled, 
                                   val_labels_enc, 
                                   shuffle=False, 
                                   batch_size=BATCH_SIZE, 
                                   seed=1)   


train_steps_per_epoch = train_imgs_scaled.shape[0] // BATCH_SIZE
val_steps_per_epoch = val_imgs_scaled.shape[0] // BATCH_SIZE


history = model.fit_generator(train_generator,
                              steps_per_epoch=train_steps_per_epoch,
                              validation_data=val_generator,
                              validation_steps=val_steps_per_epoch,
                              epochs=EPOCHS, 
                              verbose=1)


model_5_yesaug_yesrevamp_epoch_count += 1
save_model(model, 'model_data/model_5_yesaug_yesrevamp_epoch_{}.h5'.format(model_5_yesaug_yesrevamp_epoch_count))
print('Total Epoch Count: ', model_5_yesaug_yesrevamp_epoch_count)
```

#### 5.1.2 Testing Trained Models


```python
version = 2
model_name = 'model_5_yesaug_yesrevamp_epoch_{}.h5'.format(version)
model = load_model('model_data/' + model_name)
result = model.predict(val_imgs_scaled)
```


```python
THRES = 0

pred = np.argmax(result, axis=1)
act = np.argmax(val_labels_enc, axis=1)

act_total_count = [0] * 42
correct_total_count = [0] * 42

for i in range(len(pred)):
    if max(result[i] > THRES):
        act_total_count[act[i]] += 1
        if pred[i] == act[i]:
            correct_total_count[act[i]] += 1

print('Count: ', sum(act_total_count), '({}%)'.format(round(sum(act_total_count)*100/len(pred), 2)))
print('Overall Accuracy: ', round(sum(correct_total_count) / sum(act_total_count), 3))
print()
print('cat\t', 'accuracy')
for cat, prob in sorted(enumerate(list(map(lambda x: x[0]/x[1], list(zip(correct_total_count, act_total_count))))), key=lambda x:-x[1]):
    print(cat, '\t', round(prob, 2))
```


```python
for j in np.arange(10) / 10:
    count = 0
    denom = 0
    for i in range(len(val_imgs_scaled)):
        if result[i].max() > j:
            denom += 1
            if np.argmax(result[i]) == np.argmax(val_labels_enc[i]):
                count += 1
    print(j, round(denom/len(val_imgs_scaled), 3), round(count/denom, 3))
```

# 6. FINAL SET


```python
IMG_DIM = (150, 150)
```


```python
test_imgs = list()
bad_test_imgs = list()

ii = 0
all_paths = os.listdir('data/test/test/')
finish = len(all_path)

for img in all_paths:
    
    path = 'data/test/test/' + img
    
    try:
        test_imgs.append(img_to_array(load_img(
                path, target_size=IMG_DIM)))       

    except:

        bad_test_imgs.append(path)

    ii += 1
    update_progress(ii/finish)
        
```


```python
test_imgs = np.array(test_imgs)
test_imgs_scaled = test_imgs.astype('float32')
test_imgs_scaled /= 255
```


```python
print(test_imgs_scaled.shape)
```


```python
np.save('model_data/test_imgs_scaled.npy', test_imgs_scaled)
```


```python
test_imgs_scaled = np.load('model_data/test_imgs_scaled.npy')
```


```python
version = 2
model_name = 'model_3_yesaug_yesrevamp_epoch_{}.h5'.format(version)
model = load_model('model_data/' + model_name)
test_result = model.predict(test_imgs_scaled)
```


```python
test_result.shape
```


```python
label_to_img = dict()
for i in range(42):
    label_to_img[i] = list()
    
pred = np.argmax(test_result, axis=1)

for i in range(len(pred)):
    label_to_img[pred[i]].append(i)
    
```


```python
for cat in range(42):
    print("###########     CATEGORY {}       #############".format(cat))
    fig, ax = plt.subplots(10,10, figsize=(20,20))
    ax = ax.ravel()

    jj = 0
    for ind in label_to_img[cat][:100]:
        ax[jj].imshow(array_to_img(test_imgs_scaled[ind]))
        ax[jj].axis('off')
        jj += 1
    plt.savefig('test_results/cat_{}.png'.format(cat))
    plt.tight_layout()
    plt.show()
```
