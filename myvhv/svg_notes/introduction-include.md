
Pitch and rhythm information can be embedded in SVG images generated
from Humdrum data with verovio.  To embed this information, add the
option `humType: 1` to the verovio options.  These extra parameters
are stored in the `class` parameter of `g` elements that enclose
graphical elements for each note.  This information can be used to
style notes with CSS, align audio/MIDI with the image, or do basic
pitch/rhythm analyses directly from the SVG image as demonstrated
further below on this page.

Conversion from Humdrum data into MEI data inserts a `type` attribute
storing pitch and rhythm for notes.  A Humdrum note such as:

```
8G#
```

is converted into this MEI note element:

```xml
<note xml:id="note-L6F3S1" type="qon-12 qoff-25_2 pname-g acc-s oct-3 b40c-26 b12c-7" dur="8" oct="3" pname="g" accid="s" />
```

The `type` attribute contains several separate embedded parameters for passing through to the final SVG image:

qon-12 <span style="color:#AAA">(quarter-note on-time)</span>
: The starting time of the note in units of quarter notes since the start of the music.

qoff-25_2 <span style="color:#AAA">(quarter-note off-time)</span>
: The ending time of the note.  This is a rational value, representing "25/2" or 12.5 in
floating point.

pname-g
: The diatonic pitch name (a, b, c, d, e, f, or g).

acc-s
: The chromatic alteration (n=natural, s=sharp, f=flat, ff=double flat, ss=double sharp).

oct-3
: Fourth octave (middle-C octave)

b40c-26 <span style="color:#AAA">(base-40 pitch class)</span>
: This is the base-40 representation of the pitch class G#.

b40c-12 <span style="color:#AAA">(base-12 pitch class)</span>
: This is the base-12 representation of the pitch class G#/A-flat.


Subtracting the on-time from the off-time yields the duration 
of the note: 25/2 &ndash; 12 = 1/2 of a quarter note, or an eighth note.

Here is the graphical rendering of the above MEI element in and SVG 
conversion of the score:

```xml
<g class="note qon-12 qoff-25_2 pname-g acc-s oct-3 b40c-26 b12c-7" id="note-L6F3S1">
   <use xlink:href="#E0A4" x="2049" y="2615" height="720px" width="720px" />
   <g class="accid" id="accid-L6F3S1">
      <use xlink:href="#E262" x="1824" y="2615" height="720px" width="720px" />
   </g>
</g>
```

The MEI attribute 
`type="qon-12 qoff-25_2 pname-g acc-s oct-3 b40c-26 b12c-7"`
has been transformed into the SVG attribute 
`class="qon-12 qoff-25_2 pname-g acc-s oct-3 b40c-26 b12c-7"`,
preserving basic pitch and rhythm information about the note within the image.

