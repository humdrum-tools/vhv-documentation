---
search: exclude
title: Local VHV documentation
author: Craig Stuart Sapp
creation_date: 20 Aug 2017
last_updated: 20 Aug 2017
tags: [all, maintenance]
sidebar: main_sidebar
keywords: maintenance local webserver
summary: This page describes how to run the VHV documentation website on your local computer rather than from Github pages.
permalink: /maintenance/local/index.html
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
If you have windows, the good luck&mdash;although Windows 10 now comes with a [https://msdn.microsoft.com/en-us/commandline/wsl/install_guide](linux shell) that you
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
git clone https://github.com/humdrum-tools/vhv-documentation
```

This will download the website to the directory `./vhv-documentation`.

## Running the website ##

Go into the vhv-documentation directory (wherever you have stored it).  Then type:

```bash
./.serve
```

This will compile the website and allow your web browser to access the website from the address
`http://127.0.0.1:2000`.

{% include image.html
	file="webserver.png"
	alt="VHV documentation running on local webserver."
	max-width="80%"
	caption="VHV documentation running on local webserver."
%}

### Running the website offline ###

If you are not going to have access to the internet when accessing the website, then
you can run the website in local-only mode by typing:

```bash
./.serve-local
```

In order to use this script, you will first have to download the `verovio-script.js` file
by going into the `js/local` directory and typing `make` in the terminal.  This only has to 
be done once, but you can repeat the download to ensure that you have the most recent
version of the `verovio-toolkit.js` file.

## Editing pages locally ##

The easiest way to add or edit pages on the website is to install the website locally.
After you make changes, do these steps to update the online website hosted at Github pages:

#1 First type `git status` to see what files have been changed, and what new files
need to be added to the repository.  

#2 Check the files which are new, and then type
`git add myfile.txt`
to add the new file *myfile.txt* to the repository.  

#3 After all new files have been added,
type `git commit -a` to add the changes to the local repository.  This command will 
typically open the *vim* editor and you will type a brief description of the changes 
made to the documentation.  

#4 Finally type `git push` to copy the changes from the local
computer onto the Github servers.


If you do not have access to write to the documentation repository, you should instead
submit a pull request (more on how to do that later).









