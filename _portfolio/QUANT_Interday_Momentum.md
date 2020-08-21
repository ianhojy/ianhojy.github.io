---
title: "Inter-Day Momentum Trading Strategy"
excerpt: "with Optimization for lookback & holding periods"
collection: portfolio
---

<html>
<head><meta charset="utf-8" />

<title>Momentum</title>

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
<h2 id="Inter-Day-Momentum-Trading-Strategy">Inter-Day Momentum Trading Strategy<a class="anchor-link" href="#Inter-Day-Momentum-Trading-Strategy">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Current-Work-(This-notebook)">Current Work (This notebook)<a class="anchor-link" href="#Current-Work-(This-notebook)">&#182;</a></h3><p><em>(As quoted from Algorithmic Trading)</em></p>
<p>Why do many futures returns exhibit serial correlations? And why do
these serial correlations occur only at a fairly long time scale? The explanation lies in the roll return component of the total return of futures. Typically, the sign of roll returns does not vary very
often. In other words, the futures stay in contango or backwardation over long periods of time. The spot returns, however, can vary very rapidly in both sign and magnitude. So if we hold a future over a long period of time, and if the average roll returns dominate the average total returns, we will find serial correlation of total returns.</p>
<h3 id="Future-Work-(coming-soon!)">Future Work (coming soon!)<a class="anchor-link" href="#Future-Work-(coming-soon!)">&#182;</a></h3><p><em>(As quoted from Algorithmic Trading)</em></p>
<p>If we accept the explanation that the time series momentum of futures
is due to the persistence of the signs of the roll returns, then we can devise a cleaner and potentially better momentum signal than the lagged total return. We can use the lagged roll return as a signal instead, and go long when this return is higher than some threshold, go short when this return is lower than the negative of that threshold, and exit any existing position otherwise.</p>

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
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="kn">from</span> <span class="nn">scipy.stats.stats</span> <span class="kn">import</span> <span class="n">pearsonr</span>   
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Data-Import">Data Import<a class="anchor-link" href="#Data-Import">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li><code>idx = 3</code>: Brent Crude Futures</li>
<li><code>idx = 44</code>: Treasury-Note Futures</li>
<li><code>idx = 15</code>: Copper Futures</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Brent-Crude Futures</span>
<span class="n">idx</span> <span class="o">=</span> <span class="mi">3</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cl</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;cl.csv&#39;</span><span class="p">,</span> <span class="n">header</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>
<span class="n">cl</span> <span class="o">=</span> <span class="n">cl</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span>
<span class="n">cl</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(2000,)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Lookback-Holddays-Correlation">Lookback-Holddays Correlation<a class="anchor-link" href="#Lookback-Holddays-Correlation">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>I define a function <code>return correlation</code> that gives the correlation for lagged returns and future returns for a specific lookback and holding pair. Note that we ensure that that there are nonoverlapping periods for correlation calculations. If the look-back is greater than the holding period, we have to shift forward by holding period to generate new returns pair. If the holding period is greater than the lookback, we have to shift forward by lookback period.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">return_correlation</span><span class="p">(</span><span class="n">data</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">):</span>
    
    <span class="n">ret_lag</span> <span class="o">=</span> <span class="p">(</span><span class="n">cl</span> <span class="o">-</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">))</span> <span class="o">/</span> <span class="n">cl</span>
    <span class="n">ret_future</span> <span class="o">=</span> <span class="p">(</span><span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="o">-</span><span class="n">holddays</span><span class="p">)</span> <span class="o">-</span> <span class="n">cl</span><span class="p">)</span> <span class="o">/</span> <span class="n">cl</span>

    <span class="n">badDates</span> <span class="o">=</span> <span class="p">(</span><span class="n">ret_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()</span> <span class="o">|</span> <span class="n">ret_future</span><span class="o">.</span><span class="n">isna</span><span class="p">())</span>
    <span class="n">ret_lag</span> <span class="o">=</span> <span class="n">ret_lag</span><span class="p">[</span><span class="o">~</span><span class="n">badDates</span><span class="p">]</span>
    <span class="n">ret_future</span> <span class="o">=</span> <span class="n">ret_future</span><span class="p">[</span><span class="o">~</span><span class="n">badDates</span><span class="p">]</span>
    
    <span class="c1"># to ensure nonoverlapping periods for correlation calculations</span>
    <span class="k">if</span> <span class="n">lookback</span> <span class="o">&gt;=</span> <span class="n">holddays</span><span class="p">:</span>
        <span class="n">indepSet</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="nb">len</span><span class="p">(</span><span class="n">ret_lag</span><span class="p">),</span> <span class="n">holddays</span><span class="p">)</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">indepSet</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="nb">len</span><span class="p">(</span><span class="n">ret_lag</span><span class="p">),</span> <span class="n">lookback</span><span class="p">)</span>
        
    <span class="n">ret_lag</span> <span class="o">=</span> <span class="n">ret_lag</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">()[</span><span class="n">indepSet</span><span class="p">]</span>
    <span class="n">ret_future</span> <span class="o">=</span> <span class="n">ret_future</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">()[</span><span class="n">indepSet</span><span class="p">]</span>
    
    <span class="k">return</span> <span class="n">pearsonr</span><span class="p">(</span><span class="n">ret_lag</span><span class="p">,</span> <span class="n">ret_future</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We then run a grid-search for various pairs of lookback and holding to see which pairs return signification positive correlation</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">corr_results</span> <span class="o">=</span> <span class="nb">list</span><span class="p">()</span>

<span class="k">for</span> <span class="n">lookback</span> <span class="ow">in</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">60</span><span class="p">,</span> <span class="mi">120</span><span class="p">,</span> <span class="mi">250</span><span class="p">]:</span>
    <span class="k">for</span> <span class="n">holddays</span> <span class="ow">in</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">60</span><span class="p">,</span> <span class="mi">120</span><span class="p">,</span> <span class="mi">250</span><span class="p">]:</span>
        <span class="n">corr</span><span class="p">,</span> <span class="n">pval</span> <span class="o">=</span> <span class="n">return_correlation</span><span class="p">(</span><span class="n">cl</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">)</span>
        <span class="n">corr_results</span><span class="o">.</span><span class="n">append</span><span class="p">([</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">,</span> <span class="nb">round</span><span class="p">(</span><span class="n">corr</span><span class="p">,</span> <span class="mi">2</span><span class="p">),</span> <span class="nb">round</span><span class="p">(</span><span class="n">pval</span><span class="p">,</span> <span class="mi">2</span><span class="p">)])</span>
        
<span class="n">corr_results</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">corr_results</span><span class="p">,</span> 
                            <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;lookback&#39;</span><span class="p">,</span> <span class="s1">&#39;holddays&#39;</span><span class="p">,</span>
                                     <span class="s1">&#39;corr&#39;</span><span class="p">,</span> <span class="s1">&#39;pval&#39;</span><span class="p">])</span>

<span class="n">corr_results</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="s1">&#39;corr&#39;</span><span class="p">,</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">corr_results</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="k">for</span> <span class="n">sig</span> <span class="ow">in</span> <span class="p">[</span><span class="mf">0.05</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">]:</span>
    <span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;sig_&#39;</span><span class="o">+</span><span class="nb">str</span><span class="p">(</span><span class="nb">int</span><span class="p">(</span><span class="n">sig</span><span class="o">*</span><span class="mi">100</span><span class="p">))</span><span class="o">+</span><span class="s1">&#39;%&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;pval&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="s1">&#39;sig&#39;</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&lt;=</span> <span class="n">sig</span> <span class="k">else</span> <span class="s1">&#39;notsig&#39;</span><span class="p">)</span>
<span class="n">corr_results</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">20</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[5]:</div>



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
      <th>lookback</th>
      <th>holddays</th>
      <th>corr</th>
      <th>pval</th>
      <th>sig_5%</th>
      <th>sig_10%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>250</td>
      <td>250</td>
      <td>0.39</td>
      <td>0.45</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>1</th>
      <td>60</td>
      <td>60</td>
      <td>0.37</td>
      <td>0.03</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>2</th>
      <td>25</td>
      <td>60</td>
      <td>0.33</td>
      <td>0.00</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>3</th>
      <td>60</td>
      <td>25</td>
      <td>0.26</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>4</th>
      <td>120</td>
      <td>120</td>
      <td>0.22</td>
      <td>0.44</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>5</th>
      <td>60</td>
      <td>120</td>
      <td>0.22</td>
      <td>0.23</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>6</th>
      <td>120</td>
      <td>250</td>
      <td>0.21</td>
      <td>0.47</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>7</th>
      <td>25</td>
      <td>120</td>
      <td>0.21</td>
      <td>0.07</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>8</th>
      <td>60</td>
      <td>250</td>
      <td>0.16</td>
      <td>0.40</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>9</th>
      <td>120</td>
      <td>60</td>
      <td>0.14</td>
      <td>0.44</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>10</th>
      <td>25</td>
      <td>25</td>
      <td>0.13</td>
      <td>0.24</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>11</th>
      <td>60</td>
      <td>10</td>
      <td>0.12</td>
      <td>0.10</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>12</th>
      <td>10</td>
      <td>60</td>
      <td>0.12</td>
      <td>0.09</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>13</th>
      <td>10</td>
      <td>120</td>
      <td>0.12</td>
      <td>0.09</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>14</th>
      <td>25</td>
      <td>250</td>
      <td>0.11</td>
      <td>0.35</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>15</th>
      <td>120</td>
      <td>10</td>
      <td>0.08</td>
      <td>0.27</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>16</th>
      <td>5</td>
      <td>120</td>
      <td>0.08</td>
      <td>0.13</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>17</th>
      <td>10</td>
      <td>250</td>
      <td>0.07</td>
      <td>0.38</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>18</th>
      <td>120</td>
      <td>25</td>
      <td>0.07</td>
      <td>0.55</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>19</th>
      <td>60</td>
      <td>5</td>
      <td>0.07</td>
      <td>0.19</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Example:-Momentum-Strategy">Example: Momentum Strategy<a class="anchor-link" href="#Example:-Momentum-Strategy">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We run an example of a long-short momentum strategy that goes long if the return over the lookback period is positive, and goes short if the return over the lookback period is negative. Each entry into position is held of a total of <code>holddays</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lookback</span> <span class="o">=</span> <span class="mi">100</span>
<span class="n">holddays</span> <span class="o">=</span> <span class="mi">10</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">longs</span> <span class="o">=</span> <span class="n">cl</span> <span class="o">&gt;</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>
<span class="n">shorts</span> <span class="o">=</span> <span class="n">cl</span> <span class="o">&lt;</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>

<span class="n">pos</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros_like</span><span class="p">(</span><span class="n">cl</span><span class="p">)</span>

<span class="c1"># calculate holdings for holddays</span>

<span class="k">for</span> <span class="n">h</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">holddays</span><span class="p">):</span>
    
    <span class="n">long_lag</span> <span class="o">=</span> <span class="n">longs</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
    <span class="n">long_lag</span><span class="p">[</span><span class="n">long_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
    <span class="n">long_lag</span> <span class="o">=</span> <span class="n">long_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>
    
    <span class="n">short_lag</span> <span class="o">=</span> <span class="n">shorts</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
    <span class="n">short_lag</span><span class="p">[</span><span class="n">short_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
    <span class="n">short_lag</span> <span class="o">=</span> <span class="n">short_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>
    
    <span class="n">pos</span><span class="p">[</span><span class="n">long_lag</span><span class="p">]</span> <span class="o">+=</span> <span class="mi">1</span>
    <span class="n">pos</span><span class="p">[</span><span class="n">short_lag</span><span class="p">]</span> <span class="o">-=</span> <span class="mi">1</span>
    
<span class="n">pos</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">pos</span><span class="p">)</span>

<span class="c1"># returns of positions divided by holddays</span>
<span class="n">ret</span> <span class="o">=</span> <span class="p">(</span><span class="n">pos</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span> <span class="o">*</span> <span class="p">(</span><span class="n">cl</span><span class="o">-</span><span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">holddays</span>
<span class="n">ret</span><span class="p">[</span><span class="n">ret</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="mi">0</span>

<span class="c1"># cumulative return</span>
<span class="n">cumret</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">cumprod</span><span class="p">(</span><span class="n">ret</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">cumret</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Momentum Strategy</span><span class="se">\n</span><span class="si">{}</span><span class="s1"> lookback / </span><span class="si">{}</span><span class="s1"> holddays&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Cumulative Return&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Days&#39;</span><span class="p">)</span>
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
<p>I define a function to simultaneously calculate both the maximum drawdown and maximum drawdown duration.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">drawdown</span><span class="p">(</span><span class="n">data</span><span class="p">):</span>
    
    <span class="n">data</span> <span class="o">=</span> <span class="n">data</span><span class="o">.</span><span class="n">to_numpy</span><span class="p">()</span> <span class="o">+</span> <span class="mi">1</span>

    <span class="c1"># initial states </span>
    <span class="n">max_dd_amount</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="n">max_dd_duration</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="n">max_dd_duration_temp</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="n">max_sofar</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span>

    <span class="c1"># loop</span>
    <span class="k">for</span> <span class="n">ii</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="nb">len</span><span class="p">(</span><span class="n">data</span><span class="p">)):</span>
        <span class="k">if</span> <span class="n">data</span><span class="p">[</span><span class="n">ii</span><span class="p">]</span> <span class="o">&gt;=</span> <span class="n">max_sofar</span><span class="p">:</span>
            <span class="n">max_sofar</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="n">ii</span><span class="p">]</span>
            <span class="n">max_dd_duration_temp</span> <span class="o">=</span> <span class="mi">0</span>
        <span class="k">else</span><span class="p">:</span> 
            <span class="n">dd</span> <span class="o">=</span> <span class="p">(</span><span class="n">data</span><span class="p">[</span><span class="n">ii</span><span class="p">]</span> <span class="o">-</span> <span class="n">max_sofar</span><span class="p">)</span> <span class="o">/</span> <span class="n">max_sofar</span>
            <span class="n">max_dd_amount</span> <span class="o">=</span> <span class="nb">min</span><span class="p">(</span><span class="n">max_dd_amount</span><span class="p">,</span> <span class="n">dd</span><span class="p">)</span>
            <span class="n">max_dd_duration_temp</span> <span class="o">+=</span> <span class="mi">1</span>
            <span class="n">max_dd_duration</span> <span class="o">=</span> <span class="nb">max</span><span class="p">(</span><span class="n">max_dd_duration</span><span class="p">,</span> <span class="n">max_dd_duration_temp</span><span class="p">)</span>

    <span class="k">return</span> <span class="nb">round</span><span class="p">(</span><span class="n">max_dd_amount</span><span class="p">,</span> <span class="mi">4</span><span class="p">),</span> <span class="n">max_dd_duration</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ann_ret</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="mi">252</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Average Annualized Return: &#39;</span><span class="p">,</span> <span class="n">ann_ret</span><span class="p">)</span>

<span class="n">ann_vol</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">std</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="mi">252</span><span class="p">),</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Vol: &#39;</span><span class="p">,</span> <span class="n">ann_vol</span><span class="p">)</span>

<span class="n">sr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">ann_ret</span> <span class="o">/</span> <span class="n">ann_vol</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Sharpe Ratio: &#39;</span><span class="p">,</span> <span class="n">sr</span><span class="p">)</span>

<span class="n">apr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">((</span><span class="n">cumret</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">+</span> <span class="mi">1</span><span class="p">)</span> <span class="o">**</span> <span class="p">(</span><span class="mi">252</span><span class="o">/</span><span class="nb">len</span><span class="p">(</span><span class="n">ret</span><span class="p">))</span> <span class="o">-</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Percentage Return: &#39;</span><span class="p">,</span> <span class="n">apr</span><span class="p">)</span>

<span class="n">max_dd</span><span class="p">,</span> <span class="n">max_dd_days</span> <span class="o">=</span> <span class="n">drawdown</span><span class="p">(</span><span class="n">cumret</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown: </span><span class="si">{}</span><span class="s1">%&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">round</span><span class="p">(</span><span class="n">max_dd</span><span class="o">*</span><span class="mi">100</span><span class="p">,</span><span class="mi">2</span><span class="p">)))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown (Days): &#39;</span><span class="p">,</span> <span class="n">max_dd_days</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Average Annualized Return:  0.1763
Annualized Vol:  0.1622
Sharpe Ratio:  1.09
Annualized Percentage Return:  0.1771
Maximum Drawdown: -14.81%
Maximum Drawdown (Days):  191
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Generalize-Momentum-Strategy-Function">Generalize Momentum Strategy Function<a class="anchor-link" href="#Generalize-Momentum-Strategy-Function">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In the previous section, the holding and lookback periods were given due to the benefit of hindsight. In this following section, we explore the importance of choosing the right lookback and holdings periods.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">momentum</span><span class="p">(</span><span class="n">data</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">,</span> <span class="n">print_stats</span><span class="o">=</span><span class="kc">False</span><span class="p">):</span>

    <span class="n">longs</span> <span class="o">=</span> <span class="n">data</span> <span class="o">&gt;</span> <span class="n">data</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>
    <span class="n">shorts</span> <span class="o">=</span> <span class="n">data</span> <span class="o">&lt;</span> <span class="n">data</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>

    <span class="n">pos</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros_like</span><span class="p">(</span><span class="n">data</span><span class="p">)</span>

    <span class="c1"># calculate holdings for holddays</span>

    <span class="k">for</span> <span class="n">h</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">holddays</span><span class="p">):</span>

        <span class="n">long_lag</span> <span class="o">=</span> <span class="n">longs</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
        <span class="n">long_lag</span><span class="p">[</span><span class="n">long_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
        <span class="n">long_lag</span> <span class="o">=</span> <span class="n">long_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>

        <span class="n">short_lag</span> <span class="o">=</span> <span class="n">shorts</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
        <span class="n">short_lag</span><span class="p">[</span><span class="n">short_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
        <span class="n">short_lag</span> <span class="o">=</span> <span class="n">short_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>

        <span class="n">pos</span><span class="p">[</span><span class="n">long_lag</span><span class="p">]</span> <span class="o">+=</span> <span class="mi">1</span>
        <span class="n">pos</span><span class="p">[</span><span class="n">short_lag</span><span class="p">]</span> <span class="o">-=</span> <span class="mi">1</span>

    <span class="n">pos</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">pos</span><span class="p">)</span>

    <span class="c1"># returns of positions divided by holddays</span>
    <span class="n">ret</span> <span class="o">=</span> <span class="p">(</span><span class="n">pos</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span> <span class="o">*</span> <span class="p">(</span><span class="n">data</span><span class="o">-</span><span class="n">data</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">data</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">holddays</span>
    <span class="n">ret</span><span class="p">[</span><span class="n">ret</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="mi">0</span>

    <span class="c1"># cumulative return</span>
    <span class="n">cumret</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">cumprod</span><span class="p">(</span><span class="n">ret</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">cumret</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">&#39;</span><span class="si">{}</span><span class="s1">/</span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">))</span>
    
    <span class="k">if</span> <span class="n">print_stats</span><span class="p">:</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;#########################################&#39;</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;LOOKBACK = </span><span class="si">{}</span><span class="s1"> / HOLDING = </span><span class="si">{}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">))</span>
        <span class="n">ann_ret</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="mi">252</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Average Annualized Return: &#39;</span><span class="p">,</span> <span class="n">ann_ret</span><span class="p">)</span>

        <span class="n">ann_vol</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">std</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="mi">252</span><span class="p">),</span> <span class="mi">4</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Vol: &#39;</span><span class="p">,</span> <span class="n">ann_vol</span><span class="p">)</span>

        <span class="n">sr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">ann_ret</span> <span class="o">/</span> <span class="n">ann_vol</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Sharpe Ratio: &#39;</span><span class="p">,</span> <span class="n">sr</span><span class="p">)</span>

        <span class="n">apr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">((</span><span class="n">cumret</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">+</span> <span class="mi">1</span><span class="p">)</span> <span class="o">**</span> <span class="p">(</span><span class="mi">252</span><span class="o">/</span><span class="nb">len</span><span class="p">(</span><span class="n">ret</span><span class="p">))</span> <span class="o">-</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Percentage Return: &#39;</span><span class="p">,</span> <span class="n">apr</span><span class="p">)</span>

        <span class="n">max_dd</span><span class="p">,</span> <span class="n">max_dd_days</span> <span class="o">=</span> <span class="n">drawdown</span><span class="p">(</span><span class="n">cumret</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown: </span><span class="si">{}</span><span class="s1">%&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">round</span><span class="p">(</span><span class="n">max_dd</span><span class="o">*</span><span class="mi">100</span><span class="p">,</span><span class="mi">2</span><span class="p">)))</span>
        <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown (Days): &#39;</span><span class="p">,</span> <span class="n">max_dd_days</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We choose the <code>(lookback, holdding)</code> pairs which have high correlation at 95% confidence level.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">look_hold_pairs</span> <span class="o">=</span> <span class="n">corr_results</span><span class="p">[</span><span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;sig_10%&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;sig&#39;</span><span class="p">][[</span><span class="s1">&#39;lookback&#39;</span><span class="p">,</span> <span class="s1">&#39;holddays&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">values</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For each <code>(lookback, holding)</code> pair, we construct the momentum strategy and plot the cumulative returns</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">6</span><span class="p">))</span>
<span class="k">for</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span> <span class="ow">in</span> <span class="n">look_hold_pairs</span><span class="p">:</span>
    <span class="n">momentum</span><span class="p">(</span><span class="n">cl</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">,</span> <span class="n">print_stats</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">bbox_to_anchor</span><span class="o">=</span><span class="p">(</span><span class="mf">1.05</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Comparing Different Momentum Parameters&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Cumulative Return&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Days&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>#########################################
LOOKBACK = 60 / HOLDING = 60
Average Annualized Return:  0.1286
Annualized Vol:  0.1362
Sharpe Ratio:  0.94
Annualized Percentage Return:  0.1267
Maximum Drawdown: -20.16%
Maximum Drawdown (Days):  253
#########################################
LOOKBACK = 25 / HOLDING = 60
Average Annualized Return:  0.11
Annualized Vol:  0.1158
Sharpe Ratio:  0.95
Annualized Percentage Return:  0.1087
Maximum Drawdown: -10.98%
Maximum Drawdown (Days):  315
#########################################
LOOKBACK = 60 / HOLDING = 25
Average Annualized Return:  0.1463
Annualized Vol:  0.151
Sharpe Ratio:  0.97
Annualized Percentage Return:  0.1443
Maximum Drawdown: -15.49%
Maximum Drawdown (Days):  313
#########################################
LOOKBACK = 25 / HOLDING = 120
Average Annualized Return:  0.098
Annualized Vol:  0.0973
Sharpe Ratio:  1.01
Annualized Percentage Return:  0.0977
Maximum Drawdown: -15.57%
Maximum Drawdown (Days):  302
#########################################
LOOKBACK = 60 / HOLDING = 10
Average Annualized Return:  0.1645
Annualized Vol:  0.1561
Sharpe Ratio:  1.05
Annualized Percentage Return:  0.1645
Maximum Drawdown: -16.95%
Maximum Drawdown (Days):  357
#########################################
LOOKBACK = 10 / HOLDING = 60
Average Annualized Return:  0.0658
Annualized Vol:  0.0766
Sharpe Ratio:  0.86
Annualized Percentage Return:  0.0648
Maximum Drawdown: -7.93%
Maximum Drawdown (Days):  332
#########################################
LOOKBACK = 10 / HOLDING = 120
Average Annualized Return:  0.0619
Annualized Vol:  0.0643
Sharpe Ratio:  0.96
Annualized Percentage Return:  0.0616
Maximum Drawdown: -12.16%
Maximum Drawdown (Days):  751
#########################################
LOOKBACK = 10 / HOLDING = 1
Average Annualized Return:  -0.0643
Annualized Vol:  0.171
Sharpe Ratio:  -0.38
Annualized Percentage Return:  -0.076
Maximum Drawdown: -65.3%
Maximum Drawdown (Days):  1751
#########################################
LOOKBACK = 1 / HOLDING = 10
Average Annualized Return:  0.0079
Annualized Vol:  0.0524
Sharpe Ratio:  0.15
Annualized Percentage Return:  0.0065
Maximum Drawdown: -13.65%
Maximum Drawdown (Days):  908
#########################################
LOOKBACK = 5 / HOLDING = 1
Average Annualized Return:  -0.0616
Annualized Vol:  0.1715
Sharpe Ratio:  -0.36
Annualized Percentage Return:  -0.0736
Maximum Drawdown: -60.2%
Maximum Drawdown (Days):  1728
#########################################
LOOKBACK = 10 / HOLDING = 5
Average Annualized Return:  0.0443
Annualized Vol:  0.1355
Sharpe Ratio:  0.33
Annualized Percentage Return:  0.0358
Maximum Drawdown: -27.77%
Maximum Drawdown (Days):  1751
#########################################
LOOKBACK = 1 / HOLDING = 5
Average Annualized Return:  0.0046
Annualized Vol:  0.0736
Sharpe Ratio:  0.06
Annualized Percentage Return:  0.0018
Maximum Drawdown: -17.28%
Maximum Drawdown (Days):  1665
#########################################
LOOKBACK = 1 / HOLDING = 1
Average Annualized Return:  -0.0843
Annualized Vol:  0.1691
Sharpe Ratio:  -0.5
Annualized Percentage Return:  -0.094
Maximum Drawdown: -64.03%
Maximum Drawdown (Days):  1998
</pre>
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
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Treasury-Note Futures</span>
<span class="n">idx</span> <span class="o">=</span> <span class="mi">44</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cl</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;cl.csv&#39;</span><span class="p">,</span> <span class="n">header</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>
<span class="n">cl</span> <span class="o">=</span> <span class="n">cl</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span>
<span class="n">cl</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[14]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(2000,)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Lookback-Holddays-Correlation">Lookback-Holddays Correlation<a class="anchor-link" href="#Lookback-Holddays-Correlation">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">corr_results</span> <span class="o">=</span> <span class="nb">list</span><span class="p">()</span>

<span class="k">for</span> <span class="n">lookback</span> <span class="ow">in</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">60</span><span class="p">,</span> <span class="mi">120</span><span class="p">,</span> <span class="mi">250</span><span class="p">]:</span>
    <span class="k">for</span> <span class="n">holddays</span> <span class="ow">in</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">60</span><span class="p">,</span> <span class="mi">120</span><span class="p">,</span> <span class="mi">250</span><span class="p">]:</span>
        <span class="n">corr</span><span class="p">,</span> <span class="n">pval</span> <span class="o">=</span> <span class="n">return_correlation</span><span class="p">(</span><span class="n">cl</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">)</span>
        <span class="n">corr_results</span><span class="o">.</span><span class="n">append</span><span class="p">([</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">,</span> <span class="nb">round</span><span class="p">(</span><span class="n">corr</span><span class="p">,</span> <span class="mi">2</span><span class="p">),</span> <span class="nb">round</span><span class="p">(</span><span class="n">pval</span><span class="p">,</span> <span class="mi">2</span><span class="p">)])</span>
        
<span class="n">corr_results</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">corr_results</span><span class="p">,</span> 
                            <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;lookback&#39;</span><span class="p">,</span> <span class="s1">&#39;holddays&#39;</span><span class="p">,</span>
                                     <span class="s1">&#39;corr&#39;</span><span class="p">,</span> <span class="s1">&#39;pval&#39;</span><span class="p">])</span>

<span class="n">corr_results</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="s1">&#39;corr&#39;</span><span class="p">,</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">corr_results</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="k">for</span> <span class="n">sig</span> <span class="ow">in</span> <span class="p">[</span><span class="mf">0.05</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">]:</span>
    <span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;sig_&#39;</span><span class="o">+</span><span class="nb">str</span><span class="p">(</span><span class="nb">int</span><span class="p">(</span><span class="n">sig</span><span class="o">*</span><span class="mi">100</span><span class="p">))</span><span class="o">+</span><span class="s1">&#39;%&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;pval&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="s1">&#39;sig&#39;</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&lt;=</span> <span class="n">sig</span> <span class="k">else</span> <span class="s1">&#39;notsig&#39;</span><span class="p">)</span>
<span class="n">corr_results</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">20</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[16]:</div>



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
      <th>lookback</th>
      <th>holddays</th>
      <th>corr</th>
      <th>pval</th>
      <th>sig_5%</th>
      <th>sig_10%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>250</td>
      <td>120</td>
      <td>0.51</td>
      <td>0.06</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>1</th>
      <td>250</td>
      <td>250</td>
      <td>0.48</td>
      <td>0.33</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>2</th>
      <td>250</td>
      <td>60</td>
      <td>0.43</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>3</th>
      <td>120</td>
      <td>250</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>4</th>
      <td>60</td>
      <td>250</td>
      <td>0.31</td>
      <td>0.10</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>5</th>
      <td>250</td>
      <td>25</td>
      <td>0.27</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>6</th>
      <td>60</td>
      <td>25</td>
      <td>0.26</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>7</th>
      <td>25</td>
      <td>250</td>
      <td>0.26</td>
      <td>0.03</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>8</th>
      <td>25</td>
      <td>60</td>
      <td>0.23</td>
      <td>0.04</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>9</th>
      <td>120</td>
      <td>120</td>
      <td>0.22</td>
      <td>0.44</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>10</th>
      <td>60</td>
      <td>60</td>
      <td>0.22</td>
      <td>0.23</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>11</th>
      <td>25</td>
      <td>25</td>
      <td>0.19</td>
      <td>0.09</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>12</th>
      <td>250</td>
      <td>10</td>
      <td>0.18</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>13</th>
      <td>60</td>
      <td>10</td>
      <td>0.17</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>14</th>
      <td>10</td>
      <td>60</td>
      <td>0.17</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>15</th>
      <td>10</td>
      <td>250</td>
      <td>0.17</td>
      <td>0.03</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>16</th>
      <td>120</td>
      <td>25</td>
      <td>0.15</td>
      <td>0.21</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>17</th>
      <td>25</td>
      <td>120</td>
      <td>0.15</td>
      <td>0.21</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>18</th>
      <td>25</td>
      <td>10</td>
      <td>0.12</td>
      <td>0.09</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>19</th>
      <td>250</td>
      <td>5</td>
      <td>0.11</td>
      <td>0.04</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Example:-Momentum-Strategy">Example: Momentum Strategy<a class="anchor-link" href="#Example:-Momentum-Strategy">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We run an example of a long-short momentum strategy that goes long if the return over the lookback period is positive, and goes short if the return over the lookback period is negative. Each entry into position is held of a total of <code>holddays</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lookback</span> <span class="o">=</span> <span class="mi">250</span>
<span class="n">holddays</span> <span class="o">=</span> <span class="mi">20</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[18]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">longs</span> <span class="o">=</span> <span class="n">cl</span> <span class="o">&gt;</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>
<span class="n">shorts</span> <span class="o">=</span> <span class="n">cl</span> <span class="o">&lt;</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>

<span class="n">pos</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros_like</span><span class="p">(</span><span class="n">cl</span><span class="p">)</span>

<span class="c1"># calculate holdings for holddays</span>

<span class="k">for</span> <span class="n">h</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">holddays</span><span class="p">):</span>
    
    <span class="n">long_lag</span> <span class="o">=</span> <span class="n">longs</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
    <span class="n">long_lag</span><span class="p">[</span><span class="n">long_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
    <span class="n">long_lag</span> <span class="o">=</span> <span class="n">long_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>
    
    <span class="n">short_lag</span> <span class="o">=</span> <span class="n">shorts</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
    <span class="n">short_lag</span><span class="p">[</span><span class="n">short_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
    <span class="n">short_lag</span> <span class="o">=</span> <span class="n">short_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>
    
    <span class="n">pos</span><span class="p">[</span><span class="n">long_lag</span><span class="p">]</span> <span class="o">+=</span> <span class="mi">1</span>
    <span class="n">pos</span><span class="p">[</span><span class="n">short_lag</span><span class="p">]</span> <span class="o">-=</span> <span class="mi">1</span>
    
<span class="n">pos</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">pos</span><span class="p">)</span>

<span class="c1"># returns of positions divided by holddays</span>
<span class="n">ret</span> <span class="o">=</span> <span class="p">(</span><span class="n">pos</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span> <span class="o">*</span> <span class="p">(</span><span class="n">cl</span><span class="o">-</span><span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">holddays</span>
<span class="n">ret</span><span class="p">[</span><span class="n">ret</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="mi">0</span>

<span class="c1"># cumulative return</span>
<span class="n">cumret</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">cumprod</span><span class="p">(</span><span class="n">ret</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">cumret</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Momentum Strategy</span><span class="se">\n</span><span class="si">{}</span><span class="s1"> lookback / </span><span class="si">{}</span><span class="s1"> holddays&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Cumulative Return&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Days&#39;</span><span class="p">)</span>
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
<div class="prompt input_prompt">In&nbsp;[20]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ann_ret</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="mi">252</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Average Annualized Return: &#39;</span><span class="p">,</span> <span class="n">ann_ret</span><span class="p">)</span>

<span class="n">ann_vol</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">std</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="mi">252</span><span class="p">),</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Vol: &#39;</span><span class="p">,</span> <span class="n">ann_vol</span><span class="p">)</span>

<span class="n">sr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">ann_ret</span> <span class="o">/</span> <span class="n">ann_vol</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Sharpe Ratio: &#39;</span><span class="p">,</span> <span class="n">sr</span><span class="p">)</span>

<span class="n">apr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">((</span><span class="n">cumret</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">+</span> <span class="mi">1</span><span class="p">)</span> <span class="o">**</span> <span class="p">(</span><span class="mi">252</span><span class="o">/</span><span class="nb">len</span><span class="p">(</span><span class="n">ret</span><span class="p">))</span> <span class="o">-</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Percentage Return: &#39;</span><span class="p">,</span> <span class="n">apr</span><span class="p">)</span>

<span class="n">max_dd</span><span class="p">,</span> <span class="n">max_dd_days</span> <span class="o">=</span> <span class="n">drawdown</span><span class="p">(</span><span class="n">cumret</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown: </span><span class="si">{}</span><span class="s1">%&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">round</span><span class="p">(</span><span class="n">max_dd</span><span class="o">*</span><span class="mi">100</span><span class="p">,</span><span class="mi">2</span><span class="p">)))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown (Days): &#39;</span><span class="p">,</span> <span class="n">max_dd_days</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Average Annualized Return:  0.0171
Annualized Vol:  0.0161
Sharpe Ratio:  1.06
Annualized Percentage Return:  0.0171
Maximum Drawdown: -2.49%
Maximum Drawdown (Days):  342
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Generalize-Momentum-Strategy-Function">Generalize Momentum Strategy Function<a class="anchor-link" href="#Generalize-Momentum-Strategy-Function">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In the previous section, the holding and lookback periods were given due to the benefit of hindsight. In this following section, we explore the importance of choosing the right lookback and holdings periods.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We choose the <code>(lookback, holdding)</code> pairs which have high correlation at 95% confidence level.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[22]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">look_hold_pairs</span> <span class="o">=</span> <span class="n">corr_results</span><span class="p">[</span><span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;sig_10%&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;sig&#39;</span><span class="p">][[</span><span class="s1">&#39;lookback&#39;</span><span class="p">,</span> <span class="s1">&#39;holddays&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">values</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For each <code>(lookback, holding)</code> pair, we construct the momentum strategy and plot the cumulative returns</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[23]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">6</span><span class="p">))</span>
<span class="k">for</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span> <span class="ow">in</span> <span class="n">look_hold_pairs</span><span class="p">:</span>
    <span class="n">momentum</span><span class="p">(</span><span class="n">cl</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">,</span> <span class="n">print_stats</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">bbox_to_anchor</span><span class="o">=</span><span class="p">(</span><span class="mf">1.05</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Comparing Different Momentum Parameters&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Cumulative Return&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Days&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>#########################################
LOOKBACK = 250 / HOLDING = 120
Average Annualized Return:  0.0155
Annualized Vol:  0.0152
Sharpe Ratio:  1.02
Annualized Percentage Return:  0.0155
Maximum Drawdown: -2.49%
Maximum Drawdown (Days):  353
#########################################
LOOKBACK = 250 / HOLDING = 60
Average Annualized Return:  0.0168
Annualized Vol:  0.0157
Sharpe Ratio:  1.07
Annualized Percentage Return:  0.0168
Maximum Drawdown: -2.49%
Maximum Drawdown (Days):  347
#########################################
LOOKBACK = 60 / HOLDING = 250
Average Annualized Return:  0.0081
Annualized Vol:  0.0085
Sharpe Ratio:  0.95
Annualized Percentage Return:  0.0081
Maximum Drawdown: -1.36%
Maximum Drawdown (Days):  391
#########################################
LOOKBACK = 250 / HOLDING = 25
Average Annualized Return:  0.0167
Annualized Vol:  0.016
Sharpe Ratio:  1.04
Annualized Percentage Return:  0.0167
Maximum Drawdown: -2.49%
Maximum Drawdown (Days):  343
#########################################
LOOKBACK = 60 / HOLDING = 25
Average Annualized Return:  0.0098
Annualized Vol:  0.0156
Sharpe Ratio:  0.63
Annualized Percentage Return:  0.0097
Maximum Drawdown: -2.37%
Maximum Drawdown (Days):  674
#########################################
LOOKBACK = 25 / HOLDING = 250
Average Annualized Return:  0.0057
Annualized Vol:  0.0069
Sharpe Ratio:  0.83
Annualized Percentage Return:  0.0057
Maximum Drawdown: -1.13%
Maximum Drawdown (Days):  391
#########################################
LOOKBACK = 25 / HOLDING = 60
Average Annualized Return:  0.0074
Annualized Vol:  0.0119
Sharpe Ratio:  0.62
Annualized Percentage Return:  0.0074
Maximum Drawdown: -1.93%
Maximum Drawdown (Days):  668
#########################################
LOOKBACK = 25 / HOLDING = 25
Average Annualized Return:  0.0087
Annualized Vol:  0.0141
Sharpe Ratio:  0.62
Annualized Percentage Return:  0.0086
Maximum Drawdown: -2.17%
Maximum Drawdown (Days):  666
#########################################
LOOKBACK = 250 / HOLDING = 10
Average Annualized Return:  0.0173
Annualized Vol:  0.0161
Sharpe Ratio:  1.07
Annualized Percentage Return:  0.0173
Maximum Drawdown: -2.49%
Maximum Drawdown (Days):  343
#########################################
LOOKBACK = 60 / HOLDING = 10
Average Annualized Return:  0.0107
Annualized Vol:  0.0162
Sharpe Ratio:  0.66
Annualized Percentage Return:  0.0107
Maximum Drawdown: -2.05%
Maximum Drawdown (Days):  383
#########################################
LOOKBACK = 10 / HOLDING = 60
Average Annualized Return:  0.0057
Annualized Vol:  0.0083
Sharpe Ratio:  0.69
Annualized Percentage Return:  0.0057
Maximum Drawdown: -1.09%
Maximum Drawdown (Days):  664
#########################################
LOOKBACK = 10 / HOLDING = 250
Average Annualized Return:  0.0044
Annualized Vol:  0.0049
Sharpe Ratio:  0.9
Annualized Percentage Return:  0.0044
Maximum Drawdown: -0.82%
Maximum Drawdown (Days):  389
#########################################
LOOKBACK = 25 / HOLDING = 10
Average Annualized Return:  0.0074
Annualized Vol:  0.0154
Sharpe Ratio:  0.48
Annualized Percentage Return:  0.0073
Maximum Drawdown: -2.98%
Maximum Drawdown (Days):  837
#########################################
LOOKBACK = 250 / HOLDING = 5
Average Annualized Return:  0.0172
Annualized Vol:  0.0162
Sharpe Ratio:  1.06
Annualized Percentage Return:  0.0173
Maximum Drawdown: -2.49%
Maximum Drawdown (Days):  343
#########################################
LOOKBACK = 5 / HOLDING = 250
Average Annualized Return:  0.0029
Annualized Vol:  0.0036
Sharpe Ratio:  0.81
Annualized Percentage Return:  0.0029
Maximum Drawdown: -0.63%
Maximum Drawdown (Days):  557
#########################################
LOOKBACK = 250 / HOLDING = 1
Average Annualized Return:  0.0159
Annualized Vol:  0.0164
Sharpe Ratio:  0.97
Annualized Percentage Return:  0.0159
Maximum Drawdown: -2.91%
Maximum Drawdown (Days):  378
#########################################
LOOKBACK = 1 / HOLDING = 1
Average Annualized Return:  0.0009
Annualized Vol:  0.0172
Sharpe Ratio:  0.05
Annualized Percentage Return:  0.0007
Maximum Drawdown: -6.19%
Maximum Drawdown (Days):  994
#########################################
LOOKBACK = 5 / HOLDING = 1
Average Annualized Return:  -0.0102
Annualized Vol:  0.0169
Sharpe Ratio:  -0.6
Annualized Percentage Return:  -0.0103
Maximum Drawdown: -8.9%
Maximum Drawdown (Days):  1991
#########################################
LOOKBACK = 1 / HOLDING = 5
Average Annualized Return:  -0.0026
Annualized Vol:  0.0075
Sharpe Ratio:  -0.35
Annualized Percentage Return:  -0.0026
Maximum Drawdown: -3.57%
Maximum Drawdown (Days):  1935
#########################################
LOOKBACK = 5 / HOLDING = 5
Average Annualized Return:  -0.0006
Annualized Vol:  0.0122
Sharpe Ratio:  -0.05
Annualized Percentage Return:  -0.0007
Maximum Drawdown: -4.16%
Maximum Drawdown (Days):  1087
</pre>
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
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[24]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Copper Futures</span>
<span class="n">idx</span> <span class="o">=</span> <span class="mi">15</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[25]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cl</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;cl.csv&#39;</span><span class="p">,</span> <span class="n">header</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>
<span class="n">cl</span> <span class="o">=</span> <span class="n">cl</span><span class="p">[</span><span class="n">idx</span><span class="p">]</span>
<span class="n">cl</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[25]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(2000,)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Lookback-Holddays-Correlation">Lookback-Holddays Correlation<a class="anchor-link" href="#Lookback-Holddays-Correlation">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">corr_results</span> <span class="o">=</span> <span class="nb">list</span><span class="p">()</span>

<span class="k">for</span> <span class="n">lookback</span> <span class="ow">in</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">60</span><span class="p">,</span> <span class="mi">120</span><span class="p">,</span> <span class="mi">250</span><span class="p">]:</span>
    <span class="k">for</span> <span class="n">holddays</span> <span class="ow">in</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">60</span><span class="p">,</span> <span class="mi">120</span><span class="p">,</span> <span class="mi">250</span><span class="p">]:</span>
        <span class="n">corr</span><span class="p">,</span> <span class="n">pval</span> <span class="o">=</span> <span class="n">return_correlation</span><span class="p">(</span><span class="n">cl</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">)</span>
        <span class="n">corr_results</span><span class="o">.</span><span class="n">append</span><span class="p">([</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">,</span> <span class="nb">round</span><span class="p">(</span><span class="n">corr</span><span class="p">,</span> <span class="mi">2</span><span class="p">),</span> <span class="nb">round</span><span class="p">(</span><span class="n">pval</span><span class="p">,</span> <span class="mi">2</span><span class="p">)])</span>
        
<span class="n">corr_results</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">corr_results</span><span class="p">,</span> 
                            <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;lookback&#39;</span><span class="p">,</span> <span class="s1">&#39;holddays&#39;</span><span class="p">,</span>
                                     <span class="s1">&#39;corr&#39;</span><span class="p">,</span> <span class="s1">&#39;pval&#39;</span><span class="p">])</span>

<span class="n">corr_results</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="s1">&#39;corr&#39;</span><span class="p">,</span> <span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">corr_results</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="k">for</span> <span class="n">sig</span> <span class="ow">in</span> <span class="p">[</span><span class="mf">0.05</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">]:</span>
    <span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;sig_&#39;</span><span class="o">+</span><span class="nb">str</span><span class="p">(</span><span class="nb">int</span><span class="p">(</span><span class="n">sig</span><span class="o">*</span><span class="mi">100</span><span class="p">))</span><span class="o">+</span><span class="s1">&#39;%&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;pval&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="s1">&#39;sig&#39;</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&lt;=</span> <span class="n">sig</span> <span class="k">else</span> <span class="s1">&#39;notsig&#39;</span><span class="p">)</span>
<span class="n">corr_results</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">20</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[27]:</div>



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
      <th>lookback</th>
      <th>holddays</th>
      <th>corr</th>
      <th>pval</th>
      <th>sig_5%</th>
      <th>sig_10%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>25</td>
      <td>25</td>
      <td>0.18</td>
      <td>0.12</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>10</td>
      <td>0.16</td>
      <td>0.02</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>2</th>
      <td>60</td>
      <td>10</td>
      <td>0.15</td>
      <td>0.03</td>
      <td>sig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>3</th>
      <td>60</td>
      <td>25</td>
      <td>0.14</td>
      <td>0.22</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>4</th>
      <td>25</td>
      <td>60</td>
      <td>0.14</td>
      <td>0.22</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>5</th>
      <td>10</td>
      <td>60</td>
      <td>0.14</td>
      <td>0.06</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>6</th>
      <td>10</td>
      <td>25</td>
      <td>0.11</td>
      <td>0.13</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>7</th>
      <td>60</td>
      <td>5</td>
      <td>0.10</td>
      <td>0.06</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>8</th>
      <td>25</td>
      <td>10</td>
      <td>0.10</td>
      <td>0.15</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>120</td>
      <td>0.10</td>
      <td>0.19</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>10</th>
      <td>120</td>
      <td>10</td>
      <td>0.08</td>
      <td>0.25</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>11</th>
      <td>25</td>
      <td>120</td>
      <td>0.08</td>
      <td>0.48</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>12</th>
      <td>5</td>
      <td>60</td>
      <td>0.08</td>
      <td>0.10</td>
      <td>notsig</td>
      <td>sig</td>
    </tr>
    <tr>
      <th>13</th>
      <td>25</td>
      <td>5</td>
      <td>0.07</td>
      <td>0.17</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>14</th>
      <td>5</td>
      <td>25</td>
      <td>0.07</td>
      <td>0.17</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>15</th>
      <td>10</td>
      <td>5</td>
      <td>0.06</td>
      <td>0.23</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>16</th>
      <td>5</td>
      <td>120</td>
      <td>0.06</td>
      <td>0.24</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>17</th>
      <td>5</td>
      <td>10</td>
      <td>0.06</td>
      <td>0.21</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>18</th>
      <td>120</td>
      <td>25</td>
      <td>0.06</td>
      <td>0.60</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
    <tr>
      <th>19</th>
      <td>120</td>
      <td>5</td>
      <td>0.05</td>
      <td>0.32</td>
      <td>notsig</td>
      <td>notsig</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Example:-Momentum-Strategy">Example: Momentum Strategy<a class="anchor-link" href="#Example:-Momentum-Strategy">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[28]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lookback</span> <span class="o">=</span> <span class="mi">40</span>
<span class="n">holddays</span> <span class="o">=</span> <span class="mi">40</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[29]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">longs</span> <span class="o">=</span> <span class="n">cl</span> <span class="o">&gt;</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>
<span class="n">shorts</span> <span class="o">=</span> <span class="n">cl</span> <span class="o">&lt;</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">lookback</span><span class="p">)</span>

<span class="n">pos</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros_like</span><span class="p">(</span><span class="n">cl</span><span class="p">)</span>

<span class="c1"># calculate holdings for holddays</span>

<span class="k">for</span> <span class="n">h</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">holddays</span><span class="p">):</span>
    
    <span class="n">long_lag</span> <span class="o">=</span> <span class="n">longs</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
    <span class="n">long_lag</span><span class="p">[</span><span class="n">long_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
    <span class="n">long_lag</span> <span class="o">=</span> <span class="n">long_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>
    
    <span class="n">short_lag</span> <span class="o">=</span> <span class="n">shorts</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="n">h</span><span class="p">)</span>
    <span class="n">short_lag</span><span class="p">[</span><span class="n">short_lag</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="kc">False</span>
    <span class="n">short_lag</span> <span class="o">=</span> <span class="n">short_lag</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">bool</span><span class="p">)</span>
    
    <span class="n">pos</span><span class="p">[</span><span class="n">long_lag</span><span class="p">]</span> <span class="o">+=</span> <span class="mi">1</span>
    <span class="n">pos</span><span class="p">[</span><span class="n">short_lag</span><span class="p">]</span> <span class="o">-=</span> <span class="mi">1</span>
    
<span class="n">pos</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">pos</span><span class="p">)</span>

<span class="c1"># returns of positions divided by holddays</span>
<span class="n">ret</span> <span class="o">=</span> <span class="p">(</span><span class="n">pos</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span> <span class="o">*</span> <span class="p">(</span><span class="n">cl</span><span class="o">-</span><span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">cl</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span> <span class="o">/</span> <span class="n">holddays</span>
<span class="n">ret</span><span class="p">[</span><span class="n">ret</span><span class="o">.</span><span class="n">isna</span><span class="p">()]</span> <span class="o">=</span> <span class="mi">0</span>

<span class="c1"># cumulative return</span>
<span class="n">cumret</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">cumprod</span><span class="p">(</span><span class="n">ret</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span> <span class="o">-</span> <span class="mi">1</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">cumret</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Momentum Strategy</span><span class="se">\n</span><span class="si">{}</span><span class="s1"> lookback / </span><span class="si">{}</span><span class="s1"> holddays&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Cumulative Return&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Days&#39;</span><span class="p">)</span>
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
<div class="prompt input_prompt">In&nbsp;[31]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ann_ret</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">mean</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="mi">252</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Average Annualized Return: &#39;</span><span class="p">,</span> <span class="n">ann_ret</span><span class="p">)</span>

<span class="n">ann_vol</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">std</span><span class="p">(</span><span class="n">ret</span><span class="p">)</span> <span class="o">*</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="mi">252</span><span class="p">),</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Vol: &#39;</span><span class="p">,</span> <span class="n">ann_vol</span><span class="p">)</span>

<span class="n">sr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">ann_ret</span> <span class="o">/</span> <span class="n">ann_vol</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Sharpe Ratio: &#39;</span><span class="p">,</span> <span class="n">sr</span><span class="p">)</span>

<span class="n">apr</span> <span class="o">=</span> <span class="nb">round</span><span class="p">((</span><span class="n">cumret</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span> <span class="o">+</span> <span class="mi">1</span><span class="p">)</span> <span class="o">**</span> <span class="p">(</span><span class="mi">252</span><span class="o">/</span><span class="nb">len</span><span class="p">(</span><span class="n">ret</span><span class="p">))</span> <span class="o">-</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Annualized Percentage Return: &#39;</span><span class="p">,</span> <span class="n">apr</span><span class="p">)</span>

<span class="n">max_dd</span><span class="p">,</span> <span class="n">max_dd_days</span> <span class="o">=</span> <span class="n">drawdown</span><span class="p">(</span><span class="n">cumret</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown: </span><span class="si">{}</span><span class="s1">%&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="nb">round</span><span class="p">(</span><span class="n">max_dd</span><span class="o">*</span><span class="mi">100</span><span class="p">,</span><span class="mi">2</span><span class="p">)))</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Maximum Drawdown (Days): &#39;</span><span class="p">,</span> <span class="n">max_dd_days</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Average Annualized Return:  0.1777
Annualized Vol:  0.1696
Sharpe Ratio:  1.05
Annualized Percentage Return:  0.1774
Maximum Drawdown: -23.98%
Maximum Drawdown (Days):  424
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Generalize-Momentum-Strategy-Function">Generalize Momentum Strategy Function<a class="anchor-link" href="#Generalize-Momentum-Strategy-Function">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We choose the <code>(lookback, holdding)</code> pairs which have high correlation at 95% confidence level.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[33]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">look_hold_pairs</span> <span class="o">=</span> <span class="n">corr_results</span><span class="p">[</span><span class="n">corr_results</span><span class="p">[</span><span class="s1">&#39;sig_10%&#39;</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;sig&#39;</span><span class="p">][[</span><span class="s1">&#39;lookback&#39;</span><span class="p">,</span> <span class="s1">&#39;holddays&#39;</span><span class="p">]]</span><span class="o">.</span><span class="n">values</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For each <code>(lookback, holding)</code> pair, we construct the momentum strategy and plot the cumulative returns</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[34]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span><span class="mi">6</span><span class="p">))</span>
<span class="k">for</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span> <span class="ow">in</span> <span class="n">look_hold_pairs</span><span class="p">:</span>
    <span class="n">momentum</span><span class="p">(</span><span class="n">cl</span><span class="p">,</span> <span class="n">lookback</span><span class="p">,</span> <span class="n">holddays</span><span class="p">,</span> <span class="n">print_stats</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">bbox_to_anchor</span><span class="o">=</span><span class="p">(</span><span class="mf">1.05</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Comparing Different Momentum Parameters&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Cumulative Return&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Days&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>#########################################
LOOKBACK = 10 / HOLDING = 10
Average Annualized Return:  0.1008
Annualized Vol:  0.157
Sharpe Ratio:  0.64
Annualized Percentage Return:  0.0925
Maximum Drawdown: -16.7%
Maximum Drawdown (Days):  851
#########################################
LOOKBACK = 60 / HOLDING = 10
Average Annualized Return:  0.2002
Annualized Vol:  0.1942
Sharpe Ratio:  1.03
Annualized Percentage Return:  0.1988
Maximum Drawdown: -22.89%
Maximum Drawdown (Days):  592
#########################################
LOOKBACK = 10 / HOLDING = 60
Average Annualized Return:  0.0711
Annualized Vol:  0.0885
Sharpe Ratio:  0.8
Annualized Percentage Return:  0.0694
Maximum Drawdown: -11.2%
Maximum Drawdown (Days):  420
#########################################
LOOKBACK = 60 / HOLDING = 5
Average Annualized Return:  0.1993
Annualized Vol:  0.1972
Sharpe Ratio:  1.01
Annualized Percentage Return:  0.197
Maximum Drawdown: -25.02%
Maximum Drawdown (Days):  592
#########################################
LOOKBACK = 5 / HOLDING = 60
Average Annualized Return:  0.0541
Annualized Vol:  0.07
Sharpe Ratio:  0.77
Annualized Percentage Return:  0.053
Maximum Drawdown: -10.97%
Maximum Drawdown (Days):  360
#########################################
LOOKBACK = 60 / HOLDING = 1
Average Annualized Return:  0.2165
Annualized Vol:  0.2076
Sharpe Ratio:  1.04
Annualized Percentage Return:  0.2152
Maximum Drawdown: -21.45%
Maximum Drawdown (Days):  407
#########################################
LOOKBACK = 1 / HOLDING = 1
Average Annualized Return:  -0.1203
Annualized Vol:  0.2095
Sharpe Ratio:  -0.57
Annualized Percentage Return:  -0.1327
Maximum Drawdown: -72.73%
Maximum Drawdown (Days):  1903
</pre>
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
    </div>
  </div>
</body>

 


</html>
