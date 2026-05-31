# Drone Swarm Visualizer

Interactive educational visualizer for swarm intelligence and distributed coordination. Built as a companion to a self-paced curriculum covering five modules: architecture, emergent behavior, mesh networking, path planning, and real-world applications.

**Live demo:** https://aerwinapollo01.github.io/drone-swarm-visualizer/

## What's inside

Five tabs, all running live in the browser with zero dependencies:

- **Module 1 — Architecture.** Side-by-side centralized vs. decentralized swarms. Kill the controller or random drones and watch SPOF cascade failure vs. mesh self-healing in real time. Includes live latency and bandwidth meters.
- **Module 2 — Boids.** Reynolds' three-rule flocking algorithm with live sliders for separation/alignment/cohesion weights and radii. Click any boid to inspect its per-frame force breakdown. Toggle between metric and topological neighbor sensing (starlings use the latter).
- **Module 3 — Mesh & Gossip.** Mesh networking with realistic signal attenuation (link strength fades inverse-square with distance). Inject true detections, false positives, and false no-fly zones to see how quorum-based gossip propagates and self-corrects (or doesn't). Hidden-node demo and partition/relay scenarios included.
- **Module 4 — Path Planning.** Five curriculum scenarios: local minima trap, doorway deadlock, frontier exploration with fog of war, bottleneck traffic, and stigmergy/pheromone coordination. Toggle A*, force vectors, potential field heat map, and velocity-obstacle cones.
- **Glossary.** 30 searchable terms from across the modules.

## Stack

Single `index.html` file. Vanilla JS, Canvas 2D API, no build step, no dependencies.

## Running locally

```bash
npx serve .
```

Then open http://localhost:3000.
