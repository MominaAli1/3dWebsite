# Mi Donut

A 3D donut on a webpage. Scroll to move the camera.

Made with [three.js](https://threejs.org). Model made in Blender, exported as `.glb`.

## Run it

```
git clone https://github.com/MominaAli1/3dWebsite
cd 3dWebsite
python -m http.server 8000
```

Open `http://localhost:8000`. Use `python3` on Mac and Linux.

Don't double-click `index.html`. The model won't load without a server.

## Files

`index.html` — layout, styling, and all the three.js code
`model.glb` — the 3D model

## Use your own model

Replace `model.glb`, keep the filename. The code centres and resizes it automatically.

From Blender: File > Export > glTF 2.0, format `.glb`, compression off.
Or grab one from [Sketchfab](https://sketchfab.com).

## Change the animation

Edit the `SETTINGS` block near the top of the `<script>`.

| Setting | What it does |
|---|---|
| `modelSize` | bigger number, bigger model |
| `lens` | low is zoomed and flat, high is wide and distorted |
| `brightness` | exposure |
| `spin` | constant rotation. 0 is still, minus flips direction |
| `drift` | how lazily the camera follows scroll. 1 snaps, 0.02 floats |
| `start` | camera position at the top of the page |
| `end` | camera position at the bottom |

`start` and `end` each hold three numbers:

- **distance** — how far from the model
- **height** — 0 is level, 2 looks down, -1 looks up
- **angle** — degrees. 0 is front, 90 is right, 180 is behind

## How it works

Scroll becomes a number from 0 to 1. Top is 0, bottom is 1. Multiply that number by anything you want to move.

The spin is separate. Dragging adds speed, and `speed *= 0.94` shaves 6% off every frame until it stops.

Everything that moves lives in `animate()`, which runs 60 times a second.

## Deploy

Any static host. GitHub Pages, Vercel, Netlify. No build step.

## If it breaks

**Blank page** — open the console (F12), it names the broken line.

**No model** — check the Network tab for `model.glb`. 404 means wrong path or wrong capitalisation.

**"No DRACOLoader instance provided"** — your `.glb` is compressed. Re-export with compression off.

**Can't see it** — raise `modelSize`, or lower `distance`.
