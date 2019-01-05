---
title: <span class='keypress'>alt-shift-i</span>
lang: en pl
ref: commands-alt-shift-i
author: Craig Stuart Sapp
translator: 
creation_date: 20 May 2018
translation_date: 
last_updated: 20 May 2018
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands layers
summary: "The <span class='keypress'>alt-shift-i</span> command adds an empty interpretation line above the current line in the text editor."
permalink: /commands/alt-shift-i/index.html
---

Pressing <span class="keypress">alt-shift-i</span> will add an empty
interpretation line above the current line, provided that the current
line contains spines (not a global comment, empty line, or exclusive
interpretation line).  The added interpretation line will have the same
number of spine fields as the current line.

After the empty interpretation line has been added, layout commands
can be added (or any other use you have for local comments).  Below
is an example of adding some text in the score through a layout
comment.


{% include image.html
	file="clefchange.gif"
	alt="adding a clef-change."
	max-width="75%"
	caption="Adding a clef change after pressing alt-shift-i."
%}


