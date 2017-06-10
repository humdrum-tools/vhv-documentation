---
title: EsAC data import
author: Craig Stuart Sapp
creation_date: 10 Jun 2017
last_updated: 10 Jun 2017
tags: [all, getting_started]
keywords: interface esac
summary: "EsAC files can be dragged/dropped onto the VHV page to automatically convert them into Humdrum data, or EsAC data can be pasted into the text editor to edit as EsAC data."
sidebar: main_sidebar
permalink: /interface/esac/index.html
---

## Drag-and-drop EsAC files ##

The VHV interface can load EsAC files by dragging and dropping them
from the desktop onto the VHV page.  The following figure shows an
EsAC data file being dragging from the desktop to the browser,
loading the file in VHV:

{% include image.html
	file="import-esac.gif"
	alt="EsAC import example"
	max-width="100%"
	caption="EsAC data imported by drag/drop into VHVV."
%}

Try downloading the [same EsAC file](b0029.txt) and loading it into VHV in a similar manner (usually save by right clicking on the link and then choose *save link as*).


## Copy/Paste EsAC data ##

EsAC data can also be copy/pasted into the VHV text editor.  In this case VHV
behaves like a EsAC editor, since the data is not converted into the Humdrum format
within the text editor:

{% include image.html
	file="paste-esac.gif"
	alt="EsAC data pasting example"
	max-width="100%"
	caption="EsAC data pasted into VHVV."
%}


The [freeze command](/commands/alt-f) (<span class="keypress">alt-f</span>) 
is useful for pausing dynamic notation rendering while editing the EsAC data.
Sometimes invalid content will currently cause problems if not using the
freeze command while editing.

### Humdrum Filters in EsAC ###

Humdrum filters can be used in the EsAC data.  Here is a demonstration
of adding the *autobeam* filter to automatically beam notes by the time signature.

{% include image.html
	file="autobeam-esac.gif"
	alt="EsAC autobeam filtering example"
	max-width="100%"
	caption="EsAC data with Humdrum autobeam filter applied."
%}

### Saving EsAC data ###

EsAC data visible in the text editor can be downloaded with the
<span class="keypress">alt-s</span> key combination. The file will be
saved wherever your browser downloads files.

Also, the contents of the text editor can be copy/pasted into another text editor.


{% include warning.html
	content="The graphical notation editing commands cannot be used when EsAC data is loaded into the text editor, since these commands operate on Humdrum data only."
%}



