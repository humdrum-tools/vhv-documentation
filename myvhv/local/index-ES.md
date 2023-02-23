---
title: Ejecutar VHV localmente
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: myvhv-local
search: exclude
tags: [all, maintenance]
sidebar: main_sidebar
keywords: maintenance local webserver
summary: Esta página describe cómo ejecutar el sitio web de VHV en tu ordenador local en lugar de hacerlo desde las páginas de Github.
permalink: /myvhv/local/index-ES.html
---

## Preliminares ##


### Instalación de jekyll ###

Sige las instrucciones para instalar Jekyll en el sitio web [jekyllrb.com/docs/installation](https://jekyllrb.com/docs/installation) y/o [https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll)

### Instalar git ###

Para comprobar si tiene git instalado, escriba en la línea de comandos (terminal):

```bash
which git
```

que debería responder con algo como:

```
/usr/local/bin/git
```

Si usas un ordenador MacOS y no tienes git, entonces instala [Homebrew](http://brew.sh). Si usas Windows, entonces buena suerte&mdash;aunque Windows 10 ahora viene con un [https://msdn.microsoft.com/en-us/commandline/wsl/install_guide](linux shell) que podrías probar. Si no tienes git en un sistema operativo linux/unix, entonces intenta escribir uno de estos:

```bash
apt-get install git-all
yum install git
dnf install git-all
```

Véase [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
 for more information.

Además, si te gustan los GUIs, entonces lee este enlace sobre [https://git-scm.com/downloads/guis](clientes GUI para git).

### Descargar el sitio web ###

Una vez instalado git, puedes descargar el sitio web de documentación de VHV con el comando

```bash
git clone https://github.com/humdrum-tools/verovio-humdrum-viewer
```

Esto descargará el sitio web en el directorio `./verovio-humdrum-viewer`.

## Ejecutar el sitio web localmente ##

Go into the `verovio-humdrum-viewer` directory (wherever you have stored it).  Then type:

```bash
./.serve
```

Esto compilará el sitio web y permitirá a tu navegador acceder al sitio web desde la dirección
`http://127.0.0.1:2000`.

Si el script `serve` no se ejecuta, lo más probable es que tengas que escribir el comando la primera vez:

```bash
bundle install
```


{% include warning.html
	content="Recientemente el componente nokogiri que debería instalarse con el comando anterior no funciona correctamente, así que prueba a ejecutar también el comando 'gem install nokogiri -v 1.6.8.1 -- --use-system-libraries=true --with-xml2-include=\"$(xcrun --show-sdk-path)\"/usr/include/libxml2' si hay algún problema."
%}

{% include image.html
	file="local.png"
	alt="VHV funcionando en el servidor web local."
	max-width="80%"
	caption="VHV funcionando en el servidor web local."
%}

### Ejecutar el sitio web fuera de línea ###

If you are not going to have access to the internet when accessing the website (such as
working on a plane), then you can run the website in local-only mode by typing:

```bash
./.serve-local
```

Para utilizar este script, primero tendrás que descargar el archivo `verovio-script.js` entrando en el directorio `scripts/local` y escribiendo `make` en el terminal.  Esto sólo tiene que hacerse una vez, pero puedes repetir la descarga para asegurarte de que tienes la versión más reciente del archivo `verovio-toolkit.js`.


{% include note.html
	content="Los repertorios online no están todavía disponibles para una versión completamente offline de VHV.  Si necesitas usar alguno de los repertorios en línea, tendrás que descargarlos por separado (como desde [github.com/humdrum-tools/humdrum-data](https://github.com/humdrum-tools/humdrum-data), y luego [arrastrar y soltar](/interface/humdrum/#drag-and-drop-humdrum-files-into-vhv) los archivos en la página local de VHV."
%}



