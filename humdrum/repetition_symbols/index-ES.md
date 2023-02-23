---
title: Repetition symbols
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-repetition-symbols
keywords: humdrum repetition symbols
tags: [all, humdrum]
verovio: "true"
vim: ts=3 ft=javascript
summary: A description of how to encode repetition symbols in **kern spines.
sidebar: main_sidebar
permalink: /humdrum/repetition-symbols/index-ES.html
---

Las repeticiones se representan en `**kern` colocando las interpretaciones tándem `*rep` y `*Xrep` antes y después del grupo de notas a repetir.  Según el tipo de sustitución, el aspecto visual de la repetición se elegirá en función del contexto en el que se encuentre.


## Repeticiones a nivel de compás ##


{% include verovio.html
	source="repmeasure"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="repmeasure">
**kern
*M3/4
=1
4c
4d
4e
=2
*rep
4c
4d
4e
*Xrep
=3
4e
4d
4c
=4
*rep
4e
4d
4c
*Xrep
=5
*rep
4e
4d
4c
*Xrep
=
*-
</script>


## Repeticiones de medio compás ##

{% include verovio.html
	source="halfmeasure"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="halfmeasure">
**kern
*M4/4
=1
8cL
8dJ
16gLL
16f
16e
16dJJ
*rep
8cL
8dJ
16gLL
16f
16e
16dJJ
*Xrep
=
*rep
8cL
8dJ
16gLL
16f
16e
16dJJ
*Xrep
*rep
8cL
8dJ
16gLL
16f
16e
16dJJ
*Xrep
=
2c;
=
*-
</script>



## Repeticiones de tiempo ##

{% include verovio.html
	source="beat"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="beat">
**kern
*M4/4
=1
8cL
8dJ
*rep
8cL
8dJ
*Xrep
*rep
8cL
8dJ
*Xrep
*rep
8cL
8dJ
*Xrep
=2
8dL
8cJ
*rep
8dL
8cJ
*Xrep
8cL
8dJ
*rep
8cL
8dJ
*Xrep
=2
=
*-
</script>


El número de barras en un símbolo de repetición de tiempo está determinado por la duración de las notas individuales en la repetición:


{% include verovio.html
	source="beat2"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="beat2">
**kern
*M6/4
=1
8cL
8dJ
*rep
8cL
8dJ
*Xrep
16cLL
16d
16e
16fJJ
*rep
16cLL
16d
16e
16fJJ
*Xrep
32cLLL
32dL
32eJ
32fJJ
32gLL
32aL
32bJ
32ccJJJ
*rep
32cLLL
32d
32e
32fJJ
32gLL
32a
32b
32ccJJJ
*Xrep
=
*-
</script>


Ejemplos de repeticiones de ritmos mixtos:

{% include verovio.html
	source="mixed"
	humdrum-min-height="320px"
	scale="75"
%}
<script type="application/json" id="mixed">
**kern
*M4/4
=1
8.cL
16dJ
*rep
8.cL
16dJ
*Xrep
16eL
16d
8cJ
*rep
16eL
16d
8cJ
*Xrep
=2
1c
=
*-
</script>


## Eliminar los símbolos de repetición ##

Si deseas cambiar los estilos de visualización de los símbolos de repetición a la música completamente escrita, puedes utilizar el filtro [shed](/filter/shed) para eliminar los marcadores `*rep` antes de la impresión:


{% include verovio.html
	source="remove"
	humdrum-min-width="280px"
	scale="75"
%}
<script type="application/json" id="remove">
**kern
*M4/4
=1
16cLL
16e
16g
16eJJ
*rep
16cLL
16e
16g
16eJJ
*Xrep
*rep
16cLL
16e
16g
16eJJ
*Xrep
=
*-
</script>

{% include verovio.html
	source="remove2"
	humdrum-min-width="280px"
	scale="75"
%}
<script type="application/json" id="remove2">
!!!filter: shed -e 's/^X?rep$//I'
**kern
*M4/4
=1
16cLL
16e
16g
16eJJ
*rep
16cLL
16e
16g
16eJJ
*Xrep
*rep
16cLL
16e
16g
16eJJ
*Xrep
=
*-
</script>





## Comprobación de errores ##

Ten en cuenta que no se comprobará la exactitud de los símbolos de repetición. La música dentro de los marcadores del símbolo de repetición debe coincidir con la música que le precede y que se está repitiendo; sin embargo, si no es el caso, el símbolo de repetición se generará igualmente. 

{% include verovio.html
	source="bad"
	scale="75"
%}
<script type="application/json" id="bad">
**kern
*M4/4
=1
4c
4g
*rep
4d
4a
*Xrep
=
*-
</script>



