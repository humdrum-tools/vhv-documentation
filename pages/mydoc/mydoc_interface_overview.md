---
title: Interface overview
keywords: interface commands documentation 
last_updated: 2 March 2017
tags: [getting_started]
summary: "Tutorial on the main parts of the VHV interface."
sidebar: mydoc_sidebar
permalink: mydoc_interface_overview.html
folder: mydoc
---

The [VHV interface](http://verovio.humdrum.org) is organized into two main components: a 
text editor on the left and a music-notation editor on the right:

{% include image.html
	file="interface/mainwindow.png"
	url="http://verovio.humdrum.org"
	alt="VHV main page"
	caption="Text editor on the left and notation editor on the right"
	caption-margin-top="-80px"
	caption-margin-left="40px"
%}

As you type Humdrum data into the text editor, it will be converted
dynamically into music notation on the right:


{% include image.html
	file="interface/twinkle.gif"
	url="http://verovio.humdrum.org"
	alt="Entering data into the text editor"
	caption="Notation is generated as data is typed into the text editor."
	margin-left="400px"
%}

The current note being edited in the text editor will be highlighted
in red in the notation view.  Don't forget to end a spine with data
termination token `*-`; otherwise, the Humdrum file will not be
valid.  The VHV interface adds one automatically so that you can
see the music while entering data.


