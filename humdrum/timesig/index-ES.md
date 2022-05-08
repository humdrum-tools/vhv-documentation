---
title: tutorial de codificación de compases
lang: en es
ref: humdrum-getting_started-timesig
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial time signatures
creation_date: 20 Aug 2017
translation_date: 10 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar compases en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/timesig/index-ES.html
---

<!--{% include humdrum/timesig.txt %}-->

## Compases ##

Los compases se interpretan de la forma `*MX/Y` donde `X` es el numerador del compás y `Y` es el denominador del compás:

{% include verovio.html
	humdrum-min-height="310px"
	source="time1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="time1">
**kern
*clefG2
*M4/4
*met(c)
=1
4c
4d
4e
4f
=2
*M3/2
2g
2f
2d
=
*-
</script>


### Símbolos de métrica ###

Los símbolos de compasillo y compasillo binario pueden mostrarse incluyendo una interpretación de la forma `*met(X)`, donde `X` es `c|` para el compasillo binario, o `c` para el compasillo:

{% include verovio.html
	humdrum-min-height="310px"
	source="meter1"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="meter1">
**kern
*clefG2
*M4/4
*met(c)
=1
4c
4d
4e
4f
=2
*M2/2
*met(c|)
2g
2a
=
*-
</script>

El símbolo de compás equivalente al símbolo de métrica debería seguir codificándose, normalmente inmediatamente antes del símbolo de métrica.  Prueba a eliminar las líneas del símbolo de compás del ejemplo anterior y fíjate en lo que ocurre. 

La mayoría de los signos de mensuración están disponibles también con `*met()`:

{% include verovio.html
	humdrum-min-height="310px"
	source="mensural2"
	scale="55"
	spacingNonLinear="0.4"
	spacingLinear="0.05"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="mensural2">
**kern
*clefC3
*M3/1
*met(O)
=1
1c
1d
1e
=2
*M2/1
*met(C)
1f
1e
=3
*M2/1
*met(C|)
1B
1c
=4
*M6/2
*met(C.)
2d
1e
1.f
=5
*M6/2
*met(O.)
1d
2e
2d
2c
2B
1.c
=6
*M2/1
*met(Cr)
1d
1e
=7
*M2/1
*met(O|)
1f
1e
1d
=
*-
</script>


Obsérvese que `*met(c)` se utiliza para el símbolo moderno de compasillo, y `*met(C)` se utiliza para el símbolo mensural.



