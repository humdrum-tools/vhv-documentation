---
title: Marking notes with <span class='keypress'>at</span>
author: Craig Stuart Sapp
creation_date: 15 Mar 2017
last_updated: 15 Mar 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands 
summary: The <span class='keypress'>at</span> command highlights notes in the notation edtior and adds a mark signifier to the note's data token in the text editor.
permalink: /graphic/marks/index.html
---

Pressing <span class="keypress">@</span> while a note is selected
will mark the note with a user-signifier based on the last RDF line in the 
Humdrum data with a form such as:

```
!!!RDF**kern: @ = marked note
```

If there is no marked-note RDF definition in the Humdrum data, one will be 
added automatically to the end of the data.  Here is an example of 
marking notes in the notation, which adds `@` to the note tokens in the
Humdrum data.

{% include image.html
	file="mark-notes.gif"
	alt="marking notes in grahpic notation editor."
	caption="Marking notes with <span class='keypress'>@</span> in the notation editor."
%}


## Changing mark colors ##

The default color for marked notes in VHV notation is red.  If you want
to use another color, a color parameter can be added to the RDF:

{% include image.html
	file="magenta-turquoise.gif"
	alt="marking notes in grahpic notation editor in different colors."
	caption="Changing the color of marked notes."
%}

The color parameter value should be enclosed in quotes if it contains
spaces, but otherwise the quotes are optional.  Colors can be

[named colors](https://www.w3schools.com/cssref/css_colors.asp) as well as
`transparent`, or any [numeric format recognized by SVG](https://www.w3schools.com/cssref/css_colors_legal.asp): 3/6 digit hexadecimal colors, RGB colors,
RGBA colors, HSL colors, or HSLA colors.  Examples:

{% include image.html
	file="hex-c03da2.png"
	alt="example of hex color."
	caption="Example of hex color \"#c03da2\"."
%}


The same color in `rgb` format:

{% include image.html
	file="rgb-192-61-162.png"
	alt="example of hex color."
	caption="Example of rgb color \"rgb(192,61,162)\"."
%}


Adding 50% opacity to the same color in `rgba` format:

{% include image.html
	file="rgb-192-61-162-05.png"
	alt="example of hex color."
	caption="Example of rgb color \"rgb(192,61,162,0.5)\"."
%}

## Multiple marks ##

Any number of RDF marks can be given in the data.  The last mark RDF in
the data will be the one that the <span class="keypress">at</span> 
command will use to mark notes:

{% include image.html
	file="second-mark.gif"
	alt="example of two mark colors."
	caption="Example second mark (<span style='color:coral;'>coral</span> colored notes)."
%}

In this case there are two RDF marking lines:

```
!!!RDF**kern: @ = marked note color=turquoise
!!!RDF**kern: N = marked note color=coral
```

Since the last one uses `N` for the mark, typing
<span class="keypress">at</span> will add the character `N` to 
the marked note tokens instead of `@`.


## Meaning of the mark ##

RDF records are free-form texts, so you can add your own text to the line which explains the meaning of the mark.


```
!!!RDF**kern: @ = marked note color="orchid" strange note
```

If you want a more formalized system, then use `meaning="..."`:

```
!!!RDF**kern: @ = marked note color="orchid" meaning="strange note"
```

This parameter does not yet have any meaning in VHV itself yet, 
but perhaps it could be mapped to a tooltip on the note in the future.



