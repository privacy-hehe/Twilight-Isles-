# Twilight Isles (Townscaper-Style Engine)

A browser-based, procedural city-building sandbox built with Three.js. This engine replicates the context-aware, grid-snapping magic of games like *Townscaper*, packaged into a single, lightweight HTML file.

# Features

* Context-Aware Architecture: The engine intelligently determines what a block should be based on its surroundings. Blocks on the water become stone foundations; blocks above become houses; exposed blocks automatically generate roofs.
  
* Procedural Texturing: No external image assets are required. The engine utilizes a hidden Canvas API factory to procedurally generate noisy stucco, brick, and terracotta textures on runtime, completely eliminating CORS errors and loading times.
  
* Advanced Geometries: Build with standard blocks, round towers, extruded archways, and sloped wedges. The rotation of arches and wedges dynamically snaps to your camera's viewing angle.
  
* Atmospheric Lighting: A meticulously crafted twilight aesthetic using a combination of cool directional moonlight, warm hemisphere ambient light, and localized point lights to simulate town lanterns.
  
* Edge Rendering: Implements Three.js `EdgesGeometry` with angle thresholds to give the architecture a satisfying, hand-drawn "toy" aesthetic without cluttering curved surfaces.
  
* Mobile-First Controls: Unified pointer events smoothly handle both mouse and touchscreen inputs. The engine includes gesture recognition to separate camera rotation (dragging) from block placement (tapping).

# 🛠 Tech Stack

*   **HTML5 / CSS3:** For the UI overlay and glassmorphism styling.
*   **JavaScript (ES6):** Core game logic, state management, and procedural algorithms.
*   **Three.js (r128):** WebGL 3D rendering engine and math utilities (Raycasting, Vector3 math).

# 🎮 How to Run

Because this project uses entirely procedural textures and relies on CDN-hosted libraries, **no local server or build step is required.**

1. Save the code into a file named `index.html`.
2. Double-click the file to open it in any modern web browser (Chrome, Firefox, Safari, Edge).
3. Ensure you have an active internet connection so the browser can fetch the Three.js library.

# 🕹 Controls

*  Left Click / Tap: Place a block at the cursor location.
*  Right Click: Delete the targeted block.
*  Left Click + Drag / Touch + Drag: Rotate the camera around the island.
*  Scroll Wheel / Pinch: Zoom in and out.
*  UI Panel: Select colors, switch between Build/Delete modes, change block shapes, or clear the board.

# Architecture Highlights

`TextureFactory` Object: Dynamically paints textures to a 2D canvas and converts them to `THREE.CanvasTexture`, enabling infinite asset generation without external fetching.

`updateContext(x, y, z)` Method: The brain of the procedural generation. Whenever a block is added or removed, it checks the block above it (`y + 1`) to determine if a roof should be dynamically added or destroyed.

Angle-Threshold Edges: Uses `new THREE.EdgesGeometry(geometry, angle)` to ensure curved shapes (like domes and cylinders) only draw outlines on sharp corners, preventing a messy wireframe look.

