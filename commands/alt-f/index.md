---
title: <span class='keypress'>alt-f</span>
lang: en es pl
page_language: en
author: Craig Stuart Sapp
creation_date: 5 Mar 2017
last_updated:
ref: commands-alt-f
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands freeze notation
summary: "The <span class='keypress'>alt-f</span> command toggles freezing/unfreezing dynamic notation rendering."
permalink: /commands/alt-f/index.html
---

Pressing <span class="keypress">alt-f</span> will toggle between
freezing/unfreezing dynamic notation rendering.  Normally any change
in the text editor's content will trigger a re-rendering of the
graphical notation.  For large files, this takes an increasingly
longer and longer time with the current architecture.  In order to
speed up data entry in the text editing window, the notation can
be frozen with the <span class="keypress">alt-f</span> command.

While the notation generation is frozen, any changes made in the text
editor will not trigger an update in the notation.  After changes have been
made, pressing <span class="keypress">alt-f</span> will unfreeze the notation
and it will be updated to match the current contents of the text editor.

When the notation is frozen, the background of the notation turns white.  Unfreezing
the notation will return the background color to off-white:

{% include image.html
	file="freeze-unfreeze.gif"
	alt="freezing and unfreezing notation."
	caption="Freezing and unfreezing notation while typing in the text editor."
%}




