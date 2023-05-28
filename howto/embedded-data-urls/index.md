---
title: Creating short data urls
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 27 May 2023
last_updated:
ref: data-display
tags: [all]
verovio: "true"
keywords: interface data
summary: "This page explains how to create short data URLs for emails and tutorials."
sidebar: main_sidebar
permalink: /howto/embedded-data-urls/index.html
---

URLs for short examples that load when you open the URL for VHV can
be created from the <b>File&rarr;Copy MIME URL</b> option in the
VHV menu:

{% include image.html
	file="mime-url.jpg"
	url="https://verovio.humdrum.org?t=KiprZXJuCipNNC80CjRjCjRkCjRlCjRmCj0KKi0K"
	alt="Link to example score in VHV"
	max-width="250px"
	caption="<b>File&rarr;Copy MIME URL</b> in the VHV menu"
	margin-bottom="-20px"
%}

Here is example music in the VHV editor:

{% include verovio.html
	source="scale"
	scale="55"
	tabsize="15"
	pageWidth="1400"
%}
<script type="application/x-humdrum" id="scale">
**kern
*M4/4
4c
4d
4e
4f
=
*-
</script>

Copying the MIME URL will copy this URL to the clipboard:

```
https://verovio.humdrum.org?t=KiprZXJuCipNNC80CjRjCjRkCjRlCjRmCj0KKi0K
```

which you can then paste into another applications such as for sending emails.

{% include note.html
	content="Most browsers limit URLs to 2000 characters.  A warning message will appear when copying the MIME URL if it exceeds this limit."
%}

The `t` parameter in the URL indicates (MIME-encoded) text follows in the value of the parameter.

You can also use this to create a [link](https://verovio.humdrum.org?t=KiprZXJuCipNNC80CjRjCjRkCjRlCjRmCj0KKi0K) on a webpage which which, when clicked, will load the embedded Humdrum data into VHV.

In addition, you can also copy only the MIME part of the URL and paste directly into VHV:

{% include image.html
	file="mime-text.jpg"
	url="https://verovio.humdrum.org?t=KiprZXJuCipNNC80CjRjCjRkCjRlCjRmCj0KKi0K"
	alt="Pasting MIME-encoded Humdrum data into VHV editor"
	caption="Pasting MIME-encoded Humdrum data into VHV editor."
	margin-bottom="-20px"
%}

VHV internally converts MIME data and can display the music notation for the encoded
Humdrum data.   You can also paste MIME data into the text editor and then go to
<b>File&rarr;MIME decode</b> to decode the MIME data.  

Longer files which exceed the limit for any specific browsers' URL size limit can be encoded
with the <b>File&rarr;MIME encode</b> option and then pasted into a email, for example.  To
decode the data, use <b>File&rarr;MIME decode</b> to convert back to a regular Humdrum file.

Also note that the links under each Humdrum example given in the documentation ("load into VHV") 
use this same system for transferring the Humdrum data from the documentation into the VHV
editor.



