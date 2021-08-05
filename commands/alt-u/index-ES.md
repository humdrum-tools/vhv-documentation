---
title: <span class='keypress'>alt-u</span>
lang: en pl es
ref: commands-alt-u
author: Craig Stuart Sapp
translator: Mauro Loch
creation_date: 12 May 2018
translation_date: 6 Jun 2021
last_updated: 12 May 2018
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands compile filters
summary: "El comando <span class='keypress'>alt-u</span> alterna entre los formatos TSV y CSV de los datos Humdrum."
permalink: /commands/alt-u/index-ES.html
---

Al pulsar <span class="keypress">alt-u</span> se alterna entre las versiones TSV y CSV de los datos de Humdrum.  La forma estándar de los datos de Humdrum está en formato TSV:

{% include image.html
file="tsv.png"
alt="TSV view of Humdrum data"
caption="Vista TSV de los datos de Humdrum."
%}


Al pulsar <span class="keypress">alt-u</span>, los datos se mostrarán en formato CSV.

{% include image.html
file="csv.png"
alt="CSV view of Humdrum data"
caption="Vista CSV de los datos de Humdrum."
%}

Al pulsar <span class="keypress">alt-u</span> de nuevo los datos de Humdrum se volverán a mostrar en formato TSV.

El formato CSV es útil para cargarlo en un software que permita importar CSV, pero no la importación del formato TSV.  Además el formato CSV es útil para los casos en los que los caracteres de tabulación pueden quedar mezclados, como es el caso de los correos electrónicos.

Observa que los registros de referencia (el texto de color verde en la imagen de arriba) pueden tener tabulaciones que no se han convertido en comas al convertirlos al formato CSV.  Esto es debido a que tales tabulaciones no forman parte en la estructura de los datos de Humdrum.  Las tabulaciones en los comentarios globales tampoco serán alterados por la misma razón.


