# The Maze Automaton

A single-file, two-state cellular automaton that runs the rule **B3/S12345** — known in the cellular-automaton community as **"Maze."** Starting from a tiny seed, it grows a network of thin walls and empty corridors that reads unmistakably as a maze.

[**Live demo**](https://YOUR-USERNAME.github.io/YOUR-REPO/) · *(update this link after enabling GitHub Pages)*

## What it is

Like Conway's Game of Life, every cell is either alive or dead, and each generation every cell looks at its eight neighbors to decide its next state. What makes a rule is two dials:

- **Born with 3** — a dead cell comes to life only when it has *exactly* 3 live neighbors.
- **Survives with 1–5** — a live cell stays alive when it has 1, 2, 3, 4, or 5 live neighbors. It dies only if it is completely isolated (0 neighbors) or overcrowded (6, 7, or 8 neighbors).

Written in the standard notation, that is `B3/S12345`.

## Running it

No build step and no dependencies — it's one HTML file.

**Locally:** open `index.html` in any modern browser.

**On GitHub Pages:**
1. Push `index.html` to the repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your `main` branch and the `/ (root)` folder, and save.
4. Wait a minute, then visit the published URL.

## Controls

- **Run / Pause** — start or stop the simulation.
- **Step** — advance a single generation.
- **Reset seed** — return to the R-pentomino starting shape.
- **Clear** — empty the board.
- **Random fill** — seed the board with ~30% random noise (a great way to watch corridors self-organize).
- **Speed** — adjust generations per second.
- **Born with / Survives with** — toggle the rule live. The displayed rule name updates as you change it.
- **Click and drag** on the grid to paint your own starting cells.

Try `B3/S123` to tame the growth, or `B37/S12345` ("Mazectric") for longer, straighter corridors.

## Why a maze emerges

The maze is the product of two rules pulling against each other.

The **generous survival band (1–5)** gives the system a strong memory: almost any cell with a neighbor or two survives, so structure that forms tends to persist rather than flicker away. But survival is not unconditional — death by overcrowding at 6+ neighbors punishes solid, filled blocks. A cell buried inside a full region sees eight neighbors and dies, so solid fills are unstable and hollow themselves out from the inside.

The **selective birth rule (exactly 3)** is a thin growth condition. It lets the living region creep outward along its frontier, but only where the local geometry presents precisely three neighbors, so it cannot flood open space. Growth happens as narrow fingers, not sheets.

Together they create a standing tension: **the interior cannot stay solid, and the exterior cannot fill freely.** The system settles into the one geometry that satisfies both constraints at once — walls one or two cells thick separated by empty passages. A wall that grows too thick loses its core to overcrowding; a gap that closes up gets reopened. The stable width that survives everywhere is exactly a wall bordering a corridor, and repeated across the board those interlocking walls form the branching dead-end passages we read as a maze.

Once growth reaches the edges and no cell can find a stable-but-different neighborhood, the walls freeze and the maze becomes a still life — it grows, then locks in.

## Notes

The board is finite with hard edges: cells beyond the boundary count as dead, so walls absorb at the edge rather than wrapping around. Changing to a toroidal (wrap-around) world is a small edit to the neighbor-counting function.

## Credits

The rule B3/S12345 is a well-documented "Life-like" cellular automaton commonly called *Maze*; its relative B37/S12345 is called *Mazectric*. This project was built to explore the maze-forming behavior interactively.
