---
title: URL parameters
lang: en es
ref: url-parameters
author: Craig Stuart Sapp
translator: 
creation_date: 26 Dec 2020
translation_date: 
last_updated: 26 Dec 2020
tags: [all]
keywords: interface url
summary: "This page lists URL parameters that set up VHV as it is loaded."
sidebar: main_sidebar
permalink: /topics/url-parameters/index.html
---

{% include_relative scripts-local.html %}

URLs can include parameters that are passed to the VHV webpage.  The parameters
are appended to the main URL address after the `?` character.  Each parameter
is separated from the next parameter by `&` and each parameter consists of a key
and value pair which are separated from each other by `=`.   Here is an example URL that
contains all of these features:

<div style="padding-left:50px; margin-bottom:10px">
<a target="_blank" href="https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas/sonata01-1.krn">
https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas/sonata01-1.krn
</a>
</div>

The pieces of the full URL are:

<div markdown="1" style="padding-left:50px;">


`https://verovio.humdrum.org` 
: The main part of the URL. 

`?` 
: The start of the parameter list. 

`k=Ebey` 
: The first parameter, with `k` being the name of the parameter and `Ebey` being the value for the `k` parameter.

`&` 
: Parameter separator character. 

`file=beethoven/sonatas/sonata01-1.krn` 
: The second parameter in the URL called `file` with a value of `beethoven/sonatas/sonata01-1.krn`. 


</div>

The parameter order does not matter, so `k` can equivalently come after `file`:

<div style="padding-left:50px; margin-bottom:10px">
<a target="_blank" href="https://verovio.humdrum.org?file=beethoven/sonatas/sonata01-1.krn&k=Ebey">
https://verovio.humdrum.org?file=beethoven/sonatas/sonata01-1.krn&k=Ebey
</a>
</div>

Also note that certain characters are not allowed within parameter
values, such as `&`, obviously.  Instead, such characters must be
escaped using <a target="_blank"
href="https://en.wikipedia.org/wiki/Percent-encoding">percent
encoding</a>.  In addition to the list on that page, newlines must
be escaped as the characters `%0A`, tabs as `%09` and spaces
as `%20`.  Percent encoding is a hexadecimal value for the ASCII
(or generally UTF-8) byte codes of the character.


## Setup parameters ##

### k/keys ###

The `k` parameter (long form `keys`) can be used to emulate keyboard
shortcuts that are run immediately after VHV is loaded.  The characters
in the following table are given in a string to the parameter.
Here is an example use to show minimal controls in VHV:

<a target="_blank" href="https://verovio.humdrum.org/?k=Ebey&file=beethoven/sonatas/sonata01-1.krn">
https://verovio.humdrum.org/?k=Ebey&file=beethoven/sonatas/sonata01-1.krn
</a>

The string `Ebey` is equivalent to typing
<a href="/commands/alt-E"><span class="keypress">alt-shift-E</span></a>,
<a href="/commands/alt-b"><span class="keypress">alt-b</span></a>,
<a href="/commands/alt-e"><span class="keypress">alt-e</span></a>,
<a href="/commands/alt-y"><span class="keypress">alt-y</span></a> after VHV
has loaded.  The order of the letters does not matter, so `Ebey`
and `bEey` are equivalent.

<div style="height:20px"></div>

<style>
#ktable table td:first-child {
	width: 50px;
}
</style>

<div id="ktable" markdown="1">

| Character | VHV&nbsp;shortcut | Meaning |
| --------- | ------------ | ------- |
| `B`       |  <a href="/commands/alt-B"><span class="keypress">alt-shift-B</span></a> | Hide the toolbar. |
| `b`       |  <a href="/commands/alt-b"><span class="keypress">alt-b</span></a>       | Suppress the VHV logo at the top left of the VHV window. |
| `d`       |  <a href="/commands/alt-d"><span class="keypress">alt-d</span></a>       | Hide the menu in the VHV header. |
| `E`       |  <a href="/commands/alt-E"><span class="keypress">alt-shift-E</span></a> | Hide both the menu and the toolbar areas. |
| `e`       |  <a href="/commands/alt-e"><span class="keypress">alt-e</span></a>       | "Erase": Suppress the splash music when opening VHV (or any previous content from your last visit).    | |
| `w`       |  <a href="/commands/alt-w"><span class="keypress">alt-w</span></a>       | Widen the spacing of the notation. Multiple `w` characters can be used to increase the spacing more.        |
| `W`       |  <a href="/commands/alt-W"><span class="keypress">alt-shift-W</span></a> | Narrow the spacing of the notation.  Multiple `W` characters can be used to decrease the spacing more.       |
| `y`       |  <a href="/commands/alt-y"><span class="keypress">alt-y</span></a>       | Hide the text editor. |

