## Dynamics ##

Dynamics are added to the staff as a separate spine to the right of a `**kern`
spine to which the dynamics should be associated with.

{% include verovio.html
	humdrum-min-height="350px"
	source="dynam1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="dynam1">
**kern	**dynam
*clefG2	*
*M4/4	*
=1	=1
4c	p
4d	<
4e	(
4f	(
.	[
=2	=2
2g	f
.	>
4f	)
4d	)
=	=
1c	]
==	==
*-	*-
</script>

When lyrics are present, dynamics will automatically be placed above the staff:

{% include verovio.html
	humdrum-min-height="350px"
	source="dynam2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="dynam2">
**kern	**dynam	**text
*clefG2	*	*
*M4/4	*	*
=1	=1	=1
4c	p	The
4d	<	ru-
4e	(	-ler
4f	(	of
.	[	.
=2	=2	=2
2g	f	the
.	>	.
4f	)	realm
4d	)	was
=	=	=
1c	]	seen
==	==	==
*-	*-	*-
</script>


Note that the order of the `**dynam` and `**text` spines does not matter.
