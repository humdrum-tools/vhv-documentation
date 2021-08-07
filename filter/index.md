---
title: Filters
lang: en es
ref: filters
author: Craig Stuart Sapp
translator: 
creation_date: 31 Aug 2020
translation_date: 
last_updated: 23 Apr 2020
tags: [all, filters]
sidebar: main_sidebar
aton: "true"
verovio: "true"
keywords: interface commands 
summary:  "Documentation for filters in VHV."
permalink: /filter/index.html
---

<script type="text/x-aton" id="example-data">
{% include_relative examples.aton %}
</script>

{% include_relative styles-local.html %}
{% include_relative listeners.html %}
{% include_relative scripts-local.html %}


Filters allow you to manipulate the contents of Humdrum data before
it is converted into notation.  They can also be used to manipulate
the data when preparing a score, such as to add a new spine, or to
beam notes together.

As an example of filtering before rendering to music notation, a
graphic score can be transposed while keeping the Humdrum data in
the text editor at the original pitch.  Here are links to Mozart's
<i>Sonata facile</i>, which was written in C major but can be
transposed to any other key:

<a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c-">C-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&toolbar=filter">C&nbsp;major</a> (unfilterd)
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c#">C-sharp&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d">D&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d-">D-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e-">E-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e">E&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f">F&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f#">F-sharp&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G-">G-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G">G&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A-">A-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A">A&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B-">B-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B">B&nbsp;major</a>

Notice in each case that the Humdrum data in the text editor remains
in C major.  If you want to alter the Humdrum data in the text
editor, then type the <span class="keypress">alt-c</span> keyboard
shortcut.  This will "compile" the filters in the data and replace
the original data with the filtered data.  Here are examples where
the music is displayed in every key and the data is also modified
to match that key:

<a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c-">C-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&toolbar=filter">C&nbsp;major</a> (unfilterd)
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20c#">C-sharp&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d">D&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20d-">D-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e-">E-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20e">E&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f">F&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20f#">F-sharp&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G-">G-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20G">G&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A-">A-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20A">A&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B-">B-flat&nbsp;major</a>
| <a target="vhv" href="https://verovio.humdrum.org/?k=e&file=mozart/sonatas/sonata15-1.krn&filter=transpose%20-k%20B">B&nbsp;major</a>




## Filter toolbar ##

A filter toolbar is available in the top right corner of the VHV interface:

<div style="margin-left: 50px;" class="toolbar" id="toolbar-5">
	<input id="filter"  onkeyup="checkForFilterActivate(event)" type="text" spellcheck="false" placeholder="filter">
	<div title="Apply filter" class='filter-icon nav-icon fa fa-filter'></div>
	<div id="filter-compile" title="Compile filter (alt-c)" class='nav-icon fa fa-plus'></div>
	<div title="About filters" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br/>

If no toolbar is visible, then press <span
class="keypress">alt-shift-N</span> to make the toolbar visible,
or press <span class="keypress">alt-shift-E</span> to toggle display
of both the menu and the toolbar.  If a different toolbar is visible,
click on the circular icon on the right until the filter toolbar
is visible.  The keyboard shortcut <span class="keypress">5+alt-n</span>
can be typed to display the filter toolbar directly (you may need
to click in the music notation pane to defocus the text editor;
otherwise, a "5" will be inserted into the text).


### Using the filter toolbar ###

Type a filter into the filter box.  As you type the filter, nothing
will happen to the notation since the filter is not yet being
applied.  After you have finished entering the filter, either press
the <span class="keypress">return</span> key, or click on the filter
icon on the right side of the filter input box.  This will cause
the filter icon to highlight in yellow, meaning that the filter
is currently being applied to the data:

<div style="margin-left:50px;" class="toolbar" id="toolbar-6">
	<input id="filter2"  onkeyup="checkForFilterActivate(event)" oninput="updateFilterState(event)" type="text" spellcheck="false" placeholder="transpose -k d">
	<div title="Apply filter" class='active filter-icon nav-icon fa fa-filter'></div>
	<div id="filter-compile" title="Compile filter (alt-c)" class='nav-icon fa fa-plus'></div>
	<div title="About filters" class='nav-icon fas fa-question-circle'></div>
	<span id="line-break-icon2">
		<div title="Go to next toolbar menu (alt-n)" class='nav-icon fa fa-superpowers'></div>
	</span>
</div>

<br/>

If you type more content in the filter box, the filter icon will
stop highlighting and the filter will stop being applied to the
data.  In such a case, press <span class="keypress">return</span>
or click on the filter icon to reactivate the filter.  You can also
click on the yellow filter icon to stop the filter from being
applied before the data is converted into graphical notation.

