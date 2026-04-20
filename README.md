# Pure CSS Logic Engine: Animated Nativity Scene

This project is a technical demonstration of a fully functional game and animation sequence built entirely with **HTML5 and CSS3**. It uses a memory-match mechanic to "build" a traditional Nativity scene (Pesebre) using declarative logic and **zero JavaScript**.

**Deployment:** https://jeffer512.github.io/Memorama-Navidad-CSS/

## Project Origin
This project was originally developed as a group assignment during a web development bootcamp. The original codebase was audited to remove redundant CSS selectors. Specifically, invalid general sibling combinators (~) attempting to target elements preceding the trigger in the DOM.

## Technical Implementation

### 1. Declarative State Management
The game state is managed through the "Checkbox Hack."
*   **Data Storage:** Hidden `<input type="checkbox">` elements act as the database for the game.
*   **Logic Gates:** The **Adjacent Sibling Combinator (`+`)** is used to detect successful matches. For example, `#card1:checked + #card2:checked` triggers a specific state change that only occurs when both related inputs are active.

### 2. Match-Triggered Animations
When a pair is successfully matched, the CSS logic triggers a multi-stage visual sequence:
*   **Visibility Toggles:** The `controlDisplay` and `controlOverlay` keyframes manage the `opacity` and `pointer-events` of the scene elements. This allows characters to appear in the Nativity scene only after their corresponding cards are matched.
*   **Movement Mechanics:** The `animation` keyframe uses `translateY` to "drop" characters into the scene and `rotate` to create a slight wobble, simulating a 2D paper-cutout or pop-up book effect.

### 3. Layered UI & Scene Building
The project uses a strict Z-index hierarchy to manage the interaction between the game grid and the resulting scene:
*   **`main-tapas`**: The primary container for the Nativity scene, which remains hidden until the logic gates are satisfied.
*   **`overlay-main-tapas`**: A semi-transparent background that appears during character animations to provide visual focus.
*   **Absolute Positioning:** Each character (Maria, Jose, Jesus, etc.) is positioned using percentage-based coordinates to ensure the scene builds correctly across different screen sizes.
