---
title: semitones filter
lang: en
ref: filters-semitones
author: Craig Stuart Sapp
translator: 
creation_date: 15 Nov 2020
translation_date: 
last_updated: 15 Nov 2020
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/semitones/index.html
---


The semitones filter calculates melodic semitone intervals for 
`**kern` spine notes.  The filter can also be used to highlight
steps, leaps, repetitions, and interval directions in the 
rendered notation.


## Options ##

| option | description  |
| ------ | -----------  |
| -c     | Store analyses in `**cdata` spines, which display as text above staves in rendered notation. |
| -d     | Highlight/count only downward intervals. |
| -j #   | Set the semitone value for the boundary between steps and leaps (default: 3). |
| -l     | Highlight/count only leaps. |
| -m     | Extract MIDI note numbers rather than semitones. |
| -n     | Include highlighted interval count in output data. |
| -r     | Highlight/count repeated notes. |
| -s     | Highlight/count steps. |
| -u     | Highlight/count notes with upward interval. |
| -x *expr* | Exclude notes matching regular expressions. |
| -A     | Do not output analysis spines. |
| -I     | Do not include input data in output data. |
| -M     | Do not mark any notes. |
| -R     | Ignore rests. |
| -T     | Do not highlight secondary tied notes. |
| -X     | Only calculate intervals starting in tokens containing expression. |
| -1     | Only highlight first note of marked intervals. |
| -2     | Only highlight second note of marked intervals. |
| --color *string* | Set the color of the marked notes. |
| --mark  *char*   | Set the signifier character for marked notes. |


## Displaying semitone intervals ##

The default output of the semitones filter creates a `**tti` (twelve-tone interval) 
spine after each `**kern` spine.   This analysis is not printed in the 
rendered notation.   To view the semitone interval analysis in the 
notation, add the `-c` option to output the analysis in `**cdata`
spines (meaning "chord-like" data) that will be displayed above
the notation.

