
## Scale degrees in minor keys ##

Minor keys use a lowercase letter in their key designations, such
as `*c:` for C minor and `*f#:` for F&#x266f; minor.  Note that the
harmonic minor is the prototype scale for minor keys (not the natural
minor).  The harmonic minor has a major 7th interval between the
tonic and the 7th scale degree, forming a lead tone to the tonic.

{% include verovio.html
	source="harminor"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="harminor">
**kern	**deg
*clefG2	*
*M4/4	*
*k[b-e-a-]	*
*c:	*c:
=1	=1
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4bn	7
4cc	1
=	=
*-	*-
</script>

To allow conversion between harmonic and natural minors, add `h` after a `7` scale degree
to confirm that it is a major seventh above the first scale degree (or a minor second below
the first scale degree).  To encode a 7th scale degree in a natural minor key, add `n` after the `7` 
for a minor seventh above or major second below the first scale degree.

{% include verovio.html
	source="bothminor"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="bothminor">
**kern	**deg
*clefG2	*arrow
*M4/4	*
*k[b-e-a-]	*
*c:	*c:
=1	=1
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4b	7h
4cc	1
=1||	=1||
4c	1
4d	2
4e-	3
4f	4
4g	5
4a-	6
4b-	7n
4cc	1
=	=
*-	*-
</script>

`7n` implies B-flat, and since the display is set to C harmonic minor, the `n` causes a flat to 
be displayed for the 7th scale degree (`n` or `h` on any other scale degree will be ignored).

### Major/minor mode markers ###

If you want to have local information about the modality of each scale degree, append 'm' for 
minor scale degrees, or `M` for major scale degrees.  These markers are for analyses, and do
not affect rendering of scale degrees in music notation.

{% include verovio.html
	source="majorminor"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="majorminor">
**kern	**deg
*clefG2	*
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1M
4d	2M
4e	3M
4f	4M
4g	5M
4a	6M
4b	7M
4cc	1M
=||	=||
*k[b-e-a-]	*minnat
*c:	*c:
4c	1m
4d	2m
4e-	3m
4f	4m
4g	5m
4a-	6m
4b-	7nm
4cc	1m
=	=
*-	*-
</script>


### Harmonic and natural minor ###

If you want to display the scale degrees in music notation using the natural minor scale, 
add the interpretation `*minnat`.   This means that the scale degrees are based on the
natural minor scale, with `7` and `7n` meaning a minor 7th and `7+` and `7h` meaning
a major seventh.  The interpretation `*minhar` can be used to explicitly indicate
that the harmonic minor is the prototype scale (or you can switch between the
two systems in a single spine by alternating between `*minnat` and `*minhar`.

{% include verovio.html
	source="minchange"
	humdrum-min-height="325px"
	scale="40"
	tabsize="11"
	pageWidth="1300"
%}
<script type="application/x-humdrum" id="minchange">
**kern	**deg	**text
*clefG2	*minnat	*v:**deg:
*M4/4	*arrow	*vv:**deg:
*k[b-e-a-]	*circle	*color:silver
*c:	*c:	*c:
=	=	=
!!LO:TX:a:t=**minnat:color=crimson
!!LO:TX:a:t=Natural minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4b-X	7	7
4b-X	7n	7n
4b-X	7h-	7h-
4cc	1	1
=	=	=
!!LO:TX:a:t=Harmonic minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4bn	7	7
4bn	7h	7h
4bn	7n+	7n+
4cc	1	1
=||	=||	=||
*c	*minhar	*
!!LO:TX:a:t=**minhar:color=crimson
!!LO:TX:a:t=Natural minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4b-X	7	7
4b-X	7n	7n
4b-X	7h-	7h-
4cc	1	1
=	=	=
!!LO:TX:a:t=Harmonic minor degree display:color=dodgerblue:vg=2
4c	1	1
4d	2	2
4e-	3	3
4f	4	4
4g	5	5
4a-	6	6
4bn	7	7
4bn	7h	7h
4bn	7n+	7n+
4cc	1	1
==	==	==
*-	*-	*-
</script>



