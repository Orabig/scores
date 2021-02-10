# `extension-name` to be defined

:::vexflow
options debug=true timeSignature=4/4 key=Bb
staff
  bar
    A4/q, A5/q, A4/q, A4/q
  bar width=200 repeat=end
    A4/q, E4/q, A4/h
staff
  bar
    A2/q, F3/8, G3/8, A3/8, Ab3/8, An3/q
  bar
    A2/q, E2/q, E3/h
:::

Usage :
- options.debug : display vexflow struct with error messages
- options.timeSignature : if set, displays the time signature
- options.key : displays the key signature
- staff.clef : if set changes the default clef
- bar.width : sets the measure width (pixels)
- bar.repeat : if set to 'end', the measure end with a repeat bar
 

Rules :
- by default, first staff has a 'treble' clef, following are 'bass'.
- bar options are only taken into account on first staff.

# Basic notations

These rules are defined by the module [Easyscore](https://github.com/0xfe/vexflow/wiki/Using-EasyScore) on
which `extension-name` is based.

## Structure of the markup

Basic markup syntax to display a system is :

```
:::vexflow
options [opts...]
staff [opts...]
  bar [opts...]
    ...
    [...]
  [bar...]
[staff...]
:::
```

- `options` is optional (obviously) and allows to define global parameters.
- `staff` must be present at least once. staff-specific options may be defined on the same line.
- `bar` must be present at least once under each `staff`. bar-specific options may be defined.
- Series of notes may be defined under each `bar`, in one or multiple lines (which are concatenated)

## Note height and duration

Note are defined with the syntax "`[A-H]ALTER?[0-9](/DUR)?`", where :
- [A-G] : The note (anglosaxon notation)
- ALTER : (optional) an alteration. Possible values are :
  - n : natural
  - #, ## : sharp / double sharp
  - b, bb : flat / double flat
- [0-9] : the octave (C4 is the middle piano C key)
- /DUR : The duration of the note : 
  - w : whole note (4 beats)
  - h : half note (2 beats)
  - q : quarter note ( 1 beat = ♩ )
  - 8 : heighth ( 1/2 beat )
  - 16 : Sixteenth note (1/4 beat)
  - and so on...
  - the 'dot' notation may be used (ie. "h." means 3 beats)
  - the duration is mandatory only for the first note in a measure. If omitted,
    the value is the same than for the preceding note.

The notes are separated by a comma.

**Example :** the G major scale would be written (with eight notes)

```
:::vexflow
staff
  bar
    G4/8, A4, B4, C5,
    D5, E5, F#5, G5
:::
```

:::vexflow
staff
  bar width=300
    G4/8, A4, B4, C5,
    D5, E5, F#5, G5
:::

## Chords

Chords (multiple notes, same time and duration) are defined with the syntax "`(note1 note2...)(/DUR)?`"

**Example :**

```
:::vexflow
staff 
  bar
    (C4 E4 G4)/q,     (C4 Eb4 Gb4 A4),
    Bb4,              (D4 G4 B4)
:::
```


:::vexflow
staff
  bar width=300
    (C4 E4 G4)/q, (C4 Eb4 Gb4 A4),
    Bb4,          (D4 G4 B4)
:::