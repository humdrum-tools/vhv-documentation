---
title: modori filter
lang: en
ref: filters-modori
author: Craig Stuart Sapp
translator:
creation_date: 30 May 2021
translation_date:
last_updated: 17 Apr 2022
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands
summary:
permalink: /filter/modori/index.html
---

The modori ("MODern/ORIginal") filter allows encoding both a "modern"
and "original" edition in the same Humdrum file.  The filter can
reversibly switch between these two views of the score by using
either the `-m` or `-o` option.  On a diplomatically-encoded score
modori features, running `modori -m` will generate the "modern"
view of a score.  And `modori -o` will recover the "original"
diplomatic score.



<h2> Options </h2>

{% include filter-options.html file="options.aton" lang="EN" %}


<h2> Clefs </h2>

Clef interpretations such as `*clefG2` can be additionally encoded
as `*mclefG2` and `*oclefG2`:  prefixing by `m` indicates a "modern"
clef and prefixing by `o` for an "original" clef.

To use the modori filter to encode a diplomatic score, encode
the visual clef with `*clef` and the modernized clef with `*mclef`:


{% include verovio.html
	source="clef"
	scale="60"
	pageWidth="500"
	humdrum-min-height="140px"
%}
<script type="text/x-humdrum" id="clef">
**kern
*clefC3
*mclefG2
=
1c
=
*-
</script>

Then the filter `modori -m` will instead display the modern clef:

{% include verovio.html
	source="mclef"
	scale="60"
	pageWidth="500"
	humdrum-min-height="140px"
%}
<script type="text/x-humdrum" id="mclef">
!!!filter: modori -m
**kern
*clefC3
*mclefG2
=
1c
=
*-
</script>

The result of the filter will change
`*clef` to `*oclef` and `*mclef` to `*clef`:

{% include verovio.html
	source="oclef"
	scale="60"
	pageWidth="500"
	humdrum-min-height="140px"
%}
<script type="text/x-humdrum" id="oclef">
!!!Xfilter: modori -m
**kern
*oclefC3
*clefG2
=
1c
=
*-
</script>

If there are no `*mclef` or `oclef` that can pair with the `*clef`, 
then the clef will not be changed:

{% include verovio.html
	source="singleclef"
	scale="60"
	pageWidth="500"
	humdrum-min-height="140px"
%}
<script type="text/x-humdrum" id="singleclef">
**kern
*clefC3
=
1c
=
*-
</script>

{% include verovio.html
	source="singleclef2"
	scale="60"
	pageWidth="500"
	humdrum-min-height="140px"
%}
<script type="text/x-humdrum" id="singleclef2">
!!!filter: modori -m
**kern
*clefC3
=
1c
=
*-
</script>



<h2> Key signatures </h2>

Similar to clefs, `m` and `o` prefixes for key signatures can be
used to select between modern and original key signatures.


{% include verovio.html
	source="key"
	scale="60"
	pageWidth="500"
	humdrum-min-height="250px"
%}
<script type="text/x-humdrum" id="key">
**kern
*clefC3
*mclefG2
*k[b-]
*mk[b-e-]
=
4B-
4c
4d
4e-
=
*-
</script>


Switching to the modern score:


{% include verovio.html
	source="mkey"
	scale="60"
	pageWidth="500"
	humdrum-min-height="250px"
%}
<script type="text/x-humdrum" id="mkey">
!!!filter: modori -m
**kern
*clefC3
*mclefG2
*k[b-]
*mk[b-e-]
=
4B-
4c
4d
4e-
=
*-
</script>

This will create the "modern" view of the score:

{% include verovio.html
	source="modkey"
	scale="60"
	humdrum-min-height="250px"
	pageWidth="500"
%}
<script type="text/x-humdrum" id="modkey">
**kern
*oclefC3
*clefG2
*ok[b-]
*k[b-e-]
=
4B-
4c
4d
4e-
=
*-
</script>

Which can be reverted to the "original" score with the `modori -o` filter:

{% include verovio.html
	source="orikey"
	scale="60"
	humdrum-min-height="250px"
	pageWidth="500"
%}
<script type="text/x-humdrum" id="orikey">
!!!filter: modori -o
**kern
*oclefC3
*clefG2
*ok[b-]
*k[b-e-]
=
4B-
4c
4d
4e-
=
*-
</script>


<h2> Mensuration signs / Time signatures </h2>

When encoding mensuration signs, a time signature is also 
required.  Running `modori -m` will change the mensuration sign
from `*met` to `*omet`:

