## Octaves ##

The octave position of a note is indicated in `**kern` data as
various repetitions of the pitch name as an upper- or lower-case letter.
The middle-C octave is indicated by single lower case letters, and each
successively higher octave repeats an additional lower-case letter to indicate
the octave:

{% include verovio.html
	source="octave1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="octave1">
**kern
*clefG2
2c
2cc
2ccc
*-
</script>

Lower octaves are indicated by successive repetitions of upper-case letters:

{% include verovio.html
	source="octave2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="octave2">
**kern
*clefF4
2C
2CC
2CCC
*-
</script>
