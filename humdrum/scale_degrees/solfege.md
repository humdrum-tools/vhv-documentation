
## Solf&egrave;ge display of scale degrees ##

Scale degrees can alternately be display as
chromatic movable-do solf&egrave;ge syllables
by adding the `*solf` tandem interpretation to the
`**deg` data.  Use `*Xsolf` to stop displaying as
solf&egrave;ge.

{% include verovio.html
	source="solfege"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="solfege">
**kern	**deg
*clefG2	*solf
*k[]	*
*C:	*C:
=1	=1
4c	1
4d	2
4e	3
4f	4
4g	5
4a	6
4b	7
4cc	1
=	=
*k[b-e-a-d-]	*
*A-:	*A-:
4A-	1
4B-	2
4c	3
4d-	4
4e-	5
4f	6
4g	7
4a-	1
=	=


*-	*-
</script>

Chromatic alterations with use the following system.  in C major, C is `do` while C&#x266f; `di`;
E is `mi` while E&#X266e; is `me`:


| flatter |       | sharper |
| ------: | :---: | :------ |
|         |  do   |         |
|  ra     |       |   di    |
|         |  re   |         |
|  me     |       |   ri    |
|         |  mi   |         |
|         |  fa   |         |
|  se     |       |   fi    |
|         |  so   |         |
|  le     |       |   si    |
|         |  la   |         |
|  te     |       |   li    |
|         |  ti   |         |


{% include verovio.html
	source="solfegechromatic"
	humdrum-min-height="325px"
	scale="55"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="solfegechromatic">
**kern	**deg
*clefG2	*solf
*M4/4	*
*k[]	*
*C:	*C:
=1	=1
4c	1
4d	2
4e-	3-
4f#	4+
4g##	5++
4a	6
4b--	7--
4cc-	1-
=	=
*-	*-
</script>

Note that doubly altered notes are not directly represented as well as
some singly altered  note such as `1-`, `3+`, `4-` and `7+` in a major key.





