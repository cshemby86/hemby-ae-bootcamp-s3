# Epics and Stories

## MVP

- Epic: Task Data Management
	- Story: Require task titles
		- Acceptance Criteria: A task cannot be created without a title.
		- Technical Requirements: Validate that `title` is non-empty before creating a task.
	- Story: Add optional due dates to tasks
		- Acceptance Criteria: A task can be created with or without a due date.
		- Technical Requirements: Add an optional `dueDate` property to the local task model.
	- Story: Validate task due dates
		- Acceptance Criteria: A valid due date uses the `YYYY-MM-DD` format; an invalid value is treated as absent.
		- Technical Requirements: Accept only `YYYY-MM-DD` values for `dueDate` and store invalid values as absent.

- Epic: Task Prioritization
	- Story: Add task priority levels
		- Acceptance Criteria: A task priority can be set to `P1`, `P2`, or `P3`.
		- Technical Requirements: Add a `priority` property that accepts only `P1`, `P2`, or `P3`.
	- Story: Default new tasks to P3 priority
		- Acceptance Criteria: A new task without a selected priority is assigned `P3`.
		- Technical Requirements: Initialize `priority` to `P3` when a new task has no priority value.
	- Story: Display color-coded priority badges
		- Acceptance Criteria: `P1` displays a red badge, `P2` an orange badge, and `P3` a gray badge.
		- Technical Requirements: Render each task priority as a badge with styles mapped to `P1`, `P2`, and `P3`.

- Epic: Date-Based Task Filtering
	- Story: Show all tasks
		- Acceptance Criteria: The All filter displays every task, including completed tasks.
		- Technical Requirements: Implement an All filter that returns the complete local task collection.
	- Story: Show incomplete tasks due today
		- Acceptance Criteria: The Today filter displays only incomplete tasks with a due date equal to the current date.
		- Technical Requirements: Compare each task's `dueDate` to the current local calendar date and exclude completed tasks.
	- Story: Show incomplete overdue tasks
		- Acceptance Criteria: The Overdue filter displays only incomplete tasks with a due date before the current date.
		- Technical Requirements: Compare each task's `dueDate` to the current local calendar date and exclude completed or undated tasks.

- Epic: Local Task Storage
	- Story: Store task data locally
		- Acceptance Criteria: Task data is persisted locally without backend or external-storage changes.
		- Technical Requirements: Persist task records, including `title`, `dueDate`, and `priority`, in browser-local storage without API calls.

## Post-MVP

- Epic: Overdue Task Visibility
	- Story: Highlight overdue tasks
		- Acceptance Criteria: Incomplete tasks with a due date before the current date receive distinct visual highlighting.
		- Technical Requirements: Apply an overdue CSS state only when an incomplete task's `dueDate` is before the current local calendar date.

- Epic: Task Sorting
	- Story: Sort overdue tasks first
		- Acceptance Criteria: Overdue tasks appear before tasks that are not overdue.
		- Technical Requirements: Use overdue status as the first comparison key in the task sort function.
	- Story: Sort tasks by priority
		- Acceptance Criteria: Within the same overdue status, tasks are ordered from `P1` to `P3`.
		- Technical Requirements: Use the priority order `P1`, `P2`, then `P3` as the second comparison key.
	- Story: Sort tasks by due date
		- Acceptance Criteria: Within the same overdue status and priority, tasks with due dates are ordered by ascending due date.
		- Technical Requirements: Use ascending `dueDate` as the third comparison key for dated tasks.
	- Story: Place undated tasks last
		- Acceptance Criteria: Tasks without a due date appear after tasks with due dates.
		- Technical Requirements: Treat an absent `dueDate` as greater than any valid due date in the task sort function.