---
title: MusicXML import
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 6 Mar 2017
last_updated:
ref: interface-musicxml
tags: [all, getting_started]
keywords: interface musicxml
verovio: "true"
summary: "MusicXML files can be dragged/dropped onto the VHV page to automatically convert them into Humdrum data."
sidebar: main_sidebar
permalink: /interface/musicxml/index.html
---

## Drag-and-drop MusicXML files ##

The VHV interface can load MusicXML files by dragging and dropping
them from the desktop onto the VHV page.  The following figure shows
MusicXML data being exported from [MuseScore](http://www.musescore.org)
to the desktop, and then dragging the file onto the browser to load
the file in VHV.

There are two ways of loading a MusicXML file: regular drag-and-drop will
load the MusicXML data directly into the text editor, while holding down the 
<span class="keypress">shift</span> key while drag-and-dropping will 
convert the MusicXML data into Humdrum data, which is then displayed
in the text editor:


{% include image.html
	file="export-import-musicxml.gif"
	alt="MusicXML import example"
	max-width="100%"
	caption="MusicXML file exported from MuseScore, then imported by shift+drag/dropping a file into VHV."
%}

Try downloading the [same MusicXML file](bwv1011-sarabande.xml) and loading it into VHV in a similar manner (usually save by right clicking on the link and then choose *save link as*).

{% include warning.html
	content="MXL (compressed MusicXML) files cannot be loaded directly into VHV.  First unzip the MXL file and then drag-and-drop the resulting MusicXML file (with the extension `.xml`) into VHV, or load the MXL files into a notation editor that understands the MXL format and resave as uncompressed MusicXML."
%}


## Copy/Paste MusicXML data ##

MusicXML data can also be copy/pasted into the VHV text editor.  In this case VHV
behaves like a MusicXML editor, since the data is not converted into the Humdrum format
within the text editor.


The [freeze command](/commands/alt-f) (<span class="keypress">alt-f</span>)
is useful for pausing dynamic notation rendering while editing the
MusicXML data.  MusicXML data loaded in this manner is converted
to Humdrum behind the scenes, but loading the Humdrum data into the
text editor is not yet implemented.  You can, however, [convert to
MEI data](/commands/alt-m) with the <span class="keypress">alt-m</span>
and display in the text editor.


{% include warning.html
	content="The graphical notation editing commands cannot be used when MusicXML data is loaded into the text editor, since these commands operate on Humdrum data only."
%}

## Conversion of MusicXML data into Humdrum ##

If MusicXML data is displayed in the text editor, you can use the
Edit menu option "Convert to Humdrum" to convert the MusicXML data
into Humdrum data, which replaces the MusicXML data in the text editor.


## Embedding tandem interpretations ##

The MusicXML-to-Humdrum converter inside of
[VHV](https://verovio.humdrum.org) will convert text expressions
that start with an asterisk (`*`) into tandem interpretations in
the Humdrum data.  Attach the text expression to the note which
should follow immediately after the tandem interpretation.  Here
is an example of embedding an `*Xtuplet` interpretation to disable
display of tuplet numbers, and later `*tuplet` to turn them
back on:


{% include image.html
	file="musescore-tuplet.png"
	alt="Adding tuplet interpretations in MuseScore"
	max-width="100%"
	caption="Adding text expressions to control tuplet number display style in MuseScore."
%}

This <a target='_blank' href='tuplet.musicxml'>MusicXML file</a> dragged-and-dropped into 
[VHV](https://verovio.humdrum.org) will produce the following Humdrum data that preserves 
the embedded tandem interpretations controlling tuplet number styling.

{% include verovio.html
	source="musescore-tuplet"
	scale="45"
	pageWidth="1200"
	humdrum-min-height="500px"
	tabsize="8"
%}
<script type="application/json" id="musescore-tuplet">
**kern
*clefG2
*k[]
*M4/4
=1
12ccL
12dd
12ccJ
12ddL
12cc
12ddJ
*Xtuplet
12ddL
12ee
12ddJ
12ccL
12dd
12ccJ
=2
12ddL
12cc
12ddJ
*tuplet
12ccL
12dd
12ccJ
12ddL
12cc
12ddJ
12ccL
12ee
12ddJ
==
*-
</script>

### Hiding Humdrum markup text ###

If you do not want to show the Humdrum markup text on PDF output from a music editor,
you can make the text invisible in most editors.  Here is an example of how to make
the text invisible in MuseScore: click on the text and open the inspector panel and then
uncheck the _Visibility_ checkbox:

{% include image.html
	file="musescore-visibility.png"
	alt="Making text invisible inMuseScore"
	max-width="100%"
	caption="Making text expressions invisivle in MuseScore."
%}

Here is the resulting PDF output from MuseScore, where the Humdrum markup is not visible:

{% include image.html
	file="musescore-pdf.png"
	alt="Making text invisible inMuseScore"
	max-width="100%"
	caption="Making text expressions invisivle in MuseScore."
%}

In MuseScore, you can also hide the invisible text in the editor by unselecting
the menu item  View&rarr;Show Invisible.


### Another example ###


Here is another example that embeds note-coloring markers in MuseScore:


{% include image.html
	file="musescore-color.png"
	alt="Adding tuplet interpretations in MuseScore for coloring notes"
	max-width="100%"
	caption="Adding text expressions to control note colors."
%}

If you drag-and-drop <a target="_blank" href="color.musicxml">this MusicXML data</a>, the conversion
to Humdrum will look and display like this in [VHV](https://verovio.humdrum.org):

{% include verovio.html
	source="musescore-color"
	scale="45"
	pageWidth="1200"
	humdrum-min-height="500px"
	tabsize="8"
%}
<script type="application/json" id="musescore-color">
**kern
*clefG2
*k[]
*M4/4
=1
4cc
4ee
*color:hotpink
4dd
4ff
=2
2gg
2aa
=3
*color:dodgerblue
2gg
2ff
=4
4gg
4ff
*color:black
4cc
4dd
==
*-
</script>


### Adding interpretations after notes ###

When tandem interpretations are attached to notes or rests as text
expressions, they will be inserted before the note in the converted
Humdrum data.  To place interpretations after a note, use two
asterisks (`**`) instead of one.  The second asterisk will be removed
automatically (since this is reserved for exclusive interpretations).
This method of inserting after notes is needed when adding
interpretations at the end of a measure, since music editors typically
cannot attach text expressions to barlines.

Here is an example of encoding a ligature bracket in MuseScore.  The ending note of the ligature occurs
at the end of the measure, and since the text expression `*Xlig` cannot be attached to the barline,
it is encoded as `**Xlig` on the last note of the ligature group:

{% include image.html
	file="musescore-ligature.png"
	alt="Adding ligature interpretations in MuseScore"
	max-width="100%"
	caption="Adding text expressions in MuseScore to display a ligature bracket."
%}


If you drag-and-drop <a target="_blank" href="ligature.musicxml">this MusicXML data</a>, the conversion
to Humdrum will look and display like this in VHV:

{% include verovio.html
	source="musescore-ligature"
	scale="45"
	pageWidth="1200"
	humdrum-min-height="375px"
	tabsize="8"
%}
<script type="application/json" id="musescore-ligature">
**kern
*clefC3
*k[]
*M2/1
=1
1d
1B
=2
*lig
0c
=3
0d
*Xlig
=4
2e
2d
1B
=5
0c
==
*-
</script>





## Embedding local comments ##


Likewise, local comments (starting with `!`) can be embedded within the MusicXML data to be 
converted into Humdrum data when you drag-and-drop the file onto [VHV](https://verovio.humdrum.org).

{% include image.html
	file="musescore-comment.png"
	alt="Adding local comments in MuseScore"
	max-width="100%"
	caption="Adding embedded local comments in MuseScore."
%}

If you drag-and-drop <a target="_blank" href="comment.musicxml">this MusicXML data</a>, the conversion
to Humdrum will look and display like this in [VHV](https://verovio.humdrum.org):

{% include verovio.html
	source="musescore-comment"
	scale="45"
	pageWidth="1200"
	humdrum-min-height="500px"
	tabsize="8"
%}
<script type="application/json" id="musescore-comment">
**kern
*clefG2
*k[]
*M4/4
=1
4cc
!LO:TX:a:t=text
4ee
4dd
4ff
=2
!LO:TX:b:t=text2:color=red
2gg
2aa
=3
!comment
2gg
2ff
=4
!LO:N:vis=1
4gg
4ff
4cc
4dd
==
*-
</script>

Notice that any MusicXML text expressions starting with `!` will be converted to local comments
in the Humdrum data.  The comments can also be layout parameters, such as in the above example
where `!LO:N:vis=1` means that the quarter note has a visual whole-note duration.  The `!comment` 
is a regular local comment that will not be printed in the score.  Text to display in the score can
either be a plain text expression that does not start with `*` or `!`, and otherwise text can be placed 
in a `TX` layout command to add specific parameters to the text rendering in VHV.

## Embedding reference records ##


Reference records can be inserted a text comment starting with three `!!!` anywhere in the score.  To
insert reference records at the top of a Humdrum file, add them to the title area in a score editor:


{% include image.html
	file="musescore-reference.png"
	alt="Adding reference records in MuseScore"
	max-width="100%"
	caption="Adding embedded reference records in MuseScore."
%}


Note that in this example embedding of reference records, the text is made invisible in the MuseScore
editor by unchecking the Visible check box in the Inspector panel on the right.  This allows embedding 
Humdrum markup (including tandem interpretation and local comments) in the score editor, but prevent them
from being visible in the PDF printout of the notation from MuseScore.

If you drag-and-drop <a target="_blank" href="reference.musicxml">this MusicXML data</a>, the conversion
to Humdrum will look and display like this in VHV:

{% include verovio.html
	source="musescore-reference"
	scale="45"
	pageWidth="1200"
	humdrum-min-height="525px"
	humdrum-min-width="325px"
	tabsize="8"
%}
<script type="application/json" id="musescore-reference">
!!!COM: Composer's name
!!!CDT: Composer's dates
!!!CNT: Composer's nationality
!!!OTL: Composition title
!!!OMV: Movement 1
!!!ODT: Composition date
!!!LYR: Lyricist's name
!!!header-left: @{LYR}\n
!!!header-center: @{OTL}\n&lt;i&gt;@{OMV}&lt;/i&gt;
!!!header-right: @{COM}\n@{CDT}
**kern
*clefG2
*k[]
*M4/4
=1
1g
=2
1a
=3
2b
4b
4g
=4
4g
4b
2b
==
*-
</script>

If the MusicXML score contains the composer's name and title in the standard encoding for a MusicXML file,
they will automatically be converted into `!!!COM:` and `!!!OTL:` reference records, but if explicit `!!!COM:` 
and `!!!OTL:` entries are added to the file header, they will override the inferred composer's name and work
title.

Also note in this example a demonstration of the header templating system is given:


```
!!!header-left: @{LYR}\n
!!!header-center: @{OTL}\n<i>@{OMV}</i>
!!!header-right: @{COM}\n@{CDT}
```

This allows for various reference records to be displayed at the top of the score in the left, right
and middle of the header.  The `\n` character sequence represents a line break.  There is also a footer
templating system, which is useful for printing to PDF from VHV 
(with the <span class="keypress">alt-shift-T</span> keyboard shortcut).


### Reference record placement ###

An additional system for embedding reference records in the MusicXML header allows for 
placement of the records at the start or end of the file.  Replace `!!!` with `@` to indicate that a 
reference record should be placed at the top of the file, while replacing `!!!` with `@@` will cause
the reference record to be added at the bottom of the file:


{% include image.html
	file="musescore-reference2.png"
	alt="Adding reference records in MuseScore"
	max-width="100%"
	caption="Alternate system for embedding reference records in MuseScore with above/below controls."
%}

If you drag-and-drop <a target="_blank" href="reference2.musicxml">this MusicXML data</a>, the conversion
to Humdrum will look and display like this in VHV:

{% include verovio.html
	source="musescore-reference2"
	scale="45"
	pageWidth="1200"
	humdrum-min-height="525px"
	humdrum-min-width="325px"
	tabsize="8"
%}
<script type="application/json" id="musescore-reference2">
!!!COM: Composer's name
!!!OTL: Composition title
!!!OMV: Movement 1
**kern
*clefG2
*k[]
*M4/4
=1
1g
=2
1a
=3
2b
4b
4g
=4
4g
4b
2b
==
*-
!!!CDT: Composer's dates
!!!CNT: Composer's nationality
!!!ODT: Composition date
!!!LYR: Lyricist's name
!!!header-left: @{LYR}\n
!!!header-center: @{OTL}\n&lt;i&gt;@{OMV}&lt;/i&gt;
!!!header-right: @{COM}\n@{CDT}
</script>



## Batch conversion from MusicXML to Humdrum ##

If you want to convert many MusicXML files into Humdrum at once,
you can use the _musicxml2hum_ command-line tool from <a target="_blank"
href="https://humlib.humdrum.org">humlib</a>, which is the same as
the MusicXML-to-Humdrum converter built into
[VHV](https://verovio.humdrum.org).  To convert multiple MusicXML
files in a directory to Humdrum using the bash shell:

```bash
for i in *.xml
do
	echo Converting $i
	musicxml2hum $i > $(basename $i .xml).krn
done
```


{% include warning.html
	content="There is a tool in Humdrum Extras called _xml2hum_, but _musicxml2hum_ in humlib is a more advanced and more recent converter from MusicXML into Humdrum."
%}


