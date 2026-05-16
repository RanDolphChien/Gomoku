# Gomoku Project Guide

## 1. Project Overview
**Gomoku Professional Edition** is a web-based implementation of the classic Five-in-a-Row strategy game. It features professional rule enforcement, a dynamic gameplay experience, and a polished user interface.

### Key Technologies
- **HTML5**: Core structure and Canvas API for high-performance board rendering.
- **CSS3**: Modern styling including CSS Variables, Flexbox, and animations.
- **JavaScript (ES6+)**: Object-oriented game engine and logic.

### High-Level Architecture
The project follows a simple client-side web architecture:
- **Portal (`index.html`)**: Acts as the entry point/game library, featuring a loading screen and game previews.
- **Game Engine (`Gomoku.html`)**: Contains the core `Gomoku` class which manages state, rendering, AI, and rule validation.
- **Assets (`img/`)**: Contains preview images for the game library.

## 2. Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Edge, or Safari).
- No build tools or server-side environment required (can be run locally via `file://` or a simple local server).

### Installation & Running
1. Clone or download the repository.
2. Open `index.html` in your web browser.
3. Wait for the loading screen to complete.
4. Click on the **Gomoku** card to start playing.

### Basic Usage
- **Playing**: Click on the intersections of the board to place stones.
- **Undo**: Use the "Undo" button to revert the last move (subject to the configured limit).
- **Settings**: Adjust board size and undo limits using the control panel.

## 3. Project Structure

```text
.
├── .continue/
│   └── rules/
│       └── CONTINUE.md      # This guide
├── img/                     # Game preview images
│   └── preview_gomoku.png   # Gomoku thumbnail
├── index.html               # Game Portal / Entry Point
├── Gomoku.html              # Main Game Logic and UI
├── README.md                # Project documentation
└── LICENSE                  # Project license
```

### Key Files
- `index.html`: Manages the "Loading" state and the "Game Library" view.
- `Gomoku.html`: The heart of the project. It contains the `Gomoku` class, which handles:
    - `init()`: Game setup and configuration.
    - `handleClick()`: User input processing.
    - `checkWin()`: Rule-based victory detection.
    - `aiMove()`: Basic proximity-based AI logic.
    - `render()`: Canvas drawing loop.

## 4. Development Workflow

### Coding Standards
- **JavaScript**: Use ES6 classes and modern syntax. Keep game logic encapsulated within the `Gomoku` class.
- **CSS**: Use CSS variables for themes (e.g., `--wood-color`) to ensure consistency.
- **HTML**: Keep structure semantic and use IDs for direct DOM manipulation in JS.

### Testing Approach
- **Manual Testing**: Verify rule enforcement (e.g., the "two-line" rule for Black) and AI responsiveness.
- **Visual Inspection**: Ensure the Canvas rendering is smooth and responsive to different board sizes.

## 5. Key Concepts

### Professional Rules
Unlike standard Gomoku, this version implements a professional constraint: **Black is prohibited from forming two lines of five simultaneously in a single move.** This prevents overly aggressive opening strategies.

### Core Abstractions
- **The Grid**: A 2D array representing the game board state (0: empty, 1: Black, 2: White).
- **The Timer**: A countdown mechanism that triggers the AI move if the player's turn expires.
- **The Canvas**: The primary rendering surface for the game board and pieces.

## 6. Common Tasks

### Changing the Board Size
1. Open `Gomoku.html`.
2. Locate the `<input type="number" id="board-size">` element.
3. Adjust the `min` and `max` attributes if necessary.

### Modifying the AI Difficulty
The current AI uses a proximity-based scoring system. To improve it:
1. Locate the `aiMove()` method in `Gomoku.html`.
2. Enhance the `score` calculation logic to consider patterns (e.g., open threes, blocked fours).

## 7. Troubleshooting

- **Images not appearing in Portal**: Ensure the image exists at `./img/preview_gomoku.png` relative to `index.html`.
- **Canvas looks blurry**: Check the scaling between CSS pixels and Canvas internal resolution.
- **Rules not enforcing**: Verify the `countWinningLines` logic in the `attemptMove` method.

## 8. References
- [HTML5 Canvas API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
- [Gomoku Professional Rules Overview](#) (Internal documentation/Assumed)