{% include verovio.html
	source="example1"
	scale="50"
	humdrum-min-width="180"
	spacingSystem="20"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example1">
!!!filter: semitones -c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

Notice that the melodic semitone interval is shown on the first
note of the interval.  Try editing the musical text on the left
to watch the analysis change in the graphical notation on the right.


## Highlighting categories of intervals ##

The following options can be used to highlight groups of intervals:

| option | meaning |
| ------ | ------- |
| -u     | Highlight only notes involved in upward intervals. |
| -d     | Highlight only notes involved in downward intervals. |
| -r     | Highlight only repeated notes. |
| -s     | Highlight only notes involved in stepwise motion. |
| -l     | Highlight only notes involved in leaping motion. |

Examples of various highlighting options are given below.

### Highlight repeated notes ###

Adding the `-r` option will highlight notes that repeat.


{% include verovio.html
	spacingSystem="20"
	source="example-repeat"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-repeat">
!!!filter: semitones -rc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

### Highlight upward intervals ###

Adding the `-u` option will highlight notes that create upward
semitone intervals.


{% include verovio.html
	spacingSystem="20"
	source="example-up"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-up">
!!!filter: semitones -uc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

### Highlight downward intervals ###

Adding the `-d` option will highlight notes that create downward
semitone intervals.


{% include verovio.html
	spacingSystem="20"
	source="example-down"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-down">
!!!filter: semitones -dc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


### Highlight stepwise intervals ###

Adding the `-s` option will highlight notes that create stepwise
semitone intervals.


{% include verovio.html
	spacingSystem="20"
	source="example-step"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-step">
!!!filter: semitones -sc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


### Highlight leap intervals ###

Adding the `-l` option will highlight notes that create melodic leaps.


{% include verovio.html
	spacingSystem="20"
	source="example-leap"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-leap">
!!!filter: semitones -lc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


The boundary between leaps and steps is `3` by default (the smallest leap
is three semitones, or a minor third).  To change the boundary between
leaps and steps use the `-j` option (meaning "jump") followed by the
minimum leap size, such as `-j4`, which will define a `3` (minor third) 
as a step.  To make the example clear, the `-1`, option is used below
to highlight only the first note creating the intervals:

{% include verovio.html
	spacingSystem="20"
	source="example-leap2"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-leap2">
!!!filter: semitones -lc1j4
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>



### Highlight mixtures of interval groups ###

The up/down interval options can be paired with the step/leap
intervals to highlight intervals that satisfy both requirements:

| options | meaning |
| `-us`   | highlight step-wise upward intervals.   |
| `-ds`   | highlight step-wise downward intervals. |
| `-ul`   | highlight upward leaping intervals.   |
| `-dl`   | highlight upward leaping intervals.   |


Here is an example of highlighting only upward steps:

{% include verovio.html
	spacingSystem="20"
	source="example-mix-step"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-mix-step">
!!!filter: semitones -usc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

And downward leaps:


{% include verovio.html
	spacingSystem="20"
	source="example-mix-leap"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-mix-leap">
!!!filter: semitones -dlc
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>



## Highlighting only one interval note ##

The `-1` option can be used to highlight only the first note
of an interval pair:


{% include verovio.html
	spacingSystem="20"
	source="example-first"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-first">
!!!filter: semitones -s1c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

and `-2` highlights only the second note of the interval:

{% include verovio.html
	spacingSystem="20"
	source="example-second"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-second">
!!!filter: semitones -s2c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


## Highlight styling ##

Various interval groups can be highlighted in 
different colors by using the `--mark` and `--color` options.  Both
must be specified to mark intervals with different colors.

made, and the color of the groups can be controlled independently.
Here is an example of using the default markers `@` and red color
for the upward leaps, and then using a different marker to indicate
a different color for downward leaps:

{% include verovio.html
	spacingSystem="20"
	source="example-color"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-color">
!!!filter: semitones -u -l -A -1
!!!filter: semitones -dl1 --mark Z --color dodgerblue
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>


## Rests ##

By default intervals are not calculated across rests:

{% include verovio.html
	source="example-rest"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-rest">
!!!filter: semitones -c
**kern
*M4/4
=1
4c
4d
4e
4r
=
4f
4g
4a
4b
=
*-
</script>


By adding the `-R` option, rests will be ignored:

{% include verovio.html
	source="example-norest"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-norest">
!!!filter: semitones -cR
**kern
*M4/4
=1
4c
4d
4e
4r
=
4f
4g
4a
4b
=
*-
</script>


## Note exclusion/inclusion ##

The `-x` option can be used to prevent an interval from being
calculated based on a regular expression pattern.  Here is an 
example where the interval after a fermata is suppressed:


{% include verovio.html
	spacingSystem="20"
	source="example-nofermata"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-nofermata">
!!!filter: semitones -c -x ';'
**kern
*M4/4
=1
4c
4d
4e
4f;
=
4g
4a
4b
4cc
=
*-
</script>

Note that the interval for the fermata is `x`, meaning that it is
excluded from the analysis.  This is useful for use as a segmentation
boundary for post-processing of the extracted intervals.  When the
string is a semi-colon (`;`), the quotes around the exclusion
expression does not have to be in quotes, but if the filter is used
on the command-line, the quotes are required.


The `-X` option reverse the exclusion, and only note tokens that 
contain the specified regular expression will be analyzed:

{% include verovio.html
	spacingSystem="20"
	source="example-onlyfermata"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-onlyfermata">
!!!filter: semitones -c -X ';'
**kern
*M4/4
=1
4c
4d
4e
4f;
=
4g
4a
4b
4cc
=
*-
</script>

So this example only calculates the intervals that start on fermata notes.


## VHV Examples ##

Here is an example using the following filters to highlight
each refined interval class:

```
!!!filter: semitones -ul2A
!!!filter: semitones -dl2A --mark j --color hotpink
!!!filter: semitones -us2A --mark V --color dodgerblue
!!!filter: semitones -ds2A --mark Z --color blue
!!!filter: semitones -r2A --mark + --color limegreen
!!!filter: satb2gs
```

Try copy-and-pasting the above filter lines into VHV for the
example [Bach chorale](http://verovio.humdrum.org/?file=chorales/chor001.krn) used below.

The `-2` option is used to highlight only the second note of the interval
notes.  This means that the color indicates the approach interval.  You
can try changing this to `-1` to have the color indicate the departure
interval.  The `-A` option is used to prevent multiple duplicate 
output analysis spines to be generated.  This is optional, since the
analysis spines are not displayed in the graphical notation.

{% include note.html
	content="Notice that each category must be given a unique mark since the coloring occurs via these marks.  If two group have the same group, then only one color can be used for both groups."
%}


{% include image.html
	file="refinedcontour.png"
	url="http://verovio.humdrum.org/?file=chorales/chor001.krn&filter=semitones%20-ul2A|semitones%20-dl2A%20--mark%20j%20--color%20hotpink|semitones%20-us2A%20--mark%20V%20--color%20dodgerblue|semitones%20-ds2A%20--mark%20Z%20--color%20blue|semitones%20-r2A%20--mark%20+%20--color%20limegreen|satb2gs"
	alt="Highlighting step/leap categories"
	caption="Highlighting step/leap categories using the semitones filter"
	margin-bottom="-20px"
%}

Click on the image to load the score and the highlighting filters
into VHV.  Then use the left/right arrow buttons at the top of the
page to browse through other chorales with the highlighted intervals.

Try adding `-x ';'` to each semitones filter to ignore intervals after
fermatas.

Try adding `-j 5` so that leaps are defined as forths or larger intervals.



## MIDI note numbers ##

Adding the `-m` will extract MIDI note numbers rather than semitone
intervals:

{% include verovio.html
	spacingSystem="20"
	source="example-midi"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-midi">
!!!filter: semitones -cm
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

Here is an example of extracting both MIDI note numbers and semitone
intervals:

{% include verovio.html
	spacingSystem="20"
	source="example-midisemi"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-midisemi">
!!!filter: semitones -cm
!!!filter: semitones -c
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
</script>

Notice that the MIDI note number plus the semitone interval below
it gives the note number of the next note.

## Dealing with chords ##

When chords are present in the input data, only the first note
in the chord will be considered.  If you do not know the ordering
of notes in the chord, or you want to force the highest or lowest
note in the chord to be used, use the *chord*  filter to sort the
notes in the chord before analysis.


Here is an example where the chords notes are mixed up, and the 
intervals between the single note and the chord changes in each 
measure due the chord-note ordering:

{% include verovio.html
	spacingSystem="20"
	source="example-chord1"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord1">
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>

Sorting the chord notes from high to low, using the `-d` (downward) option:

{% include verovio.html
	spacingSystem="20"
	source="example-chord2"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord2">
!!!filter: chord -d
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>



Sorting the chord notes from low to high, using the `-u` (upward) option:

{% include verovio.html
	spacingSystem="20"
	source="example-chord3"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord3">
!!!filter: chord -u
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>


If you do not want the chord-tone notes not used in the semitone
analysis to be displayed, use the `-f` option (meaning "first") for
the chord filter to keep only the first note of the chord.  To sort
notes before taking the first note, use `-t` to select the top (highest)
note, or `-b` to select the bottom (lowest) note for each chord.

{% include verovio.html
	spacingSystem="20"
	source="example-chord4"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord4">
!!!filter: chord -t
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>

{% include verovio.html
	spacingSystem="20"
	source="example-chord5"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="example-chord5">
!!!filter: chord -b
!!!filter: semitones -c
**kern
*M4/4
=1
4cc
4c 4e 4g
4cc
4c 4e 4g
=
4cc
4g 4e 4c
4cc
4g 4e 4c
=
4cc
4e 4c 4g
4cc
4e 4g 4c
=
*-
</script>



## Command-line use ##

When using on the command line with no options, `**tti` (twelve-tone interval)
spines are placed after each `**kern` spine from which the analysis
is extracted:


```bash
humcat h://chorales/chor001.krn | semitones
```

```tsv
**kern	**tti	**kern	**tti	**kern	**tti	**kern	**tti
*Ibass	*Ibass	*Itenor	*Itenor	*Ialto	*Ialto	*Isoprn	*Isoprn
*clefF4	*clefF4	*clefGv2	*clefGv2	*clefG2	*clefG2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M3/4	*M3/4	*M3/4	*M3/4	*M3/4	*M3/4	*M3/4	*M3/4
4GG	12	4B	0	4d	0	4g	0
=1	=1	=1	=1	=1	=1	=1	=1
4G	-3	4B	1	4d	2	2g	7
4E	2	8cL	-1	4e	-2	.	.
.	.	8BJ	-2	.	.	.	.
4F#	1	4A	-2	4d	0	4dd	-3
=2	=2	=2	=2	=2	=2	=2	=2
4G	-5	4G	-1	2d	-3	4.b	-2
4D	2	4F#	1	.	.	.	.
.	.	.	.	.	.	8a	-2
4E	-4	4G	5	4B	5	4g	0
=3	=3	=3	=3	=3	=3	=3	=3
4C	-1	8cL	-1	8eL	-2	4.g	2
.	.	8BJ	1	8d	2	.	.
8BBL	-2	4c	2	8e	2	.	.
8AAJ	-2	.	.	8f#J	1	8a	2
4GG	7	4d	0	4g	-1	4b	-2
=4	=4	=4	=4	=4	=4	=4	=4
2D;	-7	2d;	0	2f#;	1	2a;	2
4GG	-1	4d	-5	4g	-5	4b	3
=5	=5	=5	=5	=5	=5	=5	=5
etc.
```


### Output only analysis data ###

By default the output data includes all of the input data, inserting
the analysis spines immediately to the right of each `**kern` spine.
The input data can be suppressed in the output by adding the `-I` option,
meaning "no input":

```bash
humcat h://chorales/chor001.krn | semitones -I
```

```tsv
**tti	**tti	**tti	**tti
*Ibass	*Itenor	*Ialto	*Isoprn
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M3/4	*M3/4	*M3/4	*M3/4
12	0	0	0
=1	=1	=1	=1
-3	1	2	7
2	-1	-2	.
.	-2	.	.
1	-2	0	-3
=2	=2	=2	=2
-5	-1	-3	-2
2	1	.	.
.	.	.	-2
-4	5	5	0
=3	=3	=3	=3
-1	-1	-2	2
.	1	2	.
-2	2	2	.
-2	.	1	2
7	0	-1	-2
=4	=4	=4	=4
-7	0	1	2
-1	-5	-5	3
=5	=5	=5	=5
etc.
```


### Interval histograms for Bach chorales ###

Using the humlib tools *humcat*, *serialize*, *ridx*, and *sortcount*,
as well as the unix tool *sort*:

```bash
humcat -s h://chorales | semitones -I | serialize | ridx -H | sortcount | sort -nrk2
```

```tsv
1	24
4	19
6	17
4	16
2	15
9	14
5	13
609	12
17	11
37	10
193	9
183	8
1086	7
34	6
4340	5
819	4
1038	3
15270	2
9924	1
731	r
11241	0
11157	-1
17503	-2
2065	-3
2245	-4
1589	-5
268	-6
2144	-7
116	-8
68	-9
16	-10
6	-11
461	-12
7	-14
```

The first column is the interval count and the second column contains
the semitone interval.  The largest interval is `24` (two octaves
up), and the most common interval is `-2` (major second).

The following example creates a webpage containing an interactive
plot of the semitone histogram for the Bach chorales:


```bash
humcat -s h://chorales | semitones -I | serialize | ridx -H \
     | sortcount -v --sort number -x semitones \
     -T "Bach chorale melodic semitones"  > output.html
```

{% include_relative plot.txt %}

Move the mouse over each bar to see the count for each interval.


### Exclude intervals after fermatas ###

To avoid counting intervals after notes with fermatas:

```bash
humcat -s h://chorales | semitones -Ix ';' | serialize \
     | ridx -H | sortcount | sort -nrk2
```

```tsv
2	17
274	12
4	11
13	10
77	9
75	8
784	7
23	6
3625	5
414	4
603	3
14715	2
9436	1
9363	0
9	r
10935	-1
17130	-2
1786	-3
2003	-4
1418	-5
249	-6
2029	-7
99	-8
55	-9
11	-10
2	-11
432	-12
6	-14
```

Counting only intervals between fermatas and the following notes/rests:


```bash
humcat -s h://chorales | semitones -IX ';' | serialize \
     | ridx -H | sortcount | sort -nrk2
```

```tsv
1	24
9	19
2	18
13	17
14	16
10	15
27	14
14	13
380	12
30	11
71	10
151	9
163	8
404	7
77	6
827	5
489	4
541	3
656	2
561	1
752	r
2035	0
272	-1
459	-2
348	-3
291	-4
208	-5
38	-6
143	-7
28	-8
30	-9
10	-10
4	-11
30	-12
2	-14
```


```bash
humcat -s h://chorales | semitones -IX ';' | serialize \
     | ridx -H | sortcount -v --sort number -x semitones \
     -T "Intervals after fermatas" > output.html
```

{% include_relative plot2.txt %}


Repeated notes are most common after fermatas.


### Interval sequences in Bach chorales ###

Here is an example of how to identify the most common 5-interval sequences
in the Bach choral repertory:

```bash
humcat -s h://chorales | semitones -I | ridx -M \
   | serialize | context -n 5 | ridx -H | sortcount | head -n 20
```

```tsv
311	2 1 -1 -2 -2
271	-2 -2 -1 -2 2
262	2 2 1 -1 -2
246	2 1 2 -2 -1
243	1 2 -2 -1 -2
233	-2 -1 -2 2 1
227	-2 -2 -1 -2 -2
212	2 2 -2 -2 -1
203	-1 -2 -2 2 2
185	2 -2 -2 -1 -2
184	-1 -2 2 1 2
175	1 2 2 -2 -2
162	-2 -2 2 2 1
159	-2 2 1 -1 -2
150	-2 -1 -2 -2 2
147	-2 -1 1 -1 -2
147	-2 -2 -1 1 2
145	2 2 1 2 -2
144	2 1 -1 -2 2
137	-1 -2 2 1 -1
```

The 20 most common 5-interval sequences are all step-wise with no
repeated notes, rests, or leaps.

{% comment %}

## Polyphonic staves ##

When there are spine splits, the analysis will melodically follow
both subspines.   When splitting, the left-most path will be used
to calculate an interval to the previous note before the split.
When joining, multiple subspines may share the same merged note:



{ include verovio.html
	spacingSystem="20"
	source="example-poly"
	scale="50"
	humdrum-min-width="180"
	pageWidth="900"
}
<script type="application/x-humdrum" id="example-poly">
!!!filter: semitones -c
**kern
*M4/4
4c
4d
*^
4e	4g
4f	4a
=	=
4cc	4b
*v	*v
4f
4d
4c
=
*-
</script>
{% endcomment %}


## Counting highlighted intervals ##

Add the `-n` option to count intervals that are highlighted.  This will
add a line at the bottom of the data with the interval count followed
by the options used to select steps, leaps, upward, downward, etc.

For example, given the input data:

```tsv
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
```

The command/filter:

```bash
semitones -uln
```

will count the number of upwards leaps:

```tsv
**kern	**tti
*M4/4	*M4/4
=1	=1
4c	2
4d	2
4e	1
4f	-5
=	=
@4c	4
@@4e	3
@@4g	5
@4cc	0
=	=
4cc	-1
4b	-2
4a	-2
@4g	5
=	=
@4cc	-5
4g	-3
4e	-4
4c	.
=	=
*-	*-
!!!RDF**kern: @ = marked note
!!semitone_count: 4 UP LEAP
```

The line

```
!!semitone_count: 4 UP LEAP
```

means that there were four upward leaps in the example.


The `-M` option can be used to not mark any notes in the `**kern`
spines, and `-A` can be used to not output the analysis spines. 
These options will cause only the `semitone_count` line to be added
to the input data:

```bash
semitones -ulnMA
```

```tsv
**kern
*M4/4
=1
4c
4d
4e
4f
=
4c
4e
4g
4cc
=
4cc
4b
4a
4g
=
4cc
4g
4e
4c
=
*-
!!semitone_count: 4 UP LEAP
```

If you only want the interval count, then use the command:

```bash
semitones -uln input.krn | awk 'END {print $2}'
```

which in this case will return `4`.





