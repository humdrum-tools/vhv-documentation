---
title: <span class='keypress'>alt-b</span>
author: Craig Stuart Sapp
creation_date: 9 May 2017
last_updated: 9 May 2017
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands logo 
summary: "The <span class='keypress'>alt-b</span> command toggles display of the Verovio Humdrum Viewer logo in the VHV header."
permalink: /commands/alt-b/index.html
---

Pressing <span class="keypress">alt-b</span> will toggle the
"Verovio Humdrum Viewer" logo in top left corner of the VHV interface:

{% include image.html
	file="altb.gif"
	alt="toggling logo."
	caption="Showing/hiding logo at top of VHV interface."
%}

This is useful for showing complete titles if they are long.


## URL supression of logo ##

The VHV logo can be suppressed when loading a URL, by adding `&k=b` 
to the address:

{% include image.html
	file="altb-url.png"
	alt="toggling logo from URL."
	caption="Hiding the logo through the URL."
%}


Use `?k=b` if there is no `?` already in the URL:


{% include image.html
	file="altb-direct.png"
	alt="toggling logo from URL."
	caption="Hiding the logo through the URL without loading a repertory."
%}





