---
title:  "Viewing invisible rests"
categories: update
permalink: news-invisible-rests.html
tags: [news]
---

Special meta-RDF codes have been added for data proof-reading in
the encoding structure of Humdrum data when converting into MEI data.
Invisible rests, called `<space>` in MEI data, can be displayed as colored 
rests.  one RDF instruction will set the visibility and color of all types
of rests, and three additional RDF instructions can control the 
visibility and color of each category of `<space>` that the convert
generates.

See the documnetation for [invisible rests](/humdrum/invisible_rests) for more
information.

[Here is the
commit](https://github.com/rism-ch/verovio/commit/ab44b7bfffb6869e372943c66c1a3ecd5975d534)
to the verovio codebase which adds the feature (with examples at
the bottom of the page)

