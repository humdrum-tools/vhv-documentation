---
title: Ottava marks
lang: en
ref: humdrum-ottava_marks
author: Craig Stuart Sapp
keywords: humdrum ottava marks
creation_date: 18 Mar 2017
last_updated: 18 Mar 2017
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode ottava marks in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/ottava_marks/index.html
---


Ottava marks can be encoded in Humdrum `**kern` data by starting the mark
with the tandem interpretation `*8va` and ending it with the interpretation
`*X8va`:

{% include verovio.html
	source="paganini15a"
	humdrum-min-height="560px"
	scale="55"
	pageWidth="1000"
%}
<script type="application/json" id="paganini15a">
**kern
*clefG2
*k[f#]
=20
(32GL
32g)
32a'
32b'J
32ccL
32dd
32ee
32ff#J
32ggL
32dd
32bb
32ggJ
*8va
32dddL
32bb
32ggg
32dddJ
32bbbL
32ggg
32dddd
32bbbJ
16gggg
*X8va
16G
=
*-
</script>


Notes under the ottava mark are encoded at *sounding pitch*,
not an octave lower as seen in the printed music.  Try removing the
`*8va`/`*X8va` tandem interpretations in the above example to display
notation like this:

{% include verovio.html
	source="paganini15b"
	humdrum-visible="false"
	scale="60"
	pageWidth="1000"
%}

<script type="application/json" id="paganini15b">
**kern
*clefG2
*k[f#]
=20
(32GL
32g)
32a'
32b'J
32ccL
32dd
32ee
32ff#J
32ggL
32dd
32bb
32ggJ
32dddL
32bb
32ggg
32dddJ
32bbbL
32ggg
32dddd
32bbbJ
16gggg
16G
=
*-
</script>


<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
{% include warning.html
	content="If you do not close the ottava mark with \"*X8va\", the notes will be transposed, but the mark will not be visible."
%}


# Ottava bassa

{% include verovio.html
	source="bassa"
	humdrum-min-height="200px"
	scale="55"
	pageWidth="1000"
%}
<script type="application/json" id="bassa">
**kern
*clefF4
4C
*8ba
4FF
4EE
4DD
4AAA
4GG
*X8ba
4C
=
*-
</script>

# Quindicesima

Two octaves up/down can also be encoded with quindicesima marks (with a perfect 15th being 
the interval of two octaves).


{% include verovio.html
	source="quin"
	humdrum-min-height="220px"
	humdrum-min-width="200px"
	scale="55"
	pageWidth="1000"
%}
<script type="application/json" id="quin">

**kern	**kern
*clefF4	*clefG2
4CCC	4ccc
*8ba	*8va
4CCC	4ccc
*X8ba	*X8va
*15ba	*15ma
4CCC	4ccc
*X15ba	*X15ma
=	=
*-	*-

</script>


