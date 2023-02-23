---
title: Running VHV locally
lang: en es
page_language: en
author: Craig Stuart Sapp
creation_date: 20 Aug 2017
last_updated:
ref: myvhv-local
search: exclude
tags: [all, maintenance]
sidebar: main_sidebar
keywords: maintenance local webserver
summary: This page describes how to run the VHV website on your local computer rather than from Github pages.
permalink: /myvhv/local/index.html
---

## Preliminaries ##


### Installing jekyll ###

Follow the instructions for installing Jekyll on the website
[jekyllrb.com/docs/installation](https://jekyllrb.com/docs/installation)
and/or
[https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll)

### Install git ###

To check if you have git installed, type on the command-line (terminal):

```bash
which git
```

which should reply with something like:

```
/usr/local/bin/git
```

If you are using an MacOS computer and you do not have git, then install [Homebrew](http://brew.sh).
If you use Windows, then good luck&mdash;although Windows 10 now comes with a [https://msdn.microsoft.com/en-us/commandline/wsl/install_guide](linux shell) that you
could try.
If you do not have git on a linux/unix operating system, then try typing one of these:

```bash
apt-get install git-all
yum install git
dnf install git-all
```

See [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
 for more information.

Also, if you like GUIs, then read this link about [https://git-scm.com/downloads/guis](GUI clients for git).

### Download the website ###

After git is installed, you can download the VHV documentation website with the command:

```bash
git clone https://github.com/humdrum-tools/verovio-humdrum-viewer
```

This will download the website to the directory `./verovio-humdrum-viewer`.

## Running the website locally ##

Go into the `verovio-humdrum-viewer` directory (wherever you have stored it).  Then type:

```bash
./.serve
```

This will compile the website and allow your web browser to access the website from the address
`http://127.0.0.1:2000`.

If the `serve` script fails to run, then most likely you need to type the command the first time:

```bash
bundle install
```


{% include warning.html
	content="Recently the nokogiri component which should be installed with the above command does not work properly, so try also running the command 'gem install nokogiri -v 1.6.8.1 -- --use-system-libraries=true --with-xml2-include=\"$(xcrun --show-sdk-path)\"/usr/include/libxml2' if there is a problem."
%}

{% include image.html
	file="local.png"
	alt="VHV running on local webserver."
	max-width="80%"
	caption="VHV running on local webserver."
%}

### Running the website offline ###

If you are not going to have access to the internet when accessing the website (such as
working on a plane), then you can run the website in local-only mode by typing:

```bash
./.serve-local
```

In order to use this script, you will first have to download the `verovio-script.js` file
by going into the `scripts/local` directory and typing `make` in the terminal.  This only has to 
be done once, but you can repeat the download to ensure that you have the most recent
version of the `verovio-toolkit.js` file.


{% include note.html
	content="The online repertories are not yet available for a completely offline version of VHV.  If you need to use any of the online repertories, you will have to downloaded them separately (such as from [github.com/humdrum-tools/humdrum-data](https://github.com/humdrum-tools/humdrum-data)), and then [drag-and-drop](/interface/humdrum/#drag-and-drop-humdrum-files-into-vhv) the files onto the local VHV page."
%}



