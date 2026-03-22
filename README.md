# 📚 JavaScript  Project Documentation

> Two fully self-contained frontend projects built with **Vanilla JavaScript** and **Tailwind CSS**.
> No frameworks. No build tools. Just open in a browser and run.

---

## 📁 Project Files

| File | Project |
|---|---|
| `todo.html` | To-Do List App |
| `calculator.html` | Calculator App |

---
---

# 📋 Project 1 — To-Do List

A clean, interactive To-Do List app. Add, complete, and remove tasks — all without refreshing the page.

---

## 🚀 Getting Started

No installation required. Open in any modern browser:

```
todo.html → right-click → Open with → Browser
```

Or drag and drop `todo.html` directly into your browser window.

---

## ✨ Features

| Feature | Description |
|---|---|
| ➕ Add Tasks | Type a task and click **Add** or press **Enter** |
| ✅ Complete Tasks | Click the checkbox to toggle a task as done (strikethrough) |
| 🗑️ Remove Tasks | Click the **✕** button (appears on hover) to delete a task |
| 🔢 Task Counter | Live badge shows how many tasks exist |
| 🚫 Empty Guard | Prevents adding blank tasks with an inline error message |
| 🌿 Empty State | Friendly message shown when the list is empty |
| 🎞️ Animation | New tasks slide in smoothly when added |

---

## 🧠 How It Works

### Data Flow

```
User types task → clicks Add / presses Enter
        ↓
Validation: is input empty?
  YES → show error, stop
  NO  → create task object { id, text, completed: false }
        ↓
        Push to tasks[] array
        ↓
        Re-render entire task list from array
```

### Key JavaScript Concepts Used

- **DOM Manipulation** — `document.getElementById`, `createElement`, `appendChild`
- **Event Listeners** — `addEventListener('click')`, `addEventListener('keydown')`
- **Array Methods** — `push()`, `filter()`, `map()`, `forEach()`
- **Dynamic Rendering** — `renderTasks()` rebuilds the list every time data changes
- **Unique IDs** — `Date.now()` generates a unique ID per task

### Task Object Structure

```javascript
{
  id: 1712345678901,   // Unique timestamp ID
  text: "Buy groceries",
  completed: false     // true = strikethrough style
}
```

---

## 📁 File Structure

```
todo.html
├── <head>        → Tailwind CDN + Google Fonts (DM Sans) + CSS animations
├── <body>        → Card layout with input, task list, error message
└── <script>      → All JavaScript logic (self-contained)
    ├── renderTasks()   → Rebuilds list from tasks[] array
    ├── addTask()       → Validates input + pushes new task
    ├── toggleTask(id)  → Flips completed true/false
    └── removeTask(id)  → Filters task out of array
```

---

## 🎨 UI Design

- **Color scheme:** Warm amber header on a clean white card
- **Font:** DM Sans (Google Fonts)
- **Layout:** Centered card, max-width `md`, responsive on all screens
- **Task rows:** Gray-50 background with hover-reveal delete button
- **Responsive:** Works on desktop, tablet, and mobile

---

## 🔧 Technologies Used

| Technology | Purpose | How Loaded |
|---|---|---|
| HTML5 | Page structure | — |
| Tailwind CSS v3 | All styling | CDN (no build step) |
| Vanilla JavaScript | All logic | `<script>` tag in file |
| Google Fonts | DM Sans typeface | CDN link in `<head>` |

---

## ⚙️ Assignment Requirements Checklist

- [x] Input field for task name
- [x] "Add" button
- [x] Dynamically displayed task list
- [x] Remove button per task
- [x] Mark task as completed (line-through toggle)
- [x] DOM manipulation used
- [x] `addEventListener()` used
- [x] Page does NOT refresh on task add
- [x] Empty tasks are prevented
- [x] Tailwind CSS used
- [x] Centered card layout
- [x] Clean buttons and spacing
- [x] No console errors

---

## 💡 Learning Highlights

1. **Separation of data and UI** — the `tasks[]` array is the source of truth; the DOM is just a reflection of it
2. **Event-driven programming** — all interactions are driven by `addEventListener`
3. **Defensive coding** — empty input, hover states, and edge cases are all handled
4. **Single-file architecture** — HTML, CSS, and JS coexist cleanly in one file

---

## 🖼️ UI Preview

```
┌────────────────────────────────┐
│  📋 My To-Do List              │  ← Amber header
│  Stay organized, stay...       │
├────────────────────────────────┤
│  [ Write a new task...  ] [+Add]│  ← Input + button
│                                │
│  TASKS                  3 task(s)│
│  ☑ Buy groceries ~~done~~  ✕  │  ← Completed task
│  ☐ Read chapter 5          ✕  │  ← Pending task
│  ☐ Submit assignment       ✕  │
└────────────────────────────────┘
```

---

## 👨‍💻 Author Notes

- Code is intentionally written in a **beginner-friendly** style with clear comments
- Functions are small and do one thing each (single responsibility)
- Variable names are descriptive — no abbreviations like `el` or `cb`

---
---

# 🧮 Project 2 — Calculator

A real-calculator-style web app. Performs **one operation at a time** — just like a physical calculator.

---

## 🚀 Getting Started

No installation required. Open in any modern browser:

```
calculator.html → right-click → Open with → Browser
```

Or drag and drop `calculator.html` directly into your browser window.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔢 Two Number Inputs | Enter Number 1 and Number 2 in labeled fields |
| ➕ Operator Selection | Choose one of: `+` `−` `×` `÷` |
| 🔦 Active Highlight | Selected operator button glows amber |
| ▶️ Calculate on `=` | Only runs the **selected** operation |
| 📐 Single Result | Displays one clean result — not all four at once |
| 🚫 Division Guard | Prevents division by zero with a friendly message |
| ⚠️ Input Validation | Catches empty fields and non-numeric values |
| 🔄 Clear Button | Resets all inputs, operator, and results |
| 🎞️ Result Animation | Result panel pops in smoothly on each calculation |
| ⌨️ Enter Key Support | Press Enter in either input field to calculate |

