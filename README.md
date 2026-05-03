# 🌟 Neon Orbital

*Interactive gravitational N-body simulator. Place glowing planets, watch them orbit, collide, and dance under mutual gravity. Adjust gravity constant, trail length, mass range, initial count. Click to add, right-click to delete. Neon trails, real-time physics. Zero-pressure cosmic toy.*

---

## What is this?

A gravity playground. Multiple planets exert gravitational pull on each other. Each planet has mass, position, velocity. They accelerate according to Newton's law of universal gravitation. Watch orbits form, systems stabilize, or chaotic interactions ensue. Planets leave glowing trails that fade slowly. Click anywhere to drop a new planet with a sensible initial velocity. Right-click a planet to remove it. Adjust gravity strength, trail length, mass range, and initial system size. It's a hypnotic simulation of celestial mechanics.

---

## Features

- **N-body physics** — every planet attracts every other
- **Real-time integration** — simple Euler step (good enough for visual toy)
- **Glowing trails** — each planet leaves a fading neon path
- **Interactive placement** — left-click to add planet; right-click to delete
- **Adjustable parameters:**
  - Gravity constant (G) — strength of attraction
  - Trail length — how many past positions to remember
  - Min/Max mass — range for new planet masses
  - Initial planet count — size of starting system
- **Controls:** Pause/Resume, Reset (clear all), Random System
- **Stats overlay** — planet count, FPS
- **Single HTML file** — no dependencies

---

## How to Use

1. Open `index.html`
2. An initial random system of planets appears, moving and attracting each other
3. **Watch** — orbits may stabilize, planets may fling off, collisions may happen (they pass through for now)
4. **Add a planet** — left-click anywhere. The new planet gets an initial velocity roughly tangential to the center, encouraging orbital motion
5. **Delete a planet** — right-click directly on a planet to remove it
6. **Adjust sliders** to change simulation behavior:
   - **Gravity** — higher = stronger pull, tighter orbits
   - **Trail Length** — longer trails show more history
   - **Min/Max Mass** — affects planet size and gravitational influence
   - **Initial Planets** — how many to generate on Reset/Random
7. **Pause** — freeze simulation to admire the current state
8. **Reset** — clears all planets (you start from empty)
9. **Random System** — generates a fresh random configuration

---

## Physics Details

- Force between two planets: `F = G * m1 * m2 / r²`
- Direction: along the line connecting centers; attractive
- Softening: a minimum distance squared clamp avoids singularities when planets get very close (prevents extreme forces)
- Integration: `v += F/m * dt`, `p += v * dt` (Euler with dt ≈ 1 frame)
- Boundary: planets bounce off screen edges with damping (0.8) to keep them in view
- Trail: each planet stores last N positions; drawn as a gradient line fading from recent (opaque) to old (transparent)

---

## Technical Notes

- Canvas 2D rendering with `requestAnimationFrame`
- Trail gradient via `createLinearGradient`
- Glow via `shadowBlur` on planet circles and trails
- O(N²) force computation per frame; with N ≤ 15–20 this is trivial
- Mass determines radius: `radius ≈ sqrt(mass) * 1.5`
- Initial velocity approximation for random planets: `v ≈ sqrt(G * constant / distance)` tangential to center to give roughly circular orbit
- Right-click deletion uses distance check against planet radius

---

## The Real Story

Gravity simulations are endlessly fascinating. A few simple rules produce complex emergent behavior — stable orbits, binary systems, slingshot effects, chaotic scattering. The neon trails make it easy to see patterns: rings, spirals, rosettes. Placing your own planet and watching it settle into a dance with the others is deeply satisfying. It's like playing with a cosmic choreography machine.

Random System often yields surprising configurations. Some planets get ejected. Some form tight binary pairs. Some dance in harmony for hours. No two runs are the same.

---

*Made with ✨ and a lot of attraction during a heartbeat build cycle.*

**Repo:** https://github.com/Kiloooai/neon-orbital