{% include verovio.html
	source="mensuration"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="250px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="mensuration">
**kern
*clefC3
*mclefG2
*M2/1
*met(C|)
=
1c
1d
=
0c
=
*-
</script>

{% include verovio.html
	source="mensuration2"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="250px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="mensuration2">
!!!filter: modori -m
**kern
*clefC3
*mclefG2
*M2/1
*met(C|)
=
1c
1d
=
0c
=
*-
</script>

<h2> OMD reference records </h2>

OMD records can be encoded for modern/original displays:


{% include verovio.html
	source="omd"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="250px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="omd">
!!!OMD: Allo.
!!!OMD-mod: Allegro
**kern
*clefC3
*mclefG2
*M4/4
=
1c
=
1d
=
1e
==
*-
</script>

{% include verovio.html
	source="omd2"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="300px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="omd2">
!!!filter: modori -m
!!!OMD: Allo.
!!!OMD-mod: Allegro
**kern
*clefC3
*mclefG2
*M4/4
=
1c
=
1d
=
1e
==
*-
</script>



<h2> Non-staff spines </h2>

An entire spine can be labeled as "modern" or "original".  Here
is an example of encoding two different lyrical text spines, with
the modern version hidden in the diplomatic version:


{% include verovio.html
	source="text"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.2"
	humdrum-min-height="300px"
	humdrum-min-width="300px"
	pageWidth="800"
	tabsize="12"
%}
<script type="text/x-humdrum" id="text">
**kern	**text	**mod-text
*clefC3	*	*
*mclefG2	*	*
*M4/4	*	*
=	=	=
4e	Ma-	Ma-
4d	-rie	-ry
4c	hadst	had
4d	a	a
=	=	=
4e	lit-	lit-
4e	-tleth	-tle
2e	lamb.	lamb.
=	=	=
*-	*-	*-
</script>



{% include verovio.html
	source="textmodern"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="310px"
	humdrum-min-width="300px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="textmodern">
!!!filter: modori -m
**kern	**text	**mod-text
*clefC3	*	*
*mclefG2	*	*
*M4/4	*	*
=	=	=
4e	Ma-	Ma-
4d	-rie	-ry
4c	hadst	had
4d	a	a
=	=	=
4e	lit-	lit-
4e	-tleth	-tle
2e	lamb.	lamb.
=	=	=
*-	*-	*-
</script>

Here is the view after compiling with
the `modori -m` filter:

{% include verovio.html
	source="textmodern2"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="310px"
	humdrum-min-width="300px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="textmodern2">
**kern	**ori-text	**text
*clefC3	*	*
*mclefG2	*	*
*M4/4	*	*
=	=	=
4e	Ma-	Ma-
4d	-rie	-ry
4c	hadst	had
4d	a	a
=	=	=
4e	lit-	lit-
4e	-tleth	-tle
2e	lamb.	lamb.
=	=	=
*-	*-	*-
</script>

This form of the score can be reverted to the original form again by
running the `modori -o` filter:

{% include verovio.html
	source="textmodern3"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="310px"
	humdrum-min-width="275px"
	pageWidth="800"
	tabsize="12"
%}
<script type="text/x-humdrum" id="textmodern3">
!!!filter: modori -o
**kern	**ori-text	**text
*clefC3	*	*
*mclefG2	*	*
*M4/4	*	*
=	=	=
4e	Ma-	Ma-
4d	-rie	-ry
4c	hadst	had
4d	a	a
=	=	=
4e	lit-	lit-
4e	-tleth	-tle
2e	lamb.	lamb.
=	=	=
*-	*-	*-
</script>


To view both versions of the lyrics at the same time, use the
[shed](/filter/shed) filter:

{% include verovio.html
	source="bothtext"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="325px"
	humdrum-min-width="325px"
	pageWidth="800"
	tabsize="12"
%}
<script type="text/x-humdrum" id="bothtext">
!!!filter: modori -m 
!!!filter: shed -e s/^ori-text$/text/X
**kern	**text	**mod-text
*clefC3	*	*
*mclefG2	*	*
*M4/4	*	*
=	=	=
4e	Ma-	Ma-
4d	-rie	-ry
4c	hadst	had
4d	a	a
=	=	=
4e	lit-	lit-
4e	-tleth	-tle
2e	lamb.	lamb.
=	=	=
*-	*-	*-
</script>

When a particular staff does not have separate modern/original text
variants, use `**text`, which will not be altered by the modori
filter, since there will not be any matching `**mod-text` or `**ori-text`:

{% include verovio.html
	source="bothtext2"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="350px"
	humdrum-min-width="350px"
	pageWidth="800"
	tabsize="12"
%}
<script type="text/x-humdrum" id="bothtext2">
!!!filter: modori -m 
**kern	**text	**kern	**text	**mod-text
*clefF4	*	*clefC3	*	*
*mclefF4	*	*mclefG2	*	*
*M4/4	*	*M4/4	*	*
=	=	=	=	=
2C	Do	4e	Ma-	Ma-
.	.	4d	-rie	-ry
2G	wa	4c	hadst	had
.	.	4d	a	a
=	=	=	=	=
2G	do	4e	lit-	lit-
.	.	4e	-tleth	-tle
2C	wa	2e	lamb.	lamb.
=	=	=	=	=
*-	*-	*-	*-	*-
!!!system-decoration: [s1,s2]
</script>

More than one verse can be added to a given staff, but in that case,
all of the spines must be pair with a modern/original equivalent.

Any other non-staff type of spine can also use this sytem such as
`**dynam` (using `**mod-dynam` or `**ori-dynam`).


<h2> Staff-like spines </h2>

Staff-like spines, such as `**kern` and `**mens` are treated
slightly different than non-staff types of spines.  The display
form of `**kern` spines is either `**kern-ori` or `**kern-mod`, and
the alternate would be either `**ori-kern` or `**mod-kern`:


{% include verovio.html
	source="menskern"
	scale="60"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="menskern">
**mens-ori	**mod-kern	**text	**mod-text
*clefC3	*clefG2	*	*
=	=	=	=
me	4e	Ma-	Ma-
md	4d	-rie	-ry
mc	4c	hadst	had
md	4d	a	a
=	=	=	=
me	4e	lit-	lit-
me	4e	-tleth	-tle
Me	2e	lamb.	lamb.
=	=	=	=
*-	*-	*-	*-
</script>

{% include verovio.html
	source="menskern2"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="menskern2">
!!!filter: modori -m
**mens-ori	**mod-kern	**text	**mod-text
*clefC3	*clefG2	*	*
=	=	=	=
me	4e	Ma-	Ma-
md	4d	-rie	-ry
mc	4c	hadst	had
md	4d	a	a
=	=	=	=
me	4e	lit-	lit-
me	4e	-tleth	-tle
Me	2e	lamb.	lamb.
=	=	=	=
*-	*-	*-	*-
</script>

Here is the result after compiling the `modori -m` filter:

{% include verovio.html
	source="menskern3"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="menskern3">
!!!Xfilter: modori -m
**ori-mens	**kern-mod	**ori-text	**text
*clefC3	*clefG2	*	*
=	=	=	=
me	4e	Ma-	Ma-
md	4d	-rie	-ry
mc	4c	hadst	had
md	4d	a	a
=	=	=	=
me	4e	lit-	lit-
me	4e	-tleth	-tle
Me	2e	lamb.	lamb.
=	=	=	=
*-	*-	*-	*-
</script>


<h2> LO:MO layout parameters </h2>

Individual tokens can be swapped between original and modern
variants.  

{% include verovio.html
	source="lomo"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="325px"
	humdrum-min-width="250px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="lomo">
**kern	**text
*clefG2	*
=	=
4e	Ma-
!	!LO:MO:mod=-ry
4d	-rie
!	!LO:MO:mod=had
4c	hadst
4d	a
=	=
4e	lit-
!	!LO:MO:mod=-tle
4e	-tleth
2e	lamb.
=	=
*-	*-
</script>

Applying `modori -m`:

{% include verovio.html
	source="lomo2"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="325px"
	humdrum-min-width="250px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="lomo2">
!!!filter: modori -m
**kern	**text
*clefG2	*
=	=
4e	Ma-
!	!LO:MO:mod=-ry
4d	-rie
!	!LO:MO:mod=had
4c	hadst
4d	a
=	=
4e	lit-
!	!LO:MO:mod=-tle
4e	-tleth
2e	lamb.
=	=
*-	*-
</script>

Compiling the modori filter:

{% include verovio.html
	source="lomo3"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="325px"
	humdrum-min-width="250px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="lomo3">
!!!Xfilter: modori -m
**kern	**text
*clefG2	*
=	=
4e	Ma-
!	!LO:MO:ori=-rie
4d	-ry
!	!LO:MO:ori=hadst
4c	had
4d	a
=	=
4e	lit-
!	!LO:MO:ori=-tleth
4e	-tle
2e	lamb.
=	=
*-	*-
</script>


For scribal errors, the LO:MO system can be used, although it is
better to use [sic](/filter/sic) to allow corrections to be applied
to both the diplomatic or modern editions.

<h3> Interpretations </h3>

Interpretations for modern/original displays can be switched with the
modori filter.  Here is an example of changing the stem styling on 
half notes:


{% include verovio.html
	source="interp"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="325px"
	humdrum-min-width="250px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="interp">
**kern
*clefG2
*M4/4
!LO:MO:mod=*dummy"
*2\right
=
2cc
2ff
=
2gg
2ee
==
*-
</script>

The interpretation `*2\right` will be switched to `*blank` when the `modori -m` 
filter is used to display the modern score:

{% include verovio.html
	source="interp"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="325px"
	humdrum-min-width="250px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="interp">
!!!filter: modori -m
**kern
*clefG2
*M4/4
!LO:MO:mod=*dummy"
*2\right
=
2cc
2ff
=
2gg
2ee
==
*-
</script>

The `*dummy` interpretation has no meaning, and is used as a placeholder
so that the original interpretation can be restored with `modori -o`.
Here is the compiled result of the filter:

{% include verovio.html
	source="interp2"
	scale="60"
	spacingNonLinear="0.4"
	spacingLinear="0.3"
	humdrum-min-height="325px"
	humdrum-min-width="250px"
	pageWidth="700"
	tabsize="12"
%}
<script type="text/x-humdrum" id="interp2">
!!!Xfilter: modori -m
**kern
*clefG2
*M4/4
!LO:MO:ori=*2\right"
*dummy
=
2cc
2ff
=
2gg
2ee
==
*-
</script>

Note that null interpretations cannot be used, which is why `*dummy` is 
used in this example.


<h2> LO:TX / LO:DY </h2>

LO:TX and LO:DY parameters allow modern/original text to be swapped out with the `modori` 
filter.  Both of these LO parameters can have an added `mod` or `ori` parameter to store
the modern or original text that should be alternated with the `t` text parameter.

<h3> LO:TX example </h3>

{% include verovio.html
	source="lotx"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="250px"
	humdrum-min-width="350px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="lotx">
**kern
*clefC3
*mclefG2
*M4/4
=
!LO:TX:i:a:t=original text:mod=modern text
1c
=
1d
=
1e
==
*-
</script>

{% include verovio.html
	source="lotx"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="250px"
	humdrum-min-width="350px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="lotx">
!!!filter: modori -m
**kern
*clefC3
*mclefG2
*M4/4
=
!LO:TX:i:a:t=original text:mod=modern text
1c
=
1d
=
1e
==
*-
</script>

Applying `modori -m` to display the modern score:

{% include verovio.html
	source="lotx2"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="375px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="lotx2">
!!!filter: modori -m
**kern
*clefC3
*mclefG2
*M4/4
=
!LO:TX:i:a:t=original text:mod=modern text
1c
=
1d
=
1e
==
*-
</script>

After compiling the modori filter:

{% include verovio.html
	source="lotx3"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="350px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="lotx3">
!!!Xfilter: modori -m
**kern
*clefC3
*mclefG2
*M4/4
=
!LO:TX:i:a:ori=original text:t=modern text
1c
=
1d
=
1e
==
*-
</script>

<h3> LO:DY example </h3>

{% include verovio.html
	source="lody"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="250px"
	humdrum-min-width="350px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="lody">
**kern	**dynam
*clefC3	*
*mclefG2	*
*M4/4	*
=	=
!	!LO:DY:t=pia:mod=%s
1c	p
=	=
1d	.
=	=
1e	.
==	==
*-	*-
</script>

Applying `modori -m`:

{% include verovio.html
	source="lody2"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="250px"
	humdrum-min-width="350px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="lody2">
!!!filter: modori -m
**kern	**dynam
*clefC3	*
*mclefG2	*
*M4/4	*
=	=
!	!LO:DY:t=pia:mod=%s
1c	p
=	=
1d	.
=	=
1e	.
==	==
*-	*-
</script>

After compiling the filter:

{% include verovio.html
	source="lody3"
	scale="60"
	spacingNonLinear="0.55"
	spacingLinear="0.2"
	humdrum-min-height="275px"
	humdrum-min-width="350px"
	pageWidth="700"
%}
<script type="text/x-humdrum" id="lody3">
!!!Xfilter: modori -m
**kern	**dynam
*oclefC3	*
*clefG2	*
*M4/4	*
=	=
!	!LO:DY:ori=pia:t=%s
1c	p
=	=
1d	.
=	=
1e	.
==	==
*-	*-
</script>