## Data parameters ##

The `t` and `f` parameters can be used to preload a digital score 
from the URL.

### t/text ###

The `t` parameter (or long form `text`) is used to load text from
the parameter value into the text editor as VHV is loaded.  Two
forms of data can be loaded using this parameter: either raw text
or MIME-encoded text.  This method is most useful for loading short
example scores into VHV.  The total URL length including the `t`
parameter data should not exceed about 2000 characters, although
some web browsers allow longer URLs, with the actual maximum depending
on the specific web browser.

#### Raw text data for t parameter ####

For raw text, special characters for the URL must be escaped using
<a target="_blank"
href="https://en.wikipedia.org/wiki/Percent-encoding">percent
encoding</a>.  Also, newlines need to be encoded as `%0A`, tabs as
`%09` and spaces as `%20`.  Type some text into the following box,
and a URL with the raw text encoded in the `t` parameter will be
displayed underneath.

<textarea style="font-family:Courier; tab-size:12; -moz-tab-size:12; width:500px; height:200px;" id="raw" oninput="displayRawTextUrl()"
onkeydown="if(event.keyCode===9){var v=this.value,s=this.selectionStart,e=this.selectionEnd;this.value=v.substring(0, s)+'\t'+v.substring(e);this.selectionStart=this.selectionEnd=s+1;return false;}"
>**kern	**kern
*M4/4	*M4/4
=1	=1
1CC	1cc
=	=
*-	*-</textarea>

<br/>

Here is a URL containing the above contents in the `t` parameter (click to view in VHV):
<div style="margin-top:20px;"  id="raw-url"></div>
<div style="margin-top:20px" id="raw-counter"></div>


<div style="30px;"></div>

#### MIME-encoded data for t parameter ####

Here is an example of MIME-encoded text:

<a target="_blank" href="https://verovio.humdrum.org/?t=KiprZXJuCjFjCj0KKi0">
https://verovio.humdrum.org/?t=KiprZXJuCjFjCj0KKi0
</a>


The string `KiprZXJuCjFjCj0KKi0` is the following MIME-encoded text:

```tsv
**kern
1c
=
*-
```

This will be decoded and inserted into the VHV text editor when the above link is clicked on.

You can add some text to the box below and a URL to VHV with the `t` 
parameter filled in with the MIME-encoded text will be displayed below:

<textarea style="font-family:Courier; tab-size:12; -moz-tab-size:12; width:500px; height:200px;" id="mime" oninput="displayMimeUrl()"
onkeydown="if(event.keyCode===9){var v=this.value,s=this.selectionStart,e=this.selectionEnd;this.value=v.substring(0, s)+'\t'+v.substring(e);this.selectionStart=this.selectionEnd=s+1;return false;}"
>**kern	**kern
*M4/4	*M4/4
=	=
1CC	1cc
=	=
*-	*-
</textarea>
<div style="margin-top:20px;"  id="mime-url"></div>
<div style="margin-top:20px" id="mime-counter"></div>


### f/file ###

