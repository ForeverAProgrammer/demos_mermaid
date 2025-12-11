# Other Mermaid Diagram Types

Mermaid supports many diagram types beyond flowcharts and sequence diagrams. This directory contains examples of various diagram types.

## Available Diagram Types

### Class Diagrams

Show object-oriented class structures and relationships:

```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +makeSound()
    }
    class Dog {
        +String breed
        +bark()
    }
    class Cat {
        +meow()
    }

    Animal <|-- Dog
    Animal <|-- Cat
```

### State Diagrams

Visualize state machines and transitions:

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Processing: Start
    Processing --> Success: Complete
    Processing --> Error: Fail
    Success --> [*]
    Error --> Idle: Retry
```

### Entity Relationship Diagrams (ERD)

Database schema and relationships:

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER {
        string name
        string email
        int id
    }
    ORDER {
        int orderNumber
        date orderDate
    }
    LINE-ITEM {
        int quantity
        decimal price
    }
```

### Gantt Charts

Project timelines and schedules:

```mermaid
gantt
    title Project Timeline
    dateFormat YYYY-MM-DD
    section Planning
        Requirements       :a1, 2024-01-01, 30d
        Design            :a2, after a1, 20d
    section Development
        Backend           :b1, after a2, 45d
        Frontend          :b2, after a2, 45d
        Testing           :b3, after b1, 15d
```

### Git Graph

Version control branching and merging:

```mermaid
gitGraph
    commit
    commit
    branch develop
    checkout develop
    commit
    commit
    checkout main
    merge develop
    commit
```

### Pie Charts

Data visualization:

```mermaid
pie title Project Time Distribution
    "Development" : 45
    "Testing" : 20
    "Design" : 15
    "Planning" : 10
    "Documentation" : 10
```

### User Journey

Map user experience flows:

```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```

### Mindmap

Hierarchical concept mapping:

```mermaid
mindmap
  root((Mermaid))
    Diagrams
      Flowchart
      Sequence
      Class
      State
    Features
      GitHub Support
      Themes
      Styling
    Use Cases
      Documentation
      Planning
      Teaching
```

### Timeline

Linear event visualization:

```mermaid
timeline
    title History of Web Development
    2000 : HTML/CSS dominance
    2006 : jQuery released
    2010 : AngularJS introduced
    2013 : React released
    2020 : Modern frameworks mature
```

### Quadrant Chart

2D categorization:

```mermaid
quadrantChart
    title Technology Adoption Matrix
    x-axis Low Complexity --> High Complexity
    y-axis Low Value --> High Value
    quadrant-1 Invest
    quadrant-2 Consider
    quadrant-3 Avoid
    quadrant-4 Evaluate
    Technology A: [0.3, 0.7]
    Technology B: [0.6, 0.8]
    Technology C: [0.2, 0.2]
    Technology D: [0.8, 0.4]
```

### Requirement Diagram

System requirements and relationships:

```mermaid
requirementDiagram
    requirement user_authentication {
        id: 1
        text: System must authenticate users
        risk: high
        verifymethod: test
    }

    element login_page {
        type: page
    }

    login_page - satisfies -> user_authentication
```

## GitHub Compatibility

Most of these diagram types are supported on GitHub, but some newer types may have limited support. Always test your diagrams on GitHub to ensure proper rendering.

**Well-supported on GitHub:**
- Flowcharts
- Sequence diagrams
- Class diagrams
- State diagrams
- Entity relationship diagrams
- Gantt charts
- Pie charts
- Git graphs

**May have limited support:**
- User journey
- Mindmap (newer feature)
- Timeline (newer feature)
- Quadrant chart (newer feature)
- Requirement diagrams

## Resources

- [Mermaid.js Documentation](https://mermaid.js.org/)
- [Mermaid Live Editor](https://mermaid.live/)
- [GitHub's Mermaid Support](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/)
