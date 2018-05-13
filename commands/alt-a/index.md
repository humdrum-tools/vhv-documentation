---
title: <span class='keypress'>alt-a</span>
author: Craig Stuart Sapp
creation_date: 12 May 2018
last_updated: 12 May 2018
tags: [all, commands]
sidebar: main_sidebar
keywords: interface commands compile filters
summary: "The <span class='keypress'>alt-a</span> command toggles between TSV and CSV form of Humdrum data."
permalink: /commands/alt-a/index.html
---

Pressing <span class="keypress">alt-a</span> will toggle between
TSV and CSV versions of Humdrum data.  The standard form of Humdrum data
is in TSV format:

{% include image.html
	file="tsv.png"
	alt="TSV view of Humdrum data"
	caption="TSV view of Humdrum data."
%}


After pressing <span class="keypress">alt-a</span>, the data will be
displayed in CSV format:

{% include image.html
	file="csv.png"
	alt="CSV view of Humdrum data"
	caption="CSV view of Humdrum data."
%}

Pressing <span class="keypress">alt-a</span> again will revert the 
Humdrum data to TSV form.

The CSV form is useful for loading into software that has CSV import but 
not TSV import.  Also, the CSV format is useful for cases where tab
characters may get munged, such as in emails.

Notice that reference records (the green-colored text in the above figure)
may contain tabs which are not converted into commas when converting into
the CSV form.  This is because such tabs are not integral to the 
Humdrum data structure.  Tabs in global comments will also not be altered
for the same reason.


