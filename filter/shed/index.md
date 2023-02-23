---
title: shed filter
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 29 Oct 2019
last_updated:
ref: filters-shed
tags: [all, filters]
sidebar: main_sidebar
verovio: "true"
keywords: interface commands 
summary: 
permalink: /filter/shed/index.html
---

The shed filter is a regular-expression editor to manipulate the
contents of Humdrum data.  It is similar to the <a target="_blank"
href="https://en.wikipedia.org/wiki/Sed">sed</a> tool, and the name
stands for "Streamed Humdrum EDitor" in tribute.  The shed filter
is also related to the Humdrum Toolkit command <a target="_blank"
href="https://www.humdrum.org/man/humsed">humsed</a>, but has a
sufficiently novel interface to warrant a different name.  The main
difference between shed and humsed is that shed automatically
prevents breaking of the Humdrum file structure when substitutions
are applied.

The regular-expression syntax used by the shed filter matches that
of <a target="_blank"
href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions">javascript</a>,
which in turn is nearly identical to PERL regular-expressions.  In
other words, it is a form of extended regular expressions, so
characters such as `+` function as meta-characters in addition to
the basic regular-expression operators.

## Removing articulations ##

Here is an example application of shed to remove articulations from \*\*kern data:

{% include verovio.html
	source="artic"
	scale="50"
	pageWidth="1250"
	tabsize="10"
%}
<script type="application/x-humdrum" id="artic">
**kern
*M4/4
=1
4c'
4d~
4e'~
4f^
=2
4g^^
4ao
4b`
4cc;
==
*-
</script>

The shed filter requires an option, `-e`, containing a 
regular-expression substitution string similar to sed.  The structure of
the substitution is like this:

```
s/search/replacement/options
```

where "s" is a literal character that indicates a substitution.  The
character after the "s" is used to separate three parameters for the
substitution: the search expression, then the replacement string to
use when the search pattern is matched, and finally a list of options
for the substitution.

This command is embedded into a string given to the program with the 
`-e` option, meaning "(regular) expression".  So in order to remove
the articulations from the above example, the characters "~'^`o;"
need to be removed, so the substitution command will be:

