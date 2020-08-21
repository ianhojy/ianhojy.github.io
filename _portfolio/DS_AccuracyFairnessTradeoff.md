---
title: "Accuracy-Fairness Tradeoffs in Machine Learning"
excerpt: "Under Bayesian Optimization framework"
collection: portfolio
---


<html>
<head><meta charset="utf-8" />

<title>Accuracy_Fairness_Tradeoff</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>



<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.7.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.7.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.fa-pull-left {
  float: left;
}
.fa-pull-right {
  float: right;
}
.fa.fa-pull-left {
  margin-right: .3em;
}
.fa.fa-pull-right {
  margin-left: .3em;
}
/* Deprecated as of 4.4.0 */
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
.fa-pulse {
  -webkit-animation: fa-spin 1s infinite steps(8);
  animation: fa-spin 1s infinite steps(8);
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=1)";
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2)";
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=3)";
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1)";
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook-f:before,
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-feed:before,
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before,
.fa-gratipay:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper-pp:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-resistance:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-y-combinator-square:before,
.fa-yc-square:before,
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
.fa-buysellads:before {
  content: "\f20d";
}
.fa-connectdevelop:before {
  content: "\f20e";
}
.fa-dashcube:before {
  content: "\f210";
}
.fa-forumbee:before {
  content: "\f211";
}
.fa-leanpub:before {
  content: "\f212";
}
.fa-sellsy:before {
  content: "\f213";
}
.fa-shirtsinbulk:before {
  content: "\f214";
}
.fa-simplybuilt:before {
  content: "\f215";
}
.fa-skyatlas:before {
  content: "\f216";
}
.fa-cart-plus:before {
  content: "\f217";
}
.fa-cart-arrow-down:before {
  content: "\f218";
}
.fa-diamond:before {
  content: "\f219";
}
.fa-ship:before {
  content: "\f21a";
}
.fa-user-secret:before {
  content: "\f21b";
}
.fa-motorcycle:before {
  content: "\f21c";
}
.fa-street-view:before {
  content: "\f21d";
}
.fa-heartbeat:before {
  content: "\f21e";
}
.fa-venus:before {
  content: "\f221";
}
.fa-mars:before {
  content: "\f222";
}
.fa-mercury:before {
  content: "\f223";
}
.fa-intersex:before,
.fa-transgender:before {
  content: "\f224";
}
.fa-transgender-alt:before {
  content: "\f225";
}
.fa-venus-double:before {
  content: "\f226";
}
.fa-mars-double:before {
  content: "\f227";
}
.fa-venus-mars:before {
  content: "\f228";
}
.fa-mars-stroke:before {
  content: "\f229";
}
.fa-mars-stroke-v:before {
  content: "\f22a";
}
.fa-mars-stroke-h:before {
  content: "\f22b";
}
.fa-neuter:before {
  content: "\f22c";
}
.fa-genderless:before {
  content: "\f22d";
}
.fa-facebook-official:before {
  content: "\f230";
}
.fa-pinterest-p:before {
  content: "\f231";
}
.fa-whatsapp:before {
  content: "\f232";
}
.fa-server:before {
  content: "\f233";
}
.fa-user-plus:before {
  content: "\f234";
}
.fa-user-times:before {
  content: "\f235";
}
.fa-hotel:before,
.fa-bed:before {
  content: "\f236";
}
.fa-viacoin:before {
  content: "\f237";
}
.fa-train:before {
  content: "\f238";
}
.fa-subway:before {
  content: "\f239";
}
.fa-medium:before {
  content: "\f23a";
}
.fa-yc:before,
.fa-y-combinator:before {
  content: "\f23b";
}
.fa-optin-monster:before {
  content: "\f23c";
}
.fa-opencart:before {
  content: "\f23d";
}
.fa-expeditedssl:before {
  content: "\f23e";
}
.fa-battery-4:before,
.fa-battery:before,
.fa-battery-full:before {
  content: "\f240";
}
.fa-battery-3:before,
.fa-battery-three-quarters:before {
  content: "\f241";
}
.fa-battery-2:before,
.fa-battery-half:before {
  content: "\f242";
}
.fa-battery-1:before,
.fa-battery-quarter:before {
  content: "\f243";
}
.fa-battery-0:before,
.fa-battery-empty:before {
  content: "\f244";
}
.fa-mouse-pointer:before {
  content: "\f245";
}
.fa-i-cursor:before {
  content: "\f246";
}
.fa-object-group:before {
  content: "\f247";
}
.fa-object-ungroup:before {
  content: "\f248";
}
.fa-sticky-note:before {
  content: "\f249";
}
.fa-sticky-note-o:before {
  content: "\f24a";
}
.fa-cc-jcb:before {
  content: "\f24b";
}
.fa-cc-diners-club:before {
  content: "\f24c";
}
.fa-clone:before {
  content: "\f24d";
}
.fa-balance-scale:before {
  content: "\f24e";
}
.fa-hourglass-o:before {
  content: "\f250";
}
.fa-hourglass-1:before,
.fa-hourglass-start:before {
  content: "\f251";
}
.fa-hourglass-2:before,
.fa-hourglass-half:before {
  content: "\f252";
}
.fa-hourglass-3:before,
.fa-hourglass-end:before {
  content: "\f253";
}
.fa-hourglass:before {
  content: "\f254";
}
.fa-hand-grab-o:before,
.fa-hand-rock-o:before {
  content: "\f255";
}
.fa-hand-stop-o:before,
.fa-hand-paper-o:before {
  content: "\f256";
}
.fa-hand-scissors-o:before {
  content: "\f257";
}
.fa-hand-lizard-o:before {
  content: "\f258";
}
.fa-hand-spock-o:before {
  content: "\f259";
}
.fa-hand-pointer-o:before {
  content: "\f25a";
}
.fa-hand-peace-o:before {
  content: "\f25b";
}
.fa-trademark:before {
  content: "\f25c";
}
.fa-registered:before {
  content: "\f25d";
}
.fa-creative-commons:before {
  content: "\f25e";
}
.fa-gg:before {
  content: "\f260";
}
.fa-gg-circle:before {
  content: "\f261";
}
.fa-tripadvisor:before {
  content: "\f262";
}
.fa-odnoklassniki:before {
  content: "\f263";
}
.fa-odnoklassniki-square:before {
  content: "\f264";
}
.fa-get-pocket:before {
  content: "\f265";
}
.fa-wikipedia-w:before {
  content: "\f266";
}
.fa-safari:before {
  content: "\f267";
}
.fa-chrome:before {
  content: "\f268";
}
.fa-firefox:before {
  content: "\f269";
}
.fa-opera:before {
  content: "\f26a";
}
.fa-internet-explorer:before {
  content: "\f26b";
}
.fa-tv:before,
.fa-television:before {
  content: "\f26c";
}
.fa-contao:before {
  content: "\f26d";
}
.fa-500px:before {
  content: "\f26e";
}
.fa-amazon:before {
  content: "\f270";
}
.fa-calendar-plus-o:before {
  content: "\f271";
}
.fa-calendar-minus-o:before {
  content: "\f272";
}
.fa-calendar-times-o:before {
  content: "\f273";
}
.fa-calendar-check-o:before {
  content: "\f274";
}
.fa-industry:before {
  content: "\f275";
}
.fa-map-pin:before {
  content: "\f276";
}
.fa-map-signs:before {
  content: "\f277";
}
.fa-map-o:before {
  content: "\f278";
}
.fa-map:before {
  content: "\f279";
}
.fa-commenting:before {
  content: "\f27a";
}
.fa-commenting-o:before {
  content: "\f27b";
}
.fa-houzz:before {
  content: "\f27c";
}
.fa-vimeo:before {
  content: "\f27d";
}
.fa-black-tie:before {
  content: "\f27e";
}
.fa-fonticons:before {
  content: "\f280";
}
.fa-reddit-alien:before {
  content: "\f281";
}
.fa-edge:before {
  content: "\f282";
}
.fa-credit-card-alt:before {
  content: "\f283";
}
.fa-codiepie:before {
  content: "\f284";
}
.fa-modx:before {
  content: "\f285";
}
.fa-fort-awesome:before {
  content: "\f286";
}
.fa-usb:before {
  content: "\f287";
}
.fa-product-hunt:before {
  content: "\f288";
}
.fa-mixcloud:before {
  content: "\f289";
}
.fa-scribd:before {
  content: "\f28a";
}
.fa-pause-circle:before {
  content: "\f28b";
}
.fa-pause-circle-o:before {
  content: "\f28c";
}
.fa-stop-circle:before {
  content: "\f28d";
}
.fa-stop-circle-o:before {
  content: "\f28e";
}
.fa-shopping-bag:before {
  content: "\f290";
}
.fa-shopping-basket:before {
  content: "\f291";
}
.fa-hashtag:before {
  content: "\f292";
}
.fa-bluetooth:before {
  content: "\f293";
}
.fa-bluetooth-b:before {
  content: "\f294";
}
.fa-percent:before {
  content: "\f295";
}
.fa-gitlab:before {
  content: "\f296";
}
.fa-wpbeginner:before {
  content: "\f297";
}
.fa-wpforms:before {
  content: "\f298";
}
.fa-envira:before {
  content: "\f299";
}
.fa-universal-access:before {
  content: "\f29a";
}
.fa-wheelchair-alt:before {
  content: "\f29b";
}
.fa-question-circle-o:before {
  content: "\f29c";
}
.fa-blind:before {
  content: "\f29d";
}
.fa-audio-description:before {
  content: "\f29e";
}
.fa-volume-control-phone:before {
  content: "\f2a0";
}
.fa-braille:before {
  content: "\f2a1";
}
.fa-assistive-listening-systems:before {
  content: "\f2a2";
}
.fa-asl-interpreting:before,
.fa-american-sign-language-interpreting:before {
  content: "\f2a3";
}
.fa-deafness:before,
.fa-hard-of-hearing:before,
.fa-deaf:before {
  content: "\f2a4";
}
.fa-glide:before {
  content: "\f2a5";
}
.fa-glide-g:before {
  content: "\f2a6";
}
.fa-signing:before,
.fa-sign-language:before {
  content: "\f2a7";
}
.fa-low-vision:before {
  content: "\f2a8";
}
.fa-viadeo:before {
  content: "\f2a9";
}
.fa-viadeo-square:before {
  content: "\f2aa";
}
.fa-snapchat:before {
  content: "\f2ab";
}
.fa-snapchat-ghost:before {
  content: "\f2ac";
}
.fa-snapchat-square:before {
  content: "\f2ad";
}
.fa-pied-piper:before {
  content: "\f2ae";
}
.fa-first-order:before {
  content: "\f2b0";
}
.fa-yoast:before {
  content: "\f2b1";
}
.fa-themeisle:before {
  content: "\f2b2";
}
.fa-google-plus-circle:before,
.fa-google-plus-official:before {
  content: "\f2b3";
}
.fa-fa:before,
.fa-font-awesome:before {
  content: "\f2b4";
}
.fa-handshake-o:before {
  content: "\f2b5";
}
.fa-envelope-open:before {
  content: "\f2b6";
}
.fa-envelope-open-o:before {
  content: "\f2b7";
}
.fa-linode:before {
  content: "\f2b8";
}
.fa-address-book:before {
  content: "\f2b9";
}
.fa-address-book-o:before {
  content: "\f2ba";
}
.fa-vcard:before,
.fa-address-card:before {
  content: "\f2bb";
}
.fa-vcard-o:before,
.fa-address-card-o:before {
  content: "\f2bc";
}
.fa-user-circle:before {
  content: "\f2bd";
}
.fa-user-circle-o:before {
  content: "\f2be";
}
.fa-user-o:before {
  content: "\f2c0";
}
.fa-id-badge:before {
  content: "\f2c1";
}
.fa-drivers-license:before,
.fa-id-card:before {
  content: "\f2c2";
}
.fa-drivers-license-o:before,
.fa-id-card-o:before {
  content: "\f2c3";
}
.fa-quora:before {
  content: "\f2c4";
}
.fa-free-code-camp:before {
  content: "\f2c5";
}
.fa-telegram:before {
  content: "\f2c6";
}
.fa-thermometer-4:before,
.fa-thermometer:before,
.fa-thermometer-full:before {
  content: "\f2c7";
}
.fa-thermometer-3:before,
.fa-thermometer-three-quarters:before {
  content: "\f2c8";
}
.fa-thermometer-2:before,
.fa-thermometer-half:before {
  content: "\f2c9";
}
.fa-thermometer-1:before,
.fa-thermometer-quarter:before {
  content: "\f2ca";
}
.fa-thermometer-0:before,
.fa-thermometer-empty:before {
  content: "\f2cb";
}
.fa-shower:before {
  content: "\f2cc";
}
.fa-bathtub:before,
.fa-s15:before,
.fa-bath:before {
  content: "\f2cd";
}
.fa-podcast:before {
  content: "\f2ce";
}
.fa-window-maximize:before {
  content: "\f2d0";
}
.fa-window-minimize:before {
  content: "\f2d1";
}
.fa-window-restore:before {
  content: "\f2d2";
}
.fa-times-rectangle:before,
.fa-window-close:before {
  content: "\f2d3";
}
.fa-times-rectangle-o:before,
.fa-window-close-o:before {
  content: "\f2d4";
}
.fa-bandcamp:before {
  content: "\f2d5";
}
.fa-grav:before {
  content: "\f2d6";
}
.fa-etsy:before {
  content: "\f2d7";
}
.fa-imdb:before {
  content: "\f2d8";
}
.fa-ravelry:before {
  content: "\f2d9";
}
.fa-eercast:before {
  content: "\f2da";
}
.fa-microchip:before {
  content: "\f2db";
}
.fa-snowflake-o:before {
  content: "\f2dc";
}
.fa-superpowers:before {
  content: "\f2dd";
}
.fa-wpexplorer:before {
  content: "\f2de";
}
.fa-meetup:before {
  content: "\f2e0";
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box 
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this 
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+ 
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
div.traceback-wrapper pre.traceback {
  max-height: 600px;
  overflow: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 5px;
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
[dir="rtl"] #ipython_notebook {
  margin-right: 10px;
  margin-left: 0;
}
[dir="rtl"] #ipython_notebook.pull-left {
  float: right !important;
  float: right;
}
.flex-spacer {
  flex: 1;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#kernel_logo_widget {
  margin: 0 10px;
}
span#login_widget {
  float: right;
}
[dir="rtl"] span#login_widget {
  float: left;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
