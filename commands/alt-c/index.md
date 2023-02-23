---
title: <span class='keypress'>alt-c</span>
lang: en es pl
page_language: en
author: Craig Stuart Sapp
creation_date: 9 May 2017
last_updated:
ref: commands-alt-c
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands compile filters
summary: "The <span class='keypress'>alt-c</span> command compiles embedded filters."
permalink: /commands/alt-c/index.html
---

Pressing <span class="keypress">alt-c</span> will apply any embedded
[filters](/filter/) (or [URL filters](/filter/url)) to Humdrum data in the
text editor, and then replace the contents of the text editor with the
filtered data.


## Adding an empty spine ##

To add a new spine to Humdrum data, use the 
[extract filter](/filter/extract) and the 
<span class="keypress">alt-c</span> command.  The following
filter extracts all of the original spines, and adds a
blank spine at the end of the data lines:

```
!!!filter: extract -s 1-$,0
```

The `$` character symbolizes the last spine in the file, and `0` represents
a blank line.


Before the filter is compiled:

{% include image.html
	file="precompile.png"
	alt="view before compiling a filter."
	caption="Humdrum data before compiling a filter."
%}


After pressing <span class="keypress">alt-c</span>:

{% include image.html
	file="postcompile.png"
	alt="view after compiling a filter."
	caption="Humdrum data after compiling a filter."
%}

The filter line is now changed to `!!!Xfilter:` which indicates 
that the filter has been applied (and will not be applied again).
This line can be deleted if no longer needed, or the `X` can be 
deleted to re-apply the filter.


## Transposing example ##

Here is an example of [transposing](/filter/transpose)  Humdrum data:

{% include image.html
	file="transpose1.png"
	alt="view before compiling a transpose filter."
	caption="Humdrum data before compiling a transpose filter."
%}

Notice that the music is being displayed in E major, 
but the data is in C major.  This is because the filter is applied to
the Humdrum data in the text editor before it is converted
into MEI data and then rendered into an SVG image.

In order to view the same data that generates the notation, press the
<span class="keypress">alt-c</span> command to compile the filter:

{% include image.html
	file="transpose2.png"
	alt="view after compiling a transpose filter."
	caption="Humdrum data after compiling a transpose filter."
%}

Now the musical data in the text data matches the graphical notation
of the music.










