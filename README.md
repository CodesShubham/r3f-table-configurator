[![Releases](https://img.shields.io/github/v/release/CodesShubham/r3f-table-configurator?label=Releases&style=for-the-badge)](https://github.com/CodesShubham/r3f-table-configurator/releases)

# Interactive 3D Table Configurator and R3F Practice Lab

[![3D Canvas](https://img.shields.io/badge/tech-3D%20Canvas-blue?style=flat-square)](https://threejs.org) [![React](https://img.shields.io/badge/framework-react-%2300D8FF?style=flat-square&logo=react)](https://reactjs.org) [![R3F](https://img.shields.io/badge/library-react--three--fiber-%2300D8FF?style=flat-square)](https://github.com/pmndrs/react-three-fiber) [![TypeScript](https://img.shields.io/badge/language-typescript-%23007ACC?style=flat-square&logo=typescript)](https://www.typescriptlang.org)

A compact lab project that lets you design, tweak, and render a 3D table in the browser. It uses React, react-three-fiber (R3F), Three.js and WebGL2. The app doubles as a learning ground to sharpen R3F skills and to test rendering ideas, materials, and shader tweaks.

Release assets live here:
https://github.com/CodesShubham/r3f-table-configurator/releases

Key topics: 3d, canvas, creative-coding, fiber, html5, javascript, laboratory, react, react-three-fiber, three, threejs, typescript, webgl, webgl2.

Built files and quick download
- The Releases page hosts packaged builds and tools.
- Download the file from the releases page and execute it locally or deploy it to your static host. The release asset usually appears as `r3f-table-configurator-vX.Y.Z.zip` or `r3f-table-configurator-vX.Y.Z.tar.gz`.
- If the releases link does not open, check the repository "Releases" section on GitHub.

Preview image
![Table Configurator Preview](https://raw.githubusercontent.com/pmndrs/react-three-fiber/master/docs/static/logo.png)

Why this project
- Practice R3F and Three.js in a focused, visual task.
- Iterate on lighting, PBR materials, and post-processing.
- Test performance tweaks and GPU-side effects.
- See live changes in a small, scope-limited app.

Features
- Live scene editor with GUI controls for:
  - Table size, leg count, and leg style.
  - Top material (wood, metal, glass, mixed).
  - Edge profile and bevel amount.
  - Ambient and directional light presets.
  - Environment maps and HDRI toggles.
- Post-processing stack:
  - FXAA, bloom, vignette.
  - Optional tone mapping and exposure control.
- Geometry modes:
  - Procedural top generation.
  - Extruded legs with chamfer.
  - Boolean-ready slots for add-ons (cup-holder, cable cutout).
- Export:
  - GLTF export for geometry and materials.
  - Screenshot and JSON scene settings export/import.
- Small TypeScript code base for fast iteration.

Live demo and assets
- A dev build and packaged app live on the Releases page. Download the latest build and run the included `index.html` or host it.
- Releases link: https://github.com/CodesShubham/r3f-table-configurator/releases

Quick start (developer)
- Clone the repo.
- Install packages with your package manager.
- Run the dev server that serves a hot-reload R3F scene.
- Use the GUI to change parameters. The scene updates live.

Primary files you will find in the project
- `src/App.tsx` — Entry point and scene layout.
- `src/components/Table.tsx` — Procedural table generator.
- `src/components/Materials.tsx` — PBR material presets and utility helpers.
- `src/components/Env.tsx` — Environment map loader and sky controls.
- `src/hooks/useGPUTweaks.ts` — Small hooks for performance toggles.
- `public/` — Static assets and example HDRI files.

How the scene works (simple)
- React mounts an R3F Canvas.
- The `Table` component uses geometry primitives and buffer attributes for the top and legs.
- Materials use physical-based shading from Three.js.
- Lighting uses an HDRI for global illumination plus a directional key light and rim lights.
- Post-processing runs in a separate composer pass.

Controls and interaction
- Camera: orbit controls with damping and a focus target on the table center.
- Mouse:
  - Left drag to orbit.
  - Right drag to pan.
  - Scroll to zoom.
- GUI:
  - Sliders for dimensions and bevels.
  - Select menus for materials and finishes.
  - Toggles for effects like bloom and AO.
- Keyboard:
  - `R` resets the view.
  - `E` exports GLTF.
  - `S` saves a screenshot.

Config options (examples)
- Table top:
  - Width: 600–2400 mm
  - Depth: 400–1200 mm
  - Thickness: 18–50 mm
  - Profile: flat, bevel, round
- Legs:
  - Type: cylindrical, tapered, box
  - Count: 3–6
- Material:
  - Base: oak, walnut, steel, glass
  - Roughness: 0–1
  - Metalness: 0–1
- Lighting:
  - HDRI intensity: 0–5
  - Key light intensity: 0–10
  - Exposure: 0.1–2

Performance tips
- Use buffer geometries to reduce draw calls.
- Merge static geometry where possible.
- Limit environment map resolution for older GPUs.
- Toggle post-processing effects on mobile.
- Use `useFrame` sparingly and avoid heavy CPU calculations on each frame.

Design notes for contributors
- Keep components small and focused.
- Isolate GPU code into hooks for reuse.
- Prefer typed props and clear defaults.
- Use texture atlases for small texture sets.
- Add unit tests for pure functions, not for rendering.

Suggested development workflow
- Create a feature branch.
- Keep commits small and atomic.
- Open a pull request with a clear description of the change and screenshots.
- Add visual tests if you change a shader or material.

Assets and external resources
- Three.js docs: https://threejs.org/docs
- React Three Fiber: https://github.com/pmndrs/react-three-fiber
- PMND community resources: https://pmnd.rs
- HDRI samples: https://polyhaven.com

Common tasks and how to do them
- Add a new material preset:
  - Create a new entry in `Materials.tsx`.
  - Add textures to `public/textures`.
  - Add a GUI control to select the preset.
- Add a new leg profile:
  - Add a factory in `Table.tsx` that returns geometry for the new profile.
  - Add a sample in the storybook or preview page.
- Export GLTF:
  - Use Three.js `GLTFExporter`.
  - Gather meshes and materials and call `parse` with options.

Testing locally (useful commands)
- `npm install` (or `yarn`) to install deps.
- `npm run dev` to start the dev server.
- `npm run build` to produce a production bundle.
- `npm run preview` to preview the build locally.
- Use the release assets if you want a ready-to-run build.

Example JSON scene export (structure)
- `scene.json` contains:
  - `table`: dimensions, material keys, leg config
  - `lights`: HDRI, key intensity, color
  - `post`: bloom, fxaa, exposure
- Import the JSON through GUI to restore a saved configuration.

Contributing
- Fork the repo and open PRs against main.
- Follow the coding style used in `src`.
- Run linters before opening a PR.
- Include screenshots or short GIFs for visual changes.

License
- The project uses an open license. See `LICENSE` in the repo for details.

Contact and support
- Open an issue on the repo for bugs or ideas.
- For release downloads and ready builds, visit the Releases page:
  https://github.com/CodesShubham/r3f-table-configurator/releases

Badges and credits
[![Made with Three.js](https://img.shields.io/badge/made%20with-Three.js-222222?style=flat-square&logo=three.js)](https://threejs.org) [![R3F Library](https://img.shields.io/badge/react--three--fiber-pmndrs-blue?style=flat-square)](https://github.com/pmndrs/react-three-fiber)

Images and icons used in this README come from official project assets and public sources.