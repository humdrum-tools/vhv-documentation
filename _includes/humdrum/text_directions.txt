## Text directions ##

Text can be displayed in the graphical notation by adding a text 
layout direction to the encoding:


{% include verovio.html
	humdrum-min-height="360px"
	source="dir1"
	scale="55"
	pageWidth="1000"
%}
<script type="application/x-humdrum" id="dir1">
**kern
*clefG2
*M4/4
=1
!LO:TX:b:i:t=cresc.
4c
2d
4f
=2
!LO:TX:a:i:t=accel.
4f
!LO:TX:b:t=comment
4d
4e
4c
==
*-
</script>

Text layout comments start with `!LO:TX:` and are placed immediately before the note
to which they are attached.  The parameter `a` means place the text above, and `b` means
place the text below. The font is roman by default; adding an `i`  parameter will 
make the text italic, and `b` to make it bold.  The actual text is given by the
`t` parameter, such as "*cresc.*" with the parameter `t=cresc.`.  Note that parameters
are separated by colons, and &amp;colon; is used to insert a colon into the text string.


