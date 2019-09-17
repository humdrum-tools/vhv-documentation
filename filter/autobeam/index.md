---
title: autobeam filter
lang: en
ref: filters-autobeam
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
permalink: /filter/autobeam/index.html
---

The autobeam filter can be used to automatically add beams to notes
according to the prevailing meter.  Here is an example where the 
autobeam filter is being applied to the music, which contains one
measure of 3/4 music and another in 6/8.

{% include verovio.html
	source="meterchange"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="meterchange">
!!!filter: autobeam
**kern
*M3/4
8c
8e
8d
8f
8g
8e
=
*M6/8
8c
8d
8e
8g
8f
8e
==
*-
</script>

Try deleting the filter from the above Humdrum data and see what happens.


In the VHV editor, you can also type <span class="keypress">alt-c</span>
to "compile" the filter, which will result in the beam markers being 
added to the data in the editor.  (The <span class="keypress">alt-c</span>
command will not work on this page, however).


### Selecting a particular spine ###

If only a single staff needs to be processed, then used the `-t` (track) option. 
The first track (spine) is the left-most (beginning) one in the data.  Here is an
example of beaming the second track (spine) while leaving the first one unaltered:



{% include verovio.html
	source="track"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="track">
!!!filter: autobeam -t 2
**kern	**kern
*M3/4	*M3/4
8c	8cc
8e	8ee
8d	8dd
8f	8ff
8g	8gg
8e	8ee
=	=
*M6/8	*M6/8
8c	8cc
8d	8dd
8e	8ee
8g	8gg
8f	8ff
8e	8ee
==	==
*-	*-
</script>


### Selecting a particular staff ###

In addition to selecting by track, you can also select by staff.
Specifically by `**kern` spine number, starting with 1 as the lowest
staff (left-mote `**kern` spine in the data).  In the following data,
the last spine is the 3rd track, but the 2nd staff:



{% include verovio.html
	source="kern"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="8"
%}
<script type="application/json" id="kern">
!!!filter: autobeam -k 2
**kern	**fing	**kern
*M3/4	*	*M3/4
8c	1	8cc
8e	3	8ee
8d	2	8dd
8f	4	8ff
8g	3	8gg
8e	5	8ee
=	=	=
*M6/8	*	*M6/8
8c	1	8cc
8d	2	8dd
8e	3	8ee
8g	5	8gg
8f	4	8ff
8e	3	8ee
==	==	==
*-	*-	*-
</script>


### Removing beams ###

Use the `-r` option to remove existing beams.  Here is an example
where the beams on the top staff are removed:


{% include verovio.html
	source="remove"
	scale="60"
	humdrum-min-height="365px"
	pageWidth="1450"
	tabsize="16"
%}
<script type="application/json" id="remove">
!!!filter: autobeam -r -k2
**kern	**kern
*M3/4	*M3/4
8cL	8ccL
8e	8ee
8d	8dd
8f	8ff
8g	8gg
8eJ	8eeJ
=	=
*M6/8	*M6/8
8cL	8ccL
8d	8dd
8e	8ee
8g	8gg
8f	8ff
8eJ	8eeJ
==	==
*-	*-
</script>


