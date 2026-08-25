# 3D Website Tutorial — Interactive Chocolate Donut

A beginner-friendly example of how to put a 3D model on a webpage. Scroll to orbit the camera, drag to spin the model. No frameworks, no build tools — just one HTML file and a `.glb` model.

Built with [three.js](https://threejs.org). Model made in Blender, exported as `.glb`.

## What you'll learn

- Loading a 3D model (`.glb`) into a webpage with three.js
- Scroll-driven camera movement
- Drag-to-spin interaction
- How to swap in your own 3D model

## Quick start

```
git clone https://github.com/MominaAli1/3dWebsite
cd 3dWebsite
python -m http.server 8000
```

Open `http://localhost:8000` in your browser. Use `python3` on Mac/Linux.

> **Note:** You must use a local server. Double-clicking `index.html` won't load the model.

## Files

| File | What it is |
|---|---|
| `index.html` | All the HTML, CSS, and three.js code in one file |
| `model.glb` | The 3D chocolate donut model |

## Use your own model

Replace `model.glb` with your own file (keep the same filename). The code auto-centres and resizes it.

**From Blender:** File > Export > glTF 2.0, format `.glb`, compression off.
**Or grab one from:** [Sketchfab](https://sketchfab.com)

## Customise it

Edit the `SETTINGS` block near the top of the `<script>` tag in `index.html`:

| Setting | What it does |
|---|---|
| `modelSize` | bigger number = bigger model |
| `lens` | low = zoomed/flat, high = wide/distorted |
| `brightness` | exposure level |
| `spin` | auto-rotation speed. 0 = still, negative = reverse |
| `drift` | camera lag on scroll. 1 = instant, 0.02 = floaty |
| `start` | camera position at the top of the page |
| `end` | camera position at the bottom |

`start` and `end` each take three values:

- **distance** — how far from the model
- **height** — 0 = level, 2 = looking down, -1 = looking up
- **angle** — degrees. 0 = front, 90 = right, 180 = behind

## How it works

1. Scroll position becomes a number from 0 (top) to 1 (bottom)
2. That number blends between the `start` and `end` camera positions
3. Dragging the model adds rotational speed, which decays over time (`speed *= 0.94`)
4. Everything that moves runs inside `animate()`, called ~60 times per second

## Deploy

Any static host works — GitHub Pages, Vercel, Netlify. No build step needed.

## Troubleshooting

| Problem | Fix |
|---|---|
| Blank page | Open browser console (F12) to see the error |
| Model doesn't load | Check the Network tab for `model.glb`. A 404 means wrong path or filename |
| "No DRACOLoader instance provided" | Your `.glb` is compressed. Re-export with compression off |
| Model is invisible | Increase `modelSize` or decrease `distance` |
