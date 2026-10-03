# Fibonacci Cascade

A generative music toy in a single HTML file. It plays a Cmaj7 arpeggio (C, E, G, B)
climbing through four octaves, with each note lasting a Fibonacci number of pulses
(2, 3, 5, 8, 13 …) and fading as it rises. Tapping the screen seeds a new layer,
snapped to the eighth-note grid, so layers cascade over one another.

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

- Tap or click anywhere to seed a new layer at that point (space bar also works).
- The **pulse** slider sets the length of one pulse (a sixteenth note) for new layers.
- **Reset** clears all layers and starts over.
