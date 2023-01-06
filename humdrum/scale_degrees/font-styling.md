

## Font styling ##

There are several font-styling interpretations that are described in this section.



### Font size ###

The font size of scale degrees can be set by the `*fs:` interpretation followed by a font size, such as `*fs:80%`:


{% include verovio.html
	source="sizefont"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="sizefont">
**kern	**deg	**deg	**deg	**deg
*clefG2	*	*fs:75%	*fs:120%	*fs:100%
*M4/4	*	*circle	*	*box
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

In addition to percentages, there are several symbolic font sizes that can be used:


| fontsize   | percentage |
| ---        | ---        |
| `smallest` |  60%       |
| `smaller`  |  75%       |
| `small`    |  89%       |
| `normal`   | 100%       |
| `large`    | 120%       |
| `larger`  | 150%       |
| `largest`  | 200%       |


{% include verovio.html
	source="symsize"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="symsize">
**kern	**deg	**deg	**deg
*clefG2	*fs:normal	*fs:smallest	*fs:largest
*M4/4	*	*circle	*box
*k[]	*	*	*
*C:	*C:	*C:	*C:
=1	=1	=1	=1
4c	1	1	1
4d	2	2	2
*	*	*fs:smallest	*fs:largest
4e	3	3	3
4f	4	4	4
*	*	*fs:smaller	*fs:larger
4g	5	5	5
4a	6	6	6
*	*	*fs:small	*fs:large
4b	7	7	7
4cc	1	1	1
=	=	=	=
*-	*-	*-	*-
</script>



### Font style ###

Scale degrees can be displayed in italic and/or bold:

{% include verovio.html
	source="style"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="style">
**kern	**deg	**deg	**deg	**deg
*clefG2	*	*italic	*bold	*italic
*M4/4	*	*	*	*bold
*k[]	*	*	*	*
*C:	*C:	*C:	*C:	*C:
=1	=1	=1	=1	=1
4c	1	1	1	1
4d	2	2	2	2
4e	3	3	3	3
4f	4	4	4	4
4g	5	5	5	5
*	*italic	*	*	*
*	*bold	*	*	*
*	*circle	*	*	*
4a	6	6	6	6
*	*Xitalic	*	*	*
*	*Xbold	*	*	*
*	*Xcircle	*	*	*
4b	7	7	7	7
4cc	1	1	1	1
=	=	=	=	=
*-	*-	*-	*-	*-
</script>



### Font color ###


{% include verovio.html
	source="color"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="color">
**kern	**deg	**deg	**deg	**deg
*clefG2	*	*color:crimson	*color:#00f2	*color:hsl(180,100%,25%)
*M4/4	*	*	*	*bold
*k[]	*	*	*	*
*C:	*C:	*C:	*C:	*C:
=1	=1	=1	=1	=1
4c	1	1	1	1
4d	2	2	2	2
4e	3	3	3	3
4f	4	4	4	4
*	*bold	*	*	*
*	*color:limegreen	*	*	*
4g	5	5	5	5
4a	6	6	6	6
4b	7	7	7	7
4cc	1	1	1	1
=	=	=	=	=
*-	*-	*-	*-	*-
</script>