The `f` parameter (or long form `file`) is used to load a digital
score into the editor.  The value can either be either a built-in
repertory score, or an arbitrary URL to a score available on the
web.  If you load a score using `http://` (unsecured HTTP), then
you should use the unsecured address of VHV
([http://verovio.humdrum.org](http://verovio.humdrum.org)); otherwise,
scores loaded with `https://` can be loaded from either
[http://verovio.humdrum.org](http://verovio.humdrum.org) or
[https://verovio.humdrum.org](https://verovio.humdrum.org).


#### Repertories ####

A [repertory](/repertory) file can be loaded into the editor if
there is no `https://` prefix in the `file` parameter's value.  This
will also place repertory navigation buttons at the top left side
of the navigation bar in VHV.  Here are examples of loading repertory
files.  You can click on the repertory up-arrow to view an index
of other scores in the same repertory.

<dl>

<dt>
	Beethoven, Piano sonata no. 1 in F major, mvmt. 1:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn
	</a>
</dd>

<dt>
	Mozart, Piano sonata no. 1 in C major, K 279/189d, mvmt. 1:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn
	</a>
</dd>

<dt>
	Scarlatti, Keyboard sonata in C major, L.1/K.514:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=scarlatti/sonatas/L001K514.krn">
	https://verovio.humdrum.org/?k=ey&file=scarlatti/sonatas/L001K514.krn
	</a>
</dd>

<dt>
	Chopin, Etude in C# minor, op. 10, no. 3 from the <a target="_blank" href="https://www.nifc.pl">Fryderyk Chopin Institute</a>:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=chopin-first-editions/010_1-6-1b-KI-004.krn">
	https://verovio.humdrum.org/?k=ey&file=chopin-first-editions/010_1-6-1b-KI-004.krn
	</a>
</dd>

<dt>
	J.S. Bach, Chorale <i>Aus meines Herzens Grunde</i>, BWV 269:
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn">
	https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn
	</a>
</dd>

<dt>
	Givaonnelli, <i>Non è questa la mano</i>, (1588) madrigal from the <a target="_blank" href="https://www.tassomusic.org/work?Trm0047m">Tasso in Music Project</a>
</dt>
<dd>
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn">
	https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn
	</a>
</dd>

</dl>

Notice that when you load a repertory score, there are repertory navigation buttons in the 
top left corner of VHV that allow you to browse other files in the repertory or view an
index of all of the scores in the repertory.

#### Repertory indexes #####

You can open VHV with the list of all works in the repertory by listing
the repertory path without a filename:


<div style="padding-left:50px; margin-bottom:10px">
<a target="_blank" href="https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas">
https://verovio.humdrum.org?k=Ebey&file=beethoven/sonatas
</a>
</div>

Then you can choose a specific file in the repertory to view in VHV.  You can
also press the <span class="keypress">esc</span> key to close the repertory
index without choosing a score to load.


### File URLs ###

VHV knows where built-in repertory files are located on the web, but if you
need to load a file that it is unaware of, you can
give the full URL address to the digital file.


For example, the repertory location of the Beethoven sonata movement example given above is:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn
	</a>
</div>

This can be expanded into into a fully qualified URL giving the actual location of the file on the web:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn">
	https://verovio.humdrum.org/?k=ey&file=https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn
	</a>
</div>

which loads the score from this link:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn">
	https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn
	</a>
</div>


#### Shortcuts #####

Several repertories and websites have shortcut methods to avoid specifying an entire filename or URL.


##### Github shortcuts #####

Github URLs can be long:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn">
	https://raw.githubusercontent.com/craigsapp/beethoven-piano-sonatas/master/kern/sonata01-1.krn
	</a>
</div>

Such Github URLs can be condensed into this form for the `file` parameter:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`github:username/repository/path-to-file/filename`
</div>

Notice that the directory name `master` is skipped since it is the
real root directory of the repository files and not a directory
name within the repository.  The Beethoven digital score full URL on Github can
be condensed into:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`github:craigsapp/beethoven-piano-sonatas/kern/sonata01-1.krn`
</div>

Resulting in the VHV direct link to that score being shortened to:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org?k=ey&file=github:craigsapp/beethoven-piano-sonatas/kern/sonata01-1.krn">
	https://verovio.humdrum.org?k=ey&file=github:craigsapp/beethoven-piano-sonatas/kern/sonata01-1.krn
	</a>
</div>

##### Repertory shortcuts #####

Several repertories have long names for the files that consist of
a catalog number for computational processing, followed by the title
of the work for human readability.  VHV has a shortcut that allows
loading the repertory score based on a catalog number rather than
the full filename and path to the file in the repository.

For example the repertory link for the example <a target="_blank" href="https://www.tassomusic.org">Tasso in Music Project</a> work:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn">
	https://verovio.humdrum.org/?k=ey&file=tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn
	</a>
</div>

Can have the full repertory path and name reduced from:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`tasso/Trm/Trm0047m-Non_e_questa_la_mano--Giovannelli_1588.krn`
</div>

to:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`tasso:Trm0047m`
</div>

in the VHV link to the score:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=tasso:Trm0047m">
	https://verovio.humdrum.org/?k=ey&file=tasso:Trm0047m
	</a>
</div>

<a target="_blank" href="https://josquin.stanford.edu">Josquin Research Project</a>
scores can also be loaded from a repertory shortcut.  Full repertory names for these
files can be condensed from:


<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`jrp/Ock/Ock2002-Ave_Maria.krn`
</div>

to:

<div markdown="1" style="padding-left:20px; margin-bottom:10px;">
`jrp:Ock2002`
</div>

resulting in a shorter VHV URL:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=jrp:Ock2002">
	https://verovio.humdrum.org/?k=ey&file=jrp:Ock2002
	</a>
</div>


## Search parameters ##

The three parameters `p`, `r` and `i` can be used to search for pitches, 
rhythms and/or intervals.  These parameters will be loaded into the 
<a target="_blank" href="/interface/search">search toolbar</a>
when loading VHV, and the search tool will be activated and a search
done as soon as the score has been loaded.

### p/pitch ###

Here is an example of searching for the opening theme in Beethoven piano sonata no. 1, mvmt. 1:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&p=cfacfagfef">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&p=cfacfagfef
	</a>
</div>

This searches for the diatonic pitch-class sequence `C F A C F A G F E F`.

### r/rhythm ###

Search for the rhythmic pattern `16 8 16 8 16` in Joplin's <i>The Entertainer</i>:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16">
	https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16
	</a>
</div>


### i/interval ###

Search for the diatonic interval sequence `8 -2 2 -8` 
(up an octave, down a step, up a step, down an octave)
in Mozart Piano sonata no. 1, mvmt. 1:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn&k=ey&i=8-22-8">
	https://verovio.humdrum.org/?k=ey&file=mozart/sonatas/sonata01-1.krn&k=ey&i=8-22-8
	</a>
</div>



## F/filter ##

The `filter` parameter can be used to process an incoming score
with one or more <a target="_blank" href="/filter">filters</a> after
the score has been loaded into VHV.  Note as with all parameter values,
some characters should be <a target="_blank"
href="https://en.wikipedia.org/wiki/Percent-encoding">percent
encoded</a>.

### Single filter ###

Here is an example of transposing the Beethoven piano sonata movement from F minor to A minor:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&filter=transpose%20-ka">
	https://verovio.humdrum.org/?k=ey&file=beethoven/sonatas/sonata01-1.krn&filter=transpose%20-ka
	</a>
</div>

The filter is `transpose -ka`, which means transpose the score to
the key of A (minor in this case, since modality is preserved). The `%20`
characters is the percent encoding of a space character.

### Multiple filters ###

Separate filters can be serialized in the filter parameter by separating them
with a pipe character (`|`).  The filters will be applied in the order they
are placed in the filter string.  Here is an example of displaying a
Bach chorale in grand-staff format and then coloring the triadic
sonorities:

`satb2gs|colortriads`

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?file=chorales/chor075.krn&filter=satb2gs%7Ccolortriads">
	https://verovio.humdrum.org/?file=chorales/chor075.krn&filter=satb2gs%7Ccolortriads
	</a>
</div>

The pipe character is `%7C` in percent encoding.


### Filtering and searching ###

The `filter` parameter can be mixed with music searches.  Here is an example of 
extracting the top notes of chords before searching for the rhythm `16 8 16 8 16`
in Jopin's <i>The Entertainer</i>.

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16&filter=chord%20-t">
	https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16&filter=chord%20-t
	</a>
</div>

Compare to the same search without the filter:

<div style="padding-left:20px; margin-bottom:10px;">
	<a target="_blank" 
	href="https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16">
	https://verovio.humdrum.org/?k=ey&file=joplin/entertainer.krn&r=16,8,16,8,16
	</a>
</div>


## tb/Toolbar ##

Set the visible toolbar.

