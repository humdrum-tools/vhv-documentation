---
title: Uso de Verovio en un terminal
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: myvhv-command_line
sidebar: main_sidebar
tags: [all]
vim: ts=3
keywords: verovio humdrum command-line terminal unix
summary: Verovio puede utilizarse en la línea de comandos para producir imágenes SVG o datos MEI a partir de archivos Humdrum.
permalink: /myvhv/command_line/index-ES.html
---


## Cómo empezar ##


### Descarga de Verovio ###

Para utilizar la versión de línea de comandos de Verovio, primero debes descargarlo y compilarlo.  

#### Instalación de git ####

Para descargarlo, utiliza [git](https://en.wikipedia.org/wiki/Git).  Puede ser necesario ser descargado primero.

{% include note.html
	content="Para MacOS, instala [Homebrew](http://brew.sh) que es un gestor de paquetes de Linux para MacOS. Esto instalará Git al mismo tiempo que se instala Homebrew"
%}

{% include note.html
	content="Para linux, git se puede instalar con un comando similar a `yum install git` o `apt-get install git` o `dnf install git`.  Cuál usar dependerá de tu versión de linux"
%}

Para comprobar si tienes git instalado en tu ordenador, escribe el comando
```bash
which git
```
Si git está instalado, el comando anterior informará de dónde se encuentra.  Si no se indica ninguna ubicación, entonces git no está instalado.

#### Clonación desde Github ####

Una vez instalado git, descarga Verovio con este comando:

```
git clone https://github.com/rism-ch/verovio
```

*Clonar* un repositorio con git significa descargarlo.
Este comando debería descargar el código fuente de Verovio a un directorio
llamado `verovio` en el directorio actual.

### Selecciona la rama develop-humdrum ###

La versión más actualizada de Verovio para su uso con Humdrum se encuentra en la rama `develop-humdrum` del repositorio. Cambia a esta rama con el comando:

```
cd verovio
git checkout develop-humdrum
```

### Instalación de cmake ###

También debes tener instalado [cmake](https://cmake.org) para poder configurar el Makefile para compilar verovio.  Teclea:

```bash
which cmake
```

Para ver si está instalado. Si no es así entonces habrá que instalarlo. Para instalar en MacOS si puedes ejecutar el siguiente comando para instalar cmake si Homebrew está instalado:

```bash
brew install cmake
```

Para linux, uno de los comandos `yum install cmake`, `apt-get install cmake` o `dnf install cmake` debería instalar cmake.  El comando de instalación a ejecutar dependerá de tu versión de linux.

### Creación de Makefile con cmake ###

A continuación, necesitas crear un makefile para Verovio con este comando:

```bash
cd tools
cmake ../cmake
```

### Compilación del ejecutable ###

Después de que cmake haya creado el Makefile, escribe este comando para compilar Verovio:

```bash
make
make install
```

El `make install` copiará las fuentes musicales de Verovio en `/usr/local/share/verovio`, y el ejecutable se copiará en `/usr/local/bin/verovio`.

Puedes comprobar si la instalación se ha completado escribiendo:
```bash
which verovio
```
y el comando debería responder con `/usr/local/bin/verovio`.

### Actualización de Verovio ###

Para actualizar verovio más tarde al vervio más reciente, puedes usar estos comandos:

```
cd verovio/tools
git pull
make
make install
```

Si ha habido cambios importantes en el código fuente, es posible que tengas que añadir `make clean` antes de make:

```
cd verovio/tools
git pull
make clean
make
make install
```

## Uso de Verovio ##

Consulta la [página de documentación de la línea de comandos de verovio](http://www.verovio.org/command-line.xhtml) para obtener una lista completa de las opciones que reconoce Verovio. Escribe:

```bash
verovio --help
```
dará una lista de la mayoría de las opciones.

### Conversión básica de Humdrum a SVG ###

El uso más sencillo de Verovio para convertir los datos de Humdrum en una imagen SVG es:

```bash
verovio file.krn
```

Esto creará un archivo llamado `file.svg` con la notación.  Aquí hay algunos [datos humdrum](test.txt) para usar como prueba.  Esto es lo que la salida SVG debe parecer:

<center>
<img src="test.svg">
</center>



{% include note.html
	content="En MacOS, intenta escribir `open file.svg` para ver la imagen en un navegador web (esto dependerá del programa que esté registrado para abrir las imágenes SVG cuando haga doble clic en ellas)."
%}

### --adjust-page-height ###

Observa que el ejemplo de la sección anterior tiene un gran espacio vacío en la parte inferior de la imagen SVG.  Una opción especialmente útil para solucionar esto es `--adjust-page-height`.  Esta opción reducirá la altura de la imagen SVG de salida al último sistema de música en una página con espacio extra debajo del último pentagrama.

Puedes configurar la altura de la página para que sea muy alta, y luego añadir `--adjust-page-height` para forzar que toda la música se muestre en una sola imagen SVG, incluso si hay mucha música:

```bash
verovio file.krn --adjust-page-height -h 60000
```

Ahora la salida de la imagen SVG no tendrá ningún espacio vacío en la parte inferior de la música:

<center>
<img src="test2.svg">
</center>




### Suministro de datos a Verovio mediante tuberías ###

Verovio acepta la entrada estándar si utilizas `-` como nombre de archivo de entrada.  Por ejemplo, si quieres transponer los datos de prueba a Sol menor e imprimirlos con Verovio en un solo comando:

```bash
transpose -kg file.krn | verovio - -o d-minor-version --adjust-page-height
```

Esto creará el archivo `d-minor-version.svg`:

<center>
<img src="test3.svg">
</center>



### Altura/anchura de la imagen ###

Este es un ejemplo de cómo establecer la altura y la anchura de la imagen SVG:

```bash
verovio file.krn -w 900 -h 1500
```

<center>
<img src="test4.svg">
</center>




### Seleccionar una página ###

Si la notación renderizada es más larga que una página, utiliza la opción `--page`:

```bash
verovio file.krn -w 900 -h 1500 --page=2
```

<center>
<img src="test5.svg">
</center>





### Escalar la imagen ###

La opción `-s` puede utilizarse para establecer el tamaño de la notación, siendo el valor predeterminado `-s 100` para el 100% (tamaño completo).

```bash
verovio file.krn -w 1000 -h 60000 --adjust-page-height -s 20
```

<center>
<img src="test6.svg">
</center>


### Salida de todas las páginas ###

La opción `--all-pages` puede utilizarse para imprimir todas las páginas con un solo comando:


```bash
verovio file.krn -w 1000 -h 1000 --all-pages -s 50
```

Page 1:
<center>
<img src="test7_001.svg">
</center>

Page 2:
<center>
<img src="test7_002.svg">
</center>

Page 3:
<center>
<img src="test7_003.svg">
</center>

Page 4:
<center>
<img src="test7_004.svg">
</center>



### Ajustar el espacio entre sistemas ###

La opción `--spacing-system` controla la distancia entre sistemas.  Las unidades del parámetro están en alturas de tono diatónico.

El relleno por defecto entre sistemas es "6", que es igual a la altura de 3 líneas del pentagrama.  El uso de 0 seguirá dejando espacio entre los sistemas, pero es el valor mínimo para esta opción.

```bash
verovio file.krn -w 1000 -h 1000 --page=2 --spacing-system=0 -s 50
```

<center>
<img src="test8a.svg">
</center>

```bash
verovio file.krn -w 1000 -h 1100 --page=2 --spacing-system=8 -s 50
```

<center>
<img src="test8b.svg">
</center>


La opción `--spacing-staff` funciona de forma similar a `--spacing-system`, pero controla la distancia entre pentagramas dentro de un sistema.

### Espacios de igual duración ###

Puedes ajustar el valor de `--spacing-non-linear` a 1 para generar una notación musical que tenga un espacio horizontal entre las notas que sea proporcional a la duración de las mismas. 

La opción `--spacing-linear` (por defecto 0,25) suele tener que usarse en este caso para comprimir la notación; de lo contrario, es demasiado ancha cuando se establece sólo el `--spacing-non-linear`.

```bash
verovio file.krn -w 1000 -h 1000 --spacing-system=0 -s 40 --spacing-non-linear=1 --spacing-linear=0.05 --page=2
```

<center>
<img src="test10a.svg">
</center>

La opción `--spacing-non-linear` se utiliza para controlar la relación entre el ancho de la disposición horizontal de una nota y una nota con el doble de duración de la primera.  Si se establece esta relación a 1 se produce un espaciado lineal (el nombre de la opción es confuso).  Si se ajusta a un valor de 0,5 se produce un espaciado igual para todas las duraciones de las notas:

```bash
verovio file.krn -w 1000 -h 1000 --spacing-system=0 -s 40 --spacing-non-linear=0.5 --spacing-linear=0.05
```

<center>
<img src="test10b.svg">
</center>


El espaciado básico de las notas se ajustará ligeramente para poder encajar las alteraciones en la música.  Y fíjate en que cada línea de música en el ejemplo anterior tiene espaciados ligeramente diferentes de los otros pentagramas, ya que los sistemas están justificados a todo lo ancho de la página, lo que hace que la música en cada pentagrama se estire o se comprima ligeramente.




### Convertir los datos de Humdrum en datos MEI ###

Este es un ejemplo de cómo convertir los datos de Humdrum en datos de MEI:

```bash
verovio file.krn -t mei --all-pages --no-layout
```

Las dos últimas opciones son necesarias al convertir en datos MEI.

Opciones:

-t mei
: establece la salida de destino al formato MEI (por defecto es SVG).

--all-pages
: incluir todas las páginas de datos (en realidad no hay páginas, pero es necesario).

--no-layout
: no calcular la disposición de la notación (que sólo es necesario para la creación de SVG).


### Convertir datos MusicXML en datos Humdrum ###

Puedes utilizar el convertidor de MusicXML a Humdrum incrustado para generar datos de Humdrum a partir de un archivo MusicXML de entrada:


```bash
verovio file.xml -t musicxml-hum
```




