# `push_swap` Playground

An interactive sandbox and instruction simulator for the 42 School **`push_swap`** sorting project. Test stack operations manually, verify your own `push_swap` output sequences, and watch how elements move between **Stack A** and **Stack B** in real time. Built as a lightweight, zero-dependency single HTML file with full **English** and **Arabic** (`RTL`) support.

## ✨ Features

* **Interactive Operation Pad:** Execute any of the 11 standard `push_swap` instructions (`sa`, `sb`, `ss`, `pa`, `pb`, `ra`, `rb`, `rr`, `rra`, `rrb`, `rrr`) with a single click. Invalid moves for the current stack state are automatically disabled, and tooltips explain each operation.
* **Custom Sequence Runner:** Paste the output of your own `push_swap` program (e.g., `pb pb ra rr sa pa pa`) and watch it execute step-by-step from the current stack state with adjustable animation speed.
* **Live Validation & Move Limits:** Automatically checks whether **Stack A** is sorted in ascending order and **Stack B** is empty (`Sorted ✓` / `Not sorted`), tracks total moves, and displays 42 project benchmarks for `3` (`≤ 3` moves) and `5` (`≤ 12` moves) numbers.
* **Undo, Reset & Copy History:** Step backward with **Undo** (or `Ctrl+Z` / `Cmd+Z`), reset stacks to their initial state, or copy your entire move history to the clipboard in one click.
* **Custom & Preset Inputs:** Enter your own list (`3` to `20` unique integers) or generate **Random**, **Sorted**, and **Reversed** test cases using the size slider.
* **Bilingual & Theme Support:** Instant switching between **English** and **Arabic** interfaces, plus automatic or manual **Light / Dark** mode.

## 🚀 Usage

1. Open `index.html` (or your hosted GitHub Pages URL) in any modern browser.
2. Enter space-separated unique integers (e.g., `3 7 1 9 5 2 8`) or click **Random**, **Sorted**, or **Reversed**, then click **Start**.
3. Use the **Moves** pad to manipulate the stacks manually, **or** paste an instruction list into **Run a sequence** and click **Run sequence**.

## 🕹️ Supported Operations

| Action | Stack A | Stack B | Both (`A + B`) | Description |
| :--- | :---: | :---: | :---: | :--- |
| **Swap** | `sa` | `sb` | `ss` | Swap the top 2 elements of the stack |
| **Push** | `pa` | `pb` | — | Push the top element from the other stack onto this one |
| **Rotate** | `ra` | `rb` | `rr` | Shift all elements up by 1 (top becomes bottom) |
| **Reverse Rotate** | `rra` | `rrb` | `rrr` | Shift all elements down by 1 (bottom becomes top) |