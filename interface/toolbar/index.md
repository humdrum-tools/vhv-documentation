---
title: Toolbar
lang: en
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
	<div title="About the toolbar" class='nav-icon fas fa-question-circle'></div>
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
<span class="keypress">control</span> for Linux/Windows is instead
<span class="keypress">command</span> in MacOS.

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
	of these icons will appear to the left of the main toolbar.

	The link for the icon may be stored within the data on a
	reference-record line having the form <code
	class="mine">!!!URL-pdf: <i>URL</i> <i>[description]</i></code>.

	Additional PDF icons can be displayed, such as adding "2"
	for a second PDF: <code class="mine">!!!URL2-pdf:</code>.

	The keyboard shortcut to open any second source URL is <span
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
	<span class="summary-icon">Toggle text-editor visibility.</span>

	By default the text editor is initially visible.

	To start with it hidden, add the URL parameter <code
	class="mine">k=y</code>.

	Here is a link to <a target="_blank"
	href="https://verovio.humdrum.org?file=beethoven/sonatas/sonata14-1.krn&k=ey">
	Beethoven's Moonlight sonata, movement 1</a> that demonstrates
	this feature (also adding "e" to suppress the splash music).

	Also note that when the text editor is hidden, toolbar icons
	related to the text editor will also be hidden.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Clear editor contents (alt-e)" class='nav-icon fas fa-eraser'></div>
</div>
	<span class="keypress">alt-e</span>
</td>
<td>

	<span class="summary-icon">Erase contents of text editor.</span>

	If you click on this accidentally, click again to restore
	the contents just erased.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Undo last change (ctrl-z)" class='nav-icon fas fa-undo'></div>
</div>
	<span class="keypress">control-z</span>
</td>
<td>

	<span class="summary-icon">Undo last change in text editor.</span>

	This works for both manual or automatic changes made to the
	text (such as filtering).

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Make text smaller" class='nav-icon fas fa-minus-circle'></div>
</div>
</td>
<td>

	<span class="summary-icon">Decrease text editor's font size.</span>

	Also see the square sizing buttons further to the right,
	which have a similar effect on the music notation.

	You can also decrease the font size of the text and music
	together from the web browser's zoom controls (<span
	class="keypress">control-minus</span>).

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Make text larger" class='nav-icon fas fa-plus-circle'></div>
</div>
</td>
<td>

	<span class="summary-icon">Increase text editor's font size.</span>

	Also see the square sizing buttons further to the right,
	which have a similar effect on the music notation.

	You can also increase the font size of the text and music
	together from the web browser's zoom controls (<span
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

	<span class="summary-icon">Decrease text editor's tab size.</span>

	This narrows the width of Humdrum spines so that more are
	visible; however, columns wider than the tab size will
	become visually misaligned, decreasing readability.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Increase tab size (alt->)" class='nav-icon fas fa-indent'></div>
</div>
	<span class="keypress">alt-&gt;</span>
</td>
<td>

	<span class="summary-icon">Increase text editor's tab size.</span>

	This increases the width of Humdrum spines so that spines
	are more likely to be vertically aligned properly; however,
	fewer spines may become visible (but you can scroll in the
	text editor to view content that is not visible).

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Collapse tabs" class='nav-icon fa fa-compress'></div>
</div>
</td>
<td>

	<span class="summary-icon">Collapse Humdrum tabbing.</span>

	This forces only one tab between each token on a data line.

	In general data should be saved in this format so that the
	files can be used with the original Humdrum Toolkit; however,
	<a target="_blank" href="https://humlib.humdrum.org">Humlib</a>
	tools do not care how many tabs separate each token.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Expand tabs to align spines" class='nav-icon fa fa-expand'></div>
</div>
</td>
<td>

	<span class="summary-icon">Expand Humdrum tabbing.</span>

	This ensures that the data in each spine remains in the
	same column.

	For example if a spine contains a split at some point in
	the data, regions of the spine before and after the split
	will have an extra tab inserted so that the next spine's
	data is vertically aligned in the same column.

	This facilitates piano-music editing, since melodic sequences
	remain in a single column rather than jumping around based
	on spine splits and merges in other spines to the left.

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

	<span class="summary-icon">Toggle dynamic notation generation.</span>

	When unlocked, any changes in the text editor will be
	rendered immediately into music notation.

	Locking the notation is useful when editing long pieces
	that take a while to render, allowing text edits to not
	get bogged down by the music-rendering process.

	When the notation is "frozen" the background color is white,
	and when "unfrozen" the background is off-white.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Make notation smaller" class='nav-icon fas fa-minus-square'></div>
</div>
</td>
<td>

	<span class="summary-icon">Decrease music notation size.</span>

	Also see the circular sizing buttons further to the left,
	which have a similar effect on the text editor's font size.

	You can also decrease the size of the text and music together
	from the web browser's zoom controls (<span
	class="keypress">control-minus</span>).

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Make notation larger" class='nav-icon fas fa-plus-square'></div>
</div>
</td>
<td>

	<span class="summary-icon">Increase music notation size.</span>

	Also see the circular sizing buttons further to the left,
	which have a similar effect on the text editor's font size.

	You can also increase the size of the text and music together
	from the web browser's zoom controls (<span
	class="keypress">control-plus</span>).

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
	<span class="summary-icon">Line breaking method.</span>

	Toggle between explicit line breaks and automatic line
	breaking.

	The uneven horizontal-line icon indicates automatic mode
	is active, while even horizontal lines mean encoded breaks
	are used.

	If there are no encoded breaks, automatic mode will be used
	in both states.

	For data entry, encoded line breaks are better for visual
	alignment with the source edition; however, displaying music
	with an different aspect ratio or size may make automatic
	line breaking more desirable.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="About the toolbar" class='nav-icon fa fa-question-circle'></div>
</div>
</td>
<td>

	Show this documentation page.

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

	<span class="summary-icon">Go to next toolbar.</span>
	
	To go to a specific toolbar directly, type the number for
	that toolbar before using the next-toolbar shortcut.

	For example <span class="keypress">3+alt-n</span> takes you
	to the third toolbar (the buffer loading toolbar, described
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

The save toolbar is used to save the current contents of the text
editor to one of nine buffers in the web browser.  These buffers
can be reloaded into the text editor from the next toolbar menu
(<span class="keypress">alt-n</span> moves you to the next toolbar,
or click on the toolbar-cycle button to go to the loading toolbar).

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

## Search toolbar ##

<div class="toolbar" id="toolbar-4">
	<span id="search-results" style="vertical-align: 6%; font-style: italic" class="nav-icon">Search</span>
	<span id="search-group">
		<input id="search-pitch"    type="text" spellcheck="false" placeholder="pitch">
		<input id="search-interval" type="text" spellcheck="false" placeholder="interval">
		<input id="search-rhythm"   type="text" spellcheck="false" placeholder="rhythm">
	</span>
	<div title="Search help" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br><br>
See the [documentation page for searching](/interface/search).


## Filter toolbar ##

<div class="toolbar" id="toolbar-5">
	<input id="filter"  type="text" spellcheck="false" placeholder="filter">
	<div title="Apply filter" class='filter-icon nav-icon fa fa-filter'></div>
	<div id="filter-compile" title="Compile filter (alt-c)" class='nav-icon fa fa-plus'></div>
	<div title="About filters" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br><br>
See the [documentation page for filtering](/filter).


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




