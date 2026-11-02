# FlowGuard – UI/UX Wireframes

## Figma
**Figma file:** `ADD_YOUR_FIGMA_FILE_URL_HERE`

Replace the placeholder above with the actual Figma share link after creating the design. Set the link permission to **Anyone with the link – can view** if your instructor needs to open it.

## Design direction
- Desktop-first web dashboard.
- Clear, simple layout suitable for a university project demo.
- Neutral background with one primary accent color.
- Consistent status colors: To Do, In Progress, Blocked, Completed.
- Prioritize readability of task dependencies and critical-path information.

## Screens to create in Figma

### 1. Login (optional for MVP)
- FlowGuard logo/name.
- Email and password fields.
- Sign in button.

### 2. Dashboard
- Header with project name and user menu.
- Summary cards: Total Tasks, Completed, In Progress, Delayed/Critical.
- Project progress bar.
- Upcoming and blocked tasks list.
- Button to open task board.

### 3. Project Tasks
- Task table or board.
- Columns: Task, Assignee, Duration, Status, Dependencies.
- Add Task button.
- Filters by status and assignee.

### 4. Task Details
- Task title and description.
- Duration and assignee.
- Status selector.
- Predecessor/dependency list.
- Save and Cancel actions.

### 5. Schedule Analysis
- Task timeline or dependency graph.
- Highlight critical-path tasks.
- Show duration and slack/float.
- Recalculate Schedule button.

### 6. Delay Simulator
- Select a task.
- Enter hypothetical delay duration.
- Run Simulation button.
- Comparison cards: Original Finish vs Simulated Finish.
- Clear impact message and advisory recovery suggestion.

## Low-fidelity layout sketches

### Dashboard
```text
+---------------------------------------------------------------+
| FlowGuard                         Project ▼        Profile    |
+---------------------------------------------------------------+
| Project Overview                                              |
| +-------------+ +-------------+ +-------------+ +-----------+|
| | Total Tasks | | Completed   | | In Progress | | Critical  ||
| |     12      | |      5      | |      4      | |     3     ||
| +-------------+ +-------------+ +-------------+ +-----------+|
|                                                               |
| Project Progress   [############........]  45%                 |
|                                                               |
| Recent Tasks                         Schedule Alerts          |
| - Design database                    - API task is blocked    |
| - Build dashboard                    - Review critical path   |
| - Test CPM calculation                                         |
+---------------------------------------------------------------+
| Dashboard | Tasks | Schedule Analysis | Delay Simulator       |
+---------------------------------------------------------------+
```

### Delay Simulator
```text
+---------------------------------------------------------------+
| FlowGuard / Delay Simulator                                   |
+---------------------------------------------------------------+
| Select Task: [Database Design             ▼]                  |
| Delay Duration (days): [  3  ]                                |
|                                                               |
|                     [ Run Simulation ]                        |
|                                                               |
| +---------------------------+ +-----------------------------+ |
| | Original Project Finish   | | Simulated Project Finish     | |
| | Day 18                    | | Day 21                       | |
| +---------------------------+ +-----------------------------+ |
|                                                               |
| Impact: The simulated delay moves the finish by 3 days.       |
| Suggested action: Review critical tasks and available capacity.|
+---------------------------------------------------------------+
```

## Prototype checklist
- [ ] Create the six screens above (login is optional).
- [ ] Link Dashboard → Tasks → Task Details.
- [ ] Link Dashboard → Schedule Analysis → Delay Simulator.
- [ ] Add realistic sample task names and statuses.
- [ ] Paste the public view link into this document.
