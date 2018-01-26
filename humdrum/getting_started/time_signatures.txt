## Time signatures ##

Time signatures are interpretations in the form `*MX/Y` where `X` is the top
number of the signature and `Y` is the bottom number of the signature:

{% include verovio.html
	humdrum-min-height="310px"
	source="time1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="time1">
**kern
*clefG2
*M4/4
*met(c)
=1
4c
4d
4e
4f
=2
*M3/2
2g
2f
2d
=
*-
</script>


### Meter symbols ###

Cut-time and Common-time symbols can be displayed by including an interpretation
in the form `*met(X)`, where `X` is `c|` for cut-time, or `c` for common time:

{% include verovio.html
	humdrum-min-height="310px"
	source="meter1"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="meter1">
**kern
*clefG2
*M4/4
*met(c)
=1
4c
4d
4e
4f
=2
*M2/2
*met(c|)
2g
2a
=
*-
</script>

The time signature equivalent of the meter symbol should still be encoded, 
typically immediately before the meter symbol.  Try deleting the meter symbol
lines from the above example and see what happens.
