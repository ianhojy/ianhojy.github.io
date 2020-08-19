---
title: "Neural Collaborative Filtering"
excerpt: "Capturing non-linearities in Matrix Factorization"
collection: portfolio
---

<html>
<head><meta charset="utf-8" />

<title>Collaborative_Filtering_Neural</title>

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
<h1 id="Neural-Network-Collaborative-Filtering">Neural-Network Collaborative Filtering<a class="anchor-link" href="#Neural-Network-Collaborative-Filtering">&#182;</a></h1><hr>
<h4 id="Relevant-Paper:">Relevant Paper:<a class="anchor-link" href="#Relevant-Paper:">&#182;</a></h4><ul>
<li><a href="https://dl.acm.org/citation.cfm?id=3052569">Neural Collaborative Filtering</a></li>
</ul>
<p>In this notebook, I will be experimenting with collaborative filtering matrix factorization using latent factors learnt from neural networks. I will also demonstrate the potential of multi-layer networks and hybrid variants in capturing non-linearities beyond the classic matrix factorization methodology.</p>
<p>The data used for this notebook is from the <a href="https://grouplens.org/datasets/movielens/latest/">MovieLens Dataset</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="0.-Dependencies">0. Dependencies<a class="anchor-link" href="#0.-Dependencies">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">os</span>

<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>

<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">train_test_split</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="kn">import</span> <span class="n">mean_squared_error</span>

<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="kn">import</span> <span class="n">Input</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="kn">import</span> <span class="n">Embedding</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="kn">import</span> <span class="n">Flatten</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="kn">import</span> <span class="n">Dense</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="kn">import</span> <span class="n">Multiply</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="kn">import</span> <span class="n">Concatenate</span>

<span class="kn">from</span> <span class="nn">tensorflow.keras.regularizers</span> <span class="kn">import</span> <span class="n">l2</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.models</span> <span class="kn">import</span> <span class="n">Model</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.callbacks</span> <span class="kn">import</span> <span class="n">EarlyStopping</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.callbacks</span> <span class="kn">import</span> <span class="n">ModelCheckpoint</span>
<span class="kn">import</span> <span class="nn">tensorflow.keras.backend</span> <span class="k">as</span> <span class="nn">K</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.models</span> <span class="kn">import</span> <span class="n">load_model</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.utils</span> <span class="kn">import</span> <span class="n">plot_model</span>

<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="o">%</span><span class="k">matplotlib</span> inline
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">data_dir</span> <span class="o">=</span> <span class="s1">&#39;/Users/ianhojy/Desktop/Movie_Recommendation_System/data/&#39;</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="1.-Load-Data">1. Load Data<a class="anchor-link" href="#1.-Load-Data">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Importing ratings data</span>

<span class="n">ratings_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="n">data_dir</span><span class="o">+</span><span class="s1">&#39;ratings.csv&#39;</span><span class="p">,</span>
    <span class="n">usecols</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">,</span> <span class="s1">&#39;movieId&#39;</span><span class="p">,</span> <span class="s1">&#39;rating&#39;</span><span class="p">],</span>
    <span class="n">dtype</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;userId&#39;</span><span class="p">:</span> <span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="s1">&#39;movieId&#39;</span><span class="p">:</span> <span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="s1">&#39;rating&#39;</span><span class="p">:</span> <span class="s1">&#39;float32&#39;</span><span class="p">})</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># First 5 Rows of ratings</span>

<span class="n">ratings_df</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[4]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>3</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>6</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>47</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>50</td>
      <td>5.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">num_users</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">nunique</span><span class="p">()</span>
<span class="n">num_items</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">nunique</span><span class="p">()</span>

<span class="n">user_maxId</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>
<span class="n">item_maxId</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;There are </span><span class="si">{}</span><span class="s1"> unique users and </span><span class="si">{}</span><span class="s1"> unique movies &#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;</span><span class="se">\n</span><span class="s1">However:&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The max user ID is </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">user_maxId</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The max item ID is </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">item_maxId</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>There are 610 unique users and 9724 unique movies 

However:
The max user ID is 610
The max item ID is 193609
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">compress_item</span><span class="p">(</span><span class="n">df</span><span class="p">):</span>
    
    <span class="c1"># 1. Pivot</span>
    <span class="n">pivoted_df</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">pivot</span><span class="p">(</span>
        <span class="n">index</span><span class="o">=</span><span class="s1">&#39;userId&#39;</span><span class="p">,</span>
        <span class="n">columns</span><span class="o">=</span><span class="s1">&#39;movieId&#39;</span><span class="p">,</span>
        <span class="n">values</span><span class="o">=</span><span class="s1">&#39;rating&#39;</span><span class="p">)</span>
    
    <span class="c1"># 2. Reset index</span>
    <span class="n">pivoted_df</span> <span class="o">=</span> <span class="n">pivoted_df</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span><span class="o">.</span><span class="n">T</span>
    
    <span class="c1"># 3. Un-Pivot</span>
    <span class="n">unpivoted_df</span> <span class="o">=</span> <span class="n">pivoted_df</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="s1">&#39;userId&#39;</span><span class="p">)</span> \
        <span class="o">.</span><span class="n">melt</span><span class="p">(</span>
            <span class="n">id_vars</span><span class="o">=</span><span class="s1">&#39;userId&#39;</span><span class="p">,</span> 
            <span class="n">value_vars</span><span class="o">=</span><span class="n">pivoted_df</span><span class="o">.</span><span class="n">columns</span><span class="p">,</span>
            <span class="n">var_name</span><span class="o">=</span><span class="s1">&#39;movieId&#39;</span><span class="p">,</span>
            <span class="n">value_name</span><span class="o">=</span><span class="s1">&#39;rating&#39;</span><span class="p">)</span>
    
    <span class="n">unpivoted_df</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">unpivoted_df</span> <span class="o">=</span> <span class="n">unpivoted_df</span><span class="o">.</span><span class="n">sort_values</span><span class="p">([</span><span class="s1">&#39;userId&#39;</span><span class="p">,</span> <span class="s1">&#39;movieId&#39;</span><span class="p">])</span>
    <span class="n">unpivoted_df</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    
    <span class="k">return</span> <span class="n">unpivoted_df</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ratings_df</span> <span class="o">=</span> <span class="n">compress_item</span><span class="p">(</span><span class="n">ratings_df</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># We also shift the userId down by one to make it start at 0, same as movieId</span>

<span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span> <span class="o">-=</span> <span class="mi">1</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Check that we have successfully compressed the items</span>

<span class="n">num_users</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">nunique</span><span class="p">()</span>
<span class="n">num_items</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">nunique</span><span class="p">()</span>


<span class="n">user_minId</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>
<span class="n">item_minId</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>
<span class="n">user_maxId</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">()</span>
<span class="n">item_maxId</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">()</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;There are </span><span class="si">{}</span><span class="s1"> unique users and </span><span class="si">{}</span><span class="s1"> unique movies &#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;</span><span class="se">\n</span><span class="s1">Also:&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The max user ID is </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">user_maxId</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The max item ID is </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">item_maxId</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The min user ID is </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">user_minId</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The min item ID is </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">item_minId</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>There are 610 unique users and 9724 unique movies 

Also:
The max user ID is 0
The max item ID is 0
The min user ID is 609
The min item ID is 9723
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><i> NOTE</i>: The discrepancy above is because the movieID is zero-indexed, while userID is one-indexed</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">int32</span><span class="p">)</span>
<span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">ratings_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">int32</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="2.-Train-Test-Split">2. Train-Test Split<a class="anchor-link" href="#2.-Train-Test-Split">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">train_df</span><span class="p">,</span> <span class="n">test_df</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">ratings_df</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mf">0.2</span><span class="p">,</span> <span class="n">shuffle</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">99</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Training data:</span><span class="se">\t</span><span class="s1">&#39;</span><span class="p">,</span> <span class="n">train_df</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Test data:</span><span class="se">\t</span><span class="s1">&#39;</span><span class="p">,</span> <span class="n">test_df</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Training data:	 (80668, 3)
Test data:	 (20168, 3)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.-Generic-Function">3. Generic Function<a class="anchor-link" href="#3.-Generic-Function">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="3.1-for-Training-model">3.1 for Training model<a class="anchor-link" href="#3.1-for-Training-model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">train_model</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">optimizer</span><span class="p">,</span> <span class="n">batch_size</span><span class="p">,</span> <span class="n">epochs</span><span class="p">,</span> <span class="n">val_split</span><span class="p">,</span> <span class="n">inputs</span><span class="p">,</span> <span class="n">outputs</span><span class="p">):</span>
    
    <span class="c1"># This has to be defined using keras backend functions</span>
    <span class="k">def</span> <span class="nf">rmse</span><span class="p">(</span><span class="n">y_true</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">):</span>
        <span class="k">return</span> <span class="n">K</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">K</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">K</span><span class="o">.</span><span class="n">square</span><span class="p">(</span><span class="n">y_true</span> <span class="o">-</span> <span class="n">y_pred</span><span class="p">)))</span>
    
    <span class="n">model</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="n">optimizer</span><span class="o">=</span><span class="n">optimizer</span><span class="p">,</span> <span class="n">loss</span><span class="o">=</span><span class="s1">&#39;mean_squared_error&#39;</span><span class="p">,</span> <span class="n">metrics</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;mean_squared_error&#39;</span><span class="p">,</span> <span class="n">rmse</span><span class="p">])</span>

    <span class="n">early_stopper</span> <span class="o">=</span> <span class="n">EarlyStopping</span><span class="p">(</span><span class="n">monitor</span><span class="o">=</span><span class="s1">&#39;val_rmse&#39;</span><span class="p">,</span> <span class="n">patience</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">verbose</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
    <span class="n">model_saver</span> <span class="o">=</span> <span class="n">ModelCheckpoint</span><span class="p">(</span><span class="n">filepath</span><span class="o">=</span><span class="s1">&#39;model_tmp/model.hdf5&#39;</span><span class="p">,</span>
                                  <span class="n">monitor</span><span class="o">=</span><span class="s1">&#39;val_rmse&#39;</span><span class="p">,</span>
                                  <span class="n">save_best_only</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span>
                                  <span class="n">save_weights_only</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
                
    <span class="n">history</span> <span class="o">=</span> <span class="n">model</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">inputs</span><span class="p">,</span> <span class="n">outputs</span><span class="p">,</span>
                        <span class="n">batch_size</span><span class="o">=</span><span class="n">batch_size</span><span class="p">,</span>
                        <span class="n">epochs</span><span class="o">=</span><span class="n">epochs</span><span class="p">,</span>
                        <span class="n">validation_split</span><span class="o">=</span><span class="n">val_split</span><span class="p">,</span>
                        <span class="n">callbacks</span><span class="o">=</span><span class="p">[</span><span class="n">early_stopper</span><span class="p">,</span> <span class="n">model_saver</span><span class="p">])</span>
    
    <span class="k">return</span> <span class="n">history</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="3.2-for-Loading-model-weights">3.2 for Loading model weights<a class="anchor-link" href="#3.2-for-Loading-model-weights">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">load_trained_model</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">model_path</span><span class="p">):</span>
    
    <span class="n">model</span><span class="o">.</span><span class="n">load_weights</span><span class="p">(</span><span class="n">model_path</span><span class="p">)</span>
    
    <span class="k">return</span> <span class="n">model</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="3.3-for-Plotting-Learning-curves">3.3 for Plotting Learning curves<a class="anchor-link" href="#3.3-for-Plotting-Learning-curves">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">learning_plot</span><span class="p">(</span><span class="n">history</span><span class="p">,</span> <span class="n">metric</span><span class="p">):</span>

    <span class="n">errors</span> <span class="o">=</span> <span class="n">history</span><span class="o">.</span><span class="n">history</span><span class="p">[</span><span class="n">metric</span><span class="p">]</span>
    
    <span class="n">val_errors</span> <span class="o">=</span> <span class="n">history</span><span class="o">.</span><span class="n">history</span><span class="p">[</span><span class="s1">&#39;val_</span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">metric</span><span class="p">)]</span>

    <span class="n">epochs</span> <span class="o">=</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="nb">len</span><span class="p">(</span><span class="n">errors</span><span class="p">)</span> <span class="o">+</span> <span class="mi">1</span><span class="p">)</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span> <span class="mi">7</span><span class="p">))</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">epochs</span><span class="p">,</span> <span class="n">errors</span><span class="p">,</span> <span class="s1">&#39;bo&#39;</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">&#39;training </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">metric</span><span class="p">))</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">epochs</span><span class="p">,</span> <span class="n">val_errors</span><span class="p">,</span> <span class="s1">&#39;b&#39;</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">&#39;validation </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">metric</span><span class="p">))</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of epochs&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="n">metric</span><span class="o">.</span><span class="n">upper</span><span class="p">())</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Model Learning Curve&#39;</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">grid</span><span class="p">(</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="3.4-for-Calculating-RMSE">3.4 for Calculating RMSE<a class="anchor-link" href="#3.4-for-Calculating-RMSE">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">rmse</span> <span class="o">=</span> <span class="k">lambda</span> <span class="n">actual</span><span class="p">,</span> <span class="n">pred</span><span class="p">:</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">mean_squared_error</span><span class="p">(</span><span class="n">actual</span><span class="p">,</span> <span class="n">pred</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.1-Generalized-Matrix-Factorization">4.1 Generalized Matrix Factorization<a class="anchor-link" href="#4.1-Generalized-Matrix-Factorization">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.1.1-Model-Building-Function">4.1.1 Model-Building Function<a class="anchor-link" href="#4.1.1-Model-Building-Function">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Parameters</strong></p>
<ul>
<li><code>num_users</code>: number of users</li>
<li><code>num_items</code>: number of items (movies)</li>
<li><code>latent</code>: number of latent factors </li>
<li><code>user_reg</code>: regularization for user embedding matrix</li>
<li><code>item_reg</code>: regularization for item embedding matrix</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">build_GMF_model</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">,</span> <span class="n">latent</span><span class="p">,</span> <span class="n">user_reg</span><span class="p">,</span> <span class="n">item_reg</span><span class="p">):</span>

    <span class="c1"># Input Layers</span>
    <span class="n">user_input</span> <span class="o">=</span> <span class="n">Input</span><span class="p">(</span><span class="n">shape</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,),</span> <span class="n">dtype</span><span class="o">=</span><span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;user_input&#39;</span><span class="p">)</span>
    <span class="n">item_input</span> <span class="o">=</span> <span class="n">Input</span><span class="p">(</span><span class="n">shape</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,),</span> <span class="n">dtype</span><span class="o">=</span><span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;item_input&#39;</span><span class="p">)</span>

    <span class="c1"># Embedding Layers</span>
    <span class="n">MF_Embedding_User</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_users</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">latent</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;user_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">user_reg</span><span class="p">),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
    
    <span class="n">MF_Embedding_Item</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_items</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">latent</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;item_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">item_reg</span><span class="p">),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span> 
    
    <span class="n">user_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MF_Embedding_User</span><span class="p">(</span><span class="n">user_input</span><span class="p">))</span>
    <span class="n">item_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MF_Embedding_Item</span><span class="p">(</span><span class="n">item_input</span><span class="p">))</span>

    <span class="c1"># Element-wise multiplication</span>
    <span class="n">predict_vector</span> <span class="o">=</span> <span class="n">Multiply</span><span class="p">()([</span><span class="n">user_latent</span><span class="p">,</span> <span class="n">item_latent</span><span class="p">])</span>
    
    <span class="n">prediction</span> <span class="o">=</span> <span class="n">Dense</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;glorot_uniform&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;prediction&#39;</span><span class="p">)(</span><span class="n">predict_vector</span><span class="p">)</span>
    
    <span class="n">model</span> <span class="o">=</span> <span class="n">Model</span><span class="p">([</span><span class="n">user_input</span><span class="p">,</span> <span class="n">item_input</span><span class="p">],</span> <span class="n">prediction</span><span class="p">)</span>
    
    <span class="k">return</span> <span class="n">model</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.1.2-Building-GMF-model">4.1.2 Building GMF model<a class="anchor-link" href="#4.1.2-Building-GMF-model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">GMF_model</span> <span class="o">=</span> <span class="n">build_GMF_model</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">)</span>
<span class="n">GMF_model</span><span class="o">.</span><span class="n">summary</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Model: &#34;model&#34;
__________________________________________________________________________________________________
Layer (type)                    Output Shape         Param #     Connected to                     
==================================================================================================
user_input (InputLayer)         [(None, 1)]          0                                            
__________________________________________________________________________________________________
item_input (InputLayer)         [(None, 1)]          0                                            
__________________________________________________________________________________________________
user_embedding (Embedding)      (None, 1, 10)        6100        user_input[0][0]                 
__________________________________________________________________________________________________
item_embedding (Embedding)      (None, 1, 10)        97240       item_input[0][0]                 
__________________________________________________________________________________________________
flatten (Flatten)               (None, 10)           0           user_embedding[0][0]             
__________________________________________________________________________________________________
flatten_1 (Flatten)             (None, 10)           0           item_embedding[0][0]             
__________________________________________________________________________________________________
multiply (Multiply)             (None, 10)           0           flatten[0][0]                    
                                                                 flatten_1[0][0]                  
