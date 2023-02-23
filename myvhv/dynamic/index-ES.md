---
title: Creación de imágenes dinámicas en el navegador
lang: en es
page_language: es
translator: David Rizo
translation_date: 10 Aug 2021
translation_update:
ref: myvhv-dynamic
vim: ts=3
tags: [all]
sidebar: main_sidebar
verovio: "true"
keywords: verovio dynamic
summary: Uso dinámico del toolkit javascript de Verovio  para actualizar la visualización de la notación de los datos editables de Humdrum en la página.
permalink: /myvhv/dynamic/index-ES.html
---

La página describe cómo generar notación dinámica a partir de los datos de Humdrum que se editan en una página web.  La configuración del cuadro de edición de Humdrum es un poco complicada, por lo que esta página todavía tiene que ser escrita.

Mientras tanto, puedes observar cómo se configura en el sistema de generación de sitios estáticos Jekyll para su uso en la documentación de VHV.  Empieza con el [código fuente](https://raw.githubusercontent.com/humdrum-tools/vhv-documentation/gh-pages/myvhv/dynamic/index.md) para esta página.  También puedes ver el [código fuente](https://github.com/humdrum-tools/vhv-documentation/tree/master/_includes/verovio.html) para la plantilla de figuras de Verovio, y el [código fuente](https://github.com/humdrum-tools/vhv-documentation/tree/master/_includes/verovio_support_functions.html) para las funciones de soporte de JavaScript.

## Ejemplo ##

Intenta editar los datos de Humdrum en el cuadro de abajo.  La notación debería actualizarse a medida que la modificas.

{% include verovio.html
	source="myhumdrum"
%}

<script type="text/humdrum" id="myhumdrum">
**kern
*M4/4
=1-
4c
4c
4g
4g
=2
4a
4a
2g
=3
4f
4f
4e
4e
=4
4d
4d
2c;
==
*-
</script>

La visualización de los datos de Humdrum es opcional, pero entonces la notación no es editable:



<div style="margin-top: -10px;">
{% include verovio.html
	source="myhumdrum2"
	pageWidth="1600"
	humdrum-visible="false"
%}
<script type="text/humdrum" id="myhumdrum2">
**kern
*M4/4
=1-
4c
4c
4g
4g
=2
4a
4a
2g
=3
4f
4f
4e
4e
=4
4d
4d
2c;
==
*-
</script>
</div>