```
s/['~^o`;]//g
```

This expression means to remove all of the characters within the
square brackets from the input data.  Notice the "g" at the end of
the substitution, this means to keep applying multiple substitutions
on a line; otherwise, only the first match on a line will be
substituted.  Here is a full example and the notation resulting from
the removal of the articulations:

{% include verovio.html
	source="noartic"
	scale="50"
	humdrum-min-width="300"
	pageWidth="1250"
	tabsize="10"
%}

<script type="application/x-humdrum" id="noartic">
!!!filter: shed -e "s/['~^o`;]//g"
**kern
*M4/4
=1
4c'
4d~
4e'~
4f^
=2
4g^^
4ao
4b`
4cc;
==
*-
</script>

Quotes around the string given to `-e` are optional unless there
is a space in the string.  However, it is wise to place quotes
around the substitution string when running the shed tool on the
command-line.


## Swapping articulations (multiple substitutions) ##

The expression string may contain more than one substitution operation. 
Separate each by a colon and/or space:

```
s/search1/replacement1/options1; s/search2/replacement2/options2
```

Here is an example where staccatos and tenutos are switched using three
substitutions: the first convert staccatos to a dummy string, then the
second converts tenutos to staccatos, and the third converts the
dummy string into tenutos:

```
s/'/ZZZ/g; s/~/'/g; s/ZZZ/~/g
```

For brevity, the semicolon separator can be omitted (unlike sed):

```
s/'/ZZZ/g s/~/'/g s/ZZZ/~/g
```

In this case the substitution string contains spaces, so quotes are
required in the filter.  Also note that using single or double
quotes within a substitution string also requires quotes around the
option string.

{% include verovio.html
	source="swapartic"
	scale="50"
	humdrum-min-width="400"
	humdrum-min-height="300"
	pageWidth="800"
	tabsize="10"
%}

<script type="application/x-humdrum" id="swapartic">
!!!filter: shed -e "s/'/ZZZ/g s/~/'/g s/ZZZ/~/g'"
**kern
*M4/4
=1
4c'
4d'
4e'
4f'
=2
4g~
4a~
4b~
4cc~
==
*-
</script>

The same result can be accomplished by three separate filters, although
this would run slower since the Humdrum data needs to be re-parsed two
extra times:

{% include verovio.html
	source="three"
	scale="50"
	humdrum-min-width="400"
	humdrum-min-height="325"
	pageWidth="800"
	tabsize="10"
%}

<script type="application/x-humdrum" id="three">
!!!filter: shed -e "s/'/ZZZ/g"
!!!filter: shed -e "s/~/'/g"
!!!filter: shed -e "s/ZZZ/~/g"
**kern
*M4/4
=1
4c'
4d'
4e'
4f'
=2
4g~
4a~
4b~
4cc~
==
*-
</script>






## Substitution scope ##

The main difference between sed and shed, is that shed contains
additional substitution options to control which component of the
Humdrum data is to be processed.  The default behavior is to change
only data tokens, ignoring other parts of Humdrum files, such as
global comments and tandem interpretations.

Here is a list of the additional operators that can be given for
substitutions within other components of Humdrum files:

Character | Meaning
==========|==========
I         | Only make substitutions in tandem interpretations.
X         | Only make substitutions in exclusive interpretations.
L         | Only make substitutions in local comments.
D         | Only make substitutions in data tokens.
B         | Only make substitutions in barline tokens.
R         | Only make substitutions in Reference records.
K         | Only make substitutions in Reference record keys.
V         | Only make substitutions in Reference record values.

If you specify another Humdrum component, such as `I` for tandem
interpretations, the data tokens will no longer be processed.  If
you still want data tokens to be processed along with another Humdrum
component, explicitly add the `D` option, such as `ID` to process
both tandem interpretations and data tokens.


### Convert **kern into **recip ###

Here is an example use of shed to convert \*\*kern data into
\*\*recip data:

```
!!!filter: shed -e "s/[^\d.%_\][]//gk s/kern/recip/X"
```

### Labels to colors ###

Here is an example that converts an arbitrary interpretation
marker into a color code:


{% include verovio.html
	source="marker"
	scale="50"
	humdrum-min-width="525"
	pageWidth="750"
	tabsize="10"
%}
<script type="application/x-humdrum" id="marker">
!!!filter: shed -e "s/up/color:red/I s/down/color:dodgerblue/I"
**kern	**kern
*M4/4	*M4/4
=1	=1
*up	*down
4c	4cc
4d	4b
4e	4a
4f	4g
=2	=2
4g	4f
4a	4e
4b	4d
4cc	4c
=3	=3
*down	*up
4b	4d
4a	4e
4g	4f
4f	4g
=4	=4
4e	4a
4d	4b
2c;	2cc;
==	==
*-	*-
</script>

This used of shed allows for only symbolic/analytic markup to be
encoded in the digital score, and visual markup is generated
automatically from this to generate the graphical notation.


## Selecting by data type  ##

There is a special substitution option `k` which will only process \*\*kern
spines and ignore any other spine type.  There is also a `-k` option that
can be used with the shed filter.  The difference between the two is that the
shed `-k` option would apply to all substitutions in the `-e` option, while the
`k` option would only apply to a specific substitution.

No other spine data type has a substitution operation, but there is a mechanism
by which a substitution option can be associated with a specific data type.  The
option letters `X`, `Y`, and `Z` can be assigned to particular data types by the
`-X`, `-Y`, and `-Z` shed options.  Here is an example:

```
!!!filter: shed -X text -Y dynam -e "s/f/p/gY s/[aeio]/u/gX"
```

This would mean to change all "f" characters to "p", but only in \*\*dynam
spine data, and then substitute the vowels `a`, `e`, `i`, and `o` to `u` only
in \*\*text spine data.

An alternative method of selecting specific data types to process is done by
using the -i option.  Note that this method is applied to all substitutions
operations.  Example:

```
!!!filter: shed -i "text,dynam" -e "s/f/p/g s/[aeio]/u/g"
```

This means to change `f` to `p` and `[aeio]` to `u` in only
\*\*text and \*\*dynam spines.  The changes will occur in both
spine types, so if there is an `f` in the \*\*text spine, it will
be turned into a `p`.



