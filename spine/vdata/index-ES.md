---
title: "**vdata"
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: data types
verovio: "true"
tags: [all, data_type]
sidebar: main_sidebar
keywords: data types
summary: "**vdata: para la visualización de texto general como letra de la música en notación musical."
permalink: /spine/vdata/index.html
---

El tipo de datos `**vdata` se utiliza para mostrar datos textuales arbitrarios en notación musical como si fueran letras de la música.  El nombre es la abreviatura de "datos tipo verso” (o *verse-like data*).  He aquí un ejemplo básico:


{% include verovio.html
	source="example1"
	humdrum-min-height="375"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="example1">
**kern	**vdata
*M4/4	*
=1	=1
4c	a
4g	b
4d	c
4f	d
=2	=2
2c	e
.	f
2g	g
.	h
=3	=3
4c	i
4g	j
4r	k
4c;	l
==	==
*-	*-
</script>


Fíjate en que faltan las letras `f`, `h` y `k`, ya que el renderizador de notación, [verovio](https://www.verovio.org), no puede adjuntar letras a los silencios y no puede mostrar letras donde no hay nota (ver el tipo de datos [`**cdata`](/spine/cdata) para hacerlo).

## Diferencias con **text ##

El formato de datos [`**text`](/spine/text) se utiliza para codificar la letra de la música en sintaxis Humdrum.  Esta representación asigna espacios en el contenido de los datos a caracteres de elisión, mientras que el texto `**vdata` conserva el espacio en la notación renderizada:

{% include verovio.html
	source="space"
	humdrum-min-height="225"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="space">
**kern	**text	**vdata
*M4/4	*	*
=1	=1	=1
4B	text:	vdata:
4c	a b c	a b c
4g	d e f	d e f
4d	g h i	g h i
=2	=2	=2
1f	j k l	j k l
==	==	==
*-	*-	*-
</script>


## Múltiples líneas de datos ##

Se pueden dar múltiples líneas de datos como espinas separadas `**vdata`.  Las líneas se adjuntarán al pentagrama creado por la primera línea `**kern` que se encuentre a la izquierda de las líneas `**vdata`:

{% include verovio.html
	source="multiple"
	humdrum-min-width="400"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="multiple">

**kern	**vdata	**vdata	**kern	**vdata	**vdata
*M4/4	*	*	*M4/4	*	*
=1	=1	=1	=1	=1	=1
4B	1st:	2nd:	4dd	1st:	2nd:
4c	a	e	4ee	1	5
4g	b	f	4dd	2	6
4d	c	g	4b	3	7
=2	=2	=2	=2	=2	=2
1f	d	h	1a	4	8
==	==	==	==	==	==
*-	*-	*-	*-	*-	*-
</script>


## Etiquetado de datos SVG ##

El verdadero tipo de datos de `**vdata` se puede dar añadiendo un guión después de `**vdata` y luego el nombre del tipo de datos real. Esto hará que el texto en la imagen SVG renderizada de la notación se etiquete con un nombre de clase basado en el tipo de datos, y esto puede ser manipulado por CSS, como para resaltar diferentes tipos de datos de texto en colores diferentes:


{% include verovio.html
	source="label"
	humdrum-min-width="400"
	humdrum-min-height="225"
	tabsize="15"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="label">
**kern	**vdata-letter	**vdata-number
*M4/4	*	*
=1	=1	=1
4B	1st:	2nd:
4c	a	1
4g	b	2
4d	c	3
=2	=2	=2
1f	d	4
==	==	==
*-	*-	*-
</script>

Si inspeccionas la imagen SVG de la notación, verás que el contenido del texto incluye etiquetas de clase basadas en el tipo de datos que se da después del guión en las columnas `**vdata`, como este código SVG para mostrar el número 3, donde hay una clase `number` añadida a la primera línea. El otro nombre de clase, `syl`, es un nombre de clase añadido por verovio para indicar que el elemento gráfico es una sílaba de texto:

```xml
<g class="syl number" id="syl-L7F3">
   <text x="3403" y="2337" font-size="0px">
      <tspan class="text" id="text-0000000746016912">
         <tspan font-size="405px" class="text">&nbsp;3</tspan>
      </tspan>
   </text>
</g>
```


El coloreado del texto y los cambios de fuente se hacen con el siguiente código CSS:


```css
svg .letter {
	fill: chartreuse;
  	text-shadow: 0px 0px 10px orange;
}

svg .number {
	fill: hotpink;
	font-family: Helvetica;
	font-weight: bold;
}
```


<style>
svg .letter {
	fill: chartreuse;
  	text-shadow: 0px 0px 10px orange;

}
svg .number {
	fill: hotpink;
	font-family: Helvetica;
	font-weight: bold;
}
</style>








