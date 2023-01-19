
## Ties ##

Tied notes do not get labeled with scale degrees by default:

{% include verovio.html
	source="tie1"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="tie1">
!!!filter: deg
**kern
*M3/4
*k[]
*E-:
2e-
[4f
=
4f]
2g
=
*-
</script>

If you want to see scale degrees on secondary tied notes, add the `-t` option:

{% include verovio.html
	source="tie2"
	humdrum-min-height="275px"
	scale="50"
	tabsize="8"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="tie2">
!!!filter: deg -t
**kern
*M3/4
*k[]
*E-:
2e-
[4f
=
4f]
2g
=
*-
</script>

[To do: When a scale degree is related to a tied note (other than the starting
note of the tie, an underscore is placed before the degree number in `**deg`
spines.  You can use the [shed](/filter/shed) filter to colorize the tied
scale degrees.]


