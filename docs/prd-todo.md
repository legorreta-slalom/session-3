# Product Requirements Document (PRD) - Todo App Upgrade

## 1. Overview

We are upgrading the basic TODO app so it is more useful for day-to-day task management while still remaining simple enough for an MVP. The current app only supports a task title and completion state. Based on the requirements meeting and the follow-up Slack scope confirmation, the MVP will add due dates, priority levels, and task filters without introducing backend or external storage complexity. Additional visual treatment and more advanced task ordering will be deferred until after MVP.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
- Store `dueDate` in ISO `YYYY-MM-DD` format.
- Treat invalid `dueDate` values as absent rather than failing the task.
- Add a `priority` field with allowed values `P1`, `P2`, and `P3`.
- Default `priority` to `P3` when no value is provided.
- Continue to require `title` for every task.
- Add filter views for `All`, `Today`, and `Overdue`.
- In the `All` view, show both completed and incomplete tasks.
- In the `Today` and `Overdue` views, show incomplete tasks only.
- Keep persistence local only using the existing local-storage-based approach.
- Do not make backend or external storage changes as part of MVP.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out more clearly.
- Add task sorting with the following order:
- Overdue tasks first.
- Then by priority from `P1` to `P3`.
- Then by due date in ascending order.
- Tasks without a due date last.

---

## 4. Out of Scope

- Notifications or reminders.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation enhancements.
- External storage or backend persistence.
- Additional accessibility-specific features beyond the current baseline.