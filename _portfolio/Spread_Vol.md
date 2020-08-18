---
title: "Effect of Crisis on Roll Spreads & Volatilities"
excerpt: "Intra-Day Spreads & Volatilities"
collection: portfolio
---

<html>
<head><meta charset="utf-8" />

<title>Effect of Crisis on Roll Spreads & Volatilities</title>

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
<h1 id="Effect-of-Crisis-on-Roll-Spreads-&amp;-Volatilities">Effect of Crisis on Roll Spreads &amp; Volatilities<a class="anchor-link" href="#Effect-of-Crisis-on-Roll-Spreads-&amp;-Volatilities">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In this exericse, we will be calculate roll spreads and volatilities using 1-minute transaction data, for each trading day during Feb and Mar 2020. We will be ignoring any dta before 0931 or after 1559 to isolate the most volatille intra-day periods. We will be exploring the effect of the market crisis on the following 5 tickers: DB, GM, UAL, XOM, GPRO.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For each of the stocks, I calculate the roll spreads and volatilities for each day and plot them. In order to test the difference between February and March, I conduct a t-test and report the coefficients and p-value comparing the means of each variable between the months. These are reported at the top of each diagram. <br></p>
<p>For instance, a positive coefficient with a p-value less than 0.01 indicates a statistically significant higher spread / vol on average for March compared to Feburary.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here we employ the framework from that bid-ask spread induces negative autocorrelation in observed returns based on transaction prices. Given the assumed structure, the first order autocovariance of transaction returns is
$R_t = ln(P_t) - ln(P_{t-1})$ and the first-lag covariance is $Cov(R_t, R_{t-1}) = -s^2/4$. Using this we can then recover an estimate of the effective spread via moment estimation.</p>
<p>On limitation here is that if the autocovariance is positive, then we cannot use the method of moments. Harris (1990), for example, finds that there is a 17.4% probability of obtaining positive serial covariance from 1 year of daily data for a stock with spread of 1% and daily standard deviation of 2%. An alternative would be to use MCMC simulations to compute full posterior distribution.</p>
<p>This same roll framework can be used to estimate realized volatility over some interval. Here, the formula for volatility is: $\sigma^2=Var(R_t)+s^2/2$.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Dependencies">Dependencies<a class="anchor-link" href="#Dependencies">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[276]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">from</span> <span class="nn">datetime</span> <span class="kn">import</span> <span class="n">datetime</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">warnings</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">from</span> <span class="nn">scipy</span> <span class="kn">import</span> <span class="n">stats</span>

<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>
</pre></div>

    </div>
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
<div class="prompt input_prompt">In&nbsp;[344]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">all_data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;Data.csv&#39;</span><span class="p">)</span>

<span class="n">DB</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SYM_ROOT&#39;</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;DB&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">GM</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SYM_ROOT&#39;</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;GM&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">UAL</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SYM_ROOT&#39;</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;UAL&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">XOM</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SYM_ROOT&#39;</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;XOM&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">GPRO</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SYM_ROOT&#39;</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;GPRO&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here, we apply the following standard filter:</p>
<ul>
<li>Keep trades during regular trading hours, and exclude those in opening or closing auction</li>
<li>Exclude first and last few minutes (depending on application). However, in the last couple of years, there has been a much higher proportion of activity right aroudn the open and close.</li>
<li>Exclude conditions not under <code>@, I, F</code></li>
<li>A single order may reuslt in multiple trade prints, typically all at same price and approximately same time. We want to combine all trade prints in same ticker at same price within a millisecond.</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[312]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># FILTER: single orders which may result in multiple trade prints, within a millisecond</span>

