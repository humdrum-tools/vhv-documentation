---
title: MEI export
author: Craig Stuart Sapp
creation_date: 9 Mar 2017
last_updated: 9 Mar 2017
tags: [all, getting_started]
keywords: interface mei
summary: "MEI files can be generated from Humdrum data and saved to the local file-system."
sidebar: mydoc_sidebar
permalink: /interface/mei/index.html
---

## Viewing MEI data in the text editor ##

VHV dynamically converts Humdrum data into MEI data in order to produce
graphical music notation.  The conversion to MEI is usually done
behind the scenes, but this data can be viewed in the text editor
by pressing <span class="keypress">alt-m</span>.  To return
to the Humdrum-data view press <span class="keypress">alt-h</span>.

{% include image.html
	file="mei-humdrum-toggle.gif"
	alt="MEI / humdrum toggle example"
	caption="Humdrum data converted into MEI with <span class=',eypress'>alt-m</span> and then back again to Humdrum with <span class=',eypress'>alt-h</span>."
%}

The MEI data can be edited, and the notation editor contents will
be updated to reflect the changes ([<span class='keypress'>alt-f</span>](/commands/alt-f) may be useful when editing the MEI data).  You can click on a note in the
notation editor, and the corresponding MEI element for the note
will come into view; however, graphic editing commands will not
work with MEI data.


{% include warning.html
	content=" Going back to the Humdrum view with the <span class='keypress'>alt-h</span> command will cause any changes in the MEI data to be lost."
%}

### Export by copy-and-paste ###

MEI data can be selected in the text editor and copy-and-pasted into
another text editor in the operating system; otherwise, the next section
describes how to save the MEI data to a local file.

## Downloading MEI files ##

While viewing MEI data in the text editor, type
<span class="keypress">alt-s</span> to save the context of the
text editor to a file called `data.txt`.  The file will be saved wherever
your browser saves files, such as in **Documents**.

Below is a demonstration of converting Humdrum data into MEI data
by pressing
<span class="keypress">alt-m</span>
and then saving it so a file on the local disk with the
<span class="keypress">alt-s</span> keypress:

{% include image.html
	file="mei-save.gif"
	alt="MEI save example"
	max-width="100%"
	caption="MEI content displayed with <span class='keypress'>alt-m</span> and then saved with <span class='keypress'>alt-s</span>."
%}


## Loading MEI files by drag-and-drop ##

The VHV interface can load MEI files by dragging and dropping them from the desktop
onto the VHV page:

{% include image.html
	file="mei-import.gif"
	alt="MEI import example"
	max-width="100%"
	caption="MEI file imported by drag-and-drop into VHVV."
%}

Try downloading the [same MEI file](bwv1011-sarabande.mei) and
loading it into VHV in a similar manner (usually save by right-clicking 
on the link and then choose *save link as*).


{% include warning.html
	content="The graphical notation editing commands cannot be used when MEI data is loaded into the text editor since these commands operate on Humdrum data only."
%}

## Copy-and-paste MEI data into text-editor ##

MEI data can be copy-and-pasted from another source into the VHV
text editor.  Notation will be generated dynamically from the MEI
data and will be updated as the MEI content is changed, but typing
<span="keypress">alt-h</span> will not convert the MEI data into
Humdrum data.






