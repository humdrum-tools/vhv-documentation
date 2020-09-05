
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