<span class="k">def</span> <span class="nf">drop_same_trade</span><span class="p">(</span><span class="n">data</span><span class="p">):</span>
    
    <span class="n">data</span><span class="p">[</span><span class="s1">&#39;SEC&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">&#39;TIME_M&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="nb">round</span><span class="p">(</span><span class="nb">float</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s1">&#39;:&#39;</span><span class="p">)[</span><span class="o">-</span><span class="mi">1</span><span class="p">]),</span> <span class="mi">4</span><span class="p">))</span>
    
    <span class="n">SEC</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">&#39;SEC&#39;</span><span class="p">]</span>
    <span class="n">EX</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">&#39;EX&#39;</span><span class="p">]</span>
    <span class="n">PRICE</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">&#39;PRICE&#39;</span><span class="p">]</span>
    
    <span class="n">index_drop</span> <span class="o">=</span> <span class="nb">list</span><span class="p">()</span>
    <span class="n">last</span> <span class="o">=</span> <span class="n">data</span><span class="o">.</span><span class="n">index</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>
    <span class="k">for</span> <span class="n">idx</span> <span class="ow">in</span> <span class="n">data</span><span class="o">.</span><span class="n">index</span><span class="p">[:</span><span class="o">-</span><span class="mi">1</span><span class="p">]:</span>
        
        <span class="k">if</span> <span class="n">idx</span> <span class="o">%</span> <span class="mi">10000</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span> <span class="nb">print</span><span class="p">(</span><span class="n">idx</span><span class="p">)</span>
            
        <span class="n">sec</span> <span class="o">=</span> <span class="n">SEC</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span>
        <span class="n">ex</span> <span class="o">=</span> <span class="n">EX</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span>
        <span class="n">price</span> <span class="o">=</span> <span class="n">PRICE</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span>
        <span class="n">ii</span> <span class="o">=</span> <span class="mi">1</span>

        <span class="k">while</span> <span class="mi">0</span> <span class="o">&lt;=</span> <span class="p">(</span><span class="n">SEC</span><span class="p">[</span><span class="n">idx</span><span class="o">+</span><span class="n">ii</span><span class="p">]</span> <span class="o">-</span> <span class="n">sec</span><span class="p">)</span> <span class="o">&lt;</span> <span class="mf">0.001</span><span class="p">:</span>
            <span class="k">if</span> <span class="n">EX</span><span class="p">[</span><span class="n">idx</span><span class="o">+</span><span class="n">ii</span><span class="p">]</span> <span class="o">==</span> <span class="n">ex</span> \
            <span class="ow">and</span> <span class="n">PRICE</span><span class="p">[</span><span class="n">idx</span><span class="o">+</span><span class="n">ii</span><span class="p">]</span> <span class="o">==</span> <span class="n">price</span><span class="p">:</span>
                <span class="n">index_drop</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">idx</span> <span class="o">+</span> <span class="n">ii</span><span class="p">)</span>
            <span class="n">ii</span> <span class="o">+=</span> <span class="mi">1</span>
            <span class="k">if</span> <span class="n">idx</span> <span class="o">+</span> <span class="n">ii</span> <span class="o">&gt;</span> <span class="n">last</span><span class="p">:</span>
                <span class="k">break</span>
                
    <span class="n">index_drop</span> <span class="o">=</span> <span class="nb">set</span><span class="p">(</span><span class="n">index_drop</span><span class="p">)</span>
            
    <span class="n">data</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">index_drop</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">data</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
        
    <span class="k">return</span> <span class="n">data</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[334]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># FILTER 9:30 and 15:59, Condition code (F,I), TRCORR</span>

<span class="k">def</span> <span class="nf">time_condition_filter</span><span class="p">(</span><span class="n">data</span><span class="p">):</span>
    
    <span class="n">index_drop</span> <span class="o">=</span> <span class="nb">list</span><span class="p">()</span>
    <span class="n">TIME_M</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s2">&quot;TIME_M&quot;</span><span class="p">]</span>
    <span class="n">TR_SCOND</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s2">&quot;TR_SCOND&quot;</span><span class="p">]</span>
    <span class="n">TR_CORR</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s2">&quot;TR_CORR&quot;</span><span class="p">]</span>
    
    <span class="k">for</span> <span class="n">idx</span> <span class="ow">in</span> <span class="n">data</span><span class="o">.</span><span class="n">index</span><span class="p">:</span>
        <span class="k">if</span> <span class="n">TIME_M</span><span class="p">[</span><span class="n">idx</span><span class="p">][:</span><span class="mi">5</span><span class="p">]</span> <span class="ow">in</span> <span class="p">[</span><span class="s1">&#39;9:30:&#39;</span><span class="p">,</span><span class="s1">&#39;15:59&#39;</span><span class="p">]:</span>
            <span class="n">index_drop</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">idx</span><span class="p">)</span>
        <span class="k">elif</span> <span class="n">TR_SCOND</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span> <span class="ow">not</span> <span class="ow">in</span> <span class="p">[</span><span class="s1">&#39;F&#39;</span><span class="p">,</span> <span class="s1">&#39;I&#39;</span><span class="p">,</span> <span class="s1">&#39;F I&#39;</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span> <span class="s1">&#39;@  I&#39;</span><span class="p">,</span> <span class="s1">&#39;@F I&#39;</span><span class="p">,</span> <span class="s1">&#39;@F&#39;</span><span class="p">,</span> <span class="s1">&#39;@&#39;</span><span class="p">]:</span>
            <span class="n">index_drop</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">idx</span><span class="p">)</span>
        <span class="k">elif</span> <span class="n">TR_CORR</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span> <span class="o">!=</span> <span class="mi">0</span><span class="p">:</span>
            <span class="n">index_drop</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">idx</span><span class="p">)</span>
            
    <span class="n">data</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">index_drop</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">data</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    
    <span class="k">return</span> <span class="n">data</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[314]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># CALCULATING Roll spreads and volatilities </span>

<span class="k">def</span> <span class="nf">get_results</span><span class="p">(</span><span class="n">data</span><span class="p">):</span>

    <span class="n">results</span> <span class="o">=</span> <span class="nb">list</span><span class="p">()</span>
    <span class="k">for</span> <span class="n">date</span> <span class="ow">in</span> <span class="n">data</span><span class="o">.</span><span class="n">DATE</span><span class="o">.</span><span class="n">unique</span><span class="p">():</span>
        <span class="n">temp</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="n">data</span><span class="o">.</span><span class="n">DATE</span><span class="o">==</span><span class="n">date</span><span class="p">]</span>
        <span class="n">temp</span> <span class="o">=</span> <span class="n">temp</span><span class="p">[[</span><span class="s1">&#39;TIME_M&#39;</span><span class="p">,</span><span class="s1">&#39;PRICE&#39;</span><span class="p">]]</span>
        <span class="n">temp</span><span class="p">[</span><span class="s1">&#39;RETURN&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">temp</span><span class="p">[</span><span class="s1">&#39;PRICE&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">pct_change</span><span class="p">()</span>
        <span class="n">temp</span><span class="p">[</span><span class="s1">&#39;RETURN_LAG&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">temp</span><span class="p">[</span><span class="s1">&#39;RETURN&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span>
        <span class="n">temp</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
        <span class="n">returns</span> <span class="o">=</span> <span class="n">temp</span><span class="p">[</span><span class="s1">&#39;RETURN&#39;</span><span class="p">]</span>
        <span class="n">temp</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="s1">&#39;PRICE&#39;</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
        
        <span class="n">s</span> <span class="o">=</span> <span class="mi">2</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="o">-</span><span class="n">temp</span><span class="o">.</span><span class="n">cov</span><span class="p">()</span><span class="o">.</span><span class="n">values</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">])</span>
        <span class="n">vol</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">returns</span><span class="o">.</span><span class="n">var</span><span class="p">()</span> <span class="o">-</span> <span class="p">((</span><span class="n">s</span><span class="o">**</span><span class="mi">2</span><span class="p">)</span><span class="o">/</span><span class="mi">2</span><span class="p">))</span>
        <span class="n">yearmonth</span> <span class="o">=</span> <span class="nb">str</span><span class="p">(</span><span class="n">date</span><span class="p">)[:</span><span class="mi">6</span><span class="p">]</span>
                
        <span class="n">results</span><span class="o">.</span><span class="n">append</span><span class="p">([</span><span class="n">date</span><span class="p">,</span> <span class="n">s</span><span class="p">,</span> <span class="n">vol</span><span class="p">,</span> <span class="n">yearmonth</span><span class="p">])</span>
        
    <span class="k">return</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">results</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;date&#39;</span><span class="p">,</span> <span class="s1">&#39;spread&#39;</span><span class="p">,</span> <span class="s1">&#39;vol&#39;</span><span class="p">,</span> <span class="s1">&#39;yearmonth&#39;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[322]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># PLOT the results obtained, with t-test coefficients and p-value for mean difference test</span>

<span class="k">def</span> <span class="nf">plot_results</span><span class="p">(</span><span class="n">results</span><span class="p">):</span>
    
    <span class="n">results</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    
    <span class="n">fig</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span><span class="mi">15</span><span class="p">))</span>

    <span class="n">diff_test</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">ttest_ind</span><span class="p">(</span>
                <span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s2">&quot;202003&quot;</span><span class="p">][</span><span class="s2">&quot;spread&quot;</span><span class="p">],</span>
                <span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s2">&quot;202002&quot;</span><span class="p">][</span><span class="s2">&quot;spread&quot;</span><span class="p">],</span>
                <span class="n">equal_var</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
    
    <span class="n">coef</span><span class="p">,</span> <span class="n">pval</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">diff_test</span><span class="p">[</span><span class="mi">0</span><span class="p">],</span><span class="mi">2</span><span class="p">),</span> <span class="n">diff_test</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span>
    
    <span class="n">ax</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s1">&#39;yearmonth&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202002&#39;</span><span class="p">][</span><span class="s1">&#39;spread&#39;</span><span class="p">])</span>
    <span class="n">ax</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s1">&#39;yearmonth&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202003&#39;</span><span class="p">][</span><span class="s1">&#39;spread&#39;</span><span class="p">])</span>
    <span class="n">ax</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Spread over Time&#39;</span> <span class="o">+</span> <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;Feb Average: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202002&#39;</span><span class="p">][</span><span class="s1">&#39;spread&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">mean</span><span class="p">())</span> <span class="o">+</span> 
                   <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;Mar Average: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202003&#39;</span><span class="p">][</span><span class="s1">&#39;spread&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">mean</span><span class="p">())</span> <span class="o">+</span>
                   <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;t-test Coefficient: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">coef</span><span class="p">)</span> <span class="o">+</span> 
                   <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;p-value: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">pval</span><span class="p">))</span>
    <span class="n">ax</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_xticks</span><span class="p">([])</span>
    <span class="n">ax</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">set_xlabel</span><span class="p">(</span><span class="s1">&#39;Time&#39;</span><span class="p">)</span>
    
    <span class="n">diff_test</span> <span class="o">=</span> <span class="n">stats</span><span class="o">.</span><span class="n">ttest_ind</span><span class="p">(</span>
                <span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s2">&quot;202003&quot;</span><span class="p">][</span><span class="s2">&quot;vol&quot;</span><span class="p">],</span>
                <span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s2">&quot;202002&quot;</span><span class="p">][</span><span class="s2">&quot;vol&quot;</span><span class="p">],</span>
                <span class="n">equal_var</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
    
    <span class="n">coef</span><span class="p">,</span> <span class="n">pval</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">diff_test</span><span class="p">[</span><span class="mi">0</span><span class="p">],</span><span class="mi">2</span><span class="p">),</span> <span class="n">diff_test</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span>
    
    <span class="n">ax</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s1">&#39;yearmonth&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202002&#39;</span><span class="p">][</span><span class="s1">&#39;vol&#39;</span><span class="p">])</span>
    <span class="n">ax</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s1">&#39;yearmonth&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202003&#39;</span><span class="p">][</span><span class="s1">&#39;vol&#39;</span><span class="p">])</span>
    <span class="n">ax</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Vol over Time&#39;</span> <span class="o">+</span> <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;Feb Average: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202002&#39;</span><span class="p">][</span><span class="s1">&#39;vol&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">mean</span><span class="p">())</span> <span class="o">+</span> 
                   <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;Mar Average: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">results</span><span class="p">[</span><span class="n">results</span><span class="p">[</span><span class="s2">&quot;yearmonth&quot;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;202003&#39;</span><span class="p">][</span><span class="s1">&#39;vol&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">mean</span><span class="p">())</span> <span class="o">+</span>
                   <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;t-test Coefficient: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">coef</span><span class="p">)</span> <span class="o">+</span> 
                   <span class="s1">&#39;</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">+</span> <span class="s1">&#39;p-value: </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">pval</span><span class="p">))</span>    
    <span class="n">ax</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_xticks</span><span class="p">([])</span>
    <span class="n">ax</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">set_xlabel</span><span class="p">(</span><span class="s1">&#39;Time&#39;</span><span class="p">)</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">tight_layout</span><span class="p">()</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="DB">DB<a class="anchor-link" href="#DB">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[302]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">DB</span> <span class="o">=</span> <span class="n">drop_same_trade</span><span class="p">(</span><span class="n">DB</span><span class="p">)</span>
<span class="n">DB</span> <span class="o">=</span> <span class="n">time_condition_filter</span><span class="p">(</span><span class="n">DB</span><span class="p">)</span>
<span class="n">DB_results</span> <span class="o">=</span> <span class="n">get_results</span><span class="p">(</span><span class="n">DB</span><span class="p">)</span>
<span class="n">plot_results</span><span class="p">(</span><span class="n">DB_results</span><span class="p">)</span>
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
<h3 id="GM">GM<a class="anchor-link" href="#GM">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[323]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">GM</span> <span class="o">=</span> <span class="n">drop_same_trade</span><span class="p">(</span><span class="n">GM</span><span class="p">)</span>
<span class="n">GM</span> <span class="o">=</span> <span class="n">time_condition_filter</span><span class="p">(</span><span class="n">GM</span><span class="p">)</span>
<span class="n">GM_results</span> <span class="o">=</span> <span class="n">get_results</span><span class="p">(</span><span class="n">GM</span><span class="p">)</span>
<span class="n">plot_results</span><span class="p">(</span><span class="n">GM_results</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABDAAAAQwCAYAAAATlK4WAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjEsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy8QZhcZAAAgAElEQVR4nOzdeZhcVZ3/8fcn+9bZQ0LYAgijgIDjgo4yIjiAiKOyKIIsOv5EGMZdR3FDBBlcGUUWV/ZNBEQBwVFBEFQWBzBCGBJAEkgg3Ul30p09398f59zkplK9Jd3pStXn9Tz1VNU955577u3iIfd7v+ccRQRmZmZmZmZmZrVs0EB3wMzMzMzMzMysOw5gmJmZmZmZmVnNcwDDzMzMzMzMzGqeAxhmZmZmZmZmVvMcwDAzMzMzMzOzmucAhpmZmZmZmZnVPAcwzMzMrGZIukTSWQPdj96QdJykOwa6H2ZmZvXOAQwzM7MGI+kNku6V1CqpRdIfJL16oPtVqyTNlLQ0v9ZIWl76fnpEXBkRBw90P83MzOrdkIHugJmZmW05ksYCvwROAa4DhgH7Ays2oS0Bioi1fdrJASZpcESsKb5HxJ6lsjuBKyLihwPRNzMzs0bmDAwzM7PGsjtARFwdEWsiYllE3BERjwBIOilnZJyfMzQel3RQsbOkOyWdLekPQAewi6Rxkn4k6XlJ8ySdJWlwrr+rpN9Kapa0UNKVksaX2nuFpIckLZF0LTCis45LGiTp85KekfSCpMskjctlt0k6raL+w5KOyJ9fKunXOeNklqR3lepdIulCSbdKagfe1JsLmq/ZPaXvIelUSf+Xz+sr+TrcK6lN0nWShpXqHy7pfyUtznX27s3xzczMGoUDGGZmZo3lCWCNpEslvUXShCp19gNmA5OBLwE3SJpYKj8e+CDQBDwDXAKsBl4CvAI4GPhArivgHGA68DJgB+AMgHwTfxNwOTAR+ClwZBd9Pym/3gTsAowBzs9lVwPvKSpK2gPYCbhF0mjg18BVwDbAMcAFuU7hWODsfE73sPkOAV4JvBb4NPB94L2k89+r6KukVwA/Bk4GJgEXAzdLGt4HfTAzM6srDmCYmZk1kIhoA94ABPAD4EVJN0uaWqr2AnBeRKyKiGuBWcBbS+WXRMTMiFhNCjwcBnw0Itoj4gXg26QgARHxZET8OiJWRMSLwLeAN+Z2XgsMLR3reuD+Lrp/HPCtiJgTEUuBzwLHSBoC3AjsK2mnUt0bImIFcDjwdET8JCJWR8RfgJ8BR5fa/nlE/CEi1kbE8h5ezq58LSLaImIm8FfgjtzvVuA2UqAHUiDo4oj4U86IuZQ0nOe1fdAHMzOzuuIAhpmZWYOJiMci4qSI2J6UDTAdOK9UZV5EROn7M7lO4dnS551IQYjn8xCIxaQsgm0AJE2VdE0eWtIGXEHK7CC3We1YnZleUf4MaT6vqRGxBLiFHDghZThcWerjfkX/ch+PA6Z1ck59YUHp87Iq38eU+vaJir7twIbX28zMzHAAw8zMrKFFxOOkISB7lTZvlyfoLOwIPFferfT5WVLGwOSIGJ9fY0sTX3411395RIwlDaMo2n6+k2N15jnSDX+57mrWBweuBt4j6XWkuTR+V+rjXaX+jY+IMRFxSifntCU9C5xd0bdREXH1APXHzMysZjmAYWZm1kDyZJafkLR9/r4DKVvhj6Vq2wAfljRU0tGkuSturdZeRDwP3AF8U9LYPNHmrpKKYSJNwFKgVdJ2wKdKu99HCkAUxzoCeE0X3b8a+JiknSWNIQVHrs1DWch93Ak4M28vVkf5JbC7pOPzcYZKerWkl3V3vbaAHwAfkrSfktGS3iqpaaA7ZmZmVmscwDAzM2ssS0iTdP4pr7jxR9IcDZ8o1fkTsBuwkDSx5VER0dxFmyeQlmP9G7AIuB7YNpd9GfhHoJU0xOOGYqeIWAkcQZqYswV4d7m8ih+TJvz8PfAUsBz4j1J7K/L+byZN2FlsX0KaWPQYUhbHfOBcYMAnyoyIB4D/R5qMdBHwJOl6mJmZWQVtOOzUzMzMGpmkk4APRMQbBrovZmZmZmXOwDAzMzMzMzOzmucAhpmZmZmZmZnVPA8hMTMzMzMzM7Oa5wwMMzMzMzMzM6t5DmCYmZlVkHSnpA8MdD/MzMzMbD0HMMzMrG5JelrSMklLS6/p/XSsnSWtlXRhf7RfCyTtK+lBSR35fd8u6k6UdKOkdknPSDq2ovzYvL1d0k2SJvZkX0lvlXSPpMWS5kv6oaSmUvm7JN2b+3hnxTF3l/RzSS9KapF0u6R/KJVL0lmS5klqzYGsPSv6da2kZkkLJV0paWzF9bk77ztX0hcqjn+QpMdz334naadS2SWSVlb8Vgf3ZN9c/mZJD+VrNlfSu0plkbcX7f6w4pzPzefUnD8rl+1f0Z+lua0jq/y9f5PLhuTv20i6WtJz+Xr8QdJ+vfg7dnk9zMysMTmAYWZm9e5tETGm9Hqun45zArAIeLek4f1xgOLmcCBIGgb8HLgCmABcCvw8b6/me8BKYCpwHHBhEQzI7xcDx+fyDuCCnuwLjAPOAqYDLwO2A75e2rcFOA/4ryp9Gg/cDPxDbvvP+ZwKRwPvB/YHJgL3AZeXys/K574zsGtu44xS+VXA7/O+bwROlfSv+ZwnAzcAX8jlDwDXVvTvaxW/1TU92VfSHvnYn8vXZx/gwYq29ym1W84u+iDwjrzP3sDbgJMBIuLucn+Aw4GlwK/KDUs6DhhacbwxwP3AK3OfLwVukTQml3f3d+z0epiZWeNyAMPMzBqSpNfmJ/WLJT0s6YCKKrtK+rOktvzUfmK1dnJbIgUwPg+sIt0EFmUXSvpGRf2fS/p4/jxd0s9yVsBTkj5cqneGpOslXSGpDThJ0msk3Zf7/byk88tBBEkHS5qVn3pfIOkulYbDSHq/pMckLVLKQNjgSX4XDgCGAOdFxIqI+A4g4MAq12M0cCTwhYhYGhH3kAIHx+cqxwG/iIjfR8RS0o35EZKauts3Iq6KiF9FREdELAJ+ALy+OHZE/E9EXAdsFKiKiD9HxI8ioiUiVgHfBv5B0qRcZWfgnoiYk2+WrwD2KDWxM3BTRLRFRCtwI7BnqXwGcGVErImI2cA9pfIjgJkR8dOIWE4KfOwj6aWdX/J1utv388DFEXFbRKyOiOZ8/J44EfhmRMyNiHnAN4GTuqh7fUS0FxskjQO+BHy6XDFfw29FxPP5enwfGEYKHnX7dzQzM6vGAQwzM2s4krYDbiE9AZ4IfBL4maQppWonkJ7GbwusBr7TRZNvALYHrgGuI93oFa4mZWUUafkTgIOBayQNAn4BPEx6An0Q8FFJh5T2fztwPSl74EpgDfAxYDLwurzPqbntybnuZ4FJwCzgn0rn/XbgdNIN8RTg7ty/ovyXkj7TyTnuCTwSGy5f9ggb3sAXdgdWR8QTpW0Pl+rumb8DkG+2V+b9utu30j8DMzsp684/A/Mjojl/v4YUuNpd0lDS37GcbfA94HBJE/Lf8UjgtlL5ecAJkoYqDU15HfA/uazynNuB2RXndarS0JYHK4ZpdLfvawEkPZqDWldUCbj9Pg/VuEHSjM7appNrnQNLR5EyKcq+ClwIzK/cp2L/fUkBjCc7qVLt79jZ9TAzswblAIaZmdW7m3K2wmJJN+Vt7wVujYhbI2JtRPyalJZ/WGm/yyPir/lm8QvAu7oYg38icFt+knwVcKikbXLZ3UCQhiVAugm8Lw9leTUwJSLOjIiVETGH9CT6mFLb90XETbmfyyLiwYj4Y37S/jRpKMYbc93DSE/qb4iIIuhSvrH8EHBORDyWy78K7FtkYUTE4RFRbegFpCEBrRXbWoGmTuq2dVG3q7a623cdSf9CuvZf7KTPnZK0PSkg8fHS5udJWROzgGWkISUfK5U/RLoJb86vNWw49OWXpL/vMuBx4EcRcX8u6+76fQfYDdiG9Hu7RNLre7jv9qQMlSNzGyOB75bqvpGUHfJSUmbKL0vDkSrbbgXGFAG3kiOAhcBdxQZJryJlTXyXLijNE3I58OWcuVJZXu3v2NX1MDOzBuUAhpmZ1bt3RMT4/HpH3rYTcHQpsLGYlEWxbWm/Z0ufnyGN8Z9c2bikkaQb3SsBIuI+4O/Asfl7kJ7svyfvcmxRN/djekU/TifNrVCtH8VElL/MT9PbSEGIol/Ty/XzseeWdt8J+O/SsVpIw0C22+iqbWwpMLZi21hgySbU7aq8R8eR9FpSsOioimyNbuVMmzuACyLi6lLRF0lBpR2AEcCXgd9KGpXLrwOeIAUOxpKyIK7IbU4kZWucmffdAThE0qk9OGci4qE89GN1RNxK+o0c0ZN9SQGTn0TEE3lIzlcpBePyUJ2VEbEY+AhpKMzLOml7LLC0ItMGUoDhsmJ7zh66APhIDoZVlf/7+AXwx4g4p0p51b9jN9fDzMwalAMYZmbWiJ4lZViML71GV2Qf7FD6vCNpbouFVdp6J+mm74IcVJhPCghUDiM5Kmc67Af8rNSPpyr60RQR5UyQyhvJC0lP93eLiLGkgEfxtPx50tN4YN3cHNuX9n0WOLnieCMj4t6qV2lDM4G9K57M70314RtPAEMk7Vbatk+p7sz8vejnLsDwvF93+yLpFaR5Md4fEb/pQd/XyUM/7gBujoizK4r3Ba7N80GsjohLSJN27lEqvzgi2nOg4CLWBwp2AdZExGV537mkwFVRXnnOo0kTgXY2/CVY/3ftbt9H2PB3Uvmb6XHbVFzrfLwdSHOgXFbaPBZ4FXBt/s0XmSZzJe2f9xsO3EQKop1c2Yle/h3LfTYzswblAIaZmTWiK4C3STpE0mBJIyQdkIcVFN4raY/89P1M0uSF1VZBOBH4MfBy0g3uvqS0+n0kvRwgIv5CCn78ELg9PwmHtArGEkn/KWlk7stekl7dRd+bSEMsluZJHE8pld0CvFzSO/IQgX8HppXKLwI+q/WrgYyTdHR3Fyu7kzRk4sOShks6LW//bWXFPOzmBuBMSaNz6v/bWb+ix5Wk679/vhk/E7ghIpZ0t6+kvUiZDv8REb+oPHbx9yRNODoo/22H5rKxwO3AHyKi2lwf95Myc6ZKGiTpeFLmzZOl8g/kv9VI0goej+SyJ9IhdGzedxrw7lL5jcBeko7M/fsiaU6Rx3PfjpI0Ju97MGmY08092Rf4CfA+Sbvk3+tnSMNZkLSn0vKug5VWAPkmMA94LO97GfBxSdspLTH8CeCSiutyPHBvxcSgraSMn+I3XwRqXgn8KV/z60nZISdGxNpygz34O3Z1PczMrFFFhF9++eWXX37V5Qt4GnhzJ2X7kcbztwAvkm7+d8xldwLnkAIMbaQU+MlV2tiONMHny6uU3Qp8o/T9C6SnyEdX1JtOytCYT1qG9Y9Fn0mrTVxRUf+fSRkYS0nza5xJWjmjKD+UdDPdSkrxvw84vlR+PPBoPq9ngR+Xym4DTu/ier6CtDznMtJ8EK8olZ1Omgek+D6R9PS9nTykpqKtY/P2dtJSphN7si/pZn1tPv/iNbNUflK+zuXXJbnsxPy9vWL/4u8+gjQvxvP5+jwEHFpqe+f8W2jOv5tfkTJhivIDSUGO1vz3/AEwqlT+5vy3W5Z/YzNKZXfn/dpIE2keU3G9Ot03l3+Z9Dt+kRTsmVDq06x8zi/k61rus4Cv5fNpyZ9V0fbjwL9189/ajHxth+Tvb8zfOyqu9f49/Dt2eT388ssvv/xqzJciussyNDMzs61RnqdgLnBcRPxuoPtjZmZmtjk8hMTMzKyO5GEx4/P8A8X8GH8c4G6ZmZmZbTYHMMzMzOrL60irYywE3kZahWXZwHbJzMzMbPN5CImZmZmZmZmZ1TxnYJiZmZmZmZlZzXMAw8zMzMzMzMxqngMYZmbWMCQ9LWmlpMkV2/8iKSTN6OPj7SxpraQL+7LdWiJpX0kPSurI7/t2UXeipBsltUt6RtKxFeXH5u3tkm6SNLEn+0p6k6RHJS2W1JzrbVcq307SzyW1SJor6UMVxz1Q0kOS2iTNkfTBTvr/4/w7eUlp22mSHpC0QtIlFfWHSbo+/+5C0gEV5ZJ0bu5zc/6sXLa/pKUVr5B0ZC4fLunbkp6TtEjSBZKGltq+QtLz+ZyekPSBUtmM3Fa57S+Uyr8m6dm87zOSTu/kepyQ2ym3/SlJf5W0RNJTkj5Vsc9X8t9qtaQzKsq2lXRzPqc+/+/RzMy2fg5gmJlZo3kKeE/xRdLLgVGb2pikIV0UnwAsAt6dVwXpc90cv19JGgb8HLgCmABcCvw8b6/me8BKYCpwHHChpD1zW3sCFwPH5/IO4IKe7Av8DTgkIsYD04H/A8pBoytIf/epwFuBr0p6Uz7uUODGfOxxwLuBb0nap+Jc3wDsWuWcngPOAn7cyTnfA7wXmF+l7IPAO4B9gL1Jk66eDBARd0fEmOIFHA4sBX6V9/0M8CpgL2B34B+Bz5faPgeYERFjgX8FzpL0yorjjy8d4yul7T8CXpr3/SfgOElHVFyPCaRVbmZWtCnS734CcChwmqRjSuVPAp8GbqlyPdbm8zuySpmZmZkDGGZm1nAuJ91gFU4ELitXkPRWpayMtvwk+oxSWfH0+t8k/R34bbWD5CfpJ5BuKleRbk6LsgslfaOi/s8lfTx/ni7pZ5JezE+xP1yqd0Z+qn+FpDbgJEmvkXRfzkB4XtL55SCCpIMlzZLUmp/U31Xx1Pz9kh7LT/Jvl7RTD6/lAcAQ4LyIWBER3yHdwB5Y5XqMJt2YfiEilkbEPcDNpIAFpKDELyLi9xGxFPgCcISkpu72jYgFEfFc6XBrgJfk447J/Tw7IlZFxMPA9cD7c92JwFjg8kjuBx4D9ij1fQjwXeA/Ks8rIm6IiJuA5iplKyPivNzfNVWu34nANyNibkTMA74JnFSlXlH3+ohoz9/fBnwnIloi4kXgO6VzIiJmRsSK4mt+VQvAbCQiZpWOAymw8JKKaufkYy6s2PdrEfFQRKyOiFmkANfrS+WXRsRtwJIqx10QERcA9/ekn2Zm1ngcwDAzs0bzR2CspJdJGgwcQ3pCX9ZOCj6MJz2xP0XSOyrqvBF4GXBIJ8d5A7A9cA1wHekGtHA1KSujGC4wATgYuEbSIOAXwMPAdsBBwEcllY/zdtJN+HjgStLN8ceAyaRlVA8CTs1tT851PwtMAmaRnqqTy99OepJ+BDAFuDv3ryj/paTPdHKOewKPxIZLmj2St1faHVgdEU+Utj1cqrtn/g5ARMwmZVzs3oN9kbSjpMXAMuCTwNeKoor34vNe+TgL8vm+T9JgSa8DdiJlThQ+Bvw+Ih6pdhE2wwbnTMU5retsCuAcRcpw2aCo4vP2ksaV9rtAUgfwOPA8cGvF/s8oDan5iTYeVvUZSUuBucBo4KpS2WtI2R8XdXVy+fe9PxtnaZiZmW0SBzDMzKwRFVkY/0J62j6vXBgRd0bEoxGxNt+0Xk0KWJSdERHtEbGsk2OcCNwWEYtIN3+HStoml91NeiK+f/5+FHBfziJ4NTAlIs7MT/DnAD8gBVoK90XETbl/yyLiwYj4Y37q/TRpOETR38OAmTlTYDXpqXl5OMOHgHMi4rFc/lVg3yILIyIOj4j/6uQcxwCtFdtagaZO6rZ1Ubertrrbl4j4ex5CMpmU9fJ43r4E+APwBUkjJP0jKZujPGzoauCLwArS3+ZzEfEsgKQdSMM6vljlnDZX5Tm3AmOKwFbJEaRMh7tK234FfETSFEnTgCJLZ915RcSppGu0P3AD6fzIbb2aFKh5Za5zZfmA+W/eRBqacnnRzxz0uwA4LSLWdnN+Z5D+rfmTbuqZmZn1iAMYZmbWiC4HjiWl619WWShpP0m/y0M4Wkk3+ZMrqj3bWeOSRgJHk28KI+I+4O/5mOSMhWtYPxfHsay/gdwJmJ6HgyzOWQWnk+ZvqHpsSbvnTIn5eVjJV0v9nV6un489t7T7TsB/l47VQnqavx3dW0oaflE2lirDA3pQt6vyHh8nIlpYPxdHMT/IccDOpOtwISnjZi6ApJeS/hYnAMNIGRCflvTWvO95wJkRURlc6QuV5zUWWFqR0QJ5mFPF9rOBvwD/C9wL3EQaqrSgvGNErMlDWLYHTsnblkbEAzngtQA4DThYUlPFvhERfyFltXw5bz6VlHXzx65OTNJppGv61tJQFjMzs83iAIaZmTWciHiGNKnjYaQn05WuIs2xsENEjCOlylc+Fa+8ySx7J+lm9IIcVJhPCghUDiM5Kmc67Af8LG9/FngqIsaXXk0RcVgXx76QlHGwW5548fRSf58n3bwC69L6ty/t+yxwcsXxRkbEvV2cX2EmsHdFxsDeVB8y8AQwRNJupW37lOrOzN+Lfu4CDM/7dbdvpSHANuTgQEQ8kzNJpkTEfqTgzp9z3b2AJyLi9pzRMos0weRbcvlBwNdLf0eA+1Sxgsom2uCcq51TzgA5gIpAW868OS0itouIXUhzcDzYRVbEEDqfA6P4PXX278LyvgcB7yxdj38Cvinp/FKf30+aZPSgiJi7UWtmZmabyAEMMzNrVP8GHFgxWWGhCWiJiOV5vH9vb1ZPJK1K8XJg3/x6PbCP0qon5CfbC4EfArdHxOK875+BJZL+U9LIPC/DXpJe3cXxmkhDLJbmjIJTSmW3AC+X9I6ckfDvwLRS+UXAZ7V+NZBxko7u4XneSZp/48NKy3qelrdvNLFpvs43AGdKGi3p9aS5PC7PVa4E3qa0fOho4EzghohY0t2+ko6Q9A+SBkmaAnwL+EvOxiDPd9KktKzpe0nzjXwrH/cvwG5KS6lK0q6kFT+K+S52JwUWir8jpAk0b8xtD5E0AhgMDM7DVNatDJOvy4j8dVguLwI+lwEfV1rmdTrwCeCSikt3PHBvnhNknWKf3OfXkiY9/VIu20bSMZLG5N/PIaRsn9/k8v1K12sSaVjRnRHRmredLGlCbvs1pN/Mb/KhTyLN/VJcjwdI2Rmfy20fR8oA+pc8/GkDkobm6zGIFJQakYelFOUjSIErgPK1MzMzcwDDzMwaU0TMjogHOik+lXSzvIQ098F1PW1XUjHx5nkRMb/0epA0b0E5C+Mq4M2UJkiMiDWkG+h9SVkiRZBjHJ37JCnIsoQ0X8a1pfYWkoazfI30lH4P0k3nilx+I3AuaQLRNuCvrM8+QNJtkk6vdtCIWElaBvQEYDFpFYx35O1IOl3SbaVdTgVGAi+QMlBOiYiZua2ZpKE6V+byply/231J2S2/yuf/KGnVjHeW9j0EmENa0vZDwKF55Y5istD3k27i20jzTPyMdM2JiBfKf8fc3sLS3CefJw2x+AxpudRlbLic6ay8bTvg9vy5WOXlYtKErY+SrvsteVvZCWw8eSekjIh7SRPOXgp8JiLuyGVBCmLNzef8DeCjEXFzLt+ldL3+SvotvGd907wTmJ3LryCtwPLdfD0WV1yPlUBbaYjNWaTJYu+XtDS/ypN9/iBfg/eQgh7LWL8SDfn70vz58fzdzMwMAG08zNLMzMzqldIqJ3OB4yLidwPdHzMzM7OecgaGmZlZnZN0iKTxkoazfn6MLidhNDMzM6s1DmCYmZnVv9eRhgQsJM3f8I4uln81MzMzq0keQmJmZmZmZmZmNc8ZGGZmZmZmZmZW8xzAMDMzs5qXl5T9haRWST/N286StFDSfEk75hUvBnfTzv6SZm2ZXpuZmVlfcgDDzMxsKyXpaUlv7qbOnZI+0AfHOkDS3B7Ue42kWyUtltQi6c+S3re5xweOAqYCkyLiaEk7Ap8A9oiIaRHx94gYk5eh7VRE3B0R/9AH/enR9e9i3y9Kiq72l/QVSY9KWi3pjIqyAyStLS1VulTSiZ00ZWZmVhccwDAzM7M+Iel1wG+Bu4CXAJOAU4C39EHzOwFPRMTq/H1HoDkiXuiDtrcoSbsCRwPPd1P1SeDTwC2dlD+XgzbF69K+7KeZmVmtcQDDzMxsKyTpctJN/C/y0/dPV6lzNrA/cH6uc37e/lJJv84ZErMkvau0z2GS/iZpiaR5kj4paTRwGzC99LR/epVufR24NCLOjYiFkTwYEeX2/5+kJ/Oxby6301m/JH0Z+CLw7nzsk4Ffl/pziaQZOaNhSN5noqSfSHpO0iJJN+XtG2SSSJou6WeSXpT0lKQPl8rOkHSdpMvy9Zgp6VU9vf5d+B7wn8DKripFxKURcRuwpBdtm5mZ1S0HMMzMzLZCEXE88Hfgbfnp+9eq1PkccDdwWq5zWg5G/Bq4CtgGOAa4QNIeebcfASdHRBOwF/DbiGgnZVGUn/g/Vz6WpFGk5Vqv76zPkg4EzgHeBWwLPANck8s67VdEfAn4KnBtPvbFFf05qcrhLgdGAXvm9r5dpT+DgF8ADwPbAQcBH5V0SKnav+Y+jgduBs7P17bq9Zf0iKRju7gGRwMrIuLWzur0wjaSFuTAy7fzNTQzM6tbDmCYmZk1lsOBpyPiJxGxOiL+AvyMNKQBYBWwh6SxEbEoIh7qYbsTSP+u6GpYxHHAjyPioYhYAXwWeJ2kGT3oV49J2pYU4PhQPodVEXFXlaqvBqZExJkRsTIi5gA/IAVPCvdExK15bo3LgX26OnZE7B0RV3XSryZSIOYjvT2nKh4H9iUFgg4EXgl8qw/aNTMzq1kOYJiZmdUJSReVhnic3km1nYD98iSbiyUtJgUWpuXyI4HDgGck3ZXnteiJRcBa0g11Z6aTsi4AiIilQDMp+6G7fvXGDkBLRCzqpt5OpGEo5WOeTpostDC/9LkDGFEMU9kEZwCXR8TTm7j/OhExPyL+FhFrI+Ip0lwZR25uu2ZmZrVsU/8HbGZmZgMvNvgS8SHgQ13VAZ4F7oqIf6naYMT9wNslDQVOA64jBQQq26ncr0PSfaSb6N91Uu05UtAAWDdsZBIwr7t+9dKzwERJ4yNicTf1noqI3TbxOF1ekyoOAraXdGr+PgW4TtK5EXHuJvah3Bc/mDIzs7rm/9GZmZltvRYAu/Syzi+B3SUdL2lofr1a0sskDZN0nKRxEbEKaCNlVRTtTJI0rotjfRo4SdKnJE0CkLSPpGty+dXA+yTtK2k4aTjFn3JGQqf96vnlSCLiedKkoxdImpDb+ucqVf8MLJH0n5JGShzp5/AAACAASURBVBosaS9Jr+7hoXpy/csOIs0rsm9+PQecTJrUcyO53yNI/14bImmEpMG57E2SdlKyA/BfwM970RczM7OtjgMYZmZmW69zgM/n4Q+f7KTOfwNH5ZU4vhMRS4CDSfM8PEcaInEuMDzXPx54WlIbKZvjOICIeJwUgJiTj7fRKiQRcS9pPoYDc70W4PvArbn8f4AvkOa2eB7YNfeDHvSrt44nzefxOPAC8NEq/V1DmntjX+ApYCHwQ6CrIE3ZRtc/r1RyXLXKEdGch37Mj4j5wBpgUR5KUwwBuqi0yw+AZcB7gM/lz8fnslcA9wLt+f1R4MOYmZnVMUX0NvvRzMzMzMzMzGzLcgaGmZmZmZmZmdU8BzDMzMzMzMzMrOY5gGFmZmZmZmZmNc8BDDMzMzMzMzOreQ5gmJmZ1RBJB0iaO9D9MDMzM6s1DmCYmZk1KEkzJP1OUoekxyW9uYu6wyX9WFKbpPmSPl5RflBuoyO3uVNP9pX0Wkm/ltQi6UVJP5W0bZXjD5P0WGVwR9KBkh7Kbc+R9MFS2Vsl3ZOXOZ0v6YeSmkrl35D0f5KW5L6fUNH29yXNkrRW0kkVZRdJWlp6rZC0pHS+P5L0TG77fyW9peJcrpf0tKSQdECVa32RpAX5uvxC0nYVf7db89K48yWdL2lIqTwktZf69sNS2W0V/V4p6dFS+dOSlpXK7yiVHZOvR6ukFyRdKmlsqfwKSc/nv8UTkj5Q+Xc0MzPbHA5gmJmZNa6rgb8Ak4DPAddLmtJJ3TOA3YCdgDcBn5Z0KICkycANwBeAicADwLU92ReYAHwfmJHLlwA/qXL8TwEvljdIGgrcCFwMjAPeDXxL0j65yjjgLGA68DJgO+DrpSbagbfleicC/y3pn0rlDwOnAg9VdiYiPhQRY4oX6Vr+NBcPAZ4F3pjb/jxwnaQZpSbuAd4LzK9yrh8BXgfsnfu+CPhuqfwC4AVgW2DffJxTK9rYp9S/dYGEiHhLRb/vLfW78LZSnYNL2/8AvD4ixgG75PM8q1R+DjAjIsYC/wqcJemVVc7PzMxskziAYWZm1gP5yfRnJf0tP/n+iaQRndT9T0nXV2z7b0nfyZ/fl7MJluSsgZO7OG5Ieknp+yWSzip9Pzw/4V8s6V5Je/fwfHYH/hH4UkQsi4ifAY8CR3ayy4nAVyJiUUQ8BvwAOCmXHQHMjIifRsRyUsBiH0kv7W7fiLgt79cWER3A+cDrK/q6M+lm/5yKPk0ExgKXR3I/8BiwR277qoj4VUR0RMSifNx1bUfElyLi8YhYGxF/Au4mBQ6K8u9FxG+A5d1cy9H5ul2a92uPiDMi4unc9i+Bp4BX5vKVEXFeRNwDrKnS5M7A7RGxIF/Pa4E9K8qvi4jlETEf+FVFeY/kgMr+wGU9qR8Rz0bEwtKmNcBLSuUzI2JF8TW/du1tv8zMzDrjAIaZmVnPHQccQrop2530ZL2aa4DDiuEKkgYD7wKuyuUvAIeTbr7fB3xb0j/2tjOSXgH8GDiZlEVxMXCzpOG5/AJJF3Sy+57AnIhYUtr2MFVuhCVNID3tf7iTunuWyyKiHZgN7NmDfSv9MzCzYtt3gdOBZeWNEbGAlPnwPkmDJb2OlMVxTy/aBkDSSODVnZV340hSdsjvO2l7Kun30tO2fwS8XtJ0SaNIv7vbSuXnAcdIGpWHlryFFMQo+30eXnJDReZH2QnA3RHxdMX2K5WG89xRymYpzuUNklpJmTJH5r6Uyy+Q1AE8DjwP3NqzUzYzM+ueAxhmZmY9d35+Ct0CnA28p1qliHiGNOzgnXnTgUBHRPwxl98SEbNz1sBdwB2kJ+G99UHg4oj4U0SsiYhLgRXAa/NxTo2IyqEFhTFAa8W2VqCpk7pFebW6XbXV3b7r5OyRL5KGixTb3gkMjogbOzmPq/M+K0gZFJ+LiGertP0vpEyQL3bSzkWkwMrtnZR35UTgsoiIKscdClwJXBoRj/ewvf8jDUGZB7SRhr+cWSr/PSkA1AbMJQ3ZualU/kbSkJyXAs8BvyzPkVFyAnBJxbbjWD+c53fA7ZLGF4URcU8eQrI9aTjO0+Wd8++tifR7voH0dzEzM+sTDmCYmZn1XPnG+BnS/ASVEyMel8uvYn2A41jWZ18g6S2S/pgnaFwMHAZM3oT+7AR8Ig8fWZzb2qHoVzeWkjJAysaSnqxXq1uUV6vbVVvd7QtAHiZzG/CRiLg7bxsNfA34cLUTyENUriHdiA8j3dR/WtJbK+q9lnT9j4qIJ6q083VgL+Bd1YIQXZG0I3AAVYZhSBoEXA6sBE7rRbPfA4aTsmpGkwIBt5Xa/FXeNpr0u5kAnFvsHBG/z8NUFpPm09iZFAQp9+0NwDRgg6FOEfGHPKSoIyLOARZTJbgWEfNyP66pUrYmD4/ZHjilF+dtZmbWJQcwzMzMem6H0ucdSU+3KydGvDKX/xQ4QNL2pEyMqyCtMAH8DPgGMDUixpPS7NXJMTuAUaXv00qfnwXOjojxpdeoiLi6B+cyE9hFpVU5gH2oMswhzx/xfC6vVndmuSwHHnYlzYvR3b4orVjyP6R5Mi4v1duNlA1wt6T5pJv2bfPQiBmkoMMTEXF7nmtiFnALaUhF0fYrgJuB9+f5LDYg6cu5/sER0VZZ3gPHA3+IiDkV7Yo0FGQqcGRErOpFm/sCl0RES55T4rvAa/JkqRNJv73zI2JFRDSTJj09rIv2go1/XycCN0TE0ir1u9u3MISu57jortzMzKxXHMAwMzPruX+XtL2kiaRVO67trGJEvAjcSbq5fCpPXgkpU2A4ac6E1UrLax5ctZHkf4Fj8xwPh5KGBxR+AHxI0n5KRistHVptGEhl/57IbX9J0og8VGNvUnClmsuAz0uakDMf/h/rhx/cCOwl6cg8sekXgUdKQyY63TfP4fBb0g35RRXH/CspaLRvfn0AWJA/P0taQWU3paVUJWlX0twij+S29yJlCfxHRPyi8oQkfZaUHfPmHAioLB+Wz0fA0HydKv/tVG0YBsCFpKyHt0XEsspCpaVSi0lgh+W2i0DB/cAJksblISinAs9FxMI8ieZTwCmShuThHSeWznlPSfvm38sY4JukoSiPlY49kjQnywb9lrSjpNcX5y3pU6QMjz/k8uNyxkkRdDob+E3+vo3SMqtj8rEPIWUgbRQ0MjMz21QOYJiZmfXcVaT5KuaQJqk8q+vqXAW8mdLwkTxp5oeB60jLYx5LyhDozEdIS30uJs1PsG6ug4h4gBQMOD+39STrVwZB0kWSKoMCZccAr8r7/hdpiMWLed/jJJWzMb5EOudngLuAr0fEr3I/XiRN6Hh2bmu/3Ha3+5KCErsAZ5SG4SzN7a6OiPnFC2gB1ubvayJiNvB+4Duk+SDuIgVgfpjb/gQwBfhRqe3yOX2VlM3wZKn89FL5HaSJQ/+JtNTrMtJEoMX1fR1pmMQGy5Dmm/uTSYGW+VWGFwHMyu1tR5p3YxlpSBDAJ0krn/wfKdB1GOvnU4G06suhuexJYBXwsVw2lRRYayP9TmcAh1dkgLyD9Hv6HRtqIgVeFpGCHocCbykFd/YA7pXUTgpqzCL9/iBlapxCmpNjESnD6KMR0dVv28zMrFfUy6GeZmZmDUnS08AHIuJ/BrovZmZmZo3IGRhmZmZmZmZmVvMcwDAzMzMzMzOzmuchJGZmZmZmZmZW85yBYWZmZmZmZmY1b8hAd2CgTJ48OWbMmDHQ3TAzMzMzMzOzkgcffHBhREyp3N6wAYwZM2bwwAMPDHQ3zMzMzMzMzKxE0jPVtnsIiZmZmZmZmZnVPAcwzMzMzMzMzKzmOYBhZmZmZmZmZjXPAQwzMzMzMzMzq3kOYJiZmZmZmZlZzXMAw8zMzMzMzMxqngMYZmZmZmZmZlbzHMAwMzMzMzMzs5rnAIaZmZmZmZmZ1TwHMMzMzMzMzMys5jmAYWZmZmZmZmY1zwEMMzMzMzMzM6t5DmCYmZmZmZmZWc1zAMPMzMzMzMzMap4DGGZmZmZmZmZW8xzAMDMzMzMzM7Oa5wCGmZmZmZmZmdU8BzDMzMzMzKxxdbTA774Ka1YPdE/MrBsOYJiZmZmZWeP6201w17kw/+GB7omZdcMBDDMzMzMza1zNs9P7kgUD2w8z65YDGGZmZmZm1rha5qT3Jc8PbD/MrFsOYJiZmZmZWeNal4Exf2D7YWbdcgDDzMzMzMwa09o1sOip9NkZGGY1zwEMMzMzMzNrTK1zYc3K9Hmp58Awq3UOYJiZmZmZWWNqycNHho9zBobZVsABDDMzMzMza0zF/Bc7vtZzYJhtBRzAMDMzMzOzxtQyB4aOgumvgPYXYc2qge6RmXXBAQwzMzMzM2tMzbNh4i7QNC199zwYZjXNAQwzMzMzM2tMLUUAY9v03cNIzGqaAxhmZmZmZtZ41qyGRU/DpF3XZ2A4gGFW0xzAMDMzMzOzxtP6d1i7GibuWsrA8EokZrXMAQwzMzMzM2s8zXPS+6RdYfRk0GBnYJjVOAcwzMzMzMys8bTkJVQn7gqDBsOYqQ5gmNU4BzDMzMzMzBrJgplp9Y1G1zwbho2BMduk701TPYTErMY5gGFmZmZm1khuOhV+9ZmB7sXAK1YgkdL3pm29jKpZjXMAw8zMzMyskSyZ70wDSBkYk3Zd/71pmq+LWY1zAMPMzMzMrFFEQEcztDcPdE8G1ppVsPjvaf6LQtO26dqsXjFw/TKzLjmAYWZmZmbWKJa3wtpV0P5iCmY0qkXPQKzZOAMDPIzErIY5gGFmZmZm1ig6cubF2lUpmNGoyiuQFMbkAIZXIjGrWQ5gmJmZmZk1ivaF1T83mmIVlmoZGA5gmNUsBzDMzMzMzBpFRzmA8eLA9WOgtcyG4eNg1KT125q2Te8OYJjVLAcwzMzMzMwaRbsDGEBegaS0hCqkYMagIV6JxKyGOYBhZmZmZtYoyhkYHQ08hKRl9obzXwAMGpTmwXAGhlnN6rcAhqRDJc2S9KSkz1QpHy7p2lz+J0kzSmWfzdtnSTqkuzYl3S3pf/PrOUk39dd5mZmZmZlttdqbYfDw/LlBAxirV0Dr3A3nvyg0TXUGhlkN65cAhqTBwPeAtwB7AO+RtEdFtX8DFkXES4BvA+fmffcAjgH2BA4FLpA0uKs2I2L/iNg3IvYF7gNu6I/zMjMzMzPbqnUshDFTYcT4xh1CsuhpiLUbZ2BAmgfDGRhmNau/MjBeAzwZEXMiYiVwDfD2ijpvBy7Nn68HDpKkvP2aiFgREU8BT+b2um1T0ljgQMAZGGZmZmZmldoXwuhJMHpK4wYwqq1AUmiaBksdwDCrVf0VwNgOeLb0fW7eVrVORKwGWoFJXezbkzbfAfwmIto2s/9mZmZmZvWnYyGMmpwDGA06hKQlBzAm7rJxWdM0WLYIVi3fsn0ysx6pt0k83wNc3VmhpA9KekDSAy++2KARZzMzMzNrXO3NMHpyejVyBsbICTBq4sZlxVKqzsIwq0n9FcCYB+xQ+r593la1jqQhwDiguYt9u2xT0mTSMJNbOutURHw/Il4VEa+aMmVKL0/JzMzMzGwrFpEzMCblAEYDZ2BUm/8CUgYGeB4MsxrVXwGM+4HdJO0saRhpUs6bK+rcDJyYPx8F/DYiIm8/Jq9SsjOwG/DnHrR5FPDLiHC+l5mZmZlZpZXtsHp5zsCYAh3NsHbNQPdqy2ueU33+C0jLqIJXIjGrUUP6o9GIWC3pNOB2YDDw44iYKelM4IGIuBn4EXC5pCeBFlJAglzvOuBvwGrg3yNiDUC1NkuHPQb4r/44HzMzMzOzrV5HzrgYNTkFMgjoaIExDZSZvGoZtM3tIgMjDyFZsmDL9cnMeqxfAhgAEXErcGvFti+WPi8Hju5k37OBs3vSZqnsgM3orpmZmZlZfWtvTu+jiwAGaR6MRgpgtDyV3jvLwBg1EQYNdQaGWY3qtwCGmZmZmZnVkHUZGJNgzcr0udEm8uxqBRIAKWVheA4Ms5rkAIaZmZmZWSPoyBkYoybB2tXpc6MFMJq7CWBAmsjTGRhmNckBDDMzMzOzRlCsOjJ6MqzJAYwiqNEoWmanAM7I8Z3XaZoKLz6x5fpkZj3WX6uQmJmZmZlZLelYmOZ3GD4WRk4ADWrADIw5nU/gWWjaFpZ6CIlZLXIAw8zMzMysEbQ3p+wLCQYNSquRNFoAo2V25xN4FpqmwfJWWNmxZfpkZj3mAIaZmZmZWSPoWJiCFoXRU9YPK2kEK9vT3BY9ycAAZ2GY1SAHMMzMzMzMGkH7Qhg9af330Q2WgdEyJ71P6mICT0gZGOCVSMxqkAMYZmZmZmaNoGoGRgMFMNatQNJNBsaYIoDhlUjMao0DGGZmZmZmjaCYA6MwenJjDSFZl4HRgzkwwBkYZjXIAQwzMzMzs3q3egWsXFKRgTEZVrSlskbQMhtGbwPDm7quN3ICDB7uAIZZDXIAw8zMzMys3hWZFhvMgTFlw7J61zyn++wLSKu0NE1zAMOsBjmAYWZmZmZW7zpykKJyDgxonHkwWmZ3P/9FoWlbz4FhVoMcwDAzMzMzq3frMjCqBTAaIANjxRJYuqD7FUgKzsAwq0kOYJiZmZmZ1buO5vReOQcGNEYGRjGBZ48zMBzAMKtFDmCYmZmZmdW7ahkYoxoogFEsodqTOTAgBTBWLoEVS/uvT2bWaw5gmJmZmZnVu46FoMEwYvz6bcOb0mobHQ0whKQlBzAm9nQIybbpfemC/umPmW0SBzDMzMzMzOpd+0IYNREGlf75L6V5MBphDozmOSkoMWx0z+o3TUvvnsjTrKY4gGFmZmZmVu86mjec/6IwenJjDCHpzQoksD4Dw/NgmNUUBzDMzMzMzOpd+8IN578ojJ7SGAGM5tk9X4EEYMzU9O4MDLOa4gCGmZmZmVm961gIoyZtvL0RhpAsb03n35sMjBHjYMhIZ2CY1RgHMMzMzMzM6l2nGRiTUgZGxJbv05bS2xVIIM0P4qVUzWqOAxhmZmZmZvVszSpYvriTOTCmwOrlsLJ9y/drS2mZk957k4EBaR4MBzDMaooDGGZmZmZm9ayjJb13NgcG1Pc8GEUGxsSde7df0zTPgWFWYxzAMDMzMzOrZx15jovO5sCA+p4Ho2U2jN0eho7s3X7FEJJ6Hl5jtpVxAMPMzMzMrJ4VwYmqGRh5W71nYPRmBZJC0zRY1Q4rlvR9n8xskziAYWZmZmZWz9ZlYDToEJKW2b2f/wLSHBgASxf0bX/MbJM5gGFmZmZmVs/am9N7tQyMUXWegdHRAssW9W4FkkLTtPTueTDMaoYDGGZmZmZm9azIwBg5ceOyoSNgWBN0NG/ZPm0pm7oCCazPwPBKJGY1wwEMMzMzM7N61r4QRk6AwUOql4+eXL8ZGMUKJM7AMKsLDmCYmZmZmdWzjoXV578ojJ5SvwGMltmgQTBhRu/3Hd4EQ0c7A8OshjiAYWZmZmZWz9qbq89/URg9pX6XUW2eDeO2hyHDN23/YilVs/7y0OVw4ykD3YuthgMYZmZmZmb1rGMhjJrUeXk9DyHZ1BVICk3bOoBh/WvWbfDINbCyY6B7slVwAMPMzMzMrJ61L+wmA2NyqrN27Zbr05YQAc1zNm3+i0LTNM+BYf2rbS7EWnjhsYHuyVbBAQwzMzMzs3q1di0sa+l+DoxYA8sXb7l+bQkdzbCidTMzMPIQkoi+65dZWeu89L7grwPbj62EAxhmZmZmZvVq2aL0dLe7OTCg/ubB2JwVSApN02D1Mlje2jd9MitbtXz9MscOYPSIAxhmZmZmZvWquDnqMgMjl9XbPBgtOYCxuXNgACxdsPn9Mau05Ln1n+c7gNETDmCYmZmZmdWrIqtidFeTeBYZGHUWwGieDRoME3ba9DaapqV3z4Nh/aEYPjLpJbBgpocq9YADGGZmZmZm9apHGRh1GsBomQ3jd4TBQze9jSIDwyuRWH9oywGM3Q9N87Us/vvA9mcr4ACGmZmZmVm9WpeB0UUAY+TEDevWi+bZmzf/BcCYqendGRjWH1rnpvfdDk7vngejWw5gmJmZmZnVq46W9D6qiyEkg4ekIEZHHQUwIqBlzubNfwEwfAwMa3IGhvWPtudg5ATY7pWAPA9GDziAYWZmZmZWrzoWwvCxMGR41/VGT6mvISRLX4CVSzc/AwPyUqrOwLB+0DYPxm6fAmUTd3YGRg84gGFmZmZmVq/aF8Koid3XGz2lvoaQ9MUKJIWmabDEq5BYP2idB+O2S5+n7uUARg84gGFmZmZmVq86FnY9gWdh9OT6ysBozgGMSbtsfltN2zoDw/pH21wYWwpgtDwFK5YObJ9qnAMYZmZmZmb1qr256wk8C/U2hKRlNgwaAuN23Py2mqalOTC8xKX1pZUdsGwRjJ2evk/bCwh44W8D2q1a5wCGmZmZmVm96k0GxrJFsGZV//dpS2ieDRNmpAlKN1fTNFizIl0fs77S9lx6H7d9ep+6V3qf/+jA9Gcr4QCGmZmZmVk9ikjzWozuYgWSQpGlUaxasrXrixVICk3T0rtXIrG+1JaXUC2GkIzfEYaP8zwY3XAAw8zMzMysHq1og7WrepiBMSW918MwkmIJ1b5YgQTSHBgASx3AsD7UOi+9F5N4SjB1Ty+l2g0HMMzMzMzM6lGxqkhP58CA+ghgLHkeVnXAxD6YwBOcgWH9oy0HMJqmr982ba80B8batQPTp62AAxhmZmZmZvWoozm99yoDow6WUl23AkkfZWCMKQIYXonE+lDbvPTf5tAR67dN3QtWLoXFTw9Yt2qdAxhmZmZmZvVoXQZGL+bAqIcMjJYcwOirOTCGjYIR45yBYX2rdd764SOFdRN5ehhJZxzAMDMzMzOrRx05gNGTDIwR49Oyo/UQwGieDYOHrV/doS+MmeYMDOtbbfNgbMVvdJuXgQZ5Is8uOIBhZmZmZlaPejMHhpQCHR11MISkZU5aQnXQ4L5rs2kaLFnQd+2ZVcvAGDYqZQ45A6NTDmCYmZmZmdWjjmYYMhKGje5Z/dFT6mcOjL4aPlJo2tZDSKzvrFgCK1ph7PSNy6btBQse3fJ92ko4gGFmZmZmVo/aF/Ys+6IwevLWP4Rk7VpY9FTfTeBZaMpDSCL6tl1rTG3PpffKISSQ5sFY/HdY3rpl+7SVcADDzMzMzKwedSyEUT2YwLMwesrWH8Bomwerl/fdEqqFpm1h7SroaOnbdq0xtc5N75VDSACmvTy9L/jbluvPVsQBDDMzMzOzetTrDIw6GELS0sdLqBaapqZ3T+RpfaFtXnofWyWAUaxE4ok8q+q3AIakQyXNkvSkpM9UKR8u6dpc/idJM0pln83bZ0k6pLs2lZwt6QlJj0n6cH+dl5mZmZnZVqGjuWcrkBRGT4KVS2HVsv7rU39r7uMlVAtN26Z3z4NhfaF1HqD1v6uysdPTqkDzPQ9GNf0SwJA0GPge8BZgD+A9kvaoqPZvwKKIeAnwbeDcvO8ewDHAnsChwAWSBnfT5knADsBLI+JlwDX9cV5mZmZmZluNTcnAKPbbWrXMgSEjqj/Z3hxN09L7UgcwrA+0zYMx28CQY
