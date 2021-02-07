---
title: Embedded verovio options
lang: en
ref: verovio options
author: Craig Stuart Sapp
translator: 
creation_date: 20 Mar 2019
translation_date: 
last_updated: 20 Mar 2019
tags: [all, options]
sidebar: main_sidebar
verovio: "true"
keywords: embedded verovio options
summary: 
permalink: /options/index.html
---

Verovio options can be embedded directly in Humdrum data.  When the data is 
processed by verovio, the options will be used to control the rendering 
of the music notation.

The basic format for an embedded option is

```
!!!verovio: spacingStaff 0
```

The line starts with `!!!verovio:` followed by a camelCase verovio option name 
(as used in the Javascript version of the verovio toolkit), followed by at least
one space and then the value for that option.  Multiple options can be
given in the file, with one option on each line.  In the above case, the
spacing between staves is set to 0.  Compare the following example that uses the 
default staff spacing:


{% include verovio.html
	source="spacing-default"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-min-height="470px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-default">
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>

Adding an option to widen the spacing between staves:

{% include verovio.html
	source="spacing-wide"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-wide">
!!!verovio: spacingStaff 18
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>


See the [complete list](/options/list) of verovio options that can be
embedded along with their default values and allow ranges for numeric options.


The options can occur at any location in the file.  Duplicate options give 
priority to the last occurence in the file.  For option parameter groups, the
groups will be processed in the order in which they are listed in the 
file (probably).

## Option sets ##

Multiple option sets can be embedded into a file.  For example, here are
two option groups for staff spacing:

```
!!!verovio-compact: spacingStaff 0
!!!verovio-spacious: spacingStaff 20
```

To activate a particular option group, add a line such as the following to the file:

```
!!!verovio-parameter-group: spacious
```

This will cause the "spacious" option group to be used, while all other
groups will be ignored:


{% include verovio.html
	source="spacing-group"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group">
!!!verovio-compact: spacingStaff 0
!!!verovio-compact: leftMarginClef 0.00
!!!verovio-spacious: spacingStaff 20
!!!verovio-spacious: leftMarginClef 2.00
!!!verovio-parameter-group: spacious
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>

Now choosing the "compact" parameter group:

{% include verovio.html
	source="spacing-group2"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group2">
!!!verovio-compact: spacingStaff 0
!!!verovio-compact: leftMarginClef 0.00
!!!verovio-spacious: spacingStaff 20
!!!verovio-spacious: leftMarginClef 2.00
!!!verovio-parameter-group: compact
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>

Note that embedded verovio parameters not belonging to a
specific group will always be active.  To use such parameters
as default values for a parameter, place them above any
group equivalents.  If placed afterwards, the will supercede
the group parameters.


{% include verovio.html
	source="spacing-group3"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group3">
!!!verovio-compact: spacingStaff 0
!!!verovio-spacious: spacingStaff 20
!!!verovio-parameter-group: spacious
!!!verovio: spacingStaff 0
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>


Here is the proper use of the default parameters, allowing the group
parameter set "spacious" to override it:


{% include verovio.html
	source="spacing-group4"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group4">
!!!verovio: spacingStaff 0
!!!verovio-compact: spacingStaff 0
!!!verovio-spacious: spacingStaff 20
!!!verovio-parameter-group: spacious
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>




