---
title: humbreak filter
lang: en
page_language: en
author: Craig Stuart Sapp
creation_date: 4 Apr 2024
last_updated: 4 Apr 2024
ref: filters-humbreak
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/humbreak/index.html
---

The humbreak filter can be used to insert line(system)/page breaks
into Humdrum data.

{% include filter-options.html file="options.aton" lang="EN" %}

<a name="option-m"></a>
Example usage to add line breaks:

{% include verovio.html
	source="break"
	scale="40"
	pageWidth="1350"
	tabsize="10"
	humdrum-min-height="410px"
%}
<script type="text/x-humdrum" id="break">
!!!verovio: breaks encoded
!!!filter: humbreak -m 3,7
**kern
*M4/4
=1
1c
=2
1d
=3
1e
=4
1f
=5
1g
=6
1a
=7
1b
=8
1cc
=9
1dd
=10
1ee
=11
1ff
=12
1gg
==
*-
</script>

In order for the breaks to be used, `!!!verovio: breaks encoded`
is added to set the verovio option `breaks` to `encoded`.  You can
add the option to the data as done above, or you can set the 
HNP option `"breaks": "encoded"`, or click on the linebreak button
in the main toolbar on VHV (<div title="Use embedded line breaks (if any)" class="nav-icon fas fa-align-center"></div>/<span title="Automatic line breaks" class="nav-icon fas fa-align-justify"></span>).

The humbreak filter will add `!!LO:LB` lines just before the
measures after the `-m` option:

{% include verovio.html
	source="breakout"
	scale="40"
	pageWidth="1350"
	tabsize="10"
	humdrum-min-height="410px"
%}
<script type="text/x-humdrum" id="breakout">
!!!verovio: breaks encoded
!!!Xfilter: humbreak -m 3,7
**kern
*M4/4
=1
1c
=2
1d
!!LO:LB:g=original
=3
1e
=4
1f
=5
1g
=6
1a
!!LO:LB:g=original
=7
1b
=8
1cc
=9
1dd
=10
1ee
=11
1ff
=12
1gg
==
*-
</script>


<a name="option-p"></a>

The `-p` option works similarly to `m`, but page breaks will be
added to the given barlines.


<a name="option-g"></a>

The `-g` can set the group name for the line/page breaks, with the
default group being `original`.


<a name="option-r"></a>

The `-r` option can be used to remove any `!!!LO:LB` or `!!!LO:PB`
lines in the Humdrum data.


<a name="option-l"></a>

The `-l` option is used to convert any `!!LO:PB` to `LO:LB` (convert
page brakes to line breaks.



