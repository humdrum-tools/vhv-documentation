---
title: Toolbar
lang: en
ref: interface-toolbar
author: Craig Stuart Sapp
translator: 
creation_date: 24 Aug 2020
translation_date: 
last_updated: 24 Aug 2020
tags: [all, getting_started]
keywords: interface toolbar
summary: "A Description of the VHV toolbar."
sidebar: main_sidebar
permalink: /interface/toolbar/index.html
---

{% include_relative style-local.html %}

A toolbar for quick access of basic display, editing and data-processing
functions is found in the upper right-hand corner of the VHV window:

{% include image.html
	file="toolbar.png"
	alt="VHV main page showing toolbar"
	caption="Main toolbar in VHV window, circled in red."
%}



## Main toolbar ##

<br>

<div class="toolbar" id="toolbar-1">
	<div title="Hide text editor (alt-y)" class='nav-icon fas fa-file-pdf'></div>
	<div title="Hide text editor (alt-y)" class='nav-icon fas fa-eye'></div>
	<div title="Clear editor contents (alt-e)" class='nav-icon fas fa-eraser'></div>
	<div title="Undo last change (ctrl-z)" class='nav-icon fas fa-undo'></div>
	<div title="Make text smaller" class='nav-icon fas fa-minus-circle'></div>
	<div title="Make text larger" class='nav-icon fas fa-plus-circle'></div>
	<div title="Decrease tab size (alt-<)" class='nav-icon fas fa-outdent'></div>
	<div title="Increase tab size (alt->)" class='nav-icon fas fa-indent'></div>
	<div title="Collapse tabs" class='nav-icon fa fa-compress'></div>
	<div title="Expand tabs to align spines" class='nav-icon fa fa-expand'></div>
	<div title="Click to freeze notation (alt-f)" class='nav-icon fas fa-unlock'></div>
	<div title="Make notation smaller" class='nav-icon fas fa-minus-square'></div>
	<div title="Make notation larger" class='nav-icon fas fa-plus-square'></div>
	<div title="Click to use embedded line breaks (if any)" class='nav-icon fas fa-align-center'></div>
	<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
</div>

<br>

The main toolbar allows you to resize the text/music, change the
tab size, as well as other functions described below.  If you move
your mouse over any icon in the toolbar, a tooltip will appear after
a few seconds that gives a brief description of that button.  You can
also try this hover feature on the demo toolbar above (although clicking
will have no effect on the toolbars on this documentation page).

The table below gives a description for each icon in the main
toolbar, with any associated keyboard shortcut given underneath the
icon.  For keyboard shortcuts, note that <span class="keypress">alt</span>
on Linux/Windows computers is usually called <span
class="keypress">option</span> on MacOS computers.  In addition,
<span class="keypress">control</span> for Linux/Windows users is
instead <span class="keypress">command</span> in MacOS.

<br>


<table class="toolbar-info">

<tr><td>
<div class="toolbar">
	<div title="Hide text editor (alt-y)" class='nav-icon fas fa-file-pdf'></div>
</div>
	<span class="keypress">alt-p</span>
	<span class="keypress">#+alt-p</span>
</td>
<td>

	If a scan of the source edition is available, one or more
	of these PDF-file icons appear on the left side of the main
	toolbar.  The URL for the icon will either come automatically
	from the repertory source, or may be stored within the data
	on a reference-record line having the form <code
	class="mine">!!!URL-pdf: <i>URL</i> <i>[description]</i></code>.
	If a description is given after the URL, it will be used
	as the tooltip for button.  Additional PDFs can be displayed,
	such as adding "2" for a second PDF: <code
	class="mine">!!!URL2-pdf:</code>.  The keyboard shortcut
	to open any second source URL is <span
	class="keypress">2+alt-p</span>.

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Hide text editor (alt-y)" class='nav-icon fas fa-eye'></div>
</div>
<br>
	<span class="keypress">alt-y</span>
</td>
<td>

	This button toggles text-editor visibility on the left side
	of the VHV window.  By default the text editor is visible
	when you open VHV in a web browser.  To start with it hidden,
	add the URL parameter <code class="mine">k=y</code>.  You
	can also suppress display of the splash music by adding the
	letter <code class="mine">e</code> to the <code
	class="mine">k</code>, parameter.  Here is a link to <a
	target="_blank"
	href="https://verovio.humdrum.org?file=beethoven/sonatas/sonata14-1.krn&k=ey">
	Beethoven's Moonlight sonata, movement 1</a> that demonstrates
	this feature.  Also note that when the text editor is hidden,
	toolbar icons related to the text editor are also hidden.

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Clear editor contents (alt-e)" class='nav-icon fas fa-eraser'></div>
</div>
	<span class="keypress">alt-e</span>
</td>
<td>

	This button will erase the contents of the text editor.  If
	you click on this by accident, clicking again on the button
	will restore the contents that you erased.

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Undo last change (ctrl-z)" class='nav-icon fas fa-undo'></div>
</div>
	<span class="keypress">control-z</span>
