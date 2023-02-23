---
title: <span class='keypress'>alt-c</span>
lang: en es pl
page_language: es
translator: Mauro Loch
translation_date: 6 Jun 2021
translation_update:
ref: commands-alt-c
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands compile filters
summary: "El comando <span class='keypress'>alt-c</span> compila filtros incrustados."
permalink: /commands/alt-c/index-ES.html
---

Al pulsar <span class="keypress">alt-c</span> se aplicará cualquier [filtro](/filter/) incrustado (o [filtro URL](/filter/url)) a los datos de Humdrum en el editor de textos, y luego se sustituirán los contenidos del editor de texto por los datos filtrados.


## Añadir una columna vacía.


Para añadir una nueva columna a los datos de Humdrum, utiliza el [filtro de extracción](/filter/extract) y el comando
<span class="keypress">alt-c</span>.  El siguiente filtro extrae todas las columnas originales, y añade una columna vacía al final de las líneas de datos:

```
!!!filter: extract -s 1-$,0
```

El carácter `$` representa la última columna del archivo y `0` representa una línea en blanco.


Antes de que se compile el filtro:

{% include image.html
file="precompile.png"
alt="view before compiling a filter."
caption="Los datos de la memoria antes de compilar un filtro."
%}


Después de pulsar alt+c:<span class="keypress"></span>

{% include image.html
file="postcompile.png"
alt="view after compiling a filter."
caption="Los datos de Humdrum después de compilar un filtro."
%}

La línea del filtro ha cambiado a `!!!Xfiltro:` que indica
que el filtro se ha aplicado (y no se volverá a aplicar).
Esta línea se puede eliminar si ya no se necesita, o se puede borrar la `X` para volver a aplicar el filtro.


## Ejemplo de transposición


Aquí se muestra un ejemplo de [transposición](/filter/transpose) de los datos de Humdrum:

{% include image.html
file="transpose1.png"
alt="view before compiling a transpose filter."
caption="Los datos de Humdrum antes de compilar un filtro de transposición."
%}

Observa que la música se muestra en mi mayor,
pero los datos están en do mayor.  Esto se debe a que el filtro se aplica a los datos de Humdrum en el editor de texto antes de convertirlos en datos MEI y, a continuación, se renderizan en una imagen SVG.

Para ver los mismos datos que generan la notación, pulsa <span class="keypress">alt-c</span> para compilar el filtro:

{% include image.html
file="transpose2.png"
alt="view after compiling a transpose filter."
caption="Los datos de Humdrum después de compilar un filtro de transposición."
%}

Ahora los datos musicales de los datos de texto coinciden con la notación gráfica de la música.










