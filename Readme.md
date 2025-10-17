
 # 🧩 2048 — Minimal Functional JavaScript Implementation

A minimal yet fully functional implementation of the classic **2048** puzzle game, built entirely in **vanilla HTML, CSS, and JavaScript** — with a focus on **functional programming principles**, **state management**, and **clean UI rendering**.

---

## 🎮 Live Demo

🔗 **Play here:** https://satwik259.github.io/2048-GUI/

---

## 🧠 Overview

This project demonstrates:
- Pure, functional **JavaScript logic** for all gameplay mechanics.
- A clean, responsive **graphical user interface (GUI)** using HTML & CSS Grid.
- Proper **state management** and UI updates without external frameworks.
- A fully **self-contained static application** deployable anywhere (GitHub Pages, Netlify, etc).

---

## ⚙️ Installation

### 1. Clone the repository
```bash
git clone https://github.com/Satwik259/2048-GUI.git
```

### 2. Open the game
You don’t need Node.js or any server — just open the file:

```bash

open index.html  # (macOS)
start index.html # (Windows)
```

## 🧩 Gameplay Instructions

1. **Goal:** Combine matching tiles to reach the 2048 tile.
2. **Controls:**
   - Use **Arrow keys** or **WASD** to move tiles.
   - You can also use the **on-screen arrow buttons**.
3. **Merging:**
   - When two tiles with the same number touch, they merge and form a new tile (sum of both).
   - Each move adds a new random tile (either 2 or 4).
4. **Scoring:**
   - Every merge adds that tile’s value to your score.
   - Your **best score** is saved locally using `localStorage`.
5. **Winning / Losing:**
   - Reach **2048** → 🎉 You win!
   - No empty cells & no possible merges → 💀 Game Over.
6. **Restart:**
   - Press **R** or click **Restart** to start fresh.
   - You can change the **grid size** (3×3 to 6×6) anytime.

---

## ⚙️ Implementation Details

### 🧩 Architecture Overview
The project follows a **functional programming style**:
- All core logic (merging, grid updates, scoring) is **pure and deterministic**.
- The UI rendering layer is separate from the game logic.
- No external libraries — just HTML, CSS, and vanilla JS.

### 🧱 Core Components

#### 1. State Representation
The game maintains a **state object**:
```js
{
  grid: number[][],   // 2D array representing the board
  score: number,      // current score
  status: "playing" | "won" | "over" // game state
}
```

#### 2. Pure Logic Functions
| Function | Purpose |
|-----------|----------|
| `createEmptyGrid(size)` | Creates an empty grid of given size. |
| `spawnRandomTile(state)` | Adds a new random tile (2 or 4). |
| `compressAndMergeRowLeft(row)` | Slides and merges tiles in a row (core 2048 logic). |
| `rotateLeft`, `rotateRight`, `flipHorizontally` | Grid transformations to reuse logic for all directions. |
| `evaluateGameStatus(grid)` | Checks for win, available moves, or game over. |
| `moveInDirection(state, dir)` | Handles moves for all directions (using transforms). |

All of these are **pure functions**, meaning:
- They **don’t mutate** inputs.
- They **return new copies** of state or grid.
- They are **independent of the UI**, making them testable.

#### 3. Rendering Layer
The DOM layer re-renders after every valid move:
- Creates background `.cell` elements and `.tile` elements dynamically.
- Updates score and best score.
- Shows a **Game Over / You Win overlay** when needed.



