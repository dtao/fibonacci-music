# Fibonacci Cascade

A generative music toy in a single HTML file. It plays arpeggios climbing through the
octaves, with each note lasting a Fibonacci number of pulses (2, 3, 5, 8, 13 …) and
fading as it rises. Tapping the screen seeds a new layer, snapped to a sixteenth-note
grid, so layers cascade over one another.

The screen is split into three invisible zones along its longer axis (left, middle,
right in landscape; top, middle, bottom in portrait). Each zone seeds a different
arpeggio, and each cycle of the arpeggio repeats one octave higher:

| Zone   | Notes                 | Colour  |
| ------ | --------------------- | ------- |
| first  | C · E · G · B         | blue    |
| middle | A · C · E · A · B     | amber   |
| last   | F · A · C · E · G · B | magenta |

Each layer is drawn as a Fibonacci spiral of golden squares. A note lights the quarter
arc of its square, and because an arc's length is proportional to the note's length,
the glow travels the spiral at constant speed. The viewport zooms out as the spirals grow.

## Run it

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

No build step and no dependencies.

## Controls

- Tap or click anywhere to seed a new layer at that point. Keys 1, 2 and 3 seed each arpeggio at a random spot; the space bar picks one at random.
- The **pulse** slider sets the length of one pulse for new layers. A beat is sixteen pulses, so the readout also shows the tempo in BPM (50 ms is 75 BPM).
- **beat** adds a kick on every beat and a snare on 2 and 4 at that tempo. While it is on, new layers wait for the next beat, so their first note always lands on the beat even if you tap between beats. The four dots show the bar position. The B key toggles it.
- **Reset** clears all layers and starts over.

At most 96 layers play at once. When a new layer would go over that limit, the oldest
active layer is retired: it plays no further notes, and its volume and spiral fade out
together over three seconds. The oldest layer is always the quietest, so nothing cuts out.