.modal-header {
  cursor: move;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
[dir="rtl"] .center-nav form.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] .center-nav .navbar-text {
  float: right;
}
[dir="rtl"] .navbar-inner {
  text-align: right;
}
[dir="rtl"] div.text-left {
  text-align: right;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: pointer;
  opacity: 0;
  z-index: 2;
}
.alternate_upload .btn-xs > input.fileinput {
  margin: -1px -5px;
}
.alternate_upload .btn-upload {
  position: relative;
  height: 22px;
}
::-webkit-file-upload-button {
  cursor: pointer;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
[dir="rtl"] ul#tabs.nav-tabs > li {
  float: right;
}
[dir="rtl"] ul#tabs.nav.nav-tabs {
  padding-right: 0;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons .pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .list_toolbar .col-sm-4,
[dir="rtl"] .list_toolbar .col-sm-8 {
  float: right;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: text-bottom;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
[dir="rtl"] .list_item > div input {
  margin-right: 0;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_modified {
  margin-right: 7px;
  margin-left: 7px;
}
[dir="rtl"] .item_modified.pull-right {
  float: left !important;
  float: left;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
[dir="rtl"] .item_buttons.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .item_buttons .kernel-name {
  margin-left: 7px;
  float: right;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
.sort_button {
  display: inline-block;
  padding-left: 7px;
}
[dir="rtl"] .sort_button.pull-right {
  float: left !important;
  float: left;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
[dir="rtl"] #button-select-all.btn {
  float: right ;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
  margin-top: 2px;
  height: 16px;
}
[dir="rtl"] #select-all.pull-left {
  float: right !important;
  float: right;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.fa-pull-left {
  margin-right: .3em;
}
.folder_icon:before.fa-pull-right {
  margin-left: .3em;
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.fa-pull-left {
  margin-right: .3em;
}
.file_icon:before.fa-pull-right {
  margin-left: .3em;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
#new-menu .dropdown-header {
  font-size: 10px;
  border-bottom: 1px solid #e5e5e5;
  padding: 0 0 3px;
  margin: -3px 20px 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.move-button {
  display: none;
}
.download-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
.CodeMirror-dialog {
  background-color: #fff;
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI escape sequences */
/* The color values are a mix of
   http://www.xcolors.net/dl/baskerville-ivorylight and
   http://www.xcolors.net/dl/euphrasia */
.ansi-black-fg {
  color: #3E424D;
}
.ansi-black-bg {
  background-color: #3E424D;
}
.ansi-black-intense-fg {
  color: #282C36;
}
.ansi-black-intense-bg {
  background-color: #282C36;
}
.ansi-red-fg {
  color: #E75C58;
}
.ansi-red-bg {
  background-color: #E75C58;
}
.ansi-red-intense-fg {
  color: #B22B31;
}
.ansi-red-intense-bg {
  background-color: #B22B31;
}
.ansi-green-fg {
  color: #00A250;
}
.ansi-green-bg {
  background-color: #00A250;
}
.ansi-green-intense-fg {
  color: #007427;
}
.ansi-green-intense-bg {
  background-color: #007427;
}
.ansi-yellow-fg {
  color: #DDB62B;
}
.ansi-yellow-bg {
  background-color: #DDB62B;
}
.ansi-yellow-intense-fg {
  color: #B27D12;
}
.ansi-yellow-intense-bg {
  background-color: #B27D12;
}
.ansi-blue-fg {
  color: #208FFB;
}
.ansi-blue-bg {
  background-color: #208FFB;
}
.ansi-blue-intense-fg {
  color: #0065CA;
}
.ansi-blue-intense-bg {
  background-color: #0065CA;
}
.ansi-magenta-fg {
  color: #D160C4;
}
.ansi-magenta-bg {
  background-color: #D160C4;
}
.ansi-magenta-intense-fg {
  color: #A03196;
}
.ansi-magenta-intense-bg {
  background-color: #A03196;
}
.ansi-cyan-fg {
  color: #60C6C8;
}
.ansi-cyan-bg {
  background-color: #60C6C8;
}
.ansi-cyan-intense-fg {
  color: #258F8F;
}
.ansi-cyan-intense-bg {
  background-color: #258F8F;
}
.ansi-white-fg {
  color: #C5C1B4;
}
.ansi-white-bg {
  background-color: #C5C1B4;
}
.ansi-white-intense-fg {
  color: #A1A6B2;
}
.ansi-white-intense-bg {
  background-color: #A1A6B2;
}
.ansi-default-inverse-fg {
  color: #FFFFFF;
}
.ansi-default-inverse-bg {
  background-color: #000000;
}
.ansi-bold {
  font-weight: bold;
}
.ansi-underline {
  text-decoration: underline;
}
/* The following styles are deprecated an will be removed in a future version */
.ansibold {
  font-weight: bold;
}
.ansi-inverse {
  outline: 0.5px dotted;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  position: relative;
  overflow: visible;
}
div.cell:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: transparent;
}
div.cell.jupyter-soft-selected {
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected,
div.cell.selected.jupyter-soft-selected {
  border-color: #ababab;
}
div.cell.selected:before,
div.cell.selected.jupyter-soft-selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #42A5F5;
}
@media print {
  div.cell.selected,
  div.cell.selected.jupyter-soft-selected {
    border-color: transparent;
  }
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
}
.edit_mode div.cell.selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #66BB6A;
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  /* Note that this should set vertical padding only, since CodeMirror assumes
       that horizontal padding will be set on CodeMirror pre */
  padding: 0.4em 0;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. This sets horizontal padding only,
    use .CodeMirror-lines for vertical */
  padding: 0 0.4em;
  border: 0;
  border-radius: 0;
}
.CodeMirror-cursor {
  border-left: 1.4px solid black;
}
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .CodeMirror-cursor {
    border-left: 2px solid black;
  }
}
@media screen and (min-width: 4320px) {
  .CodeMirror-cursor {
    border-left: 4px solid black;
  }
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
div.output_area .mglyph > img {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 1px 0 1px 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul:not(.list-inline),
.rendered_html ol:not(.list-inline) {
  padding-left: 2em;
}
.rendered_html ul {
  list-style: disc;
}
.rendered_html ul ul {
  list-style: square;
  margin-top: 0;
}
.rendered_html ul ul ul {
  list-style: circle;
}
.rendered_html ol {
  list-style: decimal;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin-top: 0;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
  padding: 0px;
  background-color: #fff;
}
.rendered_html code {
  background-color: #eff0f1;
}
.rendered_html p code {
  padding: 1px 5px;
}
.rendered_html pre code {
  background-color: #fff;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  color: #000;
  font-size: 100%;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-collapse: collapse;
  border-spacing: 0;
  color: black;
  font-size: 12px;
  table-layout: fixed;
}
.rendered_html thead {
  border-bottom: 1px solid black;
  vertical-align: bottom;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  text-align: right;
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html tbody tr:nth-child(odd) {
  background: #f5f5f5;
}
.rendered_html tbody tr:hover {
  background: rgba(66, 165, 245, 0.2);
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
.rendered_html .alert {
  margin-bottom: initial;
}
.rendered_html * + .alert {
  margin-top: 1em;
}
[dir="rtl"] .rendered_html p {
  text-align: right;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.rendered .rendered_html tr,
.text_cell.rendered .rendered_html th,
.text_cell.rendered .rendered_html td {
  max-width: none;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.text_cell .dropzone .input_area {
  border: 2px dashed #bababa;
  margin: -1px;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
.jupyter-keybindings {
  padding: 1px;
  line-height: 24px;
  border-bottom: 1px solid gray;
}
.jupyter-keybindings input {
  margin: 0;
  padding: 0;
  border: none;
}
.jupyter-keybindings i {
  padding: 6px;
}
.well code {
  background-color: #ffffff;
  border-color: #ababab;
  border-width: 1px;
  border-style: solid;
  padding: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.tags_button_container {
  width: 100%;
  display: flex;
}
.tag-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  overflow: hidden;
  position: relative;
}
.tag-container > * {
  margin: 0 4px;
}
.remove-tag-btn {
  margin-left: 4px;
}
.tags-input {
  display: flex;
}
.cell-tag:last-child:after {
  content: "";
  position: absolute;
  right: 0;
  width: 40px;
  height: 100%;
  /* Fade to background color of cell toolbar */
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #EEE);
}
.tags-input > * {
  margin-left: 4px;
}
.cell-tag,
.tags-input input,
.tags-input button {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  box-shadow: none;
  width: inherit;
  font-size: inherit;
  height: 22px;
  line-height: 22px;
  padding: 0px 4px;
  display: inline-block;
}
.cell-tag:focus,
.tags-input input:focus,
.tags-input button:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.cell-tag::-moz-placeholder,
.tags-input input::-moz-placeholder,
.tags-input button::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.cell-tag:-ms-input-placeholder,
.tags-input input:-ms-input-placeholder,
.tags-input button:-ms-input-placeholder {
  color: #999;
}
.cell-tag::-webkit-input-placeholder,
.tags-input input::-webkit-input-placeholder,
.tags-input button::-webkit-input-placeholder {
  color: #999;
}
.cell-tag::-ms-expand,
.tags-input input::-ms-expand,
.tags-input button::-ms-expand {
  border: 0;
  background-color: transparent;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
.cell-tag[readonly],
.tags-input input[readonly],
.tags-input button[readonly],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  background-color: #eeeeee;
  opacity: 1;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  cursor: not-allowed;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button {
  height: auto;
}
select.cell-tag,
select.tags-input input,
select.tags-input button {
  height: 30px;
  line-height: 30px;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button,
select[multiple].cell-tag,
select[multiple].tags-input input,
select[multiple].tags-input button {
  height: auto;
}
.cell-tag,
.tags-input button {
  padding: 0px 4px;
}
.cell-tag {
  background-color: #fff;
  white-space: nowrap;
}
.tags-input input[type=text]:focus {
  outline: none;
  box-shadow: none;
  border-color: #ccc;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
[dir="rtl"] #kernel_logo_widget {
  float: left !important;
  float: left;
}
.modal .modal-body .move-path {
  display: flex;
  flex-direction: row;
  justify-content: space;
  align-items: center;
}
.modal .modal-body .move-path .server-root {
  padding-right: 20px;
}
.modal .modal-body .move-path .path-input {
  flex: 1;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
[dir="rtl"] #menubar .navbar-toggle {
  float: right;
}
[dir="rtl"] #menubar .navbar-collapse {
  clear: right;
}
[dir="rtl"] #menubar .navbar-nav {
  float: right;
}
[dir="rtl"] #menubar .nav {
  padding-right: 0px;
}
[dir="rtl"] #menubar .navbar-nav > li {
  float: right;
}
[dir="rtl"] #menubar .navbar-right {
  float: left !important;
}
[dir="rtl"] ul.dropdown-menu {
  text-align: right;
  left: auto;
}
[dir="rtl"] ul#new-menu.dropdown-menu {
  right: auto;
  left: 0;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
[dir="rtl"] i.menu-icon.pull-right {
  float: left !important;
  float: left;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
[dir="rtl"] ul#help_menu li a {
  padding-left: 2.2em;
}
[dir="rtl"] ul#help_menu li a i {
  margin-right: 0;
  margin-left: -1.2em;
}
[dir="rtl"] ul#help_menu li a i.pull-right {
  float: left !important;
  float: left;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
[dir="rtl"] .dropdown-submenu > .dropdown-menu {
  right: 100%;
  margin-right: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.fa-pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.fa-pull-right {
  margin-left: .3em;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
[dir="rtl"] .dropdown-submenu > a:after {
  float: left;
  content: "\f0d9";
  margin-right: 0;
  margin-left: -10px;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
[dir="rtl"] #notification_area {
  float: left !important;
  float: left;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] .indicator_area {
  float: left !important;
  float: left;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
[dir="rtl"] #kernel_indicator {
  float: left !important;
  float: left;
  border-left: 0;
  border-right: 1px solid;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] #modal_indicator {
  float: left !important;
  float: left;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for 
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  height: 30px;
  margin-top: 4px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  width: 50%;
  flex: 1;
}
span.save_widget span.filename {
  height: 100%;
  line-height: 1em;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
[dir="rtl"] span.save_widget.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] span.save_widget span.filename {
  margin-left: 0;
  margin-right: 16px;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
  white-space: nowrap;
  padding: 0 5px;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
    padding: 0 0 0 5px;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
.toolbar-btn-label {
  margin-left: 6px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
[dir="rtl"] .btn-group > .btn,
.btn-group-vertical > .btn {
  float: right;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
[dir="rtl"] ul.typeahead-list i {
  margin-left: 0;
  margin-right: -10px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
ul.typeahead-list  > li > a.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .typeahead-list {
  text-align: right;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  min-width: 20px;
  color: transparent;
}
[dir="rtl"] .no-shortcut.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .command-shortcut.pull-right {
  float: left !important;
  float: left;
}
.command-shortcut:before {
  content: "(command mode)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
[dir="rtl"] .edit-shortcut.pull-right {
  float: left !important;
  float: left;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
[dir="ltr"] #find-and-replace .input-group-btn + .form-control {
  border-left: none;
}
[dir="rtl"] #find-and-replace .input-group-btn + .form-control {
  border-right: none;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>
<style type="text/css">
    /*This file contains any manual css for this page that needs to override the global styles.
This is only required when different pages style the same element differently. This is just
a hack to deal with our current css styles and no new styling should be added in this file.*/

#ipython-main-app {
    position: relative;
}
#jupyter-main-app {
    position: relative;
}

    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  } 
  div.output_wrapper { 
    display: block;
    page-break-inside: avoid; 
  }
  div.output { 
    display: block;
    page-break-inside: avoid; 
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Accuracy-Fairness-Tradeoff-in-Bayesian-Optimization">Accuracy-Fairness Tradeoff in Bayesian Optimization<a class="anchor-link" href="#Accuracy-Fairness-Tradeoff-in-Bayesian-Optimization">&#182;</a></h1><p><strong>Author: Ian Ho</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In recent machine learning literature, a lot of progress has been made in finding algorithms which address fairness of predictions. There have been many approaches to ensure fairness in ML methods, such as preprocessing to encode the data by preserving as much information as possible while hiding the membership to specific subgroups. Common practice is to also remove the sensitive variable and rebalance using synthetic oversampling methods like SMOTE. Other techniques focus of post-processing, such as adjusting the threshold of learned classifier.</p>
<p>Most recently, researchers at Amazon won best paper at AutoML for their paper <a href="https://arxiv.org/abs/2006.05109">Fair Bayesian Optimization</a>. The power of their approach is that it is extremely generalizable across all sorts of machine learning problems, and is versatile in that it is able to accommodate multiple constraints at once. At the heart of their approach is the application of Bayesian Optimization that searches the hyperparameter space of ML models. It turns out that hyperparameter tuning plays a crucial role in fairness, and by fitting simultaneous gaussian processes with fairness constraints, they are able to demonstrate the ability of BO in ensuring fairness through hyperparameter search.</p>
<p>Personally, I found this approach extremely fascinating not just for its simplicity but for its ability to be adapted to almost any ML modelling. In addition, it would appear that Bayesian Optimization is able to efficiently search the hyperparameter space, which reduces the amount of resource required to search for accuracy and fairness simultaneously.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Tradeoff">Tradeoff<a class="anchor-link" href="#Tradeoff">&#182;</a></h3><p>In this notebook, I want to formalize the trade-off between accuracy and fairness using the Bayesian Optimization framework. I won't be conducting FairBO as the researchers in Amazon did, but I will be running experiments to provide an understanding of how we can begin to quantify the tradeoffs between accuracy and fairnes, and what these tradeoffs can be understood in an interpretable manner.</p>
<p>This is an important step for ML researchers, because it provides a benchmark as to what is possible given the researcher's personal tolernaces for discrimination in the ML algorithm. It also provides an understanding of the extent to which accuracy compromises varying definitinos of fairness, 3 of which will be explored in the code below. This analysis will provide an efficient way to understand the <strong>accuracy-fairness frontier</strong>, which can then be used to inform decisions such as constraints on thresholds, which are required for state-of-the-art techniques like FairBO.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Overview-of-Bayesian-Optimization">Overview of Bayesian Optimization<a class="anchor-link" href="#Overview-of-Bayesian-Optimization">&#182;</a></h3><p>(As explained in <a href="https://arxiv.org/abs/2006.05109">Fair Bayesian Optimization</a>)</p>
<p>Bayesian optimization (BO) is a well-established methodology to optimize expensive black-box functions. It relies on a probabilistic model of the unknown target $f(x)$ one wishes to optimize. The black-box $f(x)$ is repeatedly queried until one runs out of budget (e.g. time). Queries consist of evaluations of $f$ at hyperparameter configurations $x^1$,...,$x^n$ selected according to an exlpore-explot trade-off critertion, or <em>acquisition function</em>. The hyperparameter configuration corresponding to the best query is then returned. A popular approach is to impose a Gaussian process (GP) prior over $f$ and then compute the posterior GP based on the observed queries. The posterior GP is characterized by a posterior mean and a posterior variance function that are required when evaluating the acquisition function for each new query of $F$.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Dependencies">Dependencies<a class="anchor-link" href="#Dependencies">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="kn">from</span> <span class="nn">custom_transformers</span> <span class="kn">import</span> <span class="n">NominalCategoryMerger</span><span class="p">,</span> <span class="n">OrdinalCategoryMerger</span>
<span class="kn">from</span> <span class="nn">custom_transformers</span> <span class="kn">import</span> <span class="n">UnknownValuesDropper</span><span class="p">,</span> <span class="n">CharacterStripper</span> 

<span class="kn">from</span> <span class="nn">sklearn.pipeline</span> <span class="kn">import</span> <span class="n">Pipeline</span>
<span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="kn">import</span> <span class="n">StandardScaler</span><span class="p">,</span> <span class="n">OneHotEncoder</span>
<span class="kn">from</span> <span class="nn">sklearn.compose</span> <span class="kn">import</span> <span class="n">ColumnTransformer</span>
<span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="kn">import</span> <span class="n">LinearRegression</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="kn">import</span> <span class="n">RandomForestClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="kn">import</span> <span class="n">accuracy_score</span>

<span class="kn">from</span> <span class="nn">xgboost</span> <span class="kn">import</span> <span class="n">XGBClassifier</span>

<span class="kn">import</span> <span class="nn">shapely.geometry</span> <span class="k">as</span> <span class="nn">geometry</span>
<span class="kn">from</span> <span class="nn">descartes</span> <span class="kn">import</span> <span class="n">PolygonPatch</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Data-Preprocessing">Data Preprocessing<a class="anchor-link" href="#Data-Preprocessing">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Import-Data">Import Data<a class="anchor-link" href="#Import-Data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_train</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;Adult_Data/adult.data&#39;</span><span class="p">,</span> <span class="n">header</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>
<span class="n">df_test</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;Adult_Data/adult.test&#39;</span><span class="p">,</span> <span class="n">header</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_train</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;age&#39;</span><span class="p">,</span> <span class="s1">&#39;workclass&#39;</span><span class="p">,</span> <span class="s1">&#39;fnlwgt&#39;</span><span class="p">,</span> <span class="s1">&#39;education&#39;</span><span class="p">,</span> <span class="s1">&#39;education-num&#39;</span><span class="p">,</span> <span class="s1">&#39;marital-status&#39;</span><span class="p">,</span> <span class="s1">&#39;occupation&#39;</span><span class="p">,</span> <span class="s1">&#39;relationship&#39;</span><span class="p">,</span> 
                <span class="s1">&#39;race&#39;</span><span class="p">,</span> <span class="s1">&#39;sex&#39;</span><span class="p">,</span> <span class="s1">&#39;capital-gain&#39;</span><span class="p">,</span> <span class="s1">&#39;capital-loss&#39;</span><span class="p">,</span> <span class="s1">&#39;hours-per-week&#39;</span><span class="p">,</span> <span class="s1">&#39;native-country&#39;</span><span class="p">,</span> <span class="s1">&#39;&lt;=50K&#39;</span><span class="p">]</span>
<span class="n">df_test</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;age&#39;</span><span class="p">,</span> <span class="s1">&#39;workclass&#39;</span><span class="p">,</span> <span class="s1">&#39;fnlwgt&#39;</span><span class="p">,</span> <span class="s1">&#39;education&#39;</span><span class="p">,</span> <span class="s1">&#39;education-num&#39;</span><span class="p">,</span> <span class="s1">&#39;marital-status&#39;</span><span class="p">,</span> <span class="s1">&#39;occupation&#39;</span><span class="p">,</span> <span class="s1">&#39;relationship&#39;</span><span class="p">,</span> 
                <span class="s1">&#39;race&#39;</span><span class="p">,</span> <span class="s1">&#39;sex&#39;</span><span class="p">,</span> <span class="s1">&#39;capital-gain&#39;</span><span class="p">,</span> <span class="s1">&#39;capital-loss&#39;</span><span class="p">,</span> <span class="s1">&#39;hours-per-week&#39;</span><span class="p">,</span> <span class="s1">&#39;native-country&#39;</span><span class="p">,</span> <span class="s1">&#39;&lt;=50K&#39;</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Class-Composition">Class Composition<a class="anchor-link" href="#Class-Composition">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df_train</span><span class="p">[</span><span class="s1">&#39;&lt;=50K&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">(</span><span class="n">normalize</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[4]:</div>




<div class="output_text output_subarea output_execute_result">
<pre> &lt;=50K    0.75919
 &gt;50K     0.24081
Name: &lt;=50K, dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Preprocessing-Pipeline">Preprocessing Pipeline<a class="anchor-link" href="#Preprocessing-Pipeline">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[105]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">num_features</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;age&#39;</span><span class="p">,</span> <span class="s1">&#39;fnlwgt&#39;</span><span class="p">,</span> <span class="s1">&#39;education-num&#39;</span><span class="p">,</span> <span class="s1">&#39;capital-gain&#39;</span><span class="p">,</span> <span class="s1">&#39;capital-loss&#39;</span><span class="p">,</span> <span class="s1">&#39;hours-per-week&#39;</span><span class="p">]</span>
<span class="n">cat_features</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;workclass&#39;</span><span class="p">,</span> <span class="s1">&#39;marital-status&#39;</span><span class="p">,</span> <span class="s1">&#39;occupation&#39;</span><span class="p">,</span> <span class="s1">&#39;relationship&#39;</span><span class="p">,</span> <span class="s1">&#39;race&#39;</span><span class="p">,</span> <span class="s1">&#39;sex&#39;</span><span class="p">,</span> 
                  <span class="s1">&#39;native-country&#39;</span><span class="p">]</span>
<span class="n">occ_features</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;education-num&#39;</span><span class="p">]</span>
<span class="n">label</span> <span class="o">=</span> <span class="s1">&#39;&lt;=50K&#39;</span>

<span class="n">df_train</span> <span class="o">=</span> <span class="n">df_train</span><span class="p">[</span><span class="n">num_features</span> <span class="o">+</span> <span class="n">cat_features</span> <span class="o">+</span> <span class="p">[</span><span class="n">label</span><span class="p">]]</span>
<span class="n">df_test</span> <span class="o">=</span> <span class="n">df_test</span><span class="p">[</span><span class="n">num_features</span> <span class="o">+</span> <span class="n">cat_features</span> <span class="o">+</span> <span class="p">[</span><span class="n">label</span><span class="p">]]</span>

<span class="c1"># Transformer parameters</span>
<span class="n">ncc_threshold</span> <span class="o">=</span> <span class="kc">None</span>
<span class="n">ncc_alpha</span> <span class="o">=</span> <span class="o">.</span><span class="mi">1</span>

<span class="c1"># Transformer Construction and definitions</span>
<span class="n">dropper</span> <span class="o">=</span> <span class="n">UnknownValuesDropper</span><span class="p">(</span><span class="n">features</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;native-country&#39;</span><span class="p">],</span> <span class="n">unknown_value</span><span class="o">=</span><span class="s1">&#39;?&#39;</span><span class="p">)</span>
<span class="n">stripper</span> <span class="o">=</span> <span class="n">CharacterStripper</span><span class="p">([</span><span class="n">label</span><span class="p">],</span> <span class="s1">&#39;.&#39;</span><span class="p">)</span>
<span class="n">nominal_merger</span> <span class="o">=</span> <span class="n">NominalCategoryMerger</span><span class="p">(</span><span class="n">cat_features</span><span class="p">,</span> <span class="n">label</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="n">ncc_alpha</span><span class="p">)</span>
<span class="n">ordinal_merger</span> <span class="o">=</span> <span class="n">OrdinalCategoryMerger</span><span class="p">(</span><span class="n">occ_features</span><span class="p">,</span> <span class="n">label</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="n">ncc_alpha</span><span class="p">)</span>
<span class="n">scaler</span> <span class="o">=</span> <span class="n">StandardScaler</span><span class="p">()</span>
<span class="n">encoder</span> <span class="o">=</span> <span class="n">OneHotEncoder</span><span class="p">(</span><span class="n">handle_unknown</span><span class="o">=</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>

<span class="n">num_pipeline</span> <span class="o">=</span> <span class="n">Pipeline</span><span class="p">([(</span><span class="s1">&#39;StandardScaler&#39;</span><span class="p">,</span> <span class="n">scaler</span><span class="p">)])</span>
<span class="n">cat_pipeline</span> <span class="o">=</span> <span class="n">Pipeline</span><span class="p">([(</span><span class="s1">&#39;OneHotEncoder&#39;</span><span class="p">,</span> <span class="n">encoder</span><span class="p">)])</span>
<span class="n">column_transformer</span> <span class="o">=</span> <span class="n">ColumnTransformer</span><span class="p">([(</span><span class="s1">&#39;Numeric Pipeline&#39;</span><span class="p">,</span> <span class="n">num_pipeline</span><span class="p">,</span> <span class="n">num_features</span><span class="p">),</span> 
                                        <span class="p">(</span><span class="s1">&#39;Categorical Pipeline&#39;</span><span class="p">,</span> <span class="n">cat_pipeline</span><span class="p">,</span> <span class="n">cat_features</span><span class="p">),</span>
                                        <span class="p">(</span><span class="s1">&#39;Label&#39;</span><span class="p">,</span> <span class="n">encoder</span><span class="p">,</span> <span class="p">[</span><span class="n">label</span><span class="p">])</span> <span class="p">])</span>

<span class="c1"># Constructing pipeline</span>
<span class="n">X_pipeline</span> <span class="o">=</span> <span class="n">Pipeline</span><span class="p">([(</span><span class="s1">&#39;UnknownValuesDropper&#39;</span><span class="p">,</span> <span class="n">dropper</span><span class="p">),</span> 
                       <span class="p">(</span><span class="s1">&#39;CharacterStripper&#39;</span><span class="p">,</span> <span class="n">stripper</span><span class="p">),</span> 
                       <span class="p">(</span><span class="s1">&#39;NominalCategoryMerger&#39;</span><span class="p">,</span> <span class="n">nominal_merger</span><span class="p">),</span> 
                       <span class="p">(</span><span class="s1">&#39;OrdinalCategoryMerger&#39;</span><span class="p">,</span> <span class="n">ordinal_merger</span><span class="p">),</span> 
                       <span class="p">(</span><span class="s1">&#39;ColumnTransformer&#39;</span><span class="p">,</span> <span class="n">column_transformer</span><span class="p">)])</span>

<span class="c1"># Fit the pipeline and transform the datasets</span>
<span class="n">dataset_train</span> <span class="o">=</span> <span class="n">X_pipeline</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">df_train</span><span class="p">)</span>
<span class="n">dataset_test</span> <span class="o">=</span> <span class="n">X_pipeline</span><span class="o">.</span><span class="n">transform</span><span class="p">(</span><span class="n">df_test</span><span class="p">)</span>

<span class="n">X_train</span> <span class="o">=</span> <span class="n">dataset_train</span><span class="p">[:,</span> <span class="p">:</span><span class="o">-</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span>
<span class="n">y_train</span> <span class="o">=</span> <span class="n">dataset_train</span><span class="p">[:,</span> <span class="o">-</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">flatten</span><span class="p">()</span>
<span class="n">X_test</span> <span class="o">=</span> <span class="n">dataset_test</span><span class="p">[:,</span> <span class="p">:</span><span class="o">-</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span>
<span class="n">y_test</span> <span class="o">=</span> <span class="n">dataset_test</span><span class="p">[:,</span> <span class="o">-</span><span class="mi">2</span><span class="p">]</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">flatten</span><span class="p">()</span>

<span class="c1"># To convert &gt;50K into 1 and &lt;=50K into 0</span>
<span class="n">y_train</span> <span class="o">=</span> <span class="mi">1</span> <span class="o">-</span> <span class="n">y_train</span>
<span class="n">y_test</span> <span class="o">=</span> <span class="mi">1</span> <span class="o">-</span> <span class="n">y_test</span>

<span class="n">X_train</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">X_test</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">y_train</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">y_test</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Dropped 0 rows with unknown values.
Dropped 0 rows with unknown values.
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[105]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>((32561, 83), (16281, 83), (32561,), (16281,))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Isolating-Protected-labels">Isolating Protected labels<a class="anchor-link" href="#Isolating-Protected-labels">&#182;</a></h3><p>Necessary for Fairness Evaluation</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Protected label: Sex</span>

<span class="n">s_test</span> <span class="o">=</span> <span class="n">df_test</span><span class="p">[</span><span class="s1">&#39;sex&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="mi">1</span> <span class="k">if</span> <span class="s1">&#39;Male&#39;</span> <span class="ow">in</span> <span class="n">x</span> <span class="k">else</span> <span class="mi">0</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Basic-Models">Basic Models<a class="anchor-link" href="#Basic-Models">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">random_forest</span> <span class="o">=</span> <span class="n">RandomForestClassifier</span><span class="p">(</span><span class="n">n_estimators</span><span class="o">=</span><span class="mi">500</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span> <span class="p">)</span>
<span class="n">random_forest</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">y_pred</span> <span class="o">=</span> <span class="n">random_forest</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>

<span class="n">accuracy_score</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[91]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">XGB</span> <span class="o">=</span> <span class="n">XGBClassifier</span><span class="p">()</span>
<span class="n">XGB</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">y_pred</span> <span class="o">=</span> <span class="n">XGB</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>

<span class="n">accuracy_score</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[91]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>0.8715680854984338</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Fairness-Definitions">Fairness Definitions<a class="anchor-link" href="#Fairness-Definitions">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li>$Y$ : true label</li>
<li>$\hat{Y}$ : predicted label</li>
<li>$\hat{S}$ : protected (sensitive) label</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="1.-Statistical-Parity">1. Statistical Parity<a class="anchor-link" href="#1.-Statistical-Parity">&#182;</a></h4><p>Requires positive preiction to be unaffected by the value of the protected attribute, regardless of the actual true label:</p>
<p>$P(\hat{Y}=1|S=0) = P(\hat{Y}=1|S=1)$</p>
<h4 id="DSP:-Difference-in-Statistical-Parity">DSP: Difference in Statistical Parity<a class="anchor-link" href="#DSP:-Difference-in-Statistical-Parity">&#182;</a></h4><p>$ DSP: \lvert\ P(\hat{Y}=1| S=0) - P(\hat{Y}=1| S=1)\ \rvert \leq \epsilon$</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[92]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">DSP</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">s_test</span><span class="p">):</span>
    
    <span class="n">y_merge</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">zip</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">s_test</span><span class="p">))</span>
    
    <span class="n">y_merge_s0</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span><span class="p">])</span>
    <span class="n">y_merge_y1_s0</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>
    <span class="n">y_merge_s1</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>
    <span class="n">y_merge_y1_s1</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>

    <span class="k">return</span> <span class="nb">abs</span><span class="p">(((</span><span class="n">y_merge_y1_s0</span><span class="p">)</span><span class="o">/</span><span class="p">(</span><span class="n">y_merge_s0</span><span class="p">))</span> <span class="o">-</span> <span class="p">((</span><span class="n">y_merge_y1_s1</span><span class="p">)</span><span class="o">/</span><span class="p">(</span><span class="n">y_merge_s1</span><span class="p">)))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[93]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">DSP</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">s_test</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[93]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>0.17297016615352</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="2.-Equal-Opportunity">2. Equal Opportunity<a class="anchor-link" href="#2.-Equal-Opportunity">&#182;</a></h4><p>Requires equal True Positive Rates (TPR) across subgroups:</p>
<p>$P(\hat{Y}=1|Y=1, S=0) = P(\hat{Y}=1|Y=1, S=1)$</p>
<h4 id="DEO:-Difference-in-Equal-Opportunity">DEO: Difference in Equal Opportunity<a class="anchor-link" href="#DEO:-Difference-in-Equal-Opportunity">&#182;</a></h4><p>In the case of EO, a model $\hat{Y}$ is $\epsilon$-fair if the difference in EO (DEO) is at most $\epsilon$</p>
<p>$ DEO: \lvert\ P(\hat{Y}=1| Y=1, S=0) - P(\hat{Y}=1| Y=1, S=1)\ \rvert \leq \epsilon$</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[94]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">DEO</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">):</span>
    
    <span class="n">y_merge</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">zip</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">))</span>
    
    <span class="n">y_merge_y1s0</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span><span class="p">])</span>
    <span class="n">y_merge_y1_y1s0</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>
    <span class="n">y_merge_y1s1</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>
    <span class="n">y_merge_y1_y1s1</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>

    <span class="k">return</span> <span class="nb">abs</span><span class="p">(((</span><span class="n">y_merge_y1_y1s0</span><span class="p">)</span><span class="o">/</span><span class="p">(</span><span class="n">y_merge_y1s0</span><span class="p">))</span> <span class="o">-</span> <span class="p">((</span><span class="n">y_merge_y1_y1s1</span><span class="p">)</span><span class="o">/</span><span class="p">(</span><span class="n">y_merge_y1s1</span><span class="p">)))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[95]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">DEO</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[95]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>0.053687585890975775</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="3.-DFP:-Difference-in-False-Positive">3. DFP: Difference in False Positive<a class="anchor-link" href="#3.-DFP:-Difference-in-False-Positive">&#182;</a></h4><p>$ DFP: \lvert\ P(\hat{Y}=1| Y=0, S=0) - P(\hat{Y}=1| Y=0, S=1)\ \rvert \leq \epsilon$</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[100]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">DFP</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">):</span>
    
    <span class="n">y_merge</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">zip</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">))</span>
    
    <span class="n">y_merge_y0s0</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span><span class="p">])</span>
    <span class="n">y_merge_y1_y0s0</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>
    <span class="n">y_merge_y0s1</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>
    <span class="n">y_merge_y1_y0s1</span> <span class="o">=</span> <span class="nb">len</span><span class="p">([</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">y_merge</span> <span class="k">if</span> <span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span> <span class="ow">and</span> <span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span><span class="p">])</span>

    <span class="k">return</span> <span class="nb">abs</span><span class="p">(((</span><span class="n">y_merge_y1_y0s0</span><span class="p">)</span><span class="o">/</span><span class="p">(</span><span class="n">y_merge_y0s0</span><span class="p">))</span> <span class="o">-</span> <span class="p">((</span><span class="n">y_merge_y1_y0s1</span><span class="p">)</span><span class="o">/</span><span class="p">(</span><span class="n">y_merge_y0s1</span><span class="p">)))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[101]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">DFP</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[101]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>0.0640657375526352</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Demonstarting-Accuracy-Discrimination-Trade-off">Demonstarting Accuracy-Discrimination Trade-off<a class="anchor-link" href="#Demonstarting-Accuracy-Discrimination-Trade-off">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Functions-for-Bayesian-Optimization">Functions for Bayesian Optimization<a class="anchor-link" href="#Functions-for-Bayesian-Optimization">&#182;</a></h3><ul>
<li><code>rfc_test_acc</code> is a generic function that fits a RandomForestClassifier given the paramter inputs, and returns the test accuracy of the model. It also produces the fairness metric according to what is specified, and appends both the accuracy and fairness metric into an outer list called <code>acc_met_results</code>, which will be used for later analysis</li>
<li><code>rfc_test_acc</code> is then fed into a wrapper function <code>rfc_wrapper</code>, which returns the same accuracy, but is necessary to so as the round off relevant hyperparameters, since the bayesian optimization algorithm does is not constrained by integer values</li>
<li><code>optimize_rfc</code> takes <code>rfc_wrapper</code> as the feeder function for producing accuracy values, which then uses the <code>BayesianOptimization</code> class to a probabilistic model of accuracy, with the objective of optimizing hyperparameters</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[102]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">bayes_opt</span> <span class="kn">import</span> <span class="n">BayesianOptimization</span> 

<span class="k">def</span> <span class="nf">rfc_test_acc</span><span class="p">(</span><span class="n">n_estimators</span><span class="p">,</span>
                 <span class="n">max_depth</span><span class="p">,</span> 
                 <span class="n">min_samples_split</span><span class="p">,</span> 
                 <span class="n">max_features</span><span class="p">,</span>
                 <span class="n">X_train</span><span class="p">,</span> <span class="n">X_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span>
                 <span class="n">metric</span><span class="p">):</span>
    
    <span class="n">model</span> <span class="o">=</span> <span class="n">RandomForestClassifier</span><span class="p">(</span><span class="n">n_estimators</span><span class="o">=</span><span class="n">n_estimators</span><span class="p">,</span>
                                   <span class="n">max_depth</span><span class="o">=</span><span class="n">max_depth</span><span class="p">,</span>
                                   <span class="n">min_samples_split</span><span class="o">=</span><span class="n">min_samples_split</span><span class="p">,</span>
                                   <span class="n">max_features</span><span class="o">=</span><span class="n">max_features</span><span class="p">,</span>
                                   <span class="n">n_jobs</span><span class="o">=-</span><span class="mi">1</span><span class="p">)</span>
    
    <span class="n">model</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
    <span class="n">y_pred</span> <span class="o">=</span> <span class="n">model</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>
    
    <span class="n">acc</span> <span class="o">=</span> <span class="n">accuracy_score</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>
    
    <span class="k">if</span> <span class="n">metric</span><span class="o">==</span><span class="s1">&#39;DSP&#39;</span><span class="p">:</span>
        <span class="n">met</span> <span class="o">=</span> <span class="n">DSP</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">s_test</span><span class="p">)</span>
        
    <span class="k">elif</span> <span class="n">metric</span><span class="o">==</span><span class="s1">&#39;DEO&#39;</span><span class="p">:</span>
        <span class="n">met</span> <span class="o">=</span> <span class="n">DEO</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">)</span>
        
    <span class="k">elif</span> <span class="n">metric</span><span class="o">==</span><span class="s1">&#39;DFP&#39;</span><span class="p">:</span>
        <span class="n">met</span> <span class="o">=</span> <span class="n">DFP</span><span class="p">(</span><span class="n">y_pred</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">s_test</span><span class="p">)</span>

    <span class="k">return</span> <span class="n">acc</span><span class="p">,</span> <span class="n">met</span>

<span class="k">def</span> <span class="nf">optimize_rfc</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">X_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span> <span class="n">metric</span><span class="p">,</span> <span class="n">n_iter</span><span class="p">,</span> <span class="n">kappa</span><span class="p">,</span> <span class="n">show</span><span class="p">,</span> <span class="n">seed</span><span class="p">):</span>
    
    <span class="k">def</span> <span class="nf">rfc_wrapper</span><span class="p">(</span><span class="n">n_estimators</span><span class="p">,</span>
                 <span class="n">max_depth</span><span class="p">,</span> 
                 <span class="n">min_samples_split</span><span class="p">,</span> 
                 <span class="n">max_features</span><span class="p">):</span>
    
        <span class="n">acc</span><span class="p">,</span> <span class="n">met</span> <span class="o">=</span> <span class="n">rfc_test_acc</span><span class="p">(</span><span class="n">n_estimators</span><span class="o">=</span><span class="nb">int</span><span class="p">(</span><span class="n">n_estimators</span><span class="p">),</span>
                            <span class="n">max_depth</span><span class="o">=</span><span class="nb">int</span><span class="p">(</span><span class="n">max_depth</span><span class="p">),</span>
                            <span class="n">min_samples_split</span><span class="o">=</span><span class="n">min_samples_split</span><span class="p">,</span>
                            <span class="n">max_features</span><span class="o">=</span><span class="n">max_features</span><span class="p">,</span>
                            <span class="n">X_train</span><span class="o">=</span><span class="n">X_train</span><span class="p">,</span> 
                            <span class="n">X_test</span><span class="o">=</span><span class="n">X_test</span><span class="p">,</span> 
                            <span class="n">y_train</span><span class="o">=</span><span class="n">y_train</span><span class="p">,</span> 
                            <span class="n">y_test</span><span class="o">=</span><span class="n">y_test</span><span class="p">,</span>
                            <span class="n">metric</span><span class="o">=</span><span class="n">metric</span><span class="p">)</span>
        
        <span class="n">acc_met_results</span><span class="o">.</span><span class="n">append</span><span class="p">([</span><span class="n">acc</span><span class="p">,</span> <span class="n">met</span><span class="p">])</span>
        
        <span class="k">return</span> <span class="n">acc</span>
        
    <span class="k">if</span> <span class="n">show</span><span class="p">:</span>
        <span class="n">verbose</span> <span class="o">=</span> <span class="mi">2</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">verbose</span> <span class="o">=</span> <span class="mi">0</span>
        
    <span class="n">optimizer</span> <span class="o">=</span> <span class="n">BayesianOptimization</span><span class="p">(</span>
        <span class="n">f</span><span class="o">=</span><span class="n">rfc_wrapper</span><span class="p">,</span>
        <span class="n">pbounds</span><span class="o">=</span><span class="p">{</span>
            <span class="s2">&quot;n_estimators&quot;</span><span class="p">:(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">100</span><span class="p">),</span>
            <span class="s2">&quot;max_depth&quot;</span><span class="p">:(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">10</span><span class="p">),</span>
            <span class="s2">&quot;min_samples_split&quot;</span><span class="p">:(</span><span class="mf">0.01</span><span class="p">,</span> <span class="mf">0.5</span><span class="p">),</span>
            <span class="s2">&quot;max_features&quot;</span><span class="p">:(</span><span class="mf">0.2</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>
        <span class="p">},</span>
        <span class="n">random_state</span><span class="o">=</span><span class="n">seed</span><span class="p">,</span>
        <span class="n">verbose</span><span class="o">=</span><span class="n">verbose</span><span class="p">,</span>
    <span class="p">)</span>
    
    <span class="n">optimizer</span><span class="o">.</span><span class="n">maximize</span><span class="p">(</span><span class="n">n_iter</span><span class="o">=</span><span class="n">n_iter</span><span class="p">,</span> <span class="n">kappa</span><span class="o">=</span><span class="n">kappa</span><span class="p">)</span>
    
    <span class="k">if</span> <span class="n">show</span><span class="p">:</span>
        <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Final results: &quot;</span><span class="p">,</span> <span class="n">optimizer</span><span class="o">.</span><span class="n">max</span><span class="p">)</span>
    
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Experimentation">Experimentation<a class="anchor-link" href="#Experimentation">&#182;</a></h3><p>Below, we run the following experiments to understand the accuracy-fairness tradeoffs for each of the metrics DSP, DEO and DFP. For each metric, we run 10 loops (with different seeds) with 10 Bayesian-Optimization iterations each. The <code>kappa</code> value is set to 5, which makes the BO algorithm biased towards exploration rather than exploitation, since the purpose of this experiment is to obtain a general relationship between accuracy and fairness, rather than quickly arriving at a local optimum.</p>
<p>The thresold for each metric is set at 0.05, but this is purely for plotting purposes, and has no direct effect on the BO algorithm. The 0.05 threshold is used to standardise with the experiments run in <a href="https://arxiv.org/abs/2006.05109">Fair Bayesian Optimization</a>.</p>
<p>For each scatter plot of accuracy vs fairness, I also provide a convex hull boundary to give quick visualisation for the extent of linearity that exists in the tradeoff between accuracy and fairness. This is also provided alongside a simple linear regression fit.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[104]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">metric</span> <span class="ow">in</span> <span class="p">[</span><span class="s1">&#39;DSP&#39;</span><span class="p">,</span> <span class="s1">&#39;DEO&#39;</span><span class="p">,</span> <span class="s1">&#39;DFP&#39;</span><span class="p">]:</span>

    <span class="n">acc_met_results</span> <span class="o">=</span> <span class="nb">list</span><span class="p">()</span>

    <span class="n">n_iter</span> <span class="o">=</span> <span class="mi">10</span>
    <span class="n">kappa</span> <span class="o">=</span> <span class="mi">5</span>
    <span class="n">loops</span> <span class="o">=</span> <span class="mi">10</span>
    <span class="n">show</span> <span class="o">=</span> <span class="kc">False</span>

    <span class="n">thres</span> <span class="o">=</span> <span class="mf">0.05</span>

    <span class="k">for</span> <span class="n">seed</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">loops</span><span class="p">):</span>

        <span class="n">optimize_rfc</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">X_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span><span class="p">,</span>
                     <span class="n">metric</span><span class="o">=</span><span class="n">metric</span><span class="p">,</span>
                     <span class="n">n_iter</span><span class="o">=</span><span class="n">n_iter</span><span class="p">,</span> <span class="n">kappa</span><span class="o">=</span><span class="n">kappa</span><span class="p">,</span>
                     <span class="n">show</span><span class="o">=</span><span class="n">show</span><span class="p">,</span> <span class="n">seed</span><span class="o">=</span><span class="n">seed</span><span class="p">)</span>

    <span class="n">acc</span> <span class="o">=</span> <span class="p">[</span><span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">acc_met_results</span><span class="p">]</span>
    <span class="n">met</span> <span class="o">=</span> <span class="p">[</span><span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">acc_met_results</span><span class="p">]</span>

    <span class="n">LR</span> <span class="o">=</span> <span class="n">LinearRegression</span><span class="p">(</span><span class="n">fit_intercept</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">LR</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">acc</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">),</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">met</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
    <span class="n">acc_</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mf">0.01</span><span class="p">)</span>
    <span class="n">met_</span> <span class="o">=</span> <span class="n">LR</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">acc_</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">acc</span><span class="p">,</span> <span class="n">met</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">acc_</span><span class="p">,</span> <span class="n">met_</span><span class="p">,</span> <span class="n">c</span><span class="o">=</span><span class="s1">&#39;r&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">hlines</span><span class="p">(</span><span class="n">thres</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mf">0.5</span><span class="p">,</span> <span class="n">linestyles</span><span class="o">=</span><span class="s1">&#39;dotted&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">xlim</span><span class="p">(</span><span class="nb">min</span><span class="p">(</span><span class="n">acc</span><span class="p">)</span><span class="o">-</span><span class="mf">0.05</span><span class="p">,</span> <span class="nb">max</span><span class="p">(</span><span class="n">acc</span><span class="p">)</span><span class="o">+</span><span class="mf">0.05</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylim</span><span class="p">(</span><span class="nb">min</span><span class="p">(</span><span class="n">met</span><span class="p">)</span><span class="o">-</span><span class="mf">0.01</span><span class="p">,</span> <span class="nb">max</span><span class="p">(</span><span class="n">met</span><span class="p">)</span><span class="o">+</span><span class="mf">0.05</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;% Test Accuracy&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;% </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">metric</span><span class="p">))</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Accuracy-</span><span class="si">{}</span><span class="s1"> Tradeoff&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">metric</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;Slope: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">round</span><span class="p">(</span><span class="n">LR</span><span class="o">.</span><span class="n">coef_</span><span class="p">[</span><span class="mi">0</span><span class="p">][</span><span class="mi">0</span><span class="p">],</span> <span class="mi">2</span><span class="p">)))</span>
    
    <span class="n">point_collection</span> <span class="o">=</span> <span class="n">geometry</span><span class="o">.</span><span class="n">MultiPoint</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">acc_met_results</span><span class="p">))</span>
    <span class="n">patch</span> <span class="o">=</span> <span class="n">PolygonPatch</span><span class="p">(</span><span class="n">point_collection</span><span class="o">.</span><span class="n">convex_hull</span><span class="o">.</span><span class="n">buffer</span><span class="p">(</span><span class="mf">0.005</span><span class="p">),</span> <span class="n">fc</span><span class="o">=</span><span class="s1">&#39;#999999&#39;</span><span class="p">,</span>
                         <span class="n">ec</span><span class="o">=</span><span class="s1">&#39;#000000&#39;</span><span class="p">,</span> <span class="n">fill</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                         <span class="n">zorder</span><span class="o">=-</span><span class="mi">1</span><span class="p">)</span>

    <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">gca</span><span class="p">()</span>
    <span class="n">ax</span><span class="o">.</span><span class="n">add_patch</span><span class="p">(</span><span class="n">patch</span><span class="p">)</span>
    
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Accuracy-Fairness-frontier">Accuracy-Fairness frontier<a class="anchor-link" href="#Accuracy-Fairness-frontier">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As seen in the plots above, there is a trade-off between accuracy and fairness for each of the fairness metrics. Using the convex hull plots, we can quickly see that this tradeoff can be linear or non-linear. As expected, the fitted slope is positive, which intuitively means that improving accuracy comes at a cost of fairness.</p>
<p>The value of these experiments is two-fold. Firstly, it provides us with an understanding of the extent of trade-off between accuracy and fairness. For instance, it would appear that accuracy comes at a huge cost in terms of <code>DSP</code> with an estimated slope coefficient of 1.83. For interpretation purposes, this would mean that every 1% improvement in accuracy increases the unfairness measure by 0.01. Secondly, it provides us with an approach to understand the bounds of tolerance that we would want to enforce when conducting Fair Bayesian Optimization. For instance, the bounds for <code>DFP</code> are clearly around 0.08, as opposed to the scatter points for <code>DEO</code> which appear to have much higher variance and upper bounds. Thirdly, it provides us with an upper bound for the level of out-of-sample test accuracy that is achievable given an optimization problem with constraints for fairness. This bound can easily be altered according to the specified tolerance for unfairness. For instance, in the case of <code>DFP</code>, we see that for a tolerance of 0.05, the highest accuracy feasible is around 0.85, while for <code>DSP</code> the highest accuracy is around 0.8.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Appendix:-Custom-Transformation">Appendix: Custom Transformation<a class="anchor-link" href="#Appendix:-Custom-Transformation">&#182;</a></h3><div class="highlight"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">warnings</span>
<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>

<span class="kn">from</span> <span class="nn">sklearn.base</span> <span class="kn">import</span> <span class="n">BaseEstimator</span><span class="p">,</span> <span class="n">TransformerMixin</span>
<span class="kn">from</span> <span class="nn">sklearn.utils.validation</span> <span class="kn">import</span> <span class="n">check_is_fitted</span>
<span class="kn">from</span> <span class="nn">statsmodels.stats.proportion</span> <span class="kn">import</span> <span class="n">proportions_ztest</span><span class="p">,</span> <span class="n">proportion_confint</span>


<span class="k">class</span> <span class="nc">NominalCategoryMerger</span><span class="p">(</span><span class="n">BaseEstimator</span><span class="p">,</span> <span class="n">TransformerMixin</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;merges nominal categories that have similar proportions of positive target.</span>
<span class="sd">    Parameters</span>
<span class="sd">    ----------</span>
<span class="sd">    nominal_features : a list of nominal features for category combining</span>
<span class="sd">    label : the dataframe column name of the label</span>
<span class="sd">    alpha : p value threshold for deciding whether categories should be merged. Default = 0.1</span>
<span class="sd">    n_threshold : a threshold for the number of samples in the category above which it will not be merged</span>
<span class="sd">                    with a larger category. Default = None</span>
<span class="sd">    Attributes</span>
<span class="sd">    ----------</span>
<span class="sd">    merged_nominal_features_map_ : a dictionary that maps each original category to the category to with which</span>
<span class="sd">                                        it was merged.</span>
<span class="sd">    &quot;&quot;&quot;</span>

    <span class="k">def</span> <span class="fm">__init__</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">nominal_features</span><span class="p">,</span> <span class="n">label</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=.</span><span class="mi">1</span><span class="p">,</span> <span class="n">n_threshold</span><span class="o">=</span><span class="kc">None</span><span class="p">):</span>
        <span class="k">if</span> <span class="n">alpha</span> <span class="o">&gt;=</span> <span class="mi">1</span> <span class="ow">or</span> <span class="n">alpha</span> <span class="o">&lt;=</span> <span class="mi">0</span><span class="p">:</span>
            <span class="k">raise</span> <span class="ne">ValueError</span><span class="p">(</span><span class="s2">&quot;alpha=</span><span class="si">{0}</span><span class="s2"> must be between 0 and 1.&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">alpha</span><span class="p">))</span>

        <span class="bp">self</span><span class="o">.</span><span class="n">nominal_features</span> <span class="o">=</span> <span class="n">nominal_features</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">label</span> <span class="o">=</span> <span class="n">label</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">alpha</span> <span class="o">=</span> <span class="n">alpha</span>
        <span class="k">if</span> <span class="nb">type</span><span class="p">(</span><span class="n">n_threshold</span><span class="p">)</span> <span class="o">==</span> <span class="nb">list</span><span class="p">:</span>
            <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">n_threshold</span><span class="p">)</span> <span class="o">!=</span> <span class="nb">len</span><span class="p">(</span><span class="n">nominal_features</span><span class="p">):</span>
                <span class="k">raise</span> <span class="ne">ValueError</span><span class="p">(</span><span class="s2">&quot;The length of n_threshold=</span><span class="si">{0}</span><span class="s2"> and nominal_features=</span><span class="si">{1}</span><span class="s2"> must be similar.&quot;</span>
                                 <span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">n_threshold</span><span class="p">),</span> <span class="n">nominal_features</span><span class="p">))</span>
            <span class="bp">self</span><span class="o">.</span><span class="n">n_threshold</span> <span class="o">=</span> <span class="n">n_threshold</span>
        <span class="k">else</span><span class="p">:</span>
            <span class="bp">self</span><span class="o">.</span><span class="n">n_threshold</span> <span class="o">=</span> <span class="p">[</span><span class="n">n_threshold</span><span class="p">]</span> <span class="o">*</span> <span class="nb">len</span><span class="p">(</span><span class="n">nominal_features</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">merged_nominal_features_map_</span> <span class="o">=</span> <span class="p">{}</span>

    <span class="nd">@staticmethod</span>
    <span class="k">def</span> <span class="nf">aggregate_categorical_feature</span><span class="p">(</span><span class="n">var</span><span class="p">,</span> <span class="n">df</span><span class="p">):</span>
        <span class="c1"># Aggregate the target variable with respect to the categorical feature</span>
        <span class="n">cat_explore</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">df</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">(),</span> <span class="n">df</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="n">var</span><span class="p">)[</span><span class="s1">&#39;num_label&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">()],</span>
                                <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">keys</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Trials&#39;</span><span class="p">,</span> <span class="s1">&#39;Successes&#39;</span><span class="p">],</span> <span class="n">sort</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
        <span class="n">cat_explore</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="n">var</span>
        <span class="k">return</span> <span class="n">cat_explore</span>

    <span class="nd">@staticmethod</span>
    <span class="k">def</span> <span class="nf">get_best_nominal_value_pair</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">,</span> <span class="n">trials</span><span class="p">,</span> <span class="n">successes</span><span class="p">,</span> <span class="n">value_pairs</span><span class="p">):</span>
        <span class="c1"># Return the pair of categories that are the most likely (in terms of p value) to be sampled from</span>
        <span class="c1"># the same distribution.</span>
        <span class="n">p_vals</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">([</span><span class="mf">0.</span><span class="p">]</span> <span class="o">*</span> <span class="nb">len</span><span class="p">(</span><span class="n">value_pairs</span><span class="p">))</span>

        <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">value_pairs</span><span class="p">)):</span>
            <span class="n">trials_i</span> <span class="o">=</span> <span class="p">[</span><span class="n">trials</span><span class="p">[</span><span class="n">value_pairs</span><span class="p">[</span><span class="n">i</span><span class="p">][</span><span class="mi">0</span><span class="p">]]]</span> <span class="o">+</span> <span class="p">[</span><span class="n">trials</span><span class="p">[</span><span class="n">value_pairs</span><span class="p">[</span><span class="n">i</span><span class="p">][</span><span class="mi">1</span><span class="p">]]]</span>
            <span class="n">successes_i</span> <span class="o">=</span> <span class="p">[</span><span class="n">successes</span><span class="p">[</span><span class="n">value_pairs</span><span class="p">[</span><span class="n">i</span><span class="p">][</span><span class="mi">0</span><span class="p">]]]</span> <span class="o">+</span> <span class="p">[</span><span class="n">successes</span><span class="p">[</span><span class="n">value_pairs</span><span class="p">[</span><span class="n">i</span><span class="p">][</span><span class="mi">1</span><span class="p">]]]</span>
            <span class="n">z</span><span class="p">,</span> <span class="n">p_vals</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">proportions_ztest</span><span class="p">(</span><span class="n">nobs</span><span class="o">=</span><span class="n">trials_i</span><span class="p">,</span> <span class="n">count</span><span class="o">=</span><span class="n">successes_i</span><span class="p">)</span>

        <span class="n">best_value_pair</span> <span class="o">=</span> <span class="nb">sorted</span><span class="p">([</span><span class="n">nominal_values</span><span class="p">[</span><span class="n">value_pairs</span><span class="p">[</span><span class="n">p_vals</span><span class="o">.</span><span class="n">argmax</span><span class="p">()][</span><span class="mi">0</span><span class="p">]],</span>
                                  <span class="n">nominal_values</span><span class="p">[</span><span class="n">value_pairs</span><span class="p">[</span><span class="n">p_vals</span><span class="o">.</span><span class="n">argmax</span><span class="p">()][</span><span class="mi">1</span><span class="p">]]],</span>
                                 <span class="n">key</span><span class="o">=</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">trials</span><span class="p">[</span><span class="nb">list</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">)</span><span class="o">.</span><span class="n">index</span><span class="p">(</span><span class="n">x</span><span class="p">)],</span> <span class="n">reverse</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

        <span class="k">return</span> <span class="n">best_value_pair</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">amax</span><span class="p">(</span><span class="n">p_vals</span><span class="p">)</span>

    <span class="k">def</span> <span class="nf">fit</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">):</span>
        <span class="sd">&quot;&quot;&quot;Fit NominalCategoryMerger to X.</span>
<span class="sd">        Parameters</span>
<span class="sd">        ----------</span>
<span class="sd">        X : a dataframe.</span>
<span class="sd">        Returns</span>
<span class="sd">        -------</span>
<span class="sd">        self</span>
<span class="sd">        &quot;&quot;&quot;</span>
        <span class="c1"># Binarize label for proportion calculations</span>
        <span class="n">label_values</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="bp">self</span><span class="o">.</span><span class="n">label</span><span class="p">]</span><span class="o">.</span><span class="n">unique</span><span class="p">()</span>
        <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">label_values</span><span class="p">)</span> <span class="o">!=</span> <span class="mi">2</span><span class="p">:</span>
            <span class="k">raise</span> <span class="ne">ValueError</span><span class="p">(</span><span class="s2">&quot;Number of classes=</span><span class="si">{0}</span><span class="s2"> must be 2&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">label_values</span><span class="p">)))</span>
        <span class="n">X</span><span class="p">[</span><span class="s1">&#39;num_label&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="bp">self</span><span class="o">.</span><span class="n">label</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">({</span><span class="n">label_values</span><span class="p">[</span><span class="mi">0</span><span class="p">]:</span> <span class="mi">1</span><span class="p">,</span> <span class="n">label_values</span><span class="p">[</span><span class="mi">1</span><span class="p">]:</span> <span class="mi">0</span><span class="p">})</span>

        <span class="k">for</span> <span class="n">var</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">nominal_features</span><span class="p">:</span>
            <span class="c1"># Get aggregate stats for pairs of categories and pick the best one.</span>
            <span class="n">ag_results</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">aggregate_categorical_feature</span><span class="p">(</span><span class="n">var</span><span class="p">,</span> <span class="n">X</span><span class="p">)</span>
            <span class="n">trials</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Trials&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
            <span class="n">successes</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Successes&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
            <span class="n">nominal_values</span> <span class="o">=</span> <span class="n">ag_results</span><span class="o">.</span><span class="n">index</span>
            <span class="n">value_pairs</span> <span class="o">=</span> <span class="p">[[</span><span class="n">i</span><span class="p">,</span> <span class="n">j</span><span class="p">]</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">))</span> <span class="k">for</span> <span class="n">j</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">))</span>
                           <span class="k">if</span> <span class="n">j</span> <span class="o">&gt;</span> <span class="n">i</span><span class="p">]</span>
            <span class="n">best_value_pair</span><span class="p">,</span> <span class="n">p_val</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">get_best_nominal_value_pair</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">,</span> <span class="n">trials</span><span class="p">,</span> <span class="n">successes</span><span class="p">,</span>
                                                                      <span class="n">value_pairs</span><span class="p">)</span>
            <span class="bp">self</span><span class="o">.</span><span class="n">merged_nominal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">]</span> <span class="o">=</span> <span class="p">{</span><span class="n">val</span><span class="p">:</span> <span class="n">val</span> <span class="k">for</span> <span class="n">val</span> <span class="ow">in</span> <span class="n">nominal_values</span><span class="p">}</span>

            <span class="k">while</span> <span class="n">p_val</span> <span class="o">&gt;</span> <span class="bp">self</span><span class="o">.</span><span class="n">alpha</span><span class="p">:</span>
                <span class="c1"># Unite best pair</span>
                <span class="n">indices_to_change</span> <span class="o">=</span> <span class="p">[</span><span class="n">i</span> <span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">x</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">merged_nominal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">]</span>
                                                                  <span class="o">.</span><span class="n">values</span><span class="p">()))</span> <span class="k">if</span> <span class="n">x</span> <span class="o">==</span> <span class="n">best_value_pair</span><span class="p">[</span><span class="mi">1</span><span class="p">]]</span>
                <span class="n">values_to_change</span> <span class="o">=</span> <span class="p">[</span><span class="nb">list</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">merged_nominal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">keys</span><span class="p">())[</span><span class="n">i</span><span class="p">]</span>
                                    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">indices_to_change</span><span class="p">]</span>
                <span class="k">for</span> <span class="n">val</span> <span class="ow">in</span> <span class="n">values_to_change</span><span class="p">:</span>
                    <span class="bp">self</span><span class="o">.</span><span class="n">merged_nominal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">][</span><span class="n">val</span><span class="p">]</span> <span class="o">=</span> <span class="n">best_value_pair</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span>
                    <span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">]</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">best_value_pair</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="k">if</span> <span class="n">x</span> <span class="o">==</span> <span class="n">val</span> <span class="k">else</span> <span class="n">x</span><span class="p">)</span>

                <span class="c1"># Find the best pair among the new set of categories.</span>
                <span class="n">ag_results</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">aggregate_categorical_feature</span><span class="p">(</span><span class="n">var</span><span class="p">,</span> <span class="n">X</span><span class="p">)</span>
                <span class="n">trials</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Trials&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
                <span class="n">successes</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Successes&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
                <span class="n">nominal_values</span> <span class="o">=</span> <span class="n">ag_results</span><span class="o">.</span><span class="n">index</span>
                <span class="n">value_pairs</span> <span class="o">=</span> <span class="p">[[</span><span class="n">i</span><span class="p">,</span> <span class="n">j</span><span class="p">]</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">))</span> <span class="k">for</span> <span class="n">j</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">))</span>
                               <span class="k">if</span> <span class="n">j</span> <span class="o">&gt;</span> <span class="n">i</span><span class="p">]</span>
                <span class="n">best_value_pair</span><span class="p">,</span> <span class="n">p_val</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">get_best_nominal_value_pair</span><span class="p">(</span><span class="n">nominal_values</span><span class="p">,</span> <span class="n">trials</span><span class="p">,</span> <span class="n">successes</span><span class="p">,</span>
                                                                          <span class="n">value_pairs</span><span class="p">)</span>
        <span class="n">X</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;num_label&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
        <span class="k">return</span> <span class="bp">self</span>

    <span class="k">def</span> <span class="nf">transform</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">):</span>
        <span class="n">check_is_fitted</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="s1">&#39;merged_nominal_features_map_&#39;</span><span class="p">)</span>

        <span class="k">for</span> <span class="n">var</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">nominal_features</span><span class="p">:</span>
            <span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">]</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">merged_nominal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">])</span>
        <span class="k">return</span> <span class="n">X</span>


<span class="k">class</span> <span class="nc">OrdinalCategoryMerger</span><span class="p">(</span><span class="n">BaseEstimator</span><span class="p">,</span> <span class="n">TransformerMixin</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;Merges adjacent ordinal categories that have similar proportions of positive target.</span>
<span class="sd">    Parameters</span>
<span class="sd">    ----------</span>
<span class="sd">    ordinal_features : a list of ordinal features for category combining</span>
<span class="sd">    label : the dataframe column name of the label</span>
<span class="sd">    alpha : p value threshold for deciding whether categories should be merged. Default = 0.1</span>
<span class="sd">    n_threshold : a threshold for the number of samples in the category above which it will not be merged</span>
<span class="sd">                    with a larger category. Default = None</span>
<span class="sd">    Attributes</span>
<span class="sd">    ----------</span>
<span class="sd">    merged_ordinal_features_map_ : a dictionary that maps each original category to the category to with which</span>
<span class="sd">                                        it was merged.</span>
<span class="sd">    &quot;&quot;&quot;</span>

    <span class="k">def</span> <span class="fm">__init__</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">ordinal_features</span><span class="p">,</span> <span class="n">label</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=.</span><span class="mi">1</span><span class="p">,</span> <span class="n">n_threshold</span><span class="o">=</span><span class="kc">None</span><span class="p">):</span>
        <span class="k">if</span> <span class="n">alpha</span> <span class="o">&gt;=</span> <span class="mi">1</span> <span class="ow">or</span> <span class="n">alpha</span> <span class="o">&lt;=</span> <span class="mi">0</span><span class="p">:</span>
            <span class="k">raise</span> <span class="ne">ValueError</span><span class="p">(</span><span class="s2">&quot;alpha=</span><span class="si">{0}</span><span class="s2"> must be between 0 and 1.&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">alpha</span><span class="p">))</span>

        <span class="bp">self</span><span class="o">.</span><span class="n">ordinal_features</span> <span class="o">=</span> <span class="n">ordinal_features</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">label</span> <span class="o">=</span> <span class="n">label</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">alpha</span> <span class="o">=</span> <span class="n">alpha</span>
        <span class="k">if</span> <span class="nb">type</span><span class="p">(</span><span class="n">n_threshold</span><span class="p">)</span> <span class="o">==</span> <span class="nb">list</span><span class="p">:</span>
            <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">n_threshold</span><span class="p">)</span> <span class="o">!=</span> <span class="nb">len</span><span class="p">(</span><span class="n">ordinal_features</span><span class="p">):</span>
                <span class="k">raise</span> <span class="ne">ValueError</span><span class="p">(</span><span class="s2">&quot;The length of n_threshold=</span><span class="si">{0}</span><span class="s2"> and ordinal_features=</span><span class="si">{1}</span><span class="s2"> must be similar.&quot;</span>
                                 <span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">n_threshold</span><span class="p">),</span> <span class="n">ordinal_features</span><span class="p">))</span>
            <span class="bp">self</span><span class="o">.</span><span class="n">n_threshold</span> <span class="o">=</span> <span class="n">n_threshold</span>
        <span class="k">else</span><span class="p">:</span>
            <span class="bp">self</span><span class="o">.</span><span class="n">n_threshold</span> <span class="o">=</span> <span class="p">[</span><span class="n">n_threshold</span><span class="p">]</span> <span class="o">*</span> <span class="nb">len</span><span class="p">(</span><span class="n">ordinal_features</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span> <span class="o">=</span> <span class="p">{}</span>

    <span class="nd">@staticmethod</span>
    <span class="k">def</span> <span class="nf">aggregate_categorical_feature</span><span class="p">(</span><span class="n">var</span><span class="p">,</span> <span class="n">df</span><span class="p">):</span>
        <span class="c1"># Aggregate the target variable with respect to the categorical feature</span>
        <span class="n">cat_explore</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">df</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">(),</span> <span class="n">df</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="n">var</span><span class="p">)[</span><span class="s1">&#39;num_label&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">sum</span><span class="p">()],</span>
                                <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">keys</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Trials&#39;</span><span class="p">,</span> <span class="s1">&#39;Successes&#39;</span><span class="p">])</span>
        <span class="n">cat_explore</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="n">var</span>
        <span class="k">return</span> <span class="n">cat_explore</span><span class="o">.</span><span class="n">sort_index</span><span class="p">()</span>

    <span class="nd">@staticmethod</span>
    <span class="k">def</span> <span class="nf">unite_ordinal_categories</span><span class="p">(</span><span class="n">ordinal_series</span><span class="p">,</span> <span class="n">category_1</span><span class="p">,</span> <span class="n">category_2</span><span class="p">):</span>
        <span class="k">return</span> <span class="n">ordinal_series</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">category_1</span> <span class="k">if</span> <span class="n">x</span> <span class="o">==</span> <span class="n">category_2</span> <span class="k">else</span> <span class="n">x</span><span class="p">)</span>

    <span class="nd">@staticmethod</span>
    <span class="k">def</span> <span class="nf">get_categories_to_collapse</span><span class="p">(</span><span class="n">ordinal_values</span><span class="p">,</span> <span class="n">trials</span><span class="p">,</span> <span class="n">successes</span><span class="p">):</span>
        <span class="c1"># Calculate P-values for adjacent categories</span>
        <span class="n">p_vals</span> <span class="o">=</span> <span class="p">[</span><span class="mf">0.</span><span class="p">]</span> <span class="o">*</span> <span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">ordinal_values</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span><span class="p">)</span>
        <span class="n">p_vals</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">p_vals</span><span class="p">)</span>
        <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">ordinal_values</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span><span class="p">):</span>
            <span class="k">if</span> <span class="n">p_vals</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
                <span class="n">z</span><span class="p">,</span> <span class="n">p</span> <span class="o">=</span> <span class="n">proportions_ztest</span><span class="p">(</span><span class="n">nobs</span><span class="o">=</span><span class="n">trials</span><span class="p">[</span><span class="n">i</span><span class="p">:</span><span class="n">i</span> <span class="o">+</span> <span class="mi">2</span><span class="p">],</span> <span class="n">count</span><span class="o">=</span><span class="n">successes</span><span class="p">[</span><span class="n">i</span><span class="p">:</span><span class="n">i</span> <span class="o">+</span> <span class="mi">2</span><span class="p">])</span>
                <span class="n">p_vals</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">p</span>
        <span class="k">return</span> <span class="n">p_vals</span>

    <span class="k">def</span> <span class="nf">fit</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">):</span>
        <span class="sd">&quot;&quot;&quot;Fit OrdinalCategoryMerger to X.</span>
<span class="sd">        Parameters</span>
<span class="sd">        ----------</span>
<span class="sd">        X : a dataframe.</span>
<span class="sd">        Returns</span>
<span class="sd">        -------</span>
<span class="sd">        self</span>
<span class="sd">        &quot;&quot;&quot;</span>
        <span class="c1"># Binarize label for proportion calculations</span>
        <span class="n">label_values</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="bp">self</span><span class="o">.</span><span class="n">label</span><span class="p">]</span><span class="o">.</span><span class="n">unique</span><span class="p">()</span>
        <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">label_values</span><span class="p">)</span> <span class="o">!=</span> <span class="mi">2</span><span class="p">:</span>
            <span class="k">raise</span> <span class="ne">ValueError</span><span class="p">(</span><span class="s2">&quot;Number of classes=</span><span class="si">{0}</span><span class="s2"> must be 2&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">label_values</span><span class="p">)))</span>
        <span class="n">X</span><span class="p">[</span><span class="s1">&#39;num_label&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="bp">self</span><span class="o">.</span><span class="n">label</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">({</span><span class="n">label_values</span><span class="p">[</span><span class="mi">0</span><span class="p">]:</span> <span class="mi">1</span><span class="p">,</span> <span class="n">label_values</span><span class="p">[</span><span class="mi">1</span><span class="p">]:</span> <span class="mi">0</span><span class="p">})</span>

        <span class="k">for</span> <span class="n">var</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">ordinal_features</span><span class="p">:</span>
            <span class="c1"># Get aggregate stats for adjacent pairs of categories and calculate P-values.</span>
            <span class="n">ag_results</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">aggregate_categorical_feature</span><span class="p">(</span><span class="n">var</span><span class="p">,</span> <span class="n">X</span><span class="p">)</span>
            <span class="n">trials</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Trials&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
            <span class="n">successes</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Successes&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
            <span class="n">ordinal_values</span> <span class="o">=</span> <span class="n">ag_results</span><span class="o">.</span><span class="n">index</span>
            <span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">]</span> <span class="o">=</span> <span class="p">{</span><span class="n">val</span><span class="p">:</span> <span class="n">val</span> <span class="k">for</span> <span class="n">val</span> <span class="ow">in</span> <span class="n">ordinal_values</span><span class="p">}</span>
            <span class="n">pvals</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">get_categories_to_collapse</span><span class="p">(</span><span class="n">ordinal_values</span><span class="o">=</span><span class="n">ordinal_values</span><span class="p">,</span> <span class="n">trials</span><span class="o">=</span><span class="n">trials</span><span class="p">,</span>
                                                    <span class="n">successes</span><span class="o">=</span><span class="n">successes</span><span class="p">)</span>

            <span class="k">while</span> <span class="n">np</span><span class="o">.</span><span class="n">amax</span><span class="p">(</span><span class="n">pvals</span><span class="p">)</span> <span class="o">&gt;</span> <span class="bp">self</span><span class="o">.</span><span class="n">alpha</span><span class="p">:</span>
                <span class="c1"># Unite best pair</span>
                <span class="n">category_1</span><span class="p">,</span> <span class="n">category_2</span> <span class="o">=</span> <span class="n">ordinal_values</span><span class="p">[</span><span class="n">pvals</span><span class="o">.</span><span class="n">argmax</span><span class="p">()],</span> <span class="n">ordinal_values</span><span class="p">[</span><span class="n">pvals</span><span class="o">.</span><span class="n">argmax</span><span class="p">()</span> <span class="o">+</span> <span class="mi">1</span><span class="p">]</span>
                <span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">][</span><span class="n">category_2</span><span class="p">]</span> <span class="o">=</span> <span class="n">category_1</span>
                <span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">]</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">unite_ordinal_categories</span><span class="p">(</span><span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">],</span> <span class="n">category_1</span><span class="p">,</span> <span class="n">category_2</span><span class="p">)</span>

                <span class="c1"># Find the best pair among the new set of categories.</span>
                <span class="n">ag_results</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">aggregate_categorical_feature</span><span class="p">(</span><span class="n">var</span><span class="o">=</span><span class="n">var</span><span class="p">,</span> <span class="n">df</span><span class="o">=</span><span class="n">X</span><span class="p">)</span>
                <span class="n">trials</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Trials&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
                <span class="n">successes</span> <span class="o">=</span> <span class="n">ag_results</span><span class="p">[</span><span class="s1">&#39;Successes&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
                <span class="n">ordinal_values</span> <span class="o">=</span> <span class="n">ag_results</span><span class="o">.</span><span class="n">index</span>
                <span class="n">pvals</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">get_categories_to_collapse</span><span class="p">(</span><span class="n">ordinal_values</span><span class="o">=</span><span class="n">ordinal_values</span><span class="p">,</span> <span class="n">trials</span><span class="o">=</span><span class="n">trials</span><span class="p">,</span>
                                                        <span class="n">successes</span><span class="o">=</span><span class="n">successes</span><span class="p">)</span>
            <span class="c1"># Recode ordinal features as consecutive integers</span>
            <span class="n">values</span> <span class="o">=</span> <span class="nb">sorted</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="nb">set</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">())))</span>
            <span class="k">for</span> <span class="n">key</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">keys</span><span class="p">():</span>
                <span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">][</span><span class="n">key</span><span class="p">]</span> <span class="o">=</span> <span class="n">values</span><span class="o">.</span><span class="n">index</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span>
                                                                           <span class="p">[</span><span class="n">var</span><span class="p">][</span><span class="n">key</span><span class="p">])</span> <span class="o">+</span> <span class="mi">1</span>
        <span class="n">X</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;num_label&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
        <span class="k">return</span> <span class="bp">self</span>

    <span class="k">def</span> <span class="nf">transform</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">):</span>
        <span class="n">check_is_fitted</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="s1">&#39;merged_ordinal_features_map_&#39;</span><span class="p">)</span>

        <span class="k">for</span> <span class="n">var</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">ordinal_features</span><span class="p">:</span>
            <span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">]</span> <span class="o">=</span> <span class="n">X</span><span class="p">[</span><span class="n">var</span><span class="p">]</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">merged_ordinal_features_map_</span><span class="p">[</span><span class="n">var</span><span class="p">])</span>

        <span class="k">return</span> <span class="n">X</span>


<span class="k">class</span> <span class="nc">UnknownValuesDropper</span><span class="p">(</span><span class="n">BaseEstimator</span><span class="p">,</span> <span class="n">TransformerMixin</span><span class="p">):</span>
    <span class="k">def</span> <span class="fm">__init__</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">features</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span> <span class="n">unknown_value</span><span class="o">=</span><span class="s1">&#39;?&#39;</span><span class="p">):</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">unknown_value</span> <span class="o">=</span> <span class="n">unknown_value</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">features</span> <span class="o">=</span> <span class="n">features</span>

    <span class="k">def</span> <span class="nf">fit</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="kc">None</span><span class="p">):</span>
        <span class="k">return</span> <span class="bp">self</span>

    <span class="k">def</span> <span class="nf">transform</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="kc">None</span><span class="p">):</span>
        <span class="n">X_transformed</span> <span class="o">=</span> <span class="n">X</span>
        <span class="k">for</span> <span class="n">feat</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">features</span><span class="p">:</span>
            <span class="n">X_transformed</span> <span class="o">=</span> <span class="n">X_transformed</span><span class="p">[</span><span class="n">X_transformed</span><span class="p">[</span><span class="n">feat</span><span class="p">]</span> <span class="o">!=</span> <span class="bp">self</span><span class="o">.</span><span class="n">unknown_value</span><span class="p">]</span>
        <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Dropped </span><span class="si">{}</span><span class="s2"> rows with unknown values.&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">X</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">-</span> <span class="n">X_transformed</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]))</span>
        <span class="k">return</span> <span class="n">X_transformed</span>


<span class="k">class</span> <span class="nc">CharacterStripper</span><span class="p">(</span><span class="n">BaseEstimator</span><span class="p">,</span> <span class="n">TransformerMixin</span><span class="p">):</span>
    <span class="k">def</span> <span class="fm">__init__</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">features_to_strip</span><span class="p">,</span> <span class="n">character_to_strip</span><span class="o">=</span><span class="s1">&#39;.&#39;</span><span class="p">):</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">character_to_strip</span> <span class="o">=</span> <span class="n">character_to_strip</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">features_to_strip</span> <span class="o">=</span> <span class="n">features_to_strip</span>

    <span class="k">def</span> <span class="nf">fit</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="kc">None</span><span class="p">):</span>
        <span class="k">return</span> <span class="bp">self</span>

    <span class="k">def</span> <span class="nf">transform</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="kc">None</span><span class="p">):</span>
        <span class="n">X_transformed</span> <span class="o">=</span> <span class="n">X</span>
        <span class="k">for</span> <span class="n">feat</span> <span class="ow">in</span> <span class="bp">self</span><span class="o">.</span><span class="n">features_to_strip</span><span class="p">:</span>
            <span class="n">X_transformed</span><span class="p">[</span><span class="n">feat</span><span class="p">]</span> <span class="o">=</span> <span class="n">X_transformed</span><span class="p">[</span><span class="n">feat</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">strip</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">character_to_strip</span><span class="p">)</span>
        <span class="k">return</span> <span class="n">X_transformed</span>
</pre></div>

</div>
</div>
</div>
    </div>
  </div>
</body>

 


</html>
