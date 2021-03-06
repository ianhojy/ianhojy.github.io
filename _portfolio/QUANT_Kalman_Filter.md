---
title: "Kalman Filter (Dynamic Regression) for Algo Trading"
excerpt: "Calculating optimal hedge for long-short mean-reversion strategy"
collection: portfolio
---

<html>
<head><meta charset="utf-8" />

<title>KF_beta_EWA_EWC</title>

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
<h1 id="Kalman-Filter---Dynamic-Regression">Kalman Filter - Dynamic Regression<a class="anchor-link" href="#Kalman-Filter---Dynamic-Regression">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Reference: Algorithmic Trading by Ernest P. Chan</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The following is meant to provide a Python version of the Matlab implementation for Long-Short Mean-Reversion of ETF pairs in Algorithm Trading. In addition, I provide a supplementary section exploring the effects of hyperparameter tuning for the Kalman Filter process.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[63]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">warnings</span>
<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>One noteworthy benefit of using the Kalman filter
to fi nd β is that not only do we obtain a dynamic hedge ratio between the two
assets, we also simultaneously obtain what we used to call “the moving average”
of the spread. This is because, as we mentioned, β includes both the slope and
the intercept between y and x. The best current estimate of the intercept is used
in place of the moving average of the spread. As a by-product, it also generates an estimate of the standard deviation of the forecast error of the observable variable, which we can use in place of the moving standard deviation of a Bollinger band.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Reading-Data">Reading Data<a class="anchor-link" href="#Reading-Data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[64]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cl</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;inputData_ETF.csv&#39;</span><span class="p">,</span> <span class="n">header</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[65]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">cl</span><span class="p">[</span><span class="mi">10</span><span class="p">]</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">()</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">cl</span><span class="p">[</span><span class="mi">11</span><span class="p">]</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Plotting Cointegrated series</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[66]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">&#39;EWA&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">&#39;EWC&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Allowing for dynamic offset</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[67]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">),</span> <span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">ones</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">x</span><span class="p">)),</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">),</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Modelling">Modelling<a class="anchor-link" href="#Modelling">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Whatabout Vw and Ve? There is a method to estimate these variances from data called autocovariance least squares developed by Rajamani and Rawlings(2007, 2009).</p>
<p>But for simplicity,
we will follow Montana and assume $ω =
(δ/1−δ) * I$ where δ is a parameter
between 0 and 1, and I is a 2 × 2 identity matrix.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>If δ = 0, this means β(t) =
β(t − 1), which reduces the Kalman fi lter to ordinary least square regression
with a fi xed offset and slope. If δ = 1, this means the estimated β will fl uctuate
wildly based on the latest observation. The optimal δ, just like the optimal
lookback in a moving linear regression, can be obtained using training data.
With the benefi t of hindsight, we pick δ = 0.0001. With the same hindsight,
we also pick Ve = 0.001.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Initialization">Initialization<a class="anchor-link" href="#Initialization">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[68]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">delta</span> <span class="o">=</span> <span class="mf">0.0001</span>

<span class="n">yhat</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
<span class="n">e</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
<span class="n">Q</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>

<span class="n">R</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span>
<span class="n">P</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span> <span class="c1"># R(t|t) = P(t)</span>

<span class="n">beta</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">empty</span><span class="p">((</span><span class="nb">len</span><span class="p">(</span><span class="n">x</span><span class="p">),</span> <span class="mi">2</span><span class="p">))</span>
<span class="n">beta</span><span class="p">[:]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span>

<span class="n">Vw</span> <span class="o">=</span> <span class="n">delta</span><span class="o">/</span><span class="p">(</span><span class="mi">1</span><span class="o">-</span><span class="n">delta</span><span class="p">)</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">identity</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
<span class="n">Ve</span> <span class="o">=</span> <span class="mf">0.001</span>

