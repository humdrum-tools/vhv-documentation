---
title: melisma filter
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 15 Sep 2019
last_updated:
ref: filters-melisma
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/melisma/index.html
---

The melisma filter can be used to analyze the relation between notes and syllables in music.

The default behavior of the filter is to highlight notes for all syllables that have two
or more notes:

{% include verovio.html
	source="basic"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="basic">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma
</script>


### Set a minimum note count ##

The `-m` option can be used to set the minimum number of notes
that will be marked as a melisma.  The default value is 2 notes,
this can be raised.  Here is an example which set the minimum to 3,
causing the first two words to no longer be marked as melismas:

{% include verovio.html
	source="three"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="three">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma -m 3
</script>


### Display melisma counts ###

The `-r` option can be used to replace the lyrics with the note counts for each syllable:

{% include verovio.html
	source="replace"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="replace">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma -r
</script>

Re-run the melisma filter to highlight melisma notes:

{% include verovio.html
	source="rerun"
	scale="60"
	pageWidth="1000"
	humdrum-min-height="400px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="rerun">
**kern	**text
*M4/4	*
=1	=1
4c	This
4d	.
4e	is
4f	.
=2	=2
4g	some
4a	.
4b	.
4cc	text.
=3	=3
4b	set
4a	to
4g	mu-
4f	-sic
==	==
*-	*-
!!!filter: melisma -r
!!!filter: melisma -m 3
</script>


### Command-line options ###

The `-a` option will calculate the average note-to-syllable ratio for identified melisma syllables.

The `-p` option will calculate note-to-syllable ratios by part.

The `-w` option will list words in the music that contain a melisma.




