
# FlowGuard – Software Design Diagrams

The diagrams below describe the proposed MVP design. They can be rendered directly by GitHub because they use Mermaid.

## 1. Use Case Diagram

```mermaid
flowchart LR
    PM[Project Manager]
    TM[Team Member]
    subgraph FG[FlowGuard System]
      UC1((Create Project))
      UC2((Manage Tasks))
      UC3((Assign Tasks))
      UC4((Define Dependencies))
      UC5((Analyze Schedule))
      UC6((View Critical Path))
      UC7((Simulate Delay))
      UC8((View Project Progress))
      UC9((Update Task Status))
    end
    PM --> UC1
    PM --> UC2
    PM --> UC3
    PM --> UC4
    PM --> UC5
    PM --> UC6
    PM --> UC7
    PM --> UC8
    TM --> UC8
    TM --> UC9
```

## 2. Class Diagram

```mermaid
classDiagram
    class User {
      +int id
      +string name
      +string email
      +string role
    }
    class Project {
      +int id
      +string name
      +string description
      +date start_date
      +create()
      +update()
    }
    class Task {
      +int id
      +string title
      +string description
      +int duration
      +string status
      +int project_id
      +int assignee_id
      +update_status()
    }
    class Dependency {
      +int id
      +int predecessor_id
      +int successor_id
    }
    class ScheduleAnalysis {
      +int id
      +int project_id
      +calculate_cpm()
      +get_critical_path()
    }
    class DelaySimulation {
      +int id
      +int task_id
      +int delay_duration
      +int original_finish
      +int simulated_finish
      +simulate()
    }
    User "1" --> "0..*" Project : manages
    Project "1" --> "1..*" Task : contains
    User "0..1" --> "0..*" Task : assigned to
    Task "1" --> "0..*" Dependency : predecessor/successor
    Project "1" --> "0..*" ScheduleAnalysis : analyzed by
    Task "1" --> "0..*" DelaySimulation : tested in
```

## 3. Activity Diagram – Delay Simulation

```mermaid
flowchart TD
    A([Start]) --> B[Select project]
    B --> C[Load tasks and dependencies]
    C --> D{Dependency graph valid?}
    D -- No --> E[Show validation error]
    E --> Z([End])
    D -- Yes --> F[Calculate original CPM schedule]
    F --> G[Select task and enter hypothetical delay]
    G --> H{Delay is non-negative?}
    H -- No --> I[Show input error]
    I --> G
    H -- Yes --> J[Temporarily apply delay]
    J --> K[Recalculate CPM schedule]
    K --> L[Compare original and simulated finish]
    L --> M[Display impact and advisory suggestion]
    M --> N[Discard simulation changes]
    N --> Z
```

## 4. State Diagram – Task

```mermaid
stateDiagram-v2
    [*] --> ToDo
    ToDo --> InProgress: Start task
    InProgress --> Blocked: Dependency or issue blocks work
    Blocked --> InProgress: Blocker resolved
    InProgress --> Completed: Finish task
    ToDo --> Cancelled: Cancel task
    InProgress --> Cancelled: Cancel task
    Completed --> [*]
    Cancelled --> [*]
```

## 5. Design notes
- A project contains multiple tasks.
- Dependencies connect tasks in the same project.
- The dependency graph must not contain cycles.
- CPM analysis is calculated from task durations and dependencies.
- Delay simulation must not overwrite the saved baseline plan.
- The diagrams represent the proposed design and should be updated if implementation decisions change.
