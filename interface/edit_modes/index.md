---
title: Edit modes and syntax highlighting
lang: en
ref: interface-edit_modes
author: Craig Stuart Sapp
creation_date: 19 Jun 2017
last_updated: 19 Jun 2017
tags: [all, getting_started]
keywords: interface color colorize coloring syntax highlighting
summary: "A Description of the two editing modes in VHV, and Humdrum syntax coloring."
sidebar: main_sidebar
permalink: /interface/edit_modes/index.html
---

Text editing in [Verovio Humdrum Viewer](http://verovio.humdrum.org) uses the
[ace](https://ace.c9.io/) editor.  There are two modes in which the
contents can be edited: (1) the initial simple-text editor 
(2) a vi editor useful to people who know [vi/vim](http://www.openvim.com/).
Switch between these two modes by pressing <span class="keypress">alt-v</span>.

## Plain-text mode ##

The Plain-text editing mode is indicated by a light background, closely matching the 
background color of the notation area of the page:

{% include image.html
	file="colorize-light.png"
	max-width="100%"
	alt="light-themed colorizing"
	caption="Light theme coloring for plain-text mode."
%}

When editing Humdrum files, their contents will be colored by syntactic function:

<style>
.light.colorlist tr,
.light.colorlist td,
.light tbody tr:nth-of-type(even),
.light tbody tr:nth-of-type(odd),
.light th,
.light tr,
.light td {
	background: #fdf6e3 !important;
}
.light td, .light th {
	color: black;
}

.colorlist td > div,
.colorlist td  {
	width: 80px;
}
</style>

<table style="width:100%" class="double">
<tr><td>
<table style="width:100%; padding:0; margin:0;" class="light colorlist">
<tr><th><div>example</div></th><th>meaning</th></tr>
<tr><td><div style="color:red">**kern</div></td><td>exclusive&nbsp;interpretations</td></tr>
<tr><td><div style="color:magenta">*^</div></td><td>spine manipulators</td></tr>
<tr><td><div style="color:darkviolet">*M4/4</div></td><td>tandem interpretations</td></tr>
<tr><td><div style="color:darkviolet; background: rgba(75,0,130,0.3)">*&gt;A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</div></td><td>section labels</td></tr>
<tr><td><div style="color:green">!!!OTL:</div></td><td>reference records</td></tr>
<tr><td><div style="color:blue">!! comment</div></td><td>global comments</td></tr>
<tr><td><div style="color:#2fc584">!bass</div></td><td>local comments</td></tr>
</table>
</td><td>
<table style="width:100%; padding:0; margin:0;" class="light colorlist">
<tr><th><div>example</div></th><th>meaning</th></tr>
<tr><td><div style="color:orange">!LO:N:vis=0</div></td><td>layout commands</td></tr>
<tr><td><div style="color:limegreen">!!!filter:&nbsp;autobeam</div></td><td>filters</td></tr>
<tr><td><div style="color:olive">!!!Xfilter:&nbsp;autobeam</div></td><td>used filters</td></tr>
<tr><td><div style="color:gray; background:rgba(0, 0, 0, 0.06);">=2</div></td><td>barlines</td></tr>
<tr><td><div style="color:gray">.</div></td><td>null tokens</td></tr>
<tr><td><div style="color:black">4E</div></td><td>data tokens</td></tr>
<tr><td><div style="background:#EEf3D5">&nbsp;&nbsp;&nbsp;</div></td><td>active cursor line</td></tr>
</table>
</td></tr>
</table>


## vi mode ##

{% include image.html
	file="colorize-dark.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Dark theme coloring for vi mode (<span class='keypress'>alt-v</span>)."
%}


Syntax coloring in vi mode:

<style>
.dark.colorlist tr,
.dark.colorlist td,
.dark tbody tr:nth-of-type(even),
.dark tbody tr:nth-of-type(odd),
.dark tr,
.dark th,
.dark td {
	background: #002b36 !important;
}
.dark td, .dark th {
	color: white;
}
table.colorlist tr td, table.colorlist td {
	hyphens: none;
}
</style>

<table style="width:100%" class="double">
<tr><td>
<table style="width:100%; padding:0; margin:0;" class="colorlist dark">
<tr><th><div>example</div></th><th>meaning</th></tr>
<tr><td><div style="color:red">**kern</div></td><td>exclusive&nbsp;interpretations</td></tr>
<tr><td><div style="color:magenta">*^</div></td><td>spine manipulators</td></tr>
<tr><td><div style="color:darkviolet">*M4/4</div></td><td>tandem interpretations</td></tr>
<tr><td><div style="color:darkviolet; background: rgba(255,200,255,0.6)">*&gt;A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</div></td><td>section labels</td></tr>
<tr><td><div style="color:green">!!!OTL:</div></td><td>reference records</td></tr>
<tr><td><div style="color:lightblue">!! comment</div></td><td>global comments</td></tr>
<tr><td><div style="color:#2fc584">!bass</div></td><td>local comments</td></tr>
</table>
</td><td>
<table style="width:100%; padding:0; margin:0;" class="colorlist dark">
<tr><th><div>example</div></th><th>meaning</th></tr>
<tr><td><div style="color:orange">!LO:N:vis=0</div></td><td>layout commands</td></tr>
<tr><td><div style="color:chartreuse">!!!filter:&nbsp;autobeam</div></td><td>filters</td></tr>
<tr><td><div style="color:olive">!!!Xfilter:&nbsp;autobeam</div></td><td>used filters</td></tr>
<tr><td><div style="color:gray; background:#1f454e;">=2</div></td><td>barlines</td></tr>
<tr><td><div style="color:gray">.</div></td><td>null tokens</td></tr>
<tr><td><div style="color:white">4E</div></td><td>data tokens</td></tr>
<tr><td><div style="color:white; background:#194a40">&nbsp;&nbsp;&nbsp;  </div></td><td>active cursor line</td></tr>
</table>
</td></tr>
</table>

## Basic syntax error highlighting ##


### Tab syntax errors ###

Tabs cannot start a line, end a line, or occur more than once between tokens in the Humdrum 
syntax.  Any of these invalid cases will be highlighted in red:

<style>
table.double {
	width: 100%;
	border: none !important;
	max-width: 100%;
}
.double td {
	width: 50% !important;
}
.double tr, .double td, .double tbody tr:nth-of-type(odd) {
	background: none !important;
}
.double tbody tr td {
	border: none !important;
}
</style>

<table class="double"><tr><td>

{% include image.html
	file="taberror-light.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Tab errors in plain-text theme."
%}

</td><td>

{% include image.html
	file="taberror-dark.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Tab errors in vi theme."
%}


</td></tr></table>


### Space syntax warnings ###

Generally tokens do not start or end with space characters, and multiple sub-tokens 
are separated by a single space (in data formats such as `**kern`).  When a token starts
or ends with a space, or there is more than one space between subtokens, the space will be highlighted
in blue.  Usually this is a syntax error that should be fixed.


<table class="double"><tr><td>

{% include image.html
	file="spacewarning-light.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Space warnings in plain-text theme."
%}

</td><td>

{% include image.html
	file="spacewarning-dark.png"
	max-width="100%"
	alt="dark-themed colorizing"
	caption="Space warnings in vi theme."
%}


</td></tr></table>


## Syntax files ##

Here are the Humdrum syntax parsing/highlighting files for the ace editor:

* [mode-humdrum.js](https://github.com/humdrum-tools/verovio-humdrum-viewer/blob/gh-pages/scripts/ace/mode-humdrum.js): syntax parsing file
* [theme-humdrum_light.js](https://github.com/humdrum-tools/verovio-humdrum-viewer/blob/gh-pages/scripts/ace/theme-humdrum_light.js) light-colored highlighting theme
* [theme-humdrum_dark.js](https://github.com/humdrum-tools/verovio-humdrum-viewer/blob/gh-pages/scripts/ace/theme-humdrum_dark.js) dark-colored highlighting theme


