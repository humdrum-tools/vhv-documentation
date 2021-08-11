---
title: Ligature y corchetes de coloración
lang: en es
ref: humdrum-ligatures
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum ligature coloration
creation_date: 18 Mar 2018
translation_date: 10 Aug 2021
last_updated: 18 Mar 2018
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: Una descripción de cómo codificar los corchetes de ligature en las columnas de **kern.
sidebar: main_sidebar
permalink: /humdrum/ligatures/index-ES.html
---

Las ligaduras son secuencias de notas unidas entre sí en la música mensural.  Cuando se escribe la música en notación moderna, normalmente se coloca un corchete sobre las notas separadas para indicar que el grupo de notas se anotó originalmente en una ligadura.

Utilice `*lig` para iniciar un corchete de ligadura, y `*Xlig` para terminar un corchete de ligadura en los datos de **kern:


{% include verovio.html
	source="ligature2"
	humdrum-min-height="400px"
	spacingNonLinear="0.55"
	spacingLinear="0.20"
	scale="55"
	url="https://digi.vatlib.it/view/MSS_Chig.C.VIII.234"
%}
<script type="application/json" id="ligature2">
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


## Corchetes de coloración ##

Los corchetes de coloración pueden mostrarse utilizando `*col` y `*Xcol` para marcar el comienzo y el final de la coloración en una notación mensural original de la partitura.  A continuación se muestra un extracto de notación mensural de la Missa Ecce ancilla domini de Ockeghem, parte de tenor:

{% include image.html
	file="chigcvii8234-tenor.jpg"
	alt="Ockghem coloration example"
	caption="Ockeghem: Missa Ecce ancilla domini, Kyrie, Tenor part opening."
%}

Las notas negras están coloreadas, por lo que se marcan con corchetes abiertos en la notación moderna equivalente a continuación.


{% include verovio.html
	source="coloration2"
	humdrum-min-height="575px"
	spacingNonLinear="0.5"
	spacingLinear="0.1"
	scale="55"
%}
<script type="application/json" id="coloration2">
**kern
*clefC4
*M3/1
*met(O)
=9
[0.d
=
0.d]
=
*col
1c
1B
[1d
=
1d]
0d
*Xcol
=
1e
2d
2B
1c
=
1d
0d
=
[0.G
=
0.G]
=
*-
</script>