</td>
<td>

	Undo the last change in the text editor.  This works for
	both manual or automatic changes (such as filtering) made
	to the text.

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Make text smaller" class='nav-icon fas fa-minus-circle'></div>
</div>
</td>
<td>

	This button decreases the text editor's font size.  Also
	see the music size buttons further to the right, which are
	similar, but have a square shape.  You can also decrease the
	font size of the text and music together from the web browser's
	zoom controls (<span class="keypress">control-minus</span>).

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Make text larger" class='nav-icon fas fa-plus-circle'></div>
</div>
</td>
<td>

	This button increases the text editor's font size.  Also
	see the music size buttons further to the right, which are
	similar, but have a square shape.  You can also increase
	the font size of the text and music together from the web
	browser's zoom controls (<span
	class="keypress">control-plus</span>).

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Decrease tab size (alt-<)" class='nav-icon fas fa-outdent'></div>
</div>
	<span class="keypress">alt-&lt;</span>
</td>
<td>

	Decrease the text editor's tab size.  This narrows the width
	of Humdrum spines so that more are visible; however, columns
	wider than the tab size will become visually misaligned,
	decreasing readability.

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Increase tab size (alt->)" class='nav-icon fas fa-indent'></div>
</div>
	<span class="keypress">alt-&gt;</span>
</td>
<td>

	Increase the text editor's tab size.  This increases the width of Humdrum spines so that
	spines are more likely to be vertically aligned properly;
	however, fewer spines may be visible (but you can scroll in the text editor to view
	content that is not visible).

</td>
</tr>


<tr><td>
<div class="toolbar">
	<div title="Collapse tabs" class='nav-icon fa fa-compress'></div>
</div>
</td>
<td>

	Collapse tabs so that there is only one tab between each
	token on a data line.  In general data should be saved in
	this format so that the files can be used with the Humdrum
	Toolkit. <a target="_blank"
	href="https://humlib.humdrum.org">Humlib</a> tools do not
	care how many tabs separate each token, so the tab state
	of the data will not matter when using filters in VHV.

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Expand tabs to align spines" class='nav-icon fa fa-expand'></div>
</div>
</td>
<td>

	Add tabs after each spine to give a constant width to the spine through the
	length of the file.  This adds an extra tab for each subspine less than the
	maximum count for the spine.  When this button is clicked, all primary spines
	are aligned in the same column, as well as all subspines.  This makes editing
	Humdrum data for piano music much more easier since the melodic sequence
	remains in a single column rather than jumping around based on spine splits
	and merges in other spines to the left.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Click to freeze notation (alt-f)" class='nav-icon fas fa-unlock'></div>
</div>
<div class="toolbar">
	<div title="Click to unfreeze notation (alt-f)" class='nav-icon fas fa-lock'></div>
</div>
	<span class="keypress">alt-f</span>
</td>
<td>

	Toggle dynamic notation generation.  When unlocked, any changes in the
	text editor will be immediately rendered into music notation.  Locking the
	notation is useful in the case of long scores that take a while to 
	render.  In such cases, it may be useful to stop rendering the
	notation temporarily so that edits can be done more quickly.  
	When the notation is "frozen" the background color is white, and
	while "unfrozen" the background is off-white.

</td>
</tr>





<tr><td>
<div class="toolbar">
	<div title="Make notation smaller" class='nav-icon fas fa-minus-square'></div>
</div>
</td>
<td>

	This button decreases the music notation size.  Also
	see the text size buttons further to the left, which are
	similar, but have a circular shape.  You can also decrease the
	size of the text and music together from the web browser's
	zoom controls (<span class="keypress">control-plus</span>).

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Make notation larger" class='nav-icon fas fa-plus-square'></div>
</div>
</td>
<td>

	This button increases the music notation size.  Also
	see the text size buttons further to the left, which are
	similar, but have a circular shape.  You can also increase the
	size of the text and music together from the web browser's
	zoom controls (<span class="keypress">control-plus</span>).

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Click to use embedded line breaks (if any)" class='nav-icon fas fa-align-center'></div>
</div>
<div class="toolbar">
	<div title="Click to use automatic line breaks (if any)" class='nav-icon fas fa-align-justify'></div>
</div>
</td>
<td>

	Toggle between line breaks explicitly encoded in the data
	or allow the line breaking of the music to be handled
	automatically.  For data entry, encoded line breaks are
	better, while displaying the music in an different aspect
	ratio or size will require automatic line breaking.  When
	this icon has uneven horizontal lines, the automatic mode
	is set, and when all lines are equal in length, the embedded
	line break mode is active.

</td>
</tr>

<tr><td>
<div class="toolbar">
	<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
</div>
	<span class="keypress">alt-n</span>
	<span class="keypress">#-alt-n</span>
