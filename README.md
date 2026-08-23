# AHAB — a whaling strategy in six chapters

A small browser game after Melville's *Moby-Dick*, rendered in three.js.

Gather timber, provisions and coin along the New Bedford wharves; raise the
Spouter-Inn and sign Queequeg, Tashtego and Daggoo; provision the Pequod, nail
the doubloon to the mainmast and put to sea. Hunt sperm whales for oil, then
settle accounts with the White Whale over three days.

## Playing

Open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000   # then visit http://localhost:8000
```

Tap a tree, drying rack or crate and the nearest idle sailor works it; tap a
sailor first to command that one in particular. Buttons below the map raise
buildings and sign crew. At sea, tap a whale to lower the boats.

During the chase, watch for Moby Dick to turn his brow on the ship — that is a
charge, and it costs hull. Oil is the only currency against him: mend the boats
(25), mend the hull (30), grind the irons for extra damage (40).

### Skipping ahead

The title page has links for it, or go straight there by URL:

| | |
|---|---|
| `index.html#hunt`  | the first lowering, fully outfitted |
| `index.html#chase` | day one of the three-day chase |
| `index.html#day2` / `#day3` | a later day of the chase |
| `index.html#god`   | the chase, with a hull that cannot be stove in and casks that never empty |

## Notes

Everything lives in the single `index.html`. three.js is loaded from a CDN via
an import map, so the first load needs a network connection; the page needs
WebGL. The whole scene is procedural — hulls and whales are lofted from
profile curves at runtime, the sea is a displaced plane with a wave shader,
and the skies are painted to canvas and used as both background and image-based
lighting. There are no external assets.

The game logic still thinks in the original 1000×620 plane; that plane is
mapped onto the 3D ground and every tap is raycast back into it.
