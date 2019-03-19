---
title: Ligatures
lang: en
ref: humdrum-ligatures
author: Craig Stuart Sapp
translator: 
keywords: humdrum tremolo
creation_date: 18 Mar 2018
translation_date: 
last_updated: 18 Mar 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode ligature brackets in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/ligatures/index.html
---

Ligature are are sequences of notes attached to each other
in mensural music.  When notating the music in modern notation,
typically a bracket will be placed over the separated notes to
indicate that the group of notes were originally notated in a
ligature.

Use `*lig` to start a ligature bracket, and `*Xlig` to end a
ligature bracket in **kern data:


{% include verovio.html
	source="tremolo"
	humdrum-min-height="400px"
	scale="55"
%}
<script type="application/json" id="tremolo">
**kern
*clefC3
*M2/1
*met(C|)
=
*lig
1d
1B
=
0c
=
0d
*Xlig
=
2e
2d
1B
=
0c
=
*-
</script>

