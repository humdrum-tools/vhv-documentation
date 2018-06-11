---
title: URL filters
lang: en
ref: filters-url
author: Craig Stuart Sapp
creation_date: 8 May 2017
last_updated: 8 May 2017
tags: [all, filters]
sidebar: main_sidebar
keywords: url filters
summary: Filters can be applied via a VHV URL when loading online repertories.  The filter will be applied to all works/movements in the same repertory even when starting at a particular work/movement.
permalink: /filters/url/index.html
---

Here is a plain URL for loading a J.S. Bach chorale:

```
http://verovio.humdrum.org/?file=chorales/chor025.krn
```

{% include image.html
	file="chor025.png"
	alt="Bach chorale #25"
	max-width="80%"
	caption="Viewing URL without filtering"
%}


## Single filter ##


Filters can be included in URLs by adding a parameter called `filter`
followed by the filter command or a pipeline of filter commands.
Here is an example of adding the string `&filter=` at the end of
the URL, and then a filter, such as [myank](/filters/myank) to
extract a range of measures from the full score:

```
http://verovio.humdrum.org/?file=chorales/chor025.krn&filter=myank%20-m3-5
```

This will result in measures 3-5 of the choral being extracted from the full 
score and displayed in graphical notation:

{% include image.html
	file="chor025-myank.png"
	alt="Bach chorale #25"
	max-width="80%"
	caption="Viewing result of URL with filter \"myank -m3-5\""
%}

The corresponding Humdrum-data embedded filter would be:

```
!!!filter: myank -m3-5
```

### Percent encoding ###

The space character must be converted into `%20` in URLs, since a space
is not allowed directly in a URL.  Some other characters not allowed 
in URLs, and their [percent encoding](https://en.wikipedia.org/wiki/Percent-encoding), are:

| Character     |   Encoding |
|---------------|------------|
| space         |  %20       |
| "             |  %22       |
| %             |  %25       |
| \| (pipe)     |  %7C       |


## Filter pipeline ##

More than one filter can be applied from the URL by separating the
filters by a pipe character, `|`.  Note that the pipe character is not
allowed directly in a URL, so it must be escaped as `%7c`.  Here is a 
filter pipe line that first extracts measures 3 to 5 of the score, and
then changes the layout to grand-staff:

```
!!!filter: myank -m 3-5 | satb2gs
```

Some of the spaces are optional, so they are best removed when using as
a URL filter to avoid unnecessary `%20` encodings of space characters:

```
!!!filter: myank -m3-5|satb2gs
```

Converting this into a URL filter:

```
http://verovio.humdrum.org/?file=chorales/chor025.krn&filter=myank%20-m3-5%7csatb2gs
```

{% include image.html
	file="chor025-35gs.png"
	alt="Bach chorale #25"
	max-width="80%"
	caption="Viewing URL with filter \"myank -m3-5\""
%}

## Repertory filtering ##

When navigating to other works/movements in the same repertory, the
URL filter will be applied to the entire repertory.  In addition, the
filter can be added to the URL for the repertory index.  Here is an example
of viewing all of the Mozart piano sonatas transposed to a tonic on
C (preserving the original mode):


```
http://verovio.humdrum.org/?file=mozart/sonatas&filter=transpose%20-kc
```

The filtering will not be immediately apparent, since the repertory
index is displayed:


{% include image.html
	file="mozart-index.png"
	alt="Mozart piano sonata index"
	max-width="80%"
	caption="Mozart piano sonata repertory index"
%}

But selecting movement 1 of the D&uuml;nitz sonata will display
the music in C major rather than D major:

{% include image.html
	file="mozart-cmajor.png"
	alt="Mozart sonata k284 transposed to C major"
	max-width="80%"
	caption="Mozart piano sonata in D major, K284/205b, mvmt. 1, transposed to C major"
%}


## Compiling URL filters ##

The results of filtering, both in the URL or embedded directly in the data, 
are visible in the graphical notation editor but not in the data in the 
text editor.  To generate the notation, filters in the data or URL are applied
before converting to MEI and rendered into SVG images.  If you want to see
resulting data from the filtering, type [alt-c](/commands/alt-c) to compile
the filter.  Below is the view of the above sonata example, where the
Humdrum data has now been transposed to C major as well 
as in the graphic notation:

{% include image.html
	file="mozart-altc.png"
	alt="Mozart sonata k284 transposed to C major, in data as well"
	max-width="80%"
	caption="Post-filtered Humdrum data displayed in text editor"
%}


{% include warning.html
	content="Graphic editing will usually not work when filters are applied to a score in the text editor.  Typing <span class='keypress'>alt-c</span> will allow the graphic editing to work properly on the data."
%}

## With URL interface commands ##

Not exactly filters, but useful in combination with filter parameters are
interface commands. Many interface commands (which are key combinations
starting with <span class="keypress">alt</span>) can be added to the 
URL.  To add one or more interface commands, include the parameter `&k=`
followed by the list of the interface command characters, excluding the `alt-`
prefix.  For example <span class="keypress">alt-y</span> becomes
`&k=y`.  Multiple commands can be placed in the `k` parameter string, with
no spaces needed between characters.  The following URL:

```
http://verovio.humdrum.org/?file=mozart/sonatas/sonata06-1.krn&filter=transpose%20-kc&k=by
```

will hide the text editor (equivalent to typing 
<span class="keypress">alt-y</span> in VHV), and will also hide the
VHV logo (equivalent to typing <span class="keypress">alt-b</span> 
in VHV).  Here is the resulting display for the above URL:

{% include image.html
	file="mozart-by.png"
	alt="Mozart sonata k284 transposed to C major, in data as well"
	max-width="80%"
	caption="Text-editor and logo suppressed with '&k=by' added to the URL"
%}



