---
title: Interface overview
keywords: interface commands documentation 
last_updated: 3 Mar 2017
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
	shadow="-12px 12px 60px #888"
	caption-margin-left="40px"
	margin-left="55px"
%}

The current note being edited in the text editor will be highlighted
in red in the notation view.  Don't forget to end a spine with data
termination token `*-`; otherwise, the Humdrum file will not be
valid.  The VHV interface adds one automatically so that you can
see the music while entering data.


You can click and drag the divider between the text and notation regions
as demonstrated in the following animation.  There is also a keyboard shortcut 
for hiding/showing the text editor by typing "alt-y".

{% include image.html
	file="interface/slidewindow.gif"
	url="http://verovio.humdrum.org"
	alt="Moving divider between text editor and notation editor"
	caption="Moving divider between text editor and notation editor (press alt-y totoggle display of text editor."
	shadow="-12px 12px 60px #888"
	margin-left="55px"
	caption-margin-left="40px"
%}


