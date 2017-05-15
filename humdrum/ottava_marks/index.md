---
title: Ottava marks
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
(32GLLL
32g)
32a'
32b'JJJ
32ccLLL
32dd
32ee
32ff#JJJ
32ggLLL
32dd
32bb
32ggJJJ
*8va
32dddLLL
32bb
32ggg
32dddJJJ
32bbbLLL
32ggg
32dddd
32bbbJJJ
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
(32GLLL
32g)
32a'
32b'JJJ
32ccLLL
32dd
32ee
32ff#JJJ
32ggLLL
32dd
32bb
32ggJJJ
32dddLLL
32bb
32ggg
32dddJJJ
32bbbLLL
32ggg
32dddd
32bbbJJJ
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
	content="If you do not close the ottava mark with \"*X8va\", the notes will currently be transposed, but the mark will not be visible."
%}



