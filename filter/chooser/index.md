---
title: chooser filter
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 15 Sep 2019
last_updated:
ref: filters-chooser
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/chooser/index.html
---

The chooser filter can be used to extract or rearrange Humdrum data segments.

Here is an example of multiple movements stored in separate data segments.  The second one is displayed
on the right since the second data segment is selected by the filter.

{% include verovio.html
	source="chooser2"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="800px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="chooser2">
!!!!filter: chooser -s 2
**kern
*M4/4
=1
1c
==
*-
**kern
*M4/4
=1
1d
==
*-
**kern
*M4/4
=1
1e
==
*-
**kern
*M4/4
=1
1f
==
*-
**kern
*M4/4
=1
1g
==
*-
**kern
*M4/4
=1
1a
==
*-
**kern
*M4/4
=1
1b
==
*-
</script>

Try changing `!!!!filter: chooser -s 2` to another segment number, such as the fifth segment that displays a whole note G.


### Choosing multiple segments ###

The `chooser` filter can also rearrange the order of segments in the Humdrum data.   Here is an example of reversing the
order of the segments, then extracting the second segment from the reordered data.  Since the last segement contained a B,
which then becomes the first segment after reversing the segments, an A pitch is displayed as a result of the two
chooser filterings.


{% include verovio.html
	source="chooser3"
	scale="60"
	pageWidth="1450"
	humdrum-min-height="800px"
	tabsize="16"
%}
<script type="text/x-humdrum" id="chooser3">
!!!!filter: chooser -s $-1
!!!!filter: chooser -s 2
**kern
*M4/4
=1
1c
==
*-
**kern
*M4/4
=1
1d
==
*-
**kern
*M4/4
=1
1e
==
*-
**kern
*M4/4
=1
1f
==
*-
**kern
*M4/4
=1
1g
==
*-
**kern
*M4/4
=1
1a
==
*-
**kern
*M4/4
=1
1b
==
*-
</script>

The symbol `$` (or equivalently `%`) is used to represent the last segment in the data.  Thus `$-1` means to extract from the
last segment to the first segment, in other words extract the segments in reverse order.  A comma can be used to separate non-contiguous
segments, such as `!!!!filter: chooser 1,3,5,2-4`.  This will expand to the segment order `1,3,5,2,3,4`.




