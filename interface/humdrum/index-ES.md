---
title: Load/Save Humdrum data
lang: en es
page_language: es
translator: ["María Yagüe Gran", "Helena Martínez Olivas"]
translation_date: 6 Jun 2021
translation_update:
ref: interface-humdrum
tags: [all, getting_started, humdrum]
keywords: interface humdrum load save import export
summary: "Humdrum data can be loaded or saved in multiple ways."
sidebar: main_sidebar
permalink: /interface/humdrum/index-ES.html
---

## Arrastrar y soltar archivos de Humdrum en VHV


La interfaz de VHV puede cargar archivos de Humdrum arrastrando y soltando un icono de archivo
desde el sistema operativo a la página VHV:

{% include image.html
file="drag-drop-humdrum.gif"
alt="Humdrum file import example"
max-width="100%"
caption="Archivo Humdrum cargado mediante arrastrar y soltar en VHV."
%}

Intenta descargar el [mismo archivo Humdrum](data.txt) utilizado en la figura de
arriba, y cárgalo en VHV de manera similar (normalmente se guarda en un
navegador web haciendo clic con el botón derecho del ratón en el enlace y luego elige *guardar
enlace como*).

## Copiar y pegar datos de Humdrum


Los datos de Humdrum también se pueden pegar directamente en el editor de texto de la VHV:

{% include image.html
file="copy-paste-humdrum.gif"
alt="Humdrum file copy/paste example"
max-width="100%"
caption="Copiar y pegar datos de Humdrum en el editor de texto VHV."
%}


## Copiar y pegar con el terminal


Copiar desde el editor de texto VHV y pegar en otro editor del sistema operativo es posible, ya sea con <span
class="keypress">ctrl-c</span>/<span class="keypress">ctrl-v</span>
en Windows, o <span class="keypress">command-c</span>/<span
class="keypress">command-v</span> en MacOS (o puedes averiguar
por tu cuenta cómo copiar/pegar en linux/unix). También hay que tener en cuenta que
<span class="keypress">ctrl-a</span> o <span class="keypress">ctrl-a</span>
pueden utilizarse para seleccionar todo el contenido del editor de texto VHV antes de copiarlo.

En las siguientes secciones se explica cómo copiar/pegar entre *entrada estándar* y
*salida estándar* en la terminal y en el editor VHV.


### MacOS usando pbcopy/pbpaste


Cuando se trabaja con un terminal en MacOS, se puede utilizar la función
[pbcopy](http://osxdaily.com/2007/03/05/manipulating-the-clipboard-from-the-command-line/)
para copiar la salida estándar al portapapeles (o *P*aste*B*oard si quieres
recordar el nombre del comando).
Si el archivo Humdrum se llama `archivo.krn`, el comando de copia es:

```bash
cat file.krn | pbcopy
```

A continuación, ve al editor de texto de VHV y escribe <span
class="keypress">command-v</span> para pegar en VHV.

{% include image.html
file="pbcopy-humdrum.gif"
alt="Humdrum file copy/paste from the terminal"
max-width="100%"
caption="Copiar y pegar en Humdrum desde la terminal usando pbcopy."
%}


Al contrario, [pbpaste](http://osxdaily.com/2007/03/05/manipulating-the-clipboard-from-the-command-line/) se puede usar para copiar datos desde el editor VHV y pegarlos a la terminal como entrada estándar.  La siguiente imagen lo muestra copiando los datos desde el editor de textos VHV al comando [census](http://www.humdrum.org/man/census/) :

{% include image.html
file="pbpaste-humdrum.gif"
alt="Humdrum file copy/paste to the terminal"
max-width="100%"
caption="Copiar y pegar en Humdrum desde la terminal usando pbpaste."
%}

El comando mostrado arriba es:

```bash
pbpaste | census -k
```

donde los datos del editor VHV están reproducidos en comando census. Esta información lleva al primer movimiento de la sonata para piano nº26 op. 81 de Beethoven:

```
Datos Humdrum

Número de datos de símbolos:     7034
Número de símbolos nulos:     3329
Número de paradas múltiples:  679
Número de datos de anotaciones:    2129
Número de comentarios:        12
Número de interpretaciones: 115
Número de anotaciones:         2256

Datos Kern

Número de cabeza de notas:      3944
Número de notas:           3917
Nota más larga:              2.
Nota más corta:             24
Nota más alta:              ffff
Nota más corta:               FFF
Número de silencios:           268
Máximo número de voces:  9
Número de líneas de barras simples: 197
Número de líneas de barras dobles: 1
```



## Guardar archivos/datos de Humdrum


Los datos de Humdrum se pueden copiar desde el editor de textos VHV y, después, se puede pegar en otro editor del mismo sistema operativo.

Un método alternativo es guardar el contenido del editor de textos VHV desde el navegador con el comando [<span
class='keypress'>alt-s</span>](/commands/alt-s).  Esto guardará el contenido del editor en el lugar donde se guardan los archivos desde tu navegador.  Hay que señalar que los contenidos del editor de textos no tienen que contener datos de Humdrum, por lo que el nombre del archivo por defecto es `data.txt` en vez de `data.krn`.

{% include note.html
content="Si un archivo ya existe en el directorio/carpeta con el mismo nombre, el navegador añadirá una extensión progresiva al nombre del archivo, como \"data (1).txt\", \"data (2).txt\", y así sucesivamente."
%}


Aunque el nombre de archivo por defecto para guardar con <span
class='keypress'>alt-s</span> es `data.txt`, puedes guardar en un nombre de archivo diferente añadiendo el texto `!!!!SEGMENT: myfile.krn` antes de la primera línea en el contenido del archivo Humdrum en el editor de texto VHV.
Para los archivos de repertorio cargados desde [kernScores](http://kern.humdrum.org), se utilizará el nombre de archivo original de los datos de origen.

El archivo guardado estará en formato [UTF-8](https://en.wikipedia.org/wiki/UTF-8).  Si no hay caracteres de bits altos en el archivo, entonces es equivalente a un archivo de texto ASCII plano.  Las personas con dificultades tecnológicas probablemente deben utilizar el método <span class='keypress'>alt-s</span> para guardar en lugar de copiar y pegar en un editor de texto, ya que deben asegurarse de que el texto copiado se guarda en un archivo ASCII y no en un archivo que contenga comandos de formato como un archivo [RTF](https://en.wikipedia.org/wiki/Rich_Text_Format) o MS Word.

Intenta guardar un archivo de esta manera y luego volver a cargarlo en el editor de texto de VHV, ya sea con el método de arrastrar y soltar o con los métodos de copiar y pegar descritos anteriormente.  Aquí se muestra una demostración de cómo guardar dos archivos (corales de Bach 61 y 62), y luego arrastrarlos de nuevo al editor VHV desde la carpeta de descargas.

{% include image.html
file="save-drag-drop.gif"
alt="saving and loading Humdrum files"
max-width="90%"
caption="Guardar dos archivos con <span class='keypress'>alt-s</span> y luego arrastrarlos de nuevo a VHV."
%}




