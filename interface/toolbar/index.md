---
title: Toolbar
lang: en es
ref: interface-toolbar
author: Craig Stuart Sapp
translator: 
creation_date: 24 Aug 2020
translation_date: 
last_updated: 3 Sep 2020
tags: [all, getting_started]
keywords: interface toolbar
summary: "A Description of the VHV toolbar."
sidebar: main_sidebar
vim: ts=3
permalink: /interface/toolbar/index.html
---

{% include_relative style-local.html %}

A toolbar for quick access to basic display, editing, searching and
data-processing funcionality sits at the upper right-hand corner of
the VHV window:

{% include image.html
	file="toolbar.png"
	alt="VHV main page showing toolbar"
	caption="Main toolbar in VHV window, circled in red."
%}



## Main toolbar ##

<br>

{% include_relative main-toolbar.md %}



## Buffer save toolbar ##

<br>

{% include_relative save-toolbar.md %}



## Buffer load toolbar ##

<br>

{% include_relative load-toolbar.md %}



## Search toolbar ##

<br>

{% include_relative search-toolbar.md %}



## Filter toolbar ##

<br>

{% include_relative filter-toolbar.md %}



## Spreadsheet toolbar ##

<br>

{% include_relative spreadsheet-toolbar.md %}



## Hiding the toolbar ##

To hide the toolbar, type <span class="keypress">alt-shift-N</span>.
Typing that shortcut again will cause the toolbar to reappear.  You
can also show/hide the toolbar from the "View &rarr; Toggle toolbar
visibility" menu entry.  The shortcut <span
class="keypress">alt-shift-E</span> will toggle display of both the
menu and the toolbar.

If you want to hide the toolbar when loading VHV, add the parameter
<code class="mine">k=N</code> to the URL.  Here is a link to <a
target="_blank"
href="https://verovio.humdrum.org?file=mozart/sonatas/sonata11-3.krn&k=eyN">Mozart's
Turkish march</a> demonstrating this feature.