<span class="n">beta</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mf">0.0</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Iteration">Iteration<a class="anchor-link" href="#Iteration">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[69]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">t</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">y</span><span class="p">)):</span>
    
    <span class="k">if</span> <span class="n">t</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">:</span>
        
        <span class="sd">&#39;&#39;&#39;State Prediction&#39;&#39;&#39;</span>
        <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>
        
        <span class="sd">&#39;&#39;&#39;State Covariance Prediction&#39;&#39;&#39;</span>
        <span class="n">R</span> <span class="o">=</span> <span class="n">P</span> <span class="o">+</span> <span class="n">Vw</span>
    
    <span class="sd">&#39;&#39;&#39;Measurement Prediction&#39;&#39;&#39;</span>
    <span class="n">yhat</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">dot</span><span class="p">(</span><span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">])</span>
    
    <span class="sd">&#39;&#39;&#39;Measurement Variance Prediction&#39;&#39;&#39;</span>
    <span class="n">Q</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">@</span> <span class="n">R</span> <span class="o">@</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> <span class="o">+</span> <span class="n">Ve</span>
    
    <span class="sd">&#39;&#39;&#39;Forecast Error&#39;&#39;&#39;</span>
    <span class="n">e</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">y</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">-</span> <span class="n">yhat</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>
    
    <span class="sd">&#39;&#39;&#39;Kalman Gain&#39;&#39;&#39;</span>
    <span class="n">K</span> <span class="o">=</span> <span class="p">(</span><span class="n">R</span> <span class="o">@</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">())</span> <span class="o">/</span> <span class="n">Q</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>
    
    <span class="sd">&#39;&#39;&#39;State Update&#39;&#39;&#39;</span>
    <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">+=</span> <span class="n">K</span> <span class="o">*</span> <span class="n">e</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>
    
    <span class="sd">&#39;&#39;&#39;State Covariance Update&#39;&#39;&#39;</span>
    <span class="n">P</span> <span class="o">=</span> <span class="n">R</span> <span class="o">-</span> <span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">K</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span> <span class="o">@</span> <span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">],</span> <span class="mi">0</span><span class="p">)</span> <span class="o">@</span> <span class="n">R</span><span class="p">)</span>
    
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Visualizations">Visualizations<a class="anchor-link" href="#Visualizations">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[70]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">beta</span><span class="p">[</span><span class="mi">1</span><span class="p">:,</span> <span class="mi">0</span><span class="p">])</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;SLOPE&#39;</span><span class="p">)</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[71]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">beta</span><span class="p">[:,</span> <span class="mi">1</span><span class="p">])</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;INTERCEPT&#39;</span><span class="p">)</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[72]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">e</span><span class="p">[</span><span class="mi">2</span><span class="p">:],</span> <span class="s1">&#39;r&#39;</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mf">0.2</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">&#39;e(t)&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">Q</span><span class="p">[</span><span class="mi">2</span><span class="p">:]),</span> <span class="s1">&#39;b&#39;</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">&#39;sqrt(Q(t))&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;PREDICTION ERROR &amp; STANDARD DEVIATION OF ERROR&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Strategy-Construction">Strategy Construction<a class="anchor-link" href="#Strategy-Construction">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[73]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">y2</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">concatenate</span><span class="p">((</span><span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">x</span><span class="p">[:,</span> <span class="mi">0</span><span class="p">],</span> <span class="mi">1</span><span class="p">),</span> <span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="mi">1</span><span class="p">)),</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The measurement prediction error e(t) (previously called the forecast error for y(t) given observation at t − 1) is none other than the deviation of the spread EWC-EWA from its predicted mean value, and we will buy this spread when the deviation is very negative, and vice versa if it is very positive.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[74]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">longsEntry</span> <span class="o">=</span> <span class="n">e</span> <span class="o">&lt;</span> <span class="o">-</span><span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">Q</span><span class="p">)</span> <span class="c1"># a long position means we should buy EWC</span>
<span class="n">longsExit</span> <span class="o">=</span> <span class="n">e</span> <span class="o">&gt;</span> <span class="o">-</span><span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">Q</span><span class="p">)</span>
<span class="n">shortsEntry</span> <span class="o">=</span> <span class="n">e</span> <span class="o">&gt;</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">Q</span><span class="p">)</span>
<span class="n">shortsExit</span> <span class="o">=</span> <span class="n">e</span> <span class="o">&lt;</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">Q</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[75]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">numUnitsLong</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
<span class="n">numUnitsShort</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[76]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">numUnitsLong</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mi">0</span>
<span class="n">numUnitsLong</span><span class="p">[</span><span class="n">longsEntry</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
<span class="n">numUnitsLong</span><span class="p">[</span><span class="n">longsExit</span><span class="p">]</span> <span class="o">=</span> <span class="mi">0</span>

<span class="n">numUnitsShort</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mi">0</span>
<span class="n">numUnitsShort</span><span class="p">[</span><span class="n">shortsEntry</span><span class="p">]</span> <span class="o">=</span> <span class="o">-</span><span class="mi">1</span>
<span class="n">numUnitsShort</span><span class="p">[</span><span class="n">shortsExit</span><span class="p">]</span> <span class="o">=</span> <span class="mi">0</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[77]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">numUnits</span> <span class="o">=</span> <span class="n">numUnitsLong</span> <span class="o">+</span> <span class="n">numUnitsShort</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Shares-Allocation:">Shares Allocation:<a class="anchor-link" href="#Shares-Allocation:">&#182;</a></h4>
<pre><code>np.concatenate((-np.expand_dims(beta[:, 0], axis=1), 
                np.expand_dims(np.ones(len(beta)), axis=1))</code></pre>
<h4 id="Dollar-Capital-Allocation:">Dollar Capital Allocation:<a class="anchor-link" href="#Dollar-Capital-Allocation:">&#182;</a></h4>
<pre><code>np.concatenate((-np.expand_dims(beta[:, 0], axis=1), 
                np.expand_dims(np.ones(len(beta)), axis=1))

                *

                y2</code></pre>
<h4 id="Dollar-Capital-in-each-ETF:">Dollar Capital in each ETF:<a class="anchor-link" href="#Dollar-Capital-in-each-ETF:">&#182;</a></h4>
<pre><code>np.repeat(numUnits[:, np.newaxis], y2.shape[1], axis=1)

                *

np.concatenate((-np.expand_dims(beta[:, 0], axis=1), 
                np.expand_dims(np.ones(len(beta)), axis=1))

                *

                y2</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[78]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">positions</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">multiply</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">multiply</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">repeat</span><span class="p">(</span><span class="n">numUnits</span><span class="p">[:,</span> <span class="n">np</span><span class="o">.</span><span class="n">newaxis</span><span class="p">],</span> <span class="n">y2</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">1</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">),</span> 
                                    <span class="n">np</span><span class="o">.</span><span class="n">concatenate</span><span class="p">((</span><span class="o">-</span><span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">beta</span><span class="p">[:,</span> <span class="mi">0</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">),</span> 
                                                     <span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">ones</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">beta</span><span class="p">)),</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)),</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)),</span>
                        <span class="n">y2</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Daily-P&amp;L-of-Strategy">Daily P&amp;L of Strategy<a class="anchor-link" href="#Daily-P&amp;L-of-Strategy">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[79]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pnl</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">multiply</span><span class="p">(</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">positions</span><span class="p">)</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">(),</span>
                         <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">y2</span><span class="p">)</span><span class="o">.</span><span class="n">pct_change</span><span class="p">()</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">()),</span>
             <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>return is P&amp;L divided by gross market value of portfolio</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[80]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ret</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">divide</span><span class="p">(</span><span class="n">pnl</span><span class="p">,</span> 
                <span class="n">np</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="nb">abs</span><span class="p">(</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">positions</span><span class="p">)</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">(),</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[81]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ret</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">nan_to_num</span><span class="p">(</span><span class="n">ret</span><span class="p">,</span> <span class="n">nan</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[82]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">cumprod</span><span class="p">(</span><span class="n">ret</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span><span class="o">-</span><span class="mi">1</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;CUMULATIVE COMPOUNDED RETURN&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;APR = {round(np.prod(ret+1)**(252/len(ret))-1,3)}&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;Sharpe = {round(np.sqrt(252) * np.mean(ret) / np.std(ret),3)}&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAXQAAAEICAYAAABPgw/pAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjMsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+AADFEAAAgAElEQVR4nO3deXxU1fn48c+TPSEkgZAAEkLYlFVUIou44C64tu5ad3/U1ta2drVat2/tV6128UtbtWpV2rovpRa17goiGhBkEwhrwhoSCNnX5/fHvRkmwySZwCSz5Hm/XvPK3HPP3PvMzcyTk3PvPUdUFWOMMZEvJtQBGGOMCQ5L6MYYEyUsoRtjTJSwhG6MMVHCEroxxkQJS+jGGBMlLKEbY0yUsITeDUTkChEpEJFKEdkuIm+KyPHuuqdF5Nc+9fNEREUkzl3eJCL1ItLPp95St16eu/yhiNzoU2e6iBR7LauIjGgn1ulunZ95lZ3gxl4pIlXu+kqvR27LvkVkkIg0ishwP9t+TUQe8oqjymc7P/N9jddrJ4nIPBHZKyJlIvK5iFzntT5DRP4iIjtEpFpElnuv7+RxfNqtV+nu6x0RGeVVf4yIzBWRchGpEJEPROS4to65V7nn9yMid7v7vNhrfVwbcVS4jxUi8r8iku71mmtFpMnnOFaKyGFe77nGff1eEflURG4SkTa/+26cte52dovIqyIy0Gv93SLS4LO/ve7nwLvM93d8Qic+oy2v2yoivxORWD/xDfYqO01ENrX1nnoKS+hdTERuBf4A/AboD+QCfwbO7+SmNgKXe213PJAcpDC9XQOUuT8BUNVPVDVVVVOBsW5xRkuZqm7xqrsVeA+4ynujItIXmAk841U8wWsbqar6oL+ARGQq8D7wETACyAS+A8xw1ycA7wJDgKlAOvBT4H73+HsL9Dg+6L7fHGAX8LRbfziwAFgODAUOA14D/uvG2RllwL3eyaqNOHoDWcB1wBRggYj08qqz0Oc4pqrqNq/157rbGALcD/wceLKD2L7nvv8RQCrwkM/6F3z2l6GqW7zL3Hrev+NPOtintwnuNk4CLgWu91lfBfyqE9vrESyhdyG3JXUvcLOqvqqqVaraoKr/VtWfdnJzc4CrvZavAZ4NVqwAIpICXATcDIwUkfyD3NQz+CR04DJgpaouP4jt/RZ4RlUfUNXd6lisqpe466/C+UN5sapudI/xW8AtOAkzzWtbnTqOqloN/BMY5xbdjZNAb1fVMlWtUNVH3O0+0Mn39RZQD3yro4qqWquqXwDn4fxBu66Dl/jbRrmqzsVJkNeIyLgAXrMXeB04qrP7CwZVLcT5A+q7/0eAy6Wd/zZ7IkvoXWsqkITTgjtUnwFpIjLabdFdCvw9CNv1diFQCbwEvE3rxNcZrwH9xO1Wcl3FQfwBcv/ITAVebqfa6cCbqlrlU/4KzvH3bjl36jiKSCpwJfCl175e8lP1RWCaG2+gFKeVeZeIxAf0AtUK4B3ghE7sx3cbnwPFgWxDRDKBbwKFB7u/Q+F2dZ3gZ/9bgb/i/IE1LkvoXSsT2K2qjUHaXkvr8nTga5wPdTBdg/OvdBNOq/TyQBONN1WtwUl6VwOIyEhgortNb0vcvteWx5l+NtcH53O6vZ1d9vO33j3uu9313gI5jj8Rkb04iSQVuLa9fbllMW68AXNbzCXAjR3V9bIN6Ou1PMXnOK4/iG34ekREytl//L7vs/4Sn31+0In4A7FERKqA1cCHON2Uvv4XOFdExvpZ1yNZQu9apTgt1bh26jQCvkkzHmh2H97mAFfgJBd/rd22ttXQUaDuCaaTgX+4Rf/Cad2e3dFr2/AMzpc+Cad1/paq7vKpc4zb99ryeNvPdvbgHIeBfta12O1vvXvc+7nrvXV0HAEecmMaoKrnqWpLkvS7L7es2Y3X3+8B2v5d3AHcjnO8AzEIp/+9xWc+x/GAE9IBbMPXLaqaDhyJ80cqx2f9iz77PDnA2AP9jB6D84f0UmAy0MtnPapaAszG6dY0WELvaguBWuCCdupsAfJ8yoYCRaraKqGr6mack3ozgVc7sa3NAcR6Fc7n4d8isgPYgJNgDqrbxT0BVopz8vdbHGR/v9uHvRCnO6gt7wIzfE4U4r6mDqebxXubHR3H9rwLXOyn/BKcvvVqnN9DP7e7BgAREZyTkgf8LlT1HZz/BL7b0c7dbZ4GdOYEo+82jsVJ6PM7quue8/g18Cf3PRyqgD+j7rmSF3F+/3e2sb3f4jREJgYhtohnCb0LqWo5zgfxTyJygYikiEi8iMwQkZYrOl4BzhaRM0Qk1r3c7A7g+TY2ewNwip/+YoAXgOvEucRPRORw4Ed+tpUgIklej1icxH0PzsmnlseFbmyZB3kInsU5UZgB/PsgtwHwM+BaEflpSywiMkFEWt7XHJw+4ZfEueQz3u2+eQS42/09+GrvOLbnHuA4EblPRPqKSG8R+T7O8fs5gHvVzyLgARFJFZFEnKtuGvH54+Lldvd9+iUiiSIyEecE5R7gb52MGxFJE5FzcD4Pf+/ECepngGycE7KHKtDPqLf7gVkiMsB3hXvS9mHaOXY9iqrao4sfOCfVCnAutdoB/Ac4zmv9ucBioBynpfJbINlr/SbgND/bjcM5sZbnVXY9sBLYh9Pq+wUQ47Ve/TzuwPlPIsvPPlbiXMLWspznvibOp96HwI0+ZUNxuiH+4me76h6PSq/HH9o5hpOAN91jVIaTMK/2Wt8XeAzYCdS4cfvGE9BxxLlE8dftxDIOeMM9xpXuez/ep85gnPMIO3C6ad4GxnitvxsnqXq/Zp6fOOqBCvdYrcT9A+n1mmuBJp/jWAkc6/Wea9xtlOO0dm8GYtt5f/5+lz8HCrxib/Czz2w/v+MRfrYfyGd0hM9r3gQe9hcfTtfMLmBTqL/roX6Ie0CMMcZEOOtyMcaYKGEJ3RhjooQldGOMiRKW0I0xJkq0d8NLl+rXr5/m5eWFavfGGBORFi9evFtVs/ytC1lCz8vLo6CgIFS7N8aYiCQibd4oaF0uxhgTJSyhG2NMlLCEbowxUcISujHGRAlL6MYYEyUsoRtjTJSwhG6MMVEiZNehG2NMJKipb+KpBRupa2iif3oSV0zKJThzfQSfJXRjjGnHK0uK+e3bazzLby7fwd3njWFEdu8QRuWfdbkYY4wfNfVN3P7acu54fQWpiXGsuOdMThjZj/mFu3lpcXGow/PLEroxxvj4csseRt/5Fv9YtAWAaSMySU2MY84NkxmUkcw/P9tCU3P4TQ5kXS7GGONSVZ7/oohH3lvnKfv6f84iKT7WszxxSB/mLtvGz17+iocvmQA4rfmlRXtbpsQjIS6GY3L7EBPTvX3tHSZ0EUkCPgYS3fovq+pdPnUScSYEnogz0/ulqrop6NEaY0wXWrx5D7e9un/u7Pu/Ob5VMgd4+JIJvLliO68sKebEw/sx/YhsHnp7DXM+O3DMrMxeCZ7nWb0T+dU5Y2hqVk483O9giYcskBZ6Hc7s6JUiEg/MF5E3VdV79vIbgD2qOkJELsOZyPbSLojXGGO6zNqdlQB8+JPp5PZN8dvCjo+N4dcXjOPnryznB88v9ZSPGtCbe84bC8DSor0U7an2rPt0fSlf76jgyicWAfDxT08mNzMl6PF3mNDV+R+i0l2Mdx++nUfn48wEDvAyMFtERG0GamNMBNmxrxYRGNQnud3ukkuPzaVPSgKz5ixm0tC+XHjMIKYMy2RIZi8AJg/LbFW/qVlZWrSHB99aw6KNZazZWRGahA4gIrHAYmAE8CdVXeRTZRBQBKCqjSJSDmQCu322MwuYBZCbm3tokRtjTJDtKK+hX2oi8bEdXy9yxtgBLLvrDNKT4zusGxsjTBzSl6evm8S0B95n4fpSTh/TPxghtxLQVS6q2qSqRwE5wCQRGedTxd+fsgNa56r6uKrmq2p+VlbX9CEZY0wgVJVte2toaGoGnP7zFwuKGZieFPA2Aknm3pITYpn7vWn86pzRnXpdoDp1lYuq7hWRD4GzgBVeq4qBwUCxiMQB6UBZsII0xphgKa2so6quiSVb9vDDF5YSI/DLmaP59X9WA3DZsV3be5DTJ/hdLS0CucolC2hwk3kycBrOSU9vc4FrgIXARcD71n9ujAk39Y3NXPDnBRSV1TAhJx2AZsWTzAGumBy53cGBtNAHAs+4/egxwIuq+oaI3AsUqOpc4ElgjogU4rTML+uyiI0x5iB8sGYX3/n7YmobnC6WZcXlDM/qhQIbSqpCG1yQBHKVy1fA0X7K7/R6XgtcHNzQjDEmeF7/ciu1Dc38cuYoeiXGsWhDGRccfRgA1z8dHRPW252ixph2VdQ2kJIQR6zXZXyFuyrZUlbFsXl96Z3UuRODobJrXx35Q/ow68ThAFw5eYhn3cb/ncmMP37ClRHc3QKW0I3pMeZ8tpmNJVVcf3weOX1SPLeptzcUbG1DE+Pv/i83HD+UW08/nMc+3sDcpVvZVOrcNPPtk4Zx24yOr9iobWhi1fZ9qEJ6chwjsnvz0doSBqYncXj/7hm1cE91fZsnJEWEt354YrfE0ZUsoRvTQ/zqdefCtLU7K5hzwySG3jaP66cN5c5zx/it/9HaEr4q2gvAk/M3sqe6nleXbAXg2ycO47GPN7CjvDagfd/64lLmLd/hWT5ueCafri8F4OwjB6KqDEhL5o6zR3fZ+CflNQ2MHxQZ/00cLEvoxvQw8wt3c8ljCwF4asHGVgn947Ul/GbeajaVVnlOHrZ4dclW+qcl8uYPTqRvrwQWbSxjQWEprywuZsLgDEZkpx6wr7rGJj5dX0rBpj2MH5TO9cfn8aMXlnmSeWavBFZv30dtfRPbynfw1IKN3HLKCG4944igv+891fVkpFhCN8ZEON+riL/YtOeAOi8VFPHTl78C4JwjB9I/LYnjhmfy0doSEuNiGDconWPz+tLXHXDquOGZ/PnD9fz4pWUAnDoqm693VHD5pMHcfPIItpfXct7s+eyurAfgqilD+MbROQxMT6ahqZnjR/TzdPfsrqzjh88vZX7hbh55v5D/+6AQVRiUkcxjV01k3KB0T5wlFXXc8++V/PqCcaQmxvHS4mIuPCaHhLgY6hubiYuRVq38C//yKSeOzKK2oZmMlP2DZUUjS+jG9ABvrnC6O4ZkprC5tLrVuk/WlXDCyCxeLCgC4MELj+SSYwd71p862v8t6j87axRXTR3Cu6t2MuezzWwqrWLr3hoe+u9ayqoaeGVJMeU1DQzKSObxqyd6+sqn+IxzAtAvNZG/3ziZSx5dyOebyjg2ry+fbyxj694aPl5X0iqh3zV3BfOW72De8u20DEl++2vLmfeDEzjrD59w4/FDueMc578OVWXx5j0s3uz8AcvqnXgwhy9iSKju/8nPz9eCgui4VMiYcPd/763j4XfW8vkvT2XSb94D4JHLj+aW577kiP69OXlUNq9/uZXUpDjevfWkg97P6u37mPHHTzzLEwZn8Oz1kwK+Rb6qrpGq+kbmLt3mudlnQFoSxwzJ4JZTR3LXv1ayaKNzE/pJh2fx0doSv9t550cnsruyntkfrGNBYamn/LXvHsfRuX0O9u2FBRFZrKr5/tZZC92YHqCyrpHEuBiy05K44+zR9EtN5LwJh7Fq2z4e/Wg9a3ZWkJ4cz40nDD2k/YwemMa/bp5GWVU9Rw3OICMlvlMTKvdKjKNXYhzD3f747N6JNDY3uy3y/SdVfzFjFDedNJyd+2rZXFrN7so6Fq4v9YxJfvrvP/a7fX/9/NHEWujGRKivivc6yS+r4yR1+2vLeXvlDgruOP2AdWVV9ezcV8sR/Xt3+ww77flwzS6OH9EPBa7462d8sWkPh6UnMf/np7QZZ3lNA59vLKOusYn6xmZGD0xj9MA0yqsbWLurgmPz+nbvm+gC1kI3JgqdN3sBALOvOJr+aUlkpSaSkuDMrpOWHO+Zaae+sZmvd1SQmuj/6963V4LnRGc4mX5Etuf5Szcdx77aBpLiYtv9o5OeHO93WNr0lPioSOYdsYRuTARZt7OCZxduZlnxXk/Z9/755QH1YmOECTnpiIjnhOCROekH1IskaRFyR2ooWUI3JoI8/N+1vLVyxwHl3zt5BDl9kmlSZW91A19u2UNtQzO7K+s8dS7OH3zA60x0sYRuTJhas6OCrXurOfmIbEqr6rnvP6t5a+UOThudzX3fGE9tQxMARWU1HD+yn99tlFTU8cvXlnNsXh+umjLEbx0TPSyhGxOGFm0o5Zbnv2TnvjruOHs0+2obee3LrUwe2pfrpw2lf9r+WXVa5rH0J6t3In+92u/5MxOFLKEbE2ZWbivn0sc/8yy3XI+dl5nCC9+eGqqwTAQIaE5RY0z3qG1o4sK/fArAo9+ayHemD/es+803x4cqLBMhrIVuTBhZWrTXMyjW9COyOGvcAI4anMEJI/uRkmBfV9M++4QY0wWq6xv5YtMequsamTF+YIf1m5sVBTaX7p8KreU68jPHDuiqME2UsYRuTJAVlVVzwoMfeJbfvfUkRmSn8vbKHQzP6sWI7NYTOjz09hpmf1CICPRyW+Gf//LUbo3ZRAdL6MYE2ZodFa2WV2/fx7B+vfj2nMUkxMaw9r4ZnnVVdY3M/qAQgPMnHEZlXRNH5qST7XUVizGBsoRuTBDd++9VPLVgY6uy7z/3JYdlJANQ3+T0j7+1Yjs/e/krrpvmDIb1P+eP5aqped0aq4k+ltCNCSLvZC4CA9OS2FZe67lyBeCR99bxu3fWAvDH99YBRP3EC6Z7WEI35hDUNTYxZ+Fm1u6sILdvimeuzJMOz+KZ6yehqgy9bV6r17Qk85tOGs6jH60HoHeSfRXNoevwUyQig4FngQFAM/C4qv7Rp8504F9AS/PkVVW9N7ihGhN+Pi0s9dz402LaiEyeuX4S4Mwm/+sLxnGHO0Fzi5YTpTPHD+C91buYNDT6RwI0XS+QZkEj8GNVXSIivYHFIvKOqq7yqfeJqp4T/BCNCV8tg1/dc95Y7pq7EnCmU/M2MN05wXl4/1S+NWUIp4zKJqdPCgBH5mRwZE5GN0ZsolmHCV1VtwPb3ecVIrIaGAT4JnRjepyyKmcC5Asn5jBj3ADW7apk7GFpreq0jN89ID2Zq+3Ep+lCneq4E5E84GhgkZ/VU0VkGbAN+ImqrvTz+lnALIDc3NzOxmpM2NlQUkVmrwRSE+NITYzze7lhSwt9QoSPR27CX8BjuYhIKvAK8ENV3eezegkwRFUnAP8HvO5vG6r6uKrmq2p+VlbWwcZsTLdqbGrmzx8Wsq+2oVX5J+tKeKGgiD4dzPYzakAab3z/eH5w6siuDNOYwBK6iMTjJPN/qOqrvutVdZ+qVrrP5wHxIuJ/gGZjIsy7q3fy4FtrePjtNa3Kr3rycwBOaGMscm/jBqUTF2tj4Zmu1eEnTJwpu58EVqvq79qoM8Cth4hMcrdbGsxAjQmVXRXOic+9Nftb6J+sK/E8//lZo7o9JmP8CaQPfRpwFbBcRJa6Zb8EcgFU9VHgIuA7ItII1ACXqap2QbzGdLuNu50BsxLcFnZjU7OndX7GmP6eQbSMCbVArnKZD7Q9zbZTZzYwO1hBGRNOyqudlvme6gb+tXQr1fVNnnW/v/SoUIVlzAHs9jRjOlBZ1wg4fenvrt7pKb/r3DH0SrSvkAkfdpbGmA5U1Tf6Lbcbgky4sYRuTAf21fhP6Nm9E/2WGxMqltCNaceiDaUs31rO0bn7W+NXTRkCwCB3SFxjwoUldNNj1DU2sby4POD6O8prufTxzwC4feZoT/m9549lw29mem7pNyZcWEI3PcaT8zdy7uz5LN5c1mHdusYmzp0937Ocn7d/NEQRsWRuwpIldNNjFJXVALBqm+/IFQdasnkvJe4NRTPH2yTNJjJYQjc9RkqCcwNQRZ3/k5zeKr3q/O4Su9bcRAa7iNb0GJ+ud0ajaGl5t6d4T7XnecudoAV3nNb+HXbGhJgldNMjqCo799UCbSf0orJq3v96F8OyenHPv53h/m+bsX+cFt+JK4wJN5bQTY9QVd/kmYxiVxsJ/ZqnPmfD7iomu9PB3Xv+WJuQwkQU60M3PcLj7mTM4L+F3tjUzAZ3EK5FG8s4YWQ/S+Ym4lhCNz3CMws3A5CWFMcut+vF27a9+8vSk+M5ZVR2t8VmTLBYl4uJer9+YxXl7ljmN00fzoNvraGqrrHVwFq7KpyE/vR1xzL9CEvmJjJZC91EtbrGJp6Yv9Gz3L+3M7+nbz96SzdMdu8D5wQ1JlJYQjdRrba+udVydppzpYpvt0tJpZPQs2zALRPBrMvFRLXaRmcyijvPGcNF+Tlsd/vKWxI4ODMS3fef1QD07WDCZ2PCmbXQTVSra3Ba6GnJ8aQlxXuGvP1i4/7xXL71xCLqGp16sTZGi4lgltBNVKtzW+hJ8c5HPSMlHth/1UtTs7J1rzPGS8vQAMZEKkvoJqq1zP+ZGOckaxHh7CMHAs7do//zhnNH6K2nH86SX50emiCNCRJL6CaqvbPKmQM0PTneUzb2sDQA6hqbWeiO7zJ1eKZnzBZjIpUldBO19lbXM/uDQnonxpE/pI+nPFacfvIbnylgd2UdE3LSOdZrvHNjIpUldBO1vtyyF4ALJ+a0mpCieI/TZz6/cDelVfVkp9m15yY6dJjQRWSwiHwgIqtFZKWI/MBPHRGRR0SkUES+EpFjuiZcYwLz6pJi3lntdLdce1xeq3U3nzyi1fIAS+gmSgTSQm8Efqyqo4EpwM0iMsanzgxgpPuYBfwlqFEa00m3vriMfy7aAkAfn2vLB6Qn8cnPTua8CYcBNiyuiR4dJnRV3a6qS9znFcBqYJBPtfOBZ9XxGZAhIgODHq0xAfCebSg2RkhLOvD+ucF9U+jjXsLYK9FOhpro0Kk+dBHJA44GFvmsGgQUeS0Xc2DSR0RmiUiBiBSUlJR0LlJjAvT851s8zzOS4xHxf7NQZZ1zSWNqot0wbaJDwAldRFKBV4AfqqrvLLv+vjF6QIHq46qar6r5WVlZnYvUmAC1TGQBEB/b9kf8jLH9Aci3K1xMlAioaSIi8TjJ/B+q+qqfKsXAYK/lHGDboYdnTOft8Bp46xdeU8j5OnPsANb/Zqbd7m+iRiBXuQjwJLBaVX/XRrW5wNXu1S5TgHJV3R7EOI1pU3lNA4ff/iYfrXW68V5dshWAXgmxHDU4o93XWjI30SSQFvo04CpguYgsdct+CeQCqOqjwDxgJlAIVAPXBT9UY/zbUlpNfVMz9/1nFScdfpKnfMU9Z7bZf25MNOowoavqfPz3kXvXUeDmYAVlTGc8u3ATAEVlNRSVVXvKLZmbnsbuFDURraismpcWFwNQ09DECQ9+AMD3TxnR3suMiUqW0E1EO/MPH/stz7SJKkwPZAndRLSW4XEB7jh7tOe5dbeYnsgSuokaw7NTee7/TQHguOGZIY7GmO5nt8iZqDEyO5WcPilsuv/sUIdiTEhYC91ErKbm/TcjP3jRkeT0SQlhNMaEniV0E7EueWyh57nNNmSMJXQToYrKqlm8eY9nOdVGTDTG+tBNZCqprAPgnvPGsruyjpMOzw5xRMaEniV0E5Gq3aFvRw3ozeRheaENxpgwYV0uJiJV1zuTWPSyscyN8bCEbiJSyw1FKQnWd25MC0voJiJVWQvdmANYQjcRqaUP3VroxuxnCd1EpP1dLtZCN6aFJXQTkbbtrSEuRmzGIWO8WEI3Eae2oYkXCopIT44PdSjGhBVL6CbiXPTopwBcPTUvtIEYE2YsoZuIs2LrPgBOOLxfiCMxJrxYQjcRq7ddsmhMK5bQTcTK69cr1CEYE1YsoZuIsmZHBQDDsnoRH2sfX2O8dfiNEJGnRGSXiKxoY/10ESkXkaXu487gh2mMY2mRM2TuhpKqEEdiTPgJpBPyaWA28Gw7dT5R1XOCEpEx7bAbiYxpW4ctdFX9GCjrhliM6VCMODcS/eXKY0IciTHhJ1idkFNFZJmIvCkiY4O0TWMO0DJs7tjD0kMciTHhJxj/vy4BhqhqpYjMBF4HRvqrKCKzgFkAubm5Qdi16Um2l9fw05e/AiA1ybpejPF1yC10Vd2nqpXu83lAvIj4veNDVR9X1XxVzc/KyjrUXZsepuVE6Olj+tO3V0KIozEm/BxyQheRASJOx6aITHK3WXqo2zXGV8sIi7ec4vcfQGN6vA7/bxWR54DpQD8RKQbuAuIBVPVR4CLgOyLSCNQAl6mqdlnEpsdq6T9PtjHQjfGrw4Suqpd3sH42zmWNxnSplhZ6r0RL6Mb4Y7famYjhmdQi3k6IGuOPJXQTMarrrMvFmPZYQjcRo7qhifhYISHOPrbG+GPfDBMxqusaSY631rkxbbGEbiJGdX0TvWwMdGPaZAndRIzqhibrPzemHZbQTcSormskxRK6MW2yhG4iRnV9kw2fa0w7LKGbiLGlrNpa6Ma0wxK6iQg7ymvZXl5LenJ8qEMxJmxZQjcRYX1JJQAzxg0McSTGhC9L6CYi1DY4t/0PTE8KcSTGhC9L6CYi1DU2A5AYbx9ZY9pi3w4TEeoanRZ6UpydFDWmLZbQTUSobbAWujEdsW+HiQh1DdZCN6YjltBNRNhdWU9sjNjk0Ma0wxK6iQhbyqo5LCOJ+Fj7yBrTFvt2mIhQVddI70S7qciY9lhCNxGhqr7R5hI1pgOW0E1EqKlvItkG5jKmXZbQTUSorm8ixWYrMqZdltBNRHCGzrWEbkx7OkzoIvKUiOwSkRVtrBcReURECkXkKxE5Jvhhmp6uxmYrMqZDgbTQnwbOamf9DGCk+5gF/OXQwzKmtep6m63ImI50mNBV9WOgrJ0q5wPPquMzIENEbIxTEzTNzUptQ7PNVmRMB4LRhz4IKPJaLnbLDiAis0SkQEQKSkpKgrBr0xPUuLf9WwvdmPYFI6GLnzL1V1FVH1fVfFXNz8rKCsKuTU9QXW8J3ZhABCOhFwODvZZzgG1B2K4xgHMNOmDXoRvTgWAk9LnA1e7VLlOAclXdHoTtGgNAdUMjYC10YzrSYZNHRJ4DpgP9RKQYuAuIB1DVR4F5wEygEKgGruuqYE3PVFVnXS7GBKLDhK6ql3ewXoGbgxaRMV5Uld+/sxbArhjiEc4AABEJSURBVHIxpgN2p6gJa+tLKplfuBuwFroxHbGEbsJaUVmN57ndKWpM+yyhm7D1UkER1z39hWfZWujGtM8SuglbLxYUtVpOttEWjWmXJXQTtraX13qezxg3gLQkm7HImPbYZQMmLDU3Kzv31XLxxBxOHpXNzPE2PJAxHbEWuglLm8uqaWhSJgzOsGRuTIAsoZtusaGkknP+7xPyfvEfXl1SzLa9NTw5fyPV9Y0H1FVVfvziUgAmDe3b3aEaE7Gsy8V0GVVlW3ktmb0SOOsPn1Df1AzArS8u89T54OtdzLlhEiL7x3j7qricJVv2ApDbN6V7gzYmglkL3XSZO/+1kmn3v8+oX71FfVMzx+RmEB8rnH/UYZ468wt3M/S2eVz5xGds3F0FwKbSKs/6JLuyxZiAWQvdBIWqsqe6gb69EjxlC9w7PFs8dPEEhmWlAvDtE4cz85FPvOqW8vjHG5g0tA9vLHPGdhN/AzMbY9okzlAs3S8/P18LCgpCsm8TfE8v2Mjd/17F9dOG8s1jBtGsyjf//CnfPmkY04/IZnCfFAakJ7V6za6KWk596CNy+qawevu+A7a5+t6z7O5QY3yIyGJVzfe3zlroJijeX+PMQPXUgo08tWCjp3z0wDSOzfN/YjO7dxLL7zkTgB+/uIxXlhRz9viBrNtVQWOzWjI3ppMsoZtOq6prJCEuhvjY/adgYgUyUuLZW90AwAMXjmdEdipHDe4T0DYfvOhI7vvGOOszN+YQWEI3AftgzS4e/2gDCzeUctrobL578ggSYmMYNyidsuoGxg9K53snj2Bp0V4uPTa3U9uOjRFiYyyZG3MoLKGbgJRV1XPd3/YPlPXu6l28u3oXAH17JVBWVc8Vk3OZPCyTycMyQxWmMT2aXbZoDlDf2Mw7q3bS1KxU1DZw05zF3PyPJZ71U4Y5feK9E532QFlVPQD9vK5wMcZ0P2uhmwOc+OAH7NhXy8jsVK6dlsdbK3d41r1001Sq65sorVzFD04bSf6Qvjz+8QZ2VdRy7bShIYzaGGMJ3RygpsGZw3Pdrkpuf22Fp3xkdqrnipWTbj3JU37nuWO6N0BjjF+W0E0rTc1KeU3DAeWvfGcqg/vYbfjGhDNL6D1YbUMTcxZuJj05nkuOHQzAZxtKD6h324xRTBxig2QZE+4sofdg//lqO/fNWw3AGWP7k5YUz98WbCQpPoald57B1zsqWLVtH5e5yd4YE94soUexusYmFm0oY+KQPuypricjJYFU98qUd1ft5Mcv7R/18Kh73/E8T02MIyk+lqMGZ3DU4Ixuj9sYc3ACSugichbwRyAWeEJV7/dZfy3wW2CrWzRbVZ8IYpzGVdvQREJsDJX1jX6nZKuqa2R9SSXjB6Xz7TmL+dC9JR/gxMOzePb6SVTXN3Ljs844Or/5xnjmF5aQlZpIckIccxZu4uFLJnTX2zHGBFGHCV1EYoE/AacDxcAXIjJXVVf5VH1BVb/XBTH2SAsKd7NuZwXHj8zitS+LWbezkvUllawv2T+0bGpiHLOvOJrpR2QD8Gnhbq54YhEAt5w60pPMr5uWx7MLN/Px2hJOffhDhrsjHvZJieeKyblcMXn/XZ2/mDGqu96iMSbIAmmhTwIKVXUDgIg8D5wP+CZ0EwQrtpbz7MJNvFhQ3Ko8PTmegT6jFVbWNfKvpds8Cf0nXl0oj7y3DoAXZk1h8rBMTh/Tnyv+uoj1JVWePwrPXj+5C9+JMaa7BZLQBwFFXsvFgL9McKGInAisBX6kqkW+FURkFjALIDe3c2N99AQVtQ2cN3s+ze6IxkfnZpAYF8PZRx7GtybnIiIU7qpk5h+d2X+GZfXik3W72bWvlq93VLCtvJafnzWK00Zns3VvDTl9kj2t8SlDM/nNN8bTPy2RIZkpLN9azrhBaSF8t8aYYOtwPHQRuRg4U1VvdJevAiap6ve96mQClapaJyI3AZeo6intbbcnjode39hMQ1MzlXWNPPbRBj5dv5tNpVUMTE+moraBZnVuo7//m+M5ZVQ22WlJ7W5v1rMF/HfVTo7MSWdPdT3b99by+e2ntZpkwhgTXQ51PPRiwPu6tRxgm3cFVfW+ePmvwAOdDbInuOW5L1vdRj+0Xy/iYmI8U6+1OO+ow0hJ6PhXc9HEHP67aidfFZcDMPawNEvmxvRggST0L4CRIjIU5yqWy4ArvCuIyEBV3e4ungesDmqUEW5PVT1fFu1plcyvmTqEe84fB0BNfRPNqjz/RRHpyfEBJXOAM8YO4IVZU7j+6S+oqm/i/m8e2SXxG2MiQ4eZQ1UbReR7wNs4ly0+paorReReoEBV5wK3iMh5QCNQBlzbhTFHnFue/5JP1jnza9500nB+eNrIVhM5tMzMc8PxnR/cavKwTFbee1ZwAjXGRLSAmoKqOg+Y51N2p9fz24Dbghta9Fi6ZS8A1x6Xx5WTc21WHmNMl7A7RbvYog2lVNQ1csspI7j1jCNCHY4xJorZBBdd7LUvnZtnzxw3IMSRGGOinSX0Lla8p4ajBmcw9rD0UIdijIlyltC7WFlVPZl2KaExphtYQu9ie6rr7dpwY0y3sITehVSV0ipL6MaY7mFXuQRBc7Pyk5eWkRgfy20zRxEjwsqt5Vz6+GcA9LGEbozpBpbQD0JVXSMpCbGICP9duYPZHxR6br9/7vMtB9Q/fkS/7g7RGNMDWULvpMJdFZz2u4/Jy0zh95cexaw5iwE4Mied9OR4Vm7bR1VdI0nxsdw+czQXHD2IhDjr2TLGdD1L6J1Q39jMLc8tBWBTaTXf+POnAMy5YRInjMwKZWjGGGMJPVBf79jHj19cxqrt+/jx6YczdXgm76zaSbMqxw23LhVjTOhZQg9AfWMz5zwyn8ZmJX9IH26aPpz42Bjy8/qGOjRjjPGwhN6BJVv28E23a+Wuc8dw3bTOj4hojDHdwc7WtaO0ss6TzMcNSuPKyUNCHJExxrTNWujteG/1LgDOOXIgs684JsTRGGNM+6yF3o6iPdXECPz+0qNCHYoxxnTIEno7isqqGZieTHysHSZjTPizTNWGTburmLd8B3n9UkIdijHGBKTH9aHXNTaREBuDiABQUdvA1r01zF26jeVby7nvgvGkJccx/aEPAewac2NMxOgRCf3vn23mjtdX8LfrjuWeuSvZureG5PhYZo4fyPNfFLWq+5OXlrFymzMuy7CsXnx3+vBQhGyMMZ0mqhqSHefn52tBQUHQt9vUrMTGCDv31fL850VU1DbwxPyNreokxsVQ19gMwKgBvbloYg5Li/aiCv9Zvh2AY3IzePW704IenzHGHAoRWayq+f7WRU0LvaGpmdtfW86LBcWMGZjGqu37Wq0/on9vcvokMyI7lV/MGMWWsmrSk+NJT473dL80NytXTsnli417+O7J1jI3xkSWiE/oTy/YyJsrdrBoY5mnLKt3ItN6ZbKgsJSrpgzhJ2ccQXpKfKvXDcnsdcC2YmKE44b3s35zY0xECiihi8hZwB+BWOAJVb3fZ30i8CwwESgFLlXVTcEN9UDby2u4+9+rPMvXTxvKj04fSe+k+HZeZYwx0anDhC4iscCfgNOBYuALEZmrqqu8qt0A7FHVESJyGfAAcGlXBAzwzKebeGL+BorKagC4cnIuvzpnDEnxsV21S2OMCXuBXIc+CShU1Q2qWg88D5zvU+d84Bn3+cvAqdLSMR1kS7bs4a65Kz3JfMa4Adz3jfGWzI0xPV4gXS6DAO9r+4qByW3VUdVGESkHMoHd3pVEZBYwCyA3N/egAlZVJg3tyxPX5JNmXSvGGOMRSAvdX0vb91rHQOqgqo+rar6q5mdlHdwMPxOH9OXFb0+1ZG6MMT4CSejFwGCv5RxgW1t1RCQOSAfKMMYY020CSehfACNFZKiIJACXAXN96swFrnGfXwS8r6G6Y8kYY3qoDvvQ3T7x7wFv41y2+JSqrhSRe4ECVZ0LPAnMEZFCnJb5ZV0ZtDHGmAMFdB26qs4D5vmU3en1vBa4OLihGWOM6QwbPtcYY6KEJXRjjIkSltCNMSZKWEI3xpgoEbLx0EWkBNh8kC/vh89dqGHIYjx04R4fhH+M4R4fWIydNURV/d6ZGbKEfihEpKCtAd7DhcV46MI9Pgj/GMM9PrAYg8m6XIwxJkpYQjfGmCgRqQn98VAHEACL8dCFe3wQ/jGGe3xgMQZNRPahG2OMOVCkttCNMcb4sIRujDFRIuISuoicJSJrRKRQRH4RohgGi8gHIrJaRFaKyA/c8r4i8o6IrHN/9nHLRUQecWP+SkSO6cZYY0XkSxF5w10eKiKL3BhfcIdERkQS3eVCd31eN8WXISIvi8jX7vGcGk7HUUR+5P6OV4jIcyKSFOpjKCJPicguEVnhVdbpYyYi17j114nINf72FeQYf+v+nr8SkddEJMNr3W1ujGtE5Eyv8i75vvuLz2vdT0RERaSfuxySY3hQVDViHjjD964HhgEJwDJgTAjiGAgc4z7vDawFxgAPAr9wy38BPOA+nwm8iTOz0xRgUTfGeivwT+ANd/lF4DL3+aPAd9zn3wUedZ9fBrzQTfE9A9zoPk8AMsLlOOJMrbgRSPY6dteG+hgCJwLHACu8yjp1zIC+wAb3Zx/3eZ8ujvEMIM59/oBXjGPc73IiMNT9jsd25ffdX3xu+WCcocI3A/1CeQwP6n2FcucH8UuYCrzttXwbcFsYxPUv4HRgDTDQLRsIrHGfPwZc7lXfU6+L48oB3gNOAd5wP5C7vb5UnuPpfoinus/j3HrSxfGluQlTfMrD4jiyf67cvu4xeQM4MxyOIZDnkyw7dcyAy4HHvMpb1euKGH3WfQP4h/u81fe45Th29ffdX3w4k9xPADaxP6GH7Bh29hFpXS7+JqweFKJYAHD/rT4aWAT0V9XtAO7PbLdaqOL+A/AzoNldzgT2qmqjnzhaTfQNtEz03ZWGASXA39xuoSdEpBdhchxVdSvwELAF2I5zTBYTXsewRWePWai/S9fjtHppJ5ZujVFEzgO2quoyn1VhEV8gIi2hBzQZdXcRkVTgFeCHqrqvvap+yro0bhE5B9ilqosDjCMUxzYO59/ev6jq0UAVTndBW7o1Rrcf+nycboDDgF7AjHZiCKvPp6utmEIWq4jcDjQC/2gpaiOWbotRRFKA24E7/a1uI46w+31HWkIPZMLqbiEi8TjJ/B+q+qpbvFNEBrrrBwK73PJQxD0NOE9ENgHP43S7/AHIEGcib984QjHRdzFQrKqL3OWXcRJ8uBzH04CNqlqiqg3Aq8BxhNcxbNHZYxaS75J74vAc4Ep1+ynCJMbhOH+4l7nfmRxgiYgMCJP4AhJpCT2QCau7nIgIzjyqq1X1d16rvCfLvganb72l/Gr3bPkUoLzl3+Ouoqq3qWqOqubhHKf3VfVK4AOcibz9xditE32r6g6gSESOcItOBVYRPsdxCzBFRFLc33lLfGFzDL109pi9DZwhIn3c/0TOcMu6jIicBfwcOE9Vq31iv8y9SmgoMBL4nG78vqvqclXNVtU89ztTjHPhww7C6Bh2KJQd+Ad5ImMmzlUl64HbQxTD8Tj/Wn0FLHUfM3H6S98D1rk/+7r1BfiTG/NyIL+b453O/qtchuF8WQqBl4BEtzzJXS501w/rptiOAgrcY/k6ztUCYXMcgXuAr4EVwBycKzFCegyB53D69BtwEs8NB3PMcPqxC93Hdd0QYyFOn3PLd+ZRr/q3uzGuAWZ4lXfJ991ffD7rN7H/pGhIjuHBPOzWf2OMiRKR1uVijDGmDZbQjTEmSlhCN8aYKGEJ3RhjooQldGOMiRKW0I0xJkpYQjfGmCjx/wGQGehMqzGRlQAAAABJRU5ErkJggg==
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>APR = 0.262
Sharpe = 2.362
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Varying-delta">Varying delta<a class="anchor-link" href="#Varying-delta">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[114]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">delta</span> <span class="ow">in</span> <span class="p">[</span><span class="mf">0.99999999</span><span class="p">,</span> <span class="mf">1e-5</span><span class="p">,</span> <span class="mf">1e-6</span><span class="p">,</span> <span class="mf">1e-7</span><span class="p">,</span> <span class="mf">1e-8</span><span class="p">,</span> <span class="mf">1e-12</span><span class="p">]:</span>
<span class="c1"># for Ve in [0.001, 0.01, 0.1, 0.5, 0.9, 1]:</span>

<span class="c1">#     delta = 0.001</span>
    
    <span class="n">yhat</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
    <span class="n">e</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
    <span class="n">Q</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>

    <span class="n">R</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span>
    <span class="n">P</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span> <span class="c1"># R(t|t) = P(t)</span>

    <span class="n">beta</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">empty</span><span class="p">((</span><span class="nb">len</span><span class="p">(</span><span class="n">x</span><span class="p">),</span> <span class="mi">2</span><span class="p">))</span>
    <span class="n">beta</span><span class="p">[:]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span>

    <span class="n">Vw</span> <span class="o">=</span> <span class="n">delta</span><span class="o">/</span><span class="p">(</span><span class="mi">1</span><span class="o">-</span><span class="n">delta</span><span class="p">)</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">identity</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
    <span class="n">Ve</span> <span class="o">=</span> <span class="mf">0.001</span>

    <span class="n">beta</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mf">0.0</span>

    <span class="k">for</span> <span class="n">t</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">y</span><span class="p">)):</span>

        <span class="k">if</span> <span class="n">t</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">:</span>

            <span class="sd">&#39;&#39;&#39;State Prediction&#39;&#39;&#39;</span>
            <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>

            <span class="sd">&#39;&#39;&#39;State Covariance Prediction&#39;&#39;&#39;</span>
            <span class="n">R</span> <span class="o">=</span> <span class="n">P</span> <span class="o">+</span> <span class="n">Vw</span>

        <span class="sd">&#39;&#39;&#39;Measurement Prediction&#39;&#39;&#39;</span>
        <span class="n">yhat</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">dot</span><span class="p">(</span><span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">])</span>

        <span class="sd">&#39;&#39;&#39;Measurement Variance Prediction&#39;&#39;&#39;</span>
        <span class="n">Q</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">@</span> <span class="n">R</span> <span class="o">@</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> <span class="o">+</span> <span class="n">Ve</span>

        <span class="sd">&#39;&#39;&#39;Forecast Error&#39;&#39;&#39;</span>
        <span class="n">e</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">y</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">-</span> <span class="n">yhat</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>

        <span class="sd">&#39;&#39;&#39;Kalman Gain&#39;&#39;&#39;</span>
        <span class="n">K</span> <span class="o">=</span> <span class="p">(</span><span class="n">R</span> <span class="o">@</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">())</span> <span class="o">/</span> <span class="n">Q</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>

        <span class="sd">&#39;&#39;&#39;State Update&#39;&#39;&#39;</span>
        <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">+=</span> <span class="n">K</span> <span class="o">*</span> <span class="n">e</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>

        <span class="sd">&#39;&#39;&#39;State Covariance Update&#39;&#39;&#39;</span>
        <span class="n">P</span> <span class="o">=</span> <span class="n">R</span> <span class="o">-</span> <span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">K</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span> <span class="o">@</span> <span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">],</span> <span class="mi">0</span><span class="p">)</span> <span class="o">@</span> <span class="n">R</span><span class="p">)</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">beta</span><span class="p">[:,</span> <span class="mi">0</span><span class="p">],</span> <span class="n">label</span><span class="o">=</span><span class="nb">str</span><span class="p">(</span><span class="n">delta</span><span class="p">),</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
    
