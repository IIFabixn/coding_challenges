# 💡 Rummikub Table Solver Challenge

## 🧩 Description

You're given the **final game state** of a [Rummikub-like](https://en.wikipedia.org/wiki/Rummikub) tile game. The game is represented as:

- A **set of arrays** (called `table`), each representing a **valid meld** (a group or a run)

- An array of **remaining tiles** in the hand of the remaining player (called `hand`)

- An array of **draw pile** stones (called `draw_pile`) that still remain in the bag

Your task is to write an algorithm that simulates what the remaining player **would have played next**, trying to place as many tiles from their hand as possible by manipulating the table.

---

## 🎯 Goal
Simulate the player turn(s).
Returns the final table state.

Optional:
* Track and return a **move log** describing each action taken
* Implement a move limit to simulate timed games
*  **draw one tile** from the draw pile and repeat until the hand is empty.

---

## 🔢 Input Format

All tiles are represented as a **tuple of `(number, color)`**, e.g. `(7, 'green')`.

Note: Jokers are represented as `(0, 'none')`.

You are given:

```python
table: Set[List[Tuple[int, str]]]
hand: List[Tuple[int, str]]
draw_pile: List[Tuple[int, str]]  # top of the pile is at the start
```

---

## 📜 Rules

### ✅ Valid Melds
* **Run (Sequence)**:
A sequence of at least 3 consecutive numbers of the same color <br>
Example: <br> `[(5, 'green'), (6, 'green'), (7, 'green')]`

* **Group (Set)**:
A set of 3 or 4 tiles with the same number in distinct colors <br>
Example: <br> `[(3, 'black'), (3, 'green'), (3, 'violet')]`

### ❌ Invalid Moves
* Groups **can not** contain the same color twice
* Runs **must** be consecutive numbers **and** the same color
* Melds must have **at least** 3 tiles
* At the end of a turn, all tiles on the table must form valid melds

### 🔁 Rearranging
* You may fully rearrange the table:
    * Split, merge, modify existing melds
    * Move tiles from existing melds into new ones
* You can reuse table tiles as long as all tiles are in valid melds when your turn ends

### 🃏 Jokers
* Represented as `(0, 'none')`
* A joker can replace **any** tile
* Jokers can be reclaimed by inserting the exact tile they replace
* A reclaimed joker must be used immediately in the same turn

### 🔄 Draws
* If no move is possible, draw **one** tile from draw_pile
* Try again with the updated hand
* Repeat until:
    * The hand is empty (success), or
    * The draw pile is empty and no moves remain