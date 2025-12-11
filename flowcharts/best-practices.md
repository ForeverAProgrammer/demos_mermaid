# Mermaid Flowchart Best Practices

This guide provides tips and best practices for creating effective and maintainable Mermaid flowcharts.

## Table of Contents

- [Diagram Direction](#diagram-direction)
- [Node Naming Conventions](#node-naming-conventions)
- [Layout and Readability](#layout-and-readability)
- [Using Subgraphs](#using-subgraphs)
- [Common Pitfalls](#common-pitfalls)
- [Performance Tips](#performance-tips)
- [Accessibility](#accessibility)

## Diagram Direction

Choose the right direction for your flowchart based on the type of process:

### Top to Bottom (TD/TB) - Default and Recommended

Best for: Sequential processes, hierarchies, decision trees

```mermaid
flowchart TD
    Start[Start] --> Step1[First Step]
    Step1 --> Step2[Second Step]
    Step2 --> End[End]
```

### Left to Right (LR)

Best for: Timeline processes, short workflows, wide displays

```mermaid
flowchart LR
    Start[Start] --> Process[Process] --> End[End]
```

### Right to Left (RL) and Bottom to Top (BT)

Less common, use when specifically needed for visual flow:

```mermaid
flowchart RL
    End[End] --> Process[Process] --> Start[Start]
```

## Node Naming Conventions

### Use Meaningful IDs

**Good:**
```mermaid
flowchart TD
    userLogin[User Login]
    validateCredentials[Validate Credentials]
    dashboardHome[Dashboard Home]

    userLogin --> validateCredentials --> dashboardHome
```

**Avoid:**
```mermaid
flowchart TD
    a[User Login]
    b[Validate Credentials]
    c[Dashboard Home]

    a --> b --> c
```

### Keep IDs Consistent

Use a consistent naming pattern throughout your diagram:
- camelCase: `userLogin`, `validateData`
- snake_case: `user_login`, `validate_data`
- PascalCase: `UserLogin`, `ValidateData`

## Layout and Readability

### Limit Node Connections

Avoid nodes with too many connections. Break complex flows into subgraphs:

**Better:**
```mermaid
flowchart TD
    Start[Start] --> Auth[Authentication]

    subgraph AuthProcess
        Auth --> CheckUser[Check User]
        CheckUser --> CheckPass[Check Password]
    end

    CheckPass --> Success{Success?}
    Success -->|Yes| Dashboard[Dashboard]
    Success -->|No| Error[Error Message]
```

### Use Whitespace Appropriately

Break long diagrams into logical sections:

```mermaid
flowchart TD
    %% Input Section
    Start([Start]) --> Input[/Get User Input/]

    %% Processing Section
    Input --> Process[[Process Data]]
    Process --> Validate{Valid?}

    %% Output Section
    Validate -->|Yes| Save[(Save)]
    Validate -->|No| Error[Error]
    Save --> End([End])
```

### Keep Text Labels Concise

**Good:** Short, clear labels
```mermaid
flowchart LR
    A[Login] --> B{Auth?}
    B -->|Yes| C[Dashboard]
    B -->|No| D[Retry]
```

**Avoid:** Long, wordy labels
```mermaid
flowchart LR
    A[User navigates to login page] --> B{Is authentication successful?}
    B -->|Yes| C[Redirect to dashboard]
    B -->|No| D[Show error and retry]
```

## Using Subgraphs

Organize complex diagrams with subgraphs:

```mermaid
flowchart TD
    Start[Start]

    subgraph Input [Input Phase]
        GetData[Get Data]
        ParseData[Parse Data]
    end

    subgraph Processing [Processing Phase]
        Validate[Validate]
        Transform[Transform]
    end

    subgraph Output [Output Phase]
        Save[Save]
        Notify[Notify User]
    end

    Start --> GetData
    GetData --> ParseData
    ParseData --> Validate
    Validate --> Transform
    Transform --> Save
    Save --> Notify
```

### Nested Subgraphs

For hierarchical organization:

```mermaid
flowchart TD
    Start[Start]

    subgraph Backend
        subgraph API
            endpoint1[Endpoint 1]
            endpoint2[Endpoint 2]
        end

        subgraph Database
            db1[(Main DB)]
            db2[(Cache)]
        end

        API --> Database
    end

    Start --> Backend
```

## Common Pitfalls

### Avoid Circular Dependencies Without Purpose

Ensure loops are intentional and have exit conditions:

**Good:**
```mermaid
flowchart TD
    Start[Start] --> Process[Process]
    Process --> Check{Done?}
    Check -->|No| Process
    Check -->|Yes| End[End]
```

**Confusing:**
```mermaid
flowchart LR
    A --> B
    B --> C
    C --> A
```

### Escape Special Characters

Use quotes for text with special characters:

```mermaid
flowchart LR
    A["Text with (parentheses)"]
    B["Text with #hash"]
    C["Text with 'quotes'"]

    A --> B --> C
```

### Handle Long Text

Use markdown strings for better text formatting:

```mermaid
%%{init: {"flowchart": {"htmlLabels": false}} }%%
flowchart TD
    A["`**Bold Title**
    Multiple lines
    of text here`"]
```

## Performance Tips

### Limit Diagram Size

Break very large diagrams into multiple smaller diagrams:
- Keep diagrams under 50 nodes when possible
- Use separate diagrams for different system components
- Link between diagrams in documentation

### Avoid Redundant Connections

**Inefficient:**
```mermaid
flowchart TD
    A --> B
    A --> C
    A --> D
    A --> E
```

**Better:**
```mermaid
flowchart TD
    A --> Group
    subgraph Group
        B
        C
        D
        E
    end
```

## Accessibility

### Use Descriptive Labels

Make your diagrams understandable without color:

```mermaid
flowchart TD
    Start([Start Process]) --> Input[User Input Required]
    Input --> Valid{Input Valid?}
    Valid -->|Yes - Continue| Process[Process Data]
    Valid -->|No - Reject| Error[Show Error Message]
```

### Add Comments

Document complex sections:

```mermaid
flowchart TD
    %% This section handles user authentication
    Start[Start] --> Auth[Authenticate]

    %% Token validation and refresh logic
    Auth --> Token{Token Valid?}
    Token -->|Yes| Success[Access Granted]
    Token -->|No| Refresh[Refresh Token]
```

### Provide Context

Always accompany diagrams with text explanations:

**Example:**
This flowchart represents the user authentication process. Users first enter their credentials (Start), which are validated (Authenticate). If the token is valid, access is granted; otherwise, the system attempts to refresh the token.

## GitHub-Specific Tips

### Test Rendering

Always preview your diagrams on GitHub before committing:
1. Create a test branch
2. Push your markdown file
3. View on GitHub to ensure proper rendering
4. Some advanced features may not work on GitHub

### Use Compatible Syntax

Stick to well-supported features:
- Use standard node shapes
- Use `%%{init: ...}%%` for configuration
- Avoid experimental features
- Test theme compatibility

## Resources

- [Mermaid.js Documentation](https://mermaid-js.github.io/mermaid/#/)
- [Mermaid Best Practices Guide](https://mermaid.js.org/intro/)
- [Flowchart Design Principles](https://en.wikipedia.org/wiki/Flowchart)
