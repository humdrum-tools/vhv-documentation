---
title: Invisible rests
author: Craig Stuart Sapp
keywords: humdrum invisible rests
last_updated: 4 Mar 2017
tags: [humdrum, RDF]
summary: "Description of invisible rests and how to display them for proof-reading."
sidebar: mydoc_sidebar
permalink: /humdrum/invisible_rests/index.html
---

Invisible rests are used to align secondary voices/layers to the primary one.
These are most common in keyboard music, where voices may appear and disappear
anywhere within a measure. 

In the conversion from Humdrum to MEI, three types of *invisible
rests* are possible.  The first type is an explicitly encoded rest
with a `yy` signifier appended to the token, such as `4ryy`, which
means an invisible quarter-note rest.  The second type is a plain
`**recip` value with no pitch or rest signifiers, such as `4` for
a quarter-note duration.

MEI requires measure layers to be completely filled in with rhythmic
elements, while Humdrum allows secondary spines to be created or merged
anywhere within a measure.  The third type of invisible rest is one which 
is added to the MEI data in order to fill in the layer where the Humdrum
layers are partially expressed.

## Color all individual rests ##

Invisible rests can be made visible in the notation by adding this
meta-RDF line anywhere in the Humdrum data:

```
!!!RDF**kern: show spaces
```

MEI calls invisible rests `<space>`, so that is why the action text is
`show spaces`.  All three categories of invisible rests in Humdrum will
be displayed with this RDF entry.  If you want to display the invisible
rests in a different color, add a color parameter to the line, such as
using the default color:

```
!!!RDF**kern: show spaces color=hotpink
```

Both [HTML 5/SVG](http://www.december.com/html/spec/colorsvg.html) and 
[hex colors](http://www.hexcolortool.com) are allowed.


## Color by rest category ##

If you want to color a single category of invisible rests in the notation,
use any of these RDF lines:

```
!!!RDF**kern: show invisible rests color=chartreuse
!!!RDF**kern: show recip spaces color=royalblue
!!!RDF**kern: show implicit spaces color=blueviolet
```

`show invisible rests` is used to display explicit rests which contain
the `yy` signifier in the rest token. `recip spaces` is used to
display invisible rests which are produced by plain recip tokens which
do not have pitch or rest signifiers.  `implicit spaces` is used to
display invisible rests generated for filling in all layers with complete
durations of the measure.

These three colorizations can be used with the `show spaces` RDF, and each will
supersede the global invisible rests color for their type of rest.


