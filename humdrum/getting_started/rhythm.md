## Rhythm ##

Rhythms in `**kern` data are given in terms of the number of units
the duration of the note will divide a whole note.  Whole notes are `1` since there
is one whole note in a whole note.  Half notes are `2` since there are two in
a whole note.  Quarter notes are `4` since there are four in a whole note, *etc.*

An exception to the numeric system for rhythms is used for some notes
longer than a whole note: breves are represented by `0`, longs are represented
by `00` and maximas by `000`.

{% include verovio.html
	humdrum-min-height="300px"
	evenNoteSpacing="1"
	spacingLinear="1"
	source="rhy1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="rhy1">
**kern
000b
00b
0b
1b
2b
4b
8b
16b
32b
64b
128b
256b
==
*-
</script>

The shortest note value that verovio can display is a 256th note, although shorter values
can be represented in `**kern` data.


### Augmentation dots ###

Augmentation dots are represented by period characters (`.`).  The first one
adds 1/2 the duration of the plain note, 
the next adds an additional 1/4 of the original note, and so on.

{% include verovio.html
	humdrum-min-height="275px"
	evenNoteSpacing="1"
	source="dots1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="dots1">
**kern
4.b
4..b
4...b
4....b
4.....b
=-
4.......b
4........b
4.........b
4..........b
4...........b
==
*-
</script>
