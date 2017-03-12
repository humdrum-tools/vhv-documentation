---
search: exclude
title: Creating and adding figures.
author: Craig Stuart Sapp
creation_date: 7 Mar 2017
last_updated: 7 Mar 2017
tags: [all, maintenance]
sidebar: mydoc_sidebar
keywords: maintenance figures images
summary: "This page describes how to add images to documentation pages and how to create animated GIFs."
permalink: /maintenance/figures/index.html
---

{% assign specialstart = '{% include image.html' %}
{% assign specialend1 = '%' %}
{% assign specialend2 = '}' %}

## Inserting a figure ##

Here is a basic template for adding a figure to a documentation page:

```liquid
{{ specialstart }}
	file="filename.png"
	caption="This is a caption that will display below the image."
{{ specialend1 }}{{ specialend2 }}
```

The resulting figure inserted onto the page:

{% include image.html
	file="filename.png"
	caption="This is a caption that will display below the image."
%}

The template uses [liquid syntax](https://shopify.github.io/liquid),
which is the templating system used by [jekyll](https://jekyllrb.com),
which in turn is the static-site generating system used for the
documentation since it is incorporated seamlessly into [Github
pages](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages).

The template inserts the contents of [image.html](https://github.com/humdrum-tools/vhv-documentation/blob/gh-pages/_includes/image.html) onto the page as it is
converted into an HTML webpage, using the following parameter values to
fill in values within the image template file.  The parameters are in the
form:

```liquid
parameter1="value1"
parameter2="value2"
```

Note that there are quotes around the values (and quotes within the value
content must be backquoted: `\"`).  The parameter and the values are separated by
an equals sign, and note that there are no commas between parameters.  Multiple
parameters can be placed on the same line, but for the documentation pages, you
should place a single parameter indented with a tab on each line after the
include line.

Here is a list of the parameters recognized by the image template:

file
: This is a required parameter that gives the URL for the image.  The URL can be relative, as in this case, or it could be absolute, or point to an image on another website.

url
: If there is a **url** parameter, the image will be embedded in a hyperlink to that URL.  If there is no URL parameter in the image template, then the image will point to itself, typically so that you can view a larger version of it in a separate web tab.

alt
: This is an optional parameter that contains text for replacing the image in non-graphical web browsers.  Mostly not needed since the **caption** can be useful in this situation.

caption
: This is text that will be displayed underneath the image, describing it.

caption-margin-top:
: There is currently a CSS bug when using the **url** parameter, where the image has an added bottom border of 20 pixels. Set the **caption-margin-top** to `"-20px"` to correct for this.

shadow="false"
: Use this parameter and value if you do not want a shadow underneath the image.  The default is to show a shadow.

max-width
: This is the maximum width of the image in terms of percentage of the width of the running text.  By default this is set to `"75%"`, so use this parameter for a different size for the image.

margin-bottom
: CSS tweak for the bottom margin of the image to add or remove extra space after the figure.

margin-top
: CSS tweak for the top margin of the image to add or remove extra space before the figure.




## Creating animated GIFs ##

Documentation pages requiring dynamic figures to show an interface
action can use animated GIFs.  This section describes how the GIFs in the
documentation were created&mdash;first by capturing a screenshot video, and then
converting that video into an animated GIF.

### Creating an MOV file ###

Animations in this documentation were created in MacOS by running
`/Applications/QuickTime Player 10.app`, then choosing
**File** from the top menu and then **New Screen Recording**.  This will bring
up a little window that looks like this:

{% include image.html
	file="quicktime-recording.png"
	alt="Quicktime recording control"
	max-width="50%"
	caption="Quicktime recording control."
%}

Click on the red recording button in the middle of the controls.
A text message will appear on the screen that says to drag a selection
around the region of the screen that you want to record.  After making
the selection, a button appears in the center of the selection:

{% include image.html
	file="quicktime-start-recording.png"
	alt="Quicktime recording start"
	max-width="20%"
	caption=""
%}

Press the button and the video recording starts.  When finished with the
recording, press the key combination 
<span class="keypress">command-control-escape</span> to stop the recording.
Then save the video with 
<span class="keypress">command-s</span>.
The saved video will be in the
[QuickTime file format](https://en.wikipedia.org/wiki/QuickTime_File_Format) with
the filename extension `.mov`.


### Converting MOV to an animated GIF ###

The video files will be relatively large (about 10MB per minute), so a more
compressed format is useful for storage and web distribution.  Animated GIFs
are a good option, and the resulting images are about 10 to 20 times smaller
than the original video.


The GIFs created for this documentation
were generated at the website [exgif.com](https://ezgif.com).

{% include image.html
	file="ezgif1.png"
	url="https://ezgif.com"
	max-width="65%"
	alt="ezgif homepage"
	caption="ezgif.com homepage."
	caption-margin-top="-20px"
%}

To start creating an animated GIF, click on the clapper board with the text
**Video to GIF** underneath it.  This brings up the following page:

{% include image.html
	file="ezgif2.png"
	max-width="65%"
	alt="ezgif upload file"
	caption="ezgif file upload page."
%}

Click on the gray **Choose File** button and select a MOV file to upload
to the website.  Then click on the blue **Upload!** button to upload
the file.  The upload progress is shown in the lower
left-hand corner of the page as the video uploads.

#### Animated GIF creation parameters ####


Finally a page similar the following one will display
the video and give some formatting options for the animated GIF.

Three parameters need to be set:


1. **End time**: this is important to set correctly from the duration of the video; otherwise, the video will truncate to the time set in this parameter.  Play the video to check the total duration.
1. **Size**: preferably select `Original (up to 800px)`.
1. **Frame rate (FPS)**: this is also important, and should be set to `5 (max 60 seconds)`.

After setting the parameters, click on the blue **Convert to GIF!** button.


{% include image.html
	file="ezgif3.png"
	max-width="65%"
	alt="ezgif conversion parameters"
	caption="ezgif conversion parameters.."
%}


{% include warning.html
	content="The maximum duration of the animated GIF will be one minute (when using 5 frames per second sampling rate).  Longer videos will be truncated regardless of the end-time parameter setting."
%}



After a brief delay, the resulting animated GIF will be added to the bottom of the
same webpage.  You now have two options: (1) click on the **save** icon underneath
the GIF to download the file, or (2) click on the **optimize** icon to do
additional processing with lossy compression.


{% include image.html
	file="ezgif4.png"
	max-width="65%"
	alt="initial conversion to GIF"
	caption="Resulting animated GIF is added to the page."
%}

#### Optimizing the animated GIF ####

If the image has a size over about 200KB, it should be "optimized" rather
than saved.  If so, then click on the **optimize** icon
underneath the animated GIF.

{% include image.html
	file="ezgif5.png"
	max-width="65%"
	alt="initial conversion to GIF"
	caption="Click on the optimize button underneath the animated GIF."
%}

The following compression options will appear. 
Set the **Optimization method** to `Lossy GIF`, and choose a compression level
of about 50&ndash;75% of the range of the slider bar.  Then click on the 
blue **Optimize it!** button.

{% include image.html
	file="ezgif6.png"
	max-width="65%"
	alt="optimizing the animated GIF"
	caption="Optimization parameters to use."
%}

#### Save the animated GIF ####

After optimization has been done, another animated GIF is added
to the webpage.  Click on the **save** icon underneath this new
image to save the final image to the hard disk.  Where the file
will be saved is dependent on your web browser and operating system, such as
in **Documents** in MacOS.  The filename starts with `ezgif`, but should be
renamed and placed in the directory with the Markdown file for the 
page on which it will be displayed.

{% include image.html
	file="ezgif7.png"
	max-width="65%"
	alt="optimizing the animated GIF"
	caption="Click on the save icon to save the final animated GIF."
%}

#### Final result #####

Here is the text to add to `index.md` for displaying the image:

```liquid
{{ specialstart }}
	file="transpose-note.gif"
	alt="graphically transposing a note"
	caption="Stepwise graphical transposition of a note with <span class='keypress'>down</span>."
{{ specialend1 }}{{ specialend2 }}
```

And here is the final resulting image displayed on the page:

{% include image.html
	file="transpose-note.gif"
	alt="graphically transposing a note"
	caption="Stepwise graphical transposition of a note with <span class='keypress'>down</span>."
%}



