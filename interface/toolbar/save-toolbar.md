
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
