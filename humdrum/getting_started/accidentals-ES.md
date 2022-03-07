---
title: Tutorial de codificación de alteraciones
lang: en es 
ref: humdrum-getting_started
author: Craig Stuart Sapp
translator: David Rizo
keywords: humdrum encoding tutorial accidentals
creation_date: 20 Aug 2017
translation_date: 17 Aug 2021
last_updated: 25 Jan 2018
tags: [all, humdrum, getting_started]
verovio: "true"
vim: ts=3 ft=javascript
summary: Un tutorial sobre cómo codificar las alteraciones en los datos de **kern.
sidebar: main_sidebar
permalink: /humdrum/getting_started/accidentals-ES.html
---

<!--{% include humdrum/accidentals.txt %}-->
## Alteraciones ##

Las alteraciones deben indicarse siempre junto con el nombre del tono diatónico, a menos que el tono sea natural.  Las alteraciones hasta el doble sostenido/bemol pueden mostrarse en VHV (no pueden representarse con Verovio los triples sostenidos/bemoles o superiores, aunque pueden representarse en datos `**kern`):


{% include verovio.html
	source="acc1"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="acc1">
**kern
*clefG2
4c--
4d-
4en
4f#
4g##
*-
</script>

VHV calculará automáticamente qué alteraciones deben ser visibles en la notación gráfica. En el siguiente ejemplo, la armadura contiene un Fa sostenido, por lo que en el primer compás no se muestran sostenidos en los Fa.  El segundo compás contiene un Fa natural, ya que no hay alteración cromática del Fa, por lo que se muestra un natural para anular el Fa sostenido de la armadura.  Y al final del segundo compás, el segundo Fa tiene una alteración de sostenido que debe mostrarse; de lo contrario, parecería un Fa natural.

{% include verovio.html
	humdrum-min-height="300px"
	source="acc2"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="acc2">
**kern
*clefG2
*k[f#]
=1
4g
4f#
4e
4f#
=
4g
4f
4e
4f#
==
*-
</script>

Prueba a eliminar la armadura y vea qué ocurre con las alteraciones que aparecen en el ejemplo.

### Alteraciones de cortesía / forzadas ###

Cuando las alteraciones no son necesarias de acuerdo con el algoritmo para calcular las alteraciones visuales, pero las alteraciones son deseadas con el fin de añadir claridad para un intérprete, la alteración de una nota puede ser forzada a ser mostrada (sea requerida o no) añadiendo `X` después de la alteración.  


{% include verovio.html
	humdrum-min-height="300px"
	source="acc3"
	scale="55"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="acc3">
**kern
*k[f#]
*clefG2
=1
4g
4f
4e
4f
=
4g
4f#X
4e
4f#
==
*-
</script>

En el primer compás, se dan dos Fa-naturales, y sólo el primer Fa-natural muestra su alteración natural.  En el segundo compás, el primer fa tiene un sostenido, pero este sostenido no se mostraría normalmente ya que está dentro de la armadura de la tonalidad, y la línea de compás anuló el Fa natural del compás anterior.  Para evitar la confusión, el primer Fa sostenido en el segundo compás debería tener un sostenido de precaución añadido a la nota como se muestra en el ejemplo anterior.

Los signos becuadros no requieren la `X`, ya que siempre se muestran cuando se dan, pero cuando se utilizan para indicar una alteración de cortesía, la `X` es necesaria.  La `X` también puede utilizarse en las codificaciones diplomáticas para indicar una alteración visual en el manuscrito de origen. Además, para forzar o indicar que un accidental está implícito en una partitura diplomática, utilice `y` inmediatamente después de la alteración para forzar que se oculte.

### Alteraciones editoriales ###

Las alteraciones editoriales pueden indicarse añadiendo un registro de referencia RDF para un significante de usuario (carácter) utilizado para marcar las alteraciones editoriales en los datos.  Normalmente, el carácter `i` se utiliza para marcar las alteraciones editoriales en las codificaciones de [Josquin Research Project](http://josquin.stanford.edu) Humdrum, mostrando la alteración sobre la nota:

{% include verovio.html
	humdrum-min-height="410px"
	humdrum-min-width="400px"
	source="acc4"
	scale="55"
	pageWidth="1200"
%}
<script type="application/x-humdrum" id="acc4">
**kern
*clefG2
=1
4f#i
4e
4f
=
4f#j
4e
4f
=
4f#Z
4e
4f
==
*-
!!!RDF**kern: i = editorial accidental
!!!RDF**kern: j = editorial accidental, bracket
!!!RDF**kern: Z = editorial accidental, parentheses
</script>

El registro de referencia RDF puede colocarse en cualquier línea del archivo, pero normalmente se coloca al final de los datos.  Ten en cuenta que las alteraciones editoriales pueden afectar a la presentación visual de las alteraciones después del tono actual.  Intente hacer que el signo natural de la última nota del ejemplo anterior sea también una alteración editorial.

Ten en cuenta también que el estilo de la alteración editorial puede controlarse desde la entrada RDF.  Añade la cadena `brack` o `bracket` a la descripción RDF para que las accidentales editoriales se muestren como alteraciones normales encerradas entre corchetes.  Prueba también a añadir `paren` o `parentheses` a la línea RDF para mostrar la alteración editorial entre paréntesis.

