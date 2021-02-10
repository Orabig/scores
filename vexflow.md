# vexflow

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
    A2/q, E2/q, A3/h
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
- 
