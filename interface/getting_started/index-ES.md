---
title: Resumen del interfaz de usuario
lang: en es
ref: interface-getting_started-2
author: Craig Stuart Sapp
translator: Ana Cartagena Pérez
keywords: interface commands documentation 
creation_date: 3 Mar 2017
translation_date: 6 Jun 2021
last_updated: 3 Mar 2017
tags: [all, getting_started]
summary: "Descripción de las dos subventanas en la interfaz de VHV."
sidebar: main_sidebar
url: /interface/getting_started/index-es.html
permalink: /interface/getting_started/index-es.html
---

[VHV](http://verovio.humdrum.org) está organizado en dos componentes principales: un
editor de texto a la izquierda y un editor de anotaciones musicales a la derecha:


{% include image.html
file="mainwindow.png"
url="http://verovio.humdrum.org"
alt="VHV main page"
caption="Editor de texto a la izquierda y editor de notación a la derecha"
margin-bottom="-20px"
%}

Los datos de Humdrum que se escriben en el editor de texto se convierten
dinámicamente en notación musical:


{% include image.html
file="twinkle.gif"
alt="Entering data into the text editor"
caption="La notación se genera a medida que los datos de Humdrum se escriben en el editor de texto."
%}

Échale un vistazo al [Tutorial de codificación de Humdrum](/humdrum/getting_started/) para
instrucciones sobre cómo escribir datos musicales directamente en el editor de texto.  Los datos musicales también se pueden cargar arrastrando y soltando archivos Humdrum, MusicXML o MEI
en la página web.  Los archivos MusicXML y MEI se convertirán automáticamente en datos Humdrum en el editor de texto.  Para editar archivos MusicXML o MEI sin convertirlos pimero en datos de Humdrum, copia y pega los datos en vez de arrastrar y soltar el archivo.  Consulta la documentación de [Importación de MusicXML](/interface/musicxml/) e [Importación de MEI](/interface/mei/)
para más información.

La nota actual que se está editando en el editor de texto se resalta en rojo en la vista de notación.  No olvides terminar una columna con los símbolos de cierre `*-`; de lo contrario, el archivo Humdrum no será
válido, aunque la interfaz de VHV añade uno automáticamente para que
puedas ver la música mientras introduce los datos.

Puedes hacer clic y arrastrar el divisor entre las regiones de texto y notación como se muestra en la siguiente animación.  También hay un atajo de teclado para ocultar/mostrar el editor de texto escribiendo <span class="keypress">alt-y</span>.

{% include image.html
file="slidewindow.gif"
alt="Moving divider between text editor and notation editor"
caption="Desplazar el divisor entre el editor de texto y el de notación<br>(pulsa <kbd>alt</kbd>+<kbd>y</kbd> para alternar la visualización del editor de texto)."
%}


Consulta el [índice de páginas de inicio](/tag_getting_started.html) y en particular la descripción del [menú de ayuda](/interface/help_menu) para obtener más información básica sobre VHV.  También échale un vistazo a la [página Humdrum cargar/guardar](/interface/humdrum) para ver más formas de cómo cargar datos de Humdrum
en VHV que no sea escribirlos a mano.  Consulta la página [introducción a Humdrum](/humdrum/getting_started) para ver un tutorial sobre cómo codificar música en la sintaxis de Humdrum, aunque la mayoría de las veces la importación de datos se hace arrastrando y soltando archivos [MusicXML](/interface/musicxml).



