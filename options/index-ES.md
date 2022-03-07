---
title: Embedded verovio options
lang: en es
ref: verovio options
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 20 Mar 2019
translation_date: 9 Aug 2021
last_updated: 20 Mar 2019
tags: [all, options]
sidebar: main_sidebar
verovio: "true"
keywords: embedded verovio options
summary: 
permalink: /options/index-ES.html
---
Las opciones de verovio pueden ser incrustadas directamente en los datos de Humdrum.  Cuando los datos son procesados por Verovio, las opciones se utilizarán para controlar la representación de la notación musical.

El formato básico de una opción incrustada es

```
!!!verovio: spacingStaff 0
```

La línea comienza con `!!!verovio:` seguido de un nombre de opción verovio en camelCase (tal y como se utiliza en la versión Javascript de Verovio), seguido de al menos un espacio y a continuación el valor de esa opción.  Se pueden dar múltiples opciones en el archivo, con una opción en cada línea.  En el caso anterior, el espaciado entre pentagramas se establece en 0. Compara el siguiente ejemplo que utiliza el espaciado entre pentagramas por defecto:


{% include verovio.html
	source="spacing-default"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-min-height="470px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-default">
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>

Añadir una opción para ampliar el espacio entre pentagramas:

{% include verovio.html
	source="spacing-wide"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-wide">
!!!verovio: spacingStaff 18
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>

Vea la [lista completa](/options/list) de las opciones de Verovio que se pueden incrustar junto con sus valores por defecto y los rangos permitidos para las opciones numéricas.

Las opciones pueden aparecer en cualquier lugar del fichero.  Las opciones duplicadas dan prioridad a la última ocurrencia en el archivo.  En el caso de los grupos de parámetros de opciones, los grupos se procesarán en el orden en que aparecen en el archivo (probablemente).

## Conjuntos de opciones ##

Se pueden incrustar varios grupos de opciones en un archivo.  Por ejemplo, aquí hay dos grupos de opciones para el espaciado del personal:

```
!!!verovio-compact: spacingStaff 0
!!!verovio-spacious: spacingStaff 20
```

Para activar un grupo de opciones concreto, añade una línea como la siguiente al archivo:

```
!!!verovio-parameter-group: spacious
```

Esto hará que se utilice el grupo de opciones "espacioso", mientras que todos los demás grupos serán ignorados:


{% include verovio.html
	source="spacing-group"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group">
!!!verovio-compact: spacingStaff 0
!!!verovio-compact: leftMarginClef 0.00
!!!verovio-spacious: spacingStaff 20
!!!verovio-spacious: leftMarginClef 2.00
!!!verovio-parameter-group: spacious
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>

Ahora eligiendo el grupo de parámetros "compacto":

{% include verovio.html
	source="spacing-group2"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group2">
!!!verovio-compact: spacingStaff 0
!!!verovio-compact: leftMarginClef 0.00
!!!verovio-spacious: spacingStaff 20
!!!verovio-spacious: leftMarginClef 2.00
!!!verovio-parameter-group: compact
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>

Ten en cuenta que los parámetros de Verovio incrustados que no pertenezcan a un grupo específico estarán siempre activos.  Para utilizar dichos parámetros como valores por defecto para un parámetro, colócalos por encima de cualquier equivalente de grupo.  Si se colocan después, sustituirán a los parámetros de grupo.


{% include verovio.html
	source="spacing-group3"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group3">
!!!verovio-compact: spacingStaff 0
!!!verovio-spacious: spacingStaff 20
!!!verovio-parameter-group: spacious
!!!verovio: spacingStaff 0
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>


Aquí está el uso correcto de los parámetros por defecto, permitiendo que el grupo de parámetros "espacioso" lo sobreescriba:

{% include verovio.html
	source="spacing-group4"
	scale="55"
	tabsize="10"
	pageWidth="1400"
	humdrum-max-height="490px"
	humdrum-min-height="490px"
	humdrum-min-width="330px"
%}
<script type="application/x-humdrum" id="spacing-group4">
!!!verovio: spacingStaff 0
!!!verovio-compact: spacingStaff 0
!!!verovio-spacious: spacingStaff 20
!!!verovio-parameter-group: spacious
**kern	**kern	**kern	**kern
*ICvox	*ICvox	*ICvox	*ICvox
*Ibass	*Itenor	*Ialto	*Isoprn
*I"Bass	*I"Tenor	*I"Alto	*I"Soprano
*clefF4	*clefGv2	*clefG2	*clefG2
*k[f#]	*k[f#]	*k[f#]	*k[f#]
*M4/4	*M4/4	*M4/4	*M4/4
*met(c)	*met(c)	*met(c)	*met(c)
4G	4B	4g	4dd
=1	=1	=1	=1
4C	8cL	4g	4ee
.	8BJ	.	.
4D	4A	4f#	8ddL
.	.	.	8ccJ
4E	4G	4g	8bL
.	.	.	8ccJ
8BBL	4G	8dL	4dd
8CJ	.	8eJ	.
=2	=2	=2	=2
2D;	2d;	2f#;	2a;
8GL	4d	4g	4b
8F#J	.	.	.
4E	4G	4g	4cc#
=	=	=	=
*-	*-	*-	*-
</script>




