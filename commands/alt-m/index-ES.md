---
title: <span class='keypress'>alt-m</span>
lang: en es pl
page_language: es
translator: David Rizo
translation_date: 5 Aug 2021
translation_update:
ref: commands-alt-m
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands 
summary: "El comando <span class='keypress'>alt-m</span> muestra la conversión de datos MEI en el editor de texto."
permalink: /commands/alt-m/index-ES.html
---
Al pulsar <span class="keypress">alt-m</span> se sustituirán los datos de Humdrum
en el editor de texto con su conversión a datos MEI.  Los datos MEI
se generan normalmente entre bastidores en el proceso de
convertir los datos de Humdrum en imágenes SVG de notación musical en VHV.

Mientras los datos MEI se muestran en el editor de texto, pueden ser
editados y cualquier cambio se reflejará en la ventana de notación gráfica.  
Además, al hacer clic en los objetos de la notación, el cursor del editor de texto se desplazará al elemento paralelo en la ventana MEI; sin embargo, los comandos de edición gráfica no funcionarán con los datos MEI.

Puedes devolver los datos originales de Humdrum al editor de texto pulsando
<span class="keypress">alt-h</span>, pero cualquier cambio realizado
a los datos MEI se perderán.  Este es un ejemplo de cómo escribir los datos de Humdrum
en el editor de texto, y luego escribiendo <span
class="keypress">alt-m</span> para ver los datos MEI transcodificados:


{% include image.html
	file="mei-data.gif"
	alt="visualizando datos MEI."
	caption="Cambiar el editor de texto al modo MEI después de escribir algunos datos de Humdrum."
%}



