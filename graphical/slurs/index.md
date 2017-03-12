---
title: Slurs
author: Craig Stuart Sapp
creation_date: 5 Mar 2017
last_updated: 7 Mar 2017
tags: [all, graphical_editing, RDF]
sidebar: mydoc_sidebar
datatable: true
keywords: graphical editing slurs
summary: "Graphically adding and editing slurs."
permalink: /graphical/slurs/index.html
---

## Key command summary ##

<script>

var columns = [
	{ data: "group", title: "Group"},
	{ data: "keys", title: "Key(s)" },
	{ data: "action", title: "Action"}
];

var data = [

	{
		group: "adding a slur to a note",
		keys: "<span class='keypress'>s</span>",
		action: "Add a slur to the next note"
	},

	{
		group: "adding a slur to a note",
		keys: "<span class='keypress'>2+s</span>",
		action: "Add slur starting on current note and including next two notes"
	},

	{
		group: "adding a slur to a note",
		keys: "<span class='keypress'>9+s</span>",
		action: "Add slur starting on current note and including next nine notes"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>a</span>",
		action: "force slur above notes"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>b</span>",
		action: "force slur below notes"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>c</span>",
		action: "clear forced slur direction"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>left</span>",
		action: "move slur start one note to the left"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>right</span>",
		action: "move slur start one note to the right"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>shift-left</span>",
		action: "move slur end one note to the left"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>shift-right</span>",
		action: "move slur end one note to the right"
	},

	{
		group: "editing slurs",
		keys: "<span class='keypress'>escape</span>",
		action: "deselect the slur"
	},

];
</script>

{% include keycommandsummary.html
	tableId="pitchkeysummary"
%}






## <span class="keypress">s</span>: Adding a simple slur ##

After clicking on a note in the notation editor, press
the <span class="keypress">s</span> key to add a slur to the next note:

{% include image.html
	file="add-slurs.gif"
	alt="adding slurs to the notation"
	max-width="75%"
	caption="Type <span class='keypress'>s</span> after selecting a note to add a slur."
%}

Notice that a pair of parentheses to mark the start and end of the
slur are added to the Humdrum data in the text editor on the left
as the slurs appear in the notation.

After adding the slur, focus shifts to the slur, which will be highlighted
in red, to allow for further editing of the slur.

## <span class="keypress">a</span>, <span class="keypress">b</span>, <span class="keypress">c</span>: Slur orientation ##

Slurs can be forced above or below the notes by using the <span
class="keypress">a</span> key to force *above* or <span
class="keypress">b</span> to force *below*.  These two commands
will be searched for in the Humdrum data as an RDF line in the form:

```humdrum
!!!RDF**kern: > = above
!!!RDF**kern: < = below
```

These two RDF signifiers, which could be assigned to other characters
(although "`<`" and "`>`" are typically used), are used to
indicate a forced direction on many graphical elements including
slurs.  If `above`/`below` signifiers are not found in the data
they will automatically be added the first time a forced direction
command is given.  You can remove a forced direction by typing <span
class="keypress">c</span> to *clear* it.

{% include image.html
	file="slur-orientation.gif"
	alt="adding slurs to the notation"
	caption="Type <span class='keypress'>a</span> to force slurs above, 
	              <span class='keypress'>b</span> to force slurs below, and
	              <span class='keypress'>c</span> to clear forced directions."
%}

## <span class="keypress meta">#</span> <span class="keypress">s</span>: Adding extended slurs ##

Typing <span class="keypress">s</span> while editing a note will
add a slur to the next note; however, the slur can be extended as
it is created by typing a digit from <span class="keypress">2</span>
through <span class="keypress">9</span> to extend from two to nine
notes after the current note.


{% include image.html
	file="add-long-slur.gif"
	alt="adding long slurs to the notation"
	max-width="75%"
	caption="adding long slurs by typing a digit before <span class='keypress'>s</span>."
%}

## Moving slurs ##

Once a slur has been added to the notation, it can be moved around by pressing
<span class="keypress">&larr;</span>/<span class="keypress">&rarr;</span>
to move the beginning of the slur forward or backward in the music, or
<span class="keypress">shift-left</span>/<span class="keypress">shift-left</span>
to move the ending of the slur.


{% include image.html
	file="move-slurs.gif"
	alt="moving slurs after they are created"
	max-width="75%"
	caption="Moving slurs after they are created."
%}

{% include note.html
	content="While editing a slur, the <span class='keypress'>&larr;</span>/<span class='keypress'>&rarr;</span> keys are not available for their usual functions to move to the next/previous page.  To move to a new page with the arrow keys, press the <span class='keypress'>esc</span> key to deselect the slur."
%}



