---
title: Saving buffers
lang: en es
author: Craig Stuart Sapp
creation_date: 18 Jun 2017
last_updated: 18 Jun 2017
tags: [all, getting_started, humdrum]
keywords: interface load save buffer
summary: "The contents of the editor can be cached into several persistent and temporary buffers."
sidebar: main_sidebar
permalink: /interface/buffers/index.html
---

## Persistent buffers ##

The VHV interface can store the contents of the text editor into nine persistent
buffers.  These buffers can be reloaded into the editor even after closing the
web browser and opening it again.  Other uses for the buffers would be to save
various analyses of a work to allow switching between the results quickly without
re-running different filters.  In particular if you are editing a complex piece, 
it is wise to save the current state of the editor occasionally in case of an
accidental closing of the VHV webpage.

To save the contents of the editor into a buffer, type a number from 1 to 9, and then
the key combination <span class="keypress">alt-shift-S</span>.  This will save the contents
of the editor into the specified buffer.  For example 
<span class="keypress">5+alt-shift-S</span> will store the editor's contents into buffer 5.


To load a buffer back into the editor, type the buffer number followed by the 
key combination <span class="keypress">alt-shift-R</span> to restore the buffer's 
contents to the editor.  For example
<span class="keypress">5+alt-shift-R</span> will restore the fifth buffer to the
editor.

Buffer 1 is the default save and load buffer.  If you type
<span class="keypress">alt-shift-S</span> without specifying a buffer number,
the first one will be used.  In other words
<span class="keypress">alt-shift-S</span> is equivalent to
<span class="keypress">1+alt-shift-S</span>.  Likewise
<span class="keypress">alt-shift-R</span> is equivalent to
<span class="keypress">1+alt-shift-R</span> when restoring the default buffer.



## Autosave buffer ##

A tenth buffer is stored in location 0.  This buffer is filled once a minute with the
current contents of the editor.  It is not normal to save to buffer 0, but it can be useful
to recover the recent contents of the editor after a significant problem, such as accidentally
moving to a new repertory piece while editing another one, or accidentally closing the 
VHV webpage.  To restore the autosave buffer,
type <span class="keypress">0+alt-shift-R</span>.  This has to be done within one minute
after VHV is reloaded before the buffer 0 content will be overwritten with the current
contents of the editor.


When restoring a persistent buffer, such as
<span class="keypress">3+alt-shift-R</span> to load the third buffer, the
current contents of the editor will be stored in buffer 0.  You then have
a minute or less to recover the old contents of the editor if you made a 
mistake in recalling one of the buffers, but typing
<span class="keypress">0+alt-shift-R</span>.


## Exit buffer ##

When the VHV webpage is closed, another autosave buffer is used to save the
current contents of the editor.  When returning to the VHV webpage within
an hour, this exit buffer will be restored to the editor.  In certain cases,
such as loading a repertory file from the URL, the editors contents will 
be overwritten with the URL's data content.  If you need to recover the
exit data, then type <span class="keypress">0+alt-shift-R</span> 
within one minute to restore the last autosave content.


## Related commands ##

Note that 
<span class="keypress">command-z</span>  (MacOS), or
<span class="keypress">control-z</span>  (Linux, Windows), 
can also be used to restore previous contents of the editor.

The <span class="keypress">alt-r</span>  command (without the shift key) will reload a repertory
file from the source.  This is occasionally necessary to flush buffering of the work
if it has changed at the source location.

