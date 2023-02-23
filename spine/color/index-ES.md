---
title: "**color"
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
summary: "**color: para colorear notas"
permalink: /spine/color/index-ES.html
---

El tipo de datos `**color` se utiliza para establecer el color de las notas en la notación musical.



{% include verovio.html
	source="example1"
	humdrum-min-height="375"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="example1">
**kern	**color
*M4/4	*
=1	=1
4c	hotpink
4g	.
4d	chartreuse
4f	.
=2	=2
2c	black
.	.
2g	.
.	.
=3	=3
4c	#9900bb44
4g	.
4r	hsl(184,49%,61%)
4c;	.
==	==
*-	*-
</script>

Prueba a cambiar los nombres de los colores en el cuadro de texto anterior.  Se puede utilizar cualquier CSS/SVG <a target="_blank" href="https://www.w3.org/TR/2018/REC-css-color-3-20180619/#svg-color">nombre de color o números</a>.


Una columna separada de `**color` a la derecha de cada columna de `**kern` controlará los colores de las notas en el pentagrama generado por la columna de `**kern`:


{% include verovio.html
	source="example2"
	humdrum-max-height="375"
	humdrum-min-width="425"
	scale="55"
	tabsize="12"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="example2">
**kern	**color	**kern	**color
*	*	*M4/4	*
=1	=1	=1	=1
2E	chartreuse	4c	hotpink
.	.	4g	.
2AA	hotpink	4d	chartreuse
.	.	4f	.
=2	=2	=2	=2
4E	#f00	2c	black
4GG	.	.	.
4BB	lightblue	2g	.
4D	.	.	.
=3	=3	=3	=3
1E	orange	4c	#9900bb44
.	.	4g	.
.	.	4r	hsl(184,49%,61%)
.	.	4c;	.
==	==	==	==
*-	*-	*-	*-
</script>


Si no hay una columna "color" asociada a cada columna "kern", se utilizará la columna `**color` más cercana a la derecha para colorear las notas de cada pentagrama.  He aquí un ejemplo de columna `**color` que controla el color de las notas en dos pentagramas:


{% include verovio.html
	source="example3"
	humdrum-max-height="375"
	humdrum-min-width="350"
	scale="55"
	tabsize="12"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="example3">
**kern	**kern	**color
*	*M4/4	*
=1	=1	=1
2E	4c	hotpink
.	4g	.
2AA	4d	chartreuse
.	4f	.
=2	=2	=2
4E	2c	black
4GG	.	.
4BB	2g	.
4D	.	.
=3	=3	=3
1E	4c	#9900bb44
.	4g	.
.	4r	hsl(184,49%,61%)
.	4c;	.
==	==	==
*-	*-	*-
</script>


## Colorear mediante la interpretación tándem ##

También es posible colorear notas con interpretaciones tándem:


{% include verovio.html
	source="tandem"
	humdrum-min-height="425"
	humdrum-min-width="250"
	scale="55"
	tabsize="12"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="tandem">
**kern
*M4/4
=1
*color:hotpink
4c
4g
*color:chartreuse
4d
4f
=2
*color:black
2c
2g
=3
*color:#9900bb44
4c
4g
*color:hsl(184,49%,61%)
4r
4c;
==
*-
</script>


## Colorear con marcador RDF ##

Un método sencillo para colorear las notas es añadir un marcador de notas RDF:

{% include verovio.html
	source="rdf"
	humdrum-min-height="400"
	humdrum-min-width="400"
	scale="55"
	tabsize="12"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="rdf">
**kern
*M4/4
=1
4c
4g@
4dN
4fZ
=2
2cZ
2g
=3
4cN
4gN
4r@
4c;
==
*-
!!!RDF**kern: @ = marked note
!!!RDF**kern: N = marked note, color=chartreuse
!!!RDF**kern: Z = marked note, color="#ccaa11"
</script>

El color por defecto de una nota marcada es el rojo.  Si añade un color SVG en la línea RDF, elegirá otro color de resaltado.



## Colorear con CSS ##

Al descargar una imagen SVG creada en VHV, puedes aplicar estilos CSS al SVG para colorear las notas con CSS en tu propia página web:

{% include verovio.html
	source="example"
	humdrum-min-height="275"
	scale="55"
	tabsize="12"
	pageWidth="500"
%}
<script type="application/x-humdrum" id="example">
**kern
*M4/4
=1
4c
4d
4e
4f
=2
4g
4a
4b
4cc
==
*-
</script>

<style>
	#example-svg g.note.pname-c { fill: red }
	#example-svg g.note.pname-d { fill: orange }
	#example-svg g.note.pname-e { fill: gold }
	#example-svg g.note.pname-f { fill: green }
	#example-svg g.note.pname-g { fill: lightblue }
	#example-svg g.note.pname-a { fill: blue }
	#example-svg g.note.pname-b { fill: violet }
</style>

Aquí están las instrucciones CSS para colorear la música anterior:

```css
#example-svg g.note.pname-c { fill: red }
#example-svg g.note.pname-d { fill: orange }
#example-svg g.note.pname-e { fill: gold }
#example-svg g.note.pname-f { fill: green }
#example-svg g.note.pname-g { fill: lightblue }
#example-svg g.note.pname-a { fill: blue }
#example-svg g.note.pname-b { fill: violet }
```

Cada nota SVG tiene información de tono incrustada en el atributo de clase de la nota:

```xml
<g class="note qon-0 qoff-1 pname-c acc-n oct-4 b40c-2 b12c-0 " id="note-L4F1">
	<use xlink:href="#E0A4" x="1398" y="1620" height="720px" width="720px"></use>
	<g class="stem" id="stem-0000001056906808">
		<rect x="1606" y="990" height="608" width="18"></rect>
	</g>
	<g class="accid" id="accid-0000001520787168"></g>
</g>
```

La lista de clases `note qon-0 qoff-1 pname-c acc-n oct-4 b40c-2 b12c-0` contiene varios tipos de información sobre la nota:

Parámetro | valor | significado
==========|=======|========
qon       | 0     | El tiempo de inicio de la nota
qoff      | 1     | El tiempo final de la nota
pname     | c     | El nombre de clase de tono de la nota
acc       | n     | La alteración de la nota
oct       | 4     | La octava de la nota
b40c      | 2     | El nombre de clase de tono base-40 de la nota
b12c      | 0     | El nombre de clase de tono base-12 de la nota




