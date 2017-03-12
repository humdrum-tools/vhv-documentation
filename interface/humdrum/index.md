---
title: Load/Save Humdrum data
author: Craig Stuart Sapp
creation_date: 6 Mar 2017
last_updated: 6 Mar 2017
tags: [all, getting_started, humdrum]
keywords: interface humdrum load save import export
summary: "Humdrum data can be loaded or saved in multiple ways."
sidebar: mydoc_sidebar
permalink: /interface/humdrum/index.html
---

## Drag-and-drop Humdrum files into VHV ##

The VHV interface can load Humdrum files by dragging and dropping a file
icon from the operating system onto the VHV page:

{% include image.html
	file="drag-drop-humdrum.gif"
	alt="Humdrum file import example"
	max-width="100%"
	caption="Humdrum file loaded by drag-and-drop into VHVV."
%}

Try downloading the [same Humdrum file](data.txt) used in the figure
above, and load it into VHV in a similar manner (usually save in a
web browser by right-clicking on the link and then choose *save
link as*).

## Copy-and-paste Humdrum data ##

Humdrum data can also be pasted directly into the VHV text editor:

{% include image.html
	file="copy-paste-humdrum.gif"
	alt="Humdrum file copy/paste example"
	max-width="100%"
	caption="Copy-and-pasting Humdrum data into VHVV text editor."
%}


## Copy-and-paste with the terminal ##

Copying from the VHV text editor and pasting to another editor in
the operating system is possible, either with <span
class="keypress">ctrl-c</span>/<span class="keypress">ctrl-v</span>
in Windows, or <span class="keypress">command-c</span>/<span
class="keypress">command-v</span> in MacOS (or you can figure out
on your own how to copy/paste in linux/unix). Also note that
<span class="keypress">ctrl-a</span> or <span class="keypress">ctrl-a</span>
can be used to select all of the VHV text editor content before copying.

The following sections discuss how to copy/paste between *standard input* and 
*standard output* in the terminal and the VHV editor.


### MacOS using pbcopy/pbpaste ###

When working with a terminal in MacOS, you can use the
[pbcopy](http://osxdaily.com/2007/03/05/manipulating-the-clipboard-from-the-command-line/)
command to copy standard output to the clipboard (or *P*aste*B*oard if you
want to remember the command name).
If the Humdrum file is called `file.krn`, the copy command is:

```bash
cat file.krn | pbcopy
```

Then go to the VHV text editor and type <span
class="keypress">command-v</span> to paste into VHV.

{% include image.html
	file="pbcopy-humdrum.gif"
	alt="Humdrum file copy/paste from the terminal"
	max-width="100%"
	caption="Copy-and-pasting Humdrum from the terminal using pbcopy."
%}


Conversely,
[pbpaste](http://osxdaily.com/2007/03/05/manipulating-the-clipboard-from-the-command-line/)
can be used to copy data from the VHV editor and paste as standard
input into the terminal.  The following figure demonstrates this by copying
data from the VHV text editor to the [census](http://www.humdrum.org/man/census/) command:

{% include image.html
	file="pbpaste-humdrum.gif"
	alt="Humdrum file copy/paste to the terminal"
	max-width="100%"
	caption="Copy-and-pasting Humdrum to the terminal using pbpaste."
%}

The command demonstrated above is:

```bash
pbpaste | census -k
```

where data from the VHV editor is piped into the census command, resulting in
this information for the first movement of Beethoven's op. 81a piano sonata:

```
HUMDRUM DATA

Number of data tokens:     7034
Number of null tokens:     3329
Number of multiple-stops:  679
Number of data records:    2129
Number of comments:        12
Number of interpretations: 115
Number of records:         2256

KERN DATA

Number of note-heads:      3944
Number of notes:           3917
Longest note:              2.
Shortest note:             24
Highest note:              ffff
Lowest note:               FFF
Number of rests:           268
Maximum number of voices:  9
Number of single barlines: 197
Number of double barlines: 1
```



## Saving Humdrum files/data ##

Humdrum data can be copied from the VHV text editor and then
pasted into another editor within the operating system.

An alternate method is to save the contents of the VHV text editor
via the web browser with the [<span
class='keypress'>alt-s</span>](/commands/alt-s) command.  This will
save the contents of the editor to wherever files are saved
from your browser.  Note that the contents of the text editor need
not contain Humdrum data, which is why the default save filename
is `data.txt` rather than `data.krn`.

{% include note.html
	content="If a file already exists in the target directory/folder with the same name, the browser will usually add an incremental extension to the filename, such as \"data (1).txt\", \"data (2).txt\", and so on."
%}


Although the default filename for saving with <span
class='keypress'>alt-s</span> is `data.txt`, you can save to a
different filename by adding the text `!!!!SEGMENT: myfile.krn`
before the first line in the Humdrum file content in the VHV text editor.
For repertory files loaded from [kernScores](http://kern.humdrum.org),
the original filename of the source data will be used.

The saved file will be in [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
format.  If there are no high-bit characters in the file, then this
is equivalent to a plain ASCII text file.  Technologically challenged
people should probably use the <span class='keypress'>alt-s</span>
method of saving rather than copy-and-pasting into a text editor,
since you should make sure that the copied text is saved in an ASCII
file rather than a file containing formatting commands such as an
[RTF](https://en.wikipedia.org/wiki/Rich_Text_Format) or MS Word file.

Try saving a file in this manner and then reloading it into the VHV
text editor either by the drag-and-drop method or the copy-and-paste
methods described above.  Here is a demonstration of saving two files
(Bach chorales 61 and 62), and then dragging them back into the 
VHV editor from the Download folder.

{% include image.html
	file="save-drag-drop.gif"
	alt="saving and loading Humdrum files"
	max-width="90%"
	caption="Saving two files with <span class='keypress'>alt-s</span> and then drag-and-dropping them back into VHV."
%}




