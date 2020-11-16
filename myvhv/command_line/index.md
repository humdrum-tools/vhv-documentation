---
title: Using verovio in a terminal
lang: en
ref: myvhv-command_line
author: Craig Stuart Sapp
translator: 
creation_date: 10 Mar 2017
translation_date: 
last_updated: 10 Mar 2017
sidebar: main_sidebar
tags: [all]
vim: ts=3
keywords: verovio humdrum command-line terminal unix
summary: Verovio can be used on the command-line to produce SVG images or MEI data from Humdrum files.
permalink: /myvhv/command_line/index.html
---


## Getting started ##


### Downloading verovio ###

To use the command-line version of verovio, you must first download
and compile it.  

#### Installing git ####

To download, use [git](https://en.wikipedia.org/wiki/Git).  Which may need to be downloaded first.

{% include note.html
	content="For MacOS, install [Homebrew](http://brew.sh) which is a linux package manager for MacOS.  This will install Git at the same time as Homebrew is installed."
%}

{% include note.html
	content="For linux, git can be installed with a command similar to `yum install git` or `apt-get install git` or `dnf install git`.  Which one to use will depend on your version of linux."
%}

To check if you have git installed on your computer, type the command:
```bash
which git
```
If git is installed, then the above command will report where it is located.  If no location is given, then git is not installed.

#### Cloning from Github ####

Once git is installed, download verovio with this command:

```
git clone https://github.com/rism-ch/verovio
```

*Cloning* a repository with git means to download it.
This command should download the verovio source code to a directory
called `verovio` in the current directory.

### Select develop-humdrum branch ###

The most up-to-date version of verovio for use with Humdrum
is found in the `develop-humdrum` branch of the repository.
Switch to this branch with the command:

```
cd verovio
git checkout develop-humdrum
```

### Installing cmake ###

You must also have [cmake](https://cmake.org) installed in order
to configure the Makefile for compiling verovio.  Type:

```bash
which cmake
```

To see if it is installed. If not then it will have to be installed.
To install in MacOS if you can run the following command to install
cmake if Homebrew is installed:

```bash
brew install cmake
```

For linux, one of the commands `yum install cmake`, `apt-get install
cmake` or `dnf install cmake` should install cmake.  Which installation
command to run will depend on your version of linux.

### Creating Makefile with cmake ###

Next, you need to create a makefile for verovio with this command:

```bash
cd tools
cmake ../cmake
```

### Compiling the executable ###

After cmake has created the Makefile, type this command to compile
verovio:

```bash
make
make install
```

The `make install` will copy the verovio music fonts to 
`/usr/local/share/verovio`, and the executable will be copied
to `/usr/local/bin/verovio`.

You can test if the installation is complete by typing:
```bash
which verovio
```
and the command should reply with `/usr/local/bin/verovio`.

### Updating verovio ###

To update verovio later to the most recent vervio, you can 
do these commands:

```
cd verovio/tools
git pull
make
make install
```

If there have been major changes to the source code, then you 
might have to add `make clean` before make:

```
cd verovio/tools
git pull
make clean
make
make install
```

## Using verovio ##

See the [verovio command-line documentation page](http://www.verovio.org/command-line.xhtml) for a full list of options that
verovio recognizes. Typing:
```bash
verovio --help
```
will give a list of most options.

### Basic conversion from Humdrum to SVG ###

The simplest use of verovio to convert Humdrum data into an SVG image is:

```bash
verovio file.krn
```

This will create a file called `file.svg` with the notation.  Here is
some [Humdrum data](test.txt) to use as a test.  This is what the
SVG output should look like:

<center>
<img src="test.svg">
</center>



{% include note.html
	content="On MacOS, try typing \"`open file.svg`\" to view the image in a web browser (this will depend on the which program is registered to open SVG images when you double-click on them)."
%}

### --adjust-page-height ###

Notice that the example in the previous section has a large empty
space at the bottom of the SVG image.  A particularly useful option 
to fix this is `--adjust-page-height`.  This option will shrink the 
height of the output SVG image to the last system of music on 
a page with extra space below the last staff.

You can set the page height to be very high, and then add
`--adjust-page-height` to force all music to be displayed
in a single SVG image, even if there is a lot of music:

```bash
verovio file.krn --adjust-page-height -h 60000
```

Now the SVG image output will not have any empty space at the
bottom of the music:

<center>
<img src="test2.svg">
</center>




### Piping data into verovio ###

Verovio accepts standard input if you use `-` as the input 
filename.  For example, if you want to transpose the test 
data to G minor and print with verovio in one command:

```bash
transpose -kg file.krn | verovio - -o d-minor-version --adjust-page-height
```

This will create the file `d-minor-version.svg`:

<center>
<img src="test3.svg">
</center>



### Image height/width ###

Here is an example of setting the height and width of the
SVG image:

```bash
verovio file.krn -w 900 -h 1500
```

<center>
<img src="test4.svg">
</center>




### Selecting a page ###

If the rendered notation is longer than one page, use the
`--page` option:

```bash
verovio file.krn -w 900 -h 1500 --page=2
```

<center>
<img src="test5.svg">
</center>





### Scaling the image ###

The `-s` option can be used to set the size of the notation, 
with the default being `-s 100` for 100% (full-size).

```bash
verovio file.krn -w 1000 -h 60000 --adjust-page-height -s 20
```

<center>
<img src="test6.svg">
</center>


### Output all pages ###

The `--all-pages` option can be used to output all pages
with a single command:


```bash
verovio file.krn -w 1000 -h 1000 --all-pages -s 50
```

Page 1:
<center>
<img src="test7_001.svg">
</center>

Page 2:
<center>
<img src="test7_002.svg">
</center>

Page 3:
<center>
<img src="test7_003.svg">
</center>

Page 4:
<center>
<img src="test7_004.svg">
</center>



### Adjusting the space between systems ###

The `--spacing-system` option controls the distance between 
systems.  The units of the paremeter argument are in
diatonic step heights.

The default padding between systems is "6" which is equal
to the height of 3 staff lines.  Using 0 will still leave 
space between the systems, but it is the minimum value for
this option.

```bash
verovio file.krn -w 1000 -h 1000 --page=2 --spacing-system=0 -s 50
```

<center>
<img src="test8a.svg">
</center>

```bash
verovio file.krn -w 1000 -h 1100 --page=2 --spacing-system=8 -s 50
```

<center>
<img src="test8b.svg">
</center>


The `--spacing-staff` option functions similar to `--spacing-system`,
but controls the distance betwen staves within a system.

### Equal-duration spacing ###

You can set the value for the `--spacing-non-linear` to 1 in order
to generate music notation which has horizontal spacing between
notes which is proportional to the duration of the notes. 

The `--spacing-linear` option (default 0.25) usually has to be used in
this case to compress the notation; otherwise it is too wide when
setting only the `--spacing-non-linear`.

```bash
verovio file.krn -w 1000 -h 1000 --spacing-system=0 -s 40 --spacing-non-linear=1 --spacing-linear=0.05 --page=2
```

<center>
<img src="test10a.svg">
</center>

The `--spacing-non-linear` option is used to control the ratio of
the horizontal layout widths of a note and note with twice the
former's duration.  Setting this ratio to 1 is linear spacing (the
name of the option is confusing).  Setting to a value of 0.5 
produces an equal spacing for all note durations:

```bash
verovio file.krn -w 1000 -h 1000 --spacing-system=0 -s 40 --spacing-non-linear=0.5 --spacing-linear=0.05
```

<center>
<img src="test10b.svg">
</center>


The basic spacing of the notes will be slightly adjusted in order
to fit accidentals into the music.  And notice that each line of
music in the above exmaple have slightly different spacings from
the other staves since the systems are justified to the full
width of the page, causing the music on each staff to be stretched
or compressed slightly.




### Convert Humdrum data into MEI data ###

Here is an example of how to convert Humdrum data into MEI data:

```bash
verovio file.krn -t mei --all-pages --no-layout
```

The last two options are required when converting into MEI data.

Options:

-t mei
: set the target output to the MEI format (default is SVG).

--all-pages
: include all pages of data (no pages really, but still required).

--no-layout
: do not calculate notation layout (which is only needed for SVG creating).


### Convert MusicXML into Humdrum data ###

You can use the embedded MusicXML-to-Humdrum converter to
generate Humdrum data from an input MusicXML file:


```bash
verovio file.xml -t musicxml-hum
```




