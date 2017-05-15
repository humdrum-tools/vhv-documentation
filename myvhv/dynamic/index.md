---
title: Creating dynamic in-browser images
author: Craig Stuart Sapp
vim: ts=3
creation_date: 11 Mar 2017
last_updated: 11 Mar 2017
tags: [all]
sidebar: main_sidebar
verovio: "true"
keywords: verovio dynamic
summary: Dynamic use of the verovio javascript toolkit to update the notation display of editable Humdrum data on the page.
permalink: /myvhv/dynamic/index.html
---

The page desribes how to generate dynamic notation from Humdrum data
that you edit on a web pages.  The setup for the Humdrum editing box
is a bit compilicated, so this page still has to be written.

In the meantime you can observe how it is setup in the Jekyll static-site
generating system for use in the VHV documentation.  Start with the
[source code](https://raw.githubusercontent.com/humdrum-tools/vhv-documentation/gh-pages/myvhv/dynamic/index.md) for this page.  Also see the 
[source code](https://github.com/humdrum-tools/vhv-documentation/blob/gh-pages/_includes/verovio.html) for the verovio figure template, and the
[source code](https://github.com/humdrum-tools/vhv-documentation/blob/gh-pages/_includes/verovio_support_functions.html) for the JavaScript support functions.

## Example ##

Try editing the Humdrum data in the box below.  The notation should update
as you change it.

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

Display of the Humdrum data is optional, but then the notation is not editable:



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


