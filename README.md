# Dungeon

A browser-based, top-down arena shooter with procedural floors, wave combat, bosses, and roguelike-style upgrades. The entire game ships as one self-contained HTML file: no build step, no npm install, no bundler.

**Live site:** [dungeon.toeffe.uk](https://dungeon.toeffe.uk)

---

## Project description

**Dungeon** drops you into large hand-crafted-feeling maps that are actually generated anew each floor. You fight escalating waves of enemies, spend gold in a shop, open chests for loot, and pick stacking upgrades when you level up. Every few waves you face a boss; defeating it opens a portal to the next floor, where the biome shifts (forest → swamp → rocky → tundra → volcanic), difficulty ramps, and the loop continues until you fall.

Combat is fast and readable: aim with the mouse, move with WASD, dash through danger, and combine weapons with dozens of passive effects (pierce, chain lightning, burn, freeze, life steal, bullet time on dash, and more). The presentation uses Canvas 2D with procedural tile patterns, particles, screen shake, and a minimap—again, all implemented inline in `index.html`.

---

## Features

- **Procedural maps** — Rooms, walls, spawn/exit placement, tree cover, and boss arenas per floor; seeded variation between runs and floors.
- **Biomes by depth** — Visuals and ground patterns change as you descend (forest through volcanic).
- **Wave structure** — Regular waves with a finite enemy pool, grace periods between waves, then a **boss wave**; after the boss, advance to the next floor.
- **Progression** — XP and levels, gold from kills, combo timing, and **three-choice level-up picks** (common / rare / legendary upgrades with stack limits).
- **Economy** — Shop NPC near spawn (locks when waves start on a floor) with heals, stats, crit, weapons, and more.
- **Arsenal** — Pistol, shotgun, laser, bouncer (ricochet), sniper, grenades; weapons also appear from chests and drops.
- **Enemies & effects** — Status effects (burn, poison, freeze, stun), slow fields, ghost allies from certain upgrades, boss attack patterns.
- **Responsive layout** — 960×540 logical resolution, scaled to fit the viewport while keeping a 16:9 aspect ratio.
- **Touch** — Touch drags map to the same aiming/shooting model as the mouse (useful on phones/tablets).

---

## Controls

| Input | Action |
|--------|--------|
| **W A S D** or **arrow keys** | Move |
| **Mouse** | Aim |
| **Left click** (hold) | Shoot |
| **Space** | Dash (direction of movement) |
| **E** | Interact: chests, shop, weapon pickups, portal |
| **Tab** | Open level-up choice screen when a level-up is pending |
| **Hold any key or mouse button** (on game over) | Restart |

The in-page hint bar lists: `WASD · mouse shoot · SPACE dash · E chest / shop / weapon / portal`.

---

## Requirements

- A **modern desktop or mobile browser** with **Canvas 2D** and **`OffscreenCanvas`** (used for procedural tile textures). Current Chromium, Firefox, and Safari releases are suitable.

---

## Running locally

**Option A — open the file**

Double-click `index.html` or open it from the browser’s File menu. Some browsers restrict certain APIs when using the `file://` URL; if anything misbehaves, use Option B.

No dependencies, no compile step.

---

## Repository layout

| Path | Purpose |
|------|---------|
| `index.html` | Full game: markup, styles, and all JavaScript (~3.8k lines). |
| `LICENSE` | Apache License 2.0 |
| `CNAME` | Custom domain for GitHub Pages (`dungeon.toeffe.uk`) |

---

## Tech stack

- **HTML5** + **CSS** (minimal UI chrome)
- **Canvas 2D** rendering
- **Vanilla JavaScript** (no frameworks)
- **`OffscreenCanvas`** for texture/pattern generation
- **`requestAnimationFrame`** game loop

---

## License

This project is licensed under the **Apache License 2.0**. See [LICENSE](LICENSE) for the full text.

---

## Contributing / hacking

All game logic lives in `index.html` inside a single `<script>` block. Search the file for section banners (e.g. `GAME STATE + INIT`, `WEAPONS`, `SHOP`, `UPGRADE SYSTEM`) to jump to major systems. Keep edits focused; the file is large but intentionally self-contained for easy hosting and forks.
