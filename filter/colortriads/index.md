---
title: colortriads filter
lang: en
ref: filters-colortriads
author: Craig Stuart Sapp
translator:
creation_date: 10 Sep 2020
translation_date:
last_updated: 10 Sep 2020
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
datatable: "true"
keywords: color triad command
summary: "Colors diatonic triadic sonorities by root pitch/function."
permalink: /filter/colortriads/index.html
---

The colortriads filter assigns colors to vertical sonorities 
according to their diatonic triadic root.  The colors are assigned
using colors of the rainbow mapped to the circle-of-fifths, with
C centered in the middle at green:

{% include image.html
	file="color-to-pitch.png"
	alt="Color-to-pitch mapping"
	caption="Color-to-pitch mapping for triad sonorities."
%}



{% include verovio.html
	source="chords"
	humdrum-min-height="225px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="chords">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads
</script>


The color green represents vertical sonorities with
the three diatonic pitch classes C, E, and G.  Any chromatic
alterations of these pitch classes are also given a green color,
such as C, E-flat, G, or C-sharp, E, G-flat.

{% include verovio.html
	source="cchords"
	humdrum-min-height="250px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="cchords">
**kern
4c 4e 4g
4cc 4e 4g
4cc 4g 4ee
4c 4g 4ee
4c 4e- 4g
4c# 4e- 4g#
4c# 4en 4g#
4c## 4e-- 4g# 4ee 4gg-
=
*-
!!!filter: colortriads
</script>



Here is a [Bach chorale with colored triadic sonorities](https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn&filter=colortriads%20%7C%20satb2gs):


{% include image.html
	file="chorale-2-pitch.png"
	alt="Colorized triads in Bach Chorale BWV 347"
	caption="Colorized triads in Bach chorale, BWV 347"
%}


Circle-of-fifth root motions are visualized by cycling through the
colors of the rainbow such as in measures 10&ndash;11 where the
chord sequence E major, B minor, F-sharp minor are shown in the
colors red, orange and yellow.  Looking at the fermata chords, most
of them are red, indicating E major (V), with an orange one on B
minor (ii), and the last chord in purple, indicating A major (I).

Non-triadic sonorities are left uncolored.  This will typically be
non-harmonic tones and seventh chords in the chorales.  Occasionally
a note will be in two or more separate triadic sonorities, such as
at the beginning of measure 6 where the downbeat is a D-major chord,
and the double passing tones create a G-diminished sonority:

{% include verovio.html
	source="double"
	tabsize="12"
	humdrum-min-height="150px"
	humdrum-min-width="400px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="double">
**kern	**kern	**kern	**kern
*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]	*k[f#c#g#]
4D	4d	8f#L	8aL
.	.	8g#J	8bJ
*-	*-	*-	*-
!!!filter: colortriads | satb2gs
</script>

In such cases the pitches shared between sonorities will only be
given one color, depending on which triadic root was assigned color
first.



## Functional coloring ##

Adding the `-r` option (meaning "relative") will instead color the
triadic sonorities by function, using green as the tonic:

{% include image.html
	file="color-to-function.png"
	alt="Color-to-function mapping"
	url="https://verovio.humdrum.org/?file=chorales/chor002.krn&filter=colortriads%20%7C%20satb2gs"
	caption="Color-to-function mapping for triad sonorities when '-r' is option is added."
%}


An initial key designation, such as `*a:` for A minor, is needed
to identify the tonic.  

{% include verovio.html
	source="achords"
	humdrum-min-height="250px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="achords">
**kern
*a:
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -r
</script>

Alternately, the `-k` option can be used
to supply a key designation if there is none in the data:

{% include verovio.html
	source="echords"
	humdrum-min-height="225px"
	humdrum-min-width="275px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="echords">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -r -k e
</script>

Now E is treated as the tonic.


Here is an example of [the same Bach chorale with functional coloring](https://verovio.humdrum.org/?file=chorales/chor002.krn&filter=colortriads%20-r%20%7C%20satb2gs):

{% include image.html
	file="chorale-2-function.png"
	alt="Functionally colored triads in Bach Chorale BWV 347"
	caption="Functionally Colored triads in Bach chorale, BWV 347"
%}


Now the fermata sonorities on the dominant chords are colored light
blue, the supertonic is dark blue, and the tonic is green.

Such functional coloring allows easier comparison of chord functions
between pieces in different keys.  You can [scroll through the
chorales](https://verovio.humdrum.org/?k=ey&file=chorales/chor001.krn&filter=colortriads%20-r%20%7C%20satb2gs)
with the arrow buttons at the top left side of the VHV window, or use
<span class="keypress">shift-right</span> and <span
class="keypress">shift-left</span> to browse through the VHV Bach
chorale repertory.


## Changing colors ##

Color assignments can be changed with the `-a` through `-g`
options.  Here is an example of changing C triads from green to fuscia:


{% include verovio.html
	source="fuchsia"
	humdrum-min-height="225px"
	humdrum-min-width="300px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="fuchsia">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -c fuchsia
</script>

Any [SVG color](https://www.december.com/html/spec/colorsvg.html) can be used,
as well as [HTML color codes](https://htmlcolorcodes.com).  To change the color
for A sonorities, use `-a`, for B sonorities use `-b`, and so on.

## Suppressing colors ##

Use options `-A` through `-G` to suppress coloring triads containing
that root.  Single-letter options can be glued to each other, so the option
`-ABC` in the example below is equivalent to `-A -B -C`:


{% include verovio.html
	source="suppress"
	humdrum-min-height="225px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="suppress">
**kern
4e 4g 4b
4b 4dd 4ff
4f 4a 4cc
4cc 4ee 4gg
4g 4b 4dd
4d 4f 4a
4a 4cc 4ee
=
*-
!!!filter: colortriads -ABC
</script>

## Extended coloring ##

The colortriads filter is a front-end to the [msearch](/filters/msearch)
filter.  Using the command-line version of colortriads, you can extract
the calls to the msearch filter by adding the `--filters` option:

```bash
colortriads --filters file.krn
```

The default settings will produce this output:

```
!!!filter: msearch -p (=ace) -m V --color darkviolet
!!!filter: msearch -p (=bdf) -m Z --color darkorange
!!!filter: msearch -p (=ceg) -m @ --color limegreen
!!!filter: msearch -p (=dfa) -m "|" --color royalblue
!!!filter: msearch -p (=egb) -m j --color crimson
!!!filter: msearch -p (=fac) -m + --color gold
!!!filter: msearch -p (=gbd) -m N --color skyblue
```

There are seven calls to msearch, one for each triadic root to
color.  The `--color` option sets the color, which is red by default.
The `-m` option is used to specify the user signifier that will
mark the note (and cause it to be colored).  This can be a character
in the set "NVZ@|+ijl" plus others with varying degrees of success,
such as characters in the set "kKhPps".  Note that mark characters
must be unique; otherwise, different color assignments with a shared
mark will collapse to one of those colors.  Unicode characters may
be allowed (or will be allowed in the future).

The `-p` option give the pitch pattern to search for.  The pattern
`(=ace)` means to search for a vertical sonority that contains one
or more of each of the three pitch classes A, C, and E.  The
parentheses indicate a harmonic search (rather than a melodic
search), and the equals sign requires that only the listed pitch
classes be present in the sonority (without the equals sign, other
pitch classes are allowed).

If you want to refine the coloring you can copy the above filters
as a template to color in various ways.  For example, to color A
minor triads dark violet and A major triads medium purple, use these
two commands:



```
!!!filter: msearch -p (=ancnen) -m N --color darkviolet
!!!filter: msearch -p (=anc#en) -m V --color mediumpurple
```



{% include verovio.html
	source="majorminor"
	humdrum-min-height="150px"
	humdrum-min-width="475px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="majorminor">
**kern
4a 4cc 4ee
4a 4cc# 4ee
=
*-
!!!filter: msearch -p (=ancnen) -m N --color darkviolet
!!!filter: msearch -p (=anc#en) -m V --color mediumpurple
</script>



The query "ancnen" means A-natural, C-natural and E-natural, with
space between notes optional.  When giving a chromatic alteration
to a diatonic pitch class, only that variant will be colored,
allowing for different colors to be assigned to major and minor
chords.

In a similar manner, dominant seventh chords could colored:

{% include verovio.html
	source="domsev"
	humdrum-min-height="175px"
	humdrum-min-width="450px"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="domsev">
**kern
4c 4e 4g
4g 4b 4dd
4g 4b 4dd 4ff
=
*-
!!!filter: colortriads
!!!filter: msearch -p (=gnbndnfn) -m l --color fuchsia
</script>

To view the command-line commands rather than as filters,
use the `--commands` option:


```bash
colortriads --commands file.krn
```

```
msearch -p (=ace) -m V --color darkviolet
msearch -p (=bdf) -m Z --color darkorange
msearch -p (=ceg) -m @ --color limegreen
msearch -p (=dfa) -m "|" --color royalblue
msearch -p (=egb) -m j --color crimson
msearch -p (=fac) -m + --color gold
msearch -p (=gbd) -m N --color skyblue
```


## Limitations ## 

Coloring is currently limited to monophonic parts, with limited
capabilities for coloring chords and sub-spines (multi-voiced) parts, as
is commonly found in piano music.  The ability to color these textures will
be added in the future.



