---
title: Marcas de transposición de octava
lang: en es
ref: humdrum-ottava_marks
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum ottava marks
creation_date: 18 Mar 2017
translation_date: 10 Aug 2021
last_updated: 18 Mar 2017
tags: [all, humdrum ]
verovio: "true"
vim: ts=3 ft=javascript
summary: "Una descripción de cómo codificar las marcas de la transposición de octava en las columnas de **kern"
sidebar: main_sidebar
permalink: /humdrum/ottava_marks/index-ES.html
---


Las marcas de transposición de octava pueden codificarse en los datos de Humdrum `**kern` comenzando la marca con la interpretación tándem `*8va` y terminándola con la interpretación `*X8va`:

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

Las notas bajo la marca de octava se codifican en la *afinación sonora*, no una octava más baja como se ve en la música impresa.  Intenta eliminar las interpretaciones tándem `*8va`/`*X8va` en el ejemplo anterior para mostrar una notación como ésta:

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
	content="Si no cierra la marca de transposición de octava con \"*X8va\", las notas se transpondrán, pero la marca no será visible."
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

Dos octavas arriba/abajo también pueden codificarse con marcas de quindicesima (siendo una 15ª perfecta el intervalo de dos octavas).


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


