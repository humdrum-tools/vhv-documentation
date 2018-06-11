---
title: cint filter
lang: en
author: Craig Stuart Sapp
creation_date: 3 Jun 2017
last_updated: 3 Jun 2017
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filters/cint/index.html
---

The *cint* filter calculates and processes music based on counterpoint
modules.  See the full technical [documentation for
cint](http://extras.humdrum.org/man/cint) on the Humdrum Extras
website for all options.

Counterpoint modules consist of four notes in two simultaneous
voices that form a module of two harmonic and two melodic intervals.
The filter name *cint* can mean either *counterpoint intervals* or
*composite melodic/harmonic intervals*, and functions as a generalization of
the [hint](http://www.humdrum.org/man/hint) (harmonic intervals)
and [mint](http://www.humdrum.org/man/mint) (melodic intervals)
tools of the original Humdrum Toolkit.

Below is an example of a module.  The first measure in the example below represents
a pair of notes being sounded together in two separate voices.  These four notes comprise
four intervals illustrated in the second measure.  the red marks indicate the melodic
intervals, and the blue marks indicate the harmonic intervals.  

{% include image.html
	file="counterpoint-module.svg"
	alt="Counterpoint module and how it is described."
	max-width="80%"
	caption="Melodic and harmonic intervals forming a counterpoint module."
%}

Given any three intervals
in the module, the fourth can be calculated automatically, so measure three gives an 
illustration of the typical description of a module which omits the top melodic interval
and would be written inline as "10 -2 12", which means that the module starts with a harmonic
interval of a 10th, then the lower voice moves down by a second and forms a harmonic
interval of a 12th with the upper voice (which implicitly had to move up a step to form the
12th).

The cint filter can describe intervals in other units such as twelve-tone and base-40, as
well as chromatically altered diatonic intervals, and allow for octave collapsing of
the harmonic intervals and note-attack configurations.

## Module Searching ##

### Searching for stepwise rising parallel thirds/tenths ###

Here is an example of searching for parallel thirds in contrapuntal music.  The basic
counterpoint module for parallel thirds going up by step is "3 2 3".  The filter used
in the following example is:

```
!!!filter: cint -O --search "3 2 3"
```

The `-O` option is used to collapse compound intervals such as a 10th to 3rd, removing
octave transpositions of the basic intervals.  Click on the examples below to load the
same data and filter into VHV.

{% include image.html
	file="search3-2-3.png"
	alt="Searching for 3-2-3 module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-O%20--search%20%223%202%203%22"
	max-width="80%"
	shadow="false"
	caption="Searching for parallel 3rds (or 10ths) in a Bach chorale."
%}


### Searching for parallel thirds with note attacks only. ###

Adding note attacks with the `-x` option will allow searching harmonic intervals based 
on whether or not the notes were attacked (`x)` or sustained (`s`).  Searching only for 
parallel thirds where both voices's notes attack together would be "3xx 2 3xx":

```
!!!filter: cint -x -O --search "3xx 2 3xx"
```

or when merging parameterless options:

```
!!!filter: cint -xO --search "3xx 2 3xx"
```

{% include image.html
	file="search3xx-2-3xx.png"
	alt="Searching for 3-2-3 module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xO%20--search%20%223xx%202%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Searching for rising parallel 3rds with note attacks in a Bach chorale"
%}

Notice that the parallel thirds in measure 11 are no longer highlighted since the
parallel thirds motion was entered with a sustained note in one voice.


### Module length ###

Longer chains of modules can be searched by adding the `-n #` option, where `#` is the
number of elided modules calculated for the search.  For example, using `-n 2` in the
cint filter will only match to two successive parallel third motions up by step by three 
pairs of notes in each voice:

```
!!!filter: cint -xO -n 2 --search "3xx 2 3xx 2 3xx"
```

{% include image.html
	file="search3xx-2-3xx-2-3xx.png"
	alt="Searching for 3-2-3 module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xOn2%20--search%20%223xx%202%203xx%202%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Searching for two-module rising parallel 3rds with note attacks in a Bach chorale"
%}


Notice that there are fewer matches since single parallel motions modules are ignored.

{% include warning.html
	content="Searching for a shorter module sequence when specifying a larger length with the <nobr>-n</nobr> option will highlight the entire longer sequence.  Use regular expression anchors such as \"^3xx 2 3xx\" to search for module sequences that start with a parallel third upwards stepwise motion followed by any other module starting with a harmonic third interval when the module sequence is 2 or higher; or \"3xx 2 3xx$\" for module sequences which end in a parallel third upwards stepwise motion. To ensure that you are searching the correct length module sequence, use both `^` and `$` such as \"^3xx 2 3xx$`; when -n2 is used, this search will return no matches since it is a length-1 module sequence."
%}


### Descending parallel thirds ###

Use `-2` as the melodic interval when searching for descending parallel thirds:

```
!!!filter: cint -xO -n 2 --search "3xx -2 3xx -2 3xx"
```

{% include image.html
	file="search3xx-n2-3xx-n2-3xx.png"
	alt="Searching for 3xx -2 3xx -2 3xx module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xOn2%20--search%20%223xx%20-2%203xx%20-2%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Searching for two-module falling parallel 3rds"
%}



### Directionless stepwise parallel thirds ###

Use `-?2` as the melodic interval when searching for parallel thirds that either
go up or down by step.

```
!!!filter: cint -xO -n 2 --search "3xx -?2 3xx -?2 3xx"
```

{% include image.html
	file="searchupdown.png"
	alt="Searching for 3xx -?2 3xx -?2 3xx module."
	url="http://verovio.humdrum.org?file=chorales/chor001.krn&k=ey&filter=cint%20-xOn2%20--search%20%223xx%20-%3f2%203xx%20-%3f2%203xx%22"
	max-width="80%"
	shadow="false"
	caption="Searching for two-module rising or falling parallel 3rds"
%}


## Cadential suspensions ##


## References ##

Bent, Margaret. “Grammar of Early Music: Preconditions for Analysis.” In Tonal Structures in Early Music, edited by Cristle Collins Judd, 15-59. London: Garland Publishing, 1998.

Burmeister, Joachim. Musical Poetics. Translation by Benito Rivera. New Haven: Yale University Press, 1993. Originally published 1606.

Conklin, Darrell, and Mathieu Bergeron, “Discovery of Contrapuntal Patterns.” In Proceedings of the International Society for Music Information Retrieval (2010): 201–206.

Cumming, Julie. “From Two-Part Framework to Movable Module.” In Medieval Music in Practice: Essays in Honor of Richard Crocker, edited by Judith Peraino, 175–213. Münster: American Institute of Musicology, 2013.

———. “Text-Setting and Imitative Technique.” In The Motet around 1500: On the Relationship of Imitation and Text Treatment, edited by Thomas Schmidt-Beste. Turnhout: Brepols, 2012.

Cumming, Julie, and Peter Schubert. “The Origins of Pervasive Imitation.” In The Cambridge History of Fifteenth-Century Music, ed. Anna Maria Busse Berger and Jesse Rodin, 200–28. New York: Cambridge University Press, 2015.
DeFord, Ruth. Tactus Mensuration, and Rhythm in Renaissance Music. Cambridge: Cambridge University Press, 2015.

Fuller, Sarah. “Contrapunctus Theory, Dissonance Regulation, and French Polyphony of the Fourteenth Century.” In Medieval Music in Practice: Studies in Honor of Richard Crocker, edited by Judith Peraino, 113–52. Middleton, Wisconsin: American Institute of Musicology, 2013.

———. “Organum – discantus – contrapunctus in the Middle Ages.” In The Cambridge History of Western Music Theory, edited by Thomas Christensen, 477–502. Cambridge: Cambridge University Press, 2002.

Milsom, John. “‘Imitatio,’ ‘intertextuality’, and early music.” In Citation and authority in Medieval and Renaissance musical culture: Learning from the learned, edited by Suzannah Clark and Elizabeth Eva Leach, 141–51. Woodbridge: Boydell & Brewer, 2005.

Morgan, Alexander. "[Renaissance Interval-Succession Theory: Treatises and Analysis](http://digitool.library.mcgill.ca/R/DPIVYXI71HL5ILGG61U4D2N5YR6UMUAASGK4S4JC42B2BFPGCD-00398?func=results-jump-full&set_entry=000001&set_number=001123&base=GEN01)". PhD diss., McGill University, 2017.

Pontio, Pietro. Ragionamento di musica. Compiled by Suzanne Clercx. Kassel: Bärenreiter, 1959. Originally published Parma: 1588.

———. [Ragionamento di musica](http://www.ums3323.paris-sorbonne.fr/TREMIR/TReMiR_Pontio/R0_start.htm). Electronic version published by Dupraz, Christophe. Traités Musicaux Romans, 2013. Accessed August 14, 2016.

Schubert, Peter. “Hidden Forms in Palestrina’s First Book of Four-Voice Motets.” Journal of the American Musicological Society 60 (2007), 483–556.

Schubert, Peter and Julie Cumming, “Another Lesson from Lassus: using Computers to Analyze Counterpoint.” Early Music 43.4 (November 2015): 577–86.

Tinctoris, Johannes. Liber de arte contrapuncti. In Johannes Tinctoris Opera Theoretica. Compiled by Albert Seay. n.p.: American Institute of Musicology, 1975. Originally written 1477.

———. Liber de arte contrapuncti. Translated by Albert Seay. Rome: American Institute of Musicology, 1961. Originally written c. 1477.

———. "[Liber de arte contrapuncti](http://earlymusictheory.org/Tinctoris/texts/deartecontrapuncti/). Translated by Jeffrey Dean. Last accessed November 16, 2015. Originally written 1477.

Vicentino, Nicola. Ancient music adapted to modern practice (L’antica musica ridotta alla moderna prattica). Translated by Maria Rika Maniates and edited by Claude Palisca. New Haven, Yale University Press 1996. Originally published 1555.

Zarlino, Gioseffo. Art of Counterpoint. Translated by Guy Marco and Claude Palisca, edited by Claude Palisca. New Haven and London: Yale University Press, 1968. Originally published: 1558.


