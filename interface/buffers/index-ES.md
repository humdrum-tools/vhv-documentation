---
title: Guardando buffers
lang: en es
author: Craig Stuart Sapp
creation_date: 18 Jun 2017
last_updated: 18 Jun 2017
tags: [all, getting_started, humdrum]
keywords: interface load save buffer
summary: "Los contenidos del editor se pueden almacenar en varios buffers persistentes y temporales."
sidebar: main_sidebar
permalink: /interface/buffers/index-ES.html
translator: Helena Martínez Olivas 
translation_date: 6 Jun 2021
---

## Buffers persistentes


La interfaz de VHV puede guardar los contenidos del editor de texto en nueve buffers persistentes.  Estos buffers se pueden cargar en el editor incluso después de cerrar el navegador y de volverlo a abrir.  Otros usos para los buffers sería guardar varios análisis de un trabajo para permitir que se cambie entre resultados rápidamente sin volver a ejecutar diferentes filtros.  Es prudente guardar el estado actual del editor de vez en cuando por si la página web de VHV se cierra accidentalmente, particularmente si estás editando un trozo complejo.

Para guardar el contenido del editor en un buffer, escribe un número del 1 al 9 y, después, la combinación de teclas <span class="keypress">alt-shift-S</span>.  Esto guardará los contenidos del editor en un buffer especificado.  Por ejemplo, <span class="keypress">5+alt-shift-S</span> guardará los contenidos del editor en el buffer 5.


Para cargar el buffer en el editor, teclea el número del buffer seguido de <span class="keypress">alt-shift-R</span> para restaurar el contenido del buffer en el editor.  Por ejemplo, <span class="keypress">5+alt-shift-R</span> restaurará el quinto buffer en el editor.

El búfer 1 es el buffer para guardar and cargar por defecto.  Si escribes <span class="keypress">alt-shift-S</span>sin especificar el número del buffer, se usará el primero.  En otras palabras, <span class="keypress">alt-shift-S</span> es equivalente a <span class="keypress">1+alt-shift-S</span>.  Asimismo, <span class="keypress">alt-shift-R</span> es equivalente a <span class="keypress">1+alt-shift-R</span> al restaurar el buffer por defecto.



## Buffer de autoguardado


En la posición 0 se almacena un décimo buffer.  Este se rellena una vez por minuto con el contenido actual del editor.   No es normal guardar en el buffer 0, pero puede ser útil para recuperar el contenido reciente del editor después de un problema importante, como por ejemplo pasar accidentalmente a una nueva pieza de repertorio mientras se edita otra, o cerrar accidentalmente la página web de VHV.  Para restaurar el buffer de autoguardado, teclea <span class="keypress">0+alt-shft-R</span>.   Esto tiene que hacerse en un minuto desde que VHV sea refrescado antes de que el contenido del buffer 0 sea sobreescrito con el contenido actual del editor.


Al restaurar un buffer persistente, como <span class="keypress">3+alt-shft-R</span> para cargar el tercer buffer, el contenido actual del editor se almacenará en el búfer 0.  Entonces tienes un minuto o menos para recuperar el contenido antiguo del editor si te equivocaste al recuperar uno de los buffers, pero escribiendo <span class="keypress">0alt-shft-R</span>.


## Buffer de salida


Cuando se cierra la página web de VHV, se utiliza otro buffer de autoguardado para guardar el contenido actual del editor.  Al volver a la página web de VHV dentro de una hora, este buffer de salida se restaurará en el editor.  En ciertos casos, como en la carga de un archivo de repertorio desde la URL, el contenido del editor se sobrescribirá con el contenido de datos de la URL.  Si necesitas recuperar los datos de salida, entonces teclea <span class="keypress">0+alt-shft-R</span> antes de que pase un minuto para restaurar el último contenido de autoguardado.


## Comandos relacionados


Ten en cuenta que <span class="keypress">command-z</span> (MacOS), o <span class="keypress">control-z</span>(Linux, Windows), también puede utilizarse para restaurar el contenido anterior del editor.

El comando <span class="keypress">alt-r</span> (sin la tecla shift) recargará un archivo de repertorio desde el origen.   Esto es necesario de vez en cuando para limpiar el buffer del trabajo si ha cambiado en la ubicación de la fuente.

