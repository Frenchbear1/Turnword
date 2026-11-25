# Turnword

Type a word, style it, then spin its outline around any axis to make 2D patterns and 3D shapes.

Everything is in a single file, `index.html`. Open it in a browser or host it with GitHub Pages; there is no build step. Three.js r128 and Google Fonts load from CDNs.

## What it does

**Text**
- 35 fonts, weight, italic, case, letter and line spacing, alignment, slant and arc bend
- Hollow (outline-only) letters, which also feed the 3D shapes

**2D effects**
- Solid, gradient or rainbow fill, outline stroke, glow and background colour
- Copies rotated around a movable pivot (spirograph patterns), with total rotation, grow or shrink per copy (spirals), fade, hue shift, blend modes, mirroring, spin and zoom

**3D shape**
- **Spin the outline:** the letter outlines are swept around an axis. Set the axis angle, its tilt in depth and its position (top, middle, bottom or outside the letters for a ring), the sweep angle and the number of steps. Show it as a solid surface, outline copies, point trails or a point cloud, and optionally animate the sweep.
- **Solid + bend:** extruded text with twist, ring wrap, curl, wave and taper, plus copies around the axis with an optional rise per copy (spiral stairs)
- Materials: chrome, clay, glass, toon, rainbow normals and wireframe, with colouring by height, distance from the axis or position around the spin

**View**
- Drag to orbit, pinch or scroll to zoom
- Optional auto-spin
- View buttons (Front, Back, Left, Right, Top, Bottom, 3/4): tap to lock a view and tap again to release it, or press and hold to peek and let go to spring back

**Code tab**
Live, copyable code for the current result:
- 3D embed (HTML + Three.js)
- 2D embed (canvas, exact)
- 2D embed (pure HTML + CSS, approximate)
- All settings as JSON

**Presets & save**
- 15 presets, "Surprise me" and reset
- Save the view as a PNG, or export the 3D shape as an STL (inside a .zip)
- Settings are remembered in the browser

## How the 3D works

The text is drawn to an offscreen canvas. Marching squares traces its outline into small line segments and fills its inside with triangles. Each segment is then either rotated step by step around the chosen axis (Rodrigues' rotation) to make a surface of revolution, or extruded and bent for the solid modes.
