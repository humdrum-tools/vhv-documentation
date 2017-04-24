---
title: autobeam filter
author: Craig Stuart Sapp
creation_date: 23 Apr 2017
last_updated: 23 Apr 2017
tags: [all, filters]
sidebar: main_sidebar
verovio: true
keywords: interface commands 
summary: 
permalink: /filters/autobeam/index.html
---

The autobeam filter can be used to automatically add beams to notes
according to the prevailing meter.  Here is an example where the 
autobeam filter is being applied to the music, which contains one
measure of 3/4 music and another in 6/8.

{% include verovio.html
	source="meterchange"
	scale="60"
	pageWidth="1450"
	tabsize="16"
%}

<script type="application/json" id="meterchange">
!!!filter: autobeam
**kern
*M3/4
8c
8e
8d
8f
8g
8e
=
*M6/8
8c
8d
8e
8g
8f
8e
==
*-
</script>

Try deleting the filter from the above Humdrum data and see what happens.


In the VHV editor, you can also type <span class="keypress">alt-c</span>
to "compile" the filter, which will result in the beam markers being 
added to the data in the editor.  (The <span class="keypress">alt-c</span>
command will not work on this page, however).













