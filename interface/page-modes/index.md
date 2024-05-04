---
title: Single- and multi-page modes
lang: en 
page_language: en
author: Craig Stuart Sapp
creation_date: 4 May 2024
last_updated: 4 May 2024
ref: interface-toolbar
tags: [all, getting_started]
keywords: interface multi-page single-page modes
summary: "Description of the the single- and multi-page display modes."
sidebar: main_sidebar
vim: ts=3
permalink: /interface/page-modes/index.html
---

{% include_relative style-local.html %}

There are two page display modes in VHV: either show the entire score on 
a single vertically scrollable page, or a multi-page mode, where each
page displays the maximum number of systems that can fit in the 
visible browser window.

By default when opening the VHV webiste, single-page mode is active.  When
in single-page mode, the page state is visible under the playback button, using
this symbol:

<div style="padding-bottom:8px;" class="toolbar" id="toolbar-3">
	<div title="switch to multi-page mode (better for MIDI playback)" class='nav-icon fa fa-map'></div>
</div>


<br/>
<br/>

To switch to multi-page mode, click on this icon, which will be replaced
with these icons:

<div style="padding-bottom:8px; padding-top:8px;" class="toolbar" id="toolbar-3">
            <div title="Previous page (shift-click for first page)" style="padding-top:10px; font-size:150%" class="nav-icon fas fa-arrow-left"></div>
            <div title="switch to single-page mode" style="padding-top:10px; font-size:125%" class="nav-icon fas fa-file-alt"></div>
            <div title="Next page (shift-click for last page)" style="padding-top:10px; font-size:150%" class="nav-icon fas fa-arrow-right"></div>
</div>

* Click on the right arrow to advance to the next page.
* Click on the left arrow to go back one page.
* Click on the center icon to return to single-page mode.
* Shift-click on left arrow to go to first page.
* Shift-click on right arrow to go to last page.


## MIDI playback

Multi-page mode is generally better for MIDI playback (play MIDI
file by pressing the triangle icon above the the page-mode icon).
Large scores tax computer resources, so MIDI playback will not be
smooth when the music is approximately longer than 10 printable page.

When in multi-page mode, the pages will be turned automatically when
playback begins another page.  In single-page mode, you have to scroll
manually to view the playback point in the score.




