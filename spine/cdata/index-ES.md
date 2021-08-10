---
title: "**cdata"
lang: en es
ref: data types
author: Craig Stuart Sapp
translator: David Rizo
creation_date: 6 Sep 2019
translation_date: 10 Aug 2021
last_updated: 7 Sep 2019
vim: ft=text
verovio: "true"
tags: [all, data_type]
sidebar: main_sidebar
keywords: data types
summary: "**cdata: para la visualización de texto general como letra de la música en la notación musicaln."
permalink: /spine/cdata/index-ES.html
---

El tipo de columna `**cdata` se utiliza para mostrar datos textuales arbitrarios en notación musical como si fueran etiquetas de acordes.  El nombre es la abreviatura de "datos similares a los acordes” (o *chord-like data*).  He aquí un ejemplo básico:


{% include verovio.html
	source="example1"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="example1">
**kern	**cdata
*M4/4	*
=1	=1
4c	a
4g	b
2c	c
.	d
=	=
4e	e
4r	f
2c	g
.	h
=	=
*-	*-
</script>


## Diferencias con **vdata ##

Una columna [`**vdata`](/spine/vdata) se utiliza para mostrar texto de forma similar, pero sólo puede mostrarse debajo del pentagrama, y el texto no puede asociarse a los silencios o a las posiciones de tiempo que no tienen notas. 

{% include verovio.html
	source="both"
	humdrum-min-height="275"
	spacing-staff="0.8"
	scale="55"
	pageWidth="900"
%}
<script type="application/x-humdrum" id="both">
**kern	**vdata	**cdata
*M4/4	*	*
=1	=1	=1
4B	vdata:	cdata:
4c	a	1
2g	b	2
.	c	3
=2	=2	=2
4f	d	4
4r	e	5
4d	f	6
4c	g	7
==	==	==
*-	*-	*-
</script>


El texto `**cdata` aún no puede mostrarse debajo del pentagrama, pero debería ser posible en el futuro.

## Posicionamiento refinado ##

El texto de `**cdata` se posiciona en un momento determinado.  Normalmente este tiempo se infiere del contenido de las columnas `**kern`.  Sin embargo, si necesita posicionarse de una manera que no se puede inferir, añada una columna `**recip` a los datos.  Cada línea de la columna `**recip` especifica la duración de la línea.

Las líneas `**kern` en blanco dividen la duración de la línea anterior en partes iguales, por lo que en el siguiente ejemplo, los textos `**cdata` `b`, `d`, `f` y `h` se sitúan a mitad de camino entre las blancas (por tanto, en las posiciones de las negras):

{% include verovio.html
	source="half"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="half">
**kern	**cdata
*M4/4	*
=1	=1
2c	a
.	b
2d	c
.	d
=	=
2e	e
.	f
2c	g
.	h
=	=
*-	*-
</script>

Una codificación equivalente que utiliza una columna  `**recip`:

{% include verovio.html
	source="halfrecip"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="halfrecip">
**recip	**kern	**cdata
*	*M4/4	*
=1	=1	=1
4	2c	a
4	.	b
4	2d	c
4	.	d
=	=	=
4	2e	e
4	.	f
4	2c	g
4	.	h
=	=	=
*-	*-	*-
</script>

Si en cambio quieres retrasar el texto `b`, `d`, `f`, y `h` en una corchea, es necesario que haya tres líneas en blanco después de cada blanca para forzar que a las líneas vacías se les asigne una duración de una corchea:

{% include verovio.html
	source="eighth"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="eighth">
**kern	**cdata
*M4/4	*
=1	=1
2c	a
.	.
.	.
.	b
2d	c
.	.
.	.
.	d
=	=
2e	e
.	.
.	.
.	f
2c	g
.	.
.	.
.	h
=	=
*-	*-
</script>

Esto es algo frágil, ya que eliminar las líneas de datos nulas (con `rid -d`) haría que el espaciado volviera al nivel original de una negra.  Aquí está el mismo resultado usando una columna `**recip`:

{% include verovio.html
	source="eighthrecip"
	humdrum-min-height="275"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="eighthrecip">
**recip	**kern	**cdata
*	*M4/4	*
=1	=1	=1
4.	2c	a
8	.	b
4.	2d	c
8	.	d
=	=	=
4.	2e	e
8	.	f
4.	2c	g
8	.	h
=	=	=
*-	*-	*-
</script>


## Múltiples líneas de datos ##

Se pueden dar múltiples líneas de datos como columnas separadas `**cdata`.  Las columnas se adjuntarán al pentagrama creado por la primera columna `**kern` que se encuentre a la izquierda de las columnas `**cdata`:

{% include verovio.html
	source="multiple"
	humdrum-min-width="400"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="multiple">
**kern	**cdata	**cdata	**kern	**cdata	**cdata
*M4/4	*	*	*M4/4	*	*
=1	=1	=1	=1	=1	=1
4.B	1st:	2nd:	4.dd	1st:	2nd:
8c	a	e	8ee	1	5
4g	b	f	4dd	2	6
4d	c	g	4b	3	7
=2	=2	=2	=2	=2	=2
1f	d	h	1a	4	8
==	==	==	==	==	==
*-	*-	*-	*-	*-	*-
</script>


## Etiquetado de datos en SVG ##

El verdadero tipo de datos de `**cdata` se puede dar añadiendo un guión después de `**cdata` y luego el nombre del tipo de datos real. Esto hará que el texto en la imagen SVG renderizada de la notación se etiquete con un nombre de clase basado en el tipo de datos, y esto puede ser manipulado por CSS, como para resaltar diferentes tipos de datos de texto en colores diferentes:


{% include verovio.html
	source="label"
	humdrum-min-width="400"
	humdrum-min-height="225"
	tabsize="15"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="label">
**kern	**cdata-letter	**cdata-number
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

Si inspeccionas la imagen SVG de la notación, verás que el contenido del texto incluye etiquetas de clase basadas en el tipo de datos que se da después del guión en las columnas `**cdata`, como este código SVG para mostrar el número 3, donde hay una clase `number` añadida a la primera línea. El otro nombre de clase, `syl`, es un nombre de clase añadido por verovio para indicar que el elemento gráfico es una sílaba de texto:

```xml
<g class="harm number" id="harm-L7F3">
   <text x="3353" y="323" font-size="0px">
      <tspan class="text" id="text-0000001671342372">
         <tspan font-size="405px" class="text" x="3353" y="323">3</tspan>
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








