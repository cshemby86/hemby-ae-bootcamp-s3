# Product Requirements Document (PRD) - Todo App Upgrade

## 1. Overview

Upgrade the basic Todo app so users can organize work by due date and priority, then quickly view all, today's, or overdue tasks. The MVP must remain simple and teachable: task data is stored locally, with no backend or external-storage changes.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
  - Accept ISO date values in the `YYYY-MM-DD` format.
  - Treat invalid due-date values as absent.
- Add a `priority` field to each task.
  - Support `P1`, `P2`, and `P3` values.
  - Default the priority to `P3`.
  - Display priorities with color-coded badges: red for `P1`, orange for `P2`, and gray for `P3`.
- Require a task title.
- Provide task filters:
  - **All**: show all tasks, including completed tasks.
  - **Today**: show incomplete tasks due today.
  - **Overdue**: show incomplete tasks with a due date before today.
- Persist task data locally only. No backend or external-storage changes are part of the MVP.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks, such as with red styling.
- Sort tasks using this precedence:
  1. Overdue tasks first.
  2. Priority from `P1` to `P3`.
  3. Due date in ascending order.
  4. Tasks without a due date last.

---

## 4. Out of Scope

- Notifications
- Recurring tasks
- Multi-user support
- Keyboard navigation or additional accessibility features
- Backend changes
- External storage