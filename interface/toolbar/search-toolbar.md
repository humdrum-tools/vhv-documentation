

<div class="toolbar" id="toolbar-4">
	<span id="search-results" style="vertical-align: 6%; font-style: italic" class="nav-icon">Search</span>
	<span id="search-group">
		<input id="search-pitch"    type="text" spellcheck="false" placeholder="pitch">
		<input id="search-interval" type="text" spellcheck="false" placeholder="interval">
		<input id="search-rhythm"   type="text" spellcheck="false" placeholder="rhythm">
	</span>
	<div title="Melodically searching highest note of chord" class='nav-icon fa fa-hand-o-up'></div>
	<div title="Show only measures with matches" class='nav-icon fa fa-search-minus'></div>
	<div title="Search help" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br>

The search toolbar allows you to locate musical features in the
score.  Type features into the appropriate pitch, interval and
rhythm boxes on the toolbar and the matches will be highlighted in
the score.  Features can be searched in tandem, such as the
pitch sequence "cdefg" starting on a rhythm of "1" (whole note).
As you type in the search fields, the number of matches will be
displayed to the left of the search boxes:

<div style="margin-left: 50px;" class="toolbar" id="toolbar-4">
	<span id="search-results" style="vertical-align: 6%; margin-bottom:5px; font-size:2.25rem; font-style: italic" class="nav-icon">5 matches</span>
	<span id="search-group">
		<input id="search-pitch"    value="cefg" type="text" spellcheck="false" placeholder="pitch">
		<input id="search-interval" type="text" spellcheck="false" placeholder="interval">
		<input id="search-rhythm"   value="1" type="text" spellcheck="false" placeholder="rhythm">
	</span>
	<div title="Melodically searching highest note of chord" class='nav-icon fa fa-hand-o-up'></div>
	<div title="Show only measures with matches" class='nav-icon fa fa-search-minus'></div>
	<div title="Search help" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>


<br>

<table class="toolbar-info">

<tr><td>
<div style="font-size:3rem !important;" class="toolbar">
	<span id="search-group">
		<input id="search-pitch" type="text" autocomplete="off" spellcheck="false" placeholder="pitch">
	</span>
</div>
</td>
<td>

	<span class="summary-icon">Pitch-class search box.</span>

	Type the letters A through G (case insensitive) to search
	by pitch class.  Add optional chromatic alterations after
	the name: "n" for natural, "-" for flat, and "#" for sharp.
	Spaces between notes are optional.

</td>
</tr>

<tr><td>
<div style="font-size:3rem !important;" class="toolbar">
	<span id="search-group">
		<input id="search-interval" type="text" autocomplete="off" spellcheck="false" placeholder="interval">
	</span>
</div>
</td>
<td>

	<span class="summary-icon">Interval search box.</span>

	Type the numbers 1 through 9 with an optional minus sign
	for falling intervals.  "1" means a repeated note, "2" is
	a step "3" is a third, and so on.  "-3" means a third down.
	Spaces between intervals are optional.

</td>
</tr>



<tr><td>
<div style="font-size:3rem !important;" class="toolbar">
	<span id="search-group">
		<input id="search-rhythm" type="text" autocomplete="off" spellcheck="false" placeholder="rhythm">
	</span>
</div>
</td>
<td>

	<span class="summary-icon">Rhythm search box.</span>

	Type rhythms as numbers, such as "1" for whole note, "2"
	for half note, "4" for quarter note, and so on.  Numbers
	can be followed by one or more augmentation dots (".").
	Spaces are optional, and rhytms such as "16", "32" and "64"
	will be automatically parsed.  Only power of two rhythms
	available at this time.

</td>
</tr>


<tr><td>
<div class="toolbar">
	<div title="Melodically searching highest note of chord" class='nav-icon fa fa-hand-o-up'></div>
<br>
	<div title="Melodically searching highest note of chord" class='nav-icon fa fa-hand-o-down'></div>
</div>
</td>
<td>

	<span class="summary-icon">Search note of chord.</span>

	If the music contains chords, choose either the highest
	note (up-pointing icon), or the lowest note (down-pointing
	icon) when searching for melodic patterns.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Show only measures with matches" class='nav-icon fa fa-search-minus'></div>
<br>
	<div title="Show only measures with matches" class='nav-icon fa fa-search-plus'></div>
</div>
</td>
<td>

	<span class="summary-icon">Compressed/Expanded results view.</span>

	This button controls the display search matches:
	either show the entire score, or show only measures that
	contain matches.

</td>
</tr>



<tr><td>
<div class="toolbar">
	<div title="Show only measures with matches" class='nav-icon fa fa-question-circle'></div>
</div>
</td>
<td>

	Display <a href="/interface/search">more information</a> about searching.

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

	To return to this toolbar directly, press <span class="keypress">4+alt-n</span>.

</td>
</tr>

</table>

<br><br>

For more information about searching, see the [documentation page
for searching](/interface/search).
