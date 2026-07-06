# Chef in a Hurry

![CS50x](https://img.shields.io/badge/CS50x-Problem%20Set%200-blue?style=for-the-badge&logo=harvard&logoColor=white)
![Scratch](https://img.shields.io/badge/Made%20with-Scratch-orange?style=for-the-badge&logo=scratch&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

Final project for **Problem Set 0** of [CS50x](https://cs50.harvard.edu/x/) (Harvard University), built in Scratch.

## Game Description

Chef in a Hurry is a game where you control a frying Bowl that catches ingredients falling from the top of the kitchen. Catching an apple adds points; catching a frog costs a life. The goal is to reach 15 points before losing all 3 lives. Fall speed increases over time, raising the difficulty progressively.

## Requirements Checklist

- ✅ At least 2 sprites (one different from the cat) — 3 sprites: `Bowl`, `Apple`, `Frog`
- ✅ At least 3 scripts total — 4 scripts across the 3 sprites
- ✅ At least 1 conditional — `if <touching...?> then / else` for collisions, `if <lives <= 0>` for game over
- ✅ At least 1 loop — `forever` blocks for movement, falling, and state checks
- ✅ At least 1 variable — `points`, `lives`, `fallSpeed`
- ✅ Custom block with at least 1 input — `resetIngredient (speed)`
- ✅ Intermediate complexity — multiple sprites, independent logic, progressive difficulty, win/lose conditions

## Sprites Used

- **Bowl** — controlled by the player with left/right arrow keys. Moves horizontally at the bottom of the stage. Contains initialization and game-over logic.
- **Apple** — good ingredient. Falls continuously; catching it adds a point and repositions it via the custom block.
- **Frog** — bad ingredient. Falls the same way; catching it subtracts a life instead of adding points.

## Variables

- `points` (all sprites) — counts apples caught. Reaching 15 wins the game.
- `lives` (all sprites) — starts at 3, decreases on each frog caught. Reaching 0 ends the game.
- `fallSpeed` (all sprites) — controls fall rate. Increases slightly each time `resetIngredient` is called.

## Game Logic

On green flag click, variables initialize (`points = 0`, `lives = 3`, `fallSpeed = 4`) and each sprite starts its own `forever` loop. `Bowl` responds to arrow keys, while a second loop continuously checks for game-over conditions.

`Apple` and `Frog` fall independently. On touching `Pan` or the bottom edge, they call `resetIngredient`, which repositions them at the top and slightly increases `fallSpeed`. The game ends when `lives` reaches 0 (loss) or `points` reaches 15 (win).

## Challenges & Solutions

**Ingredients weren't falling continuously**
Using `wait until <touching...?>` froze the sprite in place. Fixed by using a `forever` loop with `change y by (fallSpeed * -1)` each iteration, with collision checks in an `if/else` inside the same loop.

**Confusion with the custom block's input**
The `speed` parameter is local to the block definition. Fixed by using it to update the global variable `fallSpeed` (`set [fallSpeed] to (speed + 0.5)`), so the effect persists after the block runs.

**Ingredients resetting to the same position**
Used `pick random (-220) to (220)` inside `resetIngredient` to vary the horizontal position on each reset.

**Game not stopping correctly on win/loss**
Replaced `stop [this script]` with `stop [all]` to freeze every script when a win/loss condition is met.

## Demo

Play "Chef in a Hurry" on Scratch:  
https://scratch.mit.edu/projects/1351728496/

## Screenshots
<img width="946" height="445" alt="Game" src="https://github.com/user-attachments/assets/71a430da-a86a-4465-9841-9be433b94371" />
<img width="947" height="446" alt="gameplay2" src="https://github.com/user-attachments/assets/40f959fe-86b3-4ddb-b0ac-3931b2ffe5bd" />
<img width="944" height="439" alt="YA" src="https://github.com/user-attachments/assets/b63c7194-a25c-4056-90cb-410abd06e23f" />



## Technologies Used

- [Scratch](https://scratch.mit.edu/) 
- [CS50x](https://cs50.harvard.edu/x/) 

## Author & License

**[Santiago Moreno]** — GitHub: [@santiagoamorenom14-cell](https://github.com/santiagoamorenom14-cell) — Course: CS50x, Problem Set 0

Licensed under the MIT License. See [LICENSE](./LICENSE) for details.
