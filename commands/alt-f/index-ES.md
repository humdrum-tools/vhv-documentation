---
title: <span class='keypress'>alt-f</span>
lang: en pl es
ref: commands-alt-f
author: Craig Stuart Sapp
translator: Mauro Loch
creation_date: 5 Mar 2017
translation_date: 6 Jun 2021
last_updated: 5 Mar 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands freeze notation
summary: "El comando <span class='keypress'>alt-f</span> alterna el congelado del renderizado dinámico de la renderización de la partitura."
permalink: /commands/alt-f/index.html
---

Al pulsar <span class="keypress">alt-f</span> se alternará entre congelar/descongelar la representación de la notación dinámica.  Normalmente, cualquier cambio en el contenido del editor de texto desencadenará una nueva representación de la notación gráfica.  En el caso de los archivos de gran tamaño, con la estructura actual esto lleva cada vez más tiempo.  Para poder acelerar la entrada de datos en la ventana de edición de texto, la notación puede congelarse con el comando <span class="keypress">alt-f</span>.

Mientras la generación de la notación esté congelada, ningún cambio realizado en el editor de texto se actualizará en la notación.  Después de realizar los cambios, al pulsar <span class="keypress">alt-f</span> se descongelará la notación y se actualizará para que coincida con el contenido actual del editor de texto.

Cuando la notación se congela, el fondo de la notación se vuelve blanco.  Descongelar la notación devolverá el color de fondo a grisáceo:

{% include image.html
file="freeze-unfreeze.gif"
alt="freezing and unfreezing notation."
caption="Congelar y descongelar la notación mientras se escribe en el editor de texto."
%}




