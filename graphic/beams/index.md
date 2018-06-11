---
title: Beams
lang: en
ref: graphic-beams
author: Craig Stuart Sapp
creation_date: 1 Jun 2018
last_updated: 1 Jun 2018
tags: [all, graphic_editing, RDF]
sidebar: main_sidebar
datatable: "true"
vim: ts=3
keywords: graphic editing beams
summary: Graphically splitting beams in the notation editor.
permalink: /graphic/beams/index.html
---

## Key command summary ##

{% include keytable.html
	contentId="beamkeysummary"
%}
<script type="text/JSON" id="beamkeysummary">
{% include keypresses/beamkeys.json %}
</script>


## <span class="keypress">L</span>: Splitting beam before current note ##

When editing a note/chord/rest inside of a beam, type 
<span class="keypress">shift-L</span> to split the beam between the 
current note and the previous note.

{% include image.html
	file="lcommand.gif"
	alt="breaking beams with the L command."
	max-width="75%"
	caption="Breaking beams with the `L` command."
%}

## <span class="keypress">J</span>: Splitting beam after current note ##

When editing a note/chord/rest inside of a beam, type 
<span class="keypress">shift-J</span> to split the beam between the 
current note and the next note.

{% include image.html
	file="jcommand.gif"
	alt="breaking beams with the J command."
	max-width="75%"
	caption="Breaking beams with the `J` command."
%}