---

## 🧠 How It Works

### Calculation Flow

```
User enters Number 1 + Number 2
        ↓
User clicks an operator button (+, −, ×, ÷)
        ↓
Operator stored in: selectedOperator variable
Selected button gets .op-active highlight class
        ↓
User clicks "=" button
        ↓
Validation:
  - Both fields filled?        → NO  → show error
  - Valid numbers?             → NO  → show error
  - Operator selected?         → NO  → show error
  - Division by zero (÷ only)? → YES → show error
        ↓
  ALL PASS → Run ONLY the selected operation
        ↓
Display result: "25 ÷ 4 = 6.25"
```

### Key JavaScript Concepts Used

- **State variable** — `selectedOperator` stores which operator is active
- **Event Listeners** — `addEventListener('click')` on all buttons
- **Input Validation** — `trim()`, `parseFloat()`, `isNaN()` checks
- **Conditional Logic** — `if/else if` chain runs only one operation
- **DOM Updates** — result panel shown/hidden dynamically
- **CSS class toggling** — `classList.add/remove` for operator highlighting

### The Core State Variable

```javascript
// This variable is the heart of the calculator
let selectedOperator = null;   // null = nothing chosen yet

// Set when an operator button is clicked:
selectedOperator = '+';   // or '-', '*', '/'

// Used inside calculate() to decide which operation to run:
if (selectedOperator === '+') { result = a + b; }
else if (selectedOperator === '-') { result = a - b; }
// etc.
```

---

## 📁 File Structure

```
calculator.html
├── <head>        → Tailwind CDN + Google Fonts + CSS animations
├── <body>        → Dark slate card layout
│   ├── Two number inputs (Number 1, Number 2)
│   ├── Operator buttons grid (+ − × ÷)
│   ├── Selected operator label
│   ├── = button  (triggers calculation)
│   ├── Clear button
│   ├── Result display panel (hidden until calculated)
│   └── Error message panel (hidden until error)
└── <script>      → All JavaScript logic (self-contained)
    ├── selectedOperator    → state variable
    ├── Operator click loop → highlights button, saves operator
    ├── calculate()         → validates inputs + runs operation
    ├── showResult()        → renders expression + result
    ├── showError()         → displays error message
    └── hideResult/Error()  → cleans up display panels
```

---

## 🎨 UI Design

- **Color scheme:** Dark slate (`#1e293b`) header, amber (`#f59e0b`) accents
- **Font:** DM Mono for numbers (monospaced), DM Sans for labels
- **Layout:** Centered narrow card (`max-w-xs`), works on all screen sizes
- **Operator buttons:** White default → amber glow when selected
- **Result panel:** Dark inset box with amber result value
- **Animation:** Result pops in with a subtle scale animation on each calculation

---

## 🔧 Technologies Used

| Technology | Purpose | How Loaded |
|---|---|---|
| HTML5 | Page structure | — |
| Tailwind CSS v3 | All styling | CDN (no build step) |
| Vanilla JavaScript | All calculator logic | `<script>` tag in file |
| Google Fonts | DM Mono + DM Sans | CDN link in `<head>` |

---

## ⚠️ Error Handling Reference

| Scenario | Error Message Shown |
|---|---|
| Number 1 or 2 is empty | "Please enter both numbers before calculating." |
| Input is not a number | "Invalid input. Please enter valid numbers only." |
| No operator selected | "Please select an operator: + − × ÷" |
| Dividing by zero | "Cannot divide by zero — result is undefined." |

---

## ⚙️ Assignment Requirements Checklist

- [x] Two number input fields
- [x] Buttons for `+` `−` `×` `÷`
- [x] `=` button triggers calculation
- [x] Only ONE operation runs at a time
- [x] Selected operator stored in a variable
- [x] Empty input validation
- [x] Invalid number validation
- [x] Division by zero prevention
- [x] Result displayed clearly in the UI
- [x] Tailwind CSS used
- [x] Card-style layout
- [x] No console errors

---

## 💡 Learning Highlights

1. **State management** — `selectedOperator` is a state variable that drives both UI and logic
2. **Single responsibility** — each function does one clear job (`calculate`, `showResult`, `showError`, etc.)
3. **Guard clauses** — validation at the top of `calculate()` exits early on bad input, keeping the happy path clean
4. **UI feedback** — the selected operator is always visually obvious; errors are inline and contextual
5. **Real calculator UX** — unlike a form that calculates all four at once, this mimics how a real calculator works: pick an operator, then evaluate

---

## 🖼️ UI Preview

```
┌─────────────────────────────┐
│  CALCULATOR                 │  ← Dark slate header
│  Number 1: [ 25           ] │
│  Number 2: [  4           ] │
├─────────────────────────────┤
│  [ + ]  [ − ]  [ × ]  [●÷●]│  ← ÷ highlighted (selected)
│       Selected: Division (÷) │
│  [          =           ]   │  ← Amber equals button
│  [         Clear        ]   │
├─────────────────────────────┤
│  ┌──────────────────────┐   │
│  │  25 ÷ 4  =           │   │  ← Result panel
│  │                 6.25 │   │
│  └──────────────────────┘   │
└─────────────────────────────┘
```

---

## 👨‍💻 Author Notes

- Code is written in **beginner-friendly** style — no arrow functions, no destructuring, no shorthand that obscures intent
- Every section is clearly commented with a numbered block
- The `selectedOperator` variable pattern is the core concept to understand — everything else flows from it