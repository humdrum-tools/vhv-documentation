---
title: User Interface overview
author: Craig Stuart Sapp
keywords: interface commands documentation 
creation_date: 3 Mar 2017
last_updated: 3 Mar 2017
tags: [all, getting_started]
summary: "Description of the two sub-windows in the VHV interface."
sidebar: mydoc_sidebar
url: /interface/getting_started/index.html
permalink: /interface/getting_started/index.html
---

[VHV](http://verovio.humdrum.org) is organized into two main components: a 
text editor on the left and a music-notation editor on the right:


{% include image.html
	file="mainwindow.png"
	url="http://verovio.humdrum.org"
	alt="VHV main page"
	caption="Text editor on the left and notation editor on the right"
	margin-bottom="-20px"
%}

Humdrum data typed into the text editor converts
dynamically into music notation:


{% include image.html
	file="twinkle.gif"
	alt="Entering data into the text editor"
	caption="Notation is generated as data is typed into the text editor."
%}

The current note being edited in the text editor is highlighted
in red in the notation view.  Don't forget to end a spine with data
termination token `*-`; otherwise, the Humdrum file will not be
valid.  The VHV interface adds one automatically so that you can
see the music while entering data.


You can click and drag the divider between the text and notation regions
as demonstrated in the following animation.  There is also a keyboard shortcut 
for hiding/showing the text editor by typing <kbd>alt</kbd>+<kbd>y</kbd>.

{% include image.html
	file="slidewindow.gif"
	alt="Moving divider between text editor and notation editor"
	caption="Moving divider between text editor and notation editor<br>(press <kbd>alt</kbd>+<kbd>y</kbd> to toggle display of text editor)."
%}


See the [getting started index page](/tag_getting_started.html) and in particular a description of
the [help menu](/interface/help_menu) for more basic information about VHV.  Also see the
[Humdurm load/save page](/interface/humdrum) for more ways of loading Humdrum data into VHV other
than typing it in by hand.

