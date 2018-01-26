## Multiple staves ##

Each `**kern` spine in the data will produce a staff in the graphical notation.
The lowest staff is the left-most spine in the data, and the highest staff
in the notation is the right-most spine.


{% include verovio.html
	humdrum-min-height="360px"
	source="staves1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="staves1">
**kern	**kern
*M4/4	*M4/4
=1	=1
*	*^
1E	2cc	4a
.	.	4g
*	*v	*v
.	4f
.	4e
=2	=2
*	*^
1E	2cc	4a
.	.	4g
.	2ryy	4f
.	.	4e
*	*v	*v
=	=
*-	*-
</script>
