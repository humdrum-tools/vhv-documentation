---
search: exclude
title: Creating page translations
lang: en
ref: maintenance-translations
author: Craig Stuart Sapp
translator: 
creation_date: 11 Jun 2018
translation_date: 
last_updated: 11 Jun 2018
tags: [all, maintenance]
sidebar: main_sidebar
keywords: maintenance translation 
summary: "This page describes how to add page translations to the documentation."
permalink: /maintenance/translations/index.html
---


## Liquid header parameters ##

There are four parameters that should be added to page translations:

```
lang: en
ref:  reference
translator: Person's name(s)
translation_date: date that translation was done
```

If there is more than one translator, then the translator field
would be listed as an array, with the primary translator first:

```
lang: en
ref:  reference
translator: ["Person One", "Person Two"]
translation_date: date that translation was done
```

The `lang` and `ref` fields are needed to generate the translated pages 
on the website.  The `lang` field specifies the language of the translation
in [ISO 639-1](https://www.loc.gov/standards/iso639-2/php/code_list.php)
two-letter language codes.  The `ref` parameter is used to link translations
together, so it must contain a unique identifier for each page, which is
typically the value of the `permalink` parameter with slashes turned into
dashes, and any final `/index.html` text removed.

The `translator` and `translation_date` parameters are displayed on the
bottom right of pages, along with the page author(s) and creating/last edited
date.

When a new translation is added, each translation page and the main page need
to be updateded to include all of the languages.  So if there were translations
to Polish, Spanish, and French available in addition to the original in English,
then there will be four files:

```
index.md
index-PL.md
index-ES.md
index.FR.md
```

And all files would have an entry in the liquid header:

```
lang: en es fr pl
```

The langauges can be listed in any order, but perhaps alphabetical by their
language code is best.  This entry tells Jekyll that mutliple langauges are 
available for the page, and this in turn will add a list of the langauges
to the pages' headers on the website.

## Permalinks ##

Webpage target locations are controlled by
[permalinks](https://jekyllrb.com/docs/permalinks).  It is probably
best to give a separate permalink to each translated page, by adding a
dash followed by the two-letter ISO 639-1 language code in 
capital letters before the `.html` extension.  For example, the 
permalink for the 
[Humdrum tutorial page](https://raw.githubusercontent.com/humdrum-tools/vhv-documentation/gh-pages/humdrum/getting_started/index.md) is:

```
permalink: /humdrum/getting_started/index.html
```

So the Polish translation would be:

```
permalink: /humdrum/getting_started/index-PL.html
```

The Spanish translation would be:

```
permalink: /humdrum/getting_started/index-ES.html
```

And the French translation would be:

```
permalink: /humdrum/getting_started/index-FR.html
```



## References ##

[Making Jekyll multilingual](https://www.sylvaindurand.org/making-jekyll-multilingual) by Sylvain Durand, 1 Oct 2016.