</td>
<td>

	This last icon of all toolbars is the toolbar cycling button.
	Click on this button to navigate to the next toolbar menu.
	To go to a specific toolbar, type the number for that toolbar
	before using the next-toolbar shortcut, such as <span
	class="keypress">3+alt-n</span> to go to the third toolbar
	(currently the buffer loading toolbar, which is described
	below).

</td>
</tr>

</table>




## Buffer save toolbar ##

<br>

<div style="padding-bottom:8px;" class="toolbar" id="toolbar-2">
	<span class="nav-icon no-highlight" style="font-style: italic">Save</span>
	<span id="save-1" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">1</strong></span>
	<span id="save-2" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">2</strong></span>
	<span id="save-3" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">3</strong></span>
	<span id="save-4" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">4</strong></span>
	<span id="save-5" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">5</strong></span>
	<span id="save-6" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">6</strong></span>
	<span id="save-7" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">7</strong></span>
	<span id="save-8" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">8</strong></span>
	<span id="save-9" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">9</strong></span>
	<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
</div>

<br>

The buffer-saving toolbar is used to save the current contents of
the text editor to one of nine buffers in the web browser.  These
buffers can be reloaded into the text editor from the next toolbar
menu (<span class="keypress">alt-n</span> moves you to the next
toolbar, or click on the toolbar-cycle button to go to the loading
toolbar).

When a buffer has contents, its corresponding save button will be
highlighted in red.  This is demonstrated in the sample toolbar
above, where buttons for buffers 3, 5, 7, and 8 are filled with
some contents.  This is useful for knowing which buffers have
contents as well as helps prevent you from accidentally erasing
previously stored contents.  If you want to erase the contents of
a buffer, save the contents of the text editor when it has nothing
in it, or <span class="keypress">shift-click</span> on the buffer
icon to erase its contents as well.

Tooltips for filled buffers give the title of the data when it was
stored.  The tooltip matches the description given at the top of
the VHV page, and is typically the composer and title, coming from
the <code class="mine">!!!COM:</code> <code class="mine">!!!OTL:</code>
reference records; however, a different format for the description
at the top of the page (and for this tooltip) can be made using the
<code class="mine">!!!title:</code> reference record.

Keyboard shortcuts allow saving to the buffers without the need to view
or click on the buffer-save toolbar.  First type the number of the
buffer to save (<span class="keypress">1</span>
through
<span class="keypress">9</span>) and then press
<span class="keypress">alt-shift-S</span> to save to that particular buffer.



## Buffer load toolbar ##

<br>

<div style="padding-bottom:8px;" class="toolbar" id="toolbar-3">
	<span class="nav-icon no-highlight" style="font-style: italic">Load</span>
	<span id="load-1" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">1</strong></span>
	<span id="load-2" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">2</strong></span>
	<span id="load-3" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">3</strong></span>
	<span id="load-4" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">4</strong></span>
	<span id="load-5" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">5</strong></span>
	<span id="load-6" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">6</strong></span>
	<span id="load-7" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">7</strong></span>
	<span id="load-8" class="filled nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">8</strong></span>
	<span id="load-9" class="nav-icon fa-stack"><span class="fa fa-square fa-stack-2x"></span><strong class="fa-stack-1x">9</strong></span>
	<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
</div>


<br>

The load toolbar is structured in a similar manner to the save
toolbar: clicking on a numbered button will load the contents of
the buffer into the text editor.  Buffers that have contents are
highlighted in green.  The above demo toolbar has contents in buffers
3, 5, 7, and 8 that is available to load into the text editor.
Trying to load an empty buffer will have no effect (use the <span
class="keypress">alt-e</span> to otherwise clear the contents of
the text editor).  View the title of the contents (if any) as a
tooltip on the button.


Keyboard shortcuts allow loading from the buffers without the need
to view or click on the buffer-load toolbar.  First type the number
of the buffer to load (<span class="keypress">1</span> through <span
class="keypress">9</span>) and then press <span
class="keypress">alt-shift-R</span> (meaning "Restore") to load to
that particular buffer.  There is also a special buffer called <span
class="keypress">0</span> that saves the current contents of the
the buffer automatically once every minute.  To recall the contents
of this buffer, type <span class="keypress">0+alt-shift-R</span>.
Usually <span class="keypress">control-z</span> serves a similar
function to undo changes to the text.


## Hiding the toolbar ##

To hide the toolbar, type <span class="keypress">alt-shift-N</span>.
Typing that shortcut again will cause the toolbar to reappear.  You
can also show/hide the toolbar from the "View &rarr; Toggle toolbar
visibility" menu entry.

If you want to hide the toolbar when loading VHV, add the parameter
<code class="mine">k=N</code> to the URL.  Here is a link to <a
target="_blank"
href="https://verovio.humdrum.org?file=mozart/sonatas/sonata11-3.krn&k=eyN">Mozart's
Turkish march</a> demonstrating this feature.




