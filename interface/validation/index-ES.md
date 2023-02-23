---
title: Validación de sintaxis
lang: en es
page_language: es
translator: ["Olga Francés Zoroa", "Mauro Loch"]
translation_date: 19 Aug 2019
translation_update:
ref: interface-validation
tags: [all, getting_started]
keywords: interface syntax validation
summary: "VHV validará la estructura y la sintaxis rítmica de los archivos Humdrum antes de intentar convertirlos en notación gráfica."
sidebar: main_sidebar
permalink: /interface/validation/index-ES.html
---

## Errores de sintaxis


Al editar un archivo Humdrum en [Verovio Humdrum
Viewer](http://verovio.humdrum.org), el editor [Ace](https://ace.c9.io/)
valida automáticamente la estructura del archivo Humdrum a medida que se escriben los datos.  Si detectas una estructura no válida en el contenido Humdrum
las ventanas de notación musical gráfica se resaltarán en rosa,
y podrás ver un mensaje de error moviendo el ratón sobre cualquiera
de las casillas "x" que aparecen en la secuencia de los números de línea a la izquierda de la ventana del editor.

Aquí puedes ver una demostración de los errores estructurales de sintaxis:

{% include image.html
file="syntax-error-1.png"
max-width="80%"
alt="Syntax errors"
caption="Errores estructurales de sintaxis."
%}

El primer problema es que la columna no se ha dividido correctamente en dos
subcolumnas.  Añadir `*^` después de la línea 2 solucionará ese problema:

{% include image.html
file="syntax-error-2.png"
max-width="80%"
alt="Syntax error 1 fixed"
caption="Primer error de sintaxis estructural corregido."
%}

Ahora solo hay un error de sintaxis, en la línea 8.  Para solucionar este error, añade el siguiente símbolo de fusión `*v` dos veces para combinar las subcolumnas en una sola columna de nuevo:

{% include image.html
file="syntax-error-3.png"
max-width="80%"
alt="Syntax error 2 fixed"
caption="Segundo error de sintaxis estructural corregido."
%}

Observa que la notación gráfica no está resaltada en rosa, lo que
indica que los datos se han procesado correctamente.  Observa también que,
cuando la música gráfica esté resaltada en rosa, el último estado válido
de los datos Humdrum se mostrará; esto no pasará con cualquier contenido nuevo que haya sido añadido después de que se identificara la estructura no válida.


## Avisos para la sintaxis


Los avisos para la sintaxis se visualizan como un signo de exclamación en un triángulo amarillo de precaución dentro de la columna de números de línea en la parte izquierda del editor de texto.  Estos errores no son de gran importancia, pero se deberían corregir si la intención es preparar una partitura para su distribución pública.

Aquí se muestra un ejemplo del icono de aviso que aparece en las líneas en blanco:

{% include image.html
file="blank-line-warning.png"
max-width="80%"
alt="blank line warning"
caption="Icono de aviso visualizado para una línea en blanco."
%}

Cuando muevas el ratón por encima del icono de aviso, aparecerá una explicación del aviso:

{% include image.html
file="blank-line-warning-message.png"
max-width="80%"
alt="blank line warning message"
caption="El mensaje de aviso para la línea en blanco se verá cuando pases el ratón por encima del icono de aviso."
%}

### Aviso para la sintaxis al final de la columna


El aviso para la sintaxis al final de la columna es un caso especial donde el mensaje de aviso se presenta cuando una columna no se ha acabado correctamente usando un código `*-`:

{% include image.html
file="end-of-spine-warning.png"
max-width="80%"
alt="end-of-spine warning message"
caption="Mensaje de aviso para la falta del terminador de una columna."
%}

Para analizar los datos Humdrum de la línea de comandos, ten en cuenta que este aviso es un error dentro de la estructura del archivo que se identificará mediante el comando *humdrum*.   Sin embargo, se trata como un aviso en VHV para que la notación gráfica musical se pueda mostrar mientras que los datos son escritos dentro del editor de texto.  Recuerda cerrar la columna correctamente cuando hayas acabado de meter la música.


## Sintaxis rítmica


La sintaxis rítmica en VHV también se comprueba dinámicamente de forma similar a la estructura de los archivos.  En este caso, los mensajes de error se muestran en la línea en la que se advierte el error rítmico y no en la línea en la que se produce (ya que no siempre es posible identificar en qué columna está el error rítmico).

Aquí hay un ejemplo de error rítmico, en el que los datos del pentagrama superior de la música contienen una nota negra con puntillo en lugar de una nota negra normal:

{% include image.html
file="rhythm-error.png"
max-width="80%"
alt="rhythm syntax error"
caption="Error de sintaxis rítmica."
%}

Observa que el error se encuentra en la undécima línea, pero en realidad está en la décima.  Si pasas el ratón por encima del icono de error, aparecerá una explicación sobre la advertencia:

{% include image.html
file="rhythm-error-warning.png"
max-width="80%"
alt="rhythm syntax error warning "
caption="Advertencia de error de sintaxis del ritmo."
%}

Esto significa que en el campo (columna) 2 el ritmo se adelanta una corchea con respecto al campo (columna) 1, ya que hay una corchea con puntillo en lugar de una negra en la segunda columna de la línea 10.


Corregir el error rítmico permite enviar los datos de Humdrum a herramientas de Verovio para su renderización en notación gráfica:

{% include image.html
file="rhythm-error-fixed.png"
max-width="80%"
alt="rhythm syntax error fixed "
caption="Error de sintaxis rítmica corregido."
%}


