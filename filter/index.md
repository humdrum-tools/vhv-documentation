---
title: VHV Filters
lang: en
ref: filters
author: Craig Stuart Sapp
translator: 
creation_date: 23 Apr 2017
translation_date: 
last_updated: 23 Apr 2017
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/index.html
---


Filters are a method of embedding [Humdrum Extras](http://extras.humdrum.org)
commands into Humdrum files.  Filters have the form:

```
!!!filter: command 
```

Multiple filters can be given on separate lines and will be executed in sequence, 
or combined into a single line separated by a pipe character.

```
!!!filter: command1
!!!filter: command2
!!!filter: command3
```

or


```
!!!filter: command1 | command2 | command3
```


These filter lines will be processed by verovio as the Humdrum data is being
loaded, allowing Humdrum Extras commands to be used easily within
the web browser to transform the data before it is converted into notation.


A simple, but handy, filter to use is the `autobeam` tool.  Notice in the 
following example that there are no explicit beams in the data (`L` for a
beam start and `J` for a beam end).  Nevertheless, the notation is
displaying beams.  Try to add more notes and/or remove the filter line
to see what happens.  The filter line can occur anywhere in the data,
so also try moving it to the bottom of the data.


{% include verovio.html
	source="autobeamed"
	scale="30"
	pageWidth="1450"
	tabsize="16"
%}

<script type="application/json" id="autobeamed">
!!!filter: autobeam
**kern
*M2/4
*MM72
*G:
8d
=1
8g
8b
8a
16cc
16cc
=2
16b
16b
8dd
8g
16g
16a
=3
16b
16b
8cc
8dd
8ee
=4
4.a
8d
=5
8g
8b
8a
16cc
16cc
=6
16b
16b
8dd
8g
16g
16a
=7
8b
8b
8a
16a
16a
=8
4.g
8d
=9
8g
8b
8a
16cc
16cc
=10
8b
8dd
8.g
16a
=11
8.b
16cc
8dd
8ee
=12
4.a
8d
=13
8g
8b
8a
8cc
=14
16b
16dd
16dd
16b
8g
16g
16a
=15
8.b
16cc
8a
8a
=16
4.g
8r
=17
8.dd
16dd
8.ee
16dd
=18
8b
4dd
8d
=19
8.g
16g
8a
8a
=20
4.b
8d
=21
8g
8b
8a
8cc
=22
16b
16dd
16dd
16b
8g
16g
16a
=23
8.b
16cc
8a
8a
=24
4.g
8d
=25
8g
8b
8a
16cc
16cc
=26
16b
16b
8dd
8g
16g
16a
=27
16b
16b
8cc
8dd
8ee
=28
4.a
8d
=29
8g
8b
8a
16cc
16cc
=30
16b
16b
8dd
8g
16g
16a
=31
8b
8b
8a
16a
16a
=32
4.g
8d
=33
8g
8b
8a
16cc
16cc
=34
8b
8dd
8.g
16a
=35
8.b
16cc
8dd
8ee
=36
4.a
8d
=37
8g
8b
8a
8cc
=38
16b
16dd
16dd
16b
8g
16g
16a
=39
8.b
16cc
8a
8a
=40
4.g
8r
=41
8.dd
16dd
8.ee
16dd
=42
8b
4dd
8d
=43
8.g
16g
8a
8a
=44
4.b
8d
=45
8g
8b
8a
8cc
=46
16b
16dd
16dd
16b
8g
16g
16a
=47
8.b
16cc
8a
8a
=48
4.g
8r
==
*-
</script>


Multiple filters can be applied to the data.  The filters can be
given a separate lines, with the order in the file being the order
that the filters will be applied.  Also pipe characters
can be used to separate two or more filter commands on a single line.
Here is an example of transposing a chorale from A minor to G minor,
and then arranging the layout of the parts onto grand-staff:

{% include verovio.html
	source="doublefilter"
	scale="30"
	pageWidth="1450"
	tabsize="10"
%}

<script type="application/x-humdrum" id="doublefilter">
!!!filter: transpose -k g | satb2gs
**kern	**kern	**kern	**kern
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[]	*k[]	*k[]	*k[]
*a:	*a:	*a:	*a:
*M4/4	*M4/4	*M4/4	*M4/4
=1-	=1-	=1-	=1-
2D	2G#	2e	2b
4C	4A	4e	4e
4BB	4d	4g#	4b
=2	=2	=2	=2
4AA	4e	4a	4cc
4BB	4d	8gnXL	8bL
.	.	8f#J	8aJ
8CL	8eL	4e	4g
8BBJ	8dJ	.	.
4AA	4c	4f#	4a
=3	=3	=3	=3
2E;	2B;	2g#;	2b;
2E	2e	2g#	2b
=4	=4	=4	=4
4A	4e	4a	4cc
8GL	4f	4b	4dd
8FJ	.	.	.
4E	4g	4cc	8ccL
.	.	.	8bJ
4F	4c	4f	4a
=5	=5	=5	=5
4C	8cL	4e	4g
.	8BJ	.	.
4D	4A	8dL	4f
.	.	8cJ	.
2E;	2G#;	2B;	2e;
=6:|!	=6:|!	=6:|!	=6:|!
2c	2A	2e	2a
4B	4B	4d	4gnX
4A	4c	8eL	4cc
.	.	8f#J	.
=7	=7	=7	=7
4G	4d	4g	4b
8FnXL	8dL	4a	4a
8EJ	8eJ	.	.
4D	4f	8bL	8ddL
.	.	8aJ	8ccJ
4E	4B	4g#	4b
=8	=8	=8	=8
2AA;	2c;	2e;	2a;
2A	2e	2a	2cc
=9	=9	=9	=9
4E	4e	4g	4b
8DL	4e	4g	4cc
8CJ	.	.	.
4BB	4d	8gL	4dd
.	.	8fJ	.
4C	4c	4e	4g
=10	=10	=10	=10
4D	8F#	4d	4b
.	4G	.	.
4D	.	4c	4a
.	8F#	.	.
2GG;	2G;	2B;	2g;
=11	=11	=11	=11
2C	2G	2e	2g
4AA	4A	4e	4cc
4E	4G#	8eL	4b
.	.	8dJ	.
=12	=12	=12	=12
4F	4A	4c	4a
4C	4G	4c	4e
4BB-	4G	[2d	4g
4AA	4A	.	4f
=13	=13	=13	=13
4GG#	4B	4d]	1e;
4AA	4A	4c	.
2EE;	2G#X;	2B;	.
==	==	==	==
*-	*-	*-	*-
</script>

Try removing the filter in the above example to see what the notation 
of the original notation looks like.

## Bug caveat ##

Currently filters must always be syntactically correct as they are typed;
otherwise, the verovio toolkit will exit on with an error and no longer
work until you reload the page (this will eventually be fixed).  In the 
meantime, you should ensure that the filter is never in an invalid state
by using one of the two following methods.  VHV will automatically restart
verovio if it crashes due to a poorly formed filter, but sometimes there 
may still be problems.

### delaying filter activation ###

A simple method of avoiding an invalid filter command is to type the line
without the colon (`:`) after filter.  Once the filter has been finished, go
back and add the colon character.  This will activate the filter, since verovio
will not be able to interpret the line as a filter command.


### freezing notation generation ###

You can also use the <span class="keypress">alt-f</span> command to temporarily
disable processing of the Humdrum data through the verovio toolkit.  After
freezing the notation, type the filter command in any way that you like.
Afterward, type <span class="keypress">alt-f</span> again to re-activate
the processing of the Humdrum data with the verovio toolkit.  The filter
should not be applied as the Humdrum data is converted.


## Compiling filters ##

The output of filtering can replace the input Humdrum data by 
typing the command <span class="keypress">alt-c</span> to "compile"
the filter.  This is useful for doing some data processing of Humdrum
files with in the VHV editor.  For example, the `extract` tool can
be used to extract a part from a full score, or to rearrange spines
in the data.


### interaction between filters and graphic editing ###


Once a filter has been added to a file in the VHV editor, it may not
be possible to use the [graphic editing commands](/graphic) anymore.

The reason for this is that, internal to verovio, the Humdrum data is
first filtered and then converted into MEI data and then SVG images.
In order to communicate between the SVG images and the original Humdrum data,
XML IDs that embed the line and field numbers of the Humdrum data; however,
these IDs are in reference to the filtered Humdrum data not the pre-filtered
data.

If you want to be able to use graphical editing with the filtered
Humdrum data, you must first compile the Humdrum data by typing
<span class="keypress">alt-c</span>.  This will replace the original
Humdrum data with the filtered output.  Since there is no additional
filtering, the graphical editing commands should work again.



## Command-line use ##

The command-line version of verovio understands `!!!filter:`
instructions, and these filters will be applied to the Humdrum data
before it is converted into MEI data (and subsequently to SVG
images).

Here is an example Humdrum file called [scale.krn](scale.krn):

```
**kern
*M4/4
*k[]
*C:
=1-
1c
=2
2d
2e
=3
4f
2g
4f
=4
2e
2d
=5
1c
==
*-
!!!filter: transpose -k e
```

Running the shell command:

```bash
verovio scale.krn --adjust-page-height -w 1600
```

will produce the following SVG image:

{% include image.html
	file="scale.svg"
	alt="transposed image"
	max-width="100%"
	caption="scale.krn data transposed to E major by transpose filter."
	margin-top="-50px"
	caption-margin-top="-20px"
%}


Verovio can be used to apply the filter and output the resulting Humdrum data
as well.  Here is an example of using verovio in a command pipeline, sending 
the resulting Humdrum data to standard output:

```bash
cat scale.krn  | verovio - -t humdrum -o -
```

which results in

```
**kern
*Trd2c4
*M4/4
*k[f#c#g#d#]
*E:
=1-
1e
=2
2f#
2g#
=3
4a
2b
4a
=4
2g#
2f#
=5
1e
==
*-
!!!Xfilter: transpose -k e
```

The last line has been changed from `!!!filter:` to `!!!Xfilter:` which indicates
that the filter has been applied to the data.

Filters use the same code library as Humdrum Extras (specifically 
[humlib](http://humlib.humdrum.org) which is a C++ parsing library for Humdrum files),
so an equivalent way to transpose the data using the command-line `transpose` tool
would be:

```bash
transpose -k e scale.krn
```

or even more similar as a pipeline acting like a filter:


```bash
cat scale.krn | transpose -k e  > scale2.krn
```

