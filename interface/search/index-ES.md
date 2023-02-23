---
title: Search toolbar
lang: en es
page_language: es
translator: David Rizo
translation_date: 29 Jul 2021
translation_update:
ref: interface-toolbar
tags: [all, getting_started]
keywords: interface search toolbar
summary: "How to use the search toolbar."
sidebar: main_sidebar
permalink: /interface/search/index-ES.html
---

{% include_relative style-local.html %}

Se puede acceder a una [barra de herramientas](/interface/toolbar) para buscar patrones musicales en la partitura haciendo clic en el icono circular cerca de la derecha de las barras de herramientas en la esquina superior superior derecha de VHV:


{% include image.html
	file="search-toolbar.png"
	alt="Página principal de VHV mostrando la barra de herramientas"
	caption="Barra de herramientas de búsqueda en la ventana VHV, esquina superior derecha."
%}

Como alternativa, utiliza el atajo de teclado <span class="keypress">4+alt-n</span> para
saltar a la barra de herramientas de búsqueda directamente.


## Búsqueda por tono ##

El primer campo de la barra de búsqueda es para la búsqueda de tonos.  La letra
de la "a" a la "g" se utilizan para los nombres de las notas, y la "r" para el silencio.
Éste es un ejemplo de búsqueda de la secuencia de tonos "C D E":

{% include image.html
	file="pitch-search.png"
	alt="Página principal de VHV mostrando la barra de herramientas"
	caption="Búsqueda de C, D, E."
%}

Esta búsqueda hara que se resalte la secuencia de tonos C, D, E.
Ten en cuenta que las letras mayúsculas o minúsculas
son intercambiables. Los espacios son opcionales entre las notas, pero los espacios entre las notas
y las alteraciones no están permitidas.



### Calidad cromática ###
Al buscar por nombre de tono, el método por defecto es por clases de tono diatónico.  Esto significa que "C" coincidirá con C-sostenido, C-natural, C-sostenido, etc.  Para buscar una versión
versión cromática de una clase de tono, añade un accidental después del nombre del tono (usando la sintaxis `**kern`
sintaxis alteración):


| Alteración | Ejemplo | Significado           |
| ---------- | ------- | --------------------- |
| `n`        | `Cn`    | natural - becuadro    |
| `-`        | `C-`    | bemol                 |
| `#`        | `C#`    | sostenido             |
| `--`       | `C--`   | doble bemol           |
| `##`       | `C##`   | doble-sostenid        |
| *nothing*  | `C`     | cualquier estado de alteración  |



## Búsqueda por intervalos ##
Los intervalos pueden buscarse en el cuadro central de la barra de búsqueda.  Los intervalos son
números de intervalos diatónicos. 

| Intervalo  | Significado           |
| ---------- | --------------------- |
| `1`        | nota repetida         |
| `2`        | arriba un tono        |
| `-2`       | abajo un tono         |
| `3`        | arrib una tercera	 |
| `-3`       | abajo una tercera     |


Los espacios son opcionales entre los números del intervalo; sin embargo, si deseas buscar
intervalos de varios dígitos (como una décima), la búsqueda actual de intervalos no los permite
(esto se añadirá en el futuro).


## Búsqueda por ritmo ##

| Ritmo      | Significado           |
| ---------- | --------------------- |
| `1`        | redonda               |
| `2`        | blanca                |
| `4`        | negra                 |
| `8`        | corchea               |
| `.`        | puntillo              |

Los espacios son opcionales para la búsqueda de ritmo.  En el futuro se implementará un mayor refinamiento de la cadena de búsqueda. Por ejemplo, "116" se interpretará como una redonda seguida
seguida de una semicorchea.  En el futuro también se implementará la búsqueda de grupos irregulares, como por ejemplo "6" para un tresillo de negra.


## Búsquedas combinadas ##

Puedes buscar varias características al mismo tiempo.  Cada búsqueda
se hará en paralelo (una búsqueda "AND").  Por ejemplo, si se busca
la secuencia de tonos "cde" y la secuencia de ritmo "2", coincidirá
con a una secuencia de tono "cde" que comienza en una blanca (es decir, el tono C
es una semicorchea).  Dado que la secuencia rítmica es más corta que
la secuencia de tono, el ritmo de los tonos D y E puede ser cualquiera.


{% include image.html
	file="combined-pitch-rhythm-search.png"
	alt="Página principal de VHV mostrando la barra de herramientas"
	caption="Búsqueda simultánea de tono y ritmo."
%}

Observa que la secuencia de tonos "C, D, E" al comienzo del segundo y
tercer compás no coincide porque el Do no empieza en una blanca.


Aquí hay una búsqueda paralela similar de tono e intervalo:


{% include image.html
	file="combined-pitch-interval-search.png"
	alt="Página principal de VHV mostrando la barra de herramientas"
	caption="Búsqueda simultánea de tono y ritmo."
%}

La secuencia de tonos "C, D, E" coincide en los dos primeros compases pero no en el
tercero, porque el intervalo entre las dos primeras notas (Do y Re), debe ser un
segunda.  En el tercer compás, el intervalo es una séptima descendente.

## Mostrar la barra de herramientas de búsqueda en la carga de VHV desde una URL ##
Añade el parámetro "toolbar=search" a la URL de VHV para mostrar la barra de herramientas de búsqueda
al cargar VHV:


<a target="_blank" href="https://verovio.humdrum.org?toolbar=search">verovio.humdrum.org?toolbar=search</a>

## Búsqueda a partir de los parámetros de la URL ##
Se puede añadir una búsqueda a la URL.  Esto es útil si se quiere cargar un archivo específico
y hacer una búsqueda en él inmediatamente.


| Parámetro  | Ejemplo   | Significado           |
| ---------- | -------   | --------------------- |
| `p`        | `p=cdefg` | Búsqueda de la secuencia de tonos C, D, E, F, G |
| `i`        | `i=3-52`` | Búsqueda de la secuencia de intervalos 3, -5, 2 |
| `r`        | `r=4881`  | Búsqueda de la secuencia rítmica 4, 8, 8, 1 |

También hay un valor especial para el tono: `p=bach` que busca
la secuencia de tonos Si-bemol, La-natural, Do-natural, Si-natural:

<a target="_blank" href="https://verovio.humdrum.org/?k=ey&file=chorales/chor166.krn&p=bach">
https://verovio.humdrum.org/?k=ey&file=chorales/chor166.krn&p=bach
</a>

(comprueba la coincidencia resaltada en el último compás)


