# push_swap tools

Two single-file, zero-dependency web tools for learning, debugging and testing **push_swap** (the 42 sorting project). Open an HTML file in any modern browser. There is nothing to install or build.

| Tool | File | Purpose |
|------|------|---------|
| **Turk visualizer** | `Turk_push_swap_visualizer.html` | Watch the Turk algorithm sort step by step, with every decision explained. |
| **Playground** | `push_swap_playground.html` | Move the stacks yourself or replay your own program's output, to test any algorithm. |

Both tools share the same design: Apple-style interface, light and dark themes, translucent glass bars, and a full English / Arabic (RTL) interface.

---

## Quick start

```bash
git clone <your-repo-url>
cd <your-repo>
open Turk_push_swap_visualizer.html      # macOS
xdg-open push_swap_playground.html       # Linux
```

Or simply double-click a file. Fonts are loaded from Google Fonts; offline, the tools fall back to system fonts and work the same.

---

## 1. Turk visualizer

An interactive walkthrough of the Turk algorithm. Every step shows what happens, why it happens, and the matching function name you would write in C.

### What the algorithm does

1. **Phase 1, A → B:** push two numbers to B without computing anything. Then, while A has more than three numbers, compute the cost of every number in A, pick the cheapest, bring it and its target to the top, and push. B stays in descending order (circularly).
2. **Sort three:** the last three numbers in A are sorted with fixed cases.
3. **Phase 2, B → A:** for the top of B, find its target in A (the smallest number larger than it, or the smallest overall), rotate A, and push back.
4. **Finish:** rotate A until the smallest number is on top.

### Cost calculation

For each number in A:

- `costA`: moves to bring it to the top of A (`ra` or `rra`, whichever is shorter).
- `costB`: moves to bring its target to the top of B (`rb` or `rrb`).
- If both rotate the same way, merge them into `rr` / `rrr`, so the cost is `max(costA, costB)`. Otherwise it is the sum.
- Add 1 for the push.

The **"How the cost is computed"** panel walks through this in six steps for any number you select in the table.

### Features

- Animated stacks A and B. Colour shows rank (cool = small, warm = large).
- Highlighted **current number** and its **target**.
- Phase tabs: Start, A → B, Sort three, B → A, Finish.
- Cost table with hover preview and click-to-pin (click again to unpin).
- Playback: first, previous, play / pause, next, last, a step slider and a speed slider.
- Merge toggle (`rr` / `rrr`) with a live comparison of total moves **with** and **without** merging.
- Clickable move log and a **Copy moves** button.
- Custom input (5 to 14 unique integers) or Random / Sorted / Reversed.

### Shortcuts

| Key | Action |
|-----|--------|
| `→` | Next step |
| `←` | Previous step |

> Note: this is a teaching implementation. Phase 2 returns numbers from the top of B without first rotating B to put its maximum on top, so it is correct but not move-optimal.

---

## 2. Playground

A sandbox to try any strategy by hand, or to check the output of your own `push_swap`.

### Controls

Moves are laid out as a grid: columns are stacks, rows are move types.

| | Stack A | Stack B | A + B |
|---|---|---|---|
| **Swap the top two** | `sa` | `sb` | `ss` |
| **Rotate** (top goes to bottom) | `ra` | `rb` | `rr` |
| **Reverse rotate** (bottom comes to top) | `rra` | `rrb` | `rrr` |
| **Push to this stack** | `pa` | `pb` | |

- A button is disabled when the move would do nothing (for example `pa` when B is empty).
- Hover a button for a plain-language description.
- Colours: blue = both stacks, green = push, grey = single stack.

### Features

- **Undo** (`Ctrl` / `⌘` + `Z`) and **Reset** to the starting numbers.
- Move counter, move log and **Copy moves**.
- Status pill: **Sorted ✓** when A is ascending and B is empty.
- Reference limits for small sizes (3 numbers: 3 moves, 5 numbers: 12 moves).
- **Run a sequence:** paste your program's output (one move per line, or space separated) and replay it with animation. Pause, resume, and change the speed at any time. Unknown moves are reported by name.
- Custom input (3 to 20 unique integers) or Random / Sorted / Reversed.

### Testing your own push_swap

```bash
./push_swap 3 7 1 9 5 2 8 | pbcopy      # macOS (use xclip / wl-copy on Linux)
```

Paste the result into **Run a sequence**, start from the same numbers, and press **Run sequence**. If the status ends on **Sorted ✓**, your output is valid for that input. The move counter shows how long it is.

---

## Notes

- **Language and theme** are saved in your browser (`localStorage`). The first visit follows your browser language.
- **No tracking, no network calls** besides the font stylesheet.
- Numbers must be unique integers (as in push_swap). Input accepts spaces, commas or semicolons.
- Stack top is index 0, shown at the top of each column.

## Project structure

```
.
├── Turk_push_swap_visualizer.html   # Turk algorithm, step-by-step explainer
├── push_swap_playground.html        # manual moves + sequence replay
└── README.md
```

## Browser support

Any current Chrome, Edge, Safari or Firefox. The interface uses CSS variables, grid, `backdrop-filter` and `prefers-color-scheme`.

---

## بالعربية

أداتان في ملفين HTML بلا أي مكتبات، لتعلّم مشروع **push_swap** واختباره:

- **Turk visualizer:** يعرض خوارزمية Turk خطوة بخطوة، مع شرح كل قرار وحساب التكلفة لكل رقم.
- **Playground:** تحرّك المكدسين بنفسك بأزرار مرتبة (الأعمدة هي المكدسات والصفوف هي أنواع الحركة)، أو تلصق ناتج برنامجك فيُعاد تشغيله بالتحريك، ويخبرك إن كان A مرتبًا وB فارغًا.

كلا الأداتين تدعمان العربية والإنجليزية، والمظهر الفاتح والداكن. افتح الملف في المتصفح مباشرة ولا حاجة لتثبيت شيء.
