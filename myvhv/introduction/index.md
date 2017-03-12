---
title: myVHV introduction
author: Craig Stuart Sapp
creation_date: 10 Mar 2017
last_updated: 10 Mar 2017
sidebar: mydoc_sidebar
tags: [all]
verovio: true
vim: ts=3 ft=html
keywords: verovio humdrum
summary: The myVHV section of the documentation demonstrates how VHV technology can be used on your own webpages.
permalink: /myvhv/introduction/index.html
---

<style>
table td:first-child { width: 180px; }
td, tr, table { border: none !important; }
pre#myhumdrum, pre#myhumdrum2 { background: white; }
div #myhumdrum, div #myhumdrum2 { height: 420px; overflow: auto; white-space: pre; }
</style>

[Verovio Humdrum Viewer](http://verovio.humdrum.org) is a fairly
complex frontend to the [verovio javascript
toolkit](http://www.verovio.org), but simpler interactions
with verovio are easy to implement.   Verovio is a music typesetting
library [written in
C++](https://github.com/rism-ch/verovio/tree/develop-humdrum) that
converts Humdrum, MEI, MusicXML, or Plaine & Easie musical data
into SVG notation images, either within a browser with the JavaScript 
toolkit implementation or in an operating system on the
command-line.
This section of the VHV documentation gives examples
of how to use verovio on your own webpages or to generate graphical
music notation for various purposes.


## Command-line use ##

Verovio can be compiled for use in a unix-style terminal shell.
Here is the basic verovio command to generate 
an SVG image from a Humdrum file:

```bash
verovio file.krn
```
This will create a file called `file.svg` with the graphical
music notation represented in the Humdrum file `file.krn`,
using the default settings.

### Static server-generated images ###

There are several command-line options that can be used to
control formatting of the generated SVG image.  For the following
example SVG image, these options were used:

```bash
verovio input.krn --adjust-page-height -h 2000 -w 1550 --spacing-staff 3 --spacing-system 3 -s 30
```

--adjust-page-height
: shrink the height of the SVG image to  the height of the printed music (remove any blank space below the music).

-h 2000
: set the height of the SVG page to 2000 pixels.

-w 1550
: set the width of the SVG page to 1550 pixels.

--spacing-staff 3
: pad the bottom of each staff with 3 diatonic steps of additional space.

--spacing-system 3
: pad the bottom of each system with 3 diatonic steps of additional space.

-s 30
: scale the music to 30% of full size.

Additional options can be found on the 
[verovio command-line page](http://www.verovio.org/command-line.xhtml).

The resulting SVG image is shown on the right, with the input
Humdrum data shown beside it:

<center>
<table style="border: none; background-color: transparent">
<tr valign="top" style="background-color: transparent">
<td>
<div>
<pre style="width:150px; margin-top:25px; height:345px;" readonly id="myhumdrum">
**kern
*clefF4
*k[b-e-a-]
*M3/4
=1-
(8G\L
8E-\)
(8BBn\
8C\J)
4AA-/
=2
(8c\L
8A-\)
(8En\
8F\J)
4BBn/
=3
(8d\L
8A-\)
(8En\
8F\J)
(8GG\L
8G\J)
=4
(8F\L
8E-\)
(8BBn\
8C\J)
4CC/
=5
(8C\L
8E-\
8A-\)
(8G\
8d-X\
8c\J)
=6
(8D\L
8F\
8B-\)
(8A-\
8c\
8B-\J)
=7
(8A-\L
8G\)
(8D\
8E-\)
(8BB-\
8D\J)
=8
2.EE-/
=9:|!|:
(8B-\L
8G\)
(8D\
8E-\J)
4DD-X/
=10
(8B-\L
8G\)
(8En\
8F\J)
4GG/
=11
(8d-X\L
8B-\)
(8En\
8F\J)
8CC\L
8c\J
=12
(8B-\L
8A-\)
(8En\
8F\J)
4FF/
=13
(8EE-\L
8C\
8F\)
(8E-\
8B-\
8An\J)
=14
(8DD\L
8D\
8G\)
(8F\
8c\
8Bn\J)
=15
(8c\L
8A-\)
(8F#X\
8G\)
8BBn\
8C\J
=16
(8GG\L
8D\)
(8G\
8F#X\)
8c\
8Bn\J
=17
(8e-\L
8c\)
(8F#X\
8G\J)
8AAn\L
8e-\J
=18
(8d\L
8A-X\)
(8En\
8F\J)
8BBn\L
8G\J
=19
(8F\L
8E-\
8BBn\
8C\J)
(8GG\L
8Bn\J)
=20
(8CC/L
8GG/
8F/
8E-/J
4c\)
=:|!
*-
</pre>
</div>

</td>
<td>
<div style="margin-top: -30px">
<img style="width:465px;" src="bwv1011-sarabande.svg"/>
</div>
</td>
</tr>
</table>
</center>


See the [myVHV command-line page](../command_line) for more information
about command-line use of verovio with Humdrum files.


## JavaScript use ##

In addition to being able to run the converter on the command-line,
verovio is also available as a javascript toolkit that allows you
to generate SVG images directly within a webpage.  




### Static browser-generated images ###

The following Humdrum data is used to create the music notation on
the right without the need to store the notation in a separately
loaded image file:

<center>
<table style="padding:0 !important; border: none; background-color: transparent;">
<tr valign="top" style="background-color: transparent; padding:0 !important;">
<td style="padding:0 !important;">
<div>
<pre style="width:150px; margin-top:30px; height:345px;" readonly id="myhumdrum">
**kern
*clefF4
*k[b-e-a-]
*M3/4
=1-
(8G\L
8E-\)
(8BBn\
8C\J)
4AA-/
=2
(8c\L
8A-\)
(8En\
8F\J)
4BBn/
=3
(8d\L
8A-\)
(8En\
8F\J)
(8GG\L
8G\J)
=4
(8F\L
8E-\)
(8BBn\
8C\J)
4CC/
=5
(8C\L
8E-\
8A-\)
(8G\
8d-X\
8c\J)
=6
(8D\L
8F\
8B-\)
(8A-\
8c\
8B-\J)
=7
(8A-\L
8G\)
(8D\
8E-\)
(8BB-\
8D\J)
=8
2.EE-/
=9:|!|:
(8B-\L
8G\)
(8D\
8E-\J)
4DD-X/
=10
(8B-\L
8G\)
(8En\
8F\J)
4GG/
=11
(8d-X\L
8B-\)
(8En\
8F\J)
8CC\L
8c\J
=12
(8B-\L
8A-\)
(8En\
8F\J)
4FF/
=13
(8EE-\L
8C\
8F\)
(8E-\
8B-\
8An\J)
=14
(8DD\L
8D\
8G\)
(8F\
8c\
8Bn\J)
=15
(8c\L
8A-\)
(8F#X\
8G\)
8BBn\
8C\J
=16
(8GG\L
8D\)
(8G\
8F#X\)
8c\
8Bn\J
=17
(8e-\L
8c\)
(8F#X\
8G\J)
8AAn\L
8e-\J
=18
(8d\L
8A-X\)
(8En\
8F\J)
8BBn\L
8G\J
=19
(8F\L
8E-\
8BBn\
8C\J)
(8GG\L
8Bn\J)
=20
(8CC/L
8GG/
8F/
8E-/J
4c\)
=:|!
*-
</pre>
</div>

</td>
<td>
<div style="margin-top:-20px;" id="mynotation">
</div>
</td>
</tr>
</table>
</center>

<script>

var vrvToolkit;

window.addEventListener("DOMContentLoaded", showMyHumdrum);

var options = {
	inputFormat: "humdrum",
	adjustPageHeight: 1,
	pageHeight: 2000,
	pageWidth: 1550,
	scale: 30,
	spacingSystem: 3,
	spacingStaff: 3,
	font: "Leipzig"
};

function showMyHumdrum() {
	vrvToolkit = new verovio.toolkit();
	var myhumdrum = document.querySelector("#myhumdrum");
	if (!myhumdrum) {
		return;
	}
	var location = document.querySelector("#mynotation");
	if (!location) {
		return;
	}

	var svg = vrvToolkit.renderData(myhumdrum.textContent, options);
	location.innerHTML = svg;
	location.style.marginLeft = "20px";
}


</script>

To learn how to generate static SVG images within a
webpage, see [this page](../static).


### Dynamic browser-generated images ###

Using verovio to create static images on webpages is fine, but not
much different from generating the images on the command-line
and loading as an image from the web server.  Here is the same
music as in the above example, but you can now edit the 
Humdrum data and the notation to the right will be updated
immediately by re-converting the changed Humdrum data
into a new SVG image.

{% include verovio.html
	source="dynamic_humdrum"
	pageHeight="2000"
	pageWidth="1550"
	scale="30"
%}
<script  type="text/humdrum" id="dynamic_humdrum">
**kern
*clefF4
*k[b-e-a-]
*M3/4
=1-
(8G\L
8E-\)
(8BBn\
8C\J)
4AA-/
=2
(8c\L
8A-\)
(8En\
8F\J)
4BBn/
=3
(8d\L
8A-\)
(8En\
8F\J)
(8GG\L
8G\J)
=4
(8F\L
8E-\)
(8BBn\
8C\J)
4CC/
=5
(8C\L
8E-\
8A-\)
(8G\
8d-X\
8c\J)
=6
(8D\L
8F\
8B-\)
(8A-\
8c\
8B-\J)
=7
(8A-\L
8G\)
(8D\
8E-\)
(8BB-\
8D\J)
=8
2.EE-/
=9:|!|:
(8B-\L
8G\)
(8D\
8E-\J)
4DD-X/
=10
(8B-\L
8G\)
(8En\
8F\J)
4GG/
=11
(8d-X\L
8B-\)
(8En\
8F\J)
8CC\L
8c\J
=12
(8B-\L
8A-\)
(8En\
8F\J)
4FF/
=13
(8EE-\L
8C\
8F\)
(8E-\
8B-\
8An\J)
=14
(8DD\L
8D\
8G\)
(8F\
8c\
8Bn\J)
=15
(8c\L
8A-\)
(8F#X\
8G\)
8BBn\
8C\J
=16
(8GG\L
8D\)
(8G\
8F#X\)
8c\
8Bn\J
=17
(8e-\L
8c\)
(8F#X\
8G\J)
8AAn\L
8e-\J
=18
(8d\L
8A-X\)
(8En\
8F\J)
8BBn\L
8G\J
=19
(8F\L
8E-\
8BBn\
8C\J)
(8GG\L
8Bn\J)
=20
(8CC/L
8GG/
8F/
8E-/J
4c\)
=:|!
*-
</script>


Try changing the Humdrum data in the above example, such as removing
the key signature, changing to tenor clef (`*clefC4`), or changing
some pitches.  The SVG image on the right should update as you
make changes.
