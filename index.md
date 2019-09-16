---
title: Verovio Humdrum Viewer 
lang: en pl
author: Craig Stuart Sapp
creation_date: 3 Mar 2017
last_updated: 4 Mar 2017
tags: [getting_started]
sidebar: main_sidebar
keywords: homepage
permalink: /index.html
summary: 
---

## Overview ##

Verovio Humdrum Viewer is an online digital music editor and
interactive notation rendering interface for Humdrum files, located at
[http://verovio.humdrum.org](http://verovio.humdrum.org).  See the
[Getting started](/interface/getting_started) page for a tutorial on
using the VHV interface, or browse through pages on this website by
clicking on the headings in the sidebar menu to the left (or above),
which is organized by topic:

<style>

dl {
	margin-left: 10%;
	margin-right: 10%;

}

dd {
	margin-top: 0 !important;
}

</style>

User interface
: A description of the VHV web interface and the basics of how to
use it. Topics include how to [load MusicXML files](interface/musicxml),
how to [save MEI files](interface/mei), musical text 
[colorizing](interface/edit_modes), and the [visual syntax of data
validation](interface/validation).


Commands
: A list of computer keyboard commands for interacting with the VHV
interface.  For example, [<span
class="keypress">alt-shift-T</span>](/commands/alt-t/#saving-the-entire-score-to-a-pdf-file)
downloads a PDF of the music notation, [<span
class="keypress">alt-t</span>](/commands/alt-t/#saving-the-currently-displayed-page)
downloads a PDF of the currently viewed music notation, and [<span
class="keypress">alt-l</span>](/commands/alt-l) colors the notes differently in each layer of
music for proofreading.


Graphic editing
: A description of editing commands for altering the music notation
graphically.  Musical features that can be edited graphically include
[pitch](/graphic/pitch), [slurs](/graphic/slurs), and
[beams](/graphic/beams).  More complicated editing requires
manipulation of the musical encoding in the VHV text editor.


Music encoding
: Topics about representing musical features in the Humdrum syntax,
particularly advanced topics related to VHV features.  See the
[getting started](/humdrum/getting_started) page for an interactive
tutorial on encoding music in the Humdrum format.  More complete
documentation can be found at [Humdrum documentation
website](http://www.humdrum.org).  The most common use of VHV is
to edit music imported via [MusicXML](/interface/musicxml) from a
more full-featured graphical music editor, but Humdrum data can
also be typed in manually.


Repertories
: A description of online musical repertories available for display
in VHV.  Most repertories are linked to from Github, such as the
[Bach chorale repertory](https://github.com/craigsapp/bach-370-chorales)
and the [Mozart piano sonata
repertory](https://github.com/craigsapp/mozart-piano-sonatas).
Other repertories are listed in the [repertory introduction](repertory).


Filters
: Filters are embedded commands within the musical data that modify the data.
These are Humdrum data-processing tools that are part of
[humlib](https://humlib.humdrum.org).  Most of the currently available
tools are for data processing, such as [extract](/filter/extract),
which is useful for extracting part; [transpose](/filter/transpose),
which is useful for transposing scores, and [myank](/filter/myank),
which is useful for extracting measures from a full score.  The
[dissonant](/filter/dissonant) filter is used to analyze the
functions of dissonant notes in Renaissance-era music, and is used
as a tool in the [Josquin Research Project](http://josquin.stanford.edu).


Embedded options
: [This section](/options) of the documentation describes how to
embed verovio typesetting options into the Humdrum data to control
graphical aspects of the music notation.  Here is a [full
list](/options/list) of the verovio parameters that can be set from
within the musical data.  Some aspects are controllable from keyboard
commands in the VHV interface, such as <span class="keypress">alt-w</span>
to widen the spacing of the music (by increasing the <tt>spacingLinear</tt>
verovio option), and <span class="keypress">alt-shift-W</span> to
narrow the spacing of the music.


myVHV
: Instructions and demos for using [Verovio](http://www.verovio.org)
and [Humdrum](http://www.humdrum.org) for your own projects.  In
particular, after editing a Humdrum score in VHV, you can use the
[Humdrum notation plugin](https://plugin.humdrum.org) to display
the score on your own website.


Maintenance
: Topics related to creating pages and maintaining this website.


Indexes
: Lists of pages by tag category.


## Participants ##

<style>

ul.brief li {
	color: #aaa;
	padding: 0 !important;
	margin: 0 !important;
}

</style>

<dl>
<dt>Craig Stuart Sapp</dt>
<dd>Creator</dd>
<dt>Alex Morgan</dt>
<dd>
<ul class="brief"> <li> dissonance labeling algorithms in the <i><a href="/filter/dissonant">dissonant</a></i> filter</li> <li> cadential suspension definitions in the <i><a href="/filter/cint">cint</a></i> filter </li> </ul>
</dd>
<dt>Piotr Szyngiera</dt>
<dd>
<ul class="brief">
<li> Humdrum syntax validation for the ace editor</li>
<li> <a href="/interface/edit_modes">Humdrum syntax highlighting</a> </li> 
</ul>
</dd>
</dl>

Non-programmers can participate by submitting [bug reports and
feature requests](
https://github.com/humdrum-tools/verovio-humdrum-viewer/issues) for
the VHV web interface.  If you place your own Humdrum file repertory
onto Github, it can be added to the [repertory list](/repertory)
and linked up to VHV.  Reports for <a href="/filter">filters</a>
should preferably be submitted to <a
href="https://github.com/craigsapp/humlib/issues">humlib issues</a>,
and reports for graphical notation should be submitted to <a
href="https://github.com/rism-ch/verovio/issues">verovio issues</a>
(when in doubt about where to submit but reports, post them to the
[VHV issues
list](https://github.com/humdrum-tools/verovio-humdrum-viewer/issues)).
Most pages on this website have editing buttons that can be used
to fix typos or add content, provided you have a <a
href="https://github.com">Github</a> account.

## Presentations ##

<dl>

<dt><a target="_blank" href="http://bit.ly/iaml-2019">IAML July 2019 workshop</a></dt>
<dd>Workshop on Verovio Humdrum Viewer at the International Association of Music Libraries in Kraków, Poland, 18 July 2019.
</dd>

<dt><a target="_blank" href="http://bit.ly/mec-2019-vhv">MEC May 2019 workshop</a></dt>
<dd>Workshop on Verovio Humdrum Viewer and its applications at the Music Encoding Conference, Vienna, Austria, 29 May 2019.
</dd>

<dt><a target="_blank" href="http://bit.ly/simssa-xii-vhv">SIMSSA August 2017 presentation</a></dt>
<dd>Keynote presentation on Verovio Humdrum Viewer at the SIMSSA XII workshop at McGill University, Montreal, Canada, 7 August 2017.</dd>

<dt><a target="_blank" href="http://bit.ly/mec2017-vhv">MEC May 2017 presentation</a></dt>
<dd>Introduction of Verovio Humdrum at the Music Encoding Conference 
in Tours, France, May 2017.</dd>

</dl>




### Major software components ###

Here are the three major software components used to create the VHV website:

<dl>

<dt> <a href="http://www.verovio.org">verovio</a></dt>
<dd> Music notation rendering in C++ (using MEI, with data imports from Humdrum and MusicXML and exports into SVG and MIDI)</dd>

<dt> <a href="http://humlib.humdrum.org">humlib</a></dt>
<dd> Musical data conversion and analysis tools in C++ (using Humdrum, with imports from MusicXML and MEI and exports into MEI and MIDI)</dd>

<dt> <a href="https://ace.c9.io">ace editor</a></dt>
<dd> JavaScript text editor</dd>

</dl>



## Institutional/Project Supporters ##

<style>

.logo {
	padding-top: 20px;
	padding-right: 20px;
}

.shadow {
	-webkit-filter: drop-shadow(3px 3px 2px rgba(0,0,0,0.2));
	drop-shadow(3px 3px 2px rgba(0,0,0,0.2));
}

</style>

<div style="margin-left: 100px">

<a class="logo" href="http://www.packhum.org"><img class="logo shadow" style="width:300px"  src="/images/phi-logo.png"></a>
<a class="logo" href="http://wiki.ccarh.org"><img class="logo shadow" style="width:300px" src="/images/ccarh-logo.png"></a>
<a class="logo" href="http://en.chopin.nifc.pl"><img class="logo shadow" style="width:350px" src="/images/nifc-logo.png"></a>
<a class="logo" href="https://simssa.ca/"><img class="logo shadow" style="width:250px" src="/images/simssa-logo.png"></a>

</div>

## Projects utilizing VHV ##

<div style="margin-left: 100px">

<a class="logo" href="http://www.tassomusic.org"><img class="logo shadow" style="width:300px" src="/images/tmp-logo.png"></a>
<a class="logo" href="http://josquin.stanford.edu"><img class="logo shadow" style="width:419px" src="/images/jrp-logo.png"></a>

</div>

<div style="height:100px"></div>

After preparing music in VHV, it should be suitable for use with
music analysis and processing tools, such as <a target="_blank"
href="https://github.com/humdrum-tools/humdrum-tools">Humdrum
Tools</a>, and for display on webpages with the <a target="_blank"
href="https://plugin.humdrum.org">Humdrum notation plugin</a>.

For example, the Josquin Research Project (JRP) uses both the
Humdrum notation plugin to display musical incipits on <a target="_blank"
href="http://josquin.stanford.edu/work/?id=Jos2721">work pages</a> as well
as a random sample of the JRP score database displayed on the <a target="_blank"
href="http://josquin.stanford.edu">homepage</a>. In addition, some
analysis tools are implemented online through VHV.  An example
of this is the <a href="/filter/dissonant">dissonant</a>
tool.  Work pages, such as <a target="_blank"
href="http://josquin.stanford.edu/work/?id=Jos2721">this
one</a> have an analysis tool button labeled "Dissonant"
which links to VHV, loading the data from the website,
and doing the dissonance analysis <a target="_blank"
href="http://verovio.humdrum.org/?k=ey&filter=dissonant&file=jrp:Jos2721">within VHV</a>.

Files from other websites can be automatically be loaded into VHV by
giving a URL as the filename in the *file* CGI parameter.  For example,
this link to VHV:

<a target="_blank" href="https://verovio.humdrum.org/?file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn">https://verovio.humdrum.org/?file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn</a>

embeds this URL to the Humdrum data for the first movement of Beethoven's <i>Moonlight</i>
sonata:

<a target="_blank" href="https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn">https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata14-1.krn</a>

This score is part of a Github repository of Beethoven piano sonatas:

<a target="_blank" href="https://github.com/craigsapp/beethoven-piano-sonatas">https://github.com/craigsapp/beethoven-piano-sonatas</a>

which is accessible from the bottom of the help menu in the VHV interface
(the question mark icon on the top left corner of the VHV page).





