---
title: <span class='keypress'>alt-g</span>
lang: en es pl
page_language: es
translator: Mauro Loch
translation_date: 6 Jun 2021
translation_update:
ref: commands-alt-g
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands svg
summary: El comando <span class='keypress'>alt-g</span> muestra el código SVG de la notación musical mostrada en el editor. 
permalink: /commands/alt-g/index-ES.html
---

Al pulsar <span class="keypress">alt-g</span> se abrirá una nueva ventana que contenga el código SVG de la página visible en ese momento de la notación musical.  Este es un ejemplo de la función en acción:

{% include image.html
file="show-svg.gif"
alt="show SVG code for graphic notation."
max-width="50%"
caption="Al pulsar <span class='keypress'>alt-g</span> se abrirá el código SVG de la página de notación actual."
%}


[Aquí](sample.svg) está la imagen SVG extraída como en la imagen de arriba después de haberla guardado en un archivo.
El código SVG puede copiarse/pegarse en un editor de texto y guardarse en el disco duro.  Este comando es útil para extraer un ejemplo musical y utilizarlo como imagen estática en un artículo impreso o sitio web.


## Convertir la notación en imágenes de mapa de bits.


Muchas aplicaciones (como MS Word) no pueden cargar archivos de imagen SVG, por lo que los datos SVG deben convertirse en un mapa de bits para poder utilizar la imagen en esos programas.  Hay dos formas de generar mapas de bits de la notación VHV: un método sencillo es hacer una captura de pantalla.  La forma de hacer esto será diferente en los distintos sistemas operativos.  En MacOS, escribe <span class="keypress">command-shift-4</span> y luego dibuja un recuadro alrededor de la notación que desea capturar.  También es posible que quieras escribir primero <span class="keypress">alt-f</span> para que el color de fondo de la notación sea blanco.

{% include image.html
file="screenshot.gif"
alt="Capturing screenshot of notation"
max-width="100%"
caption="Hacer una captura de pantalla de la notación mostrada."
%}

Un método más refinado para extraer un mapa de bits para una página completa puede hacerse guardando la imagen SVG mostrada con el comando <span class="keypress">alt-g</span> y abriéndola después en [GIMP](https://www.gimp.org).  Aquí está la ventana de diálogo de importación de SVG
al abrir la imagen SVG en GIMP:

{% include image.html
file="svgopen.png"
alt="Loading SVG into GIMP"
max-width="50%"
caption="Ventana de opciones al abrir el SVG en GIMP."
%}

Define la anchura/altura de los píxeles en un número grande (como unos 2000 píxeles de ancho) para generar un mapa de bits de alta resolución a partir de la imagen SVG.  Aquí hay un ejemplo de la imagen cargada en GIMP:

{% include image.html
file="ingimp.png"
alt="Loading SVG into GIMP"
max-width="80%"
caption="Ventana de opciones al abrir el SVG en GIMP."
%}

El fondo gris a cuadros indica que la imagen es transparente.  Esto es útil cuando se muestra el mapa de bits sobre un fondo de color.  A continuación, puedes guardar la imagen, o seleccionar todo/copiar/pegar en otra aplicación como MS Word:

{% include image.html
file="msword.png"
alt="From GIMP to MS Word"
max-width="60%"
caption="Resultado de copiar/pegar de GIMP a MS Word."
%}


## Edición como imagen gráfica vectorial


Si quieres conservar el formato de gráficos vectoriales de la imagen SVG, pero quieres editar para hacer cambios o adiciones (como el análisis de marcado con cajas o flechas, etc.), entonces utiliza [Inkscape](https://inkscape.org/en), que es un editor gratis de gráficos vectoriales de código abierto.

{% include image.html
file="inkscape.png"
alt="in Inkscape"
max-width="80%"
caption="Cargar el SVG extraído en Inkscape y añadir marcas."
%}

Desde Inkscape, puede guardar en el [Enhanced Metafile format](https://en.wikipedia.org/wiki/Windows_Metafile) que es un antiguo formato de gráficos vectoriales de Microsoft que se puede cargar en MS Word.  Ten en cuenta en la siguiente imagen que las transparencias y la estratificación de marcas en Inkscape podrían no exportarse bien al formato EMF:

{% include image.html
file="emfword.png"
alt="EMF loaded into Word"
max-width="60%"
caption="Cargar un archivo EMF en MS Word que fue guardado desde Inkscape."
%}


Aquí hay un ejemplo de cómo guardar la imagen editada como un SVG de nuevo ([sample2.svg](sample2.svg)) y luego cargarla en un navegador web:

{% include image.html
file="svgchrome.png"
alt="Inkscape image loaded into Chrome"
max-width="60%"
caption="Cargar un archivo SVG en Google Chrome que fue guardado desde Inkscape."
%}





