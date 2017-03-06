---
title: <span class='keypress'>alt-m</span>
author: Craig Stuart Sapp
creation_date: 5 Mar 2017
last_updated: 5 Mar 2017
tags: [commands]
sidebar: mydoc_sidebar
keywords: interface commands 
summary: "The <span class='keypress'>alt-m</span> command displays the MEI data conversion in the text editor."
permalink: /commands/alt-m/index.html
---

Pressing <span class="keypress">alt-m</span> will replace Humdrum
data in the text editor with its conversion to MEI data.  The MEI
data is usually generated behind the scenes in the process of
converting Humdrum data into SVG images of music notation in VHV.

While MEI data is being displayed in the text editor, it can be
edited and any changes will be reflected in the graphical notation
window.  In addition, clicking on objects in the notation will cause
the text editor cursor to move to the parallel element in the MEI
data; however, graphic editing commands will not work with the MEI
data.

You can return the original Humdrum data to the text editor by
pressing <span class="keypress">alt-h</span>, but any changes made
to the MEI data will be lost.  Here is an example of typing Humdrum
data into the text editor, and then typing <span
class="keypress">alt-m</span> to view the transcoded MEI data:

{% include image.html
	file="mei-data.gif"
	alt="viewing MEI data."
	caption="Switching the text editor to MEI mode after typing some Humdrum data."
%}



