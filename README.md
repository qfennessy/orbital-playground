# orbital-playground

A 3D interactive orbital mechanics simulator built with Three.js. Experiment with satellite launches, orbital physics, and watch dramatic crashes into a procedurally-generated planet.

## Features

- **Interactive 3D Launch System**: Click and drag to launch satellites with custom positions and velocities
- **Realistic Orbital Physics**: Newtonian gravity simulation with accurate force calculations
- **Geosynchronous Orbits**: One-click deployment of satellites with stable geosynchronous orbits at various inclinations
- **Procedurally Generated Planet**: Beautiful Earth-like planet with continents, oceans, ice caps, and animated clouds
- **Dynamic Explosions**: Spectacular collision effects with particle systems, shockwaves, camera shake, and screen flash
- **Customizable Parameters**: Adjust satellite size, orbital height, velocity, and simulation speed in real-time
- **Visual Guides**: 3D grid, axis helpers, and orbital reference rings to help visualize spatial relationships
- **Persistent Trails**: Each satellite leaves a colored trail showing its orbital path

## How to Run

Simply open the HTML file in any modern web browser:

```bash
open orbital-simulator.html
```

Or double-click the file in your file explorer. The simulator requires an internet connection to load the Three.js library from CDN.

## Controls

### Camera
- **Click & Drag** (left or right mouse button): Rotate view around planet
- **Scroll**: Zoom in/out
- **ESC**: Cancel launch mode

### Launching Satellites
1. Click **"Launch Satellite"** button to enter launch mode
2. Click where you want to place the satellite
3. Drag to set the initial velocity (arrow shows direction and magnitude)
4. Release to launch
5. Drag horizontally for orbital motion, vertically for radial velocity, or diagonal for combined trajectories

### Buttons
- **Launch Satellite**: Enter interactive launch mode
- **Launch Geosynchronous**: Automatically add a satellite in geosynchronous orbit
- **Hide/Show 3D Guides**: Toggle spatial reference guides
- **Clear All Satellites**: Remove all satellites from the simulation

### Sliders
- **Satellite Size**: Adjust the size of newly launched satellites (2-15 units)
- **Orbital Height**: Default orbital altitude for launches (80-400 units)
- **Velocity**: Reserved for future use (currently set by drag length)
- **Simulation Speed**: Control time scale (0.1x - 5.0x speed)

## Physics Simulation

The simulator implements Newtonian gravity:

```
F = G * M * m / r²
```

Where:
- `G` = Gravitational constant (100, scaled for visualization)
- `M` = Planet mass (1000)
- `r` = Distance from planet center

Geosynchronous satellites are calculated using Kepler's third law to match the planet's rotation period, maintaining their position relative to the surface regardless of orbital inclination.

## Technical Details

- **Framework**: Three.js (r128)
- **Rendering**: WebGL with custom GLSL shaders for planet surface and atmosphere
- **Physics**: Custom integration using velocity Verlet method
- **Planet Features**:
  - Procedural noise-based continents using fractal Brownian motion
  - Separate cloud layer with animated movement
  - Atmospheric glow using rim lighting
  - Specular ocean highlights
- **Performance**: 60 FPS with dozens of satellites

## Customization

Want to experiment with different physics? Key parameters to modify in the code:

- `G = 100`: Gravitational constant (line 615)
- `planetMass = 1000`: Mass of the central body (line 616)
- `planetRadius = 50`: Size of the planet (line 344)
- `maxTrailLength = 100`: Number of trail points (line 884)

## Future Enhancements

Potential additions:
- Multiple planets with gravitational interactions
- Lagrange points visualization
- Orbital maneuvers (Hohmann transfers)
- Save/load orbital configurations
- Multiplayer synchronized simulations
