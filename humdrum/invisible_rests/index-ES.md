---
title: Silencios invisibles
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: humdrum-invisible_rests
keywords: humdrum invisible rests
verovio: "true"
tags: [all, humdrum, RDF]
summary: "Descripción de los silencios invisibles y cómo mostrarlos para su corrección."
sidebar: main_sidebar
permalink: /humdrum/invisible_rests/index-ES.html
---

Los silencios invisibles se utilizan para alinear las voces/capas secundarias con la principal. Son más comunes en la música de teclado, donde las voces pueden aparecer y desaparecer en cualquier parte de un compás. 

En la conversión de Humdrum a MEI, son posibles tres tipos de *silencios invisibles*.  El primer tipo es un silencio codificado explícitamente con un significante `yy` añadido a la señal, como `4ryy`, que significa un silencio invisible de negra.  El segundo tipo es un valor simple de `**recip` sin significantes de tono o silencio, como `4` para una duración de negra.

MEI requiere que las capas de los compases se rellenen completamente con elementos rítmicos, mientras que Humdrum permite crear o fusionar columnas secundarias en cualquier parte de un compás.  El tercer tipo de silencio invisible es el que se añade a los datos de MEI para rellenar la capa donde se expresan parcialmente las capas de Humdrum.

## Coloreado de todos los silencios individuales ##

Los silencios invisibles pueden hacerse visibles en la notación añadiendo esta línea meta-RDF en cualquier parte de los datos de Humdrum:

```
!!!RDF**kern: show spaces
```

MEI llama a los silencios invisibles `<space>`, por eso el texto de la acción es `mostrar espacios`.  Las tres categorías de silencios invisibles en Humdrum se mostrarán con esta entrada RDF.  Si quieres mostrar los silencios invisibles en un color diferente, añade un parámetro de color a la línea, como por ejemplo usar el color por defecto:

```
!!!RDF**kern: show spaces color=hotpink
```

Se permiten tanto [HTML 5/SVG](http://www.december.com/html/spec/colorsvg.html) como [colores hexadecimales](http://www.hexcolortool.com).


## Color por categoría de silencio ##

Si deseas colorear una sola categoría de silencios invisibles en la notación, utiliza cualquiera de estas líneas RDF:

```
!!!RDF**kern: show invisible rests color=chartreuse
!!!RDF**kern: show recip spaces color=hotpink
!!!RDF**kern: show implicit spaces color=blueviolet
```

`show invisible rests` se utiliza para mostrar silencios explícitos que contienen el significante "y" en el símbolo de silencio. La opción `recip spaces` se utiliza para mostrar los silencios invisibles producidos por los tokens recipients simples que no tienen significantes de tono o de silencio.  `implicit spaces` se utiliza para mostrar silencios invisibles generados para rellenar todas las capas con duraciones completas del compás.

Estos tres coloreados se pueden utilizar con el RDF `show spaces`, y cada una de ellas sustituirá al color global de los silencios invisibles para su tipo de silencio.


{% include verovio.html
	humdrum-min-height="300px"
	humdrum-min-width="500px"
	source="category"
	tabsize="8"
	scale="75"
	pageWidth="800"
%}
<script type="application/x-humdrum" id="category">
**kern
=1
*^
2cc	4
.	4e
4ryy	4d
*v	*v
4c
==
*-
!!!RDF**kern: show invisible rests color=chartreuse
!!!RDF**kern: show recip spaces color=hotpink
!!!RDF**kern: show implicit spaces color=blueviolet
</script>

Prueba a eliminar los registros RDF y observa que los silencios desaparecen de la notación.




