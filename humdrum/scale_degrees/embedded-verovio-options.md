

## Embedded verovio options ##

There are additional layout controls provided by <a href="https://verovio.org" target="_blank">verovio</a>
that can be used to refine the notation.  Here is an example, first without the option:

{% include verovio.html
	source="verovio"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="verovio">
**kern	**deg	**deg	**deg	**deg
*clefG2	*	*fs:75%	*fs:130%	*fs:100%
*M4/4	*	*circ	*	*box
*k[]	*	*	*	*
*C:	*C:	*C:	*C:	*C:
=1	=1	=1	=1	=1
4c	1	1	1	1
4d	2	2	2	2
4e	3	3	3	3
4f	4	4	4	4
*	*	*	*	*fs:50%
4g	5	5	5	5
4a	6	6	6	6
*	*	*	*	*fs:200%
4b	7	7	7	7
4cc	1	1	1	1
=	=	=	=	=
*-	*-	*-	*-	*-
</script>


And now with the verovio option:

```
!!!verovio: topMarginHarm 10
```

(still working on this example)

{% include verovio.html
	source="verovioout"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="verovioout">
!!!verovio: topMarginHarm 10
**kern	**deg	**deg	**deg	**deg
*clefG2	*	*fs:75%	*fs:130%	*fs:100%
*M4/4	*	*circ	*	*box
*k[]	*	*	*	*
*C:	*C:	*C:	*C:	*C:
=1	=1	=1	=1	=1
4c	1	1	1	1
4d	2	2	2	2
4e	3	3	3	3
4f	4	4	4	4
*	*	*	*	*fs:50%
4g	5	5	5	5
4a	6	6	6	6
*	*	*	*	*fs:200%
4b	7	7	7	7
4cc	1	1	1	1
=	=	=	=	=
*-	*-	*-	*-	*-
</script>
