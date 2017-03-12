---
title: MusicXML import
author: Craig Stuart Sapp
creation_date: 6 Mar 2017
last_updated: 6 Mar 2017
tags: [all, getting_started]
keywords: interface musicxml
summary: "MusicXML files can be dragged/dropped onto the VHV page to automatically convert them into Humdrum data."
sidebar: mydoc_sidebar
permalink: /interface/musicxml/index.html
---

## Drag-and-drop MusicXML files ##

The VHV interface can load MusicXML files by dragging and dropping them from the desktop
onto the VHV page.  The following figure shows MusicXML data being exported from
[MuseScore](http://www.musescore.org) to the desktop, and then dragging the file onto
the browser to load the file in VHV:


{% include image.html
	file="export-import-musicxml.gif"
	alt="MusicXML import example"
	max-width="100%"
	caption="MusicXML file exported from MuseScore, then imported by drag/drop file into VHVV."
%}

Try downloading the [same MusicXML file](bwv1011-sarabande.xml) and loading it into VHV in a similar manner (usually save by right clicking on the link and then choose *save link as*).

{% include warning.html
	content="MXL (compressed MusicXML) files cannot be loaded directly into VHV.  First unzip the MXL file and then drag-and-drop the resulting MusicXML file (with the extension `.xml`) into VHV, or load the MXL files into a notation editor that understands the MXL format and resave as MusicXML."
%}

{% include note.html
	content="MusicXML file conversions include a `**recip` spine in the first column.  An explantion or method for removing this spine will be added later."

%}



## Copy/Paste MusicXML data ##

MusicXML data can also be copy/pasted into the VHV text editor.  In this case VHV
behaves like a MusicXML editor, since the data is not converted into the Humdrum format
within the text editor.


The [freeze command](/commands/alt-f) is useful for pausing dynamic
notation rendering while editing the MusicXML data.  MusicXML data
loaded in this manner is converted to Humdrum behind the scenes,
but loading the Humdrum data into the text editor is not yet
implemented.  You can, however, [convert to MEI data](/commands/alt-m)
with the <span class="keypress">alt-m</span> and display in the text editor.


{% include warning.html
	content="The graphical notation editing commands cannot be used when MusicXML data is loaded into the text editor, since these commands operate on Humdrum data only."
%}





