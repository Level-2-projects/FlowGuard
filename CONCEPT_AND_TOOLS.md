# FlowGuard – Concept and Tools

## 1. Project concept
FlowGuard is a lightweight project planning and schedule-risk analysis system for small teams.

## 2. Problem
Teams can lose time because tasks are not clearly organized, dependencies are overlooked, and the impact of a delayed task is not immediately visible. A delay in one important task may affect several following tasks and the final delivery date.

## 3. Solution
FlowGuard lets a team:
- Create a project and break it into tasks.
- Assign tasks and estimate their durations.
- Define dependencies between tasks.
- Calculate the Critical Path using the Critical Path Method (CPM).
- Simulate a possible delay and compare the expected project finish before and after the delay.
- Review a basic, advisory recovery suggestion.

## 4. Target audience
- University student teams working on course projects.
- Small teams coordinating short-term projects.
- Team leaders who need a simple view of task dependencies and schedule risks.

## 5. Core technical idea
The project represents tasks and dependencies as a Directed Acyclic Graph (DAG). CPM is used to calculate:
- ES: Earliest Start
- EF: Earliest Finish
- LS: Latest Start
- LF: Latest Finish
- Slack/Float: allowable delay without delaying the project
Tasks with zero total slack are considered critical.

A delay simulation temporarily changes a task duration, recalculates the schedule, and compares the new finish time with the original plan. The original project plan remains unchanged.

## 6. Proposed Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | HTML5 | Page structure |
| Styling | CSS3 | Layout and visual design |
| Client-side behavior | JavaScript | Interactions and simple dynamic updates |
| Backend | Python | Application logic |
| Web framework | Flask | Routes and server-side handling |
| Database | SQLite | Store projects, tasks, users, and dependencies |
| Algorithm | CPM + DAG traversal | Schedule and critical-path calculation |
| Design | Figma | Wireframes and UI mockups |
| Version control | Git + GitHub | Source control, issues, and collaboration |

**Note:** This is the proposed stack for the planned MVP. Update this document if the team chooses different technologies or has already implemented a different stack.

## 7. Development tools
- Visual Studio Code: code editing.
- Git: version control.
- GitHub: repository hosting, issues, and collaboration.
- Figma: interface design and prototyping.
- Mermaid: diagrams embedded in Markdown documentation.

## 8. MVP deliverables
1. Project and task CRUD.
2. Dependency management with cycle validation.
3. CPM schedule calculation and critical-path display.
4. Delay simulation and before/after comparison.
5. Basic dashboard for project progress and schedule status.
