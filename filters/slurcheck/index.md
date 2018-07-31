---
title: slurcheck filter
lang: en
ref: filters-slurcheck
author: Craig Stuart Sapp
translator:
creation_date: 31 Jul 2018
translation_date:
last_updated: 31 Jul 2018
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
datatable: "true"
keywords: slur checking command
summary: "The slurcheck filter can be used to automatically identify unbalanced slur
markers in **kern data spines."
permalink: /filters/slurcheck/index.html
---


## Using the slurcheck filter in VHV

Here is an animated demo of using the `slurcheck` tool in
[VHV](http://verovio.humdrum.org):

{% include image.html
	file="animated-slurcheck.gif"
	alt="Identifying and fixing unbalanced slurs"
	caption="Identifying and fixing unbalanced slurs in VHV."
%}

Slurs starts, `(`, or endings `)` that do not pair with respective ending/beginning slur
marks are highlighted in pink.

Try fixing the slurs in the following example, or add additional unmatched slur endings to the example.
Either the slurs can be fixed by removing the unbalanced slur endpoint, or by adding a matching slur
endpoint to open/close the slur.


{% include verovio.html
	source="slurcheck1"
	scale="60"
	humdrum-min-height="350px"
	pageWidth="1450"
	tabsize="16"
%}

<script type="application/json" id="slurcheck1">
!!!filter: slurcheck
**kern
*M4/4
=1
4c
4d)
(4e
(4f
=2
4g
4f)
4e
((4c 4e 4g
=
1g 1e 1c;)
==
*-
</script>


Only one extra unbalanced slur will be marked  for each note/chord.
After fixing one of them, a second problematic slur may be displayed.



## Filter options

Here are useful options for use with the command-line version of the filter.  The `slurcheck`
tool is available for the command-line in the [humlib](https://humlib.humdrum.org) library.


{% include keytable.html
	contentId="options"
%}
<script type="text/JSON" id="options">
{% include_relative options.json %}
</script>



### Counting unmatched slur endpoints in a file/repertory

The `-c` option can be used with the `slurcheck` tool on the command line to count the
number of unmatched slur endpoints.  For a single work, three values will be reported:
(1) The total number of unmatched endpoints, (2) the number of unmatched slur starts, and (3)
the number of unmatched slur ends.

```bash
slurstart -c file.krn
```

May result in:

```
4	(:1	):3
```

This means that there are four unmatched slur endpoints, with open of them being a slur opening, and
three of them being a slur close.


Multiple files can be given as input.  The `-Z` option will suppress listings for file with no hanging
slurs, and the `-f` option will also display the filename at the start of the line.


```bash
 humcat -s h://mozart/sonatas | slurcheck -cZf
```

```
sonata01-1.krn:	1	(:1	):0
sonata01-3.krn:	1	(:0	):1
sonata02-3.krn:	1	(:0	):1
sonata03-3.krn:	1	(:0	):1
sonata04-3.krn:	1	(:0	):1
sonata05-1.krn:	3	(:0	):3
sonata06-3l.krn:	2	(:0	):2
sonata07-2.krn:	1	(:1	):0
sonata07-3.krn:	1	(:0	):1
sonata08-1.krn:	1	(:1	):0
sonata08-2.krn:	2	(:1	):1
sonata09-1.krn:	1	(:1	):0
sonata11-1f.krn:	1	(:1	):0
sonata11-1g.krn:	1	(:0	):1
sonata12-2.krn:	3	(:2	):1
sonata13-2.krn:	1	(:0	):1
sonata14-3.krn:	3	(:1	):2
sonata15-2.krn:	1	(:0	):1
sonata16-1.krn:	1	(:1	):0
sonata16-2.krn:	1	(:0	):1
sonata17-1.krn:	1	(:0	):1
sonata17-3.krn:	4	(:1	):3
```


### Locating unmatched slur endpoints in a file/repertory


To display the location of unbalanced slur endpoints, use the `-l` option.  In the following
example the `-f` option is also given to display which file the slur is located:

```bash
humcat -s h://mozart/sonatas | bin/slurcheck -lf
```

```
sonata01-1.krn:	UNCLOSED SLUR	line:1443	field:3	token:(8ddJ)
sonata01-3.krn:	UNOPENED SLUR	line:1072	field:4	token:8ccJ)
sonata02-3.krn:	UNOPENED SLUR	line:607	field:1	token:8f) 8a))
sonata03-3.krn:	UNOPENED SLUR	line:738	field:3	token:4a)
sonata04-3.krn:	UNOPENED SLUR	line:143	field:2	token:8ddJ))
sonata05-1.krn:	UNOPENED SLUR	line:495	field:3	token:4dd)
sonata05-1.krn:	UNOPENED SLUR	line:504	field:3	token:4b)
sonata05-1.krn:	UNOPENED SLUR	line:1134	field:3	token:4gg)
sonata06-3l.krn:	UNOPENED SLUR	line:631	field:2	token:(64cc#qLLLL>)
sonata06-3l.krn:	UNOPENED SLUR	line:646	field:2	token:128gJ)
sonata07-2.krn:	UNCLOSED SLUR	line:1044	field:3	token:((4e
sonata07-3.krn:	UNOPENED SLUR	line:1282	field:2	token:16a)
sonata08-1.krn:	UNCLOSED SLUR	line:1308	field:2	token:(4F 4A (4c
sonata08-2.krn:	UNOPENED SLUR	line:1227	field:1	token:32fJJJ))
sonata08-2.krn:	UNCLOSED SLUR	line:490	field:3	token:(>(16ccqLL
sonata09-1.krn:	UNCLOSED SLUR	line:565	field:2	token:(1dd#
sonata11-1f.krn:	UNCLOSED SLUR	line:290	field:3	token:(16ee'JJ)
sonata11-1g.krn:	UNOPENED SLUR	line:243	field:3	token:8a)
sonata12-2.krn:	UNCLOSED SLUR	line:699	field:1	token:(&(>4G 4B 4d (4f
sonata12-2.krn:	UNOPENED SLUR	line:281	field:3	token:(16b-TLL)
sonata12-2.krn:	UNCLOSED SLUR	line:723	field:3	token:(64b-JJJJ)
sonata13-2.krn:	UNOPENED SLUR	line:275	field:2	token:(8ff)
sonata14-3.krn:	UNCLOSED SLUR	line:676	field:2	token:(4F
sonata14-3.krn:	UNOPENED SLUR	line:681	field:2	token:4e- 4g)
sonata14-3.krn:	UNOPENED SLUR	line:724	field:3	token:16ccJJ))
sonata15-2.krn:	UNOPENED SLUR	line:968	field:2	token:16b)
sonata16-1.krn:	UNCLOSED SLUR	line:1095	field:2	token:(16b-L
sonata16-2.krn:	UNOPENED SLUR	line:695	field:1	token:2B-_ 2a-_)
sonata17-1.krn:	UNOPENED SLUR	line:1034	field:1	token:8f#) 8a))
sonata17-3.krn:	UNOPENED SLUR	line:1634	field:2	token:8BL)
sonata17-3.krn:	UNOPENED SLUR	line:1134	field:2	token:8bJ))
sonata17-3.krn:	UNOPENED SLUR	line:1143	field:2	token:(8.cc#L])
sonata17-3.krn:	UNCLOSED SLUR	line:1626	field:2	token:((24ddLL
```

To count the number of unbalanced slurs in a repertory, use the following command (33 in this case):

```bash
humcat -s h://mozart/sonatas | slurcheck -l  | wc -l
33
```

To count the number of files in a repertory that have unbalanced slurs, use the following command (22 in this case):

```bash
humcat -s h://mozart/sonatas | slurcheck -Zc  | wc -l
22
```



