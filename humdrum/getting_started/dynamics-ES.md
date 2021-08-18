---
title: tutorial de codificación de la dinámica
lang: en es
ref: humdrum-getting_started-dynamics
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial dynamics
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar la dinámica en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/dynamics-ES.html
---

<!--{% include humdrum/dynamics.txt %}-->
## Dinámicas ##

Las dinámicas se añaden al pentagrama como una columna separada a la derecha de una columna `**kern` a la que debe asociarse la dinámica.

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

Cuando la letra esté presente, la dinámica se colocará automáticamente encima del pentagrama:

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


Ten en cuenta que el orden de las columnas `**dynam` y `**text` no importa.


