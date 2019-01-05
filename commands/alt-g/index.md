---
title: <span class='keypress'>alt-g</span>
lang: en pl
ref: commands-alt-g
author: Craig Stuart Sapp
translator: 
creation_date: 23 Apr 2017
translation_date: 
last_updated: 23 Apr 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands svg
summary: The <span class='keypress'>alt-g</span> command displays SVG code for the graphical music seen in the notation editor. 
permalink: /commands/alt-g/index.html
---

Pressing <span class="keypress">alt-g</span> will cause a new window
to open up containing the SVG code for the currently visible page
of music notation.  Here is an example of the feature in action:

{% include image.html
	file="show-svg.gif"
	alt="show SVG code for graphic notation."
	max-width="50%"
	caption="Pressing <span class='keypress'>alt-g</span> will open up the SVG code for the current page of notation."
%}


[Here](sample.svg) is the SVG image extracted as in the above figure 
after it has been saved to a file.
The SVG code can then be copy/pasted into a text editor and saved
to the hard disk.  This command is useful for extracting a musical
example for use as a static image in a paper/article or website.


## Converting notation into bitmap images ##

Many applications (such as MS Word) cannot load SVG image files, so
the SVG data must be converted into a bitmap in order to use the
image in such programs.  There are two ways of generating bitmaps
of VHV notation:  a simple method is to do a screen-shot.  How to
do this will be different in the various operating systems.  In
MacOS, type <span class="keypress">command-shift-4</span> and then
drawing a box around the notation you want to capture.  You may
also want to type <span class="keypress">alt-f</span> first so that
the background color of the notation is white.

{% include image.html
	file="screenshot.gif"
	alt="Capturing screenshot of notation"
	max-width="100%"
	caption="Taking a screenshot of the displayed notation."
%}

A more refined method of extracting a bitmap for a full page can be done by saving the
SVG image displayed by the <span class="keypress">alt-g</span>
command and then opening in [GIMP](https://www.gimp.org).  Here is the SVG import
dialog window when opening the SVG image in GIMP:

{% include image.html
	file="svgopen.png"
	alt="Loading SVG into GIMP"
	max-width="50%"
	caption="Options window when opening SVG in GIMP."
%}

Set the pixel width/height to a large number (such as about 2000 pixels wide)
to generate a high-resolution bitmap from the SVG image.  Here is an example
of the image loaded into GIMP:

{% include image.html
	file="ingimp.png"
	alt="Loading SVG into GIMP"
	max-width="80%"
	caption="Options window when opening SVG in GIMP."
%}

The checkered gray background indicates that the image is transparent.  This 
is useful when displaying the bitmap on a colored background.  You can then save
the image, or select-all/copy/paste it into another application such as MS Word:

{% include image.html
	file="msword.png"
	alt="From GIMP to MS Word"
	max-width="60%"
	caption="Result of copy/pasting from GIMP to MS Word."
%}


## Editing as a vector-graphics image ##

If you want to preserve the vector-graphics format of the SVG image, but want
to edit to make changes or additions (such as analysis markup with boxes or
arrows, etc.), then use [Inkscape](https://inkscape.org/en), which is a free
open-source vector-graphics editor.

{% include image.html
	file="inkscape.png"
	alt="in Inkscape"
	max-width="80%"
	caption="Loading extracted SVG into Inkscape and adding markup."
%}

From Inkscape, you can save to the [Enhanced Metafile format](https://en.wikipedia.org/wiki/Windows_Metafile) which is an old Microsoft vector-graphics format that can be
loaded into MS Word.  Note in the following figure that transparencies and layering 
of markup in Inkscape might not export well to the EMF format:

{% include image.html
	file="emfword.png"
	alt="EMF loaded into Word"
	max-width="60%"
	caption="Loading an EMF file into MS Word that was saved from Inkscape."
%}


Here is an example of saving the edited image as an SVG again ([sample2.svg](sample2.svg))
 and then loading into a web browser:

{% include image.html
	file="svgchrome.png"
	alt="Inkscape image loaded into Chrome"
	max-width="60%"
	caption="Loading an SVG file into Google Chrome that was saved from Inkscape."
%}





