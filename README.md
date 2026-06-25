# To-Do List App

A clean, feature-rich To-Do List web app for managing daily tasks — built with vanilla HTML, CSS, and JavaScript. No frameworks, no dependencies, no build steps.

---

## Features

- **Add tasks** — Type a task and press Enter or click the Add button
- **Complete tasks** — Click the circle checkbox to toggle a task as done (strikethrough applied)
- **Edit tasks** — Click the pencil icon to edit inline; save with Enter or the checkmark button
- **Delete tasks** — Click the trash icon to remove a task instantly
- **Priority levels** — Click the colored dot to cycle between Low (green), Medium (amber), and High (red) priority
- **Filter tabs** — Switch between All, Active, and Done views
- **Stats bar** — Live count of Total, Done, and Remaining tasks
- **Progress bar** — Visual completion indicator that fills as tasks are completed
- **Toast notifications** — Subtle feedback message on every action
- **LocalStorage persistence** — All tasks are saved to the browser and survive page refreshes

---

## Tech Stack

| Layer | Technology | Role |
|-------|-----------|------|
| Structure | HTML5 | Semantic markup, accessibility attributes |
| Styling | CSS3 | Layout, animations, theming, responsive design |
| Logic | Vanilla JavaScript | CRUD operations, event handling, state management, localStorage |

---

## Project Structure

```
todo-app/
│
├── index.html        # Main HTML file (contains embedded CSS and JS)
└── README.md         # Project documentation
```

> All CSS and JavaScript are embedded within `index.html` for simplicity. For larger projects, these would be separated into `style.css` and `app.js`.

---

## How to Run

No installation or build process required.

1. Clone or download this repository
2. Open `index.html` in any modern web browser

```bash
# Option 1: Open directly
open index.html

# Option 2: Serve locally (recommended)
npx serve .
# or
python -m http.server 8000
```

Then visit `http://localhost:8000` in your browser.

---

## Key Concepts Used

### CRUD Operations (JavaScript)

| Operation | Function | Description |
|-----------|----------|-------------|
| Create | `addTask()` | Adds a new task object to the array |
| Read | `render()` | Reads the tasks array and rebuilds the DOM |
| Update | `saveEdit()`, `toggleDone()`, `cyclePriority()` | Modifies task properties in place |
| Delete | `deleteTask()` | Filters the task out of the array |

### Event Handling

- `onclick` — used for buttons (add, check, edit, save, delete, priority, filter)
- `onkeydown` — Enter to add/save a task; Escape to cancel editing
- All handlers are attached inline for simplicity in this single-file app

### LocalStorage

```javascript
// Save
localStorage.setItem('todo_app_tasks_v1', JSON.stringify(tasks));

// Load
const saved = localStorage.getItem('todo_app_tasks_v1');
if (saved) tasks = JSON.parse(saved);
```

Tasks are stored as a JSON string under the key `todo_app_tasks_v1`. Data persists across sessions until the user clears browser storage.

### State Management

A central `render()` function is called after every state change. It:
1. Recalculates stats (total, done, remaining)
2. Updates the progress bar width
3. Applies the active filter
4. Rebuilds the task list HTML
5. Handles the empty state display

---

## Accessibility

- `aria-label` on all icon-only buttons
- `aria-hidden="true"` on decorative icons
- Visually-hidden `<h2>` for screen reader context
- Keyboard-navigable inputs and buttons
- Focus ring on inputs via CSS

---

## Browser Support

Works in all modern browsers that support:
- `localStorage` API
- CSS Custom Properties (variables)
- ES6+ JavaScript (arrow functions, template literals, array methods)

| Browser | Support |
|---------|---------|
| Chrome 60+ | ✅ |
| Firefox 55+ | ✅ |
| Safari 11+ | ✅ |
| Edge 16+ | ✅ |

---

## Possible Enhancements

- Drag-and-drop reordering of tasks
- Due dates and reminders
- Task categories / tags
- Dark mode toggle
- Export tasks as a text or CSV file
- Subtasks / checklists within a task
- Sync with a backend (Node.js + MongoDB)

---

## License

This project is open source and free to use for personal and educational purposes.
