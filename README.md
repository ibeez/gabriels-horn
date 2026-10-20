# Gabriel's horn, in letters

A little ASCII math piece. The curve y = 1/x is written in its own values (1, ½, ⅓, ¼ ...), spun around the x-axis, and the horn it makes is spelled out in letters that thin from HORN to horn to h o r n to dots as it narrows toward infinity.

The paradox: the horn holds a finite amount of paint (volume = π) but its surface is infinite, so you could fill it and still never paint it.

[Watch one loop (MP4)](exports/gabriels-horn.mp4)

## Try it

Tap either line at the top:

- **volume = π** spins the horn up and pours paint in. The counter climbs and stops at π.
- **surface = ∞** spins the horn up and starts painting the outside. The counter never stops.

Run it locally (it loads `palette.js`, so open it through a server rather than as a file):

```bash
python3 -m http.server 8765 --bind 127.0.0.1
```

Then open http://localhost:8765/horn.html. Running locally also shows a **Record one loop** button that saves a 10 second MP4 of the canvas.

## How it works

- One canvas, plain JavaScript, no libraries. A surface of revolution is sampled point by point, projected, and z-buffered into a character grid. Each cell picks a letter from the word for its stretch of the horn and a color from its lighting.
- The volume counter uses π(1 − 1/x) for the paint poured up to x, which never passes π. The surface counter paints at a steady rate, and since the area up to x grows like 2π ln x, it never finishes.
- Past x = 3.8 the drawn horn tapers to a point at the edge of the plate. That part is artistic license: the real horn never closes, it just keeps getting thinner.

## Colors

Every color is a real marker swatch, photographed and measured from hand-made swatch sheets. `palette.js` is the single name-to-hex map; change a color there and the piece follows.

## Files

- `horn.html`: the piece
- `palette.js`: marker names to hex
- `exports/gabriels-horn.mp4`: one recorded loop