__________________________________________________________________________________________________
prediction (Dense)              (None, 1)            11          multiply[0][0]                   
==================================================================================================
Total params: 103,351
Trainable params: 103,351
Non-trainable params: 0
__________________________________________________________________________________________________
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[18]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plot_model</span><span class="p">(</span><span class="n">GMF_model</span><span class="p">,</span> <span class="n">to_file</span><span class="o">=</span><span class="s1">&#39;GMF_model.png&#39;</span><span class="p">,</span> <span class="n">show_shapes</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[18]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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MczT0xNOTk7w9fWFo6MjzM3N4eDgAHt7exw5ckRaRwgBBwcHxMbGwszMDABgYGCAbdu2ISAgAN7e3sjMzERMTIy0/6bWzszMxIULF/TuxvyAgADk5OQgPT29zuUpKSmIjY2tc3lcXByOHz+Or776SuM+jh8/jqVLlwJ4NEV3cHAwFAqFtDwwMBBubm5wd3fHF198gXXr1mHVqlUYPny4Sp2KigpER0fD39+/sd8mEVGDyUTNRzNE9NSQyWQ4dOgQpk2bputWSI9ERETAy8sLTflnobCwEFevXoW1tTUsLS3rXCcvLw/du3cH8OhswJOf9hcWFsLAwECa4W3BggUIDQ1FRUUFsrKyIJfL0aVLlxapDQBFRUVq62nS1n8/d+7cicuXLyMoKKjO5QUFBdL9YI8rLy9HdHQ0TE1N4e7u3uw+qqqqkJ+fr/aht5GRkQgPD0dUVFSz96VLbf39QtTORfLMEBERNZtcLsfLL7+sNggBkMIKgDove5LL5WqnuraystIYXJpSuylBqD2YO3cu7t69i59++qnO5XUFIeBRGEpKSoKrq2uL9GFoaKg2CN24cQPh4eE4ePBgi+yLiEgdhiEiInoqPXjwAEqlEiUlJbpupV0xMDDAnj17sH37dpw/f77B26WkpGDjxo0wMjLSYndAZmYmNm3ahNDQ0HqnASciai6GISIieuqEh4fj5MmTEEJg+fLluHTpkq5baldMTEywa9cutWdm6jJu3LhWCSfGxsbYs2eP2jNUREQtSbsf7xARETWBm5sbJk6cKL02MTHRYTftl7W1ta5bqMXCwkLXLRCRHmEYIiKip462HvpJRET0OF4mR0REREREeolhiIiIiIiI9BLDEBERERER6SXeM0T0lEpKStJ1C6Rnat5zEREROu7k6cffTyKi9kEmmvKocSLSKplMpusWiIiohRw6dAjTpk3TdRtEVFskzwwRPYX4GQXpA5lMxv8kEhGRTvGeISIiIiIi0ksMQ0REREREpJcYhoiIiIiISC8xDBERERERkV5iGCIiIiIiIr3EMERERERERHqJYYiIiIiIiPQSwxAREREREeklhiEiIiIiItJLDENERERERKSXGIaIiIiIiEgvMQwREREREZFeYhgiIiIiIiK9xDBERERERER6iWGIiIiIiIj0EsMQERERERHpJYYhIiIiIiLSSwxDRERERESklxiGiIiIiIhILzEMERERERGRXmIYIiIiIiIivcQwREREREREeolhiIiIiIiI9BLDEBERERER6SWGISIiIiIi0ksMQ0REREREpJcYhoiIiIiISC8xDBERERERkV5iGCIiIiIiIr3EMERERERERHqJYYiIiIiIiPQSwxAREREREeklhiEiIiIiItJLRrpugIiI2r/du3ejoKCg1nh0dDR+++03lbG3334bzz33XGu1RkREekwmhBC6boKIiNq3BQsWYOfOnTAxMVG7TmVlJbp27QqFQgEjI35WR0REWhfJy+SIiEjrvL29AQDl5eVqvwwNDTF9+nQGISIiajUMQ0REpHX/93//BwsLC43rVFZWSqGJiIioNTAMERGR1slkMsyYMQPGxsZq1+nVqxecnJxasSsiItJ3DENERNQqvL29UVFRUecyY2NjzJo1CzKZrJW7IiIifcYwRERErWL48OHo169fncsqKip4iRwREbU6hiEiImo1b731Fjp06FBrvF+/fhg6dKgOOiIiIn3GMERERK3mrbfeglKpVBnr0KED3n77bR11RERE+oxhiIiIWk3fvn1hZ2encm+QUqnkJXJERKQTDENERNSqfHx8YGhoCODRLHMODg7o06ePjrsiIiJ9xDBEREStytvbG9XV1QAAQ0ND+Pj46LgjIiLSVwxDRETUqiwsLDBq1CjIZDJUV1fD09NT1y0REZGeYhgiIqJWN3PmTAghMHbsWPTs2VPX7RARkZ6SCSGErpsgorYhIiICXl5eum6DiKgWDw8PREZG6roNImpbIo103QERtT2HDh3SdQvUDmzZsgXz5s2DmZkZtmzZAgB47733dNzV0yspKQlbt27l718dat4/RESNxTBERI02bdo0XbdA7cArr7yCXr16AYD0iT7fW5pt3bqVx6gOPCNERE3Fe4aIiEgnaoIQERGRrjAMERERERGRXmIYIiIiIiIivcQwREREREREeolhiIiIiIiI9BLDEBERtQsZGRnw9fVFdna2rlt5KimVSvz444/S65ycHHzyyScICAjAqVOnUFVV1az6CoUCCQkJdS4rLy/HyZMn8fHHH+PHH39U2dfFixeRmZnZrH0TETUVwxAREbULFy9eRFhYGC5fvqzrVp46hYWFCAwMxNChQwEAV69exfr16zFjxgxMnToVa9asgbW1NW7fvt3o2nl5efD3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DUtLyzrXycvLQ/fu3QE8OlPx5JmIwsJCGBgYSDO8LViwAKGhoaioqEBWVhbkcjm6dOnSIrUBoKioSG09dVry92/nzp24fPkygoKC6lxeUFAg3Zf1uPLyckRHR8PU1BTu7u7N6iEyMhLh4eGIiopqVh2gee8fItJrkTwzREREbZpcLsfLL7+sNggBkMIKgDovyZLL5WqnuraystIYXJpSu7FBqKXNnTsXd+/exU8//VTn8rqCEPAoDCUlJcHV1bVZ+79x4wbCw8Nx8ODBZtUhImouhiEiIqInPHjwAEqlEiUlJbpuRSsMDAywZ88ebN++HefPn2/wdikpKdi4cSOMjIyavO/MzExs2rQJoaGh9U7xTUSkbQxDREREjwkPD8fJkychhMDy5ctx6dIlXbekFSYmJti1axd69OjR4G3GjRvX7ABjbGyMPXv2qD37RETUmpr+0Q4REVE75ObmhokTJ0qvTUxMdNiN9llbW7fq/iwsLFp1f0REmjAMERERPaY1HjZKRERPB14mR0REREREeolhiIiIiIiI9BLDEBERERER6SXeM0REjVbzgEOilpKcnAyA7y1NsrOzAfAY1SU5ORlOTk66boOI2iCZ4KPkiaiBkpKS8Omnn+q6DSKiWpydnbFs2TJdt0FEbUskwxAREREREemjSN4zREREREREeolhiIiIiIiI9BLDEBERERER6SWGISIiIiIi0kv/D3llW9jlMMJyAAAAAElFTkSuQmCC
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
<h3 id="4.1.3-Training-GMF-model">4.1.3 Training GMF model<a class="anchor-link" href="#4.1.3-Training-GMF-model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[19]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># model config</span>
<span class="n">BATCH_SIZE</span> <span class="o">=</span> <span class="mi">64</span>
<span class="n">EPOCHS</span> <span class="o">=</span> <span class="mi">30</span>
<span class="n">VAL_SPLIT</span> <span class="o">=</span> <span class="mf">0.25</span>

<span class="c1"># train model</span>
<span class="n">history</span> <span class="o">=</span> <span class="n">train_model</span><span class="p">(</span><span class="n">GMF_model</span><span class="p">,</span> <span class="s1">&#39;adam&#39;</span><span class="p">,</span> <span class="n">BATCH_SIZE</span><span class="p">,</span> <span class="n">EPOCHS</span><span class="p">,</span> <span class="n">VAL_SPLIT</span><span class="p">,</span> 
                      <span class="n">inputs</span><span class="o">=</span><span class="p">[</span><span class="n">train_df</span><span class="p">[</span><span class="s2">&quot;userId&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">train_df</span><span class="p">[</span><span class="s2">&quot;movieId&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">],</span>
                      <span class="n">outputs</span><span class="o">=</span><span class="n">train_df</span><span class="p">[</span><span class="s2">&quot;rating&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Epoch 1/30
946/946 [==============================] - 3s 3ms/step - loss: 9.8115 - mean_squared_error: 9.8115 - rmse: 3.1029 - val_loss: 4.6862 - val_mean_squared_error: 4.6862 - val_rmse: 2.1612
Epoch 2/30
946/946 [==============================] - 2s 2ms/step - loss: 2.3123 - mean_squared_error: 2.3123 - rmse: 1.4981 - val_loss: 1.5871 - val_mean_squared_error: 1.5871 - val_rmse: 1.2529
Epoch 3/30
946/946 [==============================] - 2s 2ms/step - loss: 1.1241 - mean_squared_error: 1.1241 - rmse: 1.0542 - val_loss: 1.1755 - val_mean_squared_error: 1.1755 - val_rmse: 1.0768
Epoch 4/30
946/946 [==============================] - 2s 2ms/step - loss: 0.8376 - mean_squared_error: 0.8376 - rmse: 0.9105 - val_loss: 1.0496 - val_mean_squared_error: 1.0496 - val_rmse: 1.0165
Epoch 5/30
946/946 [==============================] - 2s 2ms/step - loss: 0.7167 - mean_squared_error: 0.7167 - rmse: 0.8421 - val_loss: 1.0021 - val_mean_squared_error: 1.0021 - val_rmse: 0.9932
Epoch 6/30
946/946 [==============================] - 2s 2ms/step - loss: 0.6542 - mean_squared_error: 0.6542 - rmse: 0.8042 - val_loss: 0.9818 - val_mean_squared_error: 0.9818 - val_rmse: 0.9831
Epoch 7/30
946/946 [==============================] - 2s 3ms/step - loss: 0.6164 - mean_squared_error: 0.6164 - rmse: 0.7807 - val_loss: 0.9748 - val_mean_squared_error: 0.9748 - val_rmse: 0.9796
Epoch 8/30
946/946 [==============================] - 2s 2ms/step - loss: 0.5893 - mean_squared_error: 0.5893 - rmse: 0.7630 - val_loss: 0.9725 - val_mean_squared_error: 0.9725 - val_rmse: 0.9784
Epoch 9/30
946/946 [==============================] - 2s 2ms/step - loss: 0.5668 - mean_squared_error: 0.5668 - rmse: 0.7480 - val_loss: 0.9694 - val_mean_squared_error: 0.9694 - val_rmse: 0.9768
Epoch 10/30
946/946 [==============================] - 2s 2ms/step - loss: 0.5441 - mean_squared_error: 0.5441 - rmse: 0.7326 - val_loss: 0.9723 - val_mean_squared_error: 0.9723 - val_rmse: 0.9784
Epoch 11/30
946/946 [==============================] - 2s 2ms/step - loss: 0.5203 - mean_squared_error: 0.5203 - rmse: 0.7164 - val_loss: 0.9791 - val_mean_squared_error: 0.9791 - val_rmse: 0.9817
Epoch 12/30
946/946 [==============================] - 2s 2ms/step - loss: 0.4963 - mean_squared_error: 0.4963 - rmse: 0.6994 - val_loss: 0.9868 - val_mean_squared_error: 0.9868 - val_rmse: 0.9857
Epoch 13/30
946/946 [==============================] - 2s 2ms/step - loss: 0.4705 - mean_squared_error: 0.4705 - rmse: 0.6812 - val_loss: 0.9955 - val_mean_squared_error: 0.9955 - val_rmse: 0.9899
Epoch 14/30
946/946 [==============================] - 2s 2ms/step - loss: 0.4447 - mean_squared_error: 0.4447 - rmse: 0.6621 - val_loss: 1.0104 - val_mean_squared_error: 1.0104 - val_rmse: 0.9973
Epoch 15/30
946/946 [==============================] - 2s 2ms/step - loss: 0.4202 - mean_squared_error: 0.4202 - rmse: 0.6430 - val_loss: 1.0234 - val_mean_squared_error: 1.0234 - val_rmse: 1.0036
Epoch 16/30
946/946 [==============================] - 2s 3ms/step - loss: 0.3968 - mean_squared_error: 0.3968 - rmse: 0.6253 - val_loss: 1.0393 - val_mean_squared_error: 1.0393 - val_rmse: 1.0116
Epoch 17/30
946/946 [==============================] - 2s 3ms/step - loss: 0.3768 - mean_squared_error: 0.3768 - rmse: 0.6090 - val_loss: 1.0536 - val_mean_squared_error: 1.0536 - val_rmse: 1.0186
Epoch 18/30
946/946 [==============================] - 2s 2ms/step - loss: 0.3586 - mean_squared_error: 0.3586 - rmse: 0.5942 - val_loss: 1.0676 - val_mean_squared_error: 1.0676 - val_rmse: 1.0257
Epoch 19/30
946/946 [==============================] - 2s 2ms/step - loss: 0.3437 - mean_squared_error: 0.3437 - rmse: 0.5814 - val_loss: 1.0848 - val_mean_squared_error: 1.0848 - val_rmse: 1.0340
Epoch 00019: early stopping
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.1.4-Plotting-GMF-Learning-Curve">4.1.4 Plotting GMF Learning Curve<a class="anchor-link" href="#4.1.4-Plotting-GMF-Learning-Curve">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[20]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">learning_plot</span><span class="p">(</span><span class="n">history</span><span class="p">,</span> <span class="s1">&#39;rmse&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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jq5Ape5obm5m5syZ5S6jX7FPi8v+LD77tPjs0+KyP4vPPu29iGj37qVO4ZAkSZIKYICWJEmSCmCAliRJkgpQdXOgJUmSKsmmTZtYvnw569evL3cpOxg1ahRLliwpdxlVob6+nr322ou6urputTdAS5Ik9cLy5csZMWIEDQ0NRES5y9lmzZo1jBgxotxlVLyUEqtWrWL58uXss88+3drHKRySJEm9sH79esaOHVtR4VndFxGMHTu2oN8gGKAlSZJ6yfBc3Qr98zNAS5IkSQUwQEuSJFWx119/nR/96Ec92veEE07g9ddf77TNueeey2233daj4/dXBmhJkqQ+NG8eNDRATU32PG9e747XWYDesmVLp/vedNNNjB49utM2F1xwAccee2yP6+tIV7VVMgO0JElSH5k3D84+G5Ytg5Sy57PP7l2I/tKXvsSzzz7LlClT+MIXvkBzczOzZs3irLPOYvLkyQCcfPLJHHzwwey///5cfvnl2/ZtaGhg5cqVLF26lIkTJ/LRj36U/fffn6amJt58800AzjzzTK699tpt7c877zymTp3K5MmTefLJJwF45ZVXaGxsZOrUqXzsYx9jwoQJrFy5cqdahw8fzrnnnsthhx3GggULaGho4Ctf+QqHH34406ZNY9GiRRx33HHsu+++XHbZZQCsWLGCGTNmMGXKFCZNmsTdd98NwC233MLhhx/O1KlTOfXUU2lpael5JxbIAC1JktRHvvpVWLdux3Xr1mXre+o73/kO++67L4sXL+a73/0uAA888ADnnnsuTzzxBABXXHEFCxcu5KGHHuKSSy5h1apVOx3n6aef5pOf/CSPP/44o0eP5rrrrmv3/XbddVcWLVrEOeecw/e+9z0AvvGNbzB79mwWLVrEe97zHp5//vl29127di2TJk3i/vvv58gjjwRg7733ZsGCBRx11FHbwvp9993HueeeC8BVV13Fcccdx+LFi3n44YeZMmUKK1eu5Jvf/Ca33XYbixYtYtq0aVx00UU978QCeR1oSZKkPtJBruxwfU8deuihNDQ0bHt9ySWXcMMNNwDwwgsv8PTTTzN27Ngd9tlnn32YMmUKAAcffDBLly5t99jvfe97t7W5/vrrAbjnnnu2Hf/4449nzJgx7e5bW1vL+973vh3WnXjiiQBMnjyZlpYWRowYwYgRI6ivr+f111/nkEMO4ayzzmLTpk2cfPLJTJkyhTvvvJMnnniCI444AoCNGzdy+OGHd7d7es0R6G4o9lwlSZI0MI0fX9j6nho2bNi25ebmZm677TYWLFjAww8/zEEHHdTuNY+HDBmybbm2tpbNmze3e+zWdvltUkrdqqu+vp7a2tp2j1dTU7NDDTU1NWzevJkZM2Zw1113seeee3L66adz5ZVXklKisbGRxYsXs3jxYp544gl++tOfdquGYjBAd6EUc5UkSdLAdOGFMHTojuuGDs3W99SIESNYs2ZNh9tXr17NmDFjGDp0KE8++ST33Xdfz9+sA0ceeSTXXHMNkM1Nfu2114p27GXLlrHbbrvx0Y9+lA9/+MMsWrSI6dOnc++99/LMM88AsG7dOp566qmivWdXDNBdKMVcJUmSNDDNnQuXXw4TJkBE9nz55dn6nho7dixHHHEEkyZN4gtf+MJO248//ng2b97MAQccwNe//nWmT5/ei0/QvvPOO49bbrmFqVOncvPNN7PHHnsU7Tbizc3NTJkyhYMOOojrrruOz3zmM7z1rW/l5z//OaeddhoHHHAA06dP33ZCY1+I7g65V4pp06alhx56qM/er6YmG3luKwK2bu2zMoqqubmZmTNnlruMfsU+LS77s/js0+KzT4urmvtzyZIlTJw4sdxl7GTNmjVFC7Fd2bBhA7W1tQwaNIgFCxZwzjnnsHjx4j5572Jp788xIhamlKa1betJhF0YPz6bttHeekmSJMHzzz/P+9//frZu3crgwYP5yU9+Uu6SSsoA3YULL8zmPOdP4+jtXCVJkqT+ZL/99uMPf/hDucvoM86B7kIp5ipJkiSpejkC3Q1z5xqYJUmSlHEEWpIkSSqAAVqSJEkqgAFakiRpgBk+fDgAL774Iqecckq7bWbOnElXlw6++OKLWZd3pYUTTjiB119/vXiFVigDtCRJ0gD1tre9jWuvvbbH+7cN0DfddBOjR48uRmnbdHRL8XIyQEuSJFWxL37xi/zoRz/a9vr888/n+9//Pi0tLRxzzDFMnTqVyZMn8+tf/3qnfZcuXcqkSZMAePPNN5kzZw4HHHAAH/jAB3jzzTe3tTvnnHOYNm0a+++/P+eddx4Al1xyCS+++CKzZs1i1qxZADQ0NLBy5UoALrroIiZNmsSkSZO4+OKLt73fxIkT+ehHP8r+++9PU1PTDu/T6swzz+Rzn/scs2bN4otf/CLnn38+H/rQh2hqaqKhoYHrr7+ef/qnf2Ly5Mkcf/zxbNq0CYAvfelL/PVf/zUHHHAAn//85wF45ZVXeN/73schhxzCIYccwr333tvrPvcqHJIkSUXy2c9CsW/AN2UK5PJnu+bMmcNnP/tZPvGJTwBwzTXX8L//+7/U19dzww03MHLkSFauXMn06dM58cQTiYh2j/PjH/+YoUOH8sgjj/DII48wderUbdsuvPBC3vKWt7BlyxaOOeYYHnnkET796U9z0UUXcccdd7DrrrvucKyFCxfys5/9jPvvv5+UEocddhhHH300Y8aM4emnn+bqq6/mJz/5Ce9///u57rrr+OAHP7hTPU899RS33XYbtbW1nH/++Tz77LPccccdPPHEExx++OFcd911/Ou//ivvec97+M1vfsOMGTO44YYbePLJJ4mIbVNJPvOZz/AP//APHHnkkTz//PMcd9xxLFmypNA/hh2UbAQ6Iuoj4oGIeDgiHo+Ib7TTZkhE/DIinomI+yOioVT1SJIk9UcHHXQQf/nLX3jxxRd5+OGHGTNmDOPHjyelxFe+8hUOOOAAjj32WP785z/z8ssvd3icu+66a1uQPeCAAzjggAO2bbvmmmuYOnUqBx10EI8//jhPPPFEpzXdc889vOc972HYsGEMHz6c9773vdx9990A7LPPPkyZMgWAgw8+mKVLl7Z7jFNPPZXa2tptr9/1rndRV1fH5MmT2bJlC8cffzwAkydPZunSpYwcOZL6+no+8pGPcP311zN06FAAbrvtNj71qU8xZcoUTjzxRN544w3WrFnTRa92rpQj0BuA2SmlloioA+6JiJtTSvfltfkw8FpK6R0RMQf4F+ADJaxJkiSpZDobKS6lU045hWuvvZaXXnqJOXPmAFnofeWVV1i4cCF1dXU0NDSwfv36To/T3uj0c889x/e+9z0efPBBxowZw5lnntnlcVJKHW4bMmTItuXa2tp2p3AADBs2rN39ampqqKur21ZrTU0NmzdvZtCgQTzwwAP87ne/Y/78+Vx66aXcfvvtbN26lQULFrDLLrt0WnMhSjYCnTItuZd1uUfb3jwJ+EVu+VrgmOjo9wqSJElq15w5c5g/fz7XXnvttqtqrF69mt122426ujruuOMOli1b1ukxZsyYwbx58wB47LHHeOSRRwB44403GDZsGKNGjeLl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
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
<h3 id="4.1.5-GMF-model-on-Test-Set">4.1.5 GMF model on Test Set<a class="anchor-link" href="#4.1.5-GMF-model-on-Test-Set">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Building architecture and loading weights</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[21]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">GMF_model</span> <span class="o">=</span> <span class="n">build_GMF_model</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">)</span>
<span class="n">GMF_model</span> <span class="o">=</span> <span class="n">load_trained_model</span><span class="p">(</span><span class="n">GMF_model</span><span class="p">,</span> <span class="s1">&#39;model_tmp/model.hdf5&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Making Predictions</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[22]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">predictions</span> <span class="o">=</span> <span class="n">GMF_model</span><span class="o">.</span><span class="n">predict</span><span class="p">([</span><span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Calcualting RMSE</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[23]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">error</span> <span class="o">=</span> <span class="n">rmse</span><span class="p">(</span><span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;rating&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">predictions</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The test-set RMSE of rating predictions is&#39;</span><span class="p">,</span> <span class="nb">round</span><span class="p">(</span><span class="n">error</span><span class="p">,</span> <span class="mi">4</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>The test-set RMSE of rating predictions is 0.9735
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.2-Multi-Layer-Perceptron-Model">4.2 Multi-Layer Perceptron Model<a class="anchor-link" href="#4.2-Multi-Layer-Perceptron-Model">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.2.1-Model-Building-Function">4.2.1 Model Building Function<a class="anchor-link" href="#4.2.1-Model-Building-Function">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[24]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">build_MLP_model</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">,</span> <span class="n">layers</span><span class="p">,</span> <span class="n">reg_layers</span><span class="p">):</span>

    <span class="k">assert</span> <span class="nb">len</span><span class="p">(</span><span class="n">layers</span><span class="p">)</span> <span class="o">==</span> <span class="nb">len</span><span class="p">(</span><span class="n">reg_layers</span><span class="p">)</span>
    <span class="n">num_layer</span> <span class="o">=</span> <span class="nb">len</span><span class="p">(</span><span class="n">layers</span><span class="p">)</span> 
    
    <span class="c1"># Input layers</span>
    <span class="n">user_input</span> <span class="o">=</span> <span class="n">Input</span><span class="p">(</span><span class="n">shape</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,),</span> <span class="n">dtype</span><span class="o">=</span><span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;user_input&#39;</span><span class="p">)</span>
    <span class="n">item_input</span> <span class="o">=</span> <span class="n">Input</span><span class="p">(</span><span class="n">shape</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,),</span> <span class="n">dtype</span><span class="o">=</span><span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;item_input&#39;</span><span class="p">)</span>

    <span class="c1"># Embedding vectors</span>
    <span class="n">MLP_Embedding_User</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_users</span> <span class="o">+</span> <span class="mi">1</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">layers</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">//</span> <span class="mi">2</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;user_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">reg_layers</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
    <span class="n">MLP_Embedding_Item</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_items</span> <span class="o">+</span> <span class="mi">1</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">layers</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">//</span> <span class="mi">2</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;item_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">reg_layers</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span> 
    
    <span class="n">user_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MLP_Embedding_User</span><span class="p">(</span><span class="n">user_input</span><span class="p">))</span>
    <span class="n">item_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MLP_Embedding_Item</span><span class="p">(</span><span class="n">item_input</span><span class="p">))</span>

    <span class="c1"># User &amp; Item Matrix Concatenation</span>
    <span class="n">vector</span> <span class="o">=</span> <span class="n">Concatenate</span><span class="p">(</span><span class="n">axis</span><span class="o">=-</span><span class="mi">1</span><span class="p">)([</span><span class="n">user_latent</span><span class="p">,</span> <span class="n">item_latent</span><span class="p">])</span>

    <span class="c1"># MLP Extended Layers</span>
    <span class="k">for</span> <span class="n">idx</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">num_layer</span><span class="p">):</span>
        <span class="n">layer</span> <span class="o">=</span> <span class="n">Dense</span><span class="p">(</span>
            <span class="n">units</span><span class="o">=</span><span class="n">layers</span><span class="p">[</span><span class="n">idx</span><span class="p">],</span>
            <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;relu&#39;</span><span class="p">,</span>
            <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;glorot_uniform&#39;</span><span class="p">,</span>
            <span class="n">kernel_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">reg_layers</span><span class="p">[</span><span class="n">idx</span><span class="p">]),</span>
            <span class="n">name</span> <span class="o">=</span> <span class="s1">&#39;layer</span><span class="si">%d</span><span class="s1">&#39;</span> <span class="o">%</span><span class="k">idx</span>)
        <span class="n">vector</span> <span class="o">=</span> <span class="n">layer</span><span class="p">(</span><span class="n">vector</span><span class="p">)</span>
    
    <span class="c1"># Final prediction layer</span>
    <span class="n">prediction</span> <span class="o">=</span> <span class="n">Dense</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;glorot_uniform&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;prediction&#39;</span><span class="p">)(</span><span class="n">vector</span><span class="p">)</span>
    
    <span class="c1"># Final Model</span>
    <span class="n">model</span> <span class="o">=</span> <span class="n">Model</span><span class="p">([</span><span class="n">user_input</span><span class="p">,</span> <span class="n">item_input</span><span class="p">],</span> <span class="n">prediction</span><span class="p">)</span>
    
    <span class="k">return</span> <span class="n">model</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.2.2-Building-MLP-Model">4.2.2 Building MLP Model<a class="anchor-link" href="#4.2.2-Building-MLP-Model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[25]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">MLP_model</span> <span class="o">=</span> <span class="n">build_MLP_model</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">,</span> <span class="p">[</span><span class="mi">64</span><span class="p">,</span> <span class="mi">32</span><span class="p">,</span> <span class="mi">16</span><span class="p">,</span> <span class="mi">8</span><span class="p">],</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">])</span>
<span class="n">MLP_model</span><span class="o">.</span><span class="n">summary</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Model: &#34;model_2&#34;
__________________________________________________________________________________________________
Layer (type)                    Output Shape         Param #     Connected to                     
==================================================================================================
user_input (InputLayer)         [(None, 1)]          0                                            
__________________________________________________________________________________________________
item_input (InputLayer)         [(None, 1)]          0                                            
__________________________________________________________________________________________________
user_embedding (Embedding)      (None, 1, 32)        19552       user_input[0][0]                 
__________________________________________________________________________________________________
item_embedding (Embedding)      (None, 1, 32)        311200      item_input[0][0]                 
__________________________________________________________________________________________________
flatten_4 (Flatten)             (None, 32)           0           user_embedding[0][0]             
__________________________________________________________________________________________________
flatten_5 (Flatten)             (None, 32)           0           item_embedding[0][0]             
__________________________________________________________________________________________________
concatenate (Concatenate)       (None, 64)           0           flatten_4[0][0]                  
                                                                 flatten_5[0][0]                  
__________________________________________________________________________________________________
layer1 (Dense)                  (None, 32)           2080        concatenate[0][0]                
__________________________________________________________________________________________________
layer2 (Dense)                  (None, 16)           528         layer1[0][0]                     
__________________________________________________________________________________________________
layer3 (Dense)                  (None, 8)            136         layer2[0][0]                     
__________________________________________________________________________________________________
prediction (Dense)              (None, 1)            9           layer3[0][0]                     
==================================================================================================
Total params: 333,505
Trainable params: 333,505
Non-trainable params: 0
__________________________________________________________________________________________________
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[26]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plot_model</span><span class="p">(</span><span class="n">MLP_model</span><span class="p">,</span>  <span class="n">to_file</span><span class="o">=</span><span class="s1">&#39;MLP_model.png&#39;</span><span class="p">,</span><span class="n">show_shapes</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[26]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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SjgYIiIAgLe3N7y8vJTthg0bGjGautGuXbs6PV9Vq4oTEVHFLDFHAcxTdYGDISICgDpZwI2IiKg6mKPIUDiBAhERERERWSQOhoiIiIiIyCJxMERERERERBbJZO8ZCg0NNXYIRAYXFRUFgK93XZS1FVUsOTlZ63oeVHPJycl8r5JFYv+rXXJyMgDmcm1M+TWkEhExdhCPCtFmKX8AACAASURBVA0Nha+vr7HDICIyOz4+Pti7d6+xw6iXxo0bh7CwMGOHQURk1kxs2AEAe01uMERkylQqFUJCQrSuDUBERFTXmJ+IqmUv7xkiIiIiIiKLxMEQERERERFZJA6GiIiIiIjIInEwREREREREFomDISIiIiIiskgcDBERERERkUXiYIiIiIiIiCwSB0NERERERGSROBgiIiIiIiKLxMEQERERERFZJA6GiIiIiIjIInEwREREREREFomDISIiIiIiskgcDBERERERkUXiYIiIiIiIiCwSB0NERERERGSROBgiIiIiIiKLxMEQERERERFZJA6GiIiIiIjIInEwREREREREFomDISIiIiIiskgcDBERERERkUXiYIiIiIiIiCwSB0NERERERGSROBgiIiIiIiKLxMEQERERERFZJA6GiIiIiIjIInEwREREREREFomDISIiIiIiskgcDBERERERkUXiYIiIiIiIiCwSB0NERERERGSROBgiIiIiIiKLpDZ2AESmKjAwELdv3y63/+DBg/jjjz809k2dOhVPPfVUXYVGREQWjPmJqPaoRESMHQSRKZo1axY2bdqEhg0bVlqmuLgYzZs3R1paGtRqfrdARESGx/xEVGv28jI5okpMnDgRAFBYWFjpn7W1NSZNmsREQ0REdYb5iaj2cDBEVIkXX3wRTk5OWssUFxcrSYmIiKguMD8R1R4OhogqoVKp4OfnBxsbm0rLtG7dGh4eHnUYFRERWTrmJ6Law8EQkRYTJ05EUVFRhcdsbGzwxhtvQKVS1XFURERk6ZifiGoHJ1AgqkKnTp1w8+bNCo/FxsaiZ8+edRwRERER8xNRLeAECkRVef3119GgQYNy+zt27MhEQ0RERsP8RFRzHAwRVeH1119HSUmJxr4GDRpg6tSpRoqIiIiI+YmoNnAwRFSFZ555Br169dK49rqkpISz9BARkVExPxHVHAdDRDqYMmUKrK2tATycxadv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d5CSkoLhw4dj69atGD58uNhvzZo1WLx4ca08njd69GisXbsWzs7OSuVBRKQKfDJERERtgrm5OQIDAxXapk6dinnz5gEAhgwZgrCwMMTFxWH48OE4cOAAAMDDwwMODg4oKyvDhx9+iN27dyM+Ph6rVq1CamoqwsLCAACDBw9WiK2np4cBAwaI21ZWVjA0NISOjg7GjRsHKysrAIC7uzv27t2LuXPnttSlNygjIwPGxsYN9hEEAeHh4QgNDYWWllajY9+9exd3797Fm2++icDAQCQmJiI9PR03b97E2LFjcffuXQDAqVOnIJVKMWrUqBfGtLCwEItSIqK2jsUQERG1Gdra2rXaOnbsCAAYNGiQ2GZubq6wapquri6kUiksLCzEtmXLlkEqlSq9wplEIlHY1tXVhbu7+wufiLQEuVyOW7duwcjIqMF+x48fh729PWxtbZWKn56eDgBwcnJCt27dAABmZmb45ptv8OjRIwQHB+Phw4cICgrCihUrGhVTX18flZWVuHnzplK5EBGpAofJERHRK0dTUxOCIDTYp1OnTujduzcKCwuViv18MaRKxcXFqKqqEgvC+iQmJmLNmjVKx69ZkOH5RStqiqrr169jyZIlsLa2xuHDh8X9v//+O8rKynDw4EEYGBjgnXfeEfd17twZwLN5XObm5krnRETUmlgMERFRu1ReXo6CggLY29srdVxbKoZ69uwJAwMDyGSyBvv17dtXYaW5xjIzMwMApKWlKbSbmpqiQ4cO0NPTQ2FhIf79738r7C8pKcGTJ0/w97//HRYWFgrF0IMHDwAAJiYmSudDRNTaWAwREVG7dPbsWZSVlYnLQEulUpSVlTV4jEQiQVVVVWuk12gWFha4d+9eg318fX2bFLtnz56wt7fH2bNnFdp///13VFRUYPTo0fD29q51XEBAACIiIpCbm1trX35+PiQSCfr169eknIiIWhPnDBERUZtRXl4O4Nly1jVKS0sBQGFCflFREcrLyxWGylVWVuLq1avi9v79+zF27FixGLKzs0NRURHCw8Px+PFjhIeH4/79+7h165b4NMPIyAgFBQW4desWsrKy8PjxY6SlpWHkyJFISkpqsetuyJgxYxp8kWlycjIcHR0V5lDVmD9/PqZMmdLgsuCbN29GTk4Ofv31V7Ht5MmTGDx4cJMWjbh9+zbs7Oygo6Oj9LFERK2NxRAREbUJ586dE+e97Nu3D/Hx8Th16hR+/PFHAMD69etRUFCAf/3rX0hOToZMJsOaNWtQWVkJANDQ0EBwcDACAgLg7u6O7Oxs8V1BAODq6gobGxt4eXnB2toaBgYGGDFiBKysrMSV6VxdXSEIAkaMGIGEhATo6uoiOzsbv/32m8oWBAgICEBeXh6ysrLq3J+SkoKEhIQ69ycmJuKnn37CDz/8UG98CwsL/PLLLwgMDMTq1auxfv16HDlyBCdOnIBUqtwAErlcjkOHDsHf31+p44iIVEUivGgGKhHRS3B1dQUAxMTEqDgTamkSiQT79u3DzJkzW/3cH3zwAcLCwiCXy5GTkwN9fX106dKlzr6FhYUwNDQEAJSVldV6glFSUgINDQ2F1eNKS0vrjaeMpn4edu7ciczMTAQFBdW5v7i4WFwN7q/Ky8tx6NAh6OjoYNq0aS88T15eHjp27IiuXbsqlV+NmJgYREZGIjY2VuljVfn9Q0RqK4ZPhoiIqF0xMTFpsHCpKYQA1DmUS19fv9Yy2s1RCL0MHx8f3L9/H+fPn69zf12FEPCsGDpz5gymTJnSqPMYGxs3uRC6du0aIiMjERUV1aTjiYhUgQsoEFGbIpfLkZycjCNHjmDSpEmN/iGutRQUFODatWsYN26c0seePn1afIlljQ4dOsDQ0BDGxsZ44403milL9fPkyRNUVlbi0aNH4tLO7YmGhgb27NkDPz8/+Pj4wNraulHHpaSkYP369UoPd1NWboVfFgAAIABJREFUdnY2NmzYgLCwsBcuA05E1JbwyRARtSmXLl1CdHQ0tm7diry8PFWnIyosLIS/vz/69+8vzmFRlqWlJbKysjB79mzMnTsXpaWlKCwsRFxcHNzc3NCvXz+sXLkSFRUVzZx9+xYZGYljx45BEAR8+umnuHDhgqpTahHa2toICQlBjx49Gn3MxIkTW6U40dLSwp49e+p9QkVE1FbxyRARtSnDhw/HokWLEBISoupUFNy+fRuenp7YvHlzk2MYGBhg7ty5WLVqFV5//XWF5ZAFQcCBAwcwb948pKSk4MCBA7WGalHdHB0d4eDgIG5ra2urMJuWZ2pqquoUajEyMlJ1CkRETcJiiIjanJohPW3p5ZfW1tYKSzs3VX1zTyQSCVxcXFBVVYVZs2ZhzJgxSElJgZaW1kufs71rystGiYiIABZDRPQKuXHjBs6ePYuMjAyMHj0aM2bMAACcOHECOTk5AJ49FXB2doa2tjZSUlJw5coVdO3aFdOnTwfwbLWsn3/+Gbm5uRg9ejQmTJggxn/w4AGioqKwcOFC/PTTT8jIyMDHH3/cqPkWRUVF2LVrF7y8vJQaxvQ8Nzc3REREICEhASkpKXj77bdfmHdOTg4OHjwIPz8/XLlyBYcOHYKpqSk8PDygofFsNLQgCDh16hQuXLgATU1NDBo0CJMmTRJjNBSfiIiovWIxRESvhK1bt+LQoUNITExEdnY2xo8fj4KCAixYsAC2trb46KOPcPnyZWRlZYnDpEaOHIn33nsPhw4dAvDsRZJRUVFYsGAB9PT04OTkBE9PT2zfvh3fffcdFi5cCLlcjurqaoSGhuLixYuYPHkyLC0tX5hfbGwsPvvsM3Tu3Bl+fn4vda02NjZISEhAcnIy3n777QbzjouLw7x581BYWAhBEJCRkYHCwkKsXLkSubm5WL58OQBg5cqV6NevHxYvXozffvsNixYtEouhhuITERG1Z1xAgYheCdu3b4eFhQUkEgn69u0LKysrHDlyBADQqVMnbNiwAcCzl0zWyM/Px5tvvgkzMzM8evQI3t7e2LJlC4YNGwZXV1e4ubkhODgYZ8+exXvvvYcZM2agsrISvXr1woULF3D16tVGFUIA4O7ujr1792Lu3Lkvfa1vvvkmACA5OfmFeU+dOhXz5s0DAAwZMgRhYWGIi4vD8OHDxReJCoKAkJAQDBgwAADwt7/9TXznzIviExERtWd8MkREr4SkpCTo6uoCAK5cuYKcnByUlpaK+x0dHTF48GB88803mDdvHiQSCfbu3QtPT08AQFRUFJ4+fYqAgADxmPz8fLz++uu4efMmbGxsYGxsDADikLpBgwY1Oj9dXV24u7u/9HUCzwqUmpiNybtmtbC/5mtubo6jR48CeDYfaeDAgXBzc0NISAimT58Of39/AI27L8o4c+ZM0y5aTeTm5gIAoqOjVZwJEREBLIaI6BXRq1cvHDt2DEeOHMHYsWPx+uuvIy0tTdwvkUjwySefwMvLCwkJCXBwcMDx48fx0UcfAQAuX74MIyOjBod+1cyvqflTVdLT0wEAb731VqPyroumpiYEQRC3g4KC4OrqCicnJ0yYMAGRkZHo0aNHk+PXZ+vWrdi6dWuzxGrP3NzcVJ0CERGBw+SI6BWxatUqrF27Fl9++SX+7//+D5qamrX6eHh4oFevXti8eTMuX74MCwsLcfEDTU1NXL9+vc2/w0cQBCQnJ0NTUxOTJk1qtrytrKyQnp6OhQsXIikpCcOHD0dxcXGz35d9+/ZBEAR+1fPl4uICFxcXlefRFr+IiFSBxRARtXl//PEH1q5di3fffVccElZdXV2rn5aWFhYvXoyTJ0/ik08+wfvvvy/uGzp0KB4/fowdO3YoHPPw4UMEBwe37AUoYcmSJUhLS8OmTZswdOjQZsm7vLwc33//PfT09LB9+3bEx8cjPz8fBw8efGXuCxERUUtgMUREbU5JSQmA/86dqfkzKioKpaWlSE5OxunTp/HgwQM8evQIMplMPNbX1xf6+vooKiqChYWF2O7m5gYTExP4+/tj06ZNuHr1KqKjozF//nzMmTMHAPD48WMAwP379+vM68GDBwCAsrKyWvvS0tIwcuRIJCUlNXhtt2/fBgA8ffq0VvuiRYvwj3/8A35+fliyZEmj866ZO/XX9yAVFRWhvLxc/K37jh07xN++29nZoXv37ujevXuj4hMREbVbAhFRC3JxcRFcXFwa3f/cuXOCvb29AEAYNmyYkJCQIAiCIHh5eQlSqVQYMGCAsGPHDmH//v2ClpaW8M477wj3799XiPHBBx8I27dvrxX7ypUrgpmZmQBAACBYWFgI6enpgiAIQmhoqNCrVy8BgDBz5kzh3LlzCscmJCQIbm5uAgDhf/7nf4Rdu3YJ+fn54v4DBw4IEolE2LVrV73XdvjwYWHcuHHi+W1tbYVJkyYJDg4OwvTp04WPP/5YSE1NVSrvpKQkoX///gIAwdvbW8jPzxeioqKELl26CACEzz//XJDJZIKRkZEwa9YsISYmRvj666+FwMDARsVXBgBh3759Sh+nTpT9PKgTfv8QkQpESwSBA3WJqOW4uroCAGJiYl46lkwmg56enrhdXl4uvlPor+zs7BAdHQ0DA4M642RnZ0MikcDU1PSlc/qr0tJSdOnSpVlj/tXL5F1ZWYnq6moUFBTUe/zL3heJRIJ9+/Zh5syZTTpeHTTn56G94fcPEalADFeTI6JXxl8LIQB1FkIXL15E//796y2EAKBPnz7NnhuAFi2EgJfLu2YhiYYKnZa6L0RERG0ViyEieuWlpaUhICAAQ4YMQVJSEmJjY1WdEhEREb0CWAwR0SuvuroaqampSEtLw65du9C3b19Vp0TUIiorK5GSkoJRo0YBAPLy8rB3717cu3cP9vb2GDduXJ3Lzr/Iw4cPsXv3bty5cwcODg6YMGFCrTgymQx79+7FH3/8gQEDBmD27Nno1KkTgGfvxnrttdf4dJGIXjlcTY6IXnnW1tYoLi5GcXGxOCeDqL0pKSnBpk2bMGTIEADPXiS8du1aeHh4wNnZGYGBgTA1NcWdO3eUiltcXIy//e1vuHjxIi5duoTJkyeLxVaN69evw8zMDJs3b8aWLVvg4+MDS0tLFBQUAAAsLS2xceNGnD59unkuloiolbAYIqJ2QSqVQkOD/6Spq4iIiFcydmPdvXsXc+bMwcKFC8W5c+vWrYOZmRmMjIxgY2ODdevWIS8vD5s2bVIqdnR0NFJSUhAREYETJ07g888/R0pKCn755Rexz5IlS3D06FHcuHEDubm58Pb2RlZWFlasWAHg2ecvKCgIGzduRGZmZvNdOBFRC+NPDkRE9EpLTEzE8uXLX7nYyli6dClmzJgBfX19sU1HRwehoaHito2NDQAgPz+/0XHlcjns7e3RrVs3sc3T0xPAfxcESUtLg4eHBywtLQEAhoaGWLNmDTQ0NPDrr7+Kx2lqamLp0qWYP39+E66QiEg1OGeIiIhURiaTISEhAVevXoWJiQns7OxgYmICAIiLi0NWVhY6d+4Mb29vyGQyREREoKKiAkZGRnBzc8PJkyfh5OQEiUSCnTt3wtjYGFOnTkVubi4OHz6MBQsW4NSpUzh69Ch69eqFefPmoWPHji8Vu6ioCLt27YKXlxd69OjR4vcoJSUF8fHxCoUPAAQHB+PPP/8Ut7OzswEA48ePb3RsLS0t9OvXT6EtIyMDjo6O4nC8vn37Yvjw4Qp9jIyMMGLECHGVwhoTJ07E4sWLcfDgQTg7Ozc6DyIiVeGTISIiUomLFy9i9OjR6NChAxYtWoSHDx/C3NxcHJY2depUhIaG4osvvgDwbGl1T09PrF69Gtu2bQMAdO3aFZaWltDW1sbAgQNhYmKCyMhIWFpawt/fHwsXLsT333+PjIwM+Pn5YezYsaioqGhybACIjY3FZ599hujo6Fa5T1999RVsbW1rLS2vo6OjsGBBbGwszM3N4ePj06TzCIKA6OhoLFu2DN9++63Y/tprr0EikdTqn5OTg8mTJ9dqHz16NNauXdukHIiIWhuLISIianVyuRyzZs3CjBkz4OzsDENDQ3z88ceYNm0afHx8cOXKFQDA4MGDFY7T09PDgAEDxG0rKysYGhpCR0cH48aNg5WVFTw8PODg4ICysjJ8+OGH2L17N+Lj47Fq1SqkpqYiLCysybEBwN3dHXv37sXcuXNb4tbUkpGRAWNj4wb7CIKA8PBwhIaGQktLS+lzPH78GL6+vnj//fdx5coVDBkyBKmpqfX2P336NKRSKZYsWVJrn4WFBTIzMyGXy5XOg4iotbEYIiKiVvfzzz/j2rVr4jyXGvb29pDL5di9e7dS8Z5/cqGrqwupVAoLCwuxbdmyZZBKpUqveFZXbHd391pPalqCXC7HrVu3YGRk1GC/48ePw97eHra2tk06j66uLkJCQiCTybBlyxbIZDIsWLCgzr5VVVUIDAzE4cOH0blz51r79fX1UVlZiZs3bzYpFyKi1sRiiIiIWl3Nk5/nf5geM2YMAODq1atKxatrGNfzOnXqhN69e6OwsLDZY7eU4uJiVFVVoWPHjg32S0xMxJo1a176fBoaGli8eDGcnZ1x/vx5lJeX1+rj7++PpUuXYtiwYXXGqPk7zc3Nfel8iIhaGoshIiJqdTWrl505c0ahvU+fPujQoQO6du2qVLzGFCzl5eUoKChA//79mz12S+nZsycMDAwgk8ka7Ne3b1+FleZe1qRJk9CtWzdoa2srtIeEhGDYsGGYNm1avcc+ePAAAMQ5VkREbRmLISIianVvvfUWANQasnbp0iVUVFSIw72kUinKysoajCWRSFBVVfXCc549exZlZWVwdHRs9tgtycLCAvfu3Wuwj6+vb7Oe89KlS5g6dapC248//ghBEMSlt2ucOnVKYTs/Px8SiaTWKnVERG0RiyEiImp1Q4cOxXvvvYfTp0/jzp07Yvt//vMfvPHGG+K7auzs7FBUVITw8HA8fvwY4eHhuH//Pm7duiU+gTAyMkJBQQFu3bqFrKwsPH78GABQWVmpMNxu//79GDt2rFgMNTV2WloaRo4ciaSkpNa4VRgzZkyDLzJNTk6Go6Ojwn2sMX/+fEyZMkVhCe6/evr0KdatW4dLly6Jbffv38f58+exZcsWse348eP48ssvUVFRgaCgIAQFBWHbtm3w9fVFRkaGQszbt2/Dzs4OOjo6yl4qEVGrYzFEREQqsWPHDnh6emLKlCn47rvvsHv3biQkJODEiRPiimiurq6wsbGBl5cXrK2tYWBggBEjRsDKygoHDhwQ+wiCgBEjRiAhIQG6uroAns1/CQ4ORkBAANzd3ZGdnY24uDjx/E2NnZ2djd9++63VFggICAhAXl4esrKy6tyfkpKChISEOvcnJibip59+wg8//FDnsdXV1Thw4AAsLS0xcuRIBAYGIjIyEgkJCeKwu/T0dDg5OeHcuXPw8/MTvxYvXoyIiAh4eHiI8eRyOQ4dOgR/f/9muHIiopYnEQRBUHUSRNR+ubq6AgBiYmJUnAm1NIlEgn379mHmzJlKHVdSUoLLly/D1NQUvXv3rrNPYWEhDA0NAQBlZWW1njqUlJRAQ0NDXOHtgw8+QFhYGORyOXJycqCvr48uXbo0S2wAKC0trTdeQ5r6edi5cycyMzMRFBRU5/7i4mJxHtZflZeX49ChQ9DR0Wlwns/Dhw+hpaWFTp06KZXX82JiYhAZGYnY2Filj23q9w8R0UuI4ZMhIiJSKX19fYwaNareQgiAWKwAqHP4lb6+fr1LXZuYmDRYuDQldlMKoZfh4+MjDl+rS12FEPCsGDpz5gymTJnSYHwDA4OXLoSuXbuGyMhIREVFvVQcIqLWxGKIiIjanSdPnqCyshKPHj1SdSrNQkNDA3v27MG3337b4MtQn5eSkoL169dDKpW2YHZAdnY2NmzYgLCwsBcuA05E1JawGCIionYlMjISx44dgyAI+PTTT3HhwgVVp9QstLW1ERISgh49ejT6mIkTJ7ZKcaKlpYU9e/bU+4SKiKitatlfFREREbUyR0dHODg4iNvPvyvnVWdqaqrqFGoxMjJSdQpERE3CYoiIiNqV5nz5KBERtW8cJkdERERERGqJxRAREREREaklFkNERERERKSWOGeIiFrc2bNnxZdNUvu2ZcsWvmC3AWfPngUAfh6IiNoIFkNE1KJsbW1VnQK1EhcXl0b1+/PPP3Hp0iVMmDChhTNqe2xsbFSdQpvl4uICExMTVadBRGpGIgiCoOokiIhIfURHR8PNzQ3874eIiFQshnOGiIiIiIhILbEYIiIiIiIitcRiiIiIiIiI1BKLISIiIiIiUksshoiIiIiISC2xGCIiIiIiIrXEYoiIiIiIiNQSiyEiIiIiIlJLLIaIiIiIiEgtsRgiIiIiIiK1xGKIiIiIiIjUEoshIiIiIiJSSyyGiIiIiIhILbEYIiIiIiIitcRiiIiIiIiI1BKLISIiIiIiUksshoiIiIiISC2xGCIiIiIiIrXEYoiIiIiIiNQSiyEiIiIiIlJLLIaIiIiIiEgtsRgiIiIiIiK1xGKIiIiIiIjUEoshIiIiIiJSSyyGiIiIiIhILbEYIiIiIiIitcRiiIiIiIiI1BKLISIiIiIiUksshoiIiIiISC2xGCIiIiIiIrXEYoiIiIiIiNQSiyEiIiIiIlJLLIaIiIiIiEgtSVWdABERtV95eXlwdHRERUWF2PbkyRPo6+tjyJAhCn2HDRuGiIiI1k6RiIjUGIshIiJqMcbGxpDL5bh8+XKtfSUlJQrbs2bNaq20iIiIAHCYHBERtTBPT09IpQ3/7k0ikWD27NmtlBEREdEzLIaIiKhFubu7o6qqqt79EokEI0aMQL9+/VoxKyIiIhZDRETUwkxMTGBjYwMNjbr/y9HU1ISnp2crZ0VERMRiiIiIWsGcOXMgkUjq3FddXY2ZM2e2ckZEREQshoiIqBW4urrW2a6pqYlx48ahR48erZwRERERiyEiImoF3bt3x4QJE6CpqVlr35w5c1SQEREREYshIiJqJe+++y4EQVBo09DQwIwZM1SUERERqTsWQ0RE1CqcnJzQoUMHcVsqlcLBwQH6+voqzIqIiNQZiyEiImoVenp6mDp1qlgQVVVV4d1331VxVkREpM5YDBERUavx8PBAZWUlAKBjx46YMmWKijMiIiJ1xmKIiIhazeTJk6GrqwsAcHFxQceOHVWcERERqTOpqhMgovbtzJkzyMnJUXUa1IZYW1vj5MmTMDExQXR0tKrToTZk1KhR6N27t6rTICI1IhGeX9qHiKgZubq6Yv/+/apOg4heAfv27eMLeImoNcVwmBwRtTgXFxcIgsCvdv4FPPth9kX9qqqqsH79epXnq4ovFxcXfh7q+SIiUgUWQ0RE1Ko0NDTwySefqDoNIiIiFkNERNT6pFJOWSUiItVjMURERERERGqJxRAREREREaklFkNERERERKSWWAwREREREZFaYjFERERtxq1bt+Dl5YXc3FxVp9ImVVZW4tdffxW38/Ly8PXXXyMgIAAnTpxAVVVVk+I+fPgQmzdvxkcffYRjx47VGUcmk2Hnzp1YtmwZQkND8eTJE3Ffeno6srOzm3RuIiJVYjFERERtRnp6OsLDw5GZmanqVNqckpISbNq0CUOGDAEAXL58GWvXroWHhwecnZ0RGBgIU1NT3LlzR6m4xcXF+Nvf/oaLFy/i0qVLmDx5MkaNGqXQ5/r16zAzM8PmzZuxZcsW+Pj4wNLSEgUFBQAAS0tLbNy4EadPn26eiyUiaiUshoiIqM1wcXFBYWEhJk+erLIcIiIiVHbu+ty9exdz5szBwoULoaenBwBYt24dzMzMYGRkBBsbG6xbtw55eXnYtGmTUrGjo6ORkpKCiIgInDhxAp9//jlSUlLwyy+/iH2WLFmCo0eP4saNG8jNzYW3tzeysrKwYsUKAM+WSg8KCsLGjRtZyBLRK4XFEBERtSndu3dX2bkTExOxfPlylZ2/PkuXLsWMGTOgr68vtuno6CA0NFTctrGxAQDk5+c3Oq5cLoe9vT26desmtnl6egIAunTpAgBIS0uDh4cHLC0tAQCGhoZYs2YNNDQ0FIbsaWpqYunSpZg/f34TrpCISDVYDBERUZtRXV2NkydPIjU1VWzLycnBtm3bUF1djUuXLmHdunX4/vvvUV1dLfbJzc1FcHAwBEFAUlISli9fjqCgIDx9+hQAEBcXh61bt4rFg0wmw/bt27F161bs27cPAHDy5Ek4OTnh0aNH2LlzJ+Li4gAARUVF2LBhA/7888/Wug0KUlJSEB8fDxcXF4X24OBgxMfHi9s1c3bGjx/f6NhaWlro16+fQltGRgYcHR3F4Xh9+/bF7NmzFfoYGRlhxIgR6Nq1q0L7xIkTIZPJcPDgwUbnQESkSnwFOBERtQlXrlzB6tWrsX//fnz77bewtrZGXFwc5s2bh8LCQgiCgIyMDBQWFmLlypXIzc3F8uXLERkZCT8/P5SVlSEzMxNyuRwFBQXYuHEjIiIi8Msvv2Dq1Kl48803UVJSAm9vb+jp6cHT0xO9e/eGhYUF3Nzc0LVrV1haWuLGjRsYOHAgDAwMAACxsbH47LPP0LlzZ/j5+bX6ffnqq69ga2srDo+roaOjgz59+ojbsbGxMDc3h4+PT5POIwgCYmJi8MUXX+Do0aNi+2uvvVZn/5ycHCxcuLBW++jRo7F27Vo4Ozs3KQ8iotbEJ0NERNQmmJubIzAwUKFt6tSpmDdvHgBgyJAhCAsLQ1xcHIYPH44DBw4AADw8PODg4ICysjJ8+OGH2L17N+Lj47Fq1SqkpqYiLCwMADB48GCF2Hp6ehgwYIC4bWVlBUNDQ+jo6GDcuHGwsrICALi7u2Pv3r2YO3duS116gzIyMmBsbNxgH0EQEB4ejtDQUGhpaSl9jsePH8PX1xfvv/8+rly5giFDhig8nXve6dOnIZVKsWTJklr7LCwsxKKUiKitYzFERERthra2dq22jh07AgAGDRoktpmbmyusmqarqwupVAoLCwuxbdmyZZBKpUqvcCaRSBS2dXV14e7uXuvJTGuQy+W4desWjIyMGux3/Phx2Nvbw9bWtknn0dXVRUhICGQyGbZs2QKZTIYFCxbU2beqqgqBgYE4fPgwOnfuXGu/vr4+KisrcfPmzSblQkTUmlgMERHRK0dTUxOCIDTYp1OnTujduzcKCwuViv18MaRKxcXFqKqqEgvC+iQmJmLNmjUvfT4NDQ0sXrwYzs7OOH/+PMrLy2v18ff3x9KlSzFs2LA6Y9QUSHxXFBG9ClgMERFRu1ReXo6CggL0799fqePaUjHUs2dPGBgYQCaTNdivb9++CivNvaxJkyahW7dutZ7UhYSEYNiwYZg2bVq9xz548AAAYGJi0mz5EBG1FBZDRETULp09exZlZWVwdHQE8OxdOGVlZQ0eI5FIUFVV1RrpNZqFhQXu3bvXYB9fX99mPeelS5cwdepUhbYff/wRgiCIS2/XOHXqlMJ2fn4+JBJJrVXqiIjaIhZDRETUZtQMyyoqKhLbSktLAUBhQn5RURHKy8sVhspVVlbi6tWr4vb+/fsxduxYsRiys7NDUVERwsPD8fjxY4SHh+P+/fu4deuW+DTDyMgIBQUFuHXrFrKysvD48WOkpaVh5MiRSEpKarHrbsiYMWMafJFpcnIyHB0dFeZQ1Zg/fz6mTJlS77LgT58+xbp163Dp0iWx7f79+zh//jy2bNkith0/fhxffvklKioqEBQUhKCgIGzbtg2+vr7IyMhQiHn79m3Y2dlBR0dH2UslImp1LIaIiKhNOHfunDjvZd++fYiPj8epU6fw448/AgDWr1+PgoIC/Otf/0JycjJkMhnWrFmDyspKAM/muwQHByMgIADu7u7Izs4W3xUEAK6urrCxsYGXlxesra1hYGCAESNGwMrKSlyZztXVFYIgYMSIEUhISICuri6ys7Px22+/qWxBgICAAOTl5SErK6vO/SkpKUhISKhzf2JiIn766Sf88MMPdR5bXV2NAwcOwNLSEiNHjkRgYCAiIyORkJAgDrtLT0+Hk5MTzp07Bz8/P/Fr8eLFiIiIgIeHhxhPLpfj0KFD8Pf3b4YrJyJqeRLhRTNQiYhegqurKwAgJiZGxZlQS5NIJNi3bx9mzpzZ6uf+4IMPEBYWBrlcjpycHOjr66NLly519i0sLIShoSEAoKysrNYTjJKSEmhoaCisHldaWlpvPGU09fOwc+dOZGZmIigoqM79xcXF6NatW6328vJyHDp0CDo6Og3O83n48CG0tLTQqVMnpfJ6XkxMDCIjIxEbG6v0sar8/iEitRXDJ0NERNSumJiYNFi41BRCAOocyqWvr19rGe3mKIReho+Pjzh8rS51FULAs2LozJkzmDJlSoPxDQwMXroQunbtGiIjIxEVFfVScYiIWpNU1QkQEf2VXC5HcnIyjhw5gkmTJr3wh7jWIpPJsHfvXvzxxx8YMGAAZs+erfQPj6dPn8bdu3cV2jp06ABDQ0MYGxvjjTfeaM6U1cqTJ09QWVmJR48e1fnum1edhoYG9uzZAz8/P/j4+MDa2rpRx6WkpGD9+vWQSlv2v/vs7Gxs2LABYWFhL1wGnIioLeGTISJqUy5duoTo6Ghs3boVeXl5qk4HAHD9+nWYmZlh8+bN2LJlC3x8fGBpaYmCggKl4lhaWiIrKwuzZ8/G3LlzUVpaisLCQsTFxcHNzQ39+vXDypUrUVFR0UJX0j5FRkbi2LFjEAQBn376KS5cuKDqlFqEtrY2QkJC0KNHj0YfM3HixFYpTrS0tLBnz556n1AREbVVLIaIqE0ZPnw4Fi1apOo0FCxZsgRHjx7FjRs3kJubC29vb2RlZWHFihVKxTEwMMDcuXMBAK+//jp8fX2xYMECfP3110hLS8OmTZvJYmmMAAAgAElEQVTwz3/+Ew4ODi98rwz9l6OjI65du4YHDx5g3bp1GDhwoKpTalGmpqaqTqEWIyOjNvV+JiKixmIxRERtTs2Qnrbww1VaWho8PDxgaWkJ4Nl8kzVr1kBDQwO//vqr0vHqm3sikUjg4uKCkJAQ/Pvf/8aYMWMUlpKm+unr68PAwED84jAtIiJqLM4ZIqJXxo0bN3D27FlkZGRg9OjRmDFjBgDgxIkTyMnJAfBsKJGzszO0tbWRkpKCK1euoGvXrpg+fToAIC8vDz///DNyc3MxevRoTJgwQYz/4MEDREVFYeHChfjpp5+QkZGBuXPnYvjw4Qp5GBkZYcSIEQrzMIqKirBr1y54eXkpNYzpeW5uboiIiEBCQgJSUlLw9ttvvzDvnJwcHDx4EH5+frhy5QoOHToEU1NTeHh4QEPj2e+8BEHAqVOncOHCBWhqamLQoEGYNGmSGKOh+ERERO0ViyEieiVs3boVhw4dQmJiIrKzszF+/HgUFBRgwYIFsLW1xUcffYTLly8jKysL2traAICRI0fivffew6FDhwAAJ0+eRFRUFBYsWAA9PT04OTnB09MT27dvx3fffYeFCxdCLpejuroaoaGhuHjxIiZPnlxncZOTk4OFCxeK27Gxsfjss8/QuXNn+Pn5vdS12tjYICEhAcnJyXj77bcbzDsuLg7z5s1DYWEhBEFARkYGCgsLsXLlSuTm5mL58uUAgJUrV6Jfv35YvHgxfvvtNyxatEgshhqKT0RE1K4JREQtyMXFRXBxcVHqmMuXLwsAhNDQULFtwIABwqJFi8RtJycnYcqUKeL24cOHBQDCrl27xLa8vDzx3DKZTOjfv7/w6NEjcf+8efMEAMKZM2cEQRAEDw8PAYBw8OBBQRAE4erVq3Xmd+rUKaF3796CTCYT2x49eiTs3btXKC0tbfDaSkpKBADC4MGD6+1z8OBBAYAwefLkRuW9bNkyAYBw/Phxsc/w4cOFESNGCIIgCNXV1UL37t2FkydPivvXrl3b6PvSWACEffv2KXWMumnK50Fd8PuHiFQgmk+GiOiVkJSUBF1dXQDAlStXkJOTg9LSUnG/o6MjBg8ejG+++Qbz5s2DRCLB3r174enpCQCIiorC06dPERAQIB6Tn5+P119/HTdv3oSNjQ2MjY0BQBxSN2jQoFp5VFVVITAwEIcPH1ZYwllXVxfu7u7Ncq2PHj0SYzYm75o5Mn/N19zcHEePHgXwbD7SwIED4ebmhpCQEEyfPh3+/v6Nvi/K2LJlC1+w24CzZ88C+O/LV4mISLVYDBHRK6FXr144duwYjhw5grFjx+L1119HWlqauF8ikeCTTz6Bl5cXEhIS4ODggOPHj+Ojjz4CAFy+fBlGRkYNDv2qmV9T82dd/P39sXTpUgwbNqyZrqy29PR0AMBbb73VqLzroqmpCUEQxO2goCC4urrCyckJEyZMQGRkJHr06NHk+ERERO0BiyEieiWsWrUKp06dwtGjR9GxY0ccOHCgVh8PDw+sWrUKmzdvRt++fWFhYSEucqCpqYnr16+joqICHTp0aFIOISEhGDZsGKZNm/ZS19IQQRCQnJwMTU1NTJo0CRERES+dNwBYWVkhPT0dy5Ytw86dOzF8+HBkZmY2y335qyVLlmDmzJkvHae9qnkixKdntbWF1SOJSP1waW0iavP++OMPrF27Fu+++644JKy6urpWPy0tLSxevBgnT57EJ598gvfff1/cN3ToUDx+/Bg7duxQOObhw4cIDg5+YQ4//vgjBEEQh93VOHXqVFMuqV5LliwR3zk0dOjQl84bAMrLy/H9999DT08P27dvR3x8PPLz83Hw4MFmiU9ERPSqYjFERG1OSUkJgP/Onan5MyoqCqWlpUhOTsbp06fx4MEDPHr0SOEFpb6+vtDX10dRUREsLCzEdjc3N5iYmMDf3x+bNm3C1atXER0djfnz52POnDkAgMePHwMA7t+/r5DP8ePH8eWXX6KiogJBQUEICgrCtm3b4Ovri4yMDADP3kc0cuRIJCUlNXhtt2/fBgA8ffq0VvuiRYvwj3/8A35+fliyZEmj866ZO/XX9xIVFRWhvLwcgiBAEATs2LFDHDZnZ2eH7t27o3v37o2KT0RE1G6pcvkGImr/lF0969y5c4K9vb0AQBg2bJiQkJAgCIIgeHl5CVKpVBgwYICwY8cOYf/+/YKWlpbwzjvvCPfv31eI8cEHHwjbt2+vFfvKlSuCmZmZAEAAIFhYWAjp6emCIAhCaGio0KtXLwGAMHPmTOHcuXOCIAhCWlqaoKurKx7z1y8dHR3x3AcOHBAkEonCanbPO3z4sDBu3DjxeFtbW2HSpEmCg4ODMH36dOHjjz8WUlNTlco7KSlJ6N+/vwBA8Pb2FvLz84WoqCihS5cuAgDh888/F2QymWBkZCTMmjVLiImJEb7++mshMDCwUfGVAa4G9kJcTa5+/P4hIhWIlgjCX2bYEhE1s+acIyGTyaCnpydul5eXi+8U+is7OztER0fDwMCgzjjZ2dmQSCQwNTV96Zz+qrS0FF26dGnWmH/1MnlXVlaiuroaBQUF9R7/svdFIpFg3759nDPUAM4Zqh+/f4hIBWK4gAIRvTL+WggBqLMQunjxIvr3719vIQQAffr0afbcALRoIQS8XN41C0k0VOi01H0hIiJqq1gMEdErLy0tDQEBARgyZAiSkpIQGxur6pSIWkRlZSVSUlIwatQoAEBeXh727t2Le/fuwd7eHuPGjYOmpmaT4xcUFODatWsYN25cg/0uXryI06dPQ0tLCw4ODrh37x5ee+01FtRE9MrhAgpE9Mqrrq5Gamoq9uzZgxUrVqBv376qTomo2ZWUlGDTpk0YMmQIgGfvzlq7di08PDzg7OyMwMBAmJqa4s6dO0rHLiwshL+/P/r3748ff/yx3n5FRUXw9vbG8uXLMX36dPj6+qJ3796wtLTExo0bcfr06SZfHxGRKrAYIqJXnrW1NYqLi1FcXCzOySD1EhER8UrGbqy7d+9izpw5WLhwoThcdN26dTAzM4ORkRFsbGywbt065OXlYdOmTUrHv337Njw9PWutcvh8n8GDB6O8vBwJCQkKQy6lUimCgoKwceNGZGZmKn+BREQqwmKIiNoFqVQKDQ3+k6aOEhMTsXz58lcutjKWLl2KGTNmQF9fX2zT0dFBaGiouG1jYwMAyM/PVzq+tbU1Bg0aVO9+uVyOmTNnolu3brXeSVVDU1MTS5cuxfz585U+PxGRqnDOEBERqYxMJkNCQgKuXr0KExMT2NnZwcTEBAAQFxeHrKwsdO7cGd7e3pDJZIiIiEBFRQWMjIzg5uaGkydPwsnJCRKJBDt37oSxsTGmTp2K3NxcHD58GAsWLMCpU6dw9OhR9OrVC/PmzUPHjh1fKnZRURF27doFLy8v9OjRo8XvUUpKCuLj4xUKHwAIDg7Gn3/+KW5nZ2cDAMaPH9/sOaxYsQKpqakIDQ2Frq5uvf0mTpyIxYsX4+DBg3B2dm72PIiImht/jUpERCpx8eJFjB49Gh06dMCiRYvw8OFDmJubi8PSpk6ditDQUHzxxRcAnq0m6OnpidWrV2Pbtm0AgK5du8LS0hLa2toYOHAgTExM8P/s3XlUFGe+PvCnoVkUEPTqUQygonEjIuqooPGiicIIqOgFEYnGi0GNxhsXQjTjkvG6TcyiuYhiWFyCDOCCIaBxFFAnAUFJBNcZZUQQSMCFRYVmeX9/+KMmLTtCN9LP5xzPnHrr7W99u5Qxj1X1VlhYGKytreHr64ulS5fi0KFDSE9Px/Lly2Fvb4+KiooW1waA6OhofPLJJ4iMjFTJefrss89gZ2dXazVFfX19pQULoqOjMXToUPj4+LR6D+Hh4ZDL5cjIyMBbb70FQ0ND/Od//ifS0tJqzR0/fjw2b97c6j0QEbUFhiEiIlI5hUKBOXPmYObMmZg1axZ69OiB1atXY/r06fDx8cH169cBAEOGDFH6nJGREQYMGCBt29jYoEePHtDX18fEiRNhY2MDLy8vODs7o6ysDB988AGCg4MRGxuL9evXIzU1FSEhIS2uDQCenp44fPgwFixY0Banppb09HT07t27wTlCCISGhiIoKAi6urqtevz79+/j/v37eOONN7BhwwbEx8cjLS0Nt2/fhr29Pe7fv68038rKChkZGVAoFK3aBxFRW2AYIiIilTt16hRu3rwpPedSw9HREQqFAsHBwc2qJ5PJlLYNDAwgl8thZWUlja1ZswZyubzZK57VVdvT07PWlZq2oFAokJmZCVNT0wbnnTlzBo6OjrCzs2v1Hmqu/ri6uqJbt24AgIEDB+LLL79EaWkpAgIClOYbGxujsrISt2/fbvVeiIhaG8MQERGpXM2VH0NDQ6XxCRMmAABu3LjRrHovBpa6dO7cGWZmZigoKGj12m3l4cOHqKqqQqdOnRqcFx8fj02bNrVJDzWLNnTv3l1pvCZ43bp1S2m85vc0JyenTfohImpNDENERKRyNVcYkpKSlMb79OkDHR0ddO3atVn1mhJYysvLkZ+fD0tLy1av3VZ69eoFExMTlJSUNDivb9++SivNtaaBAwcCeP5y49+zsLCAjo5OrStkjx49AgDpGSsiovaMYYiIiFRu7NixAFDrlrWrV6+ioqJCuuogl8tRVlbWYC2ZTIaqqqpGj5mcnIyysjK4uLi0eu22ZGVlhd9++63BOYsXL26z4/fq1QuOjo5ITk5WGv/nP/+JiooKjB8/Xmk8Ly8PMpkM/fr1a7OeiIhaC8MQERGp3PDhw/Huu+/i/PnzuHfvnjT+97//Ha+//rr0rhoHBwcUFhYiNDQUT548QWhoKB48eIDMzEzpCoSpqSny8/ORmZmJO3fu4MmTJwCAyspKpdvtjhw5Ant7eykMtbT25cuXMWbMGCQmJqriVGHChAkNvsj0woULcHFxUTqPNRYtWgQnJyelJbjrU/Od6wqIX3zxBbKzs/HTTz9JYwkJCRgyZEithSTu3r0LBwcH6OvrN3pMIiJ1YxgiIiK12Lt3L+bPnw8nJyccOHAAwcHBiIuLw9mzZ6UV0dzd3WFrawtvb2+MHj0aJiYmGDVqFGxsbHD06FFpjhACo0aNQlxcnPQeHC0tLQQEBMDPzw+enp7IyspCTEyMdPyW1s7KysKlS5dUtkCAn58fcnNzcefOnTr3p6SkIC4urs798fHxOHnyJL799tsGj3Hy5El8+OGHAJ4v0R0UFIT8/Hxpv5WVFX788Uds2LABGzduxNatW/H999/j7NmzkMv//cpChUKBEydOwNfXtyVflYhI5WRCCKHuJoio43J3dwcAREVFqbkTamsymQwRERGYPXt2sz5XVFSEa9euwcLCAmZmZnXOKSgoQI8ePQA8v3Lx4lWHoqIiaGlpSc+vLFmyBCEhIVAoFMjOzoaxsTG6dOnSKrUBoLi4uN56DWnpz0NgYCAyMjLg7+9f5/6HDx9Kz2H9Xnl5OU6cOAF9fX1Mnz692f3WJTc3F506darzua6oqCiEhYUhOjq62XVb+ueHiOglRPHKEBERqZWxsTHGjRtXbxACIIUVAHXefmVsbFzvUtfm5uYNBpeW1G5JEHoZPj4+ePDgAX7++ec699cVhIDnYSgpKQlOTk6t1kvv3r3rDEI3b95EWFgYwsPDW+1YRERtjWGIiIg6nKdPn6KyshKlpaXqbqVVaGlpYf/+/dizZw9SU1Ob/LmUlBRs3bpV6Va2tpCVlYVt27YhJCSk0WXAiYjaE4YhIiLqUMLCwnD69GkIIfDxxx/jl19+UXdLrUJPTw/79u1Dz549m/yZyZMnqySc6OrqYv/+/fVeoSIiaq/a9p+KiIiIVMzFxQXOzs7Stp6enhq7aX0WFhbqbqEWU1NTdbdARNQiDENERNShtNXLR4mIqOPhbXJERERERKSRGIaIiIiIiEgjMQwREREREZFGYhgiIiIiIiKNxAUUiKjNHTlyBDKZTN1tkAp4eHjAw8ND3W20e/x5ICJqH2RCCKHuJoio40pKSkJ2dra626B2JCkpCTt37kRERIS6W6F2Zty4cTAzM1N3G0SkOaIYhoiISKUiIyPh4eEB/vVDRERqFsVnhoiIiIiISCMxDBERERERkUZiGCIiIiIiIo3EMERERERERBqJYYiIiIiIiDQSwxAREREREWkkhiEiIiIiItJIDENERERERKSRGIaIiIiIiEgjMQwREREREZFGYhgiIiIiIiKNxDBEREREREQaiWGIiIiIiIg0EsMQERERERFpJIYhIiIiIiLSSAxDRERERESkkRiGiIiIiIhIIzEMERERERGRRmIYIiIiIiIijcQwREREREREGolhiIiIiIiINBLDEBERERERaSSGISIiIiIi0kgMQ0REREREpJEYhoiIiIiISCMxDBERERERkUZiGCIiIiIiIo3EMERERERERBqJYYiIiIiIiDQSwxAREREREWkkhiEiIiIiItJIDENERERERKSR5OpugIiIOq6ysjLk5uYqjf36668AgMzMTKVxbW1t9OnTR2W9ERERyYQQQt1NEBFRx/To0SP07NkTFRUVjc51cnJCbGysCroiIiICAETxNjkiImozXbt2hYODA7S0Gv/rZs6cOSroiIiI6N8YhoiIqE298847aOwmBD09PcycOVNFHRERET3HMERERG1q+vTp0NfXr3e/XC7H9OnTYWhoqMKuiIiIGIaIiKiNde7cGTNnzoSOjk6d+6uqquDl5aXiroiIiBiGiIhIBebOnVvvIgoGBgb44x//qOKOiIiIGIaIiEgFHBwcYGxsXGtcR0cHHh4e0NPTU0NXRESk6RiGiIiozeno6GDOnDnQ1dVVGq+oqMDcuXPV1BUREWk6hiEiIlIJT09PKBQKpbHu3bvD3t5eTR0REZGmYxgiIiKVmDBhAnr27Clt6+joYN68edDW1lZjV0REpMkYhoiISCW0tLQwb9486Va5iooKeHp6qrkrIiLSZAxDRESkMnPmzJFulTM3N8cf/vAHNXdERESajGGIiIhUZtSoURgwYAAAYMGCBZDJZGruiIiINJlc3Q0QUcf25ZdfIikpSd1tUDtSc5vcxYsX4e7uruZuqD1ZtWoV7Ozs1N0GEWkQXhkiojaVlJSE5ORkdbdBKnDkyBHk5OQ0Os/CwgImJibo0qWLCrpqX5KTk/nzUI8jR44gOztb3W0QkYbhlSEianO2traIiopSdxvUxmQyGVauXInZs2c3OvfMmTOYPHmyCrpqX2quhPHnoTbeMklE6sArQ0REpHKaGISIiKj9YRgiIiIiIiKNxDBEREREREQaiWGIiIiIiIg0EsMQERERERFpJIYhIiJqNzIzM+Ht7d2kJbo1UWVlJX766SdpOzc3F59//jn8/Pxw9uxZVFVVvVT9/Px8JCYmNjrvypUr+L//+z8EBgYiJycHaWlpyMrKeqljExGpA8MQERG1G2lpaQgNDUVGRoa6W2l3ioqKsGPHDgwbNgwAcO3aNWze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4+nTp8jKykKvXr3qfIYrKioKYWFhiI6ObtmXeEFL//wQEb2EKF4ZIiIitTI2Nsa4cePqDUIApLACoM5bsoyNjetd6trc3LzB4NKS2i0JQq3Jx8cHDx48wM8//1zn/rqCEPA8DCUlJcHJyanRY3Tu3BlDhgypMwjdvHkTYWFhCA8Pb17jRETtDMMQERF1OE+fPkVlZSVKS0vV3Uqb0NLSwv79+7Fnzx6kpqY2+XMpKSnYunWrtFJcS2RlZWHbtm0ICQlpdIlvIqL2jmGIiIg6lLCwMJw+fRpCCHz88cf45Zdf1N1Sm9DT08O+ffvQs2fPJn9m8uTJLx1gdHV1sX///nqvPhERvUpa/k9DRERE7ZCLiwucnZ2lbT09PTV20/YsLCxUejxTU1OVHo+IqC0xDBERUYfS0peNEhGR5uFtckREREREpJEYhoiIiIiISCMxDBERERERkUbiM0NE1OZycnIQGRmp7jZIBZKSktTdQruWk5MDAPx5ICJqJ2RCCKHuJoio43J3d8eRI0fU3QYRvQIiIiIwe/ZsdbdBRJojimGIiIhUKjIyEh4eHuBfP0REpGZRfGaIiIiIiIg0EsMQERERERFpJIYhIiIiIiLSSAxDRERERESkkRiGiIiIiIhIIzEMERERERGRRmIYIiIiIiIijcQwREREREREGolhiIiIiIiINBLDEBERERERaSSGISIiIiIi0kgMQ0REREREpJEYhoiIiIiISCMxDBERERERkUZiGCIiIiIiIo3EMERERERERBqJYYiIiIiIiDQSwxAREREREWkkhiEiIiIiItJIDENERERERKSRGIaIiIiIiEgjMQwREREREZFGYhgiIiIiIiKNxDBEREREREQaiWGIiIiIiIg0EsMQERERERFpJIYhIiIiIiLSSAxDRERERESkkRiGiIiIiIhIIzEMERERERGRRmIYIiIiIiIijcQwREREREREGolhiIiIiIiINJJc3Q0QEVHH9dtvvyE0NFRpLD09HQDwl7/8RWm8W7du8PHxUVlvREREMiGEUHcTRETUMVVWVqJXr1549OgRdHR06p1XXl6OxYsXY+/evSrsjoiINFwUb5MjIqI2I5fL4enpCW1tbZSXl9f7CwDmzp2r5m6JiEjTMAwREVGb8vT0REVFRYNzevXqhTfffFNFHRERET3HMERERG3Kzs4OZmZm9e7X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
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
<h3 id="4.2.3-Training-MLP-Model">4.2.3 Training MLP Model<a class="anchor-link" href="#4.2.3-Training-MLP-Model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">BATCH_SIZE</span> <span class="o">=</span> <span class="mi">64</span>
<span class="n">EPOCHS</span> <span class="o">=</span> <span class="mi">30</span>
<span class="n">VAL_SPLIT</span> <span class="o">=</span> <span class="mf">0.25</span>

<span class="n">history</span> <span class="o">=</span> <span class="n">train_model</span><span class="p">(</span><span class="n">MLP_model</span><span class="p">,</span> <span class="s1">&#39;adam&#39;</span><span class="p">,</span> <span class="n">BATCH_SIZE</span><span class="p">,</span> <span class="n">EPOCHS</span><span class="p">,</span> <span class="n">VAL_SPLIT</span><span class="p">,</span> 
                      <span class="n">inputs</span><span class="o">=</span><span class="p">[</span><span class="n">train_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">train_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">],</span>
                      <span class="n">outputs</span><span class="o">=</span><span class="n">train_df</span><span class="p">[</span><span class="s1">&#39;rating&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Epoch 1/30
946/946 [==============================] - 4s 4ms/step - loss: 2.2333 - mean_squared_error: 2.2333 - rmse: 1.2535 - val_loss: 0.7952 - val_mean_squared_error: 0.7952 - val_rmse: 0.8858
Epoch 2/30
946/946 [==============================] - 4s 4ms/step - loss: 0.7322 - mean_squared_error: 0.7322 - rmse: 0.8506 - val_loss: 0.7890 - val_mean_squared_error: 0.7890 - val_rmse: 0.8831
Epoch 3/30
946/946 [==============================] - 5s 5ms/step - loss: 0.6892 - mean_squared_error: 0.6892 - rmse: 0.8252 - val_loss: 0.7744 - val_mean_squared_error: 0.7744 - val_rmse: 0.8746
Epoch 4/30
946/946 [==============================] - 4s 4ms/step - loss: 0.6594 - mean_squared_error: 0.6594 - rmse: 0.8071 - val_loss: 0.7609 - val_mean_squared_error: 0.7609 - val_rmse: 0.8663
Epoch 5/30
946/946 [==============================] - 4s 4ms/step - loss: 0.6321 - mean_squared_error: 0.6321 - rmse: 0.7902 - val_loss: 0.7681 - val_mean_squared_error: 0.7681 - val_rmse: 0.8703
Epoch 6/30
946/946 [==============================] - 4s 4ms/step - loss: 0.6032 - mean_squared_error: 0.6032 - rmse: 0.7714 - val_loss: 0.7688 - val_mean_squared_error: 0.7688 - val_rmse: 0.8710
Epoch 7/30
946/946 [==============================] - 4s 4ms/step - loss: 0.5757 - mean_squared_error: 0.5757 - rmse: 0.7540 - val_loss: 0.7781 - val_mean_squared_error: 0.7781 - val_rmse: 0.8765
Epoch 8/30
946/946 [==============================] - 5s 5ms/step - loss: 0.5501 - mean_squared_error: 0.5501 - rmse: 0.7368 - val_loss: 0.8027 - val_mean_squared_error: 0.8027 - val_rmse: 0.8901
Epoch 9/30
946/946 [==============================] - 5s 5ms/step - loss: 0.5263 - mean_squared_error: 0.5263 - rmse: 0.7206 - val_loss: 0.8193 - val_mean_squared_error: 0.8193 - val_rmse: 0.8991
Epoch 10/30
946/946 [==============================] - 4s 4ms/step - loss: 0.5009 - mean_squared_error: 0.5009 - rmse: 0.7027 - val_loss: 0.8252 - val_mean_squared_error: 0.8252 - val_rmse: 0.9023
Epoch 11/30
946/946 [==============================] - 4s 5ms/step - loss: 0.4759 - mean_squared_error: 0.4759 - rmse: 0.6853 - val_loss: 0.8310 - val_mean_squared_error: 0.8310 - val_rmse: 0.9051
Epoch 12/30
946/946 [==============================] - 5s 5ms/step - loss: 0.4513 - mean_squared_error: 0.4513 - rmse: 0.6672 - val_loss: 0.8506 - val_mean_squared_error: 0.8506 - val_rmse: 0.9158
Epoch 13/30
946/946 [==============================] - 7s 7ms/step - loss: 0.4266 - mean_squared_error: 0.4266 - rmse: 0.6483 - val_loss: 0.8709 - val_mean_squared_error: 0.8709 - val_rmse: 0.9269
Epoch 14/30
946/946 [==============================] - 14s 14ms/step - loss: 0.4028 - mean_squared_error: 0.4028 - rmse: 0.6304 - val_loss: 0.8792 - val_mean_squared_error: 0.8792 - val_rmse: 0.9308- loss: 0.3773 - mean_squared_ - ETA: 9s - loss: 0.3791 - mean_squared_error: 0.3791 - rmse: 0 - ETA: 9s - loss: 0.3820 - mean_squ - ETA: 7s - loss: 0.38 - ETA: 3s - loss: 0.3946 - mean_squared_error: 0.39 - ETA: 2s - loss: 0.3961 - mean_s
Epoch 00014: early stopping
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.2.4-Plotting-MLP-Learning-Curve">4.2.4 Plotting MLP Learning Curve<a class="anchor-link" href="#4.2.4-Plotting-MLP-Learning-Curve">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[28]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">learning_plot</span><span class="p">(</span><span class="n">history</span><span class="p">,</span> <span class="s1">&#39;rmse&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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lCm1LqPXsd9rw37vfPZ5bdjvtWG/d75a9nlEtLh6qVM4JEmSpBIM0JIkSVIJBmhJkiSphG43B1qSJKkrefvtt1m8eDFr1qypdSk90vbbb8/ChQur+hkDBgxg5MiR9OvXb7PaG6AlSZK2wuLFixkyZAj19fVERK3L6XFWrFjBkCFDqnb+zOSll15i8eLFjB49erPe4xQOSZKkrbBmzRp23HFHw3M3FRHsuOOOpX6DYICWJEnaSobn7q3sz88ALUmSJJVggJYkSerGXn31Vb7//e9v0XuPO+44Xn311TbbnHfeedx0001bdP6eygAtSZLUiWbPhvp66NOneJ49e+vO11aAXrduXZvvvf766xk6dGibbb7xjW9w1FFHbXF9rWmvtq7MAC1JktRJZs+GmTPh6achs3ieOXPrQvSXv/xlnnjiCSZMmMCXvvQl5s6dy9SpU/noRz/KuHHjADjxxBM58MAD2X///Zk1a9aG99bX17N8+XIWLVrEmDFj+NSnPsX+++/PMcccwxtvvAHAGWecwVVXXbWh/fnnn8+kSZMYN24cDz/8MADLli3j6KOPZtKkSXz6059m1KhRLF++fJNaBw8ezHnnncd73vMe5s2bR319PV/96lc55JBDmDx5Mvfccw/ve9/72HvvvbnssssAeP755zn88MOZMGECY8eO5fbbbwfgxhtv5JBDDmHSpEmccsoprFy5css7sSQDtCRJUif52tdg9eqm+1avLvZvqW9+85vsvffe3HfffXzrW98C4C9/+QsXXnghCxYsAODyyy9n/vz53H333Vx66aW89NJLm5znscce4+yzz+ahhx5i6NChXH311S1+3vDhw7nnnns466yzuOiiiwD4+te/zrRp07jnnnv44Ac/yDPPPNPie1etWsXYsWO58847OeywwwDYY489mDdvHu9973s3hPU77riD8847D4Bf/OIXvO997+O+++7j/vvvZ8KECSxfvpx/+qd/4qabbuKee+5h8uTJfPvb397yTizJ+0BLkiR1klZyZav7t9RBBx3U5J7Gl156Kddeey0Azz77LI899hg77rhjk/eMHj2aCRMmAHDggQeyaNGiFs990kknbWhzzTXXAPDHP/5xw/mnT5/OsGHDWnxvXV0dH/rQh5rsO/744wEYN24cK1euZMiQIQwZMoQBAwbw6quvMmnSJM455xzefvttTjzxRCZMmMCtt97KggULOPTQQwF46623OOSQQza7f7aWI9CboaPnKkmSpN5pzz3L7d9SgwYN2vB67ty53HTTTcybN4/777+fiRMntnjP4/79+294XVdXx9q1a1s8d0O7xm0yc7PqGjBgAHV1dS2er0+fPk1q6NOnD2vXruXQQw/ltttuY/fdd+f000/npz/9KZnJ0UcfzX333cd9993HggUL+M///M/NqqEjGKDbUY25SpIkqXe68EIYOLDpvoEDi/1basiQIaxYsaLV46+99hrDhg1j4MCBPPzww9xxxx1b/mGtOOyww7jyyiuBYm7yK6+80mHnfuaZZ9h555351Kc+xSc/+UnuueceDj74YP70pz/x+OOPA7B69WoeffTRDvvM9hig21GNuUqSJKl3mjEDZs2CUaMgonieNavYv6V23HFHDj30UMaOHcuXvvSlTY5Pnz6dtWvXMn78eP7xH/+Rgw8+eCu+QcvOP/98brzxRiZNmsRvf/tbdt111w5bfvv2229nwoQJTJw4kauvvprPfe5z7LTTTlxxxRWcdtppjB8/noMPPnjDBY2dITZ3yL2rmDx5ct59992d9nl9+hQjz81FwPr1nVbGVpk7dy5TpkypdRm9jv1eG/Z757PPa8N+r42W+n3hwoWMGTOmNgV1EW+++SZ1dXX07duXefPmcdZZZ3Hfffd1yLlXrFjRYWG8LS39HCNifmZObt7WiwjbseeexbSNlvZLkiSpmGbx4Q9/mPXr17PNNtvwwx/+sNYlVZUBuh0XXljMeW48jWNr5ypJkiT1JPvssw/33ntvrcvoNM6Bbkc15ipJkiSp+3IEejPMmGFgliRJUsERaEmSJKkEA7QkSZJUggFakiSplxk8eDAAS5Ys4eSTT26xzZQpU2jv1sGXXHIJqxvdaeG4447j1Vdf7bhCuygDtCRJUi+12267cdVVV23x+5sH6Ouvv56hQ4d2RGkbtLakeC0ZoCVJkrqxv//7v+f73//+hu0LLriAiy++mJUrV3LkkUcyadIkxo0bx69+9atN3rto0SLGjh0LwBtvvMGpp57K+PHj+chHPsIbb7yxod1ZZ53F5MmT2X///Tn//PMBuPTSS1myZAlTp05l6tSpANTX17N8+XIAvv3tbzN27FjGjh3LJZdcsuHzxowZw6c+9Sn2339/jjnmmCaf0+CMM87gi1/8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
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
<h3 id="4.2.5-MLP-Model-on-Test-Set">4.2.5 MLP Model on Test Set<a class="anchor-link" href="#4.2.5-MLP-Model-on-Test-Set">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Building Architecture &amp; Loading Weights</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[29]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">MLP_model</span> <span class="o">=</span> <span class="n">build_MLP_model</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">,</span> <span class="p">[</span><span class="mi">64</span><span class="p">,</span> <span class="mi">32</span><span class="p">,</span> <span class="mi">16</span><span class="p">,</span> <span class="mi">8</span><span class="p">],</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">])</span>
<span class="n">MLP_model</span> <span class="o">=</span> <span class="n">load_trained_model</span><span class="p">(</span><span class="n">MLP_model</span><span class="p">,</span> <span class="s1">&#39;model_tmp/model.hdf5&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Making Preictions</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[30]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">predictions</span> <span class="o">=</span> <span class="n">MLP_model</span><span class="o">.</span><span class="n">predict</span><span class="p">([</span><span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Test-Set RMSE</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[31]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">error</span> <span class="o">=</span> <span class="n">rmse</span><span class="p">(</span><span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;rating&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">predictions</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The test-set RMSE of rating predictions is&#39;</span><span class="p">,</span> <span class="nb">round</span><span class="p">(</span><span class="n">error</span><span class="p">,</span> <span class="mi">4</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>The test-set RMSE of rating predictions is 0.8721
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="4.3-Fusion-Model">4.3 Fusion Model<a class="anchor-link" href="#4.3-Fusion-Model">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.3.1-Model-Building-Function">4.3.1 Model Building Function<a class="anchor-link" href="#4.3.1-Model-Building-Function">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[32]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">build_Fusion_model</span><span class="p">(</span><span class="n">num_users</span><span class="p">,</span> <span class="n">num_items</span><span class="p">,</span> <span class="n">MF_dim</span><span class="p">,</span> <span class="n">MF_reg</span><span class="p">,</span> <span class="n">MLP_layers</span><span class="p">,</span> <span class="n">MLP_regs</span><span class="p">):</span>

    <span class="k">assert</span> <span class="nb">len</span><span class="p">(</span><span class="n">MLP_layers</span><span class="p">)</span> <span class="o">==</span> <span class="nb">len</span><span class="p">(</span><span class="n">MLP_regs</span><span class="p">)</span>
    <span class="n">num_MLP_layer</span> <span class="o">=</span> <span class="nb">len</span><span class="p">(</span><span class="n">MLP_layers</span><span class="p">)</span>
    
    <span class="c1"># Input Layers</span>
    <span class="n">user_input</span> <span class="o">=</span> <span class="n">Input</span><span class="p">(</span><span class="n">shape</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,),</span> <span class="n">dtype</span><span class="o">=</span><span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;user_input&#39;</span><span class="p">)</span>
    <span class="n">item_input</span> <span class="o">=</span> <span class="n">Input</span><span class="p">(</span><span class="n">shape</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,),</span> <span class="n">dtype</span><span class="o">=</span><span class="s1">&#39;int32&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;item_input&#39;</span><span class="p">)</span>
    
    <span class="c1"># MF Embedding Layers</span>
    <span class="n">MF_Embedding_User</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_users</span> <span class="o">+</span> <span class="mi">1</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">MF_dim</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;mf_user_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">MF_reg</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
    
    <span class="n">MF_Embedding_Item</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_items</span> <span class="o">+</span> <span class="mi">1</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">MF_dim</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;mf_item_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">MF_reg</span><span class="p">[</span><span class="mi">1</span><span class="p">]),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
    
    <span class="c1"># MLP Embedding Layers</span>
    <span class="n">MLP_Embedding_User</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_users</span> <span class="o">+</span> <span class="mi">1</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">MLP_layers</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">//</span> <span class="mi">2</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;mlp_user_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">MLP_regs</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
    
    <span class="n">MLP_Embedding_Item</span> <span class="o">=</span> <span class="n">Embedding</span><span class="p">(</span>
        <span class="n">input_dim</span><span class="o">=</span><span class="n">num_items</span> <span class="o">+</span> <span class="mi">1</span><span class="p">,</span>
        <span class="n">output_dim</span><span class="o">=</span><span class="n">MLP_layers</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">//</span> <span class="mi">2</span><span class="p">,</span>
        <span class="n">embeddings_initializer</span><span class="o">=</span><span class="s1">&#39;uniform&#39;</span><span class="p">,</span>
        <span class="n">name</span><span class="o">=</span><span class="s1">&#39;mlp_item_embedding&#39;</span><span class="p">,</span>
        <span class="n">embeddings_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">MLP_regs</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span>
        <span class="n">input_length</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span> 
    
    <span class="c1"># MF Multiplication</span>
    <span class="n">mf_user_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MF_Embedding_User</span><span class="p">(</span><span class="n">user_input</span><span class="p">))</span>
    <span class="n">mf_item_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MF_Embedding_Item</span><span class="p">(</span><span class="n">item_input</span><span class="p">))</span>
    <span class="n">mf_vector</span> <span class="o">=</span> <span class="n">Multiply</span><span class="p">()([</span><span class="n">mf_user_latent</span><span class="p">,</span> <span class="n">mf_item_latent</span><span class="p">])</span>

    <span class="c1"># MLP Concatenation</span>
    <span class="n">mlp_user_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MLP_Embedding_User</span><span class="p">(</span><span class="n">user_input</span><span class="p">))</span>
    <span class="n">mlp_item_latent</span> <span class="o">=</span> <span class="n">Flatten</span><span class="p">()(</span><span class="n">MLP_Embedding_Item</span><span class="p">(</span><span class="n">item_input</span><span class="p">))</span>
    <span class="n">mlp_vector</span> <span class="o">=</span> <span class="n">Concatenate</span><span class="p">(</span><span class="n">axis</span><span class="o">=-</span><span class="mi">1</span><span class="p">)([</span><span class="n">mlp_user_latent</span><span class="p">,</span> <span class="n">mlp_item_latent</span><span class="p">])</span>
    
    <span class="c1"># MLP Layer Extensions</span>
    <span class="k">for</span> <span class="n">idx</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">num_MLP_layer</span><span class="p">):</span>
        <span class="n">layer</span> <span class="o">=</span> <span class="n">Dense</span><span class="p">(</span>
            <span class="n">units</span><span class="o">=</span><span class="n">MLP_layers</span><span class="p">[</span><span class="n">idx</span><span class="p">],</span>
            <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;relu&#39;</span><span class="p">,</span>
            <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;glorot_uniform&#39;</span><span class="p">,</span>
            <span class="n">kernel_regularizer</span><span class="o">=</span><span class="n">l2</span><span class="p">(</span><span class="n">MLP_regs</span><span class="p">[</span><span class="n">idx</span><span class="p">]),</span>
            <span class="n">name</span> <span class="o">=</span> <span class="s1">&#39;layer</span><span class="si">%d</span><span class="s1">&#39;</span> <span class="o">%</span><span class="k">idx</span>)
        <span class="n">mlp_vector</span> <span class="o">=</span> <span class="n">layer</span><span class="p">(</span><span class="n">mlp_vector</span><span class="p">)</span>
    
    <span class="c1"># Concatenate MF and MLP </span>
    <span class="n">predict_vector</span> <span class="o">=</span> <span class="n">Concatenate</span><span class="p">(</span><span class="n">axis</span><span class="o">=-</span><span class="mi">1</span><span class="p">)([</span><span class="n">mf_vector</span><span class="p">,</span> <span class="n">mlp_vector</span><span class="p">])</span>

    <span class="c1"># Final prediction Layer</span>
    <span class="n">prediction</span> <span class="o">=</span> <span class="n">Dense</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;glorot_uniform&#39;</span><span class="p">,</span> <span class="n">name</span><span class="o">=</span><span class="s1">&#39;prediction&#39;</span><span class="p">)(</span><span class="n">predict_vector</span><span class="p">)</span>
    
    <span class="c1"># Final Model</span>
    <span class="n">model</span> <span class="o">=</span> <span class="n">Model</span><span class="p">([</span><span class="n">user_input</span><span class="p">,</span> <span class="n">item_input</span><span class="p">],</span> <span class="n">prediction</span><span class="p">)</span>
    
    <span class="k">return</span> <span class="n">model</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.3.2-Building-Fusion-Model">4.3.2 Building Fusion Model<a class="anchor-link" href="#4.3.2-Building-Fusion-Model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[33]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fusion_model</span> <span class="o">=</span> <span class="n">build_Fusion_model</span><span class="p">(</span>
    <span class="n">num_users</span><span class="o">=</span><span class="n">num_users</span><span class="p">,</span>
    <span class="n">num_items</span><span class="o">=</span><span class="n">num_items</span><span class="p">,</span>
    <span class="n">MF_dim</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span>
    <span class="n">MF_reg</span><span class="o">=</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">),</span>
    <span class="n">MLP_layers</span><span class="o">=</span><span class="p">[</span><span class="mi">64</span><span class="p">,</span> <span class="mi">32</span><span class="p">,</span> <span class="mi">16</span><span class="p">,</span> <span class="mi">8</span><span class="p">],</span>
    <span class="n">MLP_regs</span><span class="o">=</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">])</span>

<span class="n">fusion_model</span><span class="o">.</span><span class="n">summary</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Model: &#34;model_4&#34;
__________________________________________________________________________________________________
Layer (type)                    Output Shape         Param #     Connected to                     
==================================================================================================
user_input (InputLayer)         [(None, 1)]          0                                            
__________________________________________________________________________________________________
item_input (InputLayer)         [(None, 1)]          0                                            
__________________________________________________________________________________________________
mlp_user_embedding (Embedding)  (None, 1, 32)        19552       user_input[0][0]                 
__________________________________________________________________________________________________
mlp_item_embedding (Embedding)  (None, 1, 32)        311200      item_input[0][0]                 
__________________________________________________________________________________________________
flatten_10 (Flatten)            (None, 32)           0           mlp_user_embedding[0][0]         
__________________________________________________________________________________________________
flatten_11 (Flatten)            (None, 32)           0           mlp_item_embedding[0][0]         
__________________________________________________________________________________________________
concatenate_2 (Concatenate)     (None, 64)           0           flatten_10[0][0]                 
                                                                 flatten_11[0][0]                 
__________________________________________________________________________________________________
mf_user_embedding (Embedding)   (None, 1, 10)        6110        user_input[0][0]                 
__________________________________________________________________________________________________
mf_item_embedding (Embedding)   (None, 1, 10)        97250       item_input[0][0]                 
__________________________________________________________________________________________________
layer1 (Dense)                  (None, 32)           2080        concatenate_2[0][0]              
__________________________________________________________________________________________________
flatten_8 (Flatten)             (None, 10)           0           mf_user_embedding[0][0]          
__________________________________________________________________________________________________
flatten_9 (Flatten)             (None, 10)           0           mf_item_embedding[0][0]          
__________________________________________________________________________________________________
layer2 (Dense)                  (None, 16)           528         layer1[0][0]                     
__________________________________________________________________________________________________
multiply_2 (Multiply)           (None, 10)           0           flatten_8[0][0]                  
                                                                 flatten_9[0][0]                  
__________________________________________________________________________________________________
layer3 (Dense)                  (None, 8)            136         layer2[0][0]                     
__________________________________________________________________________________________________
concatenate_3 (Concatenate)     (None, 18)           0           multiply_2[0][0]                 
                                                                 layer3[0][0]                     
__________________________________________________________________________________________________
prediction (Dense)              (None, 1)            19          concatenate_3[0][0]              
==================================================================================================
Total params: 436,875
Trainable params: 436,875
Non-trainable params: 0
__________________________________________________________________________________________________
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[34]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plot_model</span><span class="p">(</span><span class="n">fusion_model</span><span class="p">,</span>  <span class="n">to_file</span><span class="o">=</span><span class="s1">&#39;fusion_model.png&#39;</span><span class="p">,</span><span class="n">show_shapes</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[34]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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+OADTZgwQaNHj5anp2eB9hkdHa3XX39dDg5F/ygUFxenBQsWaM2aNapevbp1+bFjx/TZZ5/p/PnzSk5O5p4cAAAAAMqFitor6ZQAUHqYdASAQoiJidG8efM0d+5cubm5mR2nwPbu3auff/451zIXFxf16dPHpES/+fzzz3X16tVcy9q3by93d3eTEpVPa9eu1eeffy7DMDR9+nSNHj1aHh4eZscqMUOHDtXQoUPzXF+1alWtXLlS58+fL/A+S+KyNY6Ojvrggw9ksVhyLW/btq3atm0rSXrnnXeKfRwAAADcW3npauUl5x/RKSu+itwr6ZQAUHq4vCoAFMLBgwcVGhqqo0ePmh2lULp06aLq1avrqaee0lNPPaWkpCT16NHD7Fj685//rP379+upp57SM888o4ceekjNmzc3O1a54+Pjo1OnTun69euaP3++WrZsaXYkUzRs2LBUj+fq6npHOQQAAIA5yktXKy85/4hOWfHRK+mUAFASmHQEgEIYPHiwEhMTTT2bMywsrNDPcXR01IABA+Ti4iJJevrpp3NduqM0/T5/3bp15e/vL0ny8PDQ448/LkdHR1NylWfOzs5ycXGx/pj13xYAAAAwS15drSj9yZbolMVHp7QNeiUAoCQw6QgAhfTAAw+Yduxdu3ZpxowZRXquxWKx3sTd2dm5JGMV2N3y52RycnIyIxIAAACACuKPXa04/cmW6JRFR6cEAKBs456OAMqU8PBwnT17VjVq1NCoUaOUkpKisLAw3b59W66urvLz85MkGYahr776SocOHZK9vb1atWql//mf/7Hu5+LFi/rss88UHx8vb29vPfHEE9Z1169f1/r16zV+/Hh9+umnOnLkiF5++eUC3fw7OztbX331lWrUqGG9ufiFCxe0bds2TZgwQSdOnNCOHTvUsGFDjRgxQnZ2v53bER8fr48//ljjxo3TV199pX//+9+qX7++AgICVL169QK97t27d2vgwIGyWCx6//33Va9ePfn6+iopKUmrVq3SyJEj9eCDDxb6PTc7f2GdPn1a+/fv15EjR+Tt7a0nn3xSkvTll1/qwoULkn67H8OgQYNUtWpVRUdH68SJE6pdu7YGDBggyXa/HwAAAADM8ceull//yK8P3Lp1Szt27FD//v115coV7dy50/pce3t7Xb58WR9//LHs7Ow0ZMgQ1apVq1g5JfM7GZ2STgkAQIkxAMCGBg8ebAwePLhQz3F3dzfc3Nysj5OTk41atWoZXl5e1mUzZ840Vq1aZRiGYRw4cMDo3Lmzdd2uXbuM0aNHGwcPHjQ2bdpk1KhRwxg/frxhGIbxwQcfGPfdd5/h4OBgvPvuu0aHDh0MScbhw4fvmev48ePG4MGDDUnGihUrDMMwjI8//tioW7euIclYsmSJ8fzzzxs+Pj6GJOP11183DMMwPvroI6N27dpG9erVjbFjxxojR440+vbta0gyPD09jYyMjAK97h9++MHw9vY26tata+zevdv44YcfDMMwjFWrVhmSjHfeeeeer6FBgwaGJCMrK6vM5P/xxx8NScZjjz12z/xLliwxevToYWRnZxvnzp0zGjdubCxfvtwwDMNITU013N3dDUnG2bNncz2vVatWxo8//mgYhu1+PwyjaL/vlc3GjRsNPn7cmyRj48aNZscAAAAwTWE+D92tq+XVP/LrA3v27DGaN29uSDLeeustY8yYMca0adOM++67z/jb3/5mrFq1yhgxYoQxbNgww2KxGL6+voV6TXRKOuW90JcKhr50b/z7BACzMIoBsKmifMgZPHhwrqJhGIbRsWNHa9HIzs42HnjgAWP37t3W9fPmzTMMwzBSUlKMpk2bGjdv3rSuCwgIMCQZUVFRhmEYxogRIwxJxrZt2wzDMIyTJ08WONuRI0dyFUTDMIzAwEBDkvHFF1/kytupUyfr46efftqwWCzGsWPHrMtmzZplSDLee++9Ar1uwzCMgQMHGg0aNMi1zc2bN41169YZycnJ98z/x4JYFvIXpiA2a9bMePHFF3Ptr2/fvtbHH3/8sSHJOiFtGIZx8eJF6++grX8/+FB/b5TogqFEAwCAyq6wn4fu1tX+2D8K0gfefvttQ5KxefNm6zY5nWnr1q3WZf/4xz+MqlWr5upWRc1pdiejU5adTklfKhj60r3x7xMAzMI9HQGUOxaLRS1btpSfn5927NghSXrllVckSevXr9etW7c0bdo0vfjii3rxxRd16dIlPfzww/rpp58kSfXq1ZMk62VRWrVqVeBjV61a9Y5lOTdX//1+2rRpo/Pnz1sfOzk5ycHBQe7u7tZlgYGBcnBw0N69ewt8fOm31/97Tk5OGj58uPU+FoVldv7C2LNnj+bNmydJOnHihC5cuKAzZ85Y1/v4+Kh169Z6++23ZRiGJGndunXy9/eXZPvfD0nasmWLLBYLP3n85Fwi2ewcZf0HAAAAhXO3ribl7h8F6QM59yps166d9XktW7aUJHXo0MG6rFWrVkpPT9fFixeLndPsTkanLFudMuc18pN/X/Lz8zM9R1n+2bJlSxH/XwIAxcPFxAGUS0uXLtWQIUM0cOBAPfHEE1q7dq0efPBBHT9+XK6urlq2bFmez825p0TO/9qCvb29taDk5b777pObm5sSExMLte+cD9i2VFbz169fX59//rk++eQTde/eXQ8//LC+//77XPueOnWqRo4cqZ07d6pfv3764osvNHHiREkqld+PLl26aPLkyUV6bmUQFRWloKAgbdy40ewoZVrO5CwAAACK5/f9oyB94G6qVat2x7IqVapIklJTU4sXMA9ltZMVVFnNXx46pST60j34+flp0qRJ8vLyMjtKmbVkyRKzIwCopJh0BFAueXh46ODBgwoMDNT777+vjh076ujRo7K3t9ePP/6o27dvW0tgWZWenq6EhAT17t27UM8rjYJYEKWZ/8qVK3J2dta8efP01Vdf6d///reqV6+urVu33rHtiBEjNGvWLL311ltq3Lix3N3d5eDw23BXGr8fbm5uGjp0qE32XVEEBQXxHt0Dk44AAAAl4/f9ozz1xYKgUxZceeqUkuhL9+Dn5ycvLy/ep3xs3rzZ7AgAKikurwqgzHFwcFBaWlqe69PT0/Xhhx+qZs2aWrZsmSIiInTp0iVt27ZNHTp0UGpqqt57771cz/nll1+0fPlyW0cvlP379ystLU0+Pj6S7v26pd/KVVZWVmnEu6fSzD969GhduHBB8+bN09NPP229fE92dvYd2zo6OmrSpEnavXu3pk6dqueff966rjz9fgAAAAAonj/2j4rWB+iUBUenBACgdDDpCKDM6dWrl5KSkhQaGqrU1FSFhobq6tWriomJ0fXr12UYht577z3rpVp69eqlBx54QA888ID8/PzUoEEDvfLKK1q8eLFOnjypTZs2acyYMXrmmWck/ffyN1evXi10tvT0dElSUlKSdVlycrIkKSMjw7osKSlJ6enpuS4nk5mZqZMnT1ofb9myRd27d7cWrHu9bklydXVVQkKCYmJidPbsWaWmpur7779X586dtWfPnnvmz8ma879lIX9cXNwdx8/x66+/6u9//7scHBx069YtSb/dQyM5OVn79u3T3r17df36dd28eVMpKSnW573wwgtydnZWUlJSrnuG2Pr3AwAAAIA57tbV/tg/fHx87tkHcnpFzv4k6ebNm5Kka9euWZfl9Ibfb1fUnGZ3MjolnRIAgBJjAIANDR482Bg8eHChnpOSkmJ06dLFkGS0bt3a2LZtmzFo0CCjd+/exqpVq4xbt24Zrq6uxrBhw4zNmzcbb775pjF79mzr80+cOGG0aNHCkGRIMtzd3Y2DBw8ahmEYISEhRv369Q1JxtChQ41vv/22wLn2799vDB482JBktG3b1vjkk0+MPXv2GE2bNjUkGaNGjTIuXbpkrF+/3qhVq5YhyZgzZ45x+/Zt44UXXjDs7e2Nl156yZg6daoxbNgww9fX10hOTi7w6zYMw9i9e7fh4OBguLi4GO+8845hGIaxdetWw2KxWLe5m//85z/GqFGjrO/JoEGDjK1bt5qef+3atUbnzp0NSYbFYjEeeeQR44knnjC6du1quLu7G1WqVDEkGStXrjQMwzBGjhxpODg4GM2aNTPee+89Y8uWLYajo6Px17/+1bh69Wqu1zx27Fhj2bJld7wXtvr9MIyi/b5XNhs3bjT4+HFvkoyNGzeaHQMAAMA0hfk8dLeuZhh370/59YFvvvnG6NChgyHJePbZZ42YmBhj9+7dRseOHQ1JRr9+/Yzjx48b33zzjbX7DB061Dh9+nSRc5rdyQyDTlmWOiV9qWDoS/fGv08AMIvFMO5xV2cAKIYhQ4ZIKtq15BMTE1W3bl1JUlpamqpVq2Zdl5mZqezsbCUkJKhhw4Z3fX5cXJwsFkue60vT2LFjtWbNGmVkZOjChQtydnZWrVq17rptfq9bkm7cuCE7OzvVrFnTuiw5OTnP/ZWH/IWRkpKS67np6emqWrXqHdv16tVLmzZtkouLy133Y4vfj+L8vlcWmzZtkp+fn/j4kT+LxaKNGzdyjxIAAFBpldTnobz6R1nqiwVBp8w/f2GU5U5JXyoY+tK98e8TAMziYHYAAMhLTsmQdEfJyLmJe34f7hs1alTgY40fP/6e24wZM0YeHh4F3mdeGjRokO/6/F63JDk7O9+xzJbl8I9skb8w/lgs71YODx8+rKZNm+ZZDqXC/X4AAAAAKJ/y6h8l3QfolAVHpwQAoOJi0hEAJD3++OP33Ob3xaewfv31V2VmZurmzZuqUaNGkfdjlvKQ//vvv9e0adPUrl077dmzR9u3bzc7EkpIbGysoqKirI9btGihTp065domMzNT0dHR6tq1qyTp4sWLWrduna5cuaLevXurR48esre3L3KGhIQEnTp1Sj169LAuO3jwoOrUqXPHPzbExMTo22+/tT5u2bKlOnbsWORjAwAAoOyjU+avPOSnU1ZcdEoAKD1MOgKA/nvZCVtYu3atPv/8cxmGoenTp2v06NElcnZraSkv+bOzs3XgwAF9//33WrVqlRo3bmx2JJSQr7/+Wk8//bTWr1+vHj16yMnJKdf6GzduaPny5XrppZckScePH9eyZcs0a9YsxcXF6eWXX7aWzMJe+igxMVGLFi3S8uXLNXr06FwFsX379powYYKGDx+uxx57zLr8wQcfVNeuXXXhwgX99a9/1UsvvURBBAAAqODolHkrL/nplBUXnRIASg+TjgBgYz4+PurXr5/18d0u3VKWlZf8np6eunbtmuzs7GRnZ2d2HFOEhYXJ39+/3O27oPr06XPHpZR+/vlnjRs3Th9++KH1Mknz589X586d5erqKldXV82fP1+PP/64Fi9erHfffbdQx4yNjZW/v7/eeuutO9Y5ODho6dKl8vX1Ve3atdWuXTtJkpOTk5ycnNSoUSPVr1+/iK8WAAAA+E156WR5KS/56ZR0SjolABRf5RxBAaAUOTs7y8XFxfpTvXp1syMVSnnK7+DgUGnL4a5duzRjxoxyt+/imjJlip588slcxbFatWoKCQmxPu7SpYsk6dKlS4Xev6enp1q1apXnent7e02ZMkVjxowp9L4BAACAgihPnexuylN+OiWdUqJTAkBx8E1HAABMlpKSop07d+rkyZNq0KCBevXqpQYNGkiSwsPDdfbsWdWoUUOjRo1SSkqKwsLCdPv2bbm6usrPz0+7d+/WwIEDZbFY9P7776tevXry9fVVfHy8Pv74Y40bN05fffWV/v3vf6t+/foKCAhQ9erVi7XvpKQkrVq1SiNHjtSDDz5oyvsWHR2tiIiIXGVQkpYvX67Lly9bH8fFxUkq2H12iqJnz56aNGmStm3bpkGDBtnkGAAAAACQFzpl0dApAaDkVc5TdwAAKCMOHz4sb29vValSRS+++KJ++eUXtWnTRmFhYZIkX19fhYSE6P/+7/8kSTVr1pS/v79ee+01BQcHS5Jq166t9u3bq2rVqmrZ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9dXLL79sPXf16lVJsu6JCQAAAOQ1zHQEAAAowAoXLqwBAwZoxowZzHYEAGTI3r17dfv2bQUEBEiSnJycdPv27QdeY7FYdPfu3dwIL8N8fX0fOvZ17949S22XLl1ajRs31t69e1OV//rrr7pz547q1aunDRs2KDIyMtXP+++/r1KlSikyMlKbN29Ode2FCxdksVj05JNPZikmAAAAIKeRdAQAACjgevbsKXd3d02ZMsXWoQAAckhCQoIkKSYmxlp248YNSff2N0wRExOjhISEVEusJiUlKTw83Hq8cuVKNWjQwJp0bNSokWJiYrRgwQLFx8drwYIFunz5ss6cOWOdnefl5aXo6GidOXNGp0+fVnx8vMLCwvTcc89px44dOfa6H6R+/fo6fPhwuud3796tgICAVHtcpujWrZuaNGmiixcvpnv9pEmTdO7cOf3444/Wsu3bt6tKlSrq2LFjpuM9e/asGjVqJDc3t0xfCwAAAOQGko4AAAAFnLu7uz766CN9/vnnmd6fCwCQ9/33v/+17ku4bNkybdy4UTt37tQ333wjSRo9erSio6P173//W7t371ZsbKxGjBihpKQkSZKDg4NCQkIUHBystm3bKiIiQuvXr7e237p1a/n7+6tTp06qU6eOihUrptq1a6tGjRpatWqVtY4xRrVr11ZoaKjc3d0VERGhn376SadOncrlO3JPcHCwoqKidPr06TTP79u3T6GhoWme37ZtmzZt2qSvv/463fZ9fX31ww8/aPjw4frkk080evRobdiwQVu3bpWTU+Z2u0lMTNTatWs1YMCATF0HAAAA5CaLedgO8QAAALB78fHxeuqpp9S5c2eNHj3a1uEAyIDWrVtLklasWGHjSJDTLBaLli1bpjZt2uR63z169ND8+fOVmJioc+fOydPTU0WLFk2z7qVLl1SqVClJ0u3bt++bkXf9+nU5ODioSJEi1rIbN26k215mZPX3YdasWTp8+LCmT5+e5vkrV66oRIkS95UnJCRo7dq1cnNzU/PmzR/aT1RUlAoVKqTixYtnKr4UK1as0OLFi7VmzZpMX2vLzw8AAAAKFmY6AgAAQO7u7urXrx+zHQEA6SpXrtwDE4QpCUdJaS4B6unpmSrhKClbEo6PomvXrrp8+bJ+/vnnNM+nlXCU7iUd9+zZoyZNmmSonzJlymQ54Xj8+HEtXrxYS5cu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u3cbHQUAHmjUqFGqWLGi0TEAAAAAoEBQOgIAAKDYat26tdq1a8dqRwDFAtvyAgAAACjJKB0BAABQrE2fPl07d+5URESE0VEAAAAAAABKLUpHAAAAFGvt2rVT27ZtNWvWLKOjAAAAAAAAlFqUjgAAACj2pk+fru3bt2vPnj1GRwEAAAAAACiVKB0BAABQ7D3zzDP65z//qbfeesvoKAAAAAAAAKUSpSMAAABKBD8/P3377besdgRQ5Jw5c0ZDhgxRXFyc0VGKnPT0dP3www+W1xcvXtS7774rX19fbd++XXfu3MnVvNeuXdN7772n1157TVu3bs1ynqSkJC1dulQTJ05UQECA/vjjD8uxgwcPKjY2Nlf3BgAAAEorSkcAAACUCM8++6z++c9/avbs2UZHAYBMDh48qJUrVyo6OtroKEXK9evXNX/+fDVp0kSS9PPPP2v27Nny9vZW79695efnJ3d3d/366685mvfKlSt64okndOTIER09elSdOnXSU089lemcX375RQ0aNNB7772nBQsWaPjw4fL09FR8fLwkydPTU/PmzVNERET+vFkAAACgFKB0BAAAQIkxbdo0bd26Vd99953RUQDAok+fPkpISFCnTp0My7B69WrD7p2VCxcu6MUXX9To0aPl7OwsSfL391eDBg3k5uamli1byt/fXxcvXtT8+fNzNHdQUJAiIyO1evVqbd++XTNmzFBkZKS+//57yznjx4/Xli1bFBMTo7i4OA0bNkynT5/WlClTJEk2NjZatGiR5s2bR1kMAAAAPCRKRwAAAJQY7du3V5s2beTv7290FADIpFKlSobde8eOHZo0aZJh98/KhAkT1KtXL7m4uFjGHBwcFBAQYHndsmVLSdKlS5ceet7U1FR17NhRFSpUsIwNGjRIklSuXDlJ0oEDB+Tt7S1PT09JUuXKlTVr1ixZWVll2urV2tpaEyZM0IgRI3LxDgEAAIDSh9IRAAAAJcrUqVP1zTffZFrRAgBGysjI0M6dO7V//37L2Pnz57Vw4UJlZGTo6NGj8vf312effaaMjAzLOXFxcVqyZInMZrN27dqlSZMmadGiRbp9+7YkKTQ0VB988IGlqEtKStLixYv1wQcfaN26dZKknTt3qmfPnrp586aWLl2q0NBQSVJiYqLmzp2r3377rbA+BovIyEiFhYWpT58+mcaXLFmisLAwy+u7z1R85plnHnpuOzs71a5dO9NYVFSUunbtatnGtVatWho4cGCmc9zc3OTl5aXy5ctnGm/fvr2SkpK0cePGh84AAAAAlFY2RgcAAAAA8lOHDh0woACXAAAgAElEQVT09NNPy9/fX+Hh4UbHAVDKHTt2TNOnT9eXX36pjz76SE8++aRCQ0M1dOhQJSQkyGw2KyoqSgkJCZo6dari4uI0adIkBQYGauzYsUpOTlZ0dLRSU1MVHx+vefPmafXq1fr+++/VrVs3PfbYY7p+/bqGDRsmZ2dnDRo0SNWrV5eHh4f69++v8uXLy9PTUzExMWrYsKFcXV0lScHBwZo8ebKcnJw0duzYQv1M3nnnHbVq1cqyrepdDg4OqlmzpuV1cHCwGjdurOHDh+fqPmazWevXr9fMmTO1ZcsWy3jFihWzPP/8+fMaPXr0PeOtW7fW7Nmz1bt371zlAAAAAEoLVjoCAACgxJkyZYq+/vprRUZGGh0FQCnXuHFj+fn5ZRrr1q2bhg4dKklq0qSJVqxYodDQUDVv3lwbNmyQJHl7e6tLly5KTk7Wq6++quXLlyssLEzTpk3T/v37tWLFCklSo0aNMs3t7OysevXqWV43bdpUlStXloODg9q1a6emTZtKkgYMGKA1a9Zo8ODBBfXW7ysqKkrVqlXL9hyz2ayVK1cqICBAdnZ2Ob7HrVu3NHLkSL388ss6duyYmjRpkmml6d9FRETIxsZG48ePv+eYh4eHpfgFAAAAcH+UjgAAAChx/v3vf6t169aaNWuW0VEAQPb29veMlSlTRpL06KOPWsYaN26sX3/91fLa0dFRNjY28vDwsIxNnDhRNjY2ioiIyFEGk8mU6bWjo6MGDBhwz2rDgpaamqozZ87Izc0t2/O2bdumjh07qlWrVrm6j6Ojo5YtW6akpCQtWLBASUlJGjVqVJbn3rlzR35+ftq8ebOcnJzuOe7i4qL09HSdOnUqV1kAAACA0oLSEQAAACXSlClTFBYWxmpHAMWGtbW1zGZztueULVtW1atXV0JCQo7m/nvpaJQrV67ozp07ltL1fnbs2JEvvzhiZWWlcePGqXfv3jp06JBSUlLuOcfHx0cTJkxQs2bNspzjbhEZFxeX5zwAAABASUbpCAAAgBKpU6dOatGihd566y2jowBAvklJSVF8fLzq1KmTo+uKSulYtWpVubq6KikpKdvzatWqJRcXl3y773PPPacKFSrcs+p02bJlatasmbp3737fa69evSpJqlGjRr7lAQAAAEoiSkcAAACUWH5+fvrqq6+yfY4XABQn+/btU3Jysrp27SpJsrGxUXJycrbXmEwm3blzpzDiPRQPDw/9/vvv2Z4zcuTIfL3n0aNH1a1bt0xjmzZtktls1qBBgzKN7969O9PrS5cuyWQyqXbt2vmaCQAAAChpKB0BAABQYnXp0kUtWrTQ7NmzjY4CoBS7u6VnYmKiZezGjRuS/nzG4V2JiYlKSUnJtMVqenq6jh8/bnn95Zdfqm3btpbSsUOHDkpMTNTKlSt169YtrVy5UpcvX9aZM2csK/Tc3NwUHx+vM2fO6PTp07p165YOHDigFi1aaNeuXQX2vu+nTZs2io6Ovu/xPXv2qGvXrpmeb3nXiBEj1LlzZ/32229ZXnv79m35+/vr6NGjlrHLly/r0KFDWrBggWVs27Ztevvtt5WWlqZFixZp0aJFWrhwoUaOHKmoqKhMc547d04dOnSQg4NDTt8qAAAAUKpQOgIAAKBEmzZtmjZv3sxqRwCG+PHHHy3PJly3bp3CwsK0e/dubdq0SZI0Z84cxcfH64svvtCePXuUlJSkWbNmKT09XdKfzyRcsmSJfH19NWDAAMXGxio0NNQyf9++fdWyZUsNGTJETz75pFxdXeXl5aWmTZtqw4YNlnPMZrO8vLwUHh4uR0dHxcbG6qefftKpU6cK+RORfH19dfHiRZ0+fTrL45GRkQoPD8/y+I4dO/T111/r888/z/LajIwMbdiwQZ6enmrRooX8/PwUGBio8PBwy3atBw8eVM+ePfXjjz9q7Nixlq9x48Zp9erV8vb2tsyXmpqqkJAQ+fj45MM7BwAAAEo2k/lBT6kHAAAAirkWLVqoWrVqCg4ONjoKSgiTyaR169apX79+RkdBAQoKClL//v1l1F+bX3nlFa1YsUKpqak6f/68XFxcVK5cuSzPTUhIUOXKlSVJycnJ96zKu379uqysrOTs7GwZu3Hjxn3ny4ncfD8sXbpU0dHRWrRoUZbHr1y5ogoVKtwznpKSopCQEDk4OGT7HMZr167Jzs5OZcuWfehMWVm/fr0CAwNz9f8fRv/5AQAAAAobKx0BAABQ4k2dOlWbN2/WTz/9ZHQUAMiVGjVqZFsQ3i0cJWW5DaiLi0umwlFSvhSOuTV8+HDLtqdZyapwlP4sHffu3avOnTtnO7+rq2ueC8cTJ04oMDBQa9euzdM8AAAAQGlhY3QAAAAAoKB1795dTzzxhObMmaONGzcaHQelTGpqqvbs2aOvvvpKzz333APLksKSlJSkNWvW6OzZs6pXr54GDhyY45ImIiJCFy5cyDRma2urypUrq1q1aqpfv35+Ri51/vjjD6Wnp+vmzZtycnIyOk6+srKy0qpVqzR27FgNHz5cTz755ENdFxkZqTlz5sjGpmB/nBEbG6u5c+dqxYoVKlOmTIHeCwAAACgpWOkIAACAUmHKlCkKDg7WkSNHjI6CUubo0aMKCgrSBx98oIsXLxodR5L0yy+/qEGDBnrvvfe0YMECDR8+XJ6enoqPj8/RPJ6enjp9+rQGDhyowYMH68aNG0pISFBoaKj69++v2rVra+rUqUpLSyugd1JyBQYGauvWrTKbzXrzzTd1+PBhoyPlO3t7ey1btkxVqlR56Gvat29fKCWgnZ2dVq1add8VlwAAAADuRekIAACAUqF79+7y8vLSrFmzjI6CUqZ58+YaM2aM0TEyGT9+vLZs2aKYmBjFxcVp2LBhOn36tKZMmZKjeVxdXTV48GBJUt26dTVy5EiNGjVK7777rg4cOKD58+frww8/VJcuXZSUlFQA76Tk6tq1q06cOKGrV6/K399fDRs2NDpSgXF3dzc6wj3c3NxkMpmMjgEAAAAUK5SOAAAAKBVMJpMmT56sTZs2sdoRhe7uVpBFocQ4cOCAvL295enpKenPZwHOmjVLVlZW+uGHH3I83/2eC2gymdSnTx8tW7ZM3377rdq0aaPU1NQ8ZS9NXFxc5Orqavlii08AAAAARR3PdAQAAECp0bNnT3l6emr27Nlav3690XEAxcTEaN++fYqKilLr1q3Vq1cvSdL27dt1/vx5SX9uQdm7d2/Z29srMjJSx44dU/ny5dWjRw9J0sWLF/XNN98oLi5OrVu31rPPPmuZ/+rVq1q7dq1Gjx6tr7/+WlFRURo8eLCaN2+eKYebm5u8vLwyPScvMTFRn3zyiYYMGZKj7S//rn///lq9erXCw8MVGRmpp59++oG5z58/r40bN2rs2LE6duyYQkJC5O7uLm9vb1lZ/fm7s2azWbt379bhw4dlbW2tRx99VM8995xljuzmBwAAAADkP0pHAAAAlBomk0l+fn7q06ePoqKiLCu9ACN88MEHCgkJ0Y4dOxQbG6tnnnlG8fHxGjVqlFq1aqXXXntNP//8s06fPi17e3tJUosWLfTSSy8pJCREkrRz506tXbtWo0aNkrOzs3r27KlBgwZp8eLF+vTTTzV69GilpqYqIyNDAQEBOnLkiDp16pRliXj+/HmNHj3a8jo4OFiTJ0+Wk5OTxo4dm6f32rJlS4WHh2vPnj16+umns80dGhqqoUOHKiEhQWazWVFRUUpISNDUqVMVFxenSZMmSZKmTp2q2rVra9y4cfrpp580ZswYS+mY3fwAAAAAgILB9qoAAAAoVXr16iVPT0/5+/sbHQWl3OLFi+Xh4SGTyaRatWqpadOm+uqrryRJZcuW1dy5cyVJO3bssFxz6dIlPfbYY2rQoIFu3rypYcOGacGCBWrWrJn69u2r/v37a8mSJdq3b59eeukl9erVS+np6XrkkUd0+PBhHT9+PMuyPSIiQjY2Nho/frxlbMCAAVqzZo3lmY158dhjj0mS9uzZ88Dc3bp109ChQyVJTZo00YoVKxQaGqrmzZtrw4YNkv5c5bhs2TLVq1dPkvTEE0+oe/fukvTA+QEAAAAABYOVjgAAAChVTCaTpk6dqn79+mnq1Klq0qSJ0ZFQSu3atUuOjo6SpGPHjun8+fO6ceOG5XjXrl3VqFEjvf/++xo6dKhMJpPWrFmjQYMGSZLWrl2r27dvy9fX13LNpUuXVLduXZ06dUotW7ZUtWrVJMmyFeujjz56T447d+7Iz89PmzdvlpOTk2Xc0dFRAwYMyJf3evPmTcucD5P77vML/5q3cePG2rJli6Q/v48bNmyo/v37a9myZerRo4d8fHwe+nPJqb59++b8TZcyCxYsYNvqv4mLizM6AgAAAFCoKB0BAABQ6vznP/9RkyZN5O/vry+++MLoOCilHnnkEW3dulVfffWV2rZtq7p16+rAgQOW4yaTSW+88YaGDBmi8PBwdenSRdu2bdNrr70mSfr555/l5uaW7Zahd59/ePefWfHx8dGECRPUrFmzfHpn9zp48KAk6R//+MdD5c6KtbW1zGaz5fWiRYvUt29f9ezZU88++6wCAwNVpUqVXM8PAAAAAMgbSkcAAACUOndXOz7//POaOnWqZetHoDBNmzZNu3fv1pYtW1SmTBnL1qF/5e3trWnTpum9995TrVq15OHhIRubP/8aZ21trV9++UVpaWmytbXNVYZly5apWbNmlq1JC4LZbNaePXtkbW2t5557TqtXr85zbklq2rSpDh48qIkTJ2rp0qVq3ry5oqOj8+Vz+TtW8GXPZDJp/Pjx6tevn9FRipSgoCD179/f6BgAAABAoeGZjgAAACiV+vTpIw8PD82ZM8foKCiFzp49q9mzZ+uFF16wbCWakZFxz3l2dnYaN26cdu7cqTfeeEMvv/yy5djjjz+uW7du6eOPP850zbVr17RkyZIHZti0aZPMZrNlu9a7du/enZu3dF/jx4/XgQMHNH/+fD3++ON5zi1JKSkp+uyzz+Ts7KzFixcrLCxMly5d0saNG/NlfgAAAABAzlE6AgAAoFQymUyaMmWK1q1bp6NHjxodByXc9evXJf3/Zxve/efatWt148YN7dmzRxEREbp69apu3ryppKQky7UjR46Ui4uLEhMT5eHhYRnv37+/atSoIR8fH82fP1/Hjx9XUFCQRowYoRdffFGSdOvWLUnS5cuXM+XZtm2b3n77baWlpWnRokVatGiRFi5cqJEjRyoqKkqSdODAAbVo0UK7du3K9r2dO3dOknT79u17xseMGaP/+7//09ixYzV+/PiHzn332ZapqamW+RITE5WSkiKz2Syz2ayPP/7Yst1qhw4dVKlSJVWqVOmh5gcAAAAA5D+2VwUAAECp1bdvX82ePVtz585VYGCg0XFQQkVGRmrmzJmSpE8//VQNGjRQp06dNGTIEK1evVpeXl7y8fHRhx9+qIEDB6pHjx6ZtvN0dnbWgAED1KRJk0zz2tvba8uWLerZs6d8fX3l6+srDw8PywrA5cuXa9OmTZKk0aNH6/XXX1eLFi108OBB9ezZU7du3dKPP/6YaU4HBwdduHBBkhQbG6uffvpJp06dUrt27bJ8b6GhoXr//fcl/VkyPvXUU3JycpKdnZ1sbGxUr149RUZG6oknnnjo3Lt377bknjNnjt566y3t2rVLe/bsUVJSkmbNmqXXX39dZ8+e1cCBA/Wf//xHsbGxGjVqlHr27ClJ2c4PAAAAACgYJvPdXw0FAAAASqG1a9fqxRdf1NGjR/Xoo48aHQfFhMlk0rp16/L8DLukpKRMRVhKSors7e3vOa9Dhw4KCgqSq6trlvPExsbKZDLJ3d09T3n+7saNGypXrly+zvlXecmdnp6ujIwMxcfH3/f6vH4ud5/Jx1+bs5df3w8lDX9+AAAAUNqwvSoAAABKtf79+6tRo0by9/c3OgpKob+vvMuqcDxy5Ijq1Klz38JRkmrWrJnvhaOkAi0cpbzltrGxkZ2dXbbXF9TnAgAAAAC4F9urAgAAoFSzsrLSpEmTNGjQIE2dOlUNGzY0OhKgAwcOyNfXV02aNNGuXbsUHBxsdCSgQKSnpysyMlJPPfWUJOnixYtas2aNfv/9d3Xs2FHt2rWTtbV1ruePj4/XiRMn7rtF8F1HjhxRRESE7Ozs1KVLF/3++++qWLGiatasmet7AwAAAKUNKx0BAABQ6vXv31/169dntSOKjIyMDO3fv1+rVq3SlClTVKtWLaMjAfnu+vXrmj9/vuV5pT///LNmz54tb29v9e7dW35+fnJ3d9evv/6a47kTEhLk4+OjOnXqWJ4RmpXExEQNGzZMkyZNUo8ePTRy5EhVr15dnp6emjdvniIiInL9/gAAAIDShtIRAAAApZ61tbWmTJmiNWvW6JdffjE6DqAnn3xSV65c0ZUrV9S3b1+j48Agq1evLpZzP4wLFy7oxRdf1OjRoy3bDPv7+6tBgwZyc3NTy5Yt5e/vr4sXL2r+/Pk5nv/cuXMaNGiQbt++ne05jRo1UkpKisLDwzNtxWtjY6NFixZp3rx5io6OzvkbBAAAAEohSkcAAABA0oABA1SvXj3NnTvX6CiApD9LDysr/spWWu3YsUOTJk0qdnM/rAkTJqhXr15ycXGxjDk4OCggIMDyumXLlpKkS5cu5Xj+J598Uo8++uh9j6empqpfv36qUKGCPv744yzPsba21oQJEzRixIgc3x8AAAAojXimIwAAAKD/v9rx5Zdf1uTJk9WgQQOjIwEoppKSkhQeHq7jx4+rRo0a6tChg2rUqCFJCg0N1enTp+Xk5KRhw4YpKSlJq1evVlpamtzc3NS/f3/t3LlTPXv2lMlk0tKlS1WtWjV169ZNcXFx2rx5s0aNGqXdu3dry5YteuSRRzR06FCVKVMmT3MnJibqk08+0ZAhQ1SlSpUC/XwiIyMVFhaWqWCUpCVLlui3336zvI6NjZUkPfPMM/meYcqUKdq/f78CAgLk6Oh43/Pat2+vcePGaePGjerdu3e+5wAAAABKEn5tFgAAAPivgQMHstoRQJ4cOXJErVu3lq2trcaMGaNr166pcePGlu1Mu3XrpoCAAM2cOVOS5OzsrEGDBmn69OlauHChJKl8+fLy9PSUvb29GjZsqBo1aigwMFCenp7y8fHR6NGj9dlnnykqKkpjx45V27ZtlZaWluu5JSk4OFiTJ09WUFBQgX9G77zzjlq1amXZVvUuBwcH1axZ0/I6ODhYjRs31vDhw/M9w9q1a2VjY6Po6Gj961//kpOTk/75z3/q4MGD95zbunVrzZ49O98zAAAAACUNpSMAAADwX9bW1po0aZI+++wznTx50ug4AIqZ1NRUPf/88+rVq5d69+6typUr6/XXX1f37t01fPhwHTt2TJLUqFGjTNc5OzurXr16ltdNmzZV5cqV5eDgoHbt2qlp06by9vZWly5dlJycrFdffVXLly9XWFiYpk2bpv3792vFihW5nlv6c4vpNWvWaPDgwQXx0WQSFRWlatWqZXuO2WzWypUrFRAQIDs7u3y9/4ULF3ThwgU99thj8vPz044dO3Tw4EGdOnVKbdu21YULFzKd7+HhoejoaKWmpuZrDgAAAKCkoXQEAAAA/uKFF15Q3bp1NW/ePKOjAChmvvnmG504ccLyLMK7OnbsqNTUVC1fvjxH85lMpkyvHR0dZWNjIw8PD8vYxIkTZWNjo4iIiDzPPWDAgHtWH+a31NRUnTlzRm5ubtmet23bNnXs2FGtWrXK9wx3VzP27NlTFSpUkCQ1aNBA77//vm7evKklS5ZkOt/FxUXp6ek6depUvmcBAAAAShJKRwAAAOAv/rra8cyZM0bHAVCM3F3J6OTklGm8TZs2kqTjx4/naL6/F4NZKVu2rKpXr66EhIR8n7sgXLlyRXfu3FGZMmWyPW/Hjh2aNWtWgWRwcXGRJFWqVCnT+N2C85dffsk0fvffZ1xcXIHkAQAAAEoKSkcAAADgb1588UXVqlWLZzsCyJG7q+b27t2babxmzZqytbVV+fLlczTfwxSDKSkpio+PV506dfJ97oJQtWpVubq6KikpKdvzatWqZSkH81uDBg0kSQcOHMg07u7uLltb23tWe169elWSLM+/BAAAAJA1SkcAAADgb6ytrTVx4kR9+umnOnv2rNFxABQT//jHPyTpnq1Ojx49qrS0NMtKOhsbGyUnJ2c7l8lk0p07dx54z3379ik5OVldu3bN97kLioeHh37//fdszxk5cmSB3b9q1arq2LGj9u3bl2n85MmTSktLU+vWrTONX7p0SSaTSbVr1y6wTAAAAEBJQOkIAAAAZOHFF19UjRo1WO0I4KE9/vjjeumllxQREaFff/3VMv7dd9+pfv36GjFihCSpQ4cOSkxM1MqVK3Xr1i2tXLlSly9f1pkzZyyr6tzc3BQfH68zZ87o9OnTunXrliQpPT090zatX375pdq2bWspHXM794EDB9SiRQvt2rWrwD+nNm3aKDo6+r7H9+zZo65du2b6DO8aMWKEOnfurN9+++2B97n7frMqYd977z2dP39eP/zwg2Vs586datSokQYPHpzp3HPnzqlDhw5ycHB44D0BAACA0ozSEQAAAMiCra2tJk+erFWrVrHaEcBD+/jjjzVo0CB17txZn376qZYvX67w8HBt375ddnZ2kqS+ffuqZcuWGjJkiJ588km5urrKy8tLTZs21YYNGyznmM1meXl5KTw8XI6OjpIkKysrLVmyRL6+vhowYIBiY2MVGhpquX9u546NjdVPP/2kU6dOFfhn5Ovrq4sXL+r06dNZHo+MjFR4eHiWx3fs2KGvv/5an3/+ebb3+Prrr/Xaa69JkoKDgxUQEKD4+HjLcQ8PD33//ffy8/PT9OnTNWfOHH311Vfavn27bGxsLOelpqYqJCREPj4+uXmrAAAAQKliMpvNZqNDAAAAAEVRWlqaGjZsqA4dOujjjz82Og6KEJPJpHXr1qlfv35GR0EBCgoKUv/+/ZWbvzZfv35dP//8s9zd3VW9evUsz0lISFDlypUl/bka7+8r6a5fvy4rKyvLMwZfeeUVrVixQqmpqTp//rxcXFxUrly5fJlbkm7cuHHf+bKTm++HpUuXKjo6WosWLcry+JUrVyzPyPyrlJQUhYSEyMHBQd27d89x1qxcvHhRZcqUyfKZm+vXr1dgYKCCg4NzPG9e/vwAAAAAxRErHQEAAID7sLW11aRJk7RixQqdO3fO6DgAihEXFxc99dRT9y0cJVlKQUlZbt3p4uKSqRT8qxo1amRbEOZm7twUjrk1fPhwXb58WYcOHcryeFaFo/Rn6bh371517tw537JUq1Yty8LxxIkTCgwM1Nq1a/PtXgAAAEBJRukIAAAAZGPw4MGqXr263n77baOjACjl/vjjD6Wnp+vmzZtGR8kzKysrrVq1Sh999JH279//0NdFRkZqzpw5mbZALQixsbGaO3euVqxYoTJlyhTovQAAAICSgtIRAAAAyIatra0mTpyo5cuXKzY21ug4AEqpwMBAbd26VWazWW+++aYOHz5sdKQ8s7e317Jly1SlSpWHvqZ9+/aFUgLa2dlp1apV911xCQAAAOBelI4AAADAA7z88st65JFH9M477xgdBUAp1bVrV504cUJXr16Vv7+/GjZsaHSkfOPu7m50hHu4ubnJZDIZHQMAAAAoVigdAQAAgAewtbXVm2++qYCAAFY7AjCEi4uLXF1dLV9s+QkAAACgqKF0BAAAAB7C0KFD5ebmpvnz5xsdBQAAAAAAoMihdAQAAAAegq2trXx9fRUQEKC4uDij4wAAAAAAABQplI4AAADAQxo2bJiqVq3Ksx0BAAAAAAD+htIRAAAAeEh2dnZ644039Mknn+jChQtGxwEAAAAAACgyTGaz2Wx0CAAAAKC4SElJUb169dS7d28tXLjQ6DgwiMlkMjoCgGKCH7sAAACgtKB0BAAAAHLoww8/lK+vr06dOqVHHnnE6DgwQFBQkNERYKBLly5p3Lhxmjt3rurUqWN0HBRx/fr1MzoCAAAAUCgoHQEAAIAcSklJUd26ddW3b18tWLDA6DgACllYWJi6du2qa9euycXFxeg4AAAAAFAk8ExHAAAAIIfs7e3l6+urjz/+WBcvXjQ6DoBCFhMToypVqlA4AgAAAMBfUDoCAAAAuTBixAhVrFhR7777rtFRABSykydPqkGDBkbHAAAAAIAihdIRAAAAyAUHBwf5+Pjoo48+YrUjUMrExMRQOgIAAADA31A6AgAAALn0yiuvqEKFCnr//feNjgKgEMXExKh+/fpGxwAAAACAIoXSEQAAAMilv652/P33342OA6AQ3L59WxcuXGClIwAAAAD8DaUjAAAAkAejRo2Sq6srz3YESomTJ08qIyOD0hEAAAAA/obSEQAAAMgDBwcHTZgwQUuWLGG1I1AKxMTEyMrKSnXr1jU6CgAAAAAUKZSOAAAAQB6NGjVKTk5Oeu+994yOAqCAxcTEqGbNmnJwcDA6CgAAAAAUKZSOAAAAQB6VLVtWPj4+Wrx4MasdgRLu5MmTbK0KAAAAAFmgdAQAAADywahRo+To6KgFCxYYHQVAAYqJiaF0BAAAAIAsUDoCAAAA+cDR0VGvv/66PvzwQyUkJBgdB0ABiYmJUf369Y2OAQAAAABFDqUjAAAAkE/GjBnDakegBLt69aoSExNZ6QgAAAAAWaB0BAAAAPKJo6Ojxo8fz2pHoIT65ZdfJInSEQAAAACyQOkIAAAA5KOxY8eqTJkyWrhwodFRAOSzmJgY2dvby93d3egoAAAAAFDkUDoCAAAA+ejuaseFCxcqMTHR6DgA8tHJkydVt25dWVtbGx0FAAAAAIocSkcAAAAgn7HaESiZYmJi2FoVAAAAAO6D0hEAAADIZ05OTnrttdf0f//3f7py5f5prdsAACAASURBVIrRcQDkE0pHAAAAALg/SkcAAACgALz22muys7NjtSNQQpjNZp06dUr169c3OgoAAAAAFEmUjgAAAEABuLvaceHChbp69arRcQDk0cWLF3Xz5k1WOgIAAADAfVA6AgAAAAXkf//3f2Vtbc1qR6AEiImJkSRKRwAAAAC4D0pHAAAAoICUK1dOr732mj744ANWOwLFXExMjJydnVW1alWjowAAAABAkUTpCAAAABSgcePGycrKSh9++KHRUQDkwcmTJ9WwYUOjYwAAAABAkUXpCAAAABSgu6sd33//fV27ds3oOAByKSYmhq1VAQAAACAblI4AAABAAWO1I1D8xcTEqH79+kbHAAAAAIAii9IRAAAAKGAuLi4aO3Ysqx2BYio9PV1nz55lpSMAAAAAZIPSEQAAACgEEyZMkCQtXrzY4CQAcurs2bNKTU2ldAQAAACAbFA6AgAAAIXgr6sdk5KSjI4DIAdiYmIkSfXq1TM4CQAAAAAUXZSOAAAAQCGZMGGCMjIyeLYjUMzExMSoSpUqcnV1NToKAAAAABRZlI4AAABAIXF1ddWYMWNY7QgUMydPnmRrVQAAAAB4AEpHAAAAoBBNmDBBaWlpPNsRKEZiYmIoHQEAAADgASgdAQAAgEJUoUIFvfrqq3r33XdZ7QgUEzExMapfv77RMQAAAACgSKN0BAAAAArZhAkTlJqaqiVLlhgdBcAD3L59WxcuXGClIwAAAAA8gI3RAQAAAIDSpmLFihozZozmz5+v0aNHy9nZ2ehIACTdunVLffr0Uf369dWwYUPVr19fd+7cUUZGBqUjAAAAADyAyWw2m40OAQAAAJQ2ly9fVu3atTVt2jS98cYbRscB8F/VqlVTfHy8rK2tlZ6eLkmytraWu7u7mjRpokcffVQNGjRQo0aN9NRTTxmcFgAAAACKDkpHAAAAwCATJ07U8uXLdfbsWTk5ORkdB4CkHj166KuvvlJGRsY9x0wmk2xtbZWamqqhQ4cqICDAgIQAAAAAUDTxTEcAAADAIG+88YZSUlK0dOlSo6MA+C8vLy/Z2GT9JBKz2azU1FTZ2trKz8+vkJMBAAAAQNFG6QgAAAAYpGLFinrllVc0b9483bx50+g4ACQ1a9ZMqamp9z1ua2urMWPGyN3dvRBTAQAAAEDRR+kIAAAAGMjX11fJyclatmyZ0VEA6M/SMTs2NjaaOHFiIaUBAAAAgOKD0hEAAAAwUKVKlfTKK6/onXfe0R9//GF0HKDUq169uipUqJDlMRsbG73xxhuqUqVKIacCAAAAgKKP0hEAAAAw2Jtvvqlb/4+9O4+rusz///88gIILoY1+FXPNLUWQNA23zHIZFddUBs0lDS3N0RxzcgM31HKmtMhJR8BMNHDDQTFb1DRTUUnFrVID3FDQRCABgfP7w5/nE4koCLwRHvfbrdvc3tf7Otf1vA6cW3N6cV3vlBR2OwLFxLPPPiuTyXRPe7ly5TRx4kQDEgEAAABA8UfREQAAADBYlSpVNHr0aL333nvsdgSKgeeee05lypTJ1mZjY6OZM2eqcuXKBqUCAAAAgOKNoiMAAABQDEyZMkU3b97Uf//7X6OjAKXes88+q9u3b2drq1SpksaNG2dQIgAAAAAo/ig6AgAAAMVAtWrVNGbMGC1cuFC3bt0yOg5Qqj377LMym82WaysrK82dO1fly5c3MBUAAAAAFG8m8x+/SQEAAAAwTFxcnOrXr6+FCxdq/PjxRscBSq2srCxVrFhRt27dkslkUo0aNXTu3DmVLVvW6GgAAAAAUGyx0xEAAAAoJqpXry4vLy8tWLCA3Y6AgaysrOTi4mK5XrhwIQVHAAAAAHgAio4AAABAMfLuu+/qxo0b8vf3NzoKUKq1bt1aktSoUSMNHjzY4DQAAAAAUPxxvCoAAABQzPz973/X+vXrdfbsWZUrV87oOCXSwIEDjY6AYi46OlqHDh1S27ZtVaNGDaPjwEDr1q0zOgIAAADwWGCnIwAAAFDMTJ06VTdu3FBgYKDRUUqs9evX68KFC0bHQCG7cOGC1q9fn6/XVqpUSZUrVy4VBUc+Dzl7lN8fAAAAoDRipyMAAABQDI0fP16bN2/WL7/8IltbW6PjlDgmk0nBwcEaNGiQ0VFQiEJCQuTh4aH8fO1NT0/XgQMH1KFDh0JIVrzwecjZo/z+AAAAAKUROx0BAACAYmjatGlKSEhQQECA0VGAUqls2bKlouAIAAAAAAWFoiMAAABQDDk6Ouq1117TggULlJaWZnQcAAAAAACAXFF0BAAAAIqpd999V1evXtXKlSuNjgIAAAAAAJArio4AAABAMVWrVi2NHDlS8+fPV3p6utFxAAAAAAAA7ouiIwAAAFCMTZ06VVeuXGG3IwAAAAAAKNYoOgIAAADFWK1atTRixAj5+vqy2xEwyLlz5zRy5EhduHDB6CjFTkZGhn744QfL9aVLl/Svf/1LU6ZM0bfffqvMzMxHGj8uLk67du16YL+jR4/q448/1rJly3ThwgVFRkYqJibmkeYGAAAAkDcUHQEAAIBibtq0aYqLi9OqVauMjgKUSpGRkQoMDFRUVJTRUYqVxMRELVq0SM7OzpKkEydOaN68eRoyZIj69+8vb29v1a5dW7GxsXkeOz4+XpMnT9bTTz+tTZs23bdfQkKCXn/9dU2dOlV9+vTRmDFjVLNmTbm4uGjhwoXavXt3vtcHAAAAIG8oOgIAAADFXO3atTVixAjNmzeP3Y6AAQYMGKD4+Hh1797dsAzF7Y8OLl68qKFDh2rs2LGyt7eXJPn6+qpRo0ZydHSUm5ubfH19denSJS1atCjP40dHR2vYsGG6detWrn2aNGmitLQ0hYeHq3bt2pZ7NjY28vPz08KFCykWAwAAAEWEoiMAAADwGJg+fbouX76s1atXGx0FKJWqVKli2Nw7duzQ1KlTDZs/J5MmTVK/fv3k4OBgabOzs9OKFSss125ubpKky5cv53n8Vq1a6Zlnnrnv/fT0dA0aNEhPPvmkPv300xz7WFtba9KkSRo9enSe5wcAAACQdxQdAQAAgMdA7dq1NWzYMM2ZM4fdjkARy8rK0s6dO3Xw4EFL2/nz57VkyRJlZWXp+PHj8vX11eeff66srCxLnwsXLmjp0qUym83atWuXpk6dKj8/P8vuvbCwMC1evNhSqEtKStInn3yixYsXKzg4WJK0c+dO9e3bV8nJyVq2bJnCwsIk3TlWdMGCBbpy5UpRvQ0WERER2rp1qwYMGJCtfenSpdq6davl+u4zFTt16lTgGaZPn66DBw9qypQpqlChwn37de7cWUlJSdq4cWOBZwAAAACQHUVHAAAA4DExY8YMXb58WUFBQUZHAUqNkydPysPDQy+99JIOHz4s6U6xsGXLlpo4caI++ugjffDBB9q/f7+GDRum9957T5IUFBQkFxcXTZ48WWPHjtXnn3+uY8eOafz48erYsaNu376tXr16acWKFZo9e7Ykyd7eXsOGDZOPj4+WLFkiSapcubJcXFxka2urxo0bq1atWpKk0NBQTZs2TSEhIUX+nrz//vtq06aN5VjVu+zs7FSnTh3LdWhoqJo2bSovL68Cz7B27VrZ2NgoKipKL730kipWrKgXXnhBkZGR9/Rt166d5s2bV+AZAAAAAGRH0REAAAB4TNSpU0dDhw6Vr6+vMjIyjI4DlApNmzaVt7d3trZevXpp1KhRkiRnZ2cFBAQoLCxMLVq00IYNGyRJQ4YMUc+ePZWamqq33npL/v7+2rp1q2bOnKmDBw8qICBAktSkSZNsY9vb26tBgwaWa1dXV1WtWlV2dnZ68cUX5erqKkny9PTUmjVrNGLEiMJa+n0dO3ZMNWrUyLWP2WxWYGCgVqxYobJlyxbo/BcvXtTFixfVrFkzeXt7a8eOHYqMjNSZM2fUsWNHXbx4MVt/JycnRUVFsUscAAAAKGQUHQEAAIDHyMyZM3X+/Hl2OwJFyNbW9p62cuXKSVK25w42bdpUsbGxlusKFSrIxsZGTk5OlrZ3331XNjY22r17d54ymEymbNcVKlSQp6fnPbsNC1t6errOnTsnR0fHXPt988036tatm9q0aVPgGe7uZuzbt6+efPJJSVKjRo30wQcfKDk5WUuXLs3W38HBQRkZGTpz5kyBZwEAAADwfyg6AgAAAI+ROnXqaMiQIZo7dy67HYFixtraWmazOdc+5cuXV82aNRUfH5+nsf9cdDTK9evXlZmZaSm63s+OHTs0Z86cQsng4OAgSapSpUq29rsFzp9++ilbe8WKFSXdecYmAAAAgMJD0REAAAB4zEyfPl0xMTFas2aN0VEA5FFaWpri4uL09NNP5+l1xaXoWL16dVWqVElJSUm59qtbt66lOFjQGjVqJEmWZ2zeVbt2bZUpU+ae3Z+//fabJFmehwkAAACgcFB0BAAAAB4z9evXZ7cj8Jjav3+/UlNT5e7uLkmysbFRampqrq8xmUzKzMwsingPxcnJSVevXs21z5gxYwpt/urVq6tbt27av39/tvZffvlFt2/fVrt27bK1X758WSaTSfXq1Su0TAAAAAAoOgIAAACPpZkzZyo6OlpffPGF0VGAEi8tLU2SlJCQYGm7efOmpDvPOLwrISFBaWlp2Y5YzcjI0KlTpyzX69evV8eOHS1Fx65duyohIUGBgYFKSUlRYGCgrl27pnPnzll26Dk6OiouLk7nzp3T2bNnlZKSosOHD6t169batWtXoa37fjp06KCoqKj73t+zZ4/c3d2zPd/yrtGjR6tHjx66cuXKA+e5u/6cirL//ve/df78ef3www+Wtp07d6pJkyYaMWJEtr7R0dHq2rWr7OzsHjgnAAAAgPyj6AgAAAA8hurXr6/Bgwdrzpw57HYECtGBAwcszyYMDg7W1q1b9d1332nTpk2SpPnz5ysuLk5ffPGF9uzZo6SkpGyfSysrKy1dulRTpkyRp6enYmJiFBYWZhl/4MCBcnNz08iRI9WqVStVqlRJLVu2lKurqzZs2GDpYzab1bJlS4WHh6tChQqKiYnRoUOHdObMmSJ+R6QpU6bo0qVLOnv2bI73IyIiFB4enuP9HTt2aNu2bVq9enWuc2zbtk0TJkyQJIWGhmrFihWKi4uz3HdyctLevXvl7e0tHx8fzZ8/X1u2bNG3334rGxsbS7/09HRt3rxZkydPzs9SAQAAAOSByfygp9wDAAAAKJbOnDmjJk2aaOXKlRoyZIjRcR4rJpNJwcHBGjRokNFRUIhCQkLk4eEho772vvHGGwoICFB6errOnz8vBwcHPfHEEzn2jY+PV9WqVSXd2dn35115iYmJsrKyyva8wps3b953vLzIz+dh2bJlioqKkp+fX473r1+/rieffPKe9rS0NG3evFl2dnbq3bt3vjP/0aVLl1SuXDlVrlz5nnvr1q1TUFCQQkND8zyu0b8/AAAAwOOGnY4AAADAY6pBgwb629/+ptmzZxer570BuFetWrVyLRDeLThKyvEYUAcHh2wFR0kFUnDMLy8vL127dk0//vhjjvdzKjhKd4qO+/btU48ePQosS40aNXIsOJ4+fVpBQUFau3Ztgc0FAAAA4P4oOgIAAACPMW9vb/36668KCQkxOgqAP/n999+VkZGh5ORko6MUOCsrK61cuVL/+c9/dPDgwYd+XUREhObPn5/tCNTCEBMTowULFiggIEDlypUr1LkAAAAA3FG4/y8fAAAAQKFq2LChPDw8NHfuXHl4eMjKir8rLGjp6enas2ePtmzZoi5duhToDq1HcePGDfn7+ys2NlY9e/bUyy+/LGtr6zyNsXv3bl28eDFbW5kyZVS1alXVqFFDDRs2LMjIpUpQUJC++uormc1m/fOf/5SXl5dcXV2NjlWgbG1ttXz5csXGxj70azp37lyIif5P2bJltXLlSplMpiKZDwAAAAA7HQEAAIDHno+Pj37++Wd2OxaS48ePKyQkRIsXL9alS5eMjiPpzvPynnvuOR09elTHjx9X9+7d1bZt2zyP4+LiorNnz2rw4MEaMWKEbt68qfj4eIWFhcnDw0P16tXTjBkzdPv27UJYRcnm7u6u06dP67fffpOvr68aN25sdKRCU7t2baMj3MPR0ZGCIwAAAFDE2OkIAAAAPOYaNmyoQYMGac6cORo0aBC7HQtYixYtNG7cOC1fvtzoKBYhISGKiIiwPDdv7ty58vb21t69e9WuXbuHHqdSpUoaMWKEZs6cqfr162vMmDGWe2azWRs2bNCoUaMUERGhDRs23PNMQdyfg4OD0REAAAAAoEjxXyMAAACAEmDmzJn66aeftH79eqOjlEh3nz9XHHZOpaenq1u3bpaCoyQNGzZMkvTEE0/kebz7vcZkMmnAgAFavny5vv76a3Xo0EHp6en5Cw0AAAAAKPHY6QgAAACUAE2aNNGgQYM0e/ZsDRgwgN2OReTnn3/W/v37dezYMbVr1079+vWTJH377bc6f/68pDvPvevfv79sbW0VERGhkydPqnLlyurTp48k6dKlS/ryyy914cIFtWvXTi+//LJl/N9++01r167V2LFjtW3bNh07dkz/+Mc/VK9evWw5jh07Jnd3dzk7O1vaEhIS9N///lcjR45UtWrV8r1GDw8PrVq1SuHh4YqIiFD79u0fmPv8+fPauHGjxo8fr5MnT2rz5s2qXbu2hgwZYvndNJvN+u6773TkyBFZW1vrmWeeUZcuXSxj5DY+AAAAAKD4oegIAAAAlBDe3t5q1qyZNmzYoIEDBxodp8RbvHixNm/erB07digmJkadOnVSXFyc3nzzTbVp00YTJkzQiRMndPbsWdna2kqSWrdureHDh2vz5s2SpJ07d2rt2rV68803ZW9vr759+2rYsGH65JNP9Nlnn2ns2LFKT09XVlaWVqxYoaNHj6p79+5ycXGRdKdwt27dOs2ePVvbt2/Pli80NFTTpk1TxYoVNX78+Edaq5ubm8LDw7Vnzx61b98+19xhYWEaNWqU4uPjZTabdezYMcXHx2vGjBm6cOGCpk6dKkmaMWOG6tWrp4kTJ+rQoUMaN26cpeiY2/gAAAAAgOKJP38GAAAASogmTZpowIABmj17trKysoyOU+J98skncnJykslkUt26deXq6qotW7ZIksqXL68FCxZIknbs2GF5zeXLl9WsWTM1atRIycnJev311/Xhhx/q2Wef1cCBA+Xh4aGlS5dq//79Gj58uPr166eMjAw99dRTOnLkiE6dOmUpOKakpGjMmDF67bXXdPLkSTk7O+vgwYOWuTw9PbVmzRqNGDHikdfarFkzSdKePXsemLtXr14aNWqUJMnZ2VkBAQEKCwtTixYttGHDBkl3iqXLly9XgwYNJEnPPfecevfuLUkPHB8AAAAAUDyx0xEAAAAoQXx8fOTs7KxNmzbplVdeMTpOibZr1y5VqFBBknTy5EmdP39eN2/etNx3d3dXkyZN9MEHH2jUqFEymUxas2aN5fmLa9eu1a1btzRlyhTLay5fvqz69evrzJkzcnNzU40aNSTJchTrM888Y+lboUIFLV++XJ9++qk++ugjTZ48WW+++aYOHTpkue/p6Vkga01OTraM+TC5y5Urd0/epk2bWnZjmkwmNW7cWB4eHlq+fLn69OmjyZMnP/T7klfF4VmcxZ2Hh4c8PDyMjgEAAADgMUbREQAAAChBmjZtqldeeUU+Pj7q168fz3YsRE899ZS++uorbdmyRR07dlT9+vV1+PBhy32TyaR33nlHI0eOVHh4uHr27KlvvvlGEyZMkCSdOHFCjo6OuR4Zevfnl9vP0crKShMnTtQPP/ygDRs2KC0tzXKca0GJjIyUJD3//PMPlTsn1tbWMpvNlms/Pz8NHDhQffv21csvv6ygoCBVq1Yt3+PnJjg4uMDGKok8PDw0ceJEtWnTxugoxcq+ffu0ePFio2MAAAAAjw2KjgAAAEAJ4+PjIxcXF23evFn9+vUzOk6JNXPmTH333Xfavn27ypUrZzk69I+GDBmimTNn6t///rfq1q0rJycn2djc+RpmbW2tn376Sbdv31aZMmUeOU+XLl20c+fOAi84ms1m7dmzR9bW1urSpYtWrVpVILldXV0VGRmpd999V8uWLVOLFi0UFRVV4O+LJA0aNKhAximpPDw81KZNG96nHFB0BAAAAB4ef/YMAAAAlDBOTk7q16+fvL29ebZjIfn11181b948vfrqq5ajRHN6r8uWLauJEydq586deuedd/Taa69Z7jVv3lwpKSn69NNPs73mxo0bWrp0aZ4zHT9+XL169crz6x7k7bff1uHDh7Vo0SI1b968QHKnpaXp888/l729vT755BNt3bpVly9f1saNGwv8fQEAAAAAFA2KjgAAAEAJNHv2bJ08eVL/+9//jI5SIiQmJkr6v2cb3v3ftWvX6ubNm9qzZ492796t3377TcnJyUpKSrK8dsyYMXJwcFBCQoKcnJws7R4eHqpVq5YmT56sRYsW6dSpUwoJCdHo0aM1dOhQSVJKSook6dq1a5bX3bp1S76+vjp+/Lil7dq1a/rxxx/14YcfWtoOHz6s1q1ba9euXbmuLTo62jLun9vHjRunjz76SOPHj9fbb7/90LnvPtsyPT3dMl5CQoLS0tJkNptlNpv16aefWo5b7dq1q6pUqaIqVao81PgAAAAAgOKHoiMAAABQAjk5Oalv376aPXt2tufoIe8iIiI0e/ZsSdJnn32mbdu2ydnZWSNHjtT333+vli1b6uTJk/r444+VnJysPn366Pbt25bX29vby9PTUyNGjMg2rq2trbZv3666detqypQpatq0qebMmaOpU6fK3t5e/v7+2rRpkyRp7NixioiIkHRnR+WGDRvk4uKi1q1by9vbW0FBQQoPD5eDg4Nl/JiYGB06dEhnzpy579rCwsIsz5iMjo5W27Zt1bVrV7m7u2vixIkqV66cIiIi9NFHHz107u+++86Se/78+YqLi9MXX3yhPXv2KCkpSXPmzFFGRoZ+/fVXDR48WOvXr9cHH3ygN998U3379n3g+AAAAACA4slk5r9AAAAAACXS8ePH1bx5c23atEm9e/c2Ok6xYjKZFBwc/MjPsEtKSspWCEtLS8vxmYpdu3ZVSEiIKlWqlOM4MTExMplMql279kPPfePGDZUtW1bly5e/b5+bN2/qiSeeeOgx8yo/ue/KyMhQVlaW4uLi7vv6RxlfkkJCQuTh4UHh/QEK6vNQ0vD7AwAAAOSNjdEBAAAAABSOZs2aqXfv3po1a5Z69eolk8lkdKQS588773IqOB49elRPP/30fQuOklSnTp08z53beHcVZsFRyl/uu2xs7nwdza2g+CjjAwAA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4sQJLVu2TP369bunb37XAAAAAACFiZ2OAAAAAPAHTZs2lbe3d7a2Xr16adSoUZLu7KgLCAhQWFiYWrRooQ0bNkiShgwZop49eyo1NVVvvfWW/P39tXXrVs2cOVMHDx5UQECAJKlJkybZxra3t1eDBg0s166urqpatars7Oz04osvytXVVZLk6empNWvWaMSIEYW19Hw5duyYatSokWsfs9mswMBArVixQmXLli3Q+a9cuSJra+t7xi1fvryke485dXJyshSF86Kw11mtWjXt2bNH9evX14cffqikpCS1bds2x775XQMAAAAAFCaKjgAAAADwJ7a2tve0lStXTpKyPVuwadOmio2NtVxXqFBBNjY2cnJysrS9++67srGx0e7du/OUwWQyZbuuUKGCPD0979lpZ6T09HSdO3funl2Gf/bNN9+oW7duatOmTYFnqFixYo7tmZmZkqTq1atna3dwcFBGRoZlh+TDKKp1+vv7q2PHjho5cqT27dun559/Ptvv1135WQMAAAAAFDaKjgAAAACQT9bW1jKbzbn2KV++vGrWrKn4+Pg8jf3nomNxdP36dWVmZloKsvezY8cOzZkzp1Ay1KpVS5mZmUpLS8vWnpSUJOlOYfiP7hYpL1y48NBzFMU6AwMDFRwcrGXLlsnf31/+/v66ePGixo0bd0/f/KwBAAAAAAobRUcAAAAAKERpaWmKi4vT008/nafXPQ5Fx+rVq6tSpUqWAt/91K1bVw4ODoWS4e5xtefPn8/WnpCQIOneouNvv/0m6U6x8mEVxTo/++wzde/eXTY2NpKkkSNHysvLS1999ZVu3LiRrW9+1gAAAAAAhY2iIwAAAAAUov379ys1NVXu7u6SJBsbG6Wmpub6GpPJZDketLhzcnLS1atXc+0zZsyYQpt/1KhRsrW11d69e7O1Hz58WK6urmrUqFG29suXL8tkMqlevXp5mqew13ns2LF7iot9+vRRenq6rly5kq09v2sAAAAAgMJE0REAAAAA/uTuUZ13d8tJ0s2bNyXdeb7fXQkJCUpLS8t2xGpGRoZOnTpluV6/fr06duxoKTp27dpVCQkJCgwMVEpKigIDA3Xt2jWdO3fOsoPN0dFRcXFxOnfunM6ePauUlBQdPnxYrVu31q5duwpt3fnRoUMHRUVF3ff+nj175O7unuOzCUePHq0ePXrcU1TLyd335s8F2+rVq+utt97SokWLLD+H1NRUhYWFyd/fX1ZW2b/2RkdHq2vXrrKzs8tTjsJeZ9++fbVp0yZlZWVZ2vbv3y8XFxc1bNjwgWsAAAAAAKNRdAQAAACAPzhw4IDluXzBwcHaunWrvvvuO23atEmSNH/+fMXFxemLL77Qnj17lJSUpDlz5igjI0OSZGVlpaVLl2rKlCny9PRUTEyMwsLCLOMPHDhQbm5uGjlypFq1aqVKlSqpZcuWcnV11YYNGyx9zGazWrZsqfDwcFWoUEExMTE6dOiQzpw5U8TvSO6mTJmiS5cu6ezZsznej4iIUHh4eI73d+zYoW3btmn16tW5zrFt2zZNmDBBkhQaGqoVK1YoLi7Ocn/RokVyd3dX79699fHHH2vOnDmaMWOGWrRokW2c9PR0bd68WZMnT85zjsJep5+fn3r27KnmzZtryZIl8vLyUmRkpEJDQ7MVTu+3BgAAAAAwmsn8xz/JBQAAQIEYOHCgJGndunUGJwFKHyM/f2+88YYCAgKUnp6u8+fPy8HBQU888USOfePj41W1alVJd3bm/XnXWmJioqysrGRvb29pu3nz5n3Hy4uQkBB5eHgoL18Hg4KC9Oqrr+rGjRv3PLdw2bJlioqKkp+fX46vvX79up588sl72tPS0rR582bZ2dmpd+/eeVtEDjIzM5WQkKBq1arleH/dunUKCgpSaGhovnIUxTp///13xcTEqHr16qpcufJDr0GS6tWrp379+umDDz7IdY4/4t9XAAAAAAoKOx0BAAAAoBDUqlUr1wLh3YKjpByPyXRwcMhWcJRUIAXHR3X36Nk/8vLy0rVr1/Tjjz/m+JqcCnF3x9q3b5969OhRINmsra3vW3A8ffq0goKCtHbt2nznKIp1li9fXk2aNMmx4JjbGiQ9Ns8BBQAAAFAy2RgdAAAAADDajRs35O/vr9jYWPXs2VMvv/yyrK2tH2nM8+fPKzIyUseOHZOVlZUaNmyoVq1ayWQy6cKFC2rfvn0BpUdx8vvvvysjI0PJycmqWLGi0XEKVJkyZfTEE0/o9ddfV5s2bdSqVSt17txZ0p0jZVeuXKnx48fLy8tLrVq1eqgxIyIiNH/+fNnYFO5X05iYGC1YsEABAQEqV65cvnMYuc77reH48eP68ssvFRsbq5s3b/KcRwAAAACG4XhVAACAQsBxdY+P69evq3Xr1mrbtq0uXryoXbt26bnnntOBAwfyNV56erqmT58uPz8/jR8/Xh07dlT58uV14MABvf/++7px44b+9a9/adKkSQW8Etxl1OcvKChI//jHP3TlyhWNHTtWXl5ecnV1LdIMDys/x6s+rNjYWNWuXbvAx30Uly9fVvXq1WUymQpszKJeZ2GsQeLfVwAAAAAKDjsdAQAAkGerVq3SsGHDSsS8ISEhioiIsByLOHfuXHl7e2vv3r1q165dnsZKTU1Vu3btdPbsWX399dfZdjN26tRJAwcOVKdOnfT7778X6BoKQkn6mRrF3d1dPXv2tFzb2toamMY4xa3gKEmOjo4FPmZRr7Mw1gAAAAAABYlnOgIAACBPduzYoalTp5aIedPT09WtW7dsz2G7WwDLz7Pz5s2bp8jISL3zzjs5Hp9av359zZw5UykpKfkPXQhK0s/USA4ODqpUqZLln5yO8QQAAAAAoKSynjVr1iyjQwAAAJQ0d4+pGzRoUJ5el5ycrJCQEK1bt04JCQmqWbNmtueYERM8AAAgAElEQVRzJSUlKTQ0VOvXr9fZs2dVtWpVOTg4WO6fP39eK1euVOvWrXXixAn997//VUxMjJydnbMdyfegeX7++Wdt3bpVn3/+uVJSUtSkSRPp/2vv3qOqrvP9j782bC6KBFQuxQRLzQuMiDkm6nFhM6knREOPxpBJLRyoNCdzHNJWWuPScnKm0mWmJuIlNPCGccTylBfsJGGagniZUUaUgAIvCF64yPf3hz/3CQUEN7BJno+1WDPfz+ez3583381eM3u9/H6/knbt2qWQkBCVl5fr/vvvV15enrp37y5Jys3N1YYNG5SUlKSKigp17ty53n019L53Ym9vLw8Pjypje/fuVXFxsaZOnWoZKyws1MKFC9WtW7can9OXn5+vsWPHytnZWRs2bKjxKrdevXqpuLhYPj4+knhPG/o9le7+89eSZGZmauPGjeLrIPi8AAAAAGgoXOkIAADQTBw/flyhoaHy8/PTW2+9pcTERHXp0kVZWVmSpMOHD2vQoEFycHDQ5MmTdfHiRfn4+GjNmjWSpKSkJPXt21dTp07VokWL9P777ys1NVXh4eH629/+Vud9PvzwQ7344ouaMGGCXnnlFU2bNk0ff/yxJMnDw0N+fn5ycnJS9+7d5eXlJelGgPT222+rT58+6tmzp0JCQjR58uR69dXQ+9aXYRhKSEjQjBkzLPvelJiYqDfeeEMJCQk1vv6HH35QeXm5OnfuLFdX1xrXOTo6auzYsZJ4Txv7PQUAAAAAAE3IAAAAQIMbO3asMXbs2Dqvr6ioMPz9/Y3ly5dbxg4cOGA4OjoaSUlJRmlpqdGjRw9j9uzZVV737LPPGo6OjkZmZqZhGIYxY8YMQ5Lx1VdfWdY89thjRt++feu0j2EYRteuXY3Jkydb5kNCQoygoKAqx15eXpbj4uJio3PnzkZJSYllbOLEiYYkY9++fXXqq7H2rauSkhIjMjLSaN26tSHJcHd3N9LS0qrMr1u3zrh06VKNNd577z1DkjFy5Mg67cl72njvaX0/fy1RfHy8wddBGAafFwAAAAANx2yjrBMAAAC/kJycrEOHDmnEiBGWsccee0zFxcVydHTU559/ruPHjysgIKDK64YPH65169YpJiZG//jHPyzPkOvRo4dljY+Pj7788ss67SNJu3fvlouLiyTp6NGjOnv2rC5dulRl31/ePnP9+vW6evWqoqOjLWN5eXnq0qWLTp48qYCAgDv21Vj71pWLi4uWL1+upUuXatGiRZo+fbpefvllff/995b5sLCwWmuYzTf+r/X169frtOcXX3zBe3oX+9ZVTk5OrVemtnT79u2TJM4RlJOTo44dO9q6DQAAAAD3AEJHAACAZuDw4cNycXFR27Ztq4zfDI2OHj0qSbc9T3Dw4MGSpGPHjtVY297eXoZh1GkfSXrooYe0Y8cO/fd//7cCAwPVpUsXHThwoMr6XwZFmZmZ8vT01EcffVSn37W6vppy39rY2dlp6tSp+vbbb7Vp0yaVlpbW+GzGW/n6+kqS/vWvf9VpPe9pw+1bndTUVIWGhlpd517HOYIkyy2fAQAAAMAahI4AAADNQGVlpS5fvqxdu3Zp2LBht83ff//9km5cnXQzlJKkTp06ycHBQR4eHg2yjyTNmjVLe/bs0ZdffqlWrVpp06ZNt635ZVBkb2+vEydOqLy8XA4ODnXqozntW52hQ4dq165ddQ4cJalv375q06aNsrKydOrUKXXp0qXW9bynjbevdCNE2bBhg1U17mUJCQkKDQ2tEhKjZRo3bpytWwAAAABwj7CzdQMAAACQevXqJUlat25dlfFz585py5Yt6t+/vyQpJSWlyvyRI0dUXl6uAQMGNMg+//73vzV37lw999xzlttnVlZWVllrMpmq3EK0d+/eunz5spYuXVpl3cWLF7VkyZI69WWrfWty5MgRjRw5sl6veeCBB/TXv/5V169fr3J70Or88MMPvKeNtC8AAAAAALANrnQEAABoBkaNGqU+ffpo9erVcnZ21rhx45Senq7du3crISFBTk5Oev7557V582adOXNG3t7ekqRvvvlGjz76qKKioiTJ8ry8srIyS+3CwkKVlpbKMIw77vPPf/5T0o1n6/3hD3/Q4cOHlZKSotLSUpWUlMgwDHl6eio/P19ZWVkyDEPBwcHy8vLS9OnTde3aNQUHBysjI0MbN25UTExMnfoqKSlplH3v5OrVq3r//ff19NNP6ze/+Y2kG2HdDz/8oKSkJMu6AwcO6OWXX9Z7772nIUOG1FjvT3/6k7777jslJCQoMjJSixYtsgRukpSdna158+ZpwoQJGjx4MO9pI7ynAAAAAADARgwAAAA0uLFjxxpjx46t12tycnKMoUOHGiaTyTCZTMaQIUOMnJwcy/zVq1eNyZMnG76+vsaqVauMFStWGCNGjDDOnDljGIZh7N692+jcubMhyfjjH/9o5OXlGevXrzfuu+8+Q5Lx9ttvG+Xl5XfcJyIiwjCbzUbXrl2NpUuXGhs3bjQcHR2N3/3ud8a5c+eMXbt2GWaz2XB3dzcWLVpkGIZhHD161OjWrZshyZBk+Pr6GgcPHqxXXw29b12UlJQYffr0MUwmk9GvXz9j1qxZxsKFC43i4uIq6zZt2mSYTCbjk08+qVPdtWvXGt7e3ka7du2MUaNGGREREUa3bt2MZ555xjh+/DjvaSO+p4Zxd5+/liY+Pt7g6yAMg88LAAAAgIZjMgwe4gEAANDQbj4j626eKXfx4kVVVlZanvl3q6KiImVmZsrb21sdO3a86x5r26e4uFiurq6W49LS0irPNywqKpKdnV2VNdKNK/lMJpPlqr36stW+Fy9elKOjo1q3bl3jmkuXLum+++6rV90LFy7oyJEjcnBwULdu3XhPm2hfaz5/LQXPdMRNfF4AAAAANBRurwoAANDMuLu71zrv5uamgQMHNuo+twZAvwyJbvZQnU6dOlnVU0PuO2nSpDvuFxUVJX9//zuec0n1DhwlycPDQ4MHD77jOt7Tht8XAAAAAAA0LUJHAAAA3JOeeOKJO65p27ZtE3QCAAAAAABw7yN0BAAAwD3p5i0DAdw7KioqlJaWZrkyODc3V+vWrdPPP/+s4cOHa8iQIbK3t7/r+vn5+Tp+/LiGDBly21xJSYkSEhJ0+vRpBQQEaOjQoXJwcJAkHTx4UA888ABX6AIAAABo0exs3QAAAAAAAHdSVFSkBQsWqFevXpKkzMxMzZ07V+PHj9eYMWM0e/ZseXt768yZM/WuXVBQoOnTp6tz587asmXLbfMnTpxQnz591L59e0VHR6uoqEhdu3ZVSkqKJMnPz0/z58+3HAMAAABAS0ToCAAAAAANaM2aNb/K2s3Zjz/+qAkTJmjSpEmW54TOmzdP3bp1k6enpwICAjRv3jzl5uZqwYIF9a5/+vRphYeH6+rVq9XOv/baawoMDFRQUJDatGmjsLAwPfHEE3rzzTclSWazWYsXL9b8+fOVkZFx978oAAAAAPyKEToCAAAAQAPZuXOnZs6c+aur3dxNmzZNo0ePlpubm2XM2dlZK1assBwHBARIkvLy8updv1+/furRo0eN83l5ecrMzKwy5uTkpNLSUsuxvb29pk2bpqioqHrvDwAAAAD3AkJHAAAAAJBUXFys+Ph4vf3224qJidHZs2ctc0lJSfrwww8tIVdxcbE++ugjffjhh4qPj5ck7dq1SyEhISopKdGyZcuUlJQkScrJydGSJUtkGIZ2796tmTNnavHixZar6qypXVhYqHfffVc//fRT05wkG0hLS9O2bds0duzYKuNLlizRtm3bLMfZ2dmSpCeeeKLBexgzZoxSU1P16aefSrrxfMctW7Zo6tSpVdY9+eSTKi4u1ubNmxu8BwAAAABo7ggdAQAAALR4hw8f1qBBg+Tg4KDJkyfr4sWL8vHxsdzOdOTIkVqxYoX++te/SpJcXV0VHh6ut956SwsXLpQkeXh4yM/PT05OTurevbu8vLwUFxcnPz8/TZ8+XZMmTdLatWuVnp6uKVOmKDAwUOXl5XddW5ISExP1xhtvKCEhoalPWZN57733NGDAAMttVW9ydnZWp06dLMeJiYny8fFRZGRkg/cQFRWl7t27a8KECZo2bZr+67/+S8uWLVNYWNhtawcNGqS5c+c2eA8AAAAA0NwROgIAAABo0crKyvSHP/xBo0eP1pgxY9S2bVv9+c9/1qhRoxQZGamjR49Kknr27Fnlda6ururatavl2N/fX23btpWzs7OGDBkif39/jR8/XiNGjNC1a9f0yiuvKCYmRtu2bdOsWbO0f/9+rVy58q5rS1JYWJjWrVunF154oTFOTbOQnp6uDh061LrGMAzFxsZqxYoVcnR0bPAe2rVrp71796pLly764IMPVFxcrIEDB1a71tfXVxkZGSorK2vwPgAAAACgOSN0BAAAANCiffHFFzp+/LjlmYA3DR8+XGVlZYqJialXPZPJVOXYxcVFZrNZvr6+lrEZM2bIbDYrJSXF6tphYWG3XQV4rygrK1NWVpY8PT1rXffVV19p+PDhGjBgQKP1EhMTo8DAQEVERGjfvn3q37+/zpw5c9s6Nzc3VVRU6OTJk43WCwAAAAA0R4SOAAAAAFq0m1cytmnTpsr44MGDJUnHjh2rV71bg8HqtG7dWh07dlRBQUGD176XnD9/XtevX1erVq1qXbdz507NmTOn0fqIjY1VfHy8li1bppiYGMXExOjHH3/U5MmTb1t78+8oJyen0foBAAAAgOaI0BEAAABAi3b//fdLkvbt21dlvFOnTnJwcJCHh0e96tUlGCwtLVV+fr46d+7c4LXvJe3bt5e7u7uKi4trXffwww/Lzc2t0fpYvXq1nnrqKZnNZklSRESEIiMjtWPHDl28eLHK2gsXLkiS5bmbAAAAANBSEDoCAAAAaNH69+8vSbfd6vTIkSMqLy+33LLTbDbr2rVrtdYymUy6fv36HfdMTU3VtWvXFBwc3OC17zW+vr76+eefa13z4osvNmoP6enpt4WLTz/9tMrKyvTTTz9VGc/Ly5PJZNIjjzzSqD0BAAAAQHND6AgAAACgRevdu7eef/55paSkVHlG3zfffKNHH31UUVFRkqRhw4apsLBQsbGxunz5smJjY3Xu3DllZWVZrm7z9PRUfn6+srKydOrUKV2+fFmSVFFRUeU2rRs3blRgYKAldLzb2gcOHNDjjz+u3bt3N8WpsonBgwcrIyOjxvm9e/cqODi42ucrRkVFKSgo6LZgsDo3z3N14W9ISIi2bNmiyspKy1hqaqr8/Pz06KOPVll7+vRpDRs2TM7OznfcEwAAAADuJYSOAAAAAFq8pUuXKjw8XEFBQVq9erViYmKUnJysr7/+Wo6OjpKkcePGKSAgQBEREerXr5/c3d3Vt29f+fv7a9OmTZY1hmGob9++Sk5OlouLiyTJzs5OS5YsUXR0tMLCwpSdna2kpCTL/ndbOzs7W99//71OnjzZxGes6URHRys3N1enTp2qdj4tLU3JycnVzu/cuVPbt2/Xp59+Wuse27dv16uvvipJSkxM1IoVK5Sfn2+ZX7x4sUaMGKHevXtr4cKFioyM1MGDB5WYmCg7u//7Wl1WVqatW7dq+vTpd/OrAgAAAMCvmskwDMPWTQAAANxrxo0bJ0nasGGDjTsBWh5rPn9FRUXKzMyUt7e3OnbsWO2agoICtW3bVtKNq+JuvaKtqKhIdnZ2cnV1lSS99NJLWrlypcrKynT27Fm5ubnpvvvua5DaknTp0qUa69UkISFBoaGh+rV8HVy2bJkyMjK0ePHiaufPnz9veTbnL5WWlmrr1q1ydnbWqFGjrO7jypUrys7OVvv27at91ueGDRsUFxenxMREq/dqKvzvFQAAAICGwpWOAAAAAPD/ubm5aeDAgTUGjpIsoaCkam+h6ebmViUU/CUvL69aA8K7qV3fwPHXKDIyUufOndMPP/xQ7Xx1gaN0I3Tct2+fgoKCGqSP1q1bq2fPntUGjsePH1dcXJzWr1/fIHsBAAAAwK8NoSMAAAAANKIrV66ooqJCJSUltm7lV8vOzk6rVq3Sxx9/rP3799f5dWlpaXrnnXdkNpsbsTspOztb7777rlauXKlWrVo16l4AAAAA0FwROgIAAABAI4mLi9OOHTtkGIZef/11HTp0yNYt/Wo5OTlp+fLlateuXZ1f8+STTzZJCOjo6KhVq1bVeMUlAAAAALQEjfvPPQEAAACgBQsODtaIESMsx05OTjbs5t7g7e1t6xZu4+npaesWAAAAAMDmCB0BAAAAoJG4ubnZugUAAAAAAJoEt1cFAAAAAAAAAAAAYBVCRwAAAAAAAAAAAABWIXQEAAAAAAAAAAAAYBWe6QgAANBIUlNTNW7cOFu3AbQ4qampksTnrxY5OTmSOEe48XkJCAiwdRsAAAAA7gGEjgAAAI1gwIABtm4BuOdkZGRIknr16lXrOgKUO+vYsaPGjh1r6zbQDAQEBPC/WQAAAAAahMkwDMPWTQAAAADAnTzzzDOSpISEBBt3AgAAAAAAbsUzHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYhdARAAAAAAAAAAAAgFUIHQEAAAAAAAAAAABYxWQYhmHrJgAAAADgl9asWaP3339f169ft4wVFhZKkh588EHLmL29vaZNm6bw8PAm7xEAAAAAAPwfQkcAAAAAzc4///lPde/evU5rT5w4oW7dujVyRwAAAAAAoDbcXhUAAABAs9OtWzf17t1bJpOpxjUmk0m9e/cmcAQAAAAAoBkgdAQAAADQLIWHh8ve3r7GebPZrOeff74JOwIAAAAAADXh9qoAAAAAmqXc3Fx5eXmpsrKy2nmTyaSzZ8/qoYceauLOAAAAAADArbjSEQAAAECz1KFDBw0cOFB2drd/bbGzs9OgQYMIHAEAAAAAaCYIHQEAAAA0WxMmTKh23GQyKTw8vIm7AQAAAAAANeH2qgAAAACarQsXLqhdu3YqLy+vMm42m5Wfn68HHnjARp0BAAAAAIBf4kpHAAAAAM2Wh4eHhg4dKnt7e8uYvb29hg8fTuAIAAAAAEAzQugIAAAAoFl77rnnVFlZaTk2DEPPPfecDTsCAAAAAAC34vaqAAAAAJq1K1eu6IEHHtC1a9ckSc7OziosLJSLi4uNOwMAAAAAADdxpSMAAACAZq1169YaPXq0HBwc5ODgoNGjRxM4AgAAAADQzBA6AgAAAGj2nn32WZWXl6u8vFzPPvusrdsBAAAAAAC3MNu6AQAAANzbEhISbN0C7gHXr19X69atZRiGLl26xN8VGsQzzzxj6xYAAAAA4J7BMx0BAADQqEwmk61bAIBq8XUYAAAAABoOt1cFAABAo4uPj5dhGPzwY9XP7t27tWfPHhmGofj4eEmyeU/N/YfPX/U/N/9+AAAAAAANh9urAgAAAPhVGDx4sK1bAAAAAAAANSB0BAAAAPCrYGfHjVoAAAAAAGiu+NYOAAAAAAAAAAAAwCqEjgAAAAAAAAAAAACsQugIAAAAAAAAAAAAwCqEjgAAAAAAAAAAAACsQugIAAAAoMXKyspSRESEcnJybN1Ks1NRUaFvv/3Wcpybm6u///3vio6O1tdff63r169bVT8/P1+7d++udq6kpEQrV67U7NmzlZycrPLycsvcwYMHlZ2dbdXeAAAAAICGR+gIAAAAoMU6ePCgYmNjlZGRYetWmpWioiItWLBAvXr1kiRlZmZq7ty5Gj9+vMaMGaPZs2fL29tbZ86cqXftgoICTZ8+XZ07d9aWLVtumz9x4oT69Omj9u3bKzo6WkVFReratatSUlIkSX5+fpo/f77lGAAAAADQPBA6AgAAAGixxo4dq4KCAj311FM262HNmjU227s6P/74oyZMmKBJkybJ1dVVkjRv3jx169ZNnp6eCggI0Lx585Sbm6sFCxbUu/7p06cVHh6uq1evVjv/2muvKTAwUEFBQWrTpo3CwsL0xBNP6M0335Qkmc1mLV68WPPnzycsBgAAAIBmhNARAAAAQIv24IMP2mzvnTt3aubMmTbbvzrTpk3T6NGj5ebmZhlzdnbWihUrLMcBAQGSpLy8vHrX79evn3r06FHjfF5enjIzM6uMOTk5qbS01HJsb2+vadOmKSoqqt77AwAAAAAaB6EjAAAAgBarsrJSu3bt0v79+y1jZ8+e1cKFC1VZWakjR45o3rx5Wrt2rSorKy1rcnJytGTJEhmGod27d2vmzJlavHix5eq9pKQkffjhh5agrri4WB999JE+/PBDxcfHS5J27dqlkJAQlZSUaNmyZUpKSpIkFRYW6t1339VPP/3UVKfBIi0tTdu2bdPYsWOrjC9ZskTbtm2zHN98puITTzzR4D2MGTNGqamp+vTTTyXdeL7jli1bNHXq1CrrnnzySRUXF2vz5s0N3gMAAAAAoP7Mtm4AAAAAAGzh6NGjeuutt7Rx40Z9/PHH6tevn5KSkjRx4kQVFBTIMAylp6eroKBAb775pnJycjRz5kzFxcVpypQpunbtmjIyMlRWVqb8/HzNnz9fa9as0f/+7/9q5MiR+s1vfqOioiL98Y9/lKurq8LDw9WxY0f5+voqNDRUHh4e8vPz0z//+U91795d7u7ukqTExES98cYbatOmjaZMmdKk5+S9997TgAEDLLdVvcnZ2VmdOnWyHCcmJsrHx0eRkZEN3kNUVJTi4uI0YcIEHTx4UJmZmVq2bJlGjx5929pBgwZp7ty5GjNmTIP3AQAAAACoH650BAAAANAi+fj4aPbs2VXGRo4cqYkTJ0qSevXqpZUrVyopKUmPPfaYNm3aJEkaP368RowYoWvXrumVV15RTEyMtm3bplmzZmn//v1auXKlJKlnz55Varu6uqpr166WY39/f7Vt21bOzs4aMmSI/P39JUlhYWFat26dXnjhhcb61WuUnp6uDh061LrGMAzFxsZqxYoVcnR0bPAe2rVrp71796pLly764IMPVFxcrIEDB1a71tfX1xL8AgAAAABsi9ARAAAAQIvl5OR021irVq0kqcpzB318fHTmzBnLsYuLi8xms3x9fS1jM2bMkNlsVkpKSr16MJlMVY5dXFwUFhZ229WGja2srExZWVny9PSsdd1XX32l4cOHa8CAAY3WS0xMjAIDAxUREaF9+/apf//+Vc7/TW5ubqqoqNDJkycbrRcAAAAAQN0QOgIAAADAHdjb28swjFrXtG7dWh07dlRBQUG9at8aOtrK+fPndf36dUvoWpOdO3dqzpw5jdZHbGys4uPjtWzZMsXExCgmJkY//vijJk+efNvaNm3aSLrxjE0AAAAAgG0ROgIAAABAAygtLVV+fr46d+5cr9c1l9Cxffv2cnd3V3Fxca3rHn74Ybm5uTVaH6tXr9ZTTz0ls9ksSYqIiFBkZKR27NihixcvVll74cIFSZKXl1ej9QMAAAAAqBtCRwAAAABoAKmpqbp27ZqCg4MlSWazWdeuXav1NSaTSdevX2+K9urE19dXP//8c61rXnzxxUbtIT09/bZw8emnn1ZZWZl++umnKuN5eXkymUx65JFHGrUnAAAAAMCdEToCAAAAaLFKS0slSYWFhZaxS5cuSbrxjMObCgsLVVpaWuUWqxUVFTp27JjleOPGjQoMDLSEjsOGDVNhYaFiY2N1+fJlxcbG6ty5c8rKyrJcoefp6an8/HxlZWXp1KlTunz5sg4cOKDHH39cu3fvbrTfuyaDBw9WRkZGjfN79+5VcHBwtc9XjIqKUlBQ0G3BYHVu/v7VhbIhISHasmWLKisrLWOpqany8/PTo48+WmXt6dOnNWzYMDk7O99xTwAAAABA4yJ0BAAAANAifffdd5ZnE8bHx2vbtm3as2ePtmzZIkl65513lJ+fr88++0x79+5VcXGx5syZo4qKCkmSnZ2dlixZoujoaIWFhSk7O1tJSUmW+uPGjVNAQIAiIiLUr18/ubu7q2/fvvL399emTZssawzDUN++fZWcnCwXFxdlZ2fr+++/18mTJ5v4jEjR0dHKzc3VqVOnqp1PS0tTcnJytfM7d+7U9u3b9emnn9a6x/bt2/Xqq69KkhITE7VixQrl5+db5hcvXqwRI0aod+/eWrhwoSIjI3Xw4EElJibKzu7/vsKWlZVp69atmj59+t38qgAAAACABmYyfvlPdQEAAIAGZjKZFB8fr2eeecbWreAekpCQoNDQUNnq68xLL72klStXqqysTGfPnpWbm5vuu+++atcWFBSobdu2km5c2XfrVXlFRUWys7OTq6urZezSpUs11quPu/n8LVu2TBkZGVq8eHG18+fPn9f9999/23hpaam2bt0qZ2dnjRo16q57vunKlSvKzs5W+/bt5eHhcdv8hg0bFBcXp8TExHrXtvXfDwAAAADci7jSEQAAAACs4OXlVcfPm1QAABUMSURBVGtAeDNwlFTtbUDd3NyqBI6SGiRwvFuRkZE6d+6cfvjhh2rnqwscpRuh4759+xQUFNQgfbRu3Vo9e/asNnA8fvy44uLitH79+gbZCwAAAABgPUJHAAAAtFglJSVKSkrS66+/bhnLyspSRESEcnJyrKrdUHXuVkpKitavX1/lZ+PGjdqzZ4/+9a9/2aSne8mVK1dUUVGhkpISW7fS4Ozs7LRq1Sp9/PHH2r9/f51fl5aWpnfeeUdms7kRu5Oys7P17rvvauXKlWrVqlWj7gUAAAAAqDtCRwAAALRYX3zxhf70pz/ps88+s4wdPHhQsbGxysjIsKp2Q9W5W35+fjp16pSeffZZvfDCC7p06ZIKCgqUlJSk0NBQPfLII3rzzTdVXl5uk/5+zeLi4rRjxw4ZhqHXX39dhw4dsnVLDc7JyUnLly9Xu3bt6vyaJ598sklCQEdHR61atarGKy4BAAAAALbRuP8EFQAAAGjGxo4dqw0bNuj777+vMlZQUKAHH3ywXrXWrFmj8PBwq+s0FHd3d73wwguaNWuWunTpohdffNEyZxiGNm3apIkTJyotLU2bNm267faeqFlwcLBGjBhhOXZycrJhN43L29vb1i3cxtPT09YtAAAAAACqwZWOAAAAaNHs7OxkZ1f1/xbXNyjcuXOnZs6cedu4rQLHm2p6LqDJZNLYsWO1fPly/c///I8GDx6ssrKyJu7u18vNzU3u7u6WH27xCQAAAAAAVzoCAACgmcnJydHnn3+ul19+WXv27NGXX36phx56SBMnTrSEOxcuXND69es1adIkbd++Xenp6frzn/8ss9ms3NxcffHFF8rJydGgQYP0+9//vkr98+fPa+PGjTp9+rR++9vfyjAMmUwmy3xlZaX27NmjNm3aqF+/fpbxkpISJSYm6sSJE+rVq5eGDx8uNzc37dq1SyEhITKZTFq2bJk6dOigkSNH1linuLhYycnJOnbsmLy8vDRs2DB5eXlZ5s+ePavNmzdrypQpOnr0qLZu3Spvb2+NHz/eEo4WFhbqk08+UURERL1uf3mr0NBQrVmzRsnJyUpLS9N//Md/SFKt57Au/RmGoT179ujQoUOyt7dXjx49NHToUEuNO71HAAAAAADg14crHQEAANBsxMXFyc/PT9OnT9ekSZO0du1apaena8qUKQoMDFR5eblWr16tjh076tVXX9XixYs1c+ZMzZgxQ0ePHtWuXbv09ttvq0+fPurZs6dCQkI0efJkS/0TJ07oP//zP9WrVy/NmTNHhYWFSkxMtISOR48eVWhoqH73u9/pwIEDltcdP35coaGh8vPz01tvvaXExER16dJFWVlZ8vDwkJ+fn5ycnNS9e3d5eXnVWOfw4cMaNGiQHBwcNHnyZF28eFE+Pj5as2aNJCkpKUl9+/bV1KlTtWjRIr3//vtKTU1VeHi4/va3v1nqJCYm6o033lBCQoLV5zwgIECStHfvXkmq9RzWtb8333xTJ0+e1NSpUzVgwAC9+eablrk7vUcAAAAAAOBXygAAAAAakSQjPj6+zuufe+45w2QyGUeOHLGMzZo1y5BkLF261DAMwxg/frwhydi8ebNhGIZx7Ngxo7i42OjcubNRUlJied3EiRMNSca+ffsMwzCM/v37G3/5y18s85WVlUbnzp2Nbt26WcbS09MNScbHH39sGIZhVFRUGP7+/sby5cstaw4cOGA4OjoaSUlJhmEY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
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
<h3 id="4.3.3-Training-Fusion-Model">4.3.3 Training Fusion Model<a class="anchor-link" href="#4.3.3-Training-Fusion-Model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[35]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">BATCH_SIZE</span> <span class="o">=</span> <span class="mi">32</span>
<span class="n">EPOCHS</span> <span class="o">=</span> <span class="mi">30</span>
<span class="n">VAL_SPLIT</span> <span class="o">=</span> <span class="mf">0.25</span>

<span class="n">history</span> <span class="o">=</span> <span class="n">train_model</span><span class="p">(</span><span class="n">fusion_model</span><span class="p">,</span> <span class="s1">&#39;adam&#39;</span><span class="p">,</span> <span class="n">BATCH_SIZE</span><span class="p">,</span> <span class="n">EPOCHS</span><span class="p">,</span> <span class="n">VAL_SPLIT</span><span class="p">,</span> 
                      <span class="n">inputs</span><span class="o">=</span><span class="p">[</span><span class="n">train_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">train_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">],</span>
                      <span class="n">outputs</span><span class="o">=</span><span class="n">train_df</span><span class="p">[</span><span class="s1">&#39;rating&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Epoch 1/30
1891/1891 [==============================] - 19s 10ms/step - loss: 1.3110 - mean_squared_error: 1.3110 - rmse: 1.0232 - val_loss: 0.7806 - val_mean_squared_error: 0.7806 - val_rmse: 0.8729
Epoch 2/30
1891/1891 [==============================] - 18s 9ms/step - loss: 0.6879 - mean_squared_error: 0.6879 - rmse: 0.8198 - val_loss: 0.7541 - val_mean_squared_error: 0.7541 - val_rmse: 0.85866887 - 
Epoch 3/30
1891/1891 [==============================] - 20s 11ms/step - loss: 0.5176 - mean_squared_error: 0.5176 - rmse: 0.7101 - val_loss: 0.8000 - val_mean_squared_error: 0.8000 - val_rmse: 0.8847
Epoch 4/30
1891/1891 [==============================] - 21s 11ms/step - loss: 0.3973 - mean_squared_error: 0.3973 - rmse: 0.6209 - val_loss: 0.8495 - val_mean_squared_error: 0.8495 - val_rmse: 0.9115r: 0.3 - ETA: 1s - loss: 0.3941 - mean_
Epoch 5/30
1891/1891 [==============================] - 19s 10ms/step - loss: 0.3315 - mean_squared_error: 0.3315 - rmse: 0.5668 - val_loss: 0.8912 - val_mean_squared_error: 0.8912 - val_rmse: 0.9342
Epoch 6/30
1891/1891 [==============================] - 18s 9ms/step - loss: 0.2907 - mean_squared_error: 0.2907 - rmse: 0.5308 - val_loss: 0.9144 - val_mean_squared_error: 0.9144 - val_rmse: 0.9459
Epoch 7/30
1891/1891 [==============================] - 20s 11ms/step - loss: 0.2593 - mean_squared_error: 0.2593 - rmse: 0.5010 - val_loss: 0.9372 - val_mean_squared_error: 0.9372 - val_rmse: 0.9570
Epoch 8/30
1891/1891 [==============================] - 19s 10ms/step - loss: 0.2349 - mean_squared_error: 0.2349 - rmse: 0.4765 - val_loss: 0.9497 - val_mean_squared_error: 0.9497 - val_rmse: 0.9635
Epoch 9/30
1891/1891 [==============================] - 19s 10ms/step - loss: 0.2122 - mean_squared_error: 0.2122 - rmse: 0.4526 - val_loss: 0.9733 - val_mean_squared_error: 0.9733 - val_rmse: 0.9754
Epoch 10/30
1891/1891 [==============================] - 22s 12ms/step - loss: 0.1944 - mean_squared_error: 0.1944 - rmse: 0.4334 - val_loss: 0.9873 - val_mean_squared_error: 0.9873 - val_rmse: 0.9819
Epoch 11/30
1891/1891 [==============================] - 22s 12ms/step - loss: 0.1797 - mean_squared_error: 0.1797 - rmse: 0.4167 - val_loss: 1.0073 - val_mean_squared_error: 1.0073 - val_rmse: 0.9914
Epoch 12/30
1891/1891 [==============================] - 22s 12ms/step - loss: 0.1664 - mean_squared_error: 0.1664 - rmse: 0.4004 - val_loss: 1.0212 - val_mean_squared_error: 1.0212 - val_rmse: 0.9984 0.1642 - 
Epoch 00012: early stopping
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="4.3.4-Plotting-Fusion-Model-Learning-Curve">4.3.4 Plotting Fusion Model Learning Curve<a class="anchor-link" href="#4.3.4-Plotting-Fusion-Model-Learning-Curve">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[36]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">learning_plot</span><span class="p">(</span><span class="n">history</span><span class="p">,</span> <span class="s1">&#39;rmse&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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8MHccMMNACxfvpyJEycybtw4jjjiCB544AEA7rrrLk488USOPvpoLrzwQtatW7fjP6IkSVKF6HUBuhRX437729/m4IMPZv78+XznO98B4LHHHmP69OksXLgQgBtvvJF58+Yxd+5crr/+elauXLndeZ577jmuuOIKnnrqKQYPHswtt9zS5ucNGzaMxx9/nMsvv5xrr70WgG984xtMmTKFxx9/nA984AMsbecLrV+/niOOOIJHH32UU045BYBRo0Zxzz338O53v3tbWH/kkUe45pprAPjFL37Be9/7XubPn88f/vAHxo0bx2uvvca3vvUt7r77bh5//HEmTJjA9773vR3/ESVJUm67elqquqZHrAOdx+jR2bSNttp3peOOO67FmsbXX389t956KwAvvvgizz33HEOHDm3xnjFjxjBu3DgAjjnmGBYvXtzmuc8///xtx/zqV78C4MEHH9x2/jPPPJMhQ4a0+d6qqir++q//ukXbOeecA8CRRx7JunXrGDRoEIMGDaJ///6sXr2aY489lo9//ONs2rSJ8847j3HjxnHfffexcOFCTj75ZAA2btzIiSee2OXfR5Ik7ZyWN4nBm8TsRr1uBHp3XY07YMCAba8bGhq4++67mT17Nn/4wx8YP358m2se77nnntteV1VVsXnz5jbP3XRc8TEppS7V1b9/f6qqqto8X58+fVrU0KdPHzZv3szEiRO5//77GTFiBJdccgk///nPSSlx+umnM3/+fObPn8/ChQv5j//4jy7VIEmSdl4ppqWqa3pdgG55NS675GrcQYMGsXbt2nb3r1mzhiFDhlBdXc3TTz/NI488suMf1o5TTjmFm266CcjmJq9atWqXnXvJkiXst99+fPKTn+QTn/gEjz/+OCeccAIPPfQQzz//PACNjY08++yzu+wzJUlSx7xJTPn0ugANzVfjbt3KLrkad+jQoZx88skcccQRfOlLX9pu/5lnnsnmzZsZO3Ys//iP/8gJJ5ywcx/Yhq997WvcddddHH300dxxxx0ccMABu+zW3A0NDYwbN47x48dzyy238NnPfpa3ve1t/PSnP+Xiiy9m7NixnHDCCdsuaJQkSaXnTWLKJ7r6p//uYsKECWnu3Lkt2hYtWsRhhx1Wpoq6h7feeouqqir69u3L7Nmzufzyy5k/f36X37927dpdFrh3lP24YxoaGpg0aVK5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
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
<h3 id="4.3.5-Fusion-Model-on-Test-Set">4.3.5 Fusion Model on Test Set<a class="anchor-link" href="#4.3.5-Fusion-Model-on-Test-Set">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Building Architecture and Loading Weights</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[37]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fusion_model</span> <span class="o">=</span> <span class="n">build_Fusion_model</span><span class="p">(</span>
    <span class="n">num_users</span><span class="o">=</span><span class="n">num_users</span><span class="p">,</span>
    <span class="n">num_items</span><span class="o">=</span><span class="n">num_items</span><span class="p">,</span>
    <span class="n">MF_dim</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span>
    <span class="n">MF_reg</span><span class="o">=</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">),</span>
    <span class="n">MLP_layers</span><span class="o">=</span><span class="p">[</span><span class="mi">64</span><span class="p">,</span> <span class="mi">32</span><span class="p">,</span> <span class="mi">16</span><span class="p">,</span> <span class="mi">8</span><span class="p">],</span>
    <span class="n">MLP_regs</span><span class="o">=</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">])</span>

<span class="n">fusion_model</span> <span class="o">=</span> <span class="n">load_trained_model</span><span class="p">(</span><span class="n">fusion_model</span><span class="p">,</span> <span class="s1">&#39;model_tmp/model.hdf5&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Making Predictions</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[38]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">predictions</span> <span class="o">=</span> <span class="n">fusion_model</span><span class="o">.</span><span class="n">predict</span><span class="p">([</span><span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;userId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;movieId&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Test-Set RMSE</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[39]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">error</span> <span class="o">=</span> <span class="n">rmse</span><span class="p">(</span><span class="n">test_df</span><span class="p">[</span><span class="s1">&#39;rating&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">predictions</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;The test-set RMSE of rating predictions is&#39;</span><span class="p">,</span> <span class="nb">round</span><span class="p">(</span><span class="n">error</span><span class="p">,</span> <span class="mi">4</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>The test-set RMSE of rating predictions is 0.8709
</pre>
</div>
</div>

</div>
</div>

</div>
    </div>
  </div>
</body>

 


</html>
