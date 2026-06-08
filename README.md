# Drone Swarm Visualizer

Interactive educational visualizer paired with a self-paced curriculum on swarm intelligence, distributed coordination, and counter-UAS (C-UAS) defense. Built as a Socratic learning companion — every module pairs theory with a live, controllable simulation.

**Live demo:** https://aerwinapollo01.github.io/drone-swarm-visualizer/

## Curriculum

The visualizer follows two interlocking curricula. The first teaches how drone swarms work; the second teaches how to defend against them. By design, every architectural choice that makes a swarm robust (Modules 1-5) becomes a defensive problem (C-UAS Modules) — the two curricula illuminate each other.

### Part I — Swarm Intelligence

- **Module 1 — Architecture.** Side-by-side centralized vs. decentralized swarms. Kill the controller or random drones and watch SPOF cascade failure vs. mesh self-healing in real time. Live latency and bandwidth meters illustrate O(N) vs. O(k) scaling.
- **Module 2 — Boids.** Reynolds' three-rule flocking algorithm with live sliders for separation/alignment/cohesion weights and radii. Click any boid to inspect its per-frame force breakdown. Toggle between metric and topological (k=7) neighbor sensing — the trick starlings use.
- **Module 3 — Mesh & Gossip.** Mesh networking with realistic signal attenuation (link strength fades inverse-square with distance). Inject true detections, false positives, and false no-fly zones to see how quorum-based gossip propagates and self-corrects (or doesn't). Hidden-node, partition, and relay scenarios included.
- **Module 4 — Path Planning.** Five scenarios drawn directly from the curriculum: local minima trap, doorway deadlock, frontier exploration with fog of war, bottleneck traffic, and stigmergy/pheromone coordination. Toggle A*, force vectors, potential field heat map, and velocity-obstacle cones.

### Part II — Counter-UAS

- **C-UAS 1 — Kill Chain.** Interactive layered-defense simulator. A drone approaches a defended asset; the user toggles four defensive layers (Outer 5 km · Middle 3 km · Inner 1 km · Terminal 200 m) and adjusts drone speed (10-120 m/s). Watch the five-stage kill chain (Detect → Track → Identify → Decide → Engage) race the clock. Fast drones + missing layers = IMPACT; full layered defense + slower threats = DEFENDED. Designed to make "time is the hidden constraint" visceral rather than abstract.
- **C-UAS 2 — Detection & Tracking.** Sensor fusion simulator with all four sensor types — Radar, RF, Acoustic, EO/IR — each drawn as a live coverage ring whose effective range collapses or expands based on the selected drone profile and environment. Five drone profiles (Consumer, FPV, Autonomous, Hovering, Stealth) and three environment sliders (Wind, Urban Clutter, Thermal Noise) reveal the catastrophic blind spots: switch to Autonomous and watch RF go BLIND; switch to Hovering and watch radar collapse from the Doppler problem; crank wind to kill acoustic. A fusion-confidence bar shows how multi-sensor agreement raises certainty.
- **C-UAS 3 — Identification & Decision.** Decision-flow simulator built around the four failure modes — false positive, missed threat, decision latency collapse, and authority failure. Four scenarios pit the user against different ground-truth conditions: confirmed hostile, same threat with no legal authority, ambiguous benign drone, and a spoofed-Remote-ID adversarial case. An identification stack (track quality, Remote ID, classifier, behavior) builds in real time into a hostile-confidence score. The user escalates through ROE (Observe → Warn → Non-Kinetic → Kinetic), each step incurring approval latency, with steps locked out when the user's authority cannot reach them. Encodes the actual U.S. legal layer (18 U.S.C. § 32, 47 U.S.C. § 301, FAA Part 89) into a playable system.

### Reference

- **Glossary.** 35+ searchable terms spanning both curricula, with module tags.

## Stack

Single `index.html` file. Vanilla JS, Canvas 2D API, no build step, no npm dependencies, no external network calls. ~3,800 lines, deploys as static HTML.

## Running locally

```bash
npx serve .
```

Then open the URL printed in the terminal.

## Visual style

Modules are framed as a **command-and-control (C2) operations display**: each Swarm Intelligence module opens with an operational header strip (module designation, system LED, asset/mode/protocol callouts, and a live mission elapsed timer `T+ HH:MM:SS`), and canvases are bracketed in HUD-style corner marks. The educational content — theory panels, sliders, scenario buttons, glossary — is unchanged underneath; the C2 chrome is just a frame that makes the simulations feel like an operator's screen rather than a textbook demo.

## Pedagogical approach

The simulations are not demos — they are diagnostic tools. Each module asks you to predict what will happen before you press the button, then shows you whether you were right. Failure scenarios are first-class: the goal is to develop the engineering intuition for what breaks, not just admire what works.
