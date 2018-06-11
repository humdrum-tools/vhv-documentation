---
title: J.S. Bach chorales
lang: en
author: Craig Stuart Sapp
keywords: humdrum Bach chorales
creation_date: 18 Mar 2017
last_updated: 18 Mar 2017
verovio: "true"
tags: [all, repertories]
vim: ts=3 ft=javascript
summary: J.S. Bach chorale repertory
sidebar: main_sidebar
permalink: /repertory/bach-chorales/index.html
---

The URL
[http://verovio.humdrum.org/?file=chorales](http://verovio.humdrum.org/?k=e&file=chorales)
lists a set of 371 four-part chorales that were collected after
J.S. Bach's death by his son C.P.E. Bach (and finished by Kirnberger,
a student of J.S. Bach, after C.P.E. Bach's death).  The chorales
are ordered by Breitkopf & Härtel edition numbers and includes all
chorales except #150 which is not in four parts.


The first complete edition of the chorales in this set was published
by Breitkopf & Härtel from 1784-1787 in four volumes.  The first
incomplete edition consisted of 200 chorales in two volumes by
Friedrich Wilhelm Birnstiel in 1765 & 1769, which was reprinted in
1975 by Georg Olms.

This digital edition is referenced against the
fourth edition of the chorales by Breitkopf & Härtel: *371
vierstimmige Choralgesänge von Johann Sebastian Bach*. 4th ed. by
Alfred Dörffel. Breitkopf & Härtel, Leipzig [c. 1875]. 178 pp. Plate
Number: V.A.10. Retypeset c. 1915 as Edition Breitkopf 10. Reprinted
by Associated Music Publishers, Inc., New York [c. 1940].  

Scans of the source edition for the first 50 chorales can be viewed
by pressing <span class="keypress">alt-p</span> when viewing a
particular chorale:


{% include image.html
	file="chorale-scan.png"
	alt="chorale scan"
	caption="Displaying the source edition scan with <span class=\"keypress\">alt-p</span>."
%}


See this
article: [The History of the Breitkopf Collection of J.S. Bach's
Four-Part Chorales](http://www.bach-cantatas.com/Articles/Breitkopf-History.htm) 
by Thomas Braatz for more information about the source edition of the
Bach chorales.


## Original-clef feature ##

The Bach-chorale repertory demonstrates how to encode 
[original clefs](/commands/alt-o).  Type 
<span class="keypress">alt-o</span> in VHV to switch between modern and original clefs
when viewing the chorales:

{% include image.html
	file="alt-o-clef-switching.png"
	alt="alt-o demonstration"
	caption=""
%}




The first edition of this chorale collection was actually published
in grand-staff arrangement, using soprano clef for the top staff
and bass clef on the bottom staff:

{% include image.html
	file="chorale-first-edition.png"
	alt="first edition"
	caption="First edtion of the chorales in soprano and bass clefs on a grand staff."
%}

Here is an example arrangement of the music that more closely matches the original edition:

{% include verovio.html
	source="chorale001"
	humdrum-max-width="220px"
	scale="50"
	pageWidth="1000"
%}

<script type="application/humdrum" id="chorale001">
!!!OTL:	Aus meines Herzens Grunde
!!!SCT:	BWV 269
!!!PC#:	1
**kern	**kern
*clefF4	*clefC1
*k[f#]	*k[f#]
*M3/4	*M3/4
*^	*^
4B	4GG	4g	4d
=1	=1	=1	=1
4B	4G	2g	4d
8cL	4E	.	4e
8BJ	.	.	.
4A	4F#	4dd	4d
=2	=2	=2	=2
4G	4G	4.b	2d
4F#	4D	.	.
.	.	8a	.
4G	4E	4g	4B
=3	=3	=3	=3
8cL	4C	4.g	8eL
8BJ	.	.	8d
4c	8BBL	.	8e
.	8AAJ	8a	8f#J
4d	4GG	4b	4g
=4	=4	=4	=4
2d;y	2D;	2a;	2f#;y
*v	*v	*	*
*	*v	*v
*-	*-
</script>





## Grand-staff arrangement ##

The Same Bach chorale data can be viewed in grand-staff layout by 
using this link: [verovio.humdrum.org/?file=chorales&filter=satb2gs](http://verovio.humdrum.org/?file=chorales&filter=satb2gs).

{% include image.html
	file="chor027-grand-staff.png"
	alt="grand-staff layout"
	url="http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs"
	caption="Grand-staff layout of chorales using the satb2gs filter."
	caption-margin-top="-20px"
%}


## Transposed chorales ##

The Bach chorales can also be transposed all to the same tonic pitch 
in grand-staff layout by 
adding a transpose filter to the URL: [verovio.humdrum.org/?file=chorales&filter=satb2gs%7ctranspose%20-kc](http://verovio.humdrum.org/?file=chorales&filter=satb2gs%7ctranspose%20-kc).


{% include image.html
	file="chor027-c-tonic.png"
	alt="grand-staff layout and transposed to C"
	url="http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kc"
	caption="Chorale transposed to tonic on C using the transpose filter."
	caption-margin-top="-20px"
%}


Change the "c" at the end of the URL for C-transposed chorales to change to another tonic:


D
: [http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kd](http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kd)

E-flat
: [http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-ke-](http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-ke-)

F-sharp
: [http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kf%23](http://verovio.humdrum.org/?file=chorales/chor027.krn&filter=satb2gs%7ctranspose%20-kf%23)

Humdrum data shown in the text editor is untransposed (showing the pre-filtered 
data).  In the following screen shot, notice the music is in F major, but the
notation is in F-sharp major:

{% include image.html
	file="chor027-f-sharp.png"
	alt="chorale 27 in f-sharp major"
	caption="Chorale 27 transposed to F-sharp major using the transpose filter."
%}


To view the transposed score in the text editor, type
<span class="keypress">alt-c</span> to compile the filter instructions:

{% include image.html
	file="chor027-f-sharp2.png"
	alt="chorale 27 in f-sharp major"
	caption="Chorale 27 data compiled to F-sharp major with <span class='keypress'>alt-c</span>."
%}


## Downloading and corrections ##

This digital edition of the J.S. Bach chorales is [available on Github](https://github.com/craigsapp/bach-371-chorales) for download.  Corrections to the edition can 
be submitted on Github, either as an [issue](https://github.com/craigsapp/bach-371-chorales/issues) (in prose), or preferrably as a [pull request](https://github.com/craigsapp/bach-371-chorales/pulls) (direct corrections to the data files).  The corrections should match the source edition scans (viewed by typing
<span class='keypress'>alt-p</span> on the first 50 chorales, or an explanation
should otherwise be submitted with the correction as to why the correction 
does not match the source scans.



