---
title: "Effect of Crisis on Roll Spreads & Volatilities"
excerpt: "Intra-Day Spreads & Volatilities"
collection: portfolio
---

<html>
<head><meta charset="utf-8" />

<title>Code</title>

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
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABDAAAAQwCAYAAAATlK4WAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjEsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy8QZhcZAAAgAElEQVR4nOzdd7xlVX3//9eb3ocZQJQ6o0IUUNHYFTVq7H5taFBEjRpbjJoYTSQaDbZoiolR7BXFEisqWBK7YkGNBRV+SBtAFGTmMjMgMPD5/bHWcfYczr1zmc7c1/PxOI97z15lr73voezP+ay1UlVIkiRJkiRtzrba1AOQJEmSJElaEwMYkiRJkiRps2cAQ5IkSZIkbfYMYEiSJEmSpM2eAQxJkiRJkrTZM4AhSZIkSZI2ewYwJEnSJpXkvUletanHcUMkOTrJFzf1OCRJmksMYEiSNAckuWeSbyeZSnJZkm8ludOmHtfmKsnpSZb317VJfj94f2xVfbCqHrCpxylJ0lyyzaYegCRJ2rCS7AZ8Fng28FFgO+AI4Kq16CtAquq69TrITSzJ1lV17eh9VR06KPsq8IGqeuemGJskSWrMwJAkact3MEBVfaiqrq2qK6vqi1X1E4AkT+kZGW/qGRq/THK/UeMkX03y6iTfAq4Abp5kXpJ3Jfl1kguTvCrJ1r3+LZJ8Ocnvklya5INJdh/0d/skP0yyLMlHgB2mG3iSrZK8NMl5SX6b5P1J5vWyU5I8d6z+j5M8uv9+qyRf6hknZyR53KDee5O8JcnJSVYAf3JDbmi/Z98cvK8kz0ny//XremW/D99OcnmSjybZblD/YUn+L8nSXue2N+T8kiTNRQYwJEna8p0JXJvkfUkenGT+hDp3AX4F7Am8HPhEkgWD8mOAZwC7AucB7wVWArcEbg88AHh6rxvgtcA+wK2B/YFXAPSH+E8BJwALgP8GHjPD2J/SX38C3BzYBXhTL/sQ8PhRxSSHAAcCn0uyM/Al4ETgJsBRwPG9zsgTgFf3a/om6+6BwB8DdwVeDLwdeCLt+g8bjTXJ7YF3A88E9gDeBpyUZPv1MAZJkrZYBjAkSdrCVdXlwD2BAt4BXJLkpCR7D6r9FviPqrqmqj4CnAE8dFD+3qo6vapW0gIPDwFeUFUrquq3wBtoQQKq6qyq+lJVXVVVlwD/Dty793NXYNvBuT4GfH+G4R8N/HtVnV1Vy4GXAEcl2Qb4JHB4kgMHdT9RVVcBDwPOrar3VNXKqvoR8HHgsYO+P11V36qq66rq97O8nTN5fVVdXlWnAz8DvtjHPQWcQgv0QAsEva2qvtszYt5Hm85z1/UwBkmStlgGMCRJmgOq6hdV9ZSq2o+WDbAP8B+DKhdWVQ3en9frjCwe/H4gLQjx6z4FYikti+AmAEn2TvLhPrXkcuADtMwOep+TzjWdfcbKz6Ot4bV3VS0DPkcPnNAyHD44GONdRuPrYzwauOk017Q+/Gbw+5UT3u8yGNsLx8a2P6vfb0mSNMYAhiRJc0xV/ZI2BeSwweF9+wKdIwcAFw2bDX5fTMsY2LOqdu+v3QYLX76m179NVe1Gm0Yx6vvX05xrOhfRHviHdVeyKjjwIeDxSe5GW0vjK4Mxfm0wvt2rapeqevY017QxLQZePTa2narqQ5toPJIk3SgYwJAkaQvXF7N8YZL9+vv9adkK3xlUuwnwvCTbJnksbe2Kkyf1V1W/Br4I/FuS3fpCm7dIMpomsiuwHJhKsi/wokHzU2kBiNG5Hg3ceYbhfwj46ySLkuxCC458pE9loY/xQOC4fny0O8pngYOTHNPPs22SOyW59Zru10bwDuBZSe6SZuckD02y66YemCRJmzMDGJIkbfmW0Rbp/G7fceM7tDUaXjio813gIOBS2sKWR1bV72bo80m07Vh/DiwBPgbcrJf9E3AHYIo2xeMTo0ZVdTXwaNrCnJcBfzYsn+DdtAU/vw6cA/we+KtBf1f19venLdg5Or6MtrDoUbQsjouB1wGbfKHMqjoN+AvaYqRLgLNo90OSJM0gq09BlSRJc02SpwBPr6p7buqxSJIkTccMDEmSJEmStNkzgCFJkiRJkjZ7TiGRJEmSJEmbPTMwJEmSJEnSZs8AhiRJQJKvJnn6ph6HJEmSJjOAIUnaoiQ5N8mVSZYPXvtsoHMtSnJdkrdsiP43B0kOT/KDJFf0n4fPUHdBkk8mWZHkvCRPGCt/Qj++IsmnkiyYbdtBvXcnqSS3HBz7QJJfJ7k8yZnDQFSShb3+8PPwsrE+75/kh/3cFyR53KCs+vFR23cOyv4kyVeSTCU5d8JYX5nkp0lWJnnFWNlDk3wzydIkFyd5Z5JdB+XvTXL12Li37mVHjx2/oo/zj3v5KWPlVyf5aS87YKxseW/7wsG590pyYr+uJUk+OCg7faztyiSf6WVHTNP3Y3r5U5JcO1Z+n7H78vwk5/R7/oskB0/6HEiS5iYDGJKkLdHDq2qXweuiDXSeJwFLgD9Lsv2GOEGSbTZEv7M893bAp4EPAPOB9wGf7scneTNwNbA3cDTwliSH9r4OBd4GHNPLrwCOn03bwXjuCdxiwnlfCyysqt2A/we8avQwP7D74PPwykGfhwAnAv8AzANuB/xgrO3tBm2HWTorgHcDL5rmfpwFvBj43ISyecCrgH2AWwP7Av8yVuf1Y5/jawGq6oPD48BzgLOBH/byB4+Vfxv47152/ljZbYDrgI8PzvsJ4GLgAOAmwL+OCqrq0EHbXYHFg76/Mdb3w4DlwOcHfZ86dk1fHRX0wNPTgIcCo/aXTnNvJUlzkAEMSdKckeSuSb7dv/X+8fi3v8Atknyvf5P/6WGGwIS+QgtgvBS4Bnj4oOwtSf51rP6nk/xN/32fJB9Pckn/tvl5g3qvSPKxnlVwOfCUJHdOcmof96+TvGkYREjygCRn9G/Mj0/ytayehfDU/m32kiRfSHLgLG/ZfYBtgP+oqquq6o1AgPtOuB87A48BXlZVy6vqm8BJtIAFtKDEZ6rq61W1HHgZ8Ogku86i7SiQ81/AX42fu6pOr6qrRm/7a1KgY5KXAm+rqlOqamVV/a6qfjWbhlX1vao6gRY8mFT+vqo6BVg2oezEqvp8VV1RVUuAdwD3mOWYxz0ZeH9NWJk9yULgCOD907R9EvD1qjq3138AsD/woqqaqqprqupH07S9F7Anqwc/xsf1sapasaYLSLIV8HLgr6vq59X8qqouW1NbSdLcYQBDkjQnJNmX9k34q4AFwN8CH0+y16Dak4CnAjcDVgJvnKHLewL7AR8GPkp7WBv5EC0rI/3c84EHAB/uD2qfAX5M+9b9fsALkjxw0P4RwMeA3YEPAtcCf017WLxbb/Oc3veeve5LgD2AM4C7D677EcCxwKOBvYBv9PGNyj+b5O+nucZDgZ+MPRj/pB8fdzCwsqrOHBz78aDuof09AD1IcHVvt6a29Ov/elX9ZNJAe+DmCuCXwK+Bk8eqnJc2PeQ9/Z6N3LW3/2kPDn1gQuDq62nTPD7RAwIbwr2A08eOPSfJZWlTdx4zqVEPRt2LmQMU3xgFKMbajoJw7xscvivtM/S+JL9L8v0k956m7ycDH58UoOhBqSPH+ga4fZJL06b6vGyQYbRffx2WZHEP7P1T/+dFkiTAAIYkacv0qZ6tsDTJp/qxJwInV9XJVXVdVX0JOA14yKDdCVX1s/5A9jLgcenrDkzwZOCU/u35icCDktykl32DlgVwRH9/JC11/iLgTsBeVXVcVV1dVWfTvn0/atD3qVX1qT7OK6vqB1X1nZ4hcC5tKsboofIhwOlV9YmqGgVdLh709SzgtVX1i17+GuDwURZGVT2sqv55mmvcBZgaOzZFmzowqe7lM9Sdqa8Z2ybZH3gm8I/TjJOqek6vfwRtCsQoI+NS2j0/EPjjXueDg6b70TI9HgMcBOxIy/QYuTewELgVcBHw2fU9rSfJn9I+T8Pre2Mfz01on8X3JpmUoTEKUJwzTfdPAt47Tdk9aVN2PjY4th8t2PYV4KbAv9GmDQ2DPiTZifa5nq7vR9Pu/dcGx74OHNav6THA41k1/Wa//vMBtGktf9LLnzZN/5KkOcgAhiRpS/TIqtq9vx7Zjx0IPHYQ2FhKe4C72aDd4sHv5wHb0rIeVpNkR+Cx9AfhqjoVOB94Qn9ftMyMx/cmT2DVQ/OBwD5j4ziW9iA5aRwkObhnSlzcp5W8ZjCufYb1+7kvGDQ/EPjPwbkuo00D2fd6d+36lgO7jR3bjQlTImZRd6byNbX9D+C4qhoPgKymqq7t00/2A57djy2vqtN68Oc3wHOBB2TVgplXAu+pqjP71JbXMAhq9SkvV1fVUuD5wCLamhXrRZK70gJgRw4zUKrqh306y8qqOpn2+Xn0hC7GMyiGfd+TFoT42KRyVmVQLB8cuxI4t6re1aePfJj2+RoPnjya9ln6GpNdb1pLVZ1dVef0wNxPgeNoQZDReaGt+7F0EKgbBhglSXOcAQxJ0lyxmJZhsfvgtfNY9sH+g98PoK1tMWkRwUfRHrCP70GFi2kBgfFpJEf2TIe7sGqdgMXAOWPj2LWqhg9q42sZvIU2NeKgagtVHksLQkCbLjH69no0LWC/QdvFwDPHzrdjVX174l1a3enAbUdTYbrbcv2pDgBnAtskOWhw7HaDuqf396Nx3hzYvrdbU9v7Af8yuNcAp2aanUpo63ZMtwbG6N6O/h/oJ6x+v6+3jsSE9llDnVlJcnvaWh9Prar/vaHn7RkZ+zBzgOITYwGKUdtREG48+DF+P5jwftT3dOtu7E9bP2W6aS3DfkfXdAZtStEN+VtIkuYYAxiSpLniA8DDkzwwydZJdkhynyTDh/0nJjmkp8cfR1uA8NoJfT2ZtvvEbYDD++sewO2S3AagL3x4KfBO4Av9G3yA7wHLkvxdkh37WA5LcqcZxr4rbYrF8iS3omcXdJ8DbpPkkX1qw1/SvnUfeSvwkqzaDWRekseu6WZ1X6Wtv/G8JNsneW4//uXxin3azSeA45Ls3B+uHwGc0Kt8kHb/j+jrIxxHe7heNou2B9MCGqN7DW3R1E8muUmSo5Ls0u/lA2mZL//br/cuSf4oyVZJ9qBNzfjqIJvjPcCfJ7l5/7v/PfDZ3vbQtG1kt06yC206xYXAL3r5Vkl2oGXqpH+mhourbtvLt6IFaHbIqq1QD6PtzvFXVfWZ8fuZ5Mh+TVulLaz5RFqwY2iUQXG9jJgeoHgc00/xeBRtB52vjB3/JDA/yZP7dR9JC4h9a9D3frQpHhMzP2hTcr49vhhqkgcn2bv/fiva1JhPA1TVFcBHgBenLey6H/AM+t9CkiQwgCFJmiOqajHtofhY4BJaZsKLWP2/hSfQHvguBnYAnseYtMVA70fbmePiwesHtAfSYRbGicD9+8/ROK6lbQ95OHAOq4Ic82YY/t/SpqEso62X8ZFBf5fSvkl/PfA74BDa2h5X9fJPAq+jLSB6OfAz4MGD6zklybGTTlpVVwOPpE1TWEpb4PSR/ThJjk1yyqDJc2hrSPyWloHy7Ko6vfd1Om09jg/28l17/dm0/e3wXvf6l1bVlbRv6Z9NmzazhLbl5wuqavSwf3Pa32VZv/arWDW1h6p6Ny1T4Lu0aUNXservvne/15fTdhpZCDysqq7p5feiTX04mZaxcyXwxcE1vaMfezxtm9YrWbWzygtpi6q+K8ny/hpmtjyfFixZStte9S9q9S1Hd6AFKKYLIjyytx0PUIw8mZaRtFqWQ7VdP/4f7TM3RQvoPKJ/zkaOoa3TMt1uLdNNa7kf8JMkK2j37BO0KTsjz6VNJ7oIOJX2z827pzmHJGkOyoTMP0mSdCPVd224ADi6qqZ7eJUkSbrRMQNDkqQbuT4tZvck27NqfYzvbOJhSZIkrVcGMCRJuvG7G/Ar2nSUh9OmeVw5cxNJkqQbF6eQSJIkSZKkzZ4ZGJIkSZIkabNnAEOSJEmSJG32DGBIkrZYSc5NcnWSPceO/yhJJVm4ns+3KMl1Sd6yPvvdnCQ5PMkPklzRfx4+Q90FST6ZZEWS85I8Yaz8Cf34iiSfSrLgBrTdK8mJSaaSLEnywUHZ65MsTnJ5b3vsWNv7JvlhLz87yTMGZQ9N8s0kS5NcnOSdSXYdlO+b5NNJLktyQZJnzfb+pHldkt/11+uSpJcd3Pu9pPf9hSR/NGj7lCTXDrZcXZ7kPoPyVyb5aZKVSV4x4W/xV0nO6dd8WpJ7TqizXZJfJLngBlzT9knemuQ3fdyf6VsNj8re1f8Gy5L8X5IHj/X99CRn9ev5fJJ9xsclSdKIAQxJ0pbuHODxozdJbgPstLadJdlmhuInAUuAP+s7gqx3azj/BpVkO+DTwAeA+cD7gE/345O8Gbga2Bs4GnhLkkN7X4cCbwOO6eVXAMfPpm33CeBi4ADgJsC/DsreBdyqqnYD7g4cneTR/bzbAp/s554H/Bnw70lu19vOA14F7APcGtgX+JdB3x+gfab2Bh4KvCbJn8zy/jwDeCRwO+C2tAVXn9nLdgdOAv6o9/293tfQqVW1y+D11UHZWcCLgc+NtSHJXYB/Bo7s1/cu4JNJth6r+iLgkrG2a7qm59MWkb1tv2dLgP/qZdsAi4F79/O+FPhoeuCwB2BeAzwCWEC7rx8aH78kSSMGMCRJW7oTaIGFkScD7x9W6N+6/6h/O714+A12koVp2RpPS3I+8OVJJ+nfpD+J9pB2De3hdFT2liT/Olb/00n+pv++T5KP92/fz0nyvEG9VyT5WJIPJLkceEqSOyc5tWcJ/DrJm4ZBhCQPSHJGWnbC8Um+luTpg/Kn9m/al/Rv+g+c5b28D+2h9D+q6qqqeiNty9b7TrgfOwOPAV5WVcur6pu0B/RjepWjgc9U1derajnwMuDRSXZdU9skDwD2B15UVVNVdU1V/Wh07qo6o6pWDIZzHXDL/vsCYDfghGq+D/wCOKS3PbGqPl9VV1TVEuAdwD36eXfp9+DV/Zw/Bj4GPHWW9+fJwL9V1QVVdSHwb8BT+nm/V1XvqqrLquoa4A3AHyXZY01/lN7+fVV1CrBsQvFC4PSq+kG11dvfD+xJC/zQr20R8ETgtWNt13RNi4AvVNVvqur3wEeAQ/uYVlTVK6rq3Kq6rqo+SwtS/HFv+zDgv6vq9Kq6GnglcK8kt5jNNUuS5h4DGJKkLd13gN2S3Lp/43wU7dvkoRW04MPutG/Vn53kkWN17k37Rv6B05znnsB+wIeBj9IeVkc+RMvKGE0XmA88APhwkq2AzwA/pn3bfz/gBUmG53kE7UF5d+CDwLXAX9MeQu/W2zyn971nr/sSYA/gDFoWAr38EcCxwKOBvYBvMPjWO8lnk/z9NNd4KPCTWn0Ls5/04+MOBlZW1ZmDYz8e1D20vwegqn5Fy7g4eBZt79qv631pUzG+n+Tew5Mn+fsky4ELgJ2BE/t5ftOv98+TbJ3kbsCBwDenueZ7AaePuh37Ofr9sME1zXR/VrvmsWuadN6Lq+p3g2O3T3JpkjOTvOwGZOOcAmyd5C79n4GnAv9Hy2AZ+S/a52J8+901XdO7gHv0INxOtMDUKZMGkWRv2t/29OHhCb8fhiRJExjAkCTNBaMsjD+lfdt+4bCwqr5aVT/t3xL/hPaAe++xPl7Rv1Eef8AbeTJwSv/W/kTgQUlG33B/AyjgiP7+SNp0gIuAOwF7VdVxVXV1VZ1N+9b/qEHfp1bVp/r4ruzfpH+nqlZW1bm06RCj8T6E9m37J6pqJfBGVn9QfRbw2qr6RS9/DXD4KAujqh5WVf88zTXuAkyNHZsCdp2m7uUz1J2przW13Y8WAPoKcFNaJsOnM1jrpF/DrsAdaH//4bk+BPwjcBXtb/MPVbV4/AKS/Cnt7/qPvc9lwLeAlyXZIckdaJkioylJa7o/4+VTwC6jwNbgvPvRptD8zeDw12kP9jfp53w8bcrHbCwDPk4L0lwFvBx4xigokeRRwNZV9ckJbdd0Tf8fbZrIhbS/2a2B48Y76VN3Pgi8r6p+2Q9/Hnhcktsm2ZF2n4t1mOIlSdqyGcCQJM0FJwBPoKXrv3+8sH8z/ZU+hWOK9pC/51i16z3gDtrvCDyW9oBGVZ0KnN/PSX9Q/DCr1uJ4wqgu7dv/ffp0kKVJltK+Cd97unOnLfj42bRFJi+nBSFG491nWL+fe7go44HAfw7OdRntm+99p7u+geW06RdDuzF52sKa6s5Uvqa2VwLn9ikX11TVh2nXfI9hgz5F5Ee9/j8BJLkV7W/xJGA7WibBi5M8dNg2yV1pgagjxzJBjqZNm1gMvIWWzTO6vzf0mncDlg+zG5LsBXwROL6q/pAZU1VnV9U5PYj1U1qQ4Ehm52nAn/dr3Y42VeSzPWtiZ+D1wPOmabuma3ozsD0t22dn2tokq2Vg9CyjE2gZNs8dXNP/0IIpHwfO7a9lrP55lSTpDwxgSJK2eFV1Hm3u/UNoD1jjTqStsbB/Vc0D3srqqe3QvhmezqNoD3XH96DCxbSAwPg0kiN7psNdaA9t0B6Ez6mq3QevXavqITOc+y3AL4GD+kKVxw7G+2tahgLwh7U59hu0XQw8c+x8O1bVt2e4vpHTgduOZQzcltWnBIycCWyT5KDBsdsN6p7e34/GeXPag/CZs2j7E65/T2b6+2wDjNZVOAw4s6q+0IMBZ9AWvvzD7hhJbk/7PDy1qv53tZNUndezVPaqqrvQAkffG1zTTPdntWseu6bR1KIvAidV1atnuJ7R9Y5/RqdzOPDZqjqzX/PnaZ+TuwMH0dbI+Eb/3H4CuFn/HC+cxTUdDry3r91xFW0qyp1H2TC93btoAbnH9PU9Vl1E1Zur6qCq2pv2z8Q2wM9meV2SpDnGAIYkaa54GnDfWn1xx5Fdgcuq6vdJ7kzPnLgBngy8G7gN7YHucFo2wO3Sdj2hZwJcCryTtujh0t72e8CyJH+XZMe+LsNhSe40w/l2paXrL+8ZBc8elH0OuE2SR/Y1Ev6SNs1i5K3AS7JqN5B5SR47y+v8Km39jeelbZE5+jb9egub9vv8CeC4JDsnuQdtLY8TepUPAg9PckTPAjgO+ERVLZtF208C85M8ud+vI2lBmm8l2SrJM5PMT3Pnfg9GgYgfAQelbaWavmDkw2hBEZIcRpva8FdV9Znx6+prqeyatuXoE2lTWf59lvfn/cDfpG3Fug/wQuC9vd/dgC8A36qq661BkuTBfQ2JURbJyxjsUpJk2yQ70P7fbps+xWW0y8j3gYcmuXm/5j+lrUXxs/7an1Wf26cDv+m/L57FNX0feFL/HG1LW4vloqq6tJe/hTat5OHj06/6GA/rYzoAeDvwn30aliRJ11dVvnz58uXL1xb5oqWk33/C8W1o32Av7O+PBM6jpa9/FngT8IFetrDX3Waac+wLrARuM6HsZOBfB+9f1vt67Fi9fWgZGhfTtqH8zmjcwCtGYxnUvxctA2M5bQ2H44BvDsofRMtimKJtTXoqcMyg/Bjgp7QgyGLg3YOyU4BjZ7intwd+QJuW8UPg9oOyY2nrgIzeLwA+RVsk9XzgCWN9PaEfX0F7GF9wA9oe0a9hOXAacEQ/vhUtAHFZLzuzjyuDto+jPbiPpiu8Dtiql72HtmvJ8sHr9EHbF9C2Gl1BW1Pijjfg/oQ2XeOy/nr9aFy0IFj1fofnPqCX/ystsLACOLv/zbcd9P3e3n74esrgvMf1+7iMtg7MMeN/2173PsAFN+Ca9qAFo34LLO335M697MA+jt+PXdPRvXx3WuBoBe2z/1raWhyb/N8dvnz58uVr83yN/qMpSZK2QH39gQtoD41f2dTjkSRJWltOIZEkaQuT5IFJdk+yPavWx/jOJh6WJEnSOjGAIUnSluduwK9oa248HHhkTb/9qyRJ0o2CU0gkSZIkSdJmzwwMSZIkSZK02TOAIUmSNkt9W9nPJJlK8t/92KuSXJrk4iQHJFk+2C50un6OSHLGxhm1JEnaUAxgSJJ0I5Lk3CT3X0OdryZ5+no4132SXDCLendOcnKSpUkuS/K9JH++ruenbW+7N7BHVT02yQHAC4FDquqmVXV+Ve1SVdfO1ElVfaOq/mg9jGdW939Cm6cnOasHWz6fZJ8Z6i5I8skkK5Kcl+QJg7KbJTkpyUVJKsnCtb8SSZJufAxgSJKktZbkbsCXga8BtwT2AJ4NPHg9dH8gcGZVrezvDwB+V1W/XQ99bxRJ7gO8BngEsAA4B/jQDE3eDFxNC9wcDbwlyaG97Drg88BjNtR4JUnanBnAkCTpRiLJCbSH+M/0b/NfPKHOq4EjgDf1Om/qx2+V5Es9Q+KMJI8btHlIkp8nWZbkwiR/m2Rn4BRgn97P8mkyB/4FeF9Vva6qLq3mB1U17P8vegbCZT2DYJ9B2cRxJfkn4B+BP+vnfibwpcF43ptkYc9E2Ka3WZDkPT1DYUmST/Xjq2WSJNknyceTXJLknCTPG5S9IslHk7y/34/Tk9xxtvd/gocB/11Vp1fV1cArgXslucWEv93OtODEy6pqeVV9EzgJOAagqn5TVccD35/FeSVJ2uIYwJAk6Uaiqo4Bzgce3qdOvH5CnX8AvgE8t9d5bn8w/hJwInAT4Cjg+CSH9GbvAp5ZVbsChwFfrqoVtCyKi3o/u1TVRcNzJdmJtmXrx6Ybc5L7Aq8FHgfcDDgP+HAvm3ZcVfVyWubCR/q53zY2nqdMON0JwE7Aob2/N0wYz1bAZ4AfA/sC9wNekOSBg2r/r49xd1oA4U393k68/0l+MpzqMek2TPj9sAn1DgZWVtWZg2M/7tcjSdKcZwBDkqQt38OAc6vqPVW1sqp+BHwceGwvvwY4JMluVbWkqn44y37n0/5f4tcz1DkaeHdV/bCqrgJeAtytr9+wpnHNWpKb0QIcz+rXcE1VfW1C1TsBe1XVcVV1dVWdDbyDFjwZ+WZVndzX1jgBuN1M566q21bVidMUfx54XJLbJtmRllVStEDLuF2Ay8eOTQG7znR+SZLmCgMYkiTdiCV562CKx7HTVDsQuEtfZHNpkqW0wMJNe/ljgIcA5yX5Wl/XYjaW0NZluNkMdfahZV0AUFXLgd/Rsh/WNK4bYn/gsqpasoZ6B9KmoQzPeSxtzQMpO98AACAASURBVImRiwe/XwHsMJqmckNV1f8AL6cFZs7tr2XApMVRlwO7jR3brdeXJGnOW6v/GEuSpE2mVntT9SzgWTPVARYDX6uqP53YYdX3gUck2RZ4LvBRWkBgvJ/xdlckOZUWAPnKNNUuogUNgD9MG9kDuHBN47qBFgMLkuxeVUvXUO+cqjpoLc8z4z2Z2KDqzbTFOUlyMPBS4GcTqp4JbJPkoKr6//qx2wGnr+VYJUnaopiBIUnSjctvgJvfwDqfBQ5OckySbfvrTklunWS7JEcnmVdV19CmMFw36GePJPNmONeLgackeVGSPQCS3C7Jh3v5h4A/T3J4ku1p61p8t6rOnWlcs78dTVX9mrbo6PFJ5ve+7jWh6veAZUn+LsmOSbZOcliSO83yVLO5/3+QZIfef9K2gX078J+TMkX6uiOfAI5LsnOSe9B2Lzlh2B+wfX+7fX8vSdKcYABDkqQbl9cCL+3TH/52mjr/CRzZd+J4Y1UtAx5AW+fhItoUidex6kH4GODcJJfTsjmOBqiqX9ICEGf3811vF5Kq+jZw3/46O8lltIf0k3v5/wAvo02h+DVwiz4OZjGuG+oY2noevwR+C7xgwnivpa29cThtS9NLgXcCMwVphq53//tOJUdPU38H2iKly2nBk1Np94Pe9tgkpwzqPwfYsY//Q8Czq2qYgXFl74t+nVfOctySJN3opeoGZ0JKkiRJkiRtVGZgSJIkSZKkzZ4BDEmSJEmStNkzgCFJkiRJkjZ7BjAkSZIkSdJmzwCGJEmbiST3SXLBph6HJEnS5sgAhiRJc1SS5yc5J8mKJL9IcvAMde+Q5OtJlif5TZLnD8oWJvlKkiuS/DLJ/QdlT07ygySXJ7kgyeuTbDPW91H9/CuS/CrJEYN+q59z9BpuQfr6JIt73+clOXas37cnOSPJdUmeMuGcZySZSvLbJO9LstuE6z4oye+TfGBwLEn+Icn5/dwfHrZN8rgk3+7346sT+qx+raNreueEOtv1ezIxoJXkSb2fpw+OvSLJNWP36+aT2q9JkpslOSnJRf08C8fKZ7xGSZI2BAMYkiTNQf3B92nAQ4FdgIcBl05Td0/g88DbgD2AWwJfHFT5EPCjXvYPwMeS7NXLdgJeAOwJ3AW4H/C3g77/FHgd8OfArsC9gLPHhrB7Ve3SX68cHH8XcKuq2g24O3B0kkcPyn8MPAf44YTL+hZwj6qaB9wc2AZ41YR6bwa+P3bsScAxwD2AfYAdgf8alF8G/AfwzxP6G7nd4JqePqH8RcAlkxommQ8cC5w+ofgjg353qarxezlb19H+5o+Zpnw21yhJ0nplAEOSpDVIcm6SlyT5eZIlSd6TZIdp6v5dko+NHfvPJG/sv/95/2Z9WZKzkzxzhvNWklsO3r83yasG7x+W5P+SLO3fht92ltezFfBy4K+r6ufV/KqqLpumyd8AX6iqD1bVVVW1rKp+0fs6GLgD8PKqurKqPg78lP7gW1VvqapvVNXVVXUh8EHag//IPwHHVdV3quq6qrqw11ujqjqjqlYMDl1HC66Myt9cVf8L/H5C28VVNQzYXDts26/tKGAp8L9jzR8OvKv3sZwWgPmzJDv1vv+nqj4KXDSb6xiXZBHwROC101R5LfBGpgk4zdDvXfvnZGmSHye5z3R1q+o3VXU81w/ejMrX6RolSVobBjAkSZqdo4EHArcADgZeOk29DwMPSbIrQJKtgccBJ/by39KyHXajZR28IckdbuhgktweeDfwTFrmw9uAk5Js38uPT3L8NM3366/D+hSMc5L8Uw9sTHJX4LL+8PvbJJ9JckAvOxQ4u6qWDer/uB+f5F70zIF+b+4I7JXkrLQpJm9KsuNYm/N62Xt6NsjwPvx9kuXABcDOrLrPa5TknkmmgGW0gMt/DMp2A46jBW8mNh/7fXvgoNmeG/h6kouTfGJ8egYtm+NY4MoJY74z7Z69dZp+H57ksiSnJ3n2oN2+wOdoWSYLaFkwHx9kykiStNkzgCFJ0uy8qX/jfhnwauDxkypV1Xm0KQuP6ofuC1xRVd/p5Z/r2Q5VVV+jTcU4Yi3G8wzgbVX13aq6tqreB1xFCzZQVc+pqudM03a//vMBwG2AP+nX87QZ6j8ZeD5wAHAObdoItOknU2P1p2jTQVaT5Km0h+9/7Yf2BrYFjqTdg8OB27MqOHQpcCfgQOCPe58fHPZZVf/cj98BOGHCWKZVVd/sU0j2A/4FOHdQ/EpalsWkNSg+Dzw9bY2OecDf9eM7zfLU9wYWAreiZTB8Nn1dkCSPArauqk+ON+oBn+OB51bVdRP6/Shwa2Av4C+Af0wy+pw+ETi5qk7umS5fAk4DHjLLMUuStMkZwJAkaXYWD34/j7b2AUlOGSyYeHQvP5FVAY4nMMgKSPLgJN/p35IvpT1ArpZVMEsHAi/s0wGW9r72H41rDUbf7L++qpZW1bm0DI7pHmavBD5ZVd+vqt/Tpn3cvT+8L6dlkwztRstq+IMkj6RNfXjwYOrGaBz/VVW/7sf/fTSOqlpeVadV1cqq+g3wXOABo+yWkR4M+lHv759mcf2r6VNWPk/LniHJ4cD9gTdM0+TdtADOV2nZJF/px2e1g0xVfb1PqVlKCwotAm6dZGfg9cDzpmn6HOAno2DYhH5/XlUX9YDWt4H/pAWHoH1eHjv2ebkncLMkRww+w5PW1ZAkabOwzZqrSJIkWnBg5AD63P+qevCEuv8N/FuS/WiZGHcD6NM7Pk5bBPLTVXVNkk+x+nSEoStY/Vv9m7LqIXkx8OqqevVaXMsZwNVADY7VNHUBfjJD3dOBmyfZdTCN5HasHrR5EPAO4KFV9dM/dFK1JG2XjdmOY1Q23Rcw29Cm+KyNYdv70DIkzk8CLctk6ySHVNUdevbDy/uLJA8ALuyvtVG0z8BB/bzf6OfdDpiX5GJaZs39gHsnGQWaFgC3T3J4VT13hn6hfV5OqKq/mGYMu6zl2CVJ2mjMwJAkaXb+Msl+SRbQdtr4yHQVq+oS2rfz7wHOGS14SXsg3Z62u8TKJA+mTeOYzv8BT0iydQ8C3HtQ9g7gWUnukmbnJA8dz06YZnxX9PG/OMmuPdDyDOCz0zR5D/CoJIcn2RZ4GfDNqpqqqjP7OF+eZIc+BeK2tEANSe5Lm/bxmKr63jR9/1WSm6TtrvHXo3H0a/ujJFsl2YO2cOVXq2qqH3tmkvn9+u8M/CWDBTfTtiLdgfYQv20f31a97OjROh5JDqRNCxq1fTstmHF4f72Vtn7EA3v9BUlu0c97CC1r5LjRtI7+99qBFhTZqp932152aL+PWyfZBfg3WuDjF8DPaIGy0XmfDvym/74YeAptisio/DRaxsk/9L4fMXY/ngd8ul/TB2jrYzxwNL4k9+l/+4n6NWzf326fwcK1M12jJEkbigEMSZJm50TaehVnA79i8pab4/XvzyAToWcoPI+2VsES2vSSk2bo4/m0HS+W0hYR/dSgr9No6xy8qfd1Fu0BF4Akb00y3UKP0KZjLKdlkpzax/nu3vaItIUxR+f6Mm1Ryc/RFiG9ZR/7yFG0tS2W0LbVPLIHcaAFO+YBJw+mKZwyaPtK2k4XZ9Ie4n9ECyZA297087TpKD+jrfExXHvkUbS/xTLaA/p/sfp2pl+kTSu5Oy0ocSVtEVGAQ4BvJ1lB21L1DNr9pKquqKqLR69+n34/uKY9gZOBFcApwLur6u2D8x7Tz/UW2toeV9ICTtDW/fgIcDnts7QQeFhVXdOnygzPexlwXX9/bZ/uMyy/Gri8qkbrfhxF+xwsA94PvK6vjUJVLQYeQfs7XkILiLyImf9f8Mp+7QC/ZPVFRWe6RkmSNohUzZSpKUmSkpwLPL2q/mdTj0WSJGmuMgNDkiRJkiRt9gxgSJIkSZKkzZ5TSCRJkiRJ0mbPDAxJkiRJkrTZ22ZTD2BD2nPPPWvhwoWbehiSJEmSJGmWfvCDH1xaVXuNH9+iAxgLFy7ktNNO29TDkCRJkiRJs5TkvEnHnUIiSZIkSZI2ewYwJEmSJEnSZs8AhiRJkiRJ2uwZwJAkSZIkSZs9AxiSJEmSJGmzZwBDkiRJkiRt9gxgSJIkSZKkzZ4BDEmSJEmStNkzgCFJkiRJkjZ76xTASPKgJGckOSvJ308o3z7JR3r5d5MsHJS9pB8/I8kD19Rnkvsm+WGSnyV5X5Jt1mXskiRJkiTpxmOtAxhJtgbeDDwYOAR4fJJDxqo9DVhSVbcE3gC8rrc9BDgKOBR4EHB8kq2n6zPJVsD7gKOq6jDgPODJazt2SZIkSZJ047IuGRh3Bs6qqrOr6mrgw8Ajxuo8ghZ4APgYcL8k6cc/XFVXVdU5wFm9v+n63AO4uqrO7H19CXjMOoxdkiRJkiTdiKxLAGNfYPHg/QX92MQ6VbUSmKIFI6ZrO93xS4FtktyxHz8S2H8dxi5JkiRJkm5EbhSLeFZV0aacvCHJ94BlwLWT6iZ5RpLTkpx2ySWXbMxhSpIkSZKkDWRdAhgXsnoWxH792MQ6fdHNecDvZmg7bZ9VdWpVHVFVdwa+DpzJBFX19qq6Y1Xdca+99lrLS5MkSZIkSZuTdQlgfB84KMmiJNvRMiROGqtzEqsW2zwS+HLPpjgJOKrvUrIIOAj43kx9JrlJ/7k98HfAW9dh7JIkSZIk6UZkrbciraqVSZ4LfAHYGnh3VZ2e5DjgtKo6CXgXcEKSs4DLaAEJer2PAj8HVgJ/WVXXAkzqs5/yRUkeRgu6vKWqvry2Y5ckSZIkSTcuaQkRW6Y73vGOddppp23qYUiSJGlLcsFpcMkZcPujN/VIJGmLlOQHVXXH8eM3ikU8JUmSpM3GqW+Gk18EW/AXgZK0OTKAIUmSJN0QU4vhmhWwwh3vJGljMoAhSZIk3RBLF7efl52zacchSXOMAQxJkiRptlZeBcsvbr8vMYAhSRuTAQxJkiRptqYuWPW7GRiStFEZwJAkSZJma2rxqt/NwJCkjcoAhiRJkjRbowyM3Q8wA0OSNjIDGJIkSdJsLV0MBA68pxkYkrSRGcCQJEmSZmtqMex6U9jr4LaN6lXLNvWIJGnOMIAhSZIkzdbS82He/jB/UXvvNBJJ2mgMYEiSJEmzNbUYdt8fFvQAhtNIJGmjMYAhSZIkzcZ118HUhWZgSNImYgBDkiRJmo3lv4HrrmkZGDvsBjvtYQaGJG1EBjAkSZKk2Zha3H7O27/9nL/IDAxJ2ogMYEiSJEmzsfT89nMUwFiwyAwMSdqIDGBIkiRJszHKwNh9kIExdQGsvHrTjUmS5hADGJIkSdJsLF0MO+wO2+/a3i9YBHXdqsCGJGmDMoAhSZIkzcbUBauyL8CdSCRpIzOAIUmSJM3G1OJV619Ay8AA18GQpI3EAIYkSZK0JlVtCskwgLHL3rDtTmZgSNJGYgBDkiRJWpPfL4Wrl60+hSRp00jMwJCkjcIAhiRJkrQmS/tCncMMDGjTSMzAkKSNwgCGJEmStCZTF7Sfu48FMOYvhCXnwnXXbewRSdKcYwBDkiRJWpPRVqnzDlj9+IJFsPJKWH7xxh+TJM0xBjAkSZKkNVl6PmyzA+y85+rH3UpVkjYaAxiSJEnSmkwthnn7tYU7h9xKVZI2GgMYkiRJ0pqMb6E6Mm9/yNZmYEjSRmAAQ5IkSVqTqcXXX8ATYOtt23EzMCRpgzOAIUmSJM3kmithxSXXX8BzZL5bqUrSxmAAQ5IkSZrJ1IXt57z9JpcvWGQGhiRtBAYwJEmSpJlMnd9+TppCAi0D48olcOXSjTcmSZqDDGBIkiRJM1m6uP2ctIgnuBOJJG0kBjAkSZKkmUwthmwFu+0zuXx+D2C4DoYkbVAGMCRJkqSZTF0Au+7TdhyZZP7C9tMMDEnaoAxgSJIkSTNZOs0WqiPb7wI738QMDEnawAxgSJIkSTOZOn/6HUhGFiyCJedulOFI0lxlAEOSJEmaznXXwuUXTb+A58iCm5uBIUkbmAEMSZIkaTrLfg3XrZx5Cgm0hTwvvxCu+f3GGZckzUEGMCRJkqTp/GEL1QNmrrdgEVCw9LwNPiRJmqsMYEiSJEnTmbqg/ZxNBgY4jUSSNiADGJIkSdJ0ps5vP2eziCe4laokbUAGMCRJkqTpLF0MOy6A7Xaeud5Oe8B2u5qBIUkbkAEMSZIkaTpTi9c8fQQggQULzcCQpA3IAIYkSZI0naWL17yF6sj8RWZgSNIGZABDkiRJmqSqLeK5+xp2IBlZsKjtQnLdtRt2XJI0RxnAkCRJkia5cglcs+KGZWBcezVcftGGHZckzVEGMCRJkqRJls5yB5IRdyKRpA3KAIYkSZI0ydTi9nM2i3hCy8AA18GQpA3EAIYkSZI0ydIewJg3yzUw5u0HW21rBoYkbSAGMCRJkqRJphbDtjvBTgtmV3+rrduCn2ZgSNIGYQBDkiRJmmSqb6GazL7NgkVmYEjSBmIAQ5IkSZpk6eLZL+A5Mn8RXHZu24JVkrReGcCQJEmSJplaPPsFPEcW3ByummpbsEqS1isDGJIkSdK4q1fAFb9rU0huiNFWqpedvf7HJElznAEMSZIkadzUBe3n7rPcgWTErVQlaYMxgCFJkiSN+8MWqjcwA2P+ge2nC3lK0npnAEOSJEkaN9UDGDd0DYxtd4Rd9zEDQ5I2AAMYkiRJ0ripxZCtYZeb3vC2bqUqSRuEAQxJkiRp3NLFsNu+sPU2N7zt/EVmYEjSBmAAQ5IkSRq3NluojixYCMsvhquvWK9DkqS5zgCGJEmSNG7p4hu+gOfIaCeSJeeut+FIkgxgSJIkSau7diUsu2gdMjBGAQynkUjS+mQAQ5IkSRpadhHUdTBvv7VrP8rAcB0MSVqvDGBIkiRJQ0v7FqprO4VkpwWwwzwzMCRpPTOAIUmSJA1N9QDG7gesfR/uRCJJ650BDEmSJGnoDxkYazmFBNo6GGZgSNJ6tU4BjCQPSnJGkrOS/P2E8u2TfKSXfzfJwkHZS/rxM5I8cE19Jrlfkh8m+b8k30xyy3UZuyRJkjTR1Pmw816w7Y5r38f8RbD0/LYgqCRpvVjrAEaSrYE3Aw8GDgEen+SQsWpPA5ZU1S2BNwCv620PAY4CDgUeBByfZOs19PkW4OiqOhw4EXjp2o5dkiRJmtbUBWu//sXIgkVw3cpV01EkSetsXTIw7gycVVVnV9XVwIeBR4zVeQTwvv77x4D7JUk//uGquqqqzgHO6v3N1GcBu/Xf5wEXrcPYJUmSpMmWLl636SMAC27efjqNRJLWm3UJYOwLDEPKF/RjE+tU1UpgCthjhrYz9fl04OQkFwDHAP88aVBJnpHktCSnXXLJJWtxWZIkSZqzqloGxros4AlupSpJG8CNaRHPvwYeUlX7Ae8B/n1Spap6e1XdsaruuNdee23UAUqSJOlGbsWlsPLKdZ9CsuvNYOvtzcCQpPVoXQIYFwLDf7Pv149NrJNkG9rUj9/N0Hbi8SR7Aberqu/24x8B7r4OY5ckSZKub+r89nP3dQxgbLUVzF9oBoYkrUfrEsD4PnBQkkVJtqMtynnSWJ2TgCf3348EvlxV1Y8f1XcpWQQcBHxvhj6XAPOSHNz7+lPgF+swdkmSJOn6pi5oP9c1AwP6Vqrnrns/kiQAtlnbhlW1MslzgS8AWwPvrqrTkxwHnFZVJwHvAk5IchZwGS0gQa/3UeDnwErgL6vqWoBJffbjfwF8PMl1tIDGU9d27JIkSdJES/tybOu6iCe0dTDO+UZbVyNZ9/4kaY5b6wAGQFWdDJw8duwfB7//HnjsNG1fDbx6Nn32458EPrku45UkSZJmNLUYttsFdpy/7n0tWATXrIAVl8AuN1n3/iRpjrsxLeIpSZIkbVhLF7fpI+sjY8KdSCRpvTKAIUmSJI1Mnb/uC3iOLOgBDHcikaT1wgCGJEmSNDLKwFgfdj8AiBkYkrSeGMCQJEmSAK5aBr9fuv4yMLbZvi0GagaGJK0XBjAkSZIkWL9bqI7MX2gGhiStJwYwJEmSJBhsoboeAxgLFpmBIUnriQEMSZIkCdoCnrD+ppBA24lkxSVteookaZ0YwJAkSZKgZWBstS3sctP11+cCt1KVpPXFAIYkSZIEbQ2MefvCVuvxf5Hnu5WqJK0vBjAkSZIkgKn1uIXqiBkYkrTeGMCQJEmSoE0hWd8BjB3mwU57mIEhSeuBAQxJkiRp5dWw7NfrdwHPkfmLzMCQpPXAAIYkSZJ0+YVArf8MDHArVUlaTwxgSJIkSVOL288NlYExdUHL8pAkrTUDGJIkSdLUBe3nhsrAqOtWBUkkSWvFAIYkSZK0tAcXdtt3/fc9351IJGl9MIAhSZIkTZ0Pu+wN2+6w/vsebaXqOhiStE4MYEiSJEkbYgvVkV32hm13MgNDktaRAQxJkiRpavGGWcATIIH5C83AkKR1ZABDkiRJc9t118HUhRsuAwPaOhhmYEjSOjGAIUmSpLltxSVw7VUbNoCxYBEsOReqNtw5JGkLZwBDkiRJc9toe9MNNYUE2hSSlVfCsos33DkkaQtnAEOSJElz29Lz288NnYEBcNnZG+4ckrSFM4AhSZKkuW2jZGC4laokrSsDGJIkSZrbli6G7efBDvM23Dl2PwCytQt5StI6MIAhSZKkuW3qgg2bfQGw9bYwbz8zMCRpHRjAkCRJ0tw2tbgFFza0BTc3A0OS1oEBDEmSJM1tSxdv2AU8RxYsMgNDktaBAQxJkiTNXb+fgqumNvwUEmgLeV65BK5cuuHPtSU5/ZPtJWnO22ZTD0CSJEnaZJb2HUg2VgYGtCyMHW+/4c+3JaiCL74MEjj0UZt6NJI2MTMwJEmSNHdNXdB+7n7Ahj/XaCtV18GYvSXntjVKlp6/Ktgkac4ygCFJkqS5a2qUgbERFvGcv7D9dB2M2Tv3m6t+P//UTTcOSZsFAxiSJEmau5aeD1tvBzvfZMOfa/td2nnMwJi9c78JO+0J28+D8761qUcjaRNzDQxJkiTNXaMtVLfaSN/rLVjUpkVozarg3G/AwnvCNVfCed/e1COStImZgSFJkqS5a2NtoToyf5EZGLO15By4/MIWwDjw7nDpmbD8kk09KkmbkAEMSZIkzV1TizfOFqojCxa1h/KVV228c95Yjda/WHQvOPAe7ffzzcKQ5jIDGJIkSZqbVl4Fy38D8zbCDiQj8xcBBUvO23jnvLE65xttzZA9D4ab3Q623clpJNIcZwDj/2fvvuOrqu8/jr9OJhAgkMGGJEDYiCgziCgyXeBGq9ZVq8W2zlZ/ttZabetora1gq1XrBLeiIgiiMhKWCrJHSCCAQAYJJCHj5p7fH99cQWRk3HvPHe/n45HHCfeee847GjH3k+/38xERERGR8OQZoeqPCSQeCZ5Rqtv8d89gZNtmBUbqGWBZEBUDnQZDrhp5ioQzFTBEREREJDx5Rqj6cwtJ69oChkapnljRNji42xQwPFJGwN61cGi/c7lExFEqYIiIiIhIeCquLWD4s4lnXBLENFcjz5PJXWSOqSMPP5Y6ArBhxzJHIomI81TAEBEREZHwVJIHWNCyo//uaVlmFYYTKzDWz4KVL/j/vg2Ruxiat4Wk9MOPdTwdImNgu7aRiISrKKcDiIiIiIg4omQntGhv+iv4U0Iq7Nvo33tWV8BHd0D1ITj1JxAV69/714dtmwaenv4XHtFNTRFDjTxFwpZWYIiIiIhIeCre4d8Gnh4JXaF4O7hr/HfPNW9CeQFUlwV+AaAwG0r3/LD/hUdKBny3CipL/Z9LRBynAoaIiIiIhKeSPP828PRonQY1VXBgt3/uZ9uQNQ2Se0NkLGz51D/3bajcheaYeuaPn0vJALcLdq7wbyYRCQgqYIiIiIhI+HG7oWSXfxt4eiT4eRJJ9meQvxFG/ArSRgZBAWMxNG8Hid1+/FznoWBFBP4qEhHxCRUwRERERCT8lO4Bd7VzKzDAf5NIsqabhpj9LoH0cVC41WzTCES2bQoYaSN/2P/CI7YFtB+gAoZImFIBQ0RERETCz/cjVLv4/97xnSAi2j8rMPauNyswhvzMNO7sPsY8vnW+7+/dEAVboHTvsftfeKSMMFtIXJX+yyUiAUEFDBEREREJPyW1BQwnVmBEREKrLv5ZgbF0OkQ1hdNvMH9O7AaJ3QN3G0nuInNMHXn8c1IyoKYSdn3tn0wiEjBUwBARERGR8OMpYDgxhQRMHwxfr8AozYdv34QBUyAu8fDj6ePMmNKqct/evyFyF0GLDmZSy/F0GW6O25f4J5OIBAwVMEREREQk/BTnQZNWpqeCE1qnQVGu6fngKyufNysVhv3ih4+njzOPe1Y7BApP/4vUM47d/8KjWQK06aM+GCJhSAUMEREREQk/To1Q9UhIg8oSOLTfN9evroDlz0H6eEju8cPnUjIgOi7wtpEUbIay/BP3v/BIyYC8ZVDj8n0uEQkYKmCIiIiISPgpznOmgafH95NItvnm+mvegvICGP6LHz8XFQtdzzIFDF+uAKmvnIXmmHaC/hceKRlQVQp7vvVtJhEJKCpgiIiIiEh4se3AWIEBvmnkaduQNQ3a9oO0Ucc+J30sFO8wqx4CRe5iaNnxcHHnRLpkmKO2kYiEFRUwRERERCS8VBSb39471cAToHWqOfqikWf2AsjfAMOnHr+XRPpYcwyUbSTf978YeeL+Fx4t25tGnypgiIQVFTBEREREJLwUeyaQOLgCI7optGjvmxUYS6dDXBvod8nxz4nvBG36wua53r9/Q+RvNFte6tL/wiMlA3Zkgtvtu1wiElBUwBARERGR8OIZoerkFhIwWyW8vQJj30bYOh+G3Gx6XZxI+ljYkQUVB7yboSFyF5tjvQoYI0wT1PyNvskkIgFHBQwRERERCS/fr8BwsIknmD4Y3l6BsXQ6RDWBQTec/Nz0ceB2wbYvvJuhIXIWmhUxnq01dZHi6YOxxCeRRCTwqIAhIiIiIuGlJA+iznRULQAAIABJREFUmkJckrM5WqdB6R6oKvfO9coKYPVMGDAF4hJPfn7nIRAb73wfDLfbFCFSz6hb/wuPVimm6acKGCJhQwUMEREREQkvJXmmB0R93iz7gmcSyf5c71xvxfNQUwnDjjE69Vgio6Hb2bBlnrPjVPM3QnmhaeBZH5ZlVmFszwyscbAi4jMqYIiIiIhIeCnOc3YCicf3BQwvbCOproAVz5ltIck96/66HuPNKpA9axqfoaFyF5ljffpfeKSMgNK9ULTNu5lEJCCpgCEiIiIi4aUkz/kGnmC2kIB3+mCsfRvK8s3o1ProPsYcndxGkrvI9CNpnVL/16aMMEdtIxEJCypgiIiIiEj4qD5k3ug73cAToFkCNIlv/AoM24as6dC2H6SNqt9rm7eBDgPNNhInuN1mAklaPbePeCSlQ7Mks41EREKeChgiIiIiEj5KdppjIKzAALMKo7ErMLZ9AfvWmd4XDenrkT4Odi6H8qLG5WiIfevNKNSGbB+BI/pgaAWGSDhQAUNEREREwkeJZ4RqgBQwEtIavwIjaxrEtYH+lzbs9enjwHZD9oLG5WiI3MXm2NACBphtJMU7Do/HFZGQpQKGiIiIiIQPz5vcQGjiCWYFRvEOqHE17PX5m2DrPBjyM4iKbdg1OgyEZonO9MHIXWTGobZqxJaelAxz3JHlnUwiErBUwBARERGR8FGSB1YEtOzgdBIjIQ3cLjiws2GvXzodoprAoBsaniEi0jTz3Dof3DUNv059efpf1Hd86tHa9oXYeG0jEQkDjSpgWJY1wbKsTZZlbbUs695jPB9rWdYbtc8vsywr9Yjn7qt9fJNlWeNPdk3LshZZlrWq9mO3ZVnvNya7iIiIiISh4jxo0QEio51OYnw/iaQBY0DLCmD1TBgwBeKSGpcjfRyUF8Lubxp3nfrYtw4qihvewNMjIhK6DFMjTwk+B/fC00NgwSOmGa+cVIMLGJZlRQLTgIlAH+BKy7L6HHXajcB+27a7A08Cj9a+tg8wBegLTACmW5YVeaJr2rY90rbtU23bPhXIAt5taHYRERERCVOBMkLVI6ERo1RXvgCuCtO8s7G6jTYrU/y5jSRnkTl6RqE2RkoGFGyG0vzGX0vEH2wbPr4TCjbBwsdgzr1mVZKcUGNWYAwBttq2vc227SpgJjDpqHMmAS/Vfv42cI5lWVbt4zNt2660bTsH2Fp7vZNe07KslsBoQCswRERERKR+ivMCp4En1K4Gia1/I09XJSx/DrqPheSejc/RLAE6DfZvASN3MbRO9U5ByVME2aFVGBIk1r0LGz+CMQ+aIuSyf8OHv/TvNq4g1JgCRkfgyFa/O2sfO+Y5tm27gBIg8QSvrcs1JwOf2bZ94FihLMu62bKslZZlrczPVwVWRERERGq5a+DArsBagRERAa1T6r8CY83bULYPhk/1Xpb0cWYLSek+713zeNw1sN0L/S882g+A6GbaRiLBoawAZt8DHU6D4b+E8X+GM38D37wK79wENdVOJwxYwdjE80pgxvGetG37Wdu2B9m2PSg5OdmPsUREREQkoB38DuyawJlA4tE6Dfbn1v182zajU9v0ha5neS9H+jhz3Drfe9c8nr1roaLEewWMqBizgkSNPCUYzL4bKg/C5OkQGQWWBaPvhzF/NCsz3rgGqiucThmQGlPA2AUcWb7uVPvYMc+xLCsKiAcKT/DaE17TsqwkzDaTjxuRW0RERETC0fcjVBsxstMXEtLMCoy6NvHL+dI0wBz+C/PGx1va9Yfm7fyzjSR3sTmmnuG9a6aMgD1r4VCx964p4m3rZ8G692DUb6BN7x8+d8btcO4TsPkTeP1yqCpzJmMAa0wBYwWQbllWmmVZMZimnLOOOmcW8NPazy8FFti2bdc+PqV2SkkakA4sr8M1LwU+sm1b5SgRERERqZ+S2gJGIG0hAbMCo7oMyuq4/TlrGsS1gf6XeTeHZUH6WNi6AGpc3r320XIWQUJXiD96t3gjpGQANuQt8941RbypvAg+vgvanQIjbj/2OUN+BpOfgdxF8MrFZqWSfK/BBYzanha3AXOBDcCbtm2vsyzrIcuyLqw97Xkg0bKsrcCdwL21r10HvAmsB+YAU23brjneNY+47RROsH1EREREROS4ineYY6BtIanPJJL8TWaFxJCfQVSs97Okj4PKEti53PvX9nDXmF4V3lx9AdBpEEREaxuJBK4598KhotqtIycY5XzqVXDpC7BrJbx0AZQV+i9jgItqzItt254NzD7qsQeO+LwCOGZp2LbtR4BH6nLNI547qxFxRURERCScleyEZokQE+d0kh9K6GqO+3Ogy9ATn7v0GTO1ZNANvsnS9SyIiILNc2tXNPjAnm9NkST1TO9eN7opdDxdjTwlMG2aA9++AaPuNdu1TqbvRaYx7RvXwP/Og2vfhxbtfJ8zwAVjE08RERERkforyQu81RcArboA1slXYJQVwuoZMGAKxCX5JkuTltBlOGyZ55vrwxH9L0Z4/9opGWaSinoHSCA5VAwf3W4a7468q+6v6zEern7brB57ceLhVWRhTAUMEREREQkPxXkQH2D9L8BsBYnvZFZgnMjKF8BVAcN+4ds86eNMk9CSnb65fu5iSOgGLTt4/9opI8DtgjwfboERqa+595vxxJOnmYk59ZF2pll9UVYIL0yEwmzfZAwSKmCIiIiISOizbbMCo1WATSDxaJ164hUYrkpY8Rx0HwNtevk2i2ecqi9WYdS4zBaPNC+NTz1a5yFgRWgbiQSOLfNh1asw4tfQYWDDrtF5CFz3IbgOwQsTYO9672YMIipgiIiIiEjoKy+C6vLAXIEBppHniVZgrH0HSvfC8Km+z5Lc04ya9UUBY8+3UHkAUn1UwGjS0kx4UAFDAkHFAfjwV5DUE0b9tnHXaj8Arv/EFOj+dy7s+to7GYOMChgiIiIiEvpKaveOB9oIVY/WaWaMauXBHz9n22Z0aps+0PVs32exLOgxDrZ9YVZ+eNP3/S+8PIHkSKlnwM4V3s8uUl/zfg8HvzNTR6KbNP56yT3hhk8gpgW8dCFsz2r8NYOMChgiIiIiEvo8/RwCeQUGwP7cHz+XsxD2rjW9LyzLP3nSx0F1mfdXMuQugsR0305TSMmAmsqw/Q21BIhtX8BX/zOrpjoN8t51E7qaIkaLtvDKRZC9wHvXDgIqYIiIiIhI6CvOM8dALWC0ri1gFG378XNZ0yAuGfpf5r88qSPNuFZvbiOpcZnfGPty9QWYKSoA25f49j4ix1NZCrN+CYnd4ez7vX/9+E5mO0liN3j9Ctj4sffvEaBUwBARERGR0FeSB9HNoFmC00mOzbMC4+hGnvmbYctcGPwz7yxBr6uYZqbR5pZPvXfN71ZD1UHfNfD0aJZgttuoD4Y45bM/mqLppGkQ3dQ392jeBn76IbTrD29cA2ve9s19AowKGCIiIiIS+op3mNUX/tqCUV9N4qFpwo8beS57xqyEGHSD/zOlj4PCLcdeFdIQuYvMMcXHKzDAbCPJW2ZWfYj4U+4SWP4sDL0Fugzz7b2aJcC1H5j7vHMTfP2yb+8XAFTAEBEREZHQV5IXuA08PRLSfrgCo6wQVs2AAVdA82T/5+k+xhy9tY0kdzEk9TB7930tJQOqSs3UExF/qSqHD6aascjn/N4/94xtAT95G7qfY7atLH3GP/d1iAoYIiIiIhL6SnYGbv8Lj9ZHjVL96gVwHTLNO52Q2M3s4ffGNpKaatiR5bvxqUfrkmGO2kYi/rTgYfPf8IVPQ0yc/+4b0wymvA69zoc598LCJ/x3bz9TAUNEREREQltVGZQXmsZ3gSwhzRRaXFVmBOjy58wqiDa9ncuUPg5yFpnfLDfGd6vNighfN/D0aNneTGtQAUP8ZccyWDodBt/k+z4vxxIVC5e9BKdcAQv+BPMfNCOYQ4wKGCIiIiIS2jwjVFt1cTbHybROA9tttrusfRdK9zq3+sIjfawZSerpX9FQOQvN0V8rMMBsI9mRCW63/+4p4an6kNk6Et8ZxjzoXI7IKJj8bzj9elj8JHzym5D7/lcBQ0RERERCW6CPUPU4chJJ1jRI7g3dRjubKWUERMc1fhtJ7mJI7uXfXh4pI+DQfsjf6L97Snj64i+m4e2FT5meFE6KiIDzn4Tht5lmokv+4WweL4tyOoCIiIiIiE+V7DDHQG/i2bq2gPH1S7B3jdlH7/TUlKhY6HqWKWDYdsPy1FTDjqVw6pXeTndiKZ4+GEugbR//3lvCx86vIPNfcNq1zhccPSwLxj1stlH1u9jpNF6lFRgiIiIiEtqK8yAiClq0dzrJibVoB1FNYcMsiEuG/pc5nchIH2vG0BZsbtjrd38D1WX+3T4C0CoFWnZUHwzxHVel2TrSor0pGAQSy4LBN0LT1k4n8SoVMEREREQktJXshJYdICLS6SQnZlmHt5EMvgmimzibxyN9rDk2dBuJp39Gygjv5KkryzKrMLZnhmQzQwkACx+H/A1wwVPQJN7pNGFBBQwRERERCW0leYHf/8IjoStExsKgG51Oclh8J2jTt+EFjJxFpp+HP/tfeKRkQOkeKNrm/3tLaPtuNSz6Owy46nCRT3xOBQwRERERCW3FQVTAOOteuOIVZ97sn0j6WNieBRUH6vc6VxXkLXNmrCQcXvWhbSTiTa4qeH+q2eo14c9OpwkrKmCIiIiISOiqqYaDuwO/gadHu/7QY7zTKX4sfRy4q2HbF/V73e5voLocUs/wSayTSuoBzRJVwBDvWvykabR7/pMh12Mi0KmAISIiIiKh68BusN3BswIjUHUeArHx9d9GkrvQHFMcKmB83wdjiTP3l9Czd53pfdH/Muh1rtNpwo4KGCIiIiISukp2mmOwrMAIVJHR0O1s2DKvfg0xcxeb/hlxib7LdjIpI6B4++HvBZGGqnHB+7+Apq1g4mNOpwlLKmCIiIiISOgqyTNHrcBovPRxpiHmnjV1O99VBTuWObd9xCMlwxy1jUQaK/Mp+G4VnPc3aJbgdJqwpAKGiIiIiISuYk8Bo5OzOUJB9zHmWNdtJLu+Atch5xp4erTtB7EttY1EGmffRvjir9BnkvkQR6iAISIiIiKhq2SHmRQQ3dTpJMGvRVvoMNBsI6mL3MXm6JkE4pSISOgyTCswpOHcNfDBVIhpDuf+zek0YU0FDBEREREJXcE0QjUYpI+DncuhvOjk5+YuNKsfAmGpfcoIKNgMpflOJ5FgtHQ67FoJ5z4eeCOOw4wKGCIiIiISukry1MDTm9LHmaku2QtOfJ6rEvKWQ6rD20c8PKtAdmgVhtRT/mZY8DD0PA/6XeJ0mrCnAoaIiIiIhCbbNpMntALDezoMhGaJJ99GsusrcFU438DTo/0AiG6mbSRSPzXV8N7N5nvn/CfNWF5xVJTTAUREREREfKKswLyJVgHDeyIiTTPPrfPA7YaI4/w+NGcRYB2eAOK0qBjoNFiNPKV+Fv0ddn8Dl71kesCI47QCQ0RERERCU8kOc9QWEu9KHwflhbD76+Ofk7sI2gVI/wuPlBGwZy0cKnY6iQSD3d/Awseg/+XQd7LTaaSWChgiIiIiEpq+H6GqAoZXdRsNVsTxx6lWVwRW/wuPlAzAhrxlTieRQFd9CN79OcS1gXMfczqNHEEFDBEREREJTSW1BQytwPCuZglmO8bxChi7VkJNZeAVMDoNgohobSORk1vwMBRsgklPQ9PWTqeRI6iAISIiIiKhqWQnxLSAJq2cThJ60seaJfal+378XO5iTP+L4X6PdULRTaHj6WrkKSeWuxiypsHgm6D7OU6nkaOogCEiIiIioak4D+I7aXKAL6SPM8et83/8XM4iaNc/MH9znZJhCi9VZU4nkUBUcQDevxUS0mDsQ06nkWNQAUNEREREQlPJDm0f8ZV2p0Dzdj/eRlJdATtXQNqZzuQ6mZQR4HaZjCJHm/t/ZuXWRf+BmDin08gxqIAhIiIiIqGpOE8NPH3Fssw2kq0LoMZ1+PGdK2r7X5zhXLYT6TzENCDVNhI52qY58M0rMOJ2830iAUkFDBEREREJPZUHoaJYKzB8KX0cVJbAzuWHH8tdZAoEXQKs/4VHk5Zm9YgKGHKkskKY9Uto2w/OutfpNHICKmCIiIiISOjRCFXf63oWRET9cBtJ7mJTIGgawI1TU0aYlSKuSqeTSCCwbfj4Dji032wdiYp1OpGcgAoYIiIiIhJ6SnaaY6suzuYIZU1ampUWW+aZP1cfMoWBQN0+4pGSAa4K08zTV/I3wZz/g7n3Q85CqKn23b2kcda8Des/gNH3Q7t+TqeRk4hyOoCIiIiIiNeV7DDH+E7O5gh16eNg3u9NwagwG2qqAreBp4dne8v2JdBlmPeu666BzXNh+X9g2xcQGWMez3oamsRD9zHQYyKkjwnMCS3h6MBumH0XdB4KGb9yOo3UgQoYIiIiIhJ69q6HiGgzKUN8x1PA2DLPvBm0IrxbFPCFuERI7m36YIy8q/HXKy8yzR9X/BeKd0CLDjD6d3DadRDdFLZ9bhpEbpkLa98BK9IUUXpONB+J3RqfQerPtuGDqWZ1zORnICLS6URSBypgiIiIiEhoyV4AX70I/S+DCO2Y9qnknhDfxRQwDhVB+1PNaoNAl5IB375hJqhENvAt0Z61ZrXFt2+B65DprTH2Ieh1PkRGHz6v9wXmw+2GXV/B5k9MQePT+81HYjr0nGBWZ3Qe2vA8Uj8rnzd/V5z3dxWRgoj+6xARERGR0LF/O7x9IyT1NG9MxLc841RXzzTbR4bd6nSiuknJMG9g93wLHU+r++tqXLDxI1j+rNmCEtUUTrkMhtwM7fqf+LUREdB5sPk45wHzvbp5Dmz6BJb+GzL/ZbaWdB9rVmZ0Pyc4ikHBqDAbPv09dDsHBt3gdBqpBxUwRERERCQ0VB+CN68BtwumvAaxzZ1OFB7Sx5liAEDqSGez1FVKhjluz6xbAaOswKzqWfkiHNhlmsOO/RMMvBqaJTQsQ+sUGPpz81FxwKwG2DzH9NFY86aZ8JIywhQzekyAhLSG3Ud+yF0D791iVslMetoU4SRoqIAhIiIiIsHPtuHju+C71XDlTC0J96e0MyEy1hSOAr3/hUfLDtA6zRQwMm47/nm7vjarLda+Y1aYdD0Lzn0Ceoz3bs+EJi2h72Tz4a6BvOWHt5rMudd8JPcyhYye50KnQcHXsyF/s/ln2aYXnH6Dc9u7ljwFO5fDxf813wcSVFTAEBEREZHgt/IFWPUajPqt+Y21+E9MM/OGvqLYvBEPFqkjYOPHpjfFkW+mXVVmrOby/5ixsDHN4bSfwpCfmZ4fvhYRCSnDzcfYh6BomylkbP7ETDRZ8g9olgj9LzfFl0CftLM/F758DFbPME1e3S7TN2TS05CU7t8se9bA53+GPpOh/6X+vbd4hWXbttMZfGbQoEH2ypUrnY4hIiIiEryqD0HBZmg/wOkkx5e3HF481/x2/Ko31bjTCa5KswomuonTSepu1evw/q1waxa07QMH95hC2MoXoWwfJHQzvS1OvTJwelEcKoat803hZcMswIIBV8CIOyCpu9PpfujAblj4OHz9stkOM/gmOOMO0/B1zr3m75az74Phv/RP41JXJTw3Gsryzb/zuETf31MazLKsr2zbHvSjx1XAEBEREZHjmn2PWfY98TGzVz/QHNwLz46CqFj42ecN70cg4Wd/Ljw1AAb/zExQWf+B2b6RPg6G3gxdRwd2Max4h2n8+fXL5s1538lwxp3Q/hRnc5Xmm1UiK/5r/nmedi2cefcPt2sc3Auz74INH5rJNZOmQbt+vs01/0FY/KQpcvYY79t7SaOpgCEiIiIi9eOqhL/1hOoKMyZy/J9h+FSnUx1WUw0vTzJ9Cm6ad/IpECJHsm14sq9pyhkbbxpyDr4x+PqnlO6DpdNh+X+h6qApwIy8y//9SA7th8ynYekz5u+LAVfCqN9A69Tjv2bd+zD7bvPakXfByLshKsb72XYsgxcnmH/HF/7L+9cXr1MBQ0RERETqZ/0sM9Xjypmmv8SGD83khRG/cjqZMec+88bt4ufglMudTiPBaMt8U8Dod0nwT605VAwrnjMFhPJCM8Fk5J1mVKgvJ21UlsKyZ8xqkIoS6HsxnP1/de9vUV5ktpR8+wa06WN6Y3Q83bv5/n0G2DVwaybEtvDetcVnVMAQERERkfqZcaVZ3XDHOsCGd26C9e/DmAfNXnYnffsWvHsTDL0FJj7qbBaRQFJVBl+/Apn/NMWZ9gPM6oZeF3h3S0z1IVjxPCz+uymY9DwXzr6/4VtBNs+FD2+H0j1mpdfZ90N008bn/OhO09vkuo9N41YJCscrYGgKiYiIiIj8WFkBbPkUht16uMHeJc+bCQnzHzSTBM68x5lse9bCrF9ClwwY97AzGUQCVUwcDLsFBt1gVjUsfhLevBaSepjCY//LIDK64dd3VcE3L8PCJ+Dgd9D1bBj9OzPatTF6jIepS2HeA2Y1x8bZZjVGSkbDr7l1Pqx8HobfpuJFiAjgrjQiIiIi4pg1b5sixYCrDj8WGQUXPQunXAELHoYv/ur/XIf2wxtXm6kQl/2vcW/EREJZVAycdg3ctgIufREiY83UlX8OhOXPmRUU9VHjgm9eg6dPh4/vglYpZlXDte83vnjh0SQeLngKrp1l/v55cSJ8fDdUHqz/tQ7thw9ug+ReMPr33sknjlMBQ0RERER+bPUMaHeKGS95pMgomPyMKWx88RdY8IhphugPbje8ezOU7IQrXoEWbf1zX5FgFhEJ/S6GWxbBVW9By46mceY/+sOiv5u+FSfidsPad2D6MPjgF9A0AX7yDtwwB1LP8E3mrqPgF1kw7Bdmmsn04bD1s/pdY/Y9ZmTqRf8OrvG+ckIqYIiIiIjID+3bAN+tglOvOvbzEZFm7OHAa2DhY/DZQ/4pYnz5qNnWMuEv0HmI7+8nEkosC3qMgxvnwvWfmALlZ3+EJ/vDZ38y28aOZNtmG8d/RsLbN0BEFFzxKtz8BaSP8W1jUDBbYSb8BW6Ya3phvHoxvD/VrKw4mXXvwZq3YNRvocNA3+YUv1IPDBERERH5odUzzJuVfpce/5yICLjgn6aYsfjvpsP/mD/67k3Npjnw5V/Nyo/BN/nmHiLhIiUDrnkXdn9jemQs+htkTYPTr4OM26Bgi9kmtmslJHSFi/9rVnFERPo/a5eh8PNFpli6+B+wdR6c/yT0Ou/Y5x/cYxp3djgNzrjTv1nF5zSFREREREQOc9fAk32h/alw1cw6nO82y9E9jfLGPez9IkZhNjx7NrROgRs/9c5kAhE5LH8zLPmHafppu81Hy05w1m9hwJWB02tm9yrT12LvGjOu9dzHIS7p8PO2Da9fATlfmqJHcg/nskqjaAqJiIiIiJzcti/MZIEJdWzQGREB5/3NrNjIeto03pvwV+8VMarKTNPOiAizfF3FCxHvS+4Bk6fDWffCyhehZQc47VqIinU62Q91OBVu/twUW758zPx9de7j0O8S83fON6/Alrkw4VEVL0KUChgiIiJhyu22cds2UZFqiSVHWD3DTALoObHur7EsmPioWV6+dLopYkx83BQdGsO2zbjUfRvg6nfMCgwR8Z1WXWDMH5xOcWKR0WaEc68L4IOp8M6NZmrSGbfDnPsgdSQMudnplOIj+olFREQkTH2TV8zAh+axIrfI6SgSKCoOwIaPzG8z6/ubV8uC8X+GjF+aqQEf32m2lzTG0mfM9INzfg/dz2nctUQktLTpZbaUjXvErMR4YTxYEWZKUmOLpxKwtAJDREQkTGVlF3Cw0kW35OZOR5FAsf4DcB0yjTIbwrJg7J/MdpLFT5rGnuc/1bA3E7mL4dPfQa/z1YhPRI4tItI0He05ERb8yTQebtXZ6VTiQypgiIiIhKnM7EJ6t29JQlyM01EkUKyeCQndoNOP+qbVnWXBOX8wRYyFj5umoBf+q37TC0p2wVvXmekHk5/x/bhGEQluid3gsv85nUL8QAUMERGRMFRRXcPK7fu5Zph6Ckit/bmwfTGM/l3jCwaWZa4TEQVf/MUUMSZPr1sRw1UJb14L1Yfguo+hScvGZRERkZChAoaIiEgY+nrHfqpcbjK6JTodRQLFt2+a4ylXeO+aZ91r9qR//ojZTjL53xB5kh8/59wLu1bC5S9Dck/vZRERkaCnAoaIiEgYysouJDLCYkhagtNRJBDYtpk+kjrSTCHwplG/MSsvPnvITCe5+DkzReBYvn4FVr4AI26HPpO8m0NERIKeChgiIiJhKDO7kP4d42nR5DhvJCW85C2Hom0w8m7fXH/kXWY7ybwHzHaSS1/4cRFj19fw8V2QNgpG/943OUREJKg1ar6MZVkTLMvaZFnWVsuy7j3G87GWZb1R+/wyy7JSj3juvtrHN1mWNf5k17SMRyzL2mxZ1gbLsn7VmOwiIiLhqrTSxeq8Ym0fkcNWvw7RzaDPhb67x4hfmzGrG2aZBp2uqsPPlRWavhfN29QWN/Q7NhER+bEGFzAsy4oEpgETgT7AlZZl9TnqtBuB/bZtdweeBB6tfW0fYArQF5gATLcsK/Ik17wO6Az0sm27NzCzodlFRETC2YrcIlxum4xuSU5HkUBQXQFr34PeF0BsC9/ea/hUmPgYbPzIFCxclVDjgrevh9J9pu9FnL4vRUTk2BpT3h4CbLVtexuAZVkzgUnA+iPOmQQ8WPv528DTlmVZtY/PtG27EsixLGtr7fU4wTVvBa6ybdsNYNv2vkZkFxERCVtZ2YXEREZwekprp6NIINg0GypLYMCV/rnf0J+bxp6z74Y3roakHpDzJUyaBh1P808GEREJSo3ZQtIRyDvizztrHzvmObZtu4ASIPEErz3RNbsBV1iWtdKyrE8sy0o/VijLsm6uPWdlfn5+g74wERGRUJaZXcDALq1oGlOHkZYS+lbPhBYdIO1M/91zyM96idlpAAAgAElEQVTg/Cdhy6eQ9TScfj0MvNp/9xcRkaDUqB4YfhYLVNi2PQh4DnjhWCfZtv2sbduDbNselJyc7NeAIiIiga64vIp1uw9o+4gYpftg63wYcIWZFOJPg26Ai541hYuJj/r33iIiEpQas4VkF6YnhUen2seOdc5Oy7KigHig8CSvPd7jO4F3az9/D3ixEdlFRETC0tJtRdg2ZHRXA08B1rwFdo3/to8cbcAV5kNERKQOGrMCYwWQbllWmmVZMZimnLOOOmcW8NPazy8FFti2bdc+PqV2SkkakA4sP8k13wfOrv18FLC5EdlFRETCUlZ2AU2jIxnQqZXTUSQQrJoBHU6D5J5OJxERETmpBq/AsG3bZVnWbcBcIBJ4wbbtdZZlPQSstG17FvA88Eptk84iTEGC2vPexDTndAFTbduuATjWNWtv+VfgNcuy7gBKgZsaml1ERCRcZWYXMjgtgZioYNpFKj6xZw3sXQMTH3c6iYiISJ00asi2bduzgdlHPfbAEZ9XAJcd57WPAI/U5Zq1jxcD5zUmr4iISDjbd7CCLftKueT0Tk5HkUCweiZEREO/S5xOIiIiUif69YuIiEiYyMouBCCjm/pfhL0aF3z7JvQYD3H6fhARkeCgAoaIiEiYyMoupEWTKPp2iHc6ijgtewGU7XOueaeIiEgDqIAhIiISJjKzCxnWNZHICMvpKOK01TOgaQKkj3M6iYiISJ2pgCEiIhIG8orK2VFUru0jAoeKYePH0P9SiIpxOo2IiEidqYAhIiISBrK2efpfJDmcRBy3/n2oqYQBU5xOIiIiUi8qYIiIiISBrOxCEuNi6NG2udNRxGmrZkBST+hwmtNJRERE6kUFDBERkRBn2zaZ2QUM75aIZan/RVgr2gZ5S83qC30viIhIkFEBQ0REJMRtKyhj74FKbR8RWD0TsOCUK5xOIiIiUm8qYIiIiIS4zGzT/2JEdzXwdExVGWyaAytfBLfbmQxut5k+0nUUxHd0JoOIiEgjRDkdQERERHwrK7uAjq2a0iWhmdNRwodtQ8EW2DoPtsyD7ZmmcSZA/iaY8Bf/b+HYkQXFO+Ds3/n3viIiIl6iAoaIiEgIc7ttsrILOad3W/W/8LWqMshZaAoWW+eZYgFAUg8YfBOkj4HNn8KyZ6BFWzjjDv/mWz0DYppD7/P9e18REREvUQFDREQkhG3cc5D95dVkdNP2Ea+zbSjYfLhgsT0TaqogOs5s0xhxO3QfA61TDr8m7SwoL4D5D0JcMgy82j9Zq8ph3fvQZxLExPnnniIiIl6mAoaIiEgIy8wuAGC4ChjeUVkKOV/WFi0+g5LaVRbJvWDIzZA+FroMh6jYY78+IgImTYfyQpj1K2iWBD0n+D73xo+h6qCZPiIiIhKkVMAQEREJYVnZhXRNiqN9fFOnowQn24b8jUesssgCd7XZipE2CkbeYVZZtOpS92tGxcDlL8NLF8Bb18G1H0CXoT77EgCzfSS+M6Sc4dv7iIiI+JAKGCIiIiHKVeNmWU4Rk07t4HSU4FJ5ELZ9aQoWWz+DkjzzeHJvGHYLdPessohp+D1iW8BVb8EL4+H1y+GGudCml3fyH+3Ad7DtczjjTrMCREREJEipgCEiIhKi1uwqobTSRUa3JKejBI+NH5tVETVVZpVF17Ng5F21qyw6e/dezZPhmnfh+XHw6sVw46cQ38m79wBY8ybYbhhwpfevLSIi4kcqYIiIiISozOxCAIZ1TXA4SZA4tB8+/DUk9YQJf4bOwxq3yqIuWqfC1e/Ai+fCq5fA9Z9AMy/++7JtWDUDOg2BpO7eu66IiIgDtI5QREQkRGVlF9KrXQsSmx+noaT80Lw/QHkRTJ4GaWf6vnjh0a4/THkdirbBjClmYoi3fLca8jeoeaeIiIQEFTBERERCUKWrhhW5Rdo+Ule5S+Drl2D4VGg/wP/3TxsJl/wX8pbD29dDjcs71109AyJjoN/F3rmeiIiIg1TAEBERCUHf7Cim0uUmQ+NTT85VabaOtEqBs+51LkefSXDe32DzHJPHtht3vZpqWPMW9JwITVt7J6OIiIiD1ANDREQkBGVmFxJhwRD1vzi5RX+Hwi2mF0VMnLNZBt8Ipfvgy79C8zYw5g8Nv9aWeVBeCAOu8l4+ERERB6mAISIiEoKysgvo36kVLZtEOx0lsOVvgkV/g/6Xm0kjgeCse6F0Lyz+uyliDLu1YddZPQOaJUH3c7ybT0RExCHaQiIiIhJiyqtcfLOjWNtHTsbtNls1YpvD+D87neYwyzJbSXpfAHPuhTVv1/8a5UVmK8opl0OkilgiIhIaVMAQEREJMSty9+Ny2ypgnMzXL8GOLBj3MDRPdjrND0VEwsX/hZQR8N4tkP15/V6/7l2oqdL0ERERCSkqYIiIiISYzOwCoiMtBqWo/8VxHdxjxqamjoRTf+J0mmOLbmLGqyb1gDeuht3f1P21q2ZAm77Q7hTf5RMREfEzFTBERERCTFZ2IQO7tKZpTKTTUQLXJ78FVwWc/w+zZSNQNW1lmos2TYBXL4XC7JO/pmAL7FppVl8E8tcmIiJSTypgiIiIhJCS8mrW7irR9pET2fQJrH8fRt0DSd2dTnNyLdvDNe8BNrxyERzce+LzV88AK8L0vxAREQkhKmCIiIiEkGU5hbhtyOiW5HSUwFR5ED6+G5J7Q8avnU5Td0nd4aq3oKwAXr0EKkqOfZ7bDavfgG6joUU7/2YUERHxMRUwREREQkhmdiFNoiM4tXMrp6MEpgWPwIFdcOE/ISrG6TT10+l0uOJlyN8AM38C1RU/Pid3ERzYCQOu9H8+ERERH1MBQ0REJIRkZRcyODWBmCj9L/5Hdn4Fy/4Ng2+EzkOcTtMw3cfApOmmUPHezeCu+eHzq2dCbEvodZ4z+URERHxIP92IiIiEiPyDlWzae1DbR46lpho+/LXZVnHOA06naZwBV8C4R2D9B6YZqW2bxytLzWN9J0N0U2czioiI+ECU0wFERETEO5ZuKwRQA89jyZoGe9fAFa9Ck3in0zRexm1Quhcy/wnN25qGpBs/guoybR8REZGQpQKGiIhIiMjMLqRFkyj6dmjpdJTAUrQNvvgr9Dofel/gdBrvGfNHKMuHzx+G5smw9l1olQJdhjudTERExCdUwBAREQkRWdkFDE1LJCpSO0S/Z9vw0Z0QEQUTH3M6jXdFRMCF/zKTST66w3yto34LluV0MhEREZ/QTzgiIiIhYFfxIXILy7V95Ghr3oJtn8OYP0B8R6fTeF9kNFz+EnQYaP484Apn84iIiPiQVmCIiIiEgKzs2v4X3VXA+F55Ecy5FzoNhkE3OJ3Gd2Li4NoPoCgHEro6nUZERMRntAJDREQkBGRmF5AYF0OPNi2cjhI4Pv0dVJTABU9BRKTTaXwrtgW0P8XpFCIiIj6lAoaIiEiQs22brOxChnVLJCJC/Q8A2PYlrHoNRvwa2vZ1Oo2IiIh4gQoYIiIiQS63sJzvSirU/8Kj+hB8dLvZTnHmPU6nERERES9RDwwREZEgl5ldAEBGtySHkwSIhY+b0anXfgDRTZ1OIyIiIl6iFRgiIiJBLjO7kPbxTUhNbOZ0FOftXQdLnoIBV0HXs5xOIyIiIl6kAoaIiEgQc7ttlmYXMrxbIpYV5v0v3DUw61fQJB7GPex0GhEREfEybSEREREJYpv2HqSwrErbRwBWvgC7VsJFz0Kc+oGIiIiEGq3AEBERCWKZ2YUADA/3Bp4lu2D+H6Hr2XDK5U6nERERER9QAUNERCSIZWUXkJrYjI6twrxZ5Se/AbcLzn8Swn0rjYiISIhSAUNERCRIuWrcLNtWxPBw3z6y4UPY+BGcdS8kpDmdRkRERHxEBQwREZEgtXb3AQ5WusgI5+0jFSUw+x5o2x+GT3U6jYiIiPiQmniKiIgEqczsAgCGdQ3jAsZnD8HBPTDlNYiMdjqNiIiI+JBWYIiIiASprOxCerZtQXKLWKejOGPHMljxPAy9BTqe7nQaERER8TEVMERERIJQpauGFblF4Tt9xFUFH/4aWnaE0fc7nUZERET8QFtIREREgtCqHcVUVLvDt/9F5j8hfwNcORNiWzidRkRERPxAKzBERESCUGZ2IREWDA3H/hf7NsKXj0GfydBzotNpRERExE9UwBAREQlCWdmF9OsYT3zTMGtcWZwHr14MTVrCxEedTiMiIiJ+pAKGiIhIkCmvcvFN3v7w639Rmg+vTIbKUrj6XWjRzulEIiIi4kfqgSEiIhJkVubup7rGJqNbktNR/KfiALx2CZTsgmveg/anOJ1IRERE/EwFDBERkSCTmV1IVITF4NTWTkfxj+pDMONK2LsOpsyAlOFOJxIREREHqIAhIiISZLKyCxjYpRXNYsLgf+M11fDW9bB9CVzyX+gxzulEIiIi4hD1wBAREQkiJYeqWbOrhOHhsH3E7YYPpsLmT+C8J6D/pU4nEhEREQepgCEiIhJElucU4bYhI9QbeNo2zLkXvn0DRv8OBt/kdCIRERFxmAoYIiIiQSQzu4DYqAgGdmnldBTf+vJRWP4fGDYVRt7tdBoREREJACpgiIiIBJGs7EIGpyYQGxXpdBTfWfYf+OIvcOpPYNzDYFlOJxIREZEAoAKGiIhIkCgorWTjnoMMD+XtI6vfgE9+A73Ohwv+CRH6UUVEREQM/VQgIiISJJZuKwRCuP/Fpk/g/VshdSRc8jxEhsGUFREREakzFTBERESCRGZ2Ic1jo+jfMd7pKN6XuwTeug7anwJXzoDoJk4nEhERkQCjAoaIiEiQyMouZGhaAlGRIfa/792rYMYUaNUFfvIOxLZwOpGIiIgEoEb9BGRZ1gTLsjZZlrXVsqx7j/F8rGVZb9Q+v8yyrNQjnruv9vFNlmWNP9k1Lcv6n2VZOZZlrar9OLUx2UVERILJ7uJD5BSUhV7/i4Kt8Ool0CQernkf4kLs6xMRERGvafDmUsuyIoFpwFhgJ7DCsqxZtm2vP+K0G4H9tm13tyxrCvAocIVlWX2AKUBfoAMw37KsHrWvOdE177Ft++2GZhYREQlWWdme/hdJDifxopKd8Mpk8/k170N8R2fziIiISEBrzAqMIcBW27a32bZdBcwEJh11ziTgpdrP3wbOsSzLqn18pm3blbZt5wBba69Xl2uKiIiEnczsQlo3i6ZXuxDZXlFWAK9cBBUlcM27kNTd6UQiIiIS4BpTwOgI5B3x5521jx3zHNu2XUAJkHiC157smo9YlvWtZVlPWpYVe6xQlmXdbFnWSsuyVubn59f/q5J62VNSwQerdnH/e2t4YXGO03FEREKSbdtkZRcwvFsiERGW03Ear+KA2TZSvAOunAntBzidSERERIJAMM0nuw/YA8QAzwK/BR46+iTbtp+tfZ5BgwbZ/gwY6mzbZuf+QyzLKWLZtkKW5xaxvbAcgMgIC7dtM6xrIn06tHQ4qYhIaNleWM7ukgpuDYXtI9UVMPMq2LMGprwOqSOcTiQiIiJBojEFjF1A5yP+3Kn2sWOds9OyrCggHig8yWuP+bht29/VPlZpWdaLwN2NyC51YNs22fllLM8pYnlOIctyiviupAKAVs2iGZKawLXDUxmalkCHVk0Z/bcvePjj9bx201DMTiEREfGGzO/7XwR5g8saF7x9PeQugoufg54TnE4kIiIiQaQxBYwVQLplWWmYIsMU4KqjzpkF/BTIAi4FFti2bVuWNQt43bKsv2OaeKYDywHreNe0LKu9bdvf1fbQmAysbUR2OQa322bT3oPfr65YnlNEQWkVAMktYhmalsDQtASGpCWS3qb5j5Yx335OOg9+uJ7PNuxjTJ+2TnwJIiIhKTO7gLYtY+maFOd0lIZzu2HWL2HTbJj4OJxyudOJREREJMg0uIBh27bLsqzbgLlAJPCCbdvrLMt6CFhp2/Ys4HngFcuytgJFmIIEtee9CawHXMBU27ZrAI51zdpbvmZZVjKmyLEKuKWh2cVw1bhZt/sAy3OKWJZTyIrc/ZQcqgagY6umnJmezJC0BIZ2TSQ1sdlJV1X8ZFgKryzdzp9nb+DMHsnERDVqSq+IiODpf1HImT2Sg3d1m23Dp/fD6tfhrP+DoTc7nUhERESCUKN6YNi2PRuYfdRjDxzxeQVw2XFe+wjwSF2uWfv46MZkFVOwWJVXbHpY5BTxVW4RZVU1AKQlxTGxXzuGpCUwJC2BTq2b1fv60ZER3H9eb27430peXbqdG85I8/aXICISdtbtPkBhWRXDg3n7yMInYOl0GHorjPqN02lEREQkSAVTE09phL0HKrjppZWs2VUCQM+2Lbj4tE4M7ZrAkNQE2rRs4pX7nN2zDSPTk3jqsy1cfFpHWjWL8cp1RUTC1bTPtxIXE8mY3kG6NW/5c/D5w3DKFBj/ZwjWVSQiIiLiOBUwwsD63Qe48aUVHDhUzeOXnsI5vduSEOebwoJlWfzuvD5MfGoh/5i/hQcv7OuT+4iIhINvdxbzydo9/PqcdJ/9ve1T374Fs++BnufCpKchQlsLRUREpOH0k0SI+3zjPi77dya2DW/dksFlgzr7/Ifgnu1aMGVIF15dup3s/FKf3ktEJJQ9PncTrZtFc9PIINySt3U+vH8LpIyAS1+EyGinE4mIiEiQUwEjhL2SlcuNL60gNSmO96eOoE+Hln679x1jetAkOpK/zN7gt3uKiISSzOwCFm0pYOrZ3WnRJAjf/Cf1hN4XwpUzINo72xRFREQkvKmAEYJq3DYPfbie33+wjtG92vDmz4fTLt6/Pzwmt4hl6tndmb9hH0u2Fvj13iIiwc62bR6bs4n28U24eliK03EaplVnuOxFaOK/4rmIiIiENhUwQkxZpYufv/IVLyzJ4foRqfznmkHExTrT6uT6Eal0at2UP320nhq37UgGEZFgNG/9XlblFfPrc9JpEh3pdBwRERGRgKACRgjZe6CCy/+TxYKNe3loUl/+cEFfIiOc6/beJDqS+yb2ZuOeg7y5Ms+xHCIiwaTGbfPEp5vomhTHpad3cjqOiIiISMBQASNErN99gMnTlpBbUMbzPx3MtcNTnY4EwLn92zE4tTV/+3QTByuqnY4jIhLwPli1i817S7lzXA+iIvW/aREREREP/WQUAo6eNHJ2rzZOR/qeZ6xqQWkV07/IdjqOiEhAq3K5eXL+Zvp2aMm5/do7HUdEREQkoKiAEeReznJu0khdDejciosGduT5xTnkFZU7HUdEJGDNXLGDvKJD3DO+JxEObgEUERERCUQqYASpGrfNHz9cxwMOThqpj99M6EmEBY/O2eh0FBGRgFRe5eKfn21lSFoCo3okOx1HREREJOCogBGEzKSRlby4JNfxSSN11T6+KTef2Y2Pvv2Or7YXOR1HRCTgvLgkl4LSSn47oSeWpdUXIiIiIkdTASPIHJ40si8gJo3Uxy2jutK2ZSwPfbQBt8aqioh8r6S8mv98mc05vdpwekqC03FEREREApIKGEEkUCeN1FWzmCjuGd+L1XnFzFq92+k4IiIB498LszlY6eLu8T2djiIiIiISsFTACBKBPGmkPi4e2JF+HVvy6JyNHKqqcTqOiIjj9h2o4MUlOVw4oAO92wdeI2YRERGRQKECRhAIhkkjdRURYfH78/rwXUkF/120zek4IiKO+9eCrbhqbO4c28PpKCIiIiIBTQWMABZsk0bqamjXRCb0bcczX2az90CF03FERByzo7CcGct3cMXgzqQkxjkdR0RERCSgqYARoI6cNHLDiLSgmDRSH/ed2wtXjc0Tczc5HUVExDFPzt9MVKTFr85JdzqKiIiISMBTASMA7Sn54aSRBy7oEzSTRuoqJTGO60ak8vbXO1m7q8TpOCIifrdpz0HeX7WLn2ak0rZl8K+uExEREfE1FTACTLBPGqmP20Z3p3WzGP700XpsW2NVRSS8PPHpJprHRnHrqG5ORxEREREJCipgBJhnvswGgnvSSF21bBLNHWN7sCyniLnr9jodR0TEb77esZ956/fy8zO70qpZjNNxRERERIJC6DRVCBF/vbg/pZWusFlOfOXgzrycmctfPtnA6F5tiIlSTU1EQptt2zw+ZxNJzWO4fkSa03FEREREgobeLQaYuNiosCleAERFRnD/eb3ZXljOy1m5TscREfG5xVsLyNpWyG1ndw+p5swiIiIivqYChjjurJ5tGNUjmac+20JRWZXTcUREfMa2bR6fu4mOrZpy5dAuTscRERERCSoqYEhA+N15vSmvquEf8zc7HUVExGfmrN3DtztLuGNsD2KjIp2OIyIiIhJUVMCQgJDetgVXDenCa8t2sGXvQafjiIh4navGzROfbiK9TXMuGtjR6TgiIiIiQUcFDAkYd4ztQbOYSB6ZvcHpKCIiXvfuN7vIzi/jrnE9iYywnI4jIiIiEnRUwJCAkRAXw69Gp/PFpny+3JzvdBwREa+pdNXw1PwtDOjcivF92zodR0RERCQoqYAhAeXajBRSEpvxyMfrcdW4nY4jIuIVry3dwa7iQ/xmfE8sS6svRERERBpCBQwJKLFRkdw3sReb95Yyc0We03FERBqttNLFtM+3MqJ7IiO6JzkdR0RERCRoqYAhAWd833YMTUvgyXmbOVBR7XQcEZFGeWFxDoVlVdw9rqfTUURERESCmgoYEnAsy+L35/ehqLyKaQu2Oh1HRKTB9pdV8dzCbYzr05aBXVo7HUdEREQkqKmAIQGpX8d4LjmtEy8uyWVHYbnTcUREGuSZL7MprXJx93itvhARERFpLBUwJGDdM96MGvzrHI1VFZHgs6ekgpcyc7loYEd6tG3hdBwRERGRoKcChgSsti2bcMuobsxes4flOUVOxxERqZenPtuC27a5Y0wPp6OIiIiIhAQVMCSg3XxmV9rHN+HBWeuo1lhVEQkSOQVlvLkyj6uGdKFzQjOn44iIiIiEBBUwJKA1jYnkDxf0Yf13B3h+cY7TcURE6uTv8zYTExnBbaPTnY4iIiIiEjJUwJCAN6Ffe8b3bcuT8zaTU1DmdBwRkRNat7uED1fv5oYzUkluEet0HBEREZGQoQKGBIWHJvUjJiqC+979Ftu2nY4jInJcT8zdRHzTaG4+s5vTUURERERCigoYEhTatmzC/53bm6XbinhjRZ7TcUREjmlFbhGfb8rnllHdiG8a7XQcERERkZCiAoYEjSmDOzOsawKPzN7AvgMVTscREfkB27Z5bM5G2rSI5bqMVKfjiIiIiIQcFTAkaFiWxV8uPoUql5sHPljndBwRkR/4YlM+K3L388tz0mkaE+l0HBEREZGQowKGBJW0pDhuH9ODOev2MGftd07HCTlllS4u+NdibvzfCorKqpyOIxKwqmvcFJVVsb2wjDU7S8jcWsBjczfRJaEZVwzq7HQ8ERERkZAU5XQAkfq6aWQaH67ezQMfrGN4tyTtM/cS2/5/9u47zIryfOP4916W3pv0qqICAipFUCyxxh4jxhLFqLEHS8wvapoxiSbRxNg1ttiwYS9oNHYBaQqIoCJFqtJ73X1+f8wcPRx32QWB3YX7c13n4px5yzwz56DMM+/7TvCbZ8YxftZiPs3L46ib3+W2U/dkj9b1yzo0s82qsDBYvmYdS1etY8mqtcmfK5M/l65ay5J0+5KVyeei6q1cW1Bk37eesgdV8n1vwMzMzGxLcALDKpzKlfL4+wldOPa29/nr4Alcd3yXsg5pm/D4iOk8+9EsfnlIBw7YZQfOf2QUJ941lN8csRv9+7RFUlmHaLbR1hYUMm7mYoZPWcCIKQv4aPoiFqxYQ0kPM6qSn0edavnUqVaZ2tXyqV2tMs3qVqN21crUqZ58rp1T3rRuNdo1qrl1DszMzMxsO+QEhlVInVvU5ex923HXO5M5pmsLeu/YsKxDqtAmzF7CH54fT9+dG3HBgTtRKU+8+It9+eUTY7j6hU8Y9eUirjt+d2pV9X8yrHxbuaaAD79cyPCpCxg+ZQEffrnom9ES7RvX5KDddqBpnWrfJiCqf5uAqFPt28REtcpew8LMzMysvFGUdBuqAuvevXuMHDmyrMOwLWTlmgIOv+kdBLxyyX6+4NhEy1av45hb3mPZ6nW8fHFfGtWq+k1ZYWFw5ztfcMOrn9KuUU3u+OledGhSuwyjNVvf4hVrGTltwTcJi3EzFrOuMJCgY7M69GjbgF7tGtC9bQMa165acodmZmZmVuYkjYqI7t/Z7gSGVWRDJs3jlHs+4Lz9d+SKH+5a1uFUOBHBxY99xItjZzHw53uzd/uiR7IM+WIeAx79kOWrC7ju+N05bo8WWzlSs8TXS1YxfGoyHeSDKQv49KulREDlSqJLy3r0bNeAnu0asFeb+tSp5vVxzMzMzCqi4hIYHg9uFVqfnRrxk+6tuPvdyRzVpRmdW9Qt65C+ERHlft2IR4dP5/kxs7j80A7FJi8A+uzYiJcG9OUXAz/kksc/YsTUBfz+6I5UzfeoF9tyIoLpC1bywZT5jEhHWEydvwKAGlUqsWfr+hyxezN6tG3AHq3reRSWmZmZ2TbOIzCswlu8Yi0H3/g2TepU5dkL9iG/Utk/AWDestWc/cBIGtaswm2n7lkuL6w+mbWE425/n17tGvDAz3qSl1dysmVdQSHXv/opd70zmS4t63LbKXvSqkGNrRCtbS8igmc/mskbE+cyfMp8vlqyGoB6NSrTvU0yHaRHuwZ0al6HyuXg77qZmZmZbX6eQmLbtMHjZnP+I6O58oe7cu7+O5ZpLLMWreSn93zAzEUrWb2ukAN2acxdp+1VrkYrLF21lmNufZ8Va9bx8oC+NKy1cWsDvDp+Dpc/OYY8iRt/0pUf7NpkC0Vq25v/jp/DOQ+NokmdqvRs15CebevTs11Ddt6hVqmSbGZmZmZW8RWXwPDtK9smHN65KYd2bMI/X/uMqfOWl1kcU+Ytp9+dQ5m7dDUPn92La3+0O299OpcLH/mQNesKy7IO5poAACAASURBVCyubBHBlU+PY9r85dxy8p4bnbwAOKxTU178xb60qFedM/8zkutfnci6gvJxfFZxFRYGN77+Oe0a1eT9X/+AW07eg9N6t2WXprWdvDAzMzMzJzBs2yCJPx3XmSqV8rjy6XGUxciiCbOX0O/OoaxcW8Cj5+xNj7YNOKVXa645thOvT/iKix/7sFxc5D/ywZe8OHY2vzx0F3q2a7DJ/bRpWJOnL+jDST1acdubX3DavcOZu3T1ZozUtjevjJ/DhNlLuPigncvFVDAzMzMzK1/8L0TbZjSpU40rj9iNoZPn88TI6Vt13x9+uZCT/j2M/DzxxLl7r7eY6Om92/LbI3dj8MdzuPSJMRQUlt20rY9nLuaaFz9h/w6NOX8zTLWpVrkSf/1xF64/oQujv1zIkTe/y/ApCzZDpLa9KSgMbnztM3ZsXJOjuzYv63DMzMzMrBxyAsO2KSf1aEWvdg34y0sT+HrJqq2yzyFfzOPUez6gXo3KPHleb3baofZ36pzdtz2/PnxXXhgzi18NGkNhGSQxlq5ay0UDR9OgRhX+eWLXzTokv1/3Vjx74T7UqFKJk+8exr/f+aJMRsFYxfXSuNl8/vUyLjm4A5U8XcTMzMzMiuAEhm1T8vLEdcfvzqp1hfzh+fFbfH+vf/IVZ9w/gpb1q/Pkub03+ESO8w/YkcsO6cDTo2dy1TPjtmoSIyK44ulxTF+4kltO2WOT1r0oyW7N6vD8L/bl0I5NuPbliZz70CgWr1y72fdj256CwuBfr3/GLk1qc+Tuzco6HDMzMzMrp5zAsG1O+8a1uOTgnRn88Rxe+XjOFtvPcx/N5LyHR7Fr09o8fk5vdqhTrcQ2Aw7amYsO3InHRkzn989/vNVGKTw8bBovjZ3N5YfuQo+2m77uRUnqVKvM7afuyW+P3I03Jn7NMbe+x/hZi7fY/mzb8NxHM5k8dzmXHrKzF+s0MzMzs2I5gWHbpJ/3bU/HZnX4/XMfb5FRAAM/+JJLHv+IvdrU55Gze1G/ZpVSt/3loR04d7/2PDzsS6558ZMtnsT4eOZi/vTiBA7cpTHn7td+i+4LkgVVz+7bnsfO2ZtVaws4/vYhPDFi665JYhXHuoJCbvrf53RsVodDOzYt63DMzMzMrBxzAsO2SZUr5fG3H3dh3rLV/HXwxM3a97/f+YKrnhnHAR0a88CZPaldrfJGtZfEFT/clZ/t05b735/KXwdP3GJJjCWr1nLhwNE0rFWFf5zYbave3e7etgEvDehL97b1+b+nxvKrJ8ewck3BVtu/VQxPfziTafNXcOkhHTz6wszMzMw2yAkM22bt3rIuZ/dtz6PDv2TY5Pnfu7+I4B///ZRrX57IkV2acddp3alWudIm9SWJ3x/VkZ/u3Zq73pnMP1/77HvHlysiuOKpscxYuJJbTt6DBhsxSmRzaVSrKg+e2YsBP9iJJ0fN4Ee3v8/7k+axaq0TGQZrCwq5+X+fs3uLuhy82w5lHY6ZmZmZlXP5ZR2A2ZZ06cEdeOXjOVz59DgGX9x3kxMOhYXBNS9+wn+GTOWkHq34y492/95PSpDENcd0Zu264JY3JlG5Uh4DDtr5e/WZ7aFh03h53Byu/OGudN+C616UpFKeuOzQXdijTX0uffwjTr3nA6pUyqNb63r0bt+Qvds3ZI/W9Tb5u7GKa9CoGcxYuJI/HdsZyaMvzMzMzGzDtC0/6rB79+4xcuTIsg7Dytj7k5LHnJ5/wI78+vBdN7r9uoJCrnh6HINGzeDsfdvxmyN326wXW4WFweWDxvD06Jn8+vBdOf+AHb93n+NmLObHdwxh350bcc/p3cvN0Pxlq9cxYsoChk6ez7DJ8/l45mIKA6rk57Fn63rsnZXQqJrvhMa2bPW6Ag68/i2a1K3G0+f3cQLDzMzMzL4haVREdM/d7hEYts3bZ6dGnNi9Jf9+ZzJHdWlGp+Z1S9129boCLnnsIwZ/PIdLD+7AgIN22uwXWnl54voTurKuIPjbKxOpXClZBHNTLV65lgsGjqJRrSr8o1/XcpO8AKhVNZ8Dd92BA3dNpgssWbWWEVMWMGzyfIZNXsDN//ucf73+OVXz89izdf00odGAbk5obHOeGDGdWYtX8bcTujh5YWZmZmal4gSGbRd+c0RH3pg4l18/NZZnL9iH/EolL/+yck0B5z48inc+m8vvjurIWfu222LxVcoT/zyxK2sLCvnzSxOokp/H6b3bbnQ/EcGvB41l9qJVPH5u7416OkpZqFOtMgft1oSDdmsCJMmXbxIaU+bzr/99RrwOVfPz2KtNktDovWNDurSs64RGBbZqbQG3vjmJHm3rs+9Ojco6HDMzMzOrIJzAsO1C3RqVuebYTlzwyGjue38K5+y34WkaS1at5az/jGDUtIX8/cddOLFHqy0eY36lPG46aQ/WPjKa3z83nsqV8ji5Z+uN6uOBIVN5ZfwcrjpiV/ZqU38LRbrl1K1emYM7NuHgjmlCY8Vahk9NEhpDv5jPja9/xj9fg2qV04RGu0xCox5V8r0mcUXx6PAv+WrJam78STePvjAzMzOzUvMaGLbdiAjOeWgU734+l1cv2Y82DWsWWW/+stX0v384E2cv5V8ndeOoLs23apyr1xVw7kOjePuzuVx/QldO2KtlqdqNmb6IE+4cwv4dGnP36d23yQvDRSvWMPybNTQWMGH2EiBJaHRv04ALDtiRPr6jX66tXFPAfte/yY6Na/LYOb3LOhwzMzMzK4eKWwPje92ylHS4pE8lTZJ0RRHlVSU9npZ/IKltVtmV6fZPJR22EX3eLGnZ94nbtk+S+NOxnamcl8eVT4+jqOTdnMWr+Mm/h/H5V8u4+/TuWz15AVA1vxJ3/nQv9tmxEb8aNIbnPppZYpvFK9dy4cDR7FC7Gjf067pNJi8A6tWowqGdmvKHozsx+OK+fPi7Q7jzp3txUo/WTJ2/nP73D+eFMbPKOkzbgIeHTWPu0tVcdsguZR2KmZmZmVUwm5zAkFQJuA34IdAROFlSx5xqZwELI2In4Ebgb2nbjsBJQCfgcOB2SZVK6lNSd6DijYu3cqNp3WpcccSuDPliPk+OnLFe2ZfzV9DvriHMWbyKB87s+c1Ck2WhWuVK3H16d3q1a8BlT4zhpbGzi60bEfzfoDHMWbyKW07Zg3o1yve6F5tT/ZpVOLxzU64+phMvX9yXPVrVZ8BjH/LwsGllHZoVYfnqddz59hf03bkRPduV3aN9zczMzKxi+j4jMHoCkyJickSsAR4Djs2pcyzwQPp+EHCQklvDxwKPRcTqiJgCTEr7K7bPNLlxPfB/3yNmM07u0Zqe7Rrw55c+4eulqwD47KulnHDnEJauWsfAn/di7/YNyzhKqF6lEvf278Eerepx8WMf8t/xc4qsd//7U3l1/Fdc8cNd2bP19pvfq1OtcpJ42mUHfvvsx9z6xudFjrKxsvPg0GnMX76GSw7uUNahmJmZmVkF9H0SGC2A6VmfZ6TbiqwTEeuAxUDDDbTdUJ8XAc9HRPG3ogFJ50gaKWnk3LlzN+qAbPuQlyeuO353Vq0r5OrnxzN2xiJ+ctdQAJ44tzddWtYr4wi/VbNqPvf/rAedW9TlwoGjeXPi1+uVfzR9EdcNnsDBuzXZok9JqSiqV6nEXaftxY/2aMEN//2MP780gcJCJzHKg6Wr1nLXO19wwC6NK+QCs2ZmZmZW9irEsv2SmgP9gFtKqhsR/46I7hHRvXHjxls+OKuQdmxci4sP2pmXx82h351DqVk1nyfP602HJrXLOrTvqJ2OLNilae1vHusKyRM6LnwkWffiH9vwuhcbq3KlPP7Rrytn9GnLve9N4VeDxrKuoLCswyrSkEnzOOgfb/GP/366zY8W+c/7U1m0Yi2XevSFmZmZmW2i75PAmAlkP1uyZbqtyDqS8oG6wPwNtC1u+x7ATsAkSVOBGpImfY/YzThnv/Z0aVmX1g1qMOi8PsU+laQ8qFu9Mg+f1YsdG9fi5w+OZMikeVw+aAxfL13FbafuSd0alcs6xHIlL0/84eiOXHZIB54aPYPzHh7NqrUFZR3WN9YWFPK3VyZy6r0fMH/5Gm55YxKXPv4Ra9aVz0TL97V45VrufncyB+/WhK6tys8IJzMzMzOrWPK/R9sRwM6S2pEkGU4CTsmp8zzQHxgKnAC8EREh6XlgoKR/As2BnYHhgIrqMyLGA00znUpali4MarbJKlfKY9B5faiUJyrllf/RC/VqVOHhs3py8t3DOO2+4RQUBr87qiPdfEFYJEkMOGhn6tWozO+fG0//+4ZzT//u1K5WtsmeafOXM+DRDxkzYzEn92zF747qyP3vT+X6Vz/lqyWrufO0vahbfdtKSN333hSWrFrHJQfvXNahmJmZmVkFtskjMNI1LS4CXgUmAE9ExHhJ10g6Jq12L9AwHS1xGXBF2nY88ATwCfAKcGFEFBTX56bGaFaSKvl5FSJ5kdGwVlUeOXtvOjSpzTFdm3PmPm3LOqRy7/TebbnppG6MmraQk+8exrxlq8sslqdHz+CIm95lyrzl3H7qnlx3fBdqVMnnwgN34p8ndmXE1AX0u3MIsxatLLMYN7dFK9Zw33tTOLxTUzq3qFvW4ZiZmZlZBaZted519+7dY+TIkWUdhtlml/l763UvSu/NiV9z/iOjaF63Og+e1ZOW9WtstX0vXbWW3z37Mc9+NIuebRtw40ndaFGv+nfqvT9pHuc9NIoaVStx/xk96di8zlaLcUu54dVPue2tSQy+uC+7Nq34x2NmZmZmW56kURHRPXd7hVjE08zWJ8nJi4104K478NBZvZi7bDX97hzKpK+XbpX9jv5yIUfc/C4vjJ3NZYd04NFz9i4yeQGwz06NePL83ghx4l1Deffziv0kpQXL13D/+1M4cvdmTl6YmZmZ2ffmBIaZbTd6tG3AE+f2Zm1B0O/OoXw0fdEW21dBYXDbm5Pod+dQCgvhiXP3ZsBBO5c4ZWnXpnV45sI+tKxfnZ/dP4JBo2ZssRi3tLve+YIVawu89oWZmZmZbRZOYJjZdmW3ZnV46vze1KqWzyl3D+P9SfM2+z5mL17JqfcM4/pXP+WI3Zvx8sV92atNg1K3b1a3Ok+c15te7Rtw+ZNjuPl/n1e4x6zOXbqaB4dM49iuzdlph/L3eGIzMzMzq3icwDCz7U6bhjUZdF4fWtWvwc/uH8ErH8/ebH2/On4OP7zpXcbOWMz1J3Th5pO6bdJTRepUq8z9Z/Tk+D1b8M/XPuPKp8extqDiPGb1rre/YPW6AgYc5NEXZmZmZrZ5OIFhZtulJnWq8fi5e9O5RR0ueGQ0j4/48nv1t3JNAVc9M45zHxpFq/o1eGlAX/p1b/W91iqpkp/HP/p15Rc/2InHRkzn7AdGsmz1uu8V59bw1ZJVPDRsGj/aoyXtG9cq63DMzMzMbBvhBIaZbbfq1ajCw2f3Yt+dG/Prp8Zx19tfbFI/E2Yv4Zhb32PgB19y7n7teer8PrRrVHOzxCiJXx66C9cdvzvvTZrHT+4aytdLVm2WvreUO976gnWFwcUefWFmZmZmm5ETGGa2XatRJZ97Tu/OUV2acd3giVw3eEKp15uICO5/fwrH3vY+i1au5aGzenLlEbtRJX/z/6f15J6tuef07kyZt5wf3T5kqz1FZWPNXrySgR98Sb+9WtK64dZ7VK2ZmZmZbfucwDCz7V6V/DxuOmkPTu3VmrvensyVT4+joHDDSYz5y1Zz1gMj+eMLn7DvTo145eK+9N258RaN88Bdd+Dxc3qzel0hx98+hA8mz9+i+9sUt705iSC48MCdyjoUMzMzM9vGOIFhZgZUyhN/Pq4zFx2YrDdx4SOjWb2uoMi673w2l8Nvepf3Js3j6qM7cm//7jSsVXWrxLl7y7o8c0EfGtWuymn3DueFMbO2yn5LY8bCFTw+Yjondm9FqwYefWFmZmZmm5cTGGZmKUlcftgu/PbI3Xhl/BzO/M+I9RbNXLOukGtfnsDp9w2nXvXKPHfhPpyxT7vvtVDnpmjVoAZPn9+Hrq3q8otHP+Tf73xRLh6zeusbkxDy6AszMzMz2yKcwDAzy3F23/bc0K8rwyYv4NS7h7Fw+Romz13G8Xe8z7/fmcypvVrz/EX7sluzOmUWY70aVXjorF4c2aUZ1748kaufH1/itJctadr85Tw5agan9GpN83rVyywOMzMzM9t25Zd1AGZm5dEJe7WkbvXKXDhwNMfe9j7zlq2mSn4ed522F4d1alrW4QFQrXIlbjlpD5rXrcbd705h1uJV3HzSHlSvUmmrx3LLG5PIzxPnH7DjVt+3mZmZmW0fPALDzKwYh3RswoNn9mTh8jV0aVmXwRf3LTfJi4y8PPGbIzty9dEdeX3CV5x89zDmL1u9VWOYMm85T4+ewU/3bkOTOtW26r7NzMzMbPvhERhmZhuwd/uGjPjtwVTNz9vqa11sjDP2aUfTutW5+LEP+fEdQ/jPz3rStlHNrbLvm//3OVXy8zhvf4++MDMzM7MtxyMwzMxKUK1ypXKdvMg4vHNTBv58bxavXMvxdwxh9JcLt/g+J329lGc/mkn/3m1pXHvrPInFzMzMzLZPTmCYmW1D9mpTn6fO70OtqvmccvcwfvXkGB4YMpVR0xawYs26kjvYSP96/XNqVK7EuR59YWZmZmZbmKeQmJltY9o3rsXTF/Th9899zBsTv+bJUTMAkGDHxrXo3LwOnVvUpVPzunRqUYc61Spv0n4mzlnCS+Nmc8EBO9KgZpXNeQhmZmZmZt/hBIaZ2TaoUa2q3H7qXkQEXy1ZzbiZi/l45mLGz1rMsMkLePajWd/UbdOwBp1b1KVz87p0blGHTs3rliohcdPrn1OzSj4/79t+Sx6KmZmZmRngBIaZ2TZNEk3rVqNp3Woc0rHJN9vnLl3N+FmLGT9rCR/PXMzYGYt4aezsb8pb1KtOp3SkRucWdejcvC47ZD1hZPysxQz+eA4DDtqZejU8+sLMzMzMtjwnMMzMtkONa1flgF124IBddvhm26IVa/hk1hI+nrWYj2cmf7424Ssivm2TmX4yfMoC6lTL56x925XREZiZmZnZ9sYJDDMzA6BejSr02akRfXZq9M22ZavXJUmNmYv5eNZixs9cwtufzaUw4PJDO1C3+qatn2FmZmZmtrGcwDAzs2LVqppPz3YN6NmuwTfbVq4pYOr85XRoUrsMIzMzMzOz7Y0TGGZmtlGqV6nEbs3qlHUYZmZmZradySvrAMzMzMzMzMzMSuIEhpmZmZmZmZmVe05gmJmZmZmZmVm55wSGmZmZmZmZmZV7TmCYmZmZmZmZWbnnBIaZmZmZmZmZlXtOYJiZmZmZmZlZuecEhpmZmZmZmZmVe05gmJmZmZmZmVm55wSGmZmZmZmZmZV7TmCYmZmZmZmZWbnnBIaZmZmZmZmZlXtOYJiZmZmZmZlZuecEhpmZmZmZmZmVe05gmJmZmZmZmVm55wSGmZmZmZmZmZV7TmCYmZmZmZmZWbmniCjrGLYYSXOBaWUdh5mZmZmZmZmVWpuIaJy7cZtOYJiZmZmZmZnZtsFTSMzMzMzMzMys3HMCw8zMzMzMzMzKPScwzMzMzMzMzKzcyy/rAMzMzMwkNQT+l35sChQAc9PPKyKiT5kEZmZmZuWGF/E0MzOzckXS1cCyiLihrGMxMzOz8sNTSMzMzKxck7Qs/fMASW9Lek7SZEl/lXSqpOGSxknaMa3XWNJTkkakr33K9gjMzMxsc3ACw8zMzCqSrsB5wG7AaUCHiOgJ3AP8Iq1zE3BjRPQAfpyWmZmZWQXnNTDMzMysIhkREbMBJH0B/DfdPg44MH1/MNBRUqZNHUm1ImLZVo3UzMzMNisnMMzMzKwiWZ31vjDrcyHf/rsmD9g7IlZtzcDMzMxsy/IUEjMzM9vW/Jdvp5MgqVsZxmJmZmabiRMYZmZmtq0ZAHSXNFbSJyRrZpiZmVkF58eompmZmZmZmVm55xEYZmZmZmZmZlbuOYFhZmZmZmZmZuWeExhmZmZmZmZmVu45gWFmZmZmZmZm5Z4TGGZmZmZmZmZW7jmBYWZmZmZmZmblnhMYZmZmZmZmZlbuOYFhZmZmZmZmZuWeExhmZmZmZmZmVu45gWFmZmZmZmZm5Z4TGGZmZmZmZmZW7jmBYWZmZmZmZmblnhMYZmZmtllJOkPSe2Udx8aQ1FrSMkmVyjoWMzMzK5oTGGZmZrYeSa9IuqaI7cdKmiMpvyzi+j4k3ZkmKJZJWiNpbdbnwRHxZUTUioiCso7VzMzMiuYEhpmZmeV6APipJOVsPw14JCLWlUFMGyU3yRIR56UJilrAtcDjmc8R8cOyidLMzMw2hhMYZmZmlutZoCHQN7NBUn3gKODB9HNdSQ9KmitpmqTfSirVvyskHSNpvKRFkt6StFu6/deSBuXUvUnSzVn7vFfSbEkzJf05M+UjnbbyvqQbJc0Hrt6YA5bUVlJkEh9pXH+WNCQdpfGCpIaSHpG0RNIISW2z2u8q6TVJCyR9KunEjdm/mZmZlcwJDDMzM1tPRKwEngBOz9p8IjAxIsakn28B6gLtgf3Tuj8rqW9JHYBHgUuAxsDLwAuSqgCPAUdIqp3WrZTud2Da/D/AOmAnYA/gUODsrO57AZOBJsBfNuaYi3ESyaiTFsCOwFDgfqABMAH4QxpnTeC1NM4d0na3S+q4GWIwMzOzlBMYZmZmVpQHgBMkVUs/n55uyyQWTgKujIilETEV+AfJxX5JfgK8FBGvRcRa4AagOtAnIqYBo4EfpXV/AKyIiGGSmgBHAJdExPKI+Bq4MY0jY1ZE3BIR69IkzPd1f0R8ERGLgcHAFxHxejqF5kmSJAokI1OmRsT96b4/BJ4C+m2GGMzMzCxV4RbhMjMzsy0vIt6TNA84TtIIoCdwfFrcCKgMTMtqMo1kpEJJmme3i4hCSdOz2g4ETiaZqnIK346+aJPuc3bW0hx5wPSsvrPfbw5fZb1fWcTnWlmx9ZK0KKs8H3hoM8djZma2XXMCw8zMzIrzIMnIi12AVyMicwE/D1hLcuH+SbqtNTCzFH3OAnbPfEgXCm2V1fZJ4B+SWpKMxOidbp8OrAYabWAR0SjF/reE6cDbEXFIGe3fzMxsu+ApJGZmZlacB4GDgZ+TTh8BSB81+gTwF0m1JbUBLgMeLkWfTwBHSjpIUmXglySJiSFp33OBt0jWmpgSERPS7bOB/5IkN+pIypO0o6T9N8+hfi8vAh0knSapcvrqkVmc1MzMzDYPJzDMzMysSOnaFkOAmsDzOcW/AJaTLJr5HslUj/tK0eenwE9JFgGdBxwNHB0Ra7KqDSRJnAzMaX46UIVk1MdCYBDQbGOOaUuIiKUkC4qeRDLCZA7wN6BqWcZlZma2rVFEWY22NDMzMzMzMzMrHY/AMDMzMzMzM7NyzwkMMzMzMzMzMyv3nMAwMzMzMzMzs3LPCQwzMzMzMzMzK/ecwDAzMwMkvSXp7LKOw8zMzMyK5gSGmZltUyRNlbRS0rKsV/MttK92kgol3bEl+i8PJHWTNErSivTPbhuo20DSM5KWS5om6ZSc8lPS7cslPSupQWnaSmom6XlJsySFpLYb2P9cSe9lbTs157ewIu1jr7T8aklrc+q0z2p/tKSP0+1DJHXMKqsq6cY0roWSbpdUubTnI6vefWlMO2Vtu0jSSEmrJf2niDYnSpogaamkTyQdl1N+qaQ5kpak/VdNt+8g6dE05sWS3pfUK6vdAelvOvt89C/tMUlqLGlg2vdCSY9klY3P6XedpBeyyitJ+nMa21JJH0qqV9Q5MzOz7ZMTGGZmti06OiJqZb1mbaH9nA4sBH6SuUDc3CTlb4l+S7nvKsBzwMNAfeAB4Ll0e1FuA9YATYBTgTskdUr76gTcBZyWlq8Abi9NW6AQeAX4cQkh/w2YkL0hIh7J/i0AFwCTgdFZ1R7P+b1MTmPeGXgEOA+oB7wAPJ/1nVwBdAc6Ax2APYHflvKYSPexL7BjEccyC/gzcF9ugaQWJN/JZUAd4FfAQEk7pOWHpbEdBLQB2gN/TJvXAkYAewENSL7TlyTVyt53zvl4YCOO6WlgDtAa2AG4IVMQEZ2yvofawHTgyay2fwT6AL3T4zoNWFXEuTEzs+2UExhmZrbdkLR3ehd9kaQxkg7IqbKjpOHpXevnskcIFNGXSBIYvwXWAkdnld0h6Yac+s9Juix931zSU+logSmSBmTVu1rSIEkPS1oCnCGpp6ShadyzJd2anUSQdKikT9O73rdLeltZ02EknZnerV8o6VVJbUp5yg4A8oF/RcTqiLgZEPCDIs5HTZIEw+8iYllEvAc8T3IRCsnF7gsR8U5ELAN+BxwvqXZJbSPiq4i4neTCu0iS+pAkEu4v4Zj6Aw9GRJTi+A8D3o2I9yJiHUmCpAWwf1p+NHBzRCyIiLnAzcCZpTwfmeTULcAvcnccEU9HxLPA/CLiagksiojBkXgJWM63iZD+wL0RMT4iFgJ/As5I+50cEf+MiNkRURAR/waqALuUdDJKOiZJhwKtgF9FxOKIWBsRHxbT3X5AI+CptG194BLg5xExLT2ujyPCCQwzM/uGExhmZrZdSO9av0RyV7sBcDnwlKTGWdVOJ7kAbQasI7kgLc6+JBeSjwFPkFw0ZjxKMipD6b7rA4cCj0nKI7mTP4bkYvgg4JL0rnnGscAgkrv+jwAFwKUkF3y90zYXpH03SuteCTQEPiW5i5057mOBq4DjgcbAu2l8mfIXJV1RzDF2AsbmXOyPTbfn6gCsi4jPsraNyarbKf0MQER8QXInv0Mp2m6QpErArcBFQLGJiTRxsx/wYE7R0ZIWpFMczs9tlvNeJImS4spbSqpL6Y7pUuCdiBhb7MEVbSQwQdIx6bSL44DVJN8N5Jzr9H0TSQ1zO1IyJagKMClr8w6SvkqTazemiQtKcUx7k/z+HpA0NsP1ygAAIABJREFUX9IISftTtP7AUxGxPP28O8nfuROUTH35TNKFJZ8KMzPbnjiBYWZm26Jn09EKiyQ9m277KfByRLwcEYUR8RrJheARWe0eSu/6LicZIXBienFclP7A4PQO90Dg8MwQfpIkQQB9088nAEPTqSw9gMYRcU1ErEmnK9wNnJTV99CIeDaNc2VEjIqIYRGxLiKmkkzFyFwYHgGMT+/YZ5Iuc7L6Og+4LiImpOXXAt0yozAi4qiI+Gsxx1gLWJyzbTHJ8P+i6i7ZQN0N9VVS25IMAD6IiFEl1DudZETFlKxtTwC7kSR3fg78XtLJadnrwP5K1oWoQpIIqgLUSMtfAS5O131omsZBWr7BY5LUCjgX+H0pj/EbEVFAkoQZSJK4GAicm5UMyD3XmffrnU9JdYCHgD9GRKbORKAbSRLvByRTTf6Z1e+GvqeWJIm6N4GmwD9Iphw1ytlvDZK/E//J2twSyCR+2qXlV0s6pPgzYWZm2xsnMMzMbFt0XETUS1+ZxQ3bAP2yEhuLSEZRNMtqNz3r/TSgMsmoh/VIqg70IxkdQUQMBb4ETkk/B8nIjMyF8CmZumkczXPiuIpkTYGi4kBSh3SkxJx0Wsm1WXE1z66f7ntGVvM2wE1Z+1pAMlKgxXfO2nctI1mLIFsdYOkm1N1Q+cbsZz1KFmgdAPympLokCYzs9RyIiE8iYlY6nWIIcBPJxTMRMZEkUXUrMJvknH/Ct+f3L8CHwEfAEOBZkulEX5XimP4FXJOVOCg1SQcDfyeZ4lOFJJl1j75dYDV335n3S7P6qE4yEmhYRFyX2R4Rc9JzUpgmev6Pb9ceKemYVgJTI+LedPrIYyS/zX1y2hxP8jt8O2vbyvTPa9Kk3ViSv0NHYGZmlnICw8zMthfTSUZY1Mt61cwZfdAq631rkovReUX09SOSC7fb06TCHJKEQO40khPSkQ69SOf6p3FMyYmjdkRkX6jlToO4g+TO+M4RUYck4ZGZujCb5O418M3aHC2z2k4nuTufvb/q6cV6ScYDXTJTYVJd0u25PgPylSx8mdE1q+749HMmzvZA1bRdSW03pCdJEuqT9Hu4CeiZfi/fjJ6RtA9JsmdQCf0FWdNCImJQRHSOiIbAH4C2pGtxpBfaF0VEi4hoT7JexaiIKCzFMR0EXJ/1+wEYqmKeVJKjG8nUk5FpomEE8AFwcFq+3rlO338VEfPTc1GVJNkyg2QUSEnnI/PvxZKOaSzf/e0WNaWnqHVIxhZRvzTrlJiZ2XbECQwzM9tePEyy1sFh6boB1dKpAdkX+z+V1DEd4n4NMCgdrp+rP8nTIXYnuZjsRnKXuauk3QHSxQvnAfcAr0bEorTtcGCppF9Lqp7G0llSjw3EXptk6P4ySbsC2es0vATsLum4dFHIC0mG72fcCVypb58GUldSv5JOVuotkvU3Bih5ZOhF6fY3cium0xeeBq6RVDNNGBxLMkUBkhEoR0vqm66pcA3wdEQsLUVbJFUjSXgAVE0/AwwmSSpkvoffk4yK6Jbz3WXWXFhvVIekYyXVV6InyWiO57LK90q/o8bAv4Hn05EZSGqhZEFWSdqbZNrRH0p5PjqQXPxn4oZkUdBn0r7z02OsBGR+r5mnn4wA+mZGXEjag2S6UiYJ8CBwVvpbrkey0Ox/0rqVSZI4K4H+abIl+3wcKKlNekytgL9mzkcpjukZoL6k/uk5O4EkmfZ+Vv8tgQP57kiYL0imXv0m/a3tRjKt6kXMzMwyIsIvv/zyyy+/tpkXMBU4uJiyXiTD1hcAc0ku/lunZW8B15EkGJaQDK9vVEQfLUgWG9y9iLKXgRuyPv+O5C5yv5x6zUlGaMwheQzrsEzMwNXAwzn19yMZgbGM5CLvGuC9rPLDSe6OLyZ5NOlQ4LSs8tOAcelxTQfuyyobDFy1gfO5BzCK5IJ3NLBHVtlVJOuAZD43ILmzv5x0Sk1OX6ek25eTXBQ32Ii2kfsqJt4zss9Nuq0asAg4qIj6j5KMnFiWnuMBOeXvkUyRWECy9kjNnO9lKskjYT8FTs1pu8FjKuL4dsr6fHURx3x1VvlFJAtvLiV5LOwvc/q7jGQqyxKSJ7NUTbfvn/a1Ij3mzKtvVruZafl0kjVVam/E99Q3/a0tI1ljpm9O+ZUk65AUdQ5akKwrsiw9pnPL+r8nfvnll19+la+XIjw6z8zMbFuh5CknM0gupt8s63jMzMzMNhdPITEzM6vg0mkx9dK1DTLrYwwr47DMzMzMNisnMMzMzCq+3sAXJGtuHE3yFJaVG25iZmZmVrF4ComZmZmZmZmZlXsegWFmZmZmZmZm5Z4TGGZmZmZmZmZW7jmBYWZm2w1JUyWtkdQoZ/uHkkJS2828v3aSCiXdsTn7LU8kdZM0StKK9M9uG6jbQNIzkpZLmibplJzyU9LtyyU9K6lBadpKOlDSOEmLJM1P67XIKr9B0ueSlkqaKOn0rLK+kpblvELSj7PqXCppjqQlku5LF0tFUuti2v4yLW8m6XlJs4r6faXH9Hga8zxJj0iqk3Nu35W0WNIMSb/LaX9QejwrJL0pqU1WWdU01iVp7Jdlle0t6TVJCyTNlfSkpGY5xzs5bTtL0o2S8ksTl6SOkkZKWpi+XpfUMSfuPSW9k56vryRd/N1fi5mZ2Xc5gWFmZtubKcDJmQ+SdgdqbGpn2Rd2RTgdWAj8JHPRu7mVsP8tSlIV4DngYaA+8ADwXLq9KLcBa4AmwKnAHZI6pX11Au4CTkvLVwC3l6Yt8AlwWETUA5oDnwPZSaPlJIub1gX6AzdJ6gMQEe9GRK3MCzgKWAa8ksZ1GHAFcBDQBmgP/DFt+2VO292BQuCpdL+FaT/fJENy/Dk9b+2AHdNjuzqrfCDwDtAA2B+4QNIxaVyNgKeB36XlI4HHs9peDeycxnwg8H+SDk/L6gP/Btqm5UuB+7PaPg/sGRF1gM5AV2BAaeICZgEnpGWN0r4eyzRM436F5LtuCOwE/LeY82NmZrYeJzDMzGx78xBJYiGjP/BgdgVJRyoZlbFE0nRJV2eVtU3vpp8l6UvgjaJ2Iknpfn4LrCW5gM6U3SHphpz6z2XukktqLump9O74FEkDsupdLWmQpIclLQHOkNRT0tB0BMJsSbdmJxEkHSrp0/SO+e2S3pZ0dlb5mZImpHfMX82+k1+CA4B84F8RsToibiZ5hOsPijgfNUku5H8XEcsi4j2Si9vT0iqnAi9ExDsRsYzkwvx4SbVLahsRX0XErKzdFZBcGJOW/yEiJkZEYUR8ALxL8uSWovQHBkXE8qzP90bE+IhYCPwJOKOYtqcD70TE1Ky4bgdGFFO/HfBsRCyJiMXAM0CnrPK2wCMRURARXwDvZZUfD4yPiCcjYhVJwqKrpF2z4v5TRCyMiAnA3Zm4I2Jw2m5JRKwAbgX2yTpfX0TEovSjSBIx35zPDcUVEYsiYmokq8SLnO8CuAx4NSIeSX8zS9P4zMzMSuQEhpmZbW+GAXUk7SapEnASyQiCbMtJLkbrAUcC50s6LqfO/sBuwGHF7GdfoCXJ3ecnSC4oMx4lGZUhAEn1gUOBxyTlAS8AY4AWJHf+L0lHAmQcCwxK43uE5CLxUpI73r3TNhekfTdK615Jcsf7U6BPpiNJxwJXkVwQNya5uH80q/xFSVcUc4ydgLGx/iPNxrL+RXhGB2BdRHyWtW1MVt1O6WcguYgmGXHRoRRtM9M5FgErgcuBvxcVsKTqQA9gfBFlNUlGDzyQc4xjsj6PAZpIapjTNpOwym5bktuAoyTVT38DPwYGZ5X/CzhdUmVJu5B8t68XFVeacPkC6JT21ayIuIv6XgD2I+d8KJnOs4Tk0bxdSUZMlCauTPtFwCrgFuDarKK9gQWShkj6WtILkloXE5eZmdl6nMAwM7PtUWYUxiHABGBmdmFEvBUR49I79mNJLuj3z+nj6ohYHhEri9lHf2Bwetd+IHC4pB3SsneBAPqmn08AhqajCHoAjSPimohYExGTSe6en5TV99CIeDaNb2VEjIqIYRGxLr37f1dWvEeQ3Kl/OiLWATcDc7L6Og+4LiImpOXXAt0yozAi4qiI+Gsxx1gLWJyzbTFQu5i6SzZQd0N9ldQ2M52jHkkS57fAxGJivpPkYv7VIsqOJ7lgfzsn7uy4Mu9zj3Ffkikgg4rZb1FGA1WA+emrgPWnzbxI8ttYSXI890ZEZjRHSecLvhv3d74XSV2A3wO/yt4eEQPTKSQdSM7ZV6WMK9O+HsmUnYuAD7OKWpL83bgYaE0ypetRzMzMSsEJDDMz2x49BJxCMqT+wdxCSb2ULIo4V9Jikov8RjnVphfXeXqXvx/J6AgiYijwZbpP0hELj/HtWhynZOqSrEnQPJ0Osii9k30VycVxkfuW1CEdKTEnvWt+bVa8zbPrp/uekdW8DcmaEJl9LSAZ+t+Cki0D6uRsq0OypsLG1t1Qean3ExEL+HYtjvXWB5F0PcmaDifmjBrJ6A88mFOWu+/M+9x99weeSqe/lNYTwGckiYU6JCMoHk5jbUCyVsQ1QDWgFXCYpAuKiSsTW+Z8wXfjXi9mSTuRjPi4OCLeLSrAiPicZHTG7aWMK7vtcpLkx4NZybuVwDMRMSKd+vJHoI+kukXt38zMLJsTGGZmtt2JiGkkd36PIFkIMddAkjUWWkVEXZKLMOV2s4Fd/IjkgvH2NKkwhyQhkDuN5IR0pEMvvl34cTowJSLqZb1qR8QRG9j3HSR3wndO75pflRXvbJK73sA3Ux1aZrWdDpybs7/qETFkA8eXMR7okpkKk+pCEdMzSC7U8yXtnLWta1bd8ennTJztgappu5La5soHdiDrAl7SH4EfAodGRO5oDiS1IlnTIzehtV5c6fuvImJ+VttMwmpjpo8AdAPuSkfyLCP5nWW+5/ZAQUQ8mI6smUGS9MqU556vmiQLgWbW6phdRNzjs+q3IZn28aeIeKiEOPPTvksTV648kkVyMwmxsaz/+93Q3yMzM7P1OIFhZmbbq7OAH2Qt1pitNrAgIlZJ6kk6cmIj9AfuI3kqRbf0tQ/JIou7A0TEhyTTFe4hWdQws2jicGCppF9Lqi6pkqTOknpsYH+1SaZYLEsXcTw/q+wlYHdJx6UjEi4EmmaV3wlcqW+fBlJXUr9SHudbJNMeBih5bOdF6fbvLGyanuengWsk1ZS0D8laHpmL50eAo5U81rQmyR3+p9NFHjfYVtLxknaRlCepMfBP4MN0NAaSriT5Dg/OTjzkOA0Ykq69ke1B4CwljwetRzI95T85dX5E8rSZN3M7lVSNJBEDUDX9nDECODv9nqsD55Bc4EOStFG6FkWepKbAT7LKnwE6S/px2ufvSdYjyUydeRD4bbq+xq7AzzNxK3nE7BvArRFxZxExn50ZMaHkEahXAv8rTVySDpG0R/q7rUPyXSwkmaoFydNOfqTkUayVSRZrfS9dxNTMzGyDnMAwM7PtUvqkhZHFFF9AcrG8lOTC8InS9pteHB5E8mSOOVmvUSRD77NHYQwEDk7/zMRVQPIoz24ko0QySY4NDbG/nOQCfSnJehnfPE4zIuaRjA74O8k6Cx1JHrm5Oi1/BvgbyQKiS4CPSUYqZI5nsKSritppRKwBjiNZT2QRcCZwXLodSVdJyl6U8gKgOvA1yQiU8yNifNrXeJKpOo+k5bXT+iW2Jbm7/0p6/ONInprxo6y215KstzBJ0rL0lXtMRS7AGRGvpOfuTZJpQNOAP+RU6w88VMy0lJV8O6VjYvo540ySJ3rMIFmHpX3aF+kokeNJFmddCHxE8t38OS2fS7Lo51/S8l6sv07KH0impEwjWdPj+vRYAM5O93V11vnInvqyDzBO0nLg5fR1VWniIllY9lGSNTe+IBm5cXg6XYSIeCPt6yWS73InNj5BaGZm2ykV/f9aMzMz2xYpecrJDODUiPjOiAEzMzOz8sojMMzMzLZxkg6TVE9SVb5dH2NYGYdlZmZmtlGcwDAzM9v29SYZzj8POJpkmkdxj381MzMzK5c8hcTMzMzMzMzMyj2PwDAzMzMzMzOzcs8JDDMzM6sQ0seNviBpsaQn021/ljRP0hxJrdMnalQqoZ++kj7dOlGbmZnZ5uIEhpmZWQUmaaqkg0uo85akszfDvg6QNKMU9XpKelnSIkkLJA2X9LPvu3/gBKAJ0DAi+klqDfwS6BgRTSPiy4iolT6KtlgR8W5E7LIZ4inV+S+izYmSJkhaKukTScdtoO4Nkj5P606UdPr3j9rMzKxicgLDzMzMNhtJvYE3gLeBnYCGwPnADzdD922AzyJiXfq5NTA/Ir7eDH1vFZJaAA8DlwF1gF8BAyXtUEyT5SQLr9YF+gM3SeqzNWI1MzMrb5zAMDMzq6AkPURyEf9COnXi/4qo8xegL3BrWufWdPuukl5LR0h8KunErDZHpCMDlkqaKelySTWBwUDztJ9lkpoXEdb1wAMR8beImBeJURGR3f/PJU1K9/18dj/FxSXpj8DvgZ+k+z4XeC0rnv9IaispJOWnbRpIul/SLEkLJT2bbl9vJImk5pKekjRX0hRJA7LKrpb0hKQH0/MxXlL30p7/IrQEFkXE4PTcvESSpNixqMoR8YeImBgRhRHxAfAuyVNlzMzMtjtOYJiZmVVQEXEa8CVwdDp14u9F1PkNyUXvRWmdi9JkxGvAQGAH4CTgdkkd02b3AudGRG2gM/BGRCwnGUUxK+2nVkTMyt6XpBokF9eDiotZ0g+A64ATgWbANOCxtKzYuCLiD8C1wOPpvu/KieeMInb3EFAD6JT2d2MR8eQBLwBjgBbAQcAlkg7LqnZMGmM94Hng1vTcFnn+JY2VdEoxp2AkMEHSMZIqpdNHVgNjiztnWbFWB3oA40uqa2Zmti1yAsPMzGz7cxQwNSLuj4h1EfEh8BTQLy1fC3SUVCciFkbE6FL2W5/k3xazN1DnVOC+iBgdEauBK4HektqWIq5Sk9SMJMFxXnoMayPi7SKq9gAaR8Q1EbEmIiYDd5MkTzLei4iX07U1HgK6bmjfEdElIgYWU1YAPEiSpFmd/nlumiAqyZ0kiZZXS1HXzMxsm+MEhpmZ2TZE0p1ZUzyuKqZaG6BXusjmIkmLSBILTdPyHwNHANMkvZ2ua1EaC4FCkpEVxWlOMuoCgIhYBswnGf1QUlwboxWwICIWllCvDck0lOx9XkWyWGjGnKz3K4BqmWkqGytd8PPvwAFAFWB/4B5J3Upodz3JaJgTIyI2Zd9mZmYV3Sb9z9fMzMzKjfUuZiPiPOC8DdUBpgNvR8QhRXYYMQI4VlJl4CLgCZKEwAYvnCNihaShJAmQN4upNoskaQB8M22kITCzpLg20nSggaR6EbGohHpTImLnTdzPxiYTugHvRMTI9PMISR8ABwMfFdUgXf/jh8D+EbFkE+M0MzOr8DwCw8zMrGL7Cmi/kXVeBDpIOk1S5fTVQ9JukqpIOlVS3YhYCywhGVWR6aehpLob2Nf/AWdI+pWkhgCSukp6LC1/FPiZpG6SqpKsa/FBREzdUFylPx2JiJhNsujo7ZLqp33tV0TV4cBSSb+WVD1dl6KzpB6l3FVpzn+2EUDfzIgLSXuQLLJa5BoYkq4ETgEOjoj5G7EfMzOzbY4TGGZmZhXbdcBv0+kPlxdT5ybghPRJHDdHxFLgUJJ1HmaRTJH4G1A1rX8aMFXSEpLRHKcCRMREkgTE5HR/33kKSUQMAX6QviZLWgD8G3g5LX8d+B3J2hazSZ6+cVJaVlJcG+s0kvU8JgJfA5cUEW8Bydob3YApwDzgHpLHlpbGd85/+qSSU4uqnK7DcTUwSNJSkvNwbUT8N217qqTsRTqvJXnSyaRSTA0yMzPbpsnTKM3MzMzMzMysvPMIDDMzMzMzMzMr95zAMDMzMzMzM7NyzwkMMzMzMzMzMyv3nMAwMzMzMzMzs3LPCQwzM7MyIukASTPKOg4zMzOzisAJDDMzs+2ApKmSVmY9ivO/G6h7g6TPJS2VNFHS6TnlIWl5Vl/3FNFHFUkTshM0khpJel/S/PSxo0Ml7ZPTrr2kF9N9z5P096yyZTmvAkm3ZO1vUHqcIemAnH4vlTRZ0hJJsyTdKCk/LdtB0qPp9sVpjL1y2p8iaVp63M9KapBV9rCk2Wnfn0k6O+c8FBvXhs5Xuv0HkkanfU+WdM5GxPWWpFVZ5+vTovZdGkr8Lf3u5qfvlVV+tKSP0/0MkdRxU/dlZmZWHCcwzMzMth9HR0St9HXoBuotB44G6gL9gZsk9cmp0zWrr7O/0wP8Cpibs20ZcCbQGKgP/A14ISuRUAV4DXgDaAq0BB7ONM7aX620fCXwZFb/7wE/BeYUEc/zwJ4RUQfoDHQFBqRltYARwF5AA+AB4CVJtdK4OgF3AacBTYAVwO1ZfV8HtE37Pgb4s6S9ShlXxnfOl6TKwDPpvuv+P3t3Hl9XWS18/PckHemUUEqBpk0RiqXM2JZBQQVlUAQRZPKqKIoT93r1Xr1yHV5fFO/rdcCLMioqIIjKdUBBcUYQoRRoS1uoVKaWpunc0rlNnvePZ4eGkOG0Oefsk5zf9/PJZyf77P3slbT0w1lZz1rAucDXQwiHFRgXwCXtfm6v7Ob5PbkYeCvp53Yo6e/HB7I4JgG3AB8E6oBfAne0/blKklQsJjAkSeog+235pSGE+SGE1SGE74UQhnRx7X+EEG7vcO5/QghXZp+/J/vN+gvZb9A/0M1zYwhh/3Zffz+E8MV2X58WQpiVVS/cH0I4tPff7cvFGP9PjPGJGGNrjPFB4F7gmELvDyHsS3rD/l8d1t0cY1wQY2wFAtBCSmS0VQ1cCCyJMX49xrghu35OF485C1iWxUaMcWuM8RsxxvuydTt+T/+IMa5pCxFoBfbPXnsqe2ZTjLElxng9MAhoe8P/DuCXMca/xBjXA58F3hZCGJHdPy/GuKXtUdnHfoXE1d3PK/u5jARujslDwONAW3VDt3H1JITw3uzv5uoQwt0hhMZuLn838LUY4+IY4/PA10h/XgAnA/fGGO+LMW4nJabGAa8tJA5JkgplAkOSpM69g/TGbD/gAOAzXVx3G/CmtjeNIYRa4Bzg1uz1ZcBppDei7wGuCCEcubPBhBCOAL5L+q33aNJv3u8IIQzOXr86hNDxt+8d3RJCWB5C+G3bb/ELeO5QYBowr8NLfwkhLA0h/DSEMLHDa98E/pNUIdHZmnOAzaSqiO/EGJdlLx0NPBNC+HVI20f+HEI4pIvQ3g3cFGOMhXwf2XMvCCGsA1aQKgmu6+K6w0kJjIXZqYOA2W2vxxj/AWwl/b1ou+fqEMJG4AmgCbir0Ljo4ucVY2wGfgi8J4RQG0I4BmgkVXQUFBfwX9nP8q/tt6+EEM7Invk2UkXMvdmzuvKSZ2WfH9Tu69Dh80CqdJEkqWhMYEiS1LlvxRgXxRhXAZcD53d2UYzxWeAR4Mzs1AnAxhjjA9nrd2a//Y8xxnuA3wLH7UI8FwPXxRgfzKoEbgS2kN70E2P8cIzxw93c/w5gIukN8J+Au0MIdQU891rSm9W72517bbbWZGAJ8Kt220DOBGpjjD/rasEY46GkhM4F7HgzDmnLyHnAlcA+wJ3AL7KtJS/KKgVeS9rqUbAY463ZNo8Dsu+rueM1IYSRwM3A/40xrs1ODwfWdrh0LfBipUP2sx9B+rP9KenPpkcF/Lx+CHwuW+9e4NMxxkUFxvUfwCtI1RDXk7br7Je99kHgv2KMj2dVE18CDu+mCqPjs9YCw7M+GL8HXhtSU9pBpMTIIGC37r97SZJ2jgkMSZI6t6jd58+S3lCTVQe0NUV8R/b6rexIcFzAjuoLQginhhAeCCGsCiGsAd4E7LEL8TQC/5ZtH1mTrTW+La6exBj/GmPcFGPcGGP8L2ANPSRSQghfIf0W/Zz2lQ7ZloWt2ZaMjwL7AgeGEIYB/82O3hLdxbM5xvhD4FPtqkE2AffFGH8dY9wKfJVUbXJgh9vfmV33dAHfemfPfpJUUfKSipWs2uSXwAPZz6jNelLCpb2RwAsd1m3Jtoo0AB/qKY6efl4hhMmkCp93kRICBwGfDCG8uZC4smTXCzHGLVnC66+kv3+Q/j79T7u/S6tIVRPjQgj/2e7v+LVdPGsksD5LzD1Bqoj5Fqn6ZA9gPuCEHUlSUdlcSZKkzo1v9/kEUqUBMcZTO7n2J8DXQggNpEqMYwCy7R3/S3oD+osY47YQws95abl9ext56W+t92LHm8BFwOUxxst37dt5mdhNHIQQ/i9wKvDaGOO6AteaRKrMuDcbUDEIGBVCWAocHWN8ppN7B5KqBGYDc4BXd3JNR+8C/l8B13VnAFmfCnjxz+rnpJ93xz4l80hbTtqufQUwGPh7IWt3o9ufFyl59PcYY1v1y4IQwp2kP5c7dyGu9n/mbX+fbunkuvtJFRnttT1rRvb1YbTbVhRjvB24PYujDriI1BhVkqSisQJDkqTOfSSE0BDSWMpPAz/q6sIY43Lgz8D3gKdjjI9nLw0ivaFcDmwPIZwKdDf9YxZwQdbv4BRe2gTx28AHQwhHhWRYCOHNhTRsDCFMCCG8OqRRnUNCCJ8g/Zb8r11cfympkuQNMcaVHV47KIRweBbjcFIzx+dJzSXnkhI/h2cf7yNt0zgcWBRCODqE8JosjqEhhP8gTc94MFv+B8DRIYQ3ZL1E/pXUr+Lxds8/lrQlov30kbbXBocdzVbbvteQvfa+EMKe2edTgEuBP2RfDyS9+d4EvDtrMtreLcBbQgjHZVUTlwE/jTG+ENII1vNCCMOzn8nJpGqcPxQQV7c/L+BRYFJIo1RDtv3jNFKip6e46kIIJ2fPGpBVCx0P/Ca791rg0pAmmRBCGBVCeHvHn2k7NwEfDyGMCyHsA/wb8P123+Orsu9/DGm7yh1ZZYYkSUVjAkOSpM7dSupX8RTwD+CL3V/OrcAbaLd9JMb4Aml7wI/70l1lAAAgAElEQVSB1aSkwB3drPFR0njKNaSeFT9vt9ZM4P2kMv3VpAaTF7a9HkK4tl25f0cjgGuy+54HTgFObUtOhBDeEUJo36TzS6Sqk4XtthL8Z/baWFIyZx3pZzMROC3GuC3GuD3GuLTtg7QtoTX7uoWUzLkKWJnF8SbgzTHGtuqWBaRpHNdmsZ4BnJ5tJ2nzbrI36Z18nwtISYhxpJ4dm0hbJSBVdjwWQthAarB5F6lXA8CxpMTAScCadt/zcVlc80g9I24hNWUdAbT1G4mk7SKLs5i/CvxrjLH9n3OncfX088qacr6X1BNkHXAPqaLnOwXENZD0d3Y5KQn0z8BbY4x/z+79GWlayG0hNTadS6rs6Mp1pO01j2XX3slLm6D+D+nv7YLs5/D+btaSJGmXhJ1o3i1JUlUIITwDvC/G+Pu8Y5EkSVJiBYYkSZIkSap4JjAkSZIkSVLFcwuJJEmSJEmqeFZgSJIkSZKkijcg7wBKaY899ogTJ07MOwxJkiRJklSghx9+eEWMcUzH8/06gTFx4kRmzpyZdxiSJEmSJKlAIYRnOzvvFhJJkiRJklTxTGBIkiRJkqSKZwJDkiRJkiRVPBMYkiRJkiSp4pnAkCRJkiRJFa+gBEYI4ZQQwoIQwsIQwqc6eX1wCOFH2esPhhAmtnvt0uz8ghDCyT2tGUL4fgjh6RDCrOzj8Ox8CCFcmV0/J4RwZG++cUmSJEmS1Hf0mMAIIdQCVwGnAlOA80MIUzpcdhGwOsa4P3AF8OXs3inAecBBwCnA1SGE2gLW/ESM8fDsY1Z27lRgUvZxMXDNrnzDkiRJkiSp7ymkAmM6sDDG+FSMcStwG3BGh2vOAG7MPr8dODGEELLzt8UYt8QYnwYWZusVsmZHZwA3xeQBoC6EsHcB8UuSJEmSpD6ukATGOGBRu68XZ+c6vSbGuB1YC4zu5t6e1rw82yZyRQhh8E7EQQjh4hDCzBDCzOXLlxfw7UmSJEmSpEpXiU08LwUmA9OA3YH/2JmbY4zXxxinxhinjhkzphTxSZIkSZKkMiskgfE8ML7d1w3ZuU6vCSEMAEYBK7u5t8s1Y4xN2TaRLcD3SNtNCo1DkiRJkiT1Q4UkMB4CJoUQ9g0hDCI15byjwzV3AO/OPj8b+GOMMWbnz8umlOxLasA5o7s12/paZD003grMbfeMd2XTSI4G1sYYm3bpu5YkSZIkSX3KgJ4uiDFuDyFcAtwN1ALfjTHOCyFcBsyMMd4B3ADcHEJYCKwiJSTIrvsxMB/YDnwkxtgC0Nma2SNvCSGMAQIwC/hgdv4u4E2kRqAbgff0+ruXJEmSJEl9QkiFEv3T1KlT48yZM/MOQ5IkSZIkFSiE8HCMcWrH85XYxFOSJEmSJOklTGBIkiRJkqSKZwJDkiRJkvqSftwGQOqOCQxJkiRJ6ivWNcHVx8AfvpB3JFLZ9TiFRJIkSZJUAV5YCjeeBisXwm6j845GKjsrMCRJkiSp0q1fBje+JVVg7HUIrHk274iksjOBIUmSJEmVbP3ylLxYuxje8RM44BRY9zy0bMs7MqmsTGBIkiRJUqXasAJuOh1WPwsX/BgmvhrqGiG2poSGVEVMYEiSJElSJdqwEm46A1Y9BRfcBvsel87XN6aj20hUZUxgSJIkSVKl2bgKbj4DVjwJ5/8QXvG6Ha/VZQmM1SYwVF2cQiJJkiRJlWTTarj5rbB8QUpe7HfCS18fOQ5CrRUYqjpWYEiSJElSpdi0Bm4+E5Y9DufeAvu/4eXX1A6AUeOswFDVMYEhSZIkSZVg81r4wdtg6Vw452Y44KSur61rhDXPlS82qQKYwJAkSZKkvG1eBz84C5pmwzk3witP6f76+ka3kKjqmMCQJEmSpDxteQFuORuWPApv/z5MfnPP99RNhPXNsG1TqaOTKoYJDEmSJEnKy5b1cMs5sHgmnHUDHPiWwu57cZSq20hUPUxgSJIkSao+K56Ee78OM76dtm/kYesGuPVcWPQAnPVtOOithd9bNyEdbeSpKuIYVUmSJEnVYcWTMO/nMO9nsGzejvO//zwcfgFMvxj2mFSeWLZuTMmL5+6Ht30bDj5r5+6va6vAMIGh6mECQ5IkSVL/tfzvMP/nKXHRlrQYfzSc8mWYcjq8sBRmXA8Pfz8d9zsBjvog7P9GqClRwfq2TXDb+fDMfXDmdXDI2Tu/xvCxUDvYBIaqigkMSZIkSf3L8gUpYTH/57BsPhBgQrukxch9dlw7ch8481p44xdSEmPmDXDrOVC/b6rIOOIdMGRU8WLbthluuwCeugfeeg0cdu6urVNTk7aRuIVEVSTEGPOOoWSmTp0aZ86cmXcYkiRJkkqt06TFMamvxIGnw8i9C1unZRs8fgc8eH3qTTFwGBx2Hhz1ARjzyt7FuH0L3PYOWPg7OOMqOOKferfeD86CDcvhA3/p3TpShQkhPBxjnNrxvBUYkiRJkvqmZU/s2B6y/HFeTFqc+t87l7Ror3Zg6kdx8FmwZFbaVvLoD1Jlxitel7aXTDoJamp3bt3tW+BH70zJi7dc2fvkBaQKjMX+wlbVwwSGJEmSpL5j2eM7Ki2WPwEEaDwWTv1KGkG6K0mLruxzOLz1anjjZWl7yUM3wA/PSw00p1+ckhBD63peZ/tW+MmF8OTdcNoV8Kp3Fye+ukbYvAY2ry3uNhepQpnAkCRJklTZuktaTDkdRuxV2ucP2wOO/3d49UfhiV+l7SW//TT86XI49Ny0vWTPAzu/t2Ub3P4eWHAXvOmrMPW9xYurvm0SyXOw1yHFW1eqUCYwJEmSJFWu3/wnPHAVKWnx6pQEOPAtpU9adKZ2IBx0ZvpomgMzroNZt8LD34N9j0/bSw44Zcf2kpZtcPt7U9Lj1K/A9PcXN562UaqrnzWBoapgAkOSJElS5Zr3s9R74szrYcTYvKPZYe9DUyPON1wGj9wID30nTRepmwDT3geHXQB3/XtqCHryf8FRFxc/hvqJ6egoVVWJEg02liRJkqRe2rgKXlgC+51YWcmL9oaNhuM+Dh+dA+fcBKPGw+8+B1+dlLa8nPRFOObDpXn20HoYNMJRqqoaVmBIkiRJqkzN89Jx7JR84yhE7QCYckb6WPoYzPxeinva+0r3zBBSxYcVGKoSJjAkSZIkVaYXExgH5xvHztrrEDjt6+V5Vn0jrHq6PM+ScuYWEkmSJEmVqXku7DYahlfo9pFKUNeYppDEmHckUsmZwJAkSZJUmZbNh7EHpa0S6lx9I2zbABtX5h2JVHImMCRJkiRVntYWWPZ439s+Um7tR6lK/ZwJDEmSJEmVZ/UzsG1jqsBQ1+qzBMaaZ3INQyoHExiSJEmSKk/z3HQ0gdG9ugnpaAWGqoAJDEmSJEmVp3kehBoYMznvSCrb4BEwdHdHqaoqmMCQJEmSVHma58Hu+8HAoXlHUvnqs0kkUj9nAkOSJElS5Wme6/aRQtU1uoVEVcEEhiRJkqTKsuWF1MTTCSSFqW+EtYugtTXvSKSSMoEhSZIkqbIseyIdrcAoTN0EaNkKLzTlHYlUUiYwJEmSJFUWJ5DsnLqJ6WgjT/VzJjAkSZIkVZbmeTBoxI4RoepefWM62shT/ZwJDEmSJEmVpXleqr4IIe9I+oZR49PRRp7q50xgSJIkSaocMe5IYKgwA4fAiL3dQqJ+r6AERgjhlBDCghDCwhDCpzp5fXAI4UfZ6w+GECa2e+3S7PyCEMLJO7HmlSGE9e2+vjCEsDyEMCv7eN/OfrOSJEmSKtzaxbBlrQmMneUoVVWBHhMYIYRa4CrgVGAKcH4IYUqHyy4CVscY9weuAL6c3TsFOA84CDgFuDqEUNvTmiGEqUB9J+H8KMZ4ePbxnZ37ViVJkiRVvOZ56WgCY+fUTbACQ/1eIRUY04GFMcanYoxbgduAMzpccwZwY/b57cCJIYSQnb8txrglxvg0sDBbr8s1s+TGV4BP9u5bkyRJktTntE0g2fPAfOPoa+obYd3z0LIt70ikkikkgTEOWNTu68XZuU6viTFuB9YCo7u5t7s1LwHuiDF2NsT4rBDCnBDC7SGE8Z0FG0K4OIQwM4Qwc/ny5QV8e5IkSZIqxrL5qZpgyKi8I+lb6hohtqYtOFI/VVFNPEMI+wBvB77Zycu/BCbGGA8FfseOio+XiDFeH2OcGmOcOmbMmNIFK0mSJKn4mufB2IPzjqLveXGUqttI1H8VksB4Hmhf7dCQnev0mhDCAGAUsLKbe7s6fwSwP7AwhPAMsFsIYSFAjHFljHFLdv13gFcVELskSZKkvmLbZljxpP0vdkVdlsCwkaf6sUISGA8Bk0II+4YQBpGact7R4Zo7gHdnn58N/DHGGLPz52VTSvYFJgEzulozxnhnjHGvGOPEGONEYGPWGJQQwt7tnnc68PiufMOSJEmSKtSKBRBbTGDsipHjINRagaF+bUBPF8QYt4cQLgHuBmqB78YY54UQLgNmxhjvAG4Abs6qJVaREhJk1/0YmA9sBz4SY2wB6GzNHkL5lxDC6dk6q4ALd/q7lSRJklS5XpxA4haSnVY7AEaNswJD/VqPCQyAGONdwF0dzn2u3eebSb0rOrv3cuDyQtbs5Jrh7T6/FLi0kHglSZIk9UHN82DAENj9FXlH0jfVNVqBoX6topp4SpIkSapizXNhzGSoqc07kr6pvhHWPJd3FFLJmMCQJEmSVBmcQNI7dRNhfTNs25R3JFJJmMCQJEmSlL/1y2DDcht49saLo1StwlD/ZAJDkiRJUv5ebOBpAmOX1U1IRxt5qp8ygSFJkiQpfyYweq+urQLDBIb6JxMYkiRJkvLXPA+G7wXD9sg7kr5r+FioHWwCQ/2WCQxJkiRJ+Wuea/VFb9XUpG0kbiFRP2UCQ5IkSVK+WrbD8idMYBRDfaMVGOq3TGBIkiRJytfKhdCy1QRGMdQ1WoGhfssEhiRJkqR8LbOBZ9HUTYDNa2Dz2rwjkYrOBIYkSZKkfDXPg5oBsMcBeUfS99Vnk0iswlA/ZAJDkiRJUr6a56XkxYDBeUfS9704SvW5fOOQSsAEhiRJkqR8Nc9z+0ix1E9MRxt5qh8ygSFJkiQpP5vWwNpFJjCKZWg9DBrhFhL1SyYwJEmSJOVn2fx0HHtwvnH0FyGkRp5WYKgfMoEhSZIkKT/NTiApunpHqap/MoEhSZIkKT/Nc2FIHYzYO+9I+o+6xlSBEWPekUhFZQJDkiRJUn6a56ftIyHkHUn/Ud8I2zbCxpV5RyIVlQkMSZIkSflobU09MNw+Ulxto1TdRqJ+xgSGJEmSpHyseRa2rjeBUWz1WQJjzTO5hiEVmwkMSZIkSfl4sYGnE0iKqm5COlqBoX7GBIYkSZKkfDTPAwLsOTnvSPqXwSNg6O6OUlW/YwJDkiRJUj6a58Lur4BBw/KOpP9xlKr6IRMYkiRJkvLRPM/+F6VS1whrnss7CqmoTGBIkiRJKr+tG2DVU/a/KJX6Rli7KE16kfoJExiSJEmSym/5E0CEsVPyjqR/qpsALVvhhaa8I5GKxgSGJEmSpPJ7cQKJW0hKom5iOtrIU/2ICQxJkiRJ5dc8DwYO2/FGW8VV35iONvJUP2ICQ5IkSVL5Nc9L20dqfEtSEqPGp6ONPNWP+K+FJEmSpPKKMY1QdftI6QwcAiP2dguJ+hUTGJIkSZLK64Um2LTaCSSlVtfoFhL1KyYwJEmSJJWXDTzLo26CFRjqV0xgSJIkSSqv5rnpuKcjVEuqvhHWPQ8t2/KORCoKExiSJEmSyqt5PoxsgKF1eUfSv9U1QmyFtYvyjkQqChMYkiRJksqreZ7bR8qhbZSqk0jUT5jAkCRJklQ+27fCigUmMMqhLktg2MhT/YQJDEmSJEnls+Lv0LrdBEY5jBwHodZGnuo3TGBIkiRJKp8XJ5A4QrXkagfAqHFWYKjfMIEhSZIkqXya50LtIBi9f96RVIe6Risw1G+YwJAkSZJUPs3zYMzkVB2g0qtvtAJD/YYJDEmSJEnl0zzP7SPlVDcRNiyDbZvyjkTqNRMYkiRJkspjw0pYvxTGTsk7kurhKFX1IyYwJEmSJJXHsrYGnk4gKZu6CenoNhL1AwUlMEIIp4QQFoQQFoYQPtXJ64NDCD/KXn8whDCx3WuXZucXhBBO3ok1rwwhrC/kGZIkSZL6ACeQlF9dWwWGCQz1fT0mMEIItcBVwKnAFOD8EELHmq+LgNUxxv2BK4AvZ/dOAc4DDgJOAa4OIdT2tGYIYSpQX8gzJEmSJPURzXNh2BgYvmfekVSP4WOhdjCsfibvSKReK6QCYzqwMMb4VIxxK3AbcEaHa84Absw+vx04MYQQsvO3xRi3xBifBhZm63W5Zpbc+ArwyQKfIUmSJKkvaJ7n9pFyq6lJ20jsgaF+oJAExjhgUbuvF2fnOr0mxrgdWAuM7ube7ta8BLgjxthU4DNeIoRwcQhhZghh5vLlywv49iRJkiSVXGsLLHvc7SN5qG90C4n6hYpq4hlC2Ad4O/DNXV0jxnh9jHFqjHHqmDFjihecJEmSpF236inYvtkKjDzUNdrEU/1CIQmM54Hx7b5uyM51ek0IYQAwCljZzb1dnT8C2B9YGEJ4BtgthLCwh2dIkiRJqnTNc9PRBEb51U2AzWtg89q8I5F6pZAExkPApBDCviGEQaSmnHd0uOYO4N3Z52cDf4wxxuz8edkEkX2BScCMrtaMMd4ZY9wrxjgxxjgR2Jg17ezuGZIkSZIqXfN8CLWwxyvzjqT61GeTSKzCUB83oKcLYozbQwiXAHcDtcB3Y4zzQgiXATNjjHcANwA3Z9USq0gJCbLrfgzMB7YDH4kxtgB0tmYPoXT6DEmSJEl9QPM8GL0/DBySdyTVp/0o1b0PzTcWqRd6TGAAxBjvAu7qcO5z7T7fTOpd0dm9lwOXF7JmJ9cML+QZkiRJkipc81wY96q8o6hO9RPT0Ukk6uMqqomnJEmSpH5o87r023/7X+RjaD0MGuEWEvV5JjAkSZIkldayx9PREar5CCE18nSUqvo4ExiSJEmSSssJJPmrd5Sq+j4TGJIkSZJKq3keDB4FoxryjqR61TWmCgwHOaoPM4EhSZIkVYNffwpuOSefN7DL5qfqixDK/2wl9Y2wbSNsWJF3JNIuM4EhSZIk9XernoIZ18OTd8Pf7y7vs2NMFRhuH8nXi6NUnUSivssEhiRJktTf3fcNqBkAoybAH78Ara3le/baRbBlHYydUr5n6uXq2xIYz+QahtQbJjAkSZKk/mzt8zDrVjjynXDiZ1NDzfk/K9/zm+eloxNI8lU3IR1t5Kk+zASGJEmS1J/dfyUQ4dUfhYPPgjEHwp++BC3by/P8tgkkex5Ynuepc4NHwNDdHaWqPs0EhiRJkrQzYoTtW/OOojDrl8HD34dDz0u/ga+phRM+DSsXwpzbyhND8zyon5jeQCtfjlJVH2cCQ5IkSdoZv/88XDUdtm3KO5Ke/e1b0LIVXvOxHecmnwb7HAF//jJs31L6GJrnuX2kUtQ12sRTfZoJDEmSJGlnPP0XWP00PHB13pF0b+MqeOgGOOhtsMf+O86HACd8BtY+B4/cVNoYtm1K1R5OIKkM9Y2pqWo5m7hKRWQCQ5IkSSpUy7ZUURBq4N4rYP3yvCPq2oPXwtb1cNy/vfy1/U6ECcfCX74CWzeWLoblCyC2msCoFHWNqSLnhaa8I5F2iQkMSZIkqVDLHoeWLXD8J2HbRrjny3lH1LnNa1MCY/JpnY8vDSFNJFnfDA99u3RxOIGkstS1jVK1D4b6JhMYkiRJUqGaZqfjIW+Hqe+Bh78HK57MN6bOPPSdlMQ4/t+7vqbxWNj/DXDfFbB5XWniaJ4HA4amJp7KX32WwLCRp/ooExiSJElSoZpmwaARsPsr4LWfSm/Of//5vKN6qa0b4G9Xwf5vTM06u3PCZ2DT6tL182iem8an1tSWZn3tnFHj09EKDPVRJjAkSZKkQi2ZBXsfCjU1MHwMvOZf4YlfwbP35x3ZDg/fCBtXwvGf6PnafY6AA98C938rNf0sphhTAsP+F5Vj4BAYsbeTSNRnmcCQJEmSCtGyPb0h3/vwHeeO/jCM2Ad++5n0hj1v2zbD/VfCxONgwlGF3fP6T6dmn/ddUdxY1i9LiRT7X1SWuka3kKjPMoEhSZIkFWLFAti+GfZpl8AYtFvahvH8wzDvp/nF1mbWLWnCRHe9Lzra80A49ByY8W14YWnxYmmem45WYFSWugluIVGfZQJDkiRJKsSSWem492EvPX/YeTD2EPj9/4XtW8ofV5uWbXDfN6BhGuz72p2793WfgtZt8JevFi+eFyeQmMCoKPWNsO759PdF6mNMYEiSJEmFaJoNA4fB6P1fer6mFk66LP1We0YJR5L2ZM6PYe1zqfdFCDt37+6vgCP+CR7+fvG2Fyybn7bX7LZ7cdZTcdQ1QmyFtYvyjkTaaSYwJEmSpEI0zYK9Dul8osZ+J6SRpH/5SvGbYRaitQXu/VqKb9JJu7bG8Z+EUAP3/HdxYrKBZ2VylKr6MBMYkiRJUk9aW2DpYy/tf9HRGy+DLetSIqHc5v0MVv1j16ov2owaB9Mugtm3woonexdPyzZYvgDGTundOiq+uiyB4SQS9UEmMCRJkqSerHgStm186QSSjsYeBIdfADOuh9XPlC00WltT0mSPV8Lkt/Rurdd8HAYMhT99qXfrrFwILVudQFKJRo6DUGsjT/VJJjAkSZKknjR10cCzo9d/GmoGwB8uK31Mbf7+69Rv4vh/h5pe/u/98DFw9AfTRJWlj+36OjbwrFy1A1K1jVtI1AeZwJAkSZJ60jQ7VSbscUD3143cB465BOb+Lyx+uPRxxZj6btTvCwe9rThrHvvPMGQU/PHyXV+jeS7UDITRk4oTk4qrrrH8FRgxwl2fhJ9+IDW7bZoNLdvLG4P6vAF5ByBJkiRVvCVZA8/aAv73+dX/kqZ5/PYz8J67dr0nRSH+8QdY8iic/s3CYivE0Ho49l/gj1+ARQ/B+Gk7v0bzPBjzShgwqDgxqbjqG+Hvvy3vMxfNgBnXwaDhMOe2dG7gbrDPkenvWMM0aJieqoCkLpjAkCRJkrrT2gpL58Bh5xd2/eAR8PpL4VcfgyfuhANPK01cMcI9X4GRDXDoecVd+6gPwoPXpiTGu+/Y+fub58HE1xQ3JhVP3UTYsAy2boRBu5XnmQ9cnSp7Pv44bFgBix9KH4tmwP3fhNasGqN+4o5kRsPULHE4sDwxquKZwJAkSZK6s+ofsHV99xNIOjriXfDAtfD7/wMHnFyaN2DP/hUWPQCnfqX4lQ6Dh6eGnndfCk/dA694beH3bloN6563/0UlaxulunZRqpQptbWL4fFfwjEfgUHD0kd9Ixxydnp926a0pWTRjJTUeOY+eOwn6bUBQ2GfI1IyY/z0lNgYMbb0MasimcCQJEmSurOkrYHnTiQwageksao/PDdtJ5n+/uLH9ZevwLA94ch3Fn9tgKnvhb99K1Vh7Ht84VthmuenowmMytU2SnX1s+VJYMz4NhC7/u9g4FCYcHT6gFRdtHbxS6s0HrgG7r8yvT5qwku3nex1iNuVqoQJDEmSJKk7TbOgdvDOv9E74GSYeBz8+f/BoefCkJHFi2nRQ/DUn+GNX0hv/kph4BA4/hPwq3+Fv98NrzylsPvaJpDsaQKjYtVNSMdyNPLcujEl8SaftuO5PQkB6sanj4Oz5rTbNqetXG0JjeceSM1yIf33uc/hcNy/pf/u1G85hUSSJEnqTtNs2Ovgnd8GEgKc9AXYuAL++o3ixnTvV1OzzanvLe66HR3xT2nCyR+/mHqBFKJ5LgzdHUbsVdrYtOuGj01v+lc/U/pnzbkNNq+Boz/Uu3UGDklbSI75CJxzI3x8PnxsPrz9xlTZsXEV/PA8eOSm4sStimQCQ5IkSepKa2tKYOx92K7dv88RcMg58LerUkl8MTTNgb//Bo7+SOpVUUq1A+F1l0LzYzD/54Xd0zwvbR8p5fQV9U5NTaqGKHUFRozw4HXpv58JxxR//VHj4KC3wsmXwwfugf1OgDv+Ge79Wnq2+h0TGJIkSVJXVj8NW9btXP+Ljk78bHoz9cfLixPTvV+DwSNL01ejM4ecDWMmw5++BC3bu7+2tRWWzYexB5cnNu26+kZY81xpn/HUn2D5E3DUh0qf0Bo0DM6/LSUM/3AZ/ObSwquG1GeYwJAkSZK60pQ18NyZCSQd1U2Aoz8Is3+Yqid6Y/kCmP8LmH4xDK3r3VqFqqmF138aVj4Jc37U/bWrn4ZtG23g2RfUNaYmnqX0wDWp0WxbH4tSqx0IZ16XqpMevAZ+djFs31qeZ6ssTGBIkiRJXVkyC2oHwZgDe7fOaz6eelb87rO9K22/9+upaefRH+5dPDvrwLekKpR7/l/3bwjbGniawKh8dRNSb4rNa0uz/oqF8ORvU5+WAYNL84zO1NSkLSVv+HwaxfrDc2HL+vI9XyVlAkOSJEnqStNs2HNK70c0Dq2D134yTQ5Z+IddW2PVU+kN2dT3wrDRvYtnZ4UAJ3w2bTl45Maur1s2H0JN2nKiylbfbpRqKcy4LiX/St1otjMhwGs+Bqd/K/03d9PpsGFl+eNQ0ZnAkCRJkjoTY0pg9Gb7SHtTL0oTPX73WWht2fn77/sG1AyAYy4pTjw7a/8TYcKx8JevptGYnWmeC7vvB4N2K29s2nl1WQKjFI08N62BR2+Bg8+CEWOLv36hjnwnnHtLqgz67sml7/mhkjOBIUmSJHVm9TOpxH5XJ5B0NGBQKmtfNh9m3bJz965dDLNuTW/IRu5dnHh2VgipIen6pfDQdzq/pnkejJ1S3ri0a+onpmMpKjAe/QFs2wBHfbD4a++syW+Cd/4MNiyDG06GZY/nHZF6wQSGJEmS1Jmm2enYmwkkHU05Axqmp4kkWzcUft9frwQivPqjxYtlVzQeC/udCPd9HTave+lrW7dDCJIAACAASURBVNbDqqedQNJXDK2HQSOKX5XQ2pK2j0w4tnjVS73VeCy859dATJUYzz2Qd0TaRSYwJEmSpM40zUpbNorZkDIEOOmLqYrh/m8Vds/6ZanvxGHnpcaLeTvhM7BpNTxw9UvPL38CiDbw7CtCyEapFrkCY8GvU1Lk6Aqovmhv7EHw3rth2Bi46QxY8Ju8I9IuMIEhSZIkdWbJLNjzwOJPUJhwFBx4Ovz1f+CF5p6v/9u3oGVrmmRSCcYdCZNPSwmYjat2nG+em44mMPqOugnF30Ly4LUwajy88s3FXbcY6htTEmPPA+G2C1KfDvUpJjAkSZKkjtoaeBZz+0h7b/g8tGyBP3+p++s2roKHbkjNEEfvV5pYdsUJn4Gt6+Gv39hxrnle2pIwqgKqRFSYuqwCozejfdtrmgPP3AvT3w+1A4qzZrEN2wPe/UvY9zj4xYdTIlF9RkEJjBDCKSGEBSGEhSGET3Xy+uAQwo+y1x8MIUxs99ql2fkFIYSTe1ozhHBDCGF2CGFOCOH2EMLw7PyFIYTlIYRZ2cf7evONS5IkSV1auwg2rSpeA8+ORu8H094Hj9wEy57o+roHr02JguP+rTRx7Ko9D4RD3g4PXg8vLE3nmuenBp41/o60z6hvhG0bYcOK4qz34HUwcDc48l3FWa9UBo+AC34CB70Nfvc5uPvT0Nqad1QqQI//uoQQaoGrgFOBKcD5IYSOrYUvAlbHGPcHrgC+nN07BTgPOAg4Bbg6hFDbw5ofizEeFmM8FHgOaD8n6kcxxsOzjy5aH0uSJEm91NbAc58jSveM4z8Jg4anN1Cd2bw2JTAOfEtKGFSa130qbW2592vpN/jNc90+0tcUc5Tq+uXw2E/gsPNTg9BKN2AQnHUDTL84bdP6+QehZVveUakHhaRHpwMLY4xPxRi3ArcBZ3S45gzgxuzz24ETQwghO39bjHFLjPFpYGG2XpdrxhjXAWT3DwWKVM8kSZIkFWjJLAi1pX1DPmx0qqx48m54+i8vf/2h76QkRqVVX7QZvR8c8U8w83uw6ME0ctYERt9SX8QExsPfS9uiKmF0aqFqauDU/4bXfwbm/Ah+eP7OTQdS2RWSwBgHLGr39eLsXKfXxBi3A2uB0d3c2+2aIYTvAUuBycA32113VrutJeM7CzaEcHEIYWYIYeby5csL+PYkSZKkDppmwZjJMHBoaZ9z1AdTw8PffualJexbN8DfroL931jaKpDeeu0n0zSLn2VvWh2h2re0TbXpbSPP7VtTwm3/N8CYA3ofVzmFAK/9BLzlf+Aff0gTSto3p1VFqcgNajHG9wD7AI8D52anfwlMzLaW/I4dFR8d770+xjg1xjh1zJgxZYlXkiRJ/UiMqQJjnxI18Gxv4BA48XNpy8pjP9lx/uHvw8aVcPwnSh9Db4xqgKkXweqn09eVuNVFXRs8Aobu3vsKjPk/h/XNcNSHihNXHl51IZxzU2pE+t1TYO3ivCNSJwpJYDwPtK92aMjOdXpNCGEAMApY2c29Pa4ZY2whbS05K/t6ZYxxS/byd4BXFRC7JEmStHPWLYGNK0o3gaSjg89OzUL/+AXYtgm2bYa/XgkTj0sjVyvdcR+HgcPS9JEho/KORjurvrF3FRgxwgNXw+hJsN8JxYsrDwe+Bd75U3ihCW44CZYvyDsidVBIAuMhYFIIYd8QwiBSU847OlxzB/Du7POzgT/GGGN2/rxsSsm+wCRgRldrhmR/eLEHxunAE9nXe7d73umk6gxJkiSpuJpmpWOpJpB0VFMDJ30xTT558FqY9QNYv7Tyqy/aDN8zld+/7mXDCtUXtI1S3VWLZsCSR+GoD/SPCTQTXwMX3pkaen735PT9qWL0OJw3xrg9hHAJcDdQC3w3xjgvhHAZMDPGeAdwA3BzCGEhsIqUkCC77sfAfGA78JGssoIu1qwBbgwhjAQCMBtoq0P6lxDC6dk6q4ALi/ITkCRJktprmg2hBvY6pHzP3Pd4OOAUuPfrMHgkNExP5/qKQ9+edwTaVfWN8MSdqQfLriQgHrwmVd4cdn7xY8vL3ofCRb+Fm8+EG0+Hc2+GSW/MOyoBIRVK9E9Tp06NM2fOzDsMSZIk9SW3nANrnoOPPFDe5y57Aq45BmIrXPATOOCk8j5f1emhG+DOj8PH5sOojrMaerB2MXzjUDjmw6mKqL9Zvwx+cBYsmw/vuB32e33eEVWNEMLDMcapHc/3gxofSZIkqYiaZpVv+0h7e06GY/8Z9jvR3/aqfOp6MUp1xreBCNMvLmpIFWP4nmk7yZBRMOfHeUcjCthCIkmSJFWNF5amaQrlmEDSmTdels9zVb3qswTG6meh8djC79u6MU3LmfzmHeNY+6MhI2H8UbDYXhiVwAoMSZIkqc2SMjfwlPI2KhsOubMVGHN+BJvXwNEfLn5MlaZhKqxcCBtX5R1J1TOBIUmSJLVpmg0E2OvQvCORymPgEBix986NUo0xTczZ61CYcEzpYqsUDdPT8fmH841DJjAkSZKkFzXNgj0mweDheUcilU9dY2pcW6in/gTLn4CjPwQhlC6uSrHPEWky0eKH8o6k6pnAkCRJktosyamBp5Sn+sad20LywLUwbAwcfFbpYqokg4fDngfBIvtg5M0EhiRJkgRpZOILS2DvnBp4SnmpmwDrnoeWbT1fu/If8OTdMPUiGDC49LFVioapaQtJa2vekVQ1ExiSJEkSZP0vyG8CiZSXukaIrbB2Uc/XPngd1AyEqe8tfVyVZPx02LIOVvw970iqmgkMSZIkCXZMINnrkHzjkMqt/SjV7mxeC7NuSVtHRowtfVyVpGFaOtoHI1cmMCRJkiRIDTx33w+GjMo7Eqm86rIERk99MB79AWxdD0d/sPQxVZrd94MhdbDYPhh5MoEhSZIkQdpC4vYRVaOR4yDUdj+JpLUlbR+ZcEyaylFtampSFcbimXlHUtVMYEiSJEkbVqb9/04gUTWqHQCjxnW/hWTBr1OFxlFVWH3RpmEaLHscNq/LO5KqZQJDkiRJasr6XziBRNWqrodRqg9eC6PGw+TTyhdTpWmYCsQ0jUS5MIEhSZIkvZjAODTfOKS81Dd2XYGxdC48cy9Mf3+q1qhW416Vjm4jyY0JDEmSJKlpNtRPhKH1eUci5aNuImxYBls3vvy1B6+BgbvBke8qe1gVZWgdjJnsJJIcmcCQJEmSlsxy+4iqW9so1Y6NPDesgDk/gcPOM8EHaRvJ4ocgxrwjqUomMCRJklTdNq5Ke/9t4KlqVtdFAmPm96BlS3U372yvYRpsWgWrnso7kqpkAkOSJEnVbemcdHSEqqpZ3YR0bN/Ic/tWeOg7sN+JMOaV+cRVaRqmpaPbSHJhAkOSJEnVbYkTSCSGj4XawbD6mR3n5v8c1i+Foz+UW1gVZ8xkGDTCBEZOTGBIkiSpujXNglETYLfd845Eyk9NTarCaKvAiBEeuAZG758qMJTU1MK4I01g5MQEhiRJkqpb02zYx/4X0ktGqS5+CJY8knpf1Pi28SUapqXRsls35B1J1fFvoiRJkqrX5rWpGZ/bR6TUyLOtiecD18DgUXDY+fnGVInGT4fYsmP7mcrGBIYkSZKqV9PsdDSBIaUtJJvXwLLHYf4v4Mh3wuDheUdVecZNTUe3kZSdCQxJkiRVrxcTGG4hkajPRqn+9rNAhOkX5xpOxRo2GnZ/hQmMHJjAkCRJUvVaMgtGjoPhY/KORMpfXZbAWPg7mPzmHQkNvVzDtJTAiDHvSKqKCQxJkiRVr6bZbh+R2tRP3PH5UY5O7VbDNFjfDGsX5R1JVTGBIUmSpOq05QVYuRD2MYEhATC0HgaPhL0OgcZj846msjVMS0e3kZTVgLwDkCRJknLRNAeI9r+Q2oQAp38Tdt83fa6ujT0IBgyFRQ/BwWflHU3VMIEhSZKk6uQEEunlDnpr3hH0DbUDYZ8jrMAoM7eQSJIkqTo1zYIRe8OIsXlHIqkvGj8Nls6B7VvyjqRqmMCQJElSdVoyy+0jknZdwzRo2ZptR1M5mMCQJElS9dm6AVb83e0jknbdi408Z+QbRxUxgSFJkqTqs/QxIDqBRNKuG7EXjJpgH4wyMoEhSZKk6rNkVjq6hURSbzRMhcUz846iapjAkCRJUvVpmg3D9kxNPCVpVzVMg7WLYF1T3pFUBRMYkiRJqj5NWQPPEPKORFJf9mIfDLeRlIMJDEmSJFWXrRth+RP2v5DUe3sfCrWDTGCUiQkMSZIkVZfmeRBbnUAiqfcGDE7VXPbBKAsTGJIkSaouTTbwlFREDdNgyaPQsi3vSPo9ExiSJEmqLk2zYLfRMKoh70gk9QcNU2H7Jmiem3ck/Z4JDEmSJFWXJbPT9hEbeEoqhobp6eg2kpIzgSFJkqTqsW0zLH/c7SOSimdUAwzfy0aeZWACQ5IkSdVj2Txo3e4EEknFE0LaRrJoRt6R9HsFJTBCCKeEEBaEEBaGED7VyeuDQwg/yl5/MIQwsd1rl2bnF4QQTu5pzRDCDSGE2SGEOSGE20MIw3t6hiRJklSQJW0NPE1gSCqi8dNh9dOwYUXekfRrPSYwQgi1wFXAqcAU4PwQwpQOl10ErI4x7g9cAXw5u3cKcB5wEHAKcHUIobaHNT8WYzwsxngo8BxwSXfPkCRJkgrWNAuG1EHdhLwjkdSfNExLR/tglFQhFRjTgYUxxqdijFuB24AzOlxzBnBj9vntwIkhhJCdvy3GuCXG+DSwMFuvyzVjjOsAsvuHArGHZ0iSJEmFaZqdto/4v5GSimnvwyHU2gejxApJYIwDFrX7enF2rtNrYozbgbXA6G7u7XbNEML3gKXAZOCbPTxDkiRJ6tn2LdA83waekopv0G6w18Gw2D4YpVSRTTxjjO8B9gEeB87dmXtDCBeHEGaGEGYuX768JPFJkiSpD1r2OLRus/+FpNJomA7PPwKtLXlH0m8VksB4Hhjf7uuG7Fyn14QQBgCjgJXd3NvjmjHGFtLWkrN6eAYd7rs+xjg1xjh1zJgxBXx7kiRJqgpNWQNPJ5BIKoWGabB1PSx/Iu9I+q1CEhgPAZNCCPuGEAaRmnLe0eGaO4B3Z5+fDfwxxhiz8+dlE0T2BSYBM7paMyT7w4s9ME4HnujhGZIkSVLPlsyCwaOgft+8I5HUHzVMTUfHqZbMgJ4uiDFuDyFcAtwN1ALfjTHOCyFcBsyMMd4B3ADcHEJYCKwiJSTIrvsxMB/YDnwkq6ygizVrgBtDCCOBAMwGPpSF0ukzJEmSpII0zYa9D7WBp6TS2P0VsNvoNIlk6nvyjqZfCv25iGHq1Klx5kzH2EiSJFW9lm3wpXFw1MVw0hfzjkZSf3XrubDqabjEKozeCCE8HGOc2vF8RTbxlCRJkopq2ePQssUGnpJKq2EqrFgAm9bkHUm/ZAJDkiRJ/V/T7HQ0gSGplBqmpePz7gQoBRMYkiRJ6trzj8CvPgZNc/KOpHeaZsGgEWmPuiSVyrhXASH1wVDRmcCQJElS1+75b5j5XbjuOLjl7fDcg3lHtGuWzEoNPGv8319JJTR4BOw5BRY/lHck/ZL/gkuSJKlzm1bDwt/Dqy6E138m/UbxuyfB90+Df/wJ+koz+Jbt0DzX7SOSyqNhavr3srU170j6HRMYkiRJ6tzjv4LWbSmB8dpPwL8+BiddDiuehJvfCt85EZ64q/ITGSsWwPbNsPdheUciqRo0TIPNa2Dlwrwj6XdMYEiSJKlzc29PPSPaKhcGD4djL4GPzoY3fx02LIfbzodrXg2P3Q6tLfnG25W2Bp77WIEhqQzGT09Ht5EUnQkMSZIkvdz6ZfD0X+DgsyCEl742cAhMuwj++RF467WpSuN/L4JvTYNHbobtW/OJuStLZsHAYTB6/7wjkVQNRk+CwaNMYJSACQxJkiS93PxfQGxNCYyu1A6Ew8+HDz8Ib78RBg2DOy6BK4+AB6+DbZvKF293mmbBXodATW3ekUiqBjU10PAqExglYAJDkiRJL/fY7bDnQbDngT1fW1MDB70VPvAXeMftMKoBfv1J+MYhcN8VsHld6ePtSmsLLH3M7SOSyqthGiybD1teyDuSfsUEhiRJkl5qzSJY9AAc/Laduy8EmPRGeO9v4MI7YezB8PvPwzcOhj99CTauKkm43VrxJGzb6AQSSeXVMD1VsS15NO9I+hUTGJIkSXqpeT9Lx51NYLQJASa+Bt71c3j/H6HxNXDPl+GKg+G3n4EXmosXa0+aZqWjE0gkldO4I9PRbSRFZQJDkqQqtXj1Rr7wq/k8t3Jj3qGo0sy9Hca9Kk0g6a1xr4Lzb4UP3Q+vPBX+dlXaWnLnv8Ga53q/fk+aZsOAobDHAaV/liS12W331MxzkQmMYjKBIUlSlZrx9CpuuO9pNm7bnncoqiQrFqY3/d0179wVYw+Cs2+AS2bCoefAwzemZp8//QA881eIsbjPa7NkFux1MNQOKM36ktSV8dNTBUap/n2rQiYwJEmqUo88t5rhgwcwac8ReYeiSjLvp0CAg84szfqj94MzvgUfnQXT3gdP/Aq+/ya48nC4579T/41iaW2FpXPsfyEpHw1TYeMKWP1M3pH0GyYwJEmqUo88u4bDx9dRWxPyDkWVIsY0faTx1TByn9I+a1QDnPpl+Pe/w5nXwajx8KfL0/aSm86AOT+Grb3c3rTqH7B1vRNIJOWjYVo6Lp6Zbxz9iAkMSZKq0IYt23li6TqOnFCXdyiqJM3zYMWCXW/euSsGDYPDzoMLfwUfnQ2v+xSsegp++n742ivhlx+FRTN2rQR7iQ08JeVozIEwcBgsnpF3JP2GmwElSapCsxevoTXCEY31eYeiSjL3fyHUwpQz8nl+/cSUwDj+k/DsfTDr1lSJ8fD3UxPOwy+AQ8+DkXsXtl7TLKgdDGMmlzJqSepc7YA0jcRJJEVjBYYkSVXo0efWAHDEeCswlIkxJTD2ez0M2yPfWGpqYN/j4cxr0xaT078Fu42G338erpgCPzg7jXrdvqX7dZpmZw08B5YlbEl6mYZpsPQx2LapvM/dvhV+eEFqktyPmMCQJKkKPfLsal4xZhh1uw3KOxRViucfhjXPFn/6SG8NHgFHvhPe+xv450fgNR+HZfPhJxfCVw+AO/8dljz68i0mra0pgeH2EUl5apgGrdt3bGkrl3u+DAvuhM1ryvvcEjOBIUlSlYkx8uiiNRw5we0jamfu/6btFpPfnHckXRu9H5z4WfjXx+Cffgr7vwEeuQmufx1ccyzc/y1Yvzxdu/pp2LLOCSSS8vViI88ybiNZNAPu+zoc/k+V/W/6LrAHhiRJVeaZlRtZtWGrCQzt0NoCc38Kk94IQ0blHU3Pamph/xPTx6Y1afTro7fAbz8Nv/8/MOkkqJuQrnUCiaQ8DR+T+vuUK4GxdQP87AMwsgFO+a/yPLOMTGBIklRlHnl2NQBHNtr/Qpln74f1Sytv+0ghhtbB1Pemj2VPwOxbYfZtsOAuqB2UpgBIUp4appWvF8XvPgernk6TnYaMLM8zy8gEhiRJVebRRasZPngAk/YckXcoqhRz/zeN+jvg5Lwj6Z09J8MbL4MTPgf/+EM6N8A+L5Jy1jANHvsJrF0MoxpK95yFv4eHvgPHXAITX1O65+TIBIYkSVXmkWfXcPj4OmprQt6hqBK0bIP5v4BXngqDhuUdTXHUDuj7yRhJ/Uf7PhilSmBsXAW/uCSNjT7hs6V5RgWwiackSVVkw5btPLF0HUdOcPuIMk/9GTatgkPOzjsSSeqfxh4MA4bA4pmle8Zdn4ANy+HM62DgkNI9J2cmMCRJqiKzF6+hNcIRjTbw/P/t3XmclXXd//HXd1aWgUGQAWQXUERcQDb3PbXMLfulZZmJmkt2133XrXZnZctdd4uVpeVu5pKpKalpmpXmAoyDsimIIDMgOzMDw8Cs398f56iECKPMzHXOzOv56DzOOde5ru/1OUDOnPe5vp+v0uY+kGrcOeKYpCuRpI4pryC1IlJbNfKc+wDMvR+OvKLDNy42wJAkqROZVZ5aD378YAMMAQ1b4NVHYJ+PQ15h0tVIUsc1aAK89TI01rfuuBtWwCNfhYEHwWFfad2xM5ABhiRJnUjZ0kpG9O1Ocbf8pEtRJnj9r1C/EcY6fUSS2tTgSdBUByvntN6YMcK0y6CxDk6/MdX/p4MzwJAkqZOIMTKroorxQ7z6QmlzH4DufWHY4UlXIkkd29aNPFvLS7elVh75yHdh95GtN24GM8CQJKmTeHNdLes31TPOAEMAdRth4RMw5rRO8a2dJCWq5x7QcyAsm9E64617A574Bux5NEw4v3XGzAIGGJIkdRJlSysBGD/UFUgELPgLNG529RFJai+DJrTOFRjNTfDQxZCTD6f+GnI6z8f6zvNOJUnq5MrKKykqzGNUSY+kS1EmmPsA9BwEgyYlXYkkdQ6DJkFVOWxctWvjPPcLqJgOH/sJFA9sndqyhAGGJEmdRFl5FQcO7kVuTki6FCWtdj0s+huMPb1TfXMnSYl6uw/G8tIPP8bKOfD3H6Sm/+33ydapK4v4E0uSpE6gpq6RBSs3MH6I00cEvPpnaG5w9RFJak8DDkhN+6j4kH0wGuvgwYugW2/42M8gdL4vJOzYJElSJzB7WRXNEcYNtYGnSE0f6T0i9cu0JKl95HeBAfvDsg95Bcbfvw+r58Gn74PufVq3tizhFRiSJHUCs8qrABg/2ACj09u4Ct58FsZ+olN+eydJiRo0Ed4qg6bGD3bc0hfguV/C+HNhrxPaprYsYIAhSVInULa0khF9u1PcLT/pUpS0+Q9BbE4FGJKk9jVoIjTUwur5LT+mbiP86SLYbSic8IO2qy0LGGBIktTBxRiZVVHF+CFefSFS00f6jYWS0UlXIkmdz6AJqftlH6APxhPfSK1ectpvoLCoberKEgYYkiR1cG+uq2X9pnrG2/9CVeWppffGnpF0JZLUOfUaCt1LWt4HY+ETUHYHHHo5DD24bWvLAgYYkiR1cGVLKwG8AkMw98HUvdNHJCkZIaSmkSybufN9N62Dhy+Dkn3h6G+0fW1ZwABDkqQOrqy8kqLCPEaWdO7LTkVq+sjACbDbsKQrkaTOa9AEWLcIate//z4xwqNfgc2VcMZvIa+w/erLYAYYkiR1cGXlVRw4uBe5Oa440amtfR1WzvbqC0lK2qCJqfsdTSOZ80eY/zAcfRX036996soCBhiSJHVgNXWNLFi5gfFDeiVdipI29wEgwL6nJ12JJHVuA8dDyHn/aSTVy+HR/4LBk+HQL7dvbRmuRQFGCOHEEMKCEMKiEMIV23m9MITwh/Tr00MIw7Z67cr09gUhhBN2NmYI4a709rkhhFtDCPnp7UeFEKpDCC+nb1fvyhuXJKkzmF1RRXOEcTbw7NxiTAUYww6DngOSrkaSOreC7tBv3+0HGM3N8PAl0NwIp90AObntX18G22mAEULIBX4NnASMAc4OIYzZZrfzgcoY40jgWuBH6WPHAGcB+wInAteHEHJ3MuZdwGhgP6ArMHWr8zwbYzwwfbvmw7xhSZI6k7LydAPPwQYYndqqubB2oauPSFKmGDQRlr+UCiy2VnoLLP4HnPA96DMikdIyWUuuwJgELIoxLo4x1gP3Aqdus8+pwB3px/cDx4YQQnr7vTHGuhjjEmBRerz3HTPG+FhMA2YAg3btLUqS1HmVlVcxom93irvlJ12KkjTnfsjJg322/RVOkpSIQZOgbgOsXfDutrWvw1+/CSOPg4POS662DNaSAGMgULHV82XpbdvdJ8bYCFQDfXZw7E7HTE8d+Szw+FabDw4hvBJC+EsIYd/tFRtCuDCEUBpCKF2zZk0L3p4kSR1TjJFZ5ZUun9rZxZhaPnXPo6F7n6SrkSTBVo0809NImhrhTxelVhs55Vep5Vb1HpncxPN64JkY47Pp52XA0BjjAcB1wEPbOyjGeGOMcUKMcULfvn3bqVRJkjLPm+tqqaxtYLz9Lzq3ZaVQXe7qI5KUSfqMgC693g0w/nVtakrJyT+zV9EOtCTAWA4M3ur5oPS27e4TQsgDioF1Ozh2h2OGEL4F9AW++va2GOOGGGNN+vFjQH4IYfcW1C9JUqdUtjTd/8IrMDq3ufdDbiGM/ljSlUiS3hZC6iqMipnw1svwzx/C2DMNm3eiJQHGTGBUCGF4CKGAVFPOadvsMw04N/34TODpdA+LacBZ6VVKhgOjSPW1eN8xQwhTgROAs2OM73Q0CSH0T/fVIIQwKV37ug/zpiVJ6gzKyivpUZjHqJKipEtRUpqbYN6fYK+PQJeeSVcjSdra4Emw5jV44Hzo3hc++uOkK8p4eTvbIcbYGEK4DHgCyAVujTHOCyFcA5TGGKcBtwB3hhAWAetJBRKk97sPmA80ApfGGJsAtjdm+pS/AZYCL6TzigfTK46cCVwcQmgENgNnpUMSSZK0HWXlVRw4pBc5Oc6j7bSWPgc1q/xGT5Iy0aAJQIR1i+CcB6Bb76Qryng7DTDgnSkbj22z7eqtHm8BPvk+x34f+H5Lxkxv325NMcZfAb9qSb2SJHV2NXWNLFi5geOPHpl0KUrSnPuhoAhGnZB0JZKkbQ08CPK7wYGfTq08op1qUYAhSZKyy+yKKpojjLOBZ+fVWA+vToO9PwoF3ZKuRpK0rS7FcPks6F6SdCVZwwBDkqQOqKw83cBzsAFGp7X4H7C50ukjkpTJevRPuoKsksnLqEqSpA+prLyKEX27U9wtP+lSlJS5D6SW6BtxTNKVSJLUKgwwJEnqYGKMzCqvdPnUzqxhM7z2CIw5BfIKkq5GkqRWYYAhSVIHs2TtJiprGxhv/4vO6/W/Qn2N00ckSR2KAYYkSR1MWXkVgFdgdGZzH0g1hRt2eNKVSJLUagwwJEnqYGaVV9KjMI9RJUVJl9I2mptg9WtJV5G5tmyAhU/AvqdBTm7S1UiS1GoMMCRJ6mDKyqs4cEgvcnJCdtB6cQAAIABJREFU0qW0jae+BddPhjeeTrqSzLTgL9C4BcaemXQlkiS1KgMMSZI6kJq6Rhas3MC4jjp9pHw6PP+r1OO//wBiTLaeTDT3ASgeDIMmJl2JJEmtygBDkqQOZHZFFc0Rxg/plXQpra9hMzx8SerD+Ue+D8tmwqKnkq4qs9Suhzf+BvueDjn+midJ6lj8ySZJUgdSVl4JwLjBHfAKjKe/B+sWwanXweSLoNdQ+Pv3vQpja69Og+ZG2M/pI5KkjscAQ5KkDqSsvIoRfbtT3C0/6VJa19IX4IVfw4TzYc+jIDcfjvw6vDUr1fNBKXMfgD4jof/+SVciSVKrM8CQJKmDiDEyq7yy4y2fWl+bmjrSazAcf8272/c/C3YbnuqF0dycXH2ZYuNKWPIsjP0EhA7awFWS1KkZYEiS1EEsWbuJytoGxg/tYAHG09+F9Yvh1F9D4VZLw+bmwVFXwKo58NojydWXKeY9BMRUgCFJUgdkgCFJUgdRVl4F0LGuwFj6PLx4A0y8AIYf8d7Xx54JfUbBP/7XqzDmPgD99oO+eyddiSRJbcIAQ5KkDqKsvJIehXmMKina+c7ZoH4TPHQJ9BoCx317+/u8fRXG6vkw/6H2rC6zVC6FZTNg7BlJVyJJUpsxwJAkqYMoW1rJgUN6kZPTQfof/O0aqFzy3qkj29r3dOg7Gv7xQ2huar/6MsnMm1L3BhiSpA7MAEOSpA6gpq6Rhas2Mq6jTB95818w/Tcw6UIYfviO983JTV2FsXYBzH2wferLJG+9DC9cD+POgd2GJV2NJEltxgBDkqQO4JWKKpojjB/SK+lSdl39Jnj40tSH8eO+3bJj9jkVSvaFf/4QmhrbsLgM09QA0y6D7n3hI99PuhpJktqUAYYkSR3ArPJKAMYN7gBXYDz1bah8E069Hgq6t+yYnBw4+kpYtwjm/LEtq8ssz/8SVs6Bj/0EunaA8EqSpB0wwJAkqQMoK69iZEkRxd3yky5l1yx5BmbcCJO/CMMO/WDHjj4Z+u8P//xR6sqEjm7NQvjHj2DMqbDPx5OuRpKkNmeAIUlSlosxMqu8knGDs/wb+Lqa1NSR3nvCsVd/8ONDgKOvSjX+fOXe1q8vkzQ3w58vh/yucNKPk65GkqR2YYAhSVKWW7J2E5W1DYwfmuXTR576FlRVfLCpI9va60TYYzw883/QWN+69WWS0lug/AU48X+hR7+kq5EkqV0YYEiSlOXKyqsAGJ/NK5As/ifMvBmmXAxDD/7w44QAR38Dqsrh5btar75MUlWR6hMy4hg44Oykq5Ekqd0YYEiSlOXKyivpUZjHqJKipEv5cOo2wsOXQe8RcMw3d328kcfCoEnwzE+gsW7Xx8skMcIjX0ndn/zzVGAjSVInYYAhSVKWK1tayYFDepGTk6UfZp+8Gqor4LTroaDbro/3di+MDcug7He7Pl4mmfNHWPRkqkfIbkOTrkaSpHZlgCFJUharqWtk4aqNjMvW6SNv/B1Kb4WDL4UhU1pv3D2PgiGHwLM/hYYtrTdukmrWwF/+O3V1yaQLkq5GkqR2Z4AhSVIWe6WiiuYI44dk4QokWzbAtC9Bn5FwzP+07thvX4WxcQW8dHvrjp2Ux/8b6mvglOsgJzfpaiRJancGGJIkZbGypZUAjBuchVdgPPlN2LAcTrshtRxoaxt+OAw7HP71M6ivbf3x29OCv8DcB+CIr0HJ6KSrkSQpEQYYkiRlsbLySkaWFFHcLT/pUj6YRX9LXRlx8KUweFLbnefoq6BmVWrZ0Wy1pRoe+SqU7AuH/kfS1UiSlBgDDEmSslSMkVkVVdk3fWRLNUy7HPqMSi152paGHgJ7Hg3/+jnU1bTtudrKk9+CmpVw6nWQV5B0NZIkJcYAQ5KkLLVk7SaqahsYn20NPP/6P7DxrbabOrKto6+C2rUw86a2P1drW/IsvHQbTLkEBh6UdDWSJCXKAEOSpCxVVl4FkF0rkCx6KrW06SFfgsET2+ecgyfByOPhuV+kGodmi4bN8OfLYbdhbX+liiRJWcAAQ5KkLFVWXkmPwjxGlRQlXUrLvD11ZPe94air2vfcR18Jmythxm/b97y74h//C+sXp1YdKeiWdDWSJCXOAEOSpCxVtrSSA4f0IicnJF1KyzyRXtb0tBsgv0v7nnvgQbDXSfD8dakgJdMtL0vVOv5zMPyIpKuRJCkjGGBIkpSFauoaWbhqY/ZMH3n9SZj1ezj0yzAooV4OR1+ZCi9evCGZ87dUUwNM+xJ0L4Hjv5t0NZIkZQwDDEmSstArFVU0R7JjBZLNVakP5H1Hw1FXJlfHgANg9Mnwwq9T00ky1XM/h1Vz4eSfQdcs+PuVJKmdGGBIkpSFypamPoCPG5wFV2A8cRXUrIbTroe8wmRrOepKqNuQCjEy0ZqF8M//g31Ph9EfS7oaSZIyigGGJElZqKy8kpElRRR3y0+6lB1b+AS8fFdq6kgmLAPaf2wqHHjxBqhdn3Q1/665GaZdBvnd4KT/S7oaSZIyjgGGJElZJsbIrIqqzJ8+srkytepI333gqCuSruZdR14B9Zvg+V8mXcm/m3kzVEyHE38IRSVJVyNJUsYxwJAkKcssXruJqtoGxmd6A8/Hr4RNa+D0G5KfOrK1ktGw35kw/UaoWZN0NSlV5fC378CIY+GAs5KuRpKkjGSAIUlSlnm7/8X4oRkcYCx4HF65Bw77CuwxLulq3uvI/4bGzfD8L5KuBGKER76Suv/4zyFkybK4kiS1MwMMSZKyTFl5FT265DGyb1HSpby/AfvD5C/CkV9PupLt230U7P8pmHEzbFyVbC2z/wCLnoLjvgW9hiRbiyRJGaxFAUYI4cQQwoIQwqIQwnsmsYYQCkMIf0i/Pj2EMGyr165Mb18QQjhhZ2OGEO5Kb58bQrg1hJCf3h5CCL9M7z87hDB+V964JEnZalZ5JQcO7kVOTgZ/U99zDzjpR5k1dWRbR3wNmupTy5YmpWYNPH4FDJ4ME6cmV4ckSVlgpwFGCCEX+DVwEjAGODuEMGab3c4HKmOMI4FrgR+ljx0DnAXsC5wIXB9CyN3JmHcBo4H9gK7A2z/NTwJGpW8XAjd8mDcsSVI2q6lrZOGqjYzL9P4X2aDPCDjwbJh5C2xYkUwNf/l6qqHoKddBTm4yNUiSlCVacgXGJGBRjHFxjLEeuBc4dZt9TgXuSD++Hzg2hBDS2++NMdbFGJcAi9Ljve+YMcbHYhowAxi01Tl+l37pRaBXCGHAh3zfkiRlpVcqqmiOZP4KJNniiK9BbIJ//az9z/3aozDvwdQ0m757t//5JUnKMi0JMAYCFVs9X5bett19YoyNQDXQZwfH7nTM9NSRzwKPf4A6CCFcGEIoDSGUrlmTIZ3FJUlqJW838Bw32CswWsVuw2DcOfDS7VC9rP3Ou7kKHv1P6DcWDv2P9juvJElZLJObeF4PPBNjfPaDHBRjvDHGOCHGOKFv375tVJokSckoK69kZEkRxd3yky6l4zj8v1IrgDzzk/Y755NXQ82q1NSRXP8uJUlqiZYEGMuBwVs9H5Tett19Qgh5QDGwbgfH7nDMEMK3gL7AVz9gHZIkdVgxRmZVVDl9pLX1GgwHnQuz7oTKpW1/viXPQNkdcPBlMNCe5JIktVRLAoyZwKgQwvAQQgGpppzTttlnGnBu+vGZwNPpHhbTgLPSq5QMJ9WAc8aOxgwhTAVOAM6OMTZvc47PpVcjmQJUxxgT6rglSVL7W7x2E1W1DYy3gWfrO+yrEHLhmR+37Xnqa2Ha5bDbcDjqyrY9lyRJHcxOA4x0T4vLgCeAV4H7YozzQgjXhBBOSe92C9AnhLCI1FUTV6SPnQfcB8wn1cvi0hhj0/uNmR7rN0A/4IUQwsshhKvT2x8DFpNqBHoTcMmuvXVJkrLL2/0vxg81wGh1xQNhwnnw8t2wfnHbnecfP4DKJXDKL6GgW9udR5KkDiikLpTomCZMmBBLS0uTLkOSpFZx5YNzeGT2W7xy9UfIyQlJl9PxbFwJvzgARp8MR18FTfXpW0PqvrHu3cdbb3/PreHd+8a6rR5vgfkPwfjPwcd/kfS7lSQpY4UQXooxTth2e14SxUiSpA9uVnklBw7uZXjRVnr0h4lT4YVfwdz7d22s3IL0Lf/fH+95NBx/TevUK0lSJ2OAIUlSFti4pYEFqzZywr79ky6lYzv6Kui/HxBSgUNe4faDiHcev09QEQyZJElqbQYYkiRlgVcqqonR/hdtrqA7HHBW0lVIkqTtaMkqJJIkKWGzylMNPA8c5BKqkiSpczLAkCQpC5SVVzKypIjibvlJlyJJkpQIAwxJkjJcjJFZFVWMH+LVF5IkqfMywJAkKcMtXruJqtoGxg+x/4UkSeq8DDAkScpwZUtT/S9s4ClJkjozVyGRJGkXxRh5ZVk1OQF2LyqkT1EBhXm5rTZ+WXkVPbrkMbJvUauNKUmSlG0MMCRJ2gV1jU1c+eAcHixb/m/be3TJo29R4TuBxtb3qVv6cY9CuhfkEkJ433PMKq/kwMG9yMl5/30kSZI6OgMMSZI+pHU1dVx050uULq3kS8eMZL+BxaytqWddTR1ra+pYW1PP2po6Fq7ayPNvrKN6c8N2xynMy3knzNi9+7+HHbt1z2fBqo2csG//dn53kiRJmcUAQ5KkD2HByo2cf8dM1mys41efHsfJ+++x02PqG5tZv6k+HW7UbTfseKt6C7OXV7N+Uz1NzfGdYyfv2bst344kSVLGM8CQJOkD+vuC1Xzp7ll0K8jlvosO5oDBLVvetCAvh/7FXehf3GWn+zY3R6o2N7C2po66hmbGDuy5q2VLkiRlNQMMSZJaKMbIbc+9yfcenc/o/j255fMTGFDctU3OlZMT6N29gN7dC9pkfEmSpGxjgCFJUgs0NDXzrWnzuHt6OR8Z04+fn3Ug3Qr8MSpJktRe/M1LkqSdqK5t4JK7X+K5Reu4+KgRfO0je7siiCRJUjszwJAkaQeWrN3E+bfPpKKylp988gDOPGhQ0iVJkiR1SgYYkiS9j+ffWMvFvy8jJ8BdU6cwabgrgUiSJCXFAEOSpO24Z0Y533xoLsN3784t505kSJ9uSZckSZLUqRlgSJK0labmyP8+9io3/2sJR+7Vl+s+PY6eXfKTLkuSJKnTM8CQJCmtpq6RL98zi7+9tprPHzKM//nYPuTl5iRdliRJkjDAkCQJgGWVtUy9o5TXV9fw3dPG8tkpQ5MuSZIkSVsxwJAkdXovLa3kojtLqWts5vbzJnL4qL5JlyRJkqRtGGBIkjq1h2Yt5+sPzGZAcRfuvXAiI0uKki5JkiRJ22GAIUnqlJqbI9c+tZDrnl7E5OG9+c05B7Fb94Kky5IkSdL7MMCQJHU6m+ub+M8/vsxjc1byqQmD+e5pYynIs1mnJElSJjPAkCR1Kqs2bOGC35UyZ3k13/joPkw9fDghhKTLkiRJ0k4YYEiSOo25y6uZekcpG7Y0cNNnJ3DcmH5JlyRJkqQWMsCQJHVoMUbKyqu4d0Y50155iz7dC7j/i4cwZo+eSZcmSZKkD8AAQ5LUIVXXNvDgrGXcO6OCBas20q0gl9PHDeSrH9mLkh5dki5PkiRJH5ABhiSpw4gxMvPNSu6ZUc5jc1ZQ19jM/oOK+cHp+3HKgXtQVOiPPUmSpGzlb3KSpKy3flM9D7y0jHtnlvPGmk30KMzjkxMGcdbEIYwdWJx0eZIkSWoFBhiSpKzU3Bx5YfE67plRzl/nraK+qZnxQ3rxf2fuz8n7D6BbgT/iJEmSOhJ/u5MkZZXVG7dw/0vL+MPMCpauq6W4az6fnjyEsycNYe/+PZIuT5IkSW3EAEOSlPGamyPPLlrLPdPLeerVVTQ2RyYN781/HDeKk8YOoEt+btIlSpIkqY0ZYEiSMtbK6i38sbSCe2dWsLxqM727F3DeocP41MQhjCwpSro8SZIktSMDDElSRmlsauafC9dwz4xynn5tNc0RDh3ZhytOGs1H9u1HYZ5XW0iSJHVGBhiSpIyxeE0Nn7t1BssqN7N7USEXHTmCsyYOZmif7kmXJkmSpIQZYEiSMsKajXWce9sMauub+M054zl2n37k5+YkXZYkSZIyhAGGJClxtfWNnH/HTNZsrOOeC6YwbshuSZckSZKkDONXW5KkRDU2NXPZ3bOYu7ya684eb3ghSZKk7fIKDElSYmKMfPPhuTz92mq+d9pYjh/TL+mSJEmSlKG8AqMTWbhqI6Vvrk+6DEl6x6//voh7ZlRwyVEjOGfK0KTLkSRJUgZrUYARQjgxhLAghLAohHDFdl4vDCH8If369BDCsK1euzK9fUEI4YSdjRlCuCy9LYYQdt9q+1EhhOoQwsvp29Uf9k13Ro/MfouPX/cvzrrxRf71+tqky5Ek7n9pGT/560JOHzeQr52wd9LlSJIkKcPtNMAIIeQCvwZOAsYAZ4cQxmyz2/lAZYxxJHAt8KP0sWOAs4B9gROB60MIuTsZ8zngOGDpdsp5NsZ4YPp2zQd7q51TjJFfPPU6l909i/0GFjOibxEX//4lFqzcmHRpkjqxZ19fwxUPzObQkX340Sf2J4SQdEmSJEnKcC25AmMSsCjGuDjGWA/cC5y6zT6nAnekH98PHBtSv42eCtwbY6yLMS4BFqXHe98xY4yzYoxv7uL7ErCloYkv3/sy1z61kDPGD+SuCyZz63kT6VqQyxdun8nqDVuSLlFSJzTvrWou/n0ZI0uKuOGcgyjIczajJEmSdq4lvzUOBCq2er4svW27+8QYG4FqoM8Ojm3JmNtzcAjhlRDCX0II+25vhxDChSGE0hBC6Zo1a1owZMe0ZmMdZ9/0ItNeeYuvn7g3P/3kARTm5TKwV1du/fxEKmvrOf+OUmrrG5MuVVInsrxqM+fdNpMeXfK4/bxJ9OySn3RJkiRJyhLZ9LVXGTA0xngAcB3w0PZ2ijHeGGOcEGOc0Ldv33YtMFO8umIDp/36OV5dsYHfnDOeS44a+W+XZ48dWMx1Z49j3lvVXH7PyzQ1xwSrldRZVNc28PlbZ7C5oYnbz5tE/+IuSZckSZKkLNKSAGM5MHir54PS27a7TwghDygG1u3g2JaM+W9ijBtijDXpx48B+Vs3+VTK315dxZk3PE9jczP3f/EQThw7YLv7HbtPP759yr489eoqvvvI/HauUlJnU9fYxAV3lrJ0XS03fnYCe/fvkXRJkiRJyjItCTBmAqNCCMNDCAWkmnJO22afacC56cdnAk/HGGN6+1npVUqGA6OAGS0c89+EEPqn+2oQQpiUrn1dS95kZxBj5OZnFzP1d6Xs2beIhy89jLEDi3d4zOcOHsb5hw3n9uff5LbnlrRTpZI6m+bmyH/e9wozlqznx5/cn4NH9Em6JEmSJGWhvJ3tEGNsDCFcBjwB5AK3xhjnhRCuAUpjjNOAW4A7QwiLgPWkAgnS+90HzAcagUtjjE2QWi512zHT2y8Hvg70B2aHEB6LMU4lFYxcHEJoBDYDZ6VDkk6vvrGZb02byz0zKjhpbH9+9v8OpGtBbouOveqj+7CsspZrHpnPoN26cfyYfm1craTO5oePv8Yjs1dw5UmjOfXAlrQ7kiRJkt4rdOQMYMKECbG0tDTpMtpUVW09F/++jBcWr+Oyo0fy1eP3Iifngy1HuLm+ibNufIGFq2r4w0VT2H9QrzaqVlJnc9tzS/jOn+dz7sFD+fYp+7pcqiRJknYqhPBSjHHCttuzqYmntrF4TQ2nX/88Ly2t5Gf/7wD+64S9P3B4AdC1IJebz51In6ICvnB7Kcsqa9ugWkmdzeNzV3DNI/P5yJh+XP1xwwtJkiTtGgOMLPX8orWcfv3zbNjcwN0XTOaM8YN2aby+PQq57fMTqWts4gu3z2TDloZWqlRSZ1T65nq+fO/LjBvci1+ePY7cDxGuSpIkSVszwMhCd08v53O3zqBfz0IeuvRQJgzr3SrjjurXg9+ecxCL12zikt+X0dDU3CrjSupc3lhTw9TflbJHr67cfO5EuuS3rCePJEmStCMGGFmkqTny3Ufmc9Wf5nDYqN154OJDGNy7W6ue45CRu/PDT+zPvxat5Rt/mkNH7pEiqfWt3riFc2+dQV5O4I7zJtG7e0HSJUmSJKmD2OkqJMoMG7c08OV7X+bp11Zz3qHD+MZH9yEvt23ypzMPGkT5+lp++bfXGdK7G5cdM6pNziOpY9lU18j5t5eyrqaeey+cwpA+rRuwSpIkqXMzwMgCFetrmXpHKYvW1PC908ZyzpShbX7Orxw3ior1tfzkrwsZ3LubSx9K2qHGpmYuvbuMeW9Vc/O5EzhgsKsZSZIkqXUZYGS4l5ZWctGdpdQ3NnPHeZM4bNTu7XLeEAI//MR+LK/azNf+OJsBxV2ZNLx1em10NDFGVlRv4fXVNSxaXcOi1Rt5fVUNi9bUUFvfRGFeDoV5uXTJz3nncWF+Dl3S9//+ei6FeTl0yU/dF+a//2v7DOjJbl6erwwQY+R/HprLPxas4Qen78cxo/slXZIkSZI6oNCRexxMmDAhlpaWJl3Gh/bQrOV8/YHZ7FHchVs+P5ERfYvavYaq2nrOuOF51m+q58GLD2HPBGrIFE3NkYr1tSxaXcPrq2t4ffVG3kiHFpvqm97Zb7du+Ywq6cGIkiKKu+ZT19jEloZm6hqbqGtspu7tx+n7rV/b0vDuffNO/q/ZrSCXcw8ZxoWH72mQoUT98m+v87MnF/KlY0bynx/ZO+lyJEmSlOVCCC/FGCe8Z7sBRuZpbo78/KmF/PLpRUzZszc3fOagRD+glq+r5fTrn6OoSx4PXnwIfYoKE6ulPdQ3NrN03aZ3rqh4fXUNr6/ayOK1m6hvfHdlln49CxlV0oORJUXv3EaVFLXan09DU3M68GhiS/r+7XBjU10T95VW8OfZb9EtP5cvHDacqYftSXG3/FY5t9RSfyyt4Gv3z+aM8QP56ScPIASXS5UkSdKuMcDIEpvrm/ivP77Co3NW8KkJg/nuaWMpyEt+sZiy8krOvvFFxg4s5q6pkzvMsoirN2zhhcXrUlM+0ldVLF1XS+NWlz8M2q0ro0qKGNWvByP7FjGyXyqs6Nkl+bBg4aqN/OKp13l0zgp6FObxhcOG84XDhlPcNfna2lOMkTnLqxnap3une+9J+ufCNZx/+0wOHtGHW86dmBH/rZIkSVL2M8DIEpfc9RJ/mbuSq07ah6mHD8+obzMfm7OCS+4q42P7D+C6s8aRk5M5tX0Yc5ZV87lbp1NZ20BuTmBon26M7FvEqH5F71xZsWff7nQryPxWMa+u2MAvnnqdx+etpGeXPC44fE8+f+gwemRAyNKWmpojj89dyY3PvMEry6oZWVLE3RdMpqRHl6RL6/DmLq/mU799gSF9unPfRVM6/L81SZIktR8DjCzx2soNVKzfzPFjMrMJ3o3PvMEPHnuNLx45gitOGp10OR/ajCXr+cLtMynums+vPj2OMXv0pDAv+68qmbu8mp8/9TpPvbqKXt3yU0HGIcPoXpj5IcwHsbm+iftfquDmfy1h6bpahvVJrZRz07OL6V/chXsumEK/np0zxGhoaua5RWt5dPYK/vbaamq2NEKAAIQAgZC+TzXrDfDO6zk54d+2h/SLYTvHV9U2sFu3fP506aGd9s9akiRJbcMAQ63i7dUG7ppezv+esR9nTxqSdEkf2DML13DhnaXs0asrd02dzIDirkmX1OpmL6vi2icX8vcFa+jdvYCLjtiTzx48NCuuJtmR9Zvq+d0Lb/K7F5ayflM9Bw7uxReP3JPjx/QnNycwY8l6zrttBiU9UyFG/+LO8cG6oamZ599Yx6Oz3+KJeauo3txAj8I8jt2nhP7FXYlE0v8jxkh85zFEUs95+7VttqdmU6WP2Wp7fl4O5x82PJHmwpIkSerYDDDUahqbmpn6u1KefX0tt35+Ikfu1Tfpklrs8bkrufyeWYwoKeLO8yexewdvSDqrvJJrn3qdZxauYfeiAr545Ag+M3koXQuy62qTpes2cfOzS/jjSxVsaWjmuH1KuPCIEUwcttt7plm9tHQ95946kz5FBdxzwRT26NXxAipIhRYvvLGOx+as4PF5K6mqbaCoMI+PjOnHR/cbwOF77d4hriqSJElS52OAoVZVU9fIJ3/zAhXra/njFw9mnwE9ky5ppx4sW8bX7p/N/oOKuf3zkzrVih2lb67n2qcW8tyidfTtUcglR43g7ElDMr4Z6ysVVdz4zGL+MncFeTk5nDZuDy48Yk9GlvTY4XFl5ZWce8sMenXP554LpjBot27tVHHbamxq5sXF63l0zls8PncllbUNdC/I5fgx/fjY/ntw+KjdM/7vVJIkSdoZAwy1upXVWzjt188RAjyU4fPg73xxKd98aC6HjOjDTZ+b0OF6QrTU9MXr+NmTC5m+ZD39ehZy6dEj+dTEwRn1TX2MkX8sWMNvn3mDFxevp0eXPM6ZMpTzDhlGyQf4N/ZKRRWfvWU6Pbrkc++FUxjcOztDjMamZqYvWc8js1fwxLyVrN9UT/eCXI4b04+P7TeAI/bqa2ghSZKkDsUAQ21i/lsb+ORvnmfY7t2576KDMzIY+M0/3+CHf3mNY0eX8OvPjPfDHvD8G2u59smFzHyzkj2Ku3DpMSP55EGDE10Gs76xmWmvvMWNz7zBwlU1DCjuwvmHDeesSUMo+pD/ruYsq+acW6ZTVJjH3RdMZmif7q1cddtoao5MX7yOR+es4PG5K1m3qZ5uBbkct09qeshRextaSJIkqeMywFCb+fuC1Uy9o5SDhuzGjz+5f8Z8SIwx8tO/LuRXf1/EyfsP4NpPHUh+bnIf0DNNjJF/LVrLz55cyKzyKgb26srlx47kjPGD2vXPacOWBu6ZXs5tz73Jyg1bGN2/BxcesScfP2CPVqlj7vJUiNE1P5d7LpjCsN0z49/ntpqaIzOWvDs9ZG1NPV3zczl2nxL6XfnFAAAKyElEQVRO3n8AR+1dYmghSZKkTsEAQ23q4ZeX840/zaWhqZnLjx3FBYfvmei3+c3NkWsemc/tz7/JpyYM5gdn7EduTtj5gZ1QjJF/LlzDtU8u5JVl1Qzp3Y3j9ulHn6ICencvYLduqfve3fPp3b2Q4q75rfJnubJ6C7c9t4S7p5ezsa6RQ0b04cIj9uTIvfq+pzHnrpr/1gbOuWU6+bmBey6Ywp4ZtHLGS0srefjl5Tw2ZyVra+romp/LMfuUcPJ+qdAi2xquSpIkSbvKAENtbmX1Fr7z53n8Ze5KRpUU8YMz9mPisN7tXkdTc+TKB2dzX+kyvnDocL558j6t/oG4I4ox8vRrq/nV3xexYOVGauubtrtfCNCra3461Ng64NjqeVEBvdPbd+teQPeC3Hf+Dhau2siNzyzm4ZeX09Qc+eh+A7joiBHsN6i4Td/fgpUb+fRNL5KTkwoxRpYkG2Isq6zle4+8yuPzVtIlP4djRpfwsf324OjRfbN+uVtJkiRpVxhgqN08NX8V35o2j+VVmzl70hCuOHF0u634Ud/YzFf+8DKPzlnB5ceO4ivHjTK8+JC2NDRRWVvP+k3v3io31bO+toH1m+qo3NSQ2lZbz7r0a43N2//vSUFeDr27FVDUJY9Fq2vokp/DpyYMZurhe7Zrc83XV23k7JumA3DPBZMZ1W/Hq5m0hS0NTfz2n4u5/h+LyAmBy44ZyecPGZaR/WMkSZKkJBhgqF1tqmvk508t5JZ/LaF39wK+efIYTjlgjzYNE7Y0NHHJXWU8/dpqrvroaC48YkSbnUvvFWNkY10jlZveDTS2DTgqaxvYb2Axn50ylN26FyRS56LVNXz6phdpao7cfcEU9u7fPiFGjJGnXl3NNY/Mo2L9Zj62/wC+8dF92KNX13Y5vyRJkpQtDDCUiLnLq/nGn+bwyrJqDh+1O987bWybNPmsqWtk6h0zmb5kPd87bSyfmTy01c+hjmPxmhrOvulFGpoivz9/MmP26Nnm5/vOn+fzz4VrGFVSxHdO2ZdDRu7epueUJEmSspUBhhLT1By584U3+clfF7ZJk8+q2nrOvW0mc5dX89NPHsBp4wa2yrjq2N5cu4mzb3qRzQ1N/P78yYwd2Po9ODbVNfKrvy/i5mcX0yUvl/84fi8+d/BQV8ORJEmSdsAAQ4lbUb2Z70ybz+PzVrJXvyJ+cPp+TNjFJp9rNtbx2Vums3jNJq779DhO2Ld/K1WrzqB8XS1n3/QiNXWN/P78ya3WSDTGyJ9nr+AHj77Kyg1b+MT4Qfz3SXtT0qNLq4wvSZIkdWQGGMoYT81fxdUPz+Wt6i271ORzedVmPnvzdFZUb+HGzx3E4aP6tkG16ugq1tdy1o0vsmFLA3eeP5kDB/fapfFeW7mBbz08j+lL1jN2YE++c8pYDhq6WytVK0mSJHV8BhjKKJvqGrn2yYXc+twSencv5OqPj+Hj+w9ocZPPN9du4jM3T2fD5gZuPW9iIsu1quNYVpm6EqNqUwN3nD+J8UM+eOBQvbmBa59cyJ0vLqVHlzy+dsLenDVxCLk5roIjSZIkfRAGGMpIc5dXc9Wf5jB7WTVH7NWX7506liF9drys5oKVGznnluk0NjVzZxv1LlDn81bVZs6+6UXW1dRzxxcmctDQloVizc2R+8uW8aO/vMb62no+M3kI/3n83omtsiJJkiRlOwMMZay3m3z++IkFNDZHvnxcqsnn9hodvlJRxbm3zaAgN4e7pk5mVL/2WQJTncPK6i2cfdOLrN6whdvOm8Sk4TsOMWYvq+Lqh+fxckUVBw3dje+csq+BmiRJkrSLDDCU8bZu8rl3vx784Iyx//Yt+PTF6zj/jlJ6dcvn7qlTdnqlhvRhrN6whbNuepEVVVu49fMTOXhEn/fss35TPT9+4jXunVlBn+6FXPXR0Zw+bmCLp0BJkiRJen8GGMoaT85fxbfSTT4/PXkI/33CaGZVVPLF37/EwF5duWvqFPoXu5qD2s7qjVv49E3TWVZZy63nTuSQkbsD0NjUzN0zyvnpXxeyqa6Rzx8yjC8fN4oeXT54E1pJkiRJ22eAoazy700+C6je3MCokh787vxJ7F5UmHR56gTW1tTxmZum8+a6Tdx87gS65Ody9cPzeHXFBg4d2Ydvf3xfpzBJkiRJbcAAQ1lp7vJqvvnwXArzcvjtZydQ3NVvutV+1tXU8Zmbp7NodQ2NzZE9irvwPyeP4aSx/Z0uIkmSJLURAwxJ+hDWb6rn6/e/wj4DenLxUSPoVpCXdEmSJElSh/Z+AYa/iUvSDvTuXsDN505MugxJkiSp03vvOpWSJEmSJEkZxgBDkiRJkiRlPAMMSZIkSZKU8QwwJEmSJElSxjPAkCRJkiRJGc8AQ5IkSZIkZTwDDEmSJEmSlPEMMCRJkiRJUsZrUYARQjgxhLAghLAohHDFdl4vDCH8If369BDCsK1euzK9fUEI4YSdjRlCuCy9LYYQdt9qewgh/DL92uwQwvgP+6YlSZIkSVJ22WmAEULIBX4NnASMAc4OIYzZZrfzgcoY40jgWuBH6WPHAGcB+wInAteHEHJ3MuZzwHHA0m3OcRIwKn27ELjhg71VSZIkSZKUrVpyBcYkYFGMcXGMsR64Fzh1m31OBe5IP74fODaEENLb740x1sUYlwCL0uO975gxxlkxxje3U8epwO9iyotArxDCgA/yZiVJkiRJUnZqSYAxEKjY6vmy9Lbt7hNjbASqgT47OLYlY36YOiRJkiRJUgfU4Zp4hhAuDCGUhhBK16xZk3Q5kiRJkiSpFbQkwFgODN7q+aD0tu3uE0LIA4qBdTs4tiVjfpg6iDHeGGOcEGOc0Ldv350MKUmSJEmSskFLAoyZwKgQwvAQQgGpppzTttlnGnBu+vGZwNMxxpjeflZ6lZLhpBpwzmjhmNuaBnwuvRrJFKA6xriiBfVLkiRJkqQsl7ezHWKMjSGEy4AngFzg1hjjvBDCNUBpjHEacAtwZwhhEbCeVCBBer/7gPlAI3BpjLEJUsulbjtmevvlwNeB/sDsEMJjMcapwGPAR0k1Aq0FzmutPwRJkiRJkpTZQupCiY5pwoQJsbS0NOkyJEmSJElSC4UQXooxTth2e4dr4ilJkiRJkjqeDn0FRghhDbA06TokSZIkSVKLDY0xvmdVjg4dYEiSJEmSpI7BKSSSJEmSJCnjGWBIkiRJkqSMZ4AhSZIkSZIyXl7SBUiSJIUQ+gB/Sz/tDzQBa9LPa2OMhyRSmCRJyhg28ZQkSRklhPBtoCbG+JOka5EkSZnDKSSSJCmjhRBq0vdHhRD+GUJ4OISwOITwwxDCZ0IIM0IIc0III9L79Q0hPBBCmJm+HZrsO5AkSa3BAEOSJGWTA4AvAvsAnwX2ijFOAm4GvpTe5xfAtTHGicAn0q9JkqQsZw8MSZKUTWbGGFcAhBDeAP6a3j4HODr9+DhgTAjh7WN6hhCKYow17VqpJElqVQYYkiQpm9Rt9bh5q+fNvPt7TQ4wJca4pT0LkyRJbcspJJIkqaP5K+9OJyGEcGCCtUiSpFZigCFJkjqay4EJIYTZIYT5pHpmSJKkLOcyqpIkSZIkKeN5BYYkSZIkScp4BhiSJEmSJCnjGWBIkiRJkqSMZ4AhSZIkSZIyngGGJEmSJEnKeAYYkiRJkiQp4xlgSJIkSZKkjPf/AeMH1iHFkNYnAAAAAElFTkSuQmCC
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
<img src="data:image/png;base64,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CjBEREREREREJPAUYIiIiIiIiIhI4CnAEBEREREREZHAU4AhIiIiIiIiIoGnAENEREREREREAs+cc/EeQ1yYWQPwarzHISIiIiIiIiIHmOacKxr44JgNMEREREREREQkcWgJiYiIiIiIiIgEngIMEREREREREQk8BRgiIiIiIiIiEnip8R6AiIiISCwzmwj8zf92MtAHNPjftzvnXheXgYmIiEhcqYiniIiIBJaZfQVodc59J95jERERkfjSEhIRERFJGGbW6n8+x8z+YWb3mdk2M7vZzK4xs+fNbJ2ZlfvPKzKzlWb2gv9xRnxfgYiIiBwtBRgiIiKSqBYD7wfmAdcCc5xzpwC/BP7Lf84PgO87504GlvnbREREJAGpBoaIiIgkqhecczsBzGwr8Kj/+DrgDf7X5wLzzSy6T56Z5TjnWkd1pCIiInLMFGCIiIhIouqK+ToS832E/X/jhIDTnHOdozkwERERGX5aQiIiIiLJ7FH2LyfBzJbEcSwiIiJyDBRgiIiISDL7MHCSma01sw14NTNEREQkAamNqoiIiIiIiIgEnmZgiIiIiIiIiEjgKcAQERERERERkcBTgCEiIiIiIiIigacAQ0REREREREQCTwGGiIiIiIiIiASeAgwRERERERERCTwFGCIiIiIiIiISeAowRERERERERCTwFGCIiIiIiIiISOApwBARERERERGRwFOAISIiIiIiIiKBpwBDRERERERERAJPAYaIiIiMGDN7l5k9He9xHAkzO87MWs0sJd5jERERkf0UYIiIiMhBmdnDZvbVQR6/1MzqzCw1HuM6Fmb2Mz+gaDWzbjPrifn+IefcDudcjnOuL95jFRERkf0UYIiIiMih3Aa808xswOPXAnc553rjMKYjMjBkcc693w8ocoCvA7+Pfu+cuyA+oxQREZHDUYAhIiIih/InYCJwVvQBMxsPXAzc7n+fb2a3m1mDmb1qZl8wsyH9jWFmbzWz9WbWZGZPmNk8//FPm9mKAc/9gZn9MOacvzKznWZWY2Zfiy758JetPGNm3zez3cBXjuQFm9l0M3PR4MMf19fM7Fl/lsYDZjbRzO4ys31m9oKZTY/Zf66ZPWZme8xss5lddSTnFxERkcEpwBAREZGDcs51AH8Arot5+Cpgk3Ou0v/+R0A+MBN4vf/c/zjcsc1sDvBb4KNAEfAX4AEzSwd+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
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
<h3 id="UAL">UAL<a class="anchor-link" href="#UAL">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[351]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">UAL</span> <span class="o">=</span> <span class="n">drop_same_trade</span><span class="p">(</span><span class="n">UAL</span><span class="p">)</span>
<span class="n">UAL</span> <span class="o">=</span> <span class="n">time_condition_filter</span><span class="p">(</span><span class="n">UAL</span><span class="p">)</span>
<span class="n">UAL_results</span> <span class="o">=</span> <span class="n">get_results</span><span class="p">(</span><span class="n">UAL</span><span class="p">)</span>
<span class="n">plot_results</span><span class="p">(</span><span class="n">UAL_results</span><span class="p">)</span>
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
<h3 id="XOM">XOM<a class="anchor-link" href="#XOM">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[349]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">XOM</span> <span class="o">=</span> <span class="n">drop_same_trade</span><span class="p">(</span><span class="n">XOM</span><span class="p">)</span>
<span class="n">XOM</span> <span class="o">=</span> <span class="n">time_condition_filter</span><span class="p">(</span><span class="n">XOM</span><span class="p">)</span>
<span class="n">XOM_results</span> <span class="o">=</span> <span class="n">get_results</span><span class="p">(</span><span class="n">XOM</span><span class="p">)</span>
<span class="n">plot_results</span><span class="p">(</span><span class="n">XOM_results</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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MaYj8LjKGPOSMeZRY0yFMeb/M8Z8whjzljHmHWPMvMB+OcaYdcaYtwN/znX3FYiIiEgoKIEhIiIikWQJcCuwCLgJKLLWngH8DvhyYJ+fAbdba08Hrg08JyIiIhFOPTBEREQkkrxtrT0MYIzZBzwT2P4OcGHg64uBxcaY4DHpxphUa21HWCMVERGRkFICQ0RERCJJ75Cv/UO+9/Pu+xofcJa1tiecgYmIiMjEUgmJiIiIRJtneLecBGPMUhdjERERkRBRAkNERESizT8BK40x24wxO3F6ZoiIiEiE0xhVEREREREREfE8rcAQEREREREREc9TAkNEREREREREPE8JDBERERERERHxPCUwRERERERERMTzlMAQEREREREREc9TAkNEREREREREPE8JDBERERERERHxPCUwRERERERERMTzlMAQEREREREREc9TAkNEREREREREPE8JDBERERERERHxPCUwRERERERERMTzlMAQERGRkDLG/IMx5lW34xgNY8xMY0yHMSbG7VhERERkeEpgiIiIyHsYY542xvxgmO1XGmNqjTGxbsQ1HsaYOwIJig5jTJ8xpn/I909Zaw9Za1OttYNuxyoiIiLDUwJDREREjvUn4JPGGHPM9puAe621Ay7ENCrHJlmstbcGEhSpwP8FHgh+b6293J0oRUREZDSUwBAREZFjPQJMBc4PbjDGTAE+Atwd+D7DGHO3MabBGHPQGPOvxpgRva8wxlxhjNlhjDlijPmbMWZRYPu/GGPWHrPvz4wxPx9yzd8bYw4bY6qNMT8MlnwEylb+boy53RjTBHx/NC/YGDPbGGODiY9AXD80xrwWWKXxuDFmqjHmXmNMmzHmbWPM7CHHLzTGPGuMaTbG7DHGXD+a64uIiMjJKYEhIiIi72Gt7QYeBG4esvl6YLe1dmvg+18AGcBc4ILAvv94snMbY4qAvwBfBXKAJ4HHjTHxwP3Ah4wxaYF9YwLXvS9w+B+BAWA+sAy4FPjskNOfCVQAecCPRvOaj+MGnFUnhcA84HXgD0AWsAv490CcKcCzgThzA8f92hizOAQxiIiISIASGCIiIjKcPwFrjDGJge9vDmwLJhZuAL5jrW231h4Afopzs38yHwP+aq191lrbD/wESALOsdYeBDYBVwf2/SDQZa19wxiTB3wI+Kq1ttNaWw/cHogjqMZa+wtr7UAg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sT0VGCIiIiIiIiJieyowRERERERERMT2VGCIiIiIiIiIiO2pwBARERERERER21OBISIiIiIiIiK2pwJDRERERERERGzPME3T6gx1xjCMAiDL6hwiIiIiIiIicsJamaYZ9scPNugCQ0REREREREQaBm0hERERERERERHbU4EhIiIiIiIiIranAkNEREREREREbM/L6gAiIiIihmGEAEtqfhsJVAMFNb8vMU3zbEuCiYiIiG1oiKeIiIjYimEYjwFHTNN83uosIiIiYh/aQiIiIiK2ZhjGkZqfBxiG8b1hGDMNw9hpGMbThmFcYRjGWsMwfjYMo23N48IMw/jKMIx1NT/6WPtfICIiIrVBBYaIiIi4kiTg70A8cBUQa5pmL+Bt4B81j3kZeNE0zZ7AuJrPiYiIiIvTDAwRERFxJetM09wLYBjGDmBhzcd/BgbW/HowkGAYxq/PCTIMo5FpmkfqNamIiIjUKhUYIiIi4krKf/Nrx29+7+C/39d4AGeapllWn8FERESkbmkLiYiIiDQ0C/nvdhIMw+hiYRYRERGpJSowREREpKG5HehhGEaKYRipOGdmiIiIiIvTMaoiIiIiIiIiYntagSEiIiIiIiIitqcCQ0RERERERERsTwWGiIiIiIiIiNieCgwRERERERERsT0VGCIiIiIiIiJieyowRERERERERMT2VGCIiIiIiIiIiO39P5tzG/ACmqsNAAAAAElFTkSuQmCC
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
<h3 id="GPRO">GPRO<a class="anchor-link" href="#GPRO">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[352]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">GPRO</span> <span class="o">=</span> <span class="n">drop_same_trade</span><span class="p">(</span><span class="n">GPRO</span><span class="p">)</span>
<span class="n">GPRO</span> <span class="o">=</span> <span class="n">time_condition_filter</span><span class="p">(</span><span class="n">GPRO</span><span class="p">)</span>
<span class="n">GPRO_results</span> <span class="o">=</span> <span class="n">get_results</span><span class="p">(</span><span class="n">GPRO</span><span class="p">)</span>
<span class="n">plot_results</span><span class="p">(</span><span class="n">GPRO_results</span><span class="p">)</span>
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
    </div>
  </div>
</body>

 


</html>