<table style="border-style: none !important; border-collapse: collapse !important; max-width: 100% !important; margin:0 !important; padding:0 !important;">
	<tr style="width:100%; padding:0; border: none !important; background:none !important;">
		<td style="border: none; width:100% !important; padding:0;">
If you want to replace the original Humdrum data in the text editor
with the filtered data, click on the
<div style="font-size:1rem; padding-left:3px; margin-top: -15px; padding-right: 3px; display:inline-block !important;" class="toolbar">
	<span style="display:inline-block !important;"  class='filter-icon nav-icon fa fa-plus'>
	</span>
</div>
icon or type <span class="keypress">alt-c</span> to "compile" the filter.
</td></tr></table>


## Embedded filters ##

Instead of using the toolbar interface, you can also type filter
commands directly into the Humdrum data.  Prefix the filter with
`!!!filter:`.  Each filter line found in the data will be processed
in sequence before displaying the notation; otherwise, the placement
of the filter lines is not important: they can go at the top, bottom
or somewhere in the middle of the data.

Here is an example of embedding three separate filters into the data:

{% include image.html
	file="three-filters.jpg"
	alt="Embedding three filters."
	caption="Embedding three filters into Humdrum data."
%}

The first three lines of the data contain the filters:

```
!!!filter: myank -m 1-3
!!!filter: extract -i kern
!!!filter: transpose -t -m3
```

The *myank* filter extracts the first three measures of the score,
the *extract* filter removes the lyrics from the score, and *transpose*
transposes the music down a minor third.  To use all three filters
from the toolbar, separate them with the pipe character (|).  This
can also be done to merge multiple filters onto a single line in
the data:


```
!!!filter: myank -m 1-3 | extract -i kern | transpose -t -m3
```

{% include image.html
	file="combined-filters.png"
	alt="Combining three filters."
	caption="Combining three filters on filter toolbar."
%}


## Examples by topic/filter ##

Click on the blue filter text to load the filter into VHV and apply
to a sample piece of music.


### Transposition ###

The [transposition](/filter/transposition) filter can be used to
transpose the score in various ways that are illustrated below.

<div data-category="transposition"></div>


### Compound filters ###

Here are examples of how to mix multiple filters together.  Each filter 
is separated from the next with a pipe character (|).

<div data-category="pipeline"></div>


### Musical excerpts ###

The [myank](/filter/myank) filter can be used to extract musical examples
from longer scores.


<div data-category="excerpt"></div>



### Part extraction ###

The [extract](/filter/extract) filter can be used to extract parts
and other data spines from a full score.


<div data-category="extract"></div>




### Chords ###

The [chord](/filter/chord) filter can be used to manipulate chords.


<div data-category="chord"></div>



### Searching ###

The [msearch](/filter/chord) filter (meaning *music search*) can
be used to search for musical patterns.

<div data-category="search"></div>



### Search and replace ###

The [shed](/filter/shed) filter can be used to search and replace content
in Humdrum data.  "Shed" stands for "Humdrum <a target="_blank" href="https://www.gnu.org/software/sed/manual/sed.html">sed</a>" (dyslexic, but easier to pronounce).


<div data-category="regular_expressions"></div>



### Counterpoint ###

The [cint](/filter/cint) filter (meaning *composite intervals*) can
be used to study counterpoint.  The cint program is an intersection
of functionalities between the mint and hint programs of the Humdrum
Toolkit, and it creates counterpoint modules that consist of four
notes in two voices, which in turn generates two harmonic and two
melodic intervals for each module.


<div data-category="counterpoint"></div>


## Command-line filters ##

The filters available in VHV come from <a target="_blank"
href="https://humlib.humdrum.org">humlib</a>. Filters can be compiled
as command-line tools:

{% include image.html
	file="command-line.jpg"
	alt="Command-line use of myank and transpose filters."
	caption="Command-line use of myank and transpose filters."
%}

{% include image.html
	file="vhv-filtering.jpg"
	alt="Equivalent filtering in VHV."
	caption="Equivalent filtering in VHV."
%}


There are additional command-line tools in humlib that are not
available as filters.  These mostly involve extra tools for data
analysis other than data manipulation or generating music notation.
More tools for the command-line are also available in Humdrum Extras
and the Humdrum Toolkit.  See the <a target="_blank"
href="https://github.com/humdrum-tools/humdrum-tools">humdrum-tools</a>
repository for instructions on how to compile and use these tools
on the command-line.



