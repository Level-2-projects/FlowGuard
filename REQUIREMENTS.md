# FlowGuard – Software Requirements Specification

## 1. Purpose
This document defines the initial functional and non-functional requirements for FlowGuard. It describes the minimum scope that can be designed, implemented, and demonstrated by the student team.

## 2. Problem statement
Small project teams often manage tasks informally. They may not clearly understand which tasks depend on others, which delays can affect the final deadline, or where work should be reassigned. As a result, schedule risks can be noticed too late.

## 3. Proposed solution
FlowGuard provides a lightweight project-planning workspace. It stores tasks, durations, assignments, and dependencies; calculates the project critical path; and allows the team to simulate delays and inspect their effect on the schedule.

## 4. Target users
- **Project Manager / Team Leader:** creates projects, plans tasks, assigns work, and monitors schedule risk.
- **Team Member:** views assigned tasks and updates task progress.

## 5. Functional requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | The system shall allow a project manager to create and edit a project. | Must |
| FR-02 | The system shall allow users to add, edit, and delete project tasks. | Must |
| FR-03 | Each task shall have a title, description, duration, status, and optional assignee. | Must |
| FR-04 | The system shall allow a user to define predecessor/dependency relationships between tasks. | Must |
| FR-05 | The system shall validate dependencies and prevent circular dependency chains. | Must |
| FR-06 | The system shall calculate earliest start, earliest finish, latest start, and latest finish for tasks. | Must |
| FR-07 | The system shall identify and display the project's critical path. | Must |
| FR-08 | The system shall allow a user to simulate a delay to a selected task. | Must |
| FR-09 | The system shall display the estimated impact of the simulated delay on the project completion date. | Must |
| FR-10 | The system shall display task status and overall project progress. | Should |
| FR-11 | The system shall provide a basic suggestion for reallocating or prioritizing work when a delay is simulated. | Could |
| FR-12 | The system shall allow team members to update the status of their assigned tasks. | Should |

## 6. Non-functional requirements

| ID | Requirement |
|---|---|
| NFR-01 | The interface should be simple and understandable for first-time users. |
| NFR-02 | The system should provide calculation results within a reasonable time for a typical student project. |
| NFR-03 | The system should validate user input and show understandable error messages. |
| NFR-04 | Project and task data should be stored persistently in the database. |
| NFR-05 | The application should run in a modern desktop web browser. |
| NFR-06 | The code should be modular enough to separate routes, business logic, and data access. |
| NFR-07 | The system should avoid exposing one team's project data to another team if authentication/multi-user support is implemented. |

## 7. User stories and acceptance criteria

### Epic 1 – Project and Task Management
**US-01 – Create a project**  
As a project manager, I want to create a project so that I can organize its work in one place.
- Given I am on the projects page, when I enter a valid project name and save, then the project is created and appears in the project list.
- Given the project name is empty, when I save, then the system displays a validation message.

**US-02 – Add a task**  
As a project manager, I want to add tasks so that the project work is broken into manageable units.
- Given a project exists, when I enter a title and a positive duration, then the task is saved under that project.
- Given the duration is zero or negative, then the system rejects it and explains the error.

**US-03 – Assign a task**  
As a project manager, I want to assign a task to a team member so that responsibility is clear.
- Given a task and team member exist, when I assign the member, then the assignee is shown on the task.

**US-04 – Update task status**  
As a team member, I want to update my task status so that the team can track progress.
- Given a task is assigned to me, when I change its status to In Progress or Completed, then the new status is saved and displayed.

### Epic 2 – Dependency Planning
**US-05 – Define dependencies**  
As a project manager, I want to link dependent tasks so that the task order is represented correctly.
- Given two tasks exist, when I set Task B to depend on Task A, then the dependency is displayed.
- A task cannot depend on itself.

**US-06 – Prevent circular dependencies**  
As a project manager, I want the system to reject circular dependencies so that schedule calculations remain valid.
- Given A depends on B, when I attempt to make B depend on A, then the system rejects the change and shows an explanation.

### Epic 3 – Schedule Analysis
**US-07 – Calculate project schedule**  
As a project manager, I want to calculate task schedule dates so that I can understand the project timeline.
- When I run schedule analysis on a valid dependency graph, then the system displays ES, EF, LS, and LF for each task.

**US-08 – View critical path**  
As a project manager, I want to identify the critical path so that I know which tasks cannot be delayed without affecting the deadline.
- When schedule analysis completes, then all critical tasks are highlighted.
- The displayed path follows the defined dependencies and has the project's longest duration.

**US-09 – View project progress**  
As a project manager, I want to see task statuses and completion progress so that I can monitor project health.
- When task statuses change, then the progress summary reflects the saved task data.

### Epic 4 – Delay Simulation
**US-10 – Simulate a delay**  
As a project manager, I want to add a hypothetical delay to a task so that I can evaluate schedule risk.
- Given a valid project schedule, when I enter a non-negative delay for a task, then the system calculates the updated schedule without overwriting the original plan.

**US-11 – See delay impact**  
As a project manager, I want to see whether a simulated delay changes the project finish date so that I can assess its impact.
- The result shows the original and simulated finish dates/durations.
- The result identifies whether the project completion date is affected.

**US-12 – Review a recovery suggestion**  
As a project manager, I want to see a basic recovery suggestion so that I can discuss how to respond to a delay.
- When a delay affects the finish date, then the system may show a clearly labelled suggested action, such as reviewing task assignment or prioritizing a critical task.
- The suggestion is advisory and does not automatically change assignments.

## 8. Constraints and assumptions
- The MVP is intended for a university project demonstration, not enterprise project control.
- CPM calculations assume task durations are known and dependencies form a directed acyclic graph (DAG).
- Resource optimization/reassignment is a simplified recommendation, not a guaranteed optimal schedule.
- User authentication and advanced collaboration may be treated as later enhancements unless required by the instructor.

## 9. Out of scope for the initial MVP
- Real-time chat and video calls.
- Integration with external project-management platforms.
- Automatic changes to team-member assignments.
- Advanced machine-learning predictions.