<span class="c1">#     plt.plot(beta[:, 0], label=str(Ve), linewidth=2)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;SLOPE&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[108]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">delta</span> <span class="ow">in</span> <span class="p">[</span><span class="mf">1e-5</span><span class="p">,</span> <span class="mf">1e-6</span><span class="p">,</span> <span class="mf">1e-7</span><span class="p">,</span> <span class="mf">1e-8</span><span class="p">,</span> <span class="mf">1e-40</span><span class="p">]:</span>
<span class="c1"># for Ve in [0.001, 0.01, 0.1, 0.5, 0.9, 1]:</span>

<span class="c1">#     delta = 0.001</span>
    
    <span class="n">yhat</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
    <span class="n">e</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>
    <span class="n">Q</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full_like</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">double</span><span class="p">)</span>

    <span class="n">R</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span>
    <span class="n">P</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">2</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span> <span class="c1"># R(t|t) = P(t)</span>

    <span class="n">beta</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">empty</span><span class="p">((</span><span class="nb">len</span><span class="p">(</span><span class="n">x</span><span class="p">),</span> <span class="mi">2</span><span class="p">))</span>
    <span class="n">beta</span><span class="p">[:]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span>

    <span class="n">Vw</span> <span class="o">=</span> <span class="n">delta</span><span class="o">/</span><span class="p">(</span><span class="mi">1</span><span class="o">-</span><span class="n">delta</span><span class="p">)</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">identity</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>
    <span class="n">Ve</span> <span class="o">=</span> <span class="mf">0.001</span>

    <span class="n">beta</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mf">0.0</span>

    <span class="k">for</span> <span class="n">t</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">y</span><span class="p">)):</span>

        <span class="k">if</span> <span class="n">t</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">:</span>

            <span class="sd">&#39;&#39;&#39;State Prediction&#39;&#39;&#39;</span>
            <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>

            <span class="sd">&#39;&#39;&#39;State Covariance Prediction&#39;&#39;&#39;</span>
            <span class="n">R</span> <span class="o">=</span> <span class="n">P</span> <span class="o">+</span> <span class="n">Vw</span>

        <span class="sd">&#39;&#39;&#39;Measurement Prediction&#39;&#39;&#39;</span>
        <span class="n">yhat</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">dot</span><span class="p">(</span><span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">])</span>

        <span class="sd">&#39;&#39;&#39;Measurement Variance Prediction&#39;&#39;&#39;</span>
        <span class="n">Q</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">@</span> <span class="n">R</span> <span class="o">@</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">()</span> <span class="o">+</span> <span class="n">Ve</span>

        <span class="sd">&#39;&#39;&#39;Forecast Error&#39;&#39;&#39;</span>
        <span class="n">e</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">=</span> <span class="n">y</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">-</span> <span class="n">yhat</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>

        <span class="sd">&#39;&#39;&#39;Kalman Gain&#39;&#39;&#39;</span>
        <span class="n">K</span> <span class="o">=</span> <span class="p">(</span><span class="n">R</span> <span class="o">@</span> <span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">]</span><span class="o">.</span><span class="n">transpose</span><span class="p">())</span> <span class="o">/</span> <span class="n">Q</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>

        <span class="sd">&#39;&#39;&#39;State Update&#39;&#39;&#39;</span>
        <span class="n">beta</span><span class="p">[</span><span class="n">t</span><span class="p">]</span> <span class="o">+=</span> <span class="n">K</span> <span class="o">*</span> <span class="n">e</span><span class="p">[</span><span class="n">t</span><span class="p">]</span>

        <span class="sd">&#39;&#39;&#39;State Covariance Update&#39;&#39;&#39;</span>
        <span class="n">P</span> <span class="o">=</span> <span class="n">R</span> <span class="o">-</span> <span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">K</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span> <span class="o">@</span> <span class="n">np</span><span class="o">.</span><span class="n">expand_dims</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="n">t</span><span class="p">],</span> <span class="mi">0</span><span class="p">)</span> <span class="o">@</span> <span class="n">R</span><span class="p">)</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">beta</span><span class="p">[:,</span> <span class="mi">1</span><span class="p">],</span> <span class="n">label</span><span class="o">=</span><span class="nb">str</span><span class="p">(</span><span class="n">delta</span><span class="p">),</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
    
<span class="c1">#     plt.plot(beta[:, 0], label=str(Ve), linewidth=2)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;INTERCEPT&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>When 
δ
 is very small, the Kalman filter approaches normal OLS regression with a fixed intercept. When 
δ
 is huge, the estimated slope is very sensitive to the latest observations.</p>

</div>
</div>
</div>
    </div>
  </div>
</body>

 


</html>
