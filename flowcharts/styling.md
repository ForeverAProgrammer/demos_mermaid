# Styling and Colors in Mermaid Flowcharts

This document demonstrates how to style nodes and links in Mermaid flowcharts using colors, CSS classes, and inline styles.

## Table of Contents

- [Basic Node Styling](#basic-node-styling)
- [Styling Individual Nodes](#styling-individual-nodes)
- [Styling Multiple Nodes](#styling-multiple-nodes)
- [Link Styling](#link-styling)
- [Using CSS Classes](#using-css-classes)
- [Color Examples](#color-examples)
- [Resources](#resources)

## Basic Node Styling

You can style individual nodes using the `style` keyword followed by the node ID and CSS properties:

```mermaid
flowchart LR
    A[Normal Node]
    B[Styled Node]
    style B fill:#f9f,stroke:#333,stroke-width:4px
```

## Styling Individual Nodes

### Fill and Stroke Colors

```mermaid
flowchart TD
    A[Default]
    B[Blue Fill]
    C[Red Border]
    D[Both Styled]

    style B fill:#4287f5,stroke:#333
    style C fill:#fff,stroke:#ff0000,stroke-width:3px
    style D fill:#90EE90,stroke:#006400,stroke-width:4px
```

### Text Styling

```mermaid
flowchart LR
    A[Normal Text]
    B[Bold Text]
    C[Large Text]

    style B fill:#f9f,stroke:#333,color:#000,font-weight:bold
    style C fill:#ff9,stroke:#333,font-size:20px
```

## Styling Multiple Nodes

Style multiple nodes at once by listing their IDs separated by commas:

```mermaid
flowchart TD
    Start([Start]) --> Process1[Process 1]
    Process1 --> Process2[Process 2]
    Process2 --> Process3[Process 3]
    Process3 --> End([End])

    style Start fill:#90EE90,stroke:#006400,stroke-width:2px
    style Process1,Process2,Process3 fill:#87CEEB,stroke:#4682B4,stroke-width:2px
    style End fill:#FFB6C1,stroke:#DC143C,stroke-width:2px
```

## Link Styling

### Basic Link Styling

```mermaid
flowchart LR
    A[Node A] -->|Normal| B[Node B]
    B -->|Styled| C[Node C]

    linkStyle 1 stroke:#ff3,stroke-width:4px,color:red
```

### Multiple Link Styles

```mermaid
flowchart TD
    A[Start] --> B[Step 1]
    B --> C[Step 2]
    C --> D[Step 3]
    D --> E[End]

    linkStyle 0 stroke:#0f0,stroke-width:2px
    linkStyle 1 stroke:#00f,stroke-width:2px
    linkStyle 2 stroke:#f0f,stroke-width:2px
    linkStyle 3 stroke:#f00,stroke-width:2px
```

## Using CSS Classes

Define and apply CSS classes to nodes:

```mermaid
flowchart LR
    A[Success Node]:::success
    B[Warning Node]:::warning
    C[Error Node]:::error
    D[Info Node]:::info

    A --> B --> C --> D

    classDef success fill:#90EE90,stroke:#006400,stroke-width:2px
    classDef warning fill:#FFD700,stroke:#FFA500,stroke-width:2px
    classDef error fill:#FFB6C1,stroke:#DC143C,stroke-width:2px
    classDef info fill:#87CEEB,stroke:#4682B4,stroke-width:2px
```

### Applying Classes to Multiple Nodes

```mermaid
flowchart TD
    Start([Start]) --> Input1[Input A]
    Start --> Input2[Input B]
    Input1 --> Process[Process Data]
    Input2 --> Process
    Process --> Output[Output]

    class Input1,Input2 inputClass
    class Process processClass
    class Output outputClass

    classDef inputClass fill:#E6E6FA,stroke:#9370DB,stroke-width:2px
    classDef processClass fill:#FFF8DC,stroke:#DAA520,stroke-width:2px
    classDef outputClass fill:#F0FFF0,stroke:#228B22,stroke-width:2px
```

## Color Examples

### Using Hex Colors

```mermaid
flowchart LR
    A[Red #FF0000]
    B[Green #00FF00]
    C[Blue #0000FF]
    D[Yellow #FFFF00]
    E[Purple #800080]

    A --> B --> C --> D --> E

    style A fill:#FF0000,color:#fff
    style B fill:#00FF00,color:#000
    style C fill:#0000FF,color:#fff
    style D fill:#FFFF00,color:#000
    style E fill:#800080,color:#fff
```

### Common Color Palette

```mermaid
flowchart TD
    Primary[Primary #2563eb]
    Secondary[Secondary #64748b]
    Success[Success #10b981]
    Warning[Warning #f59e0b]
    Danger[Danger #ef4444]
    Info[Info #06b6d4]

    style Primary fill:#2563eb,stroke:#1e40af,color:#fff,stroke-width:2px
    style Secondary fill:#64748b,stroke:#475569,color:#fff,stroke-width:2px
    style Success fill:#10b981,stroke:#059669,color:#fff,stroke-width:2px
    style Warning fill:#f59e0b,stroke:#d97706,color:#fff,stroke-width:2px
    style Danger fill:#ef4444,stroke:#dc2626,color:#fff,stroke-width:2px
    style Info fill:#06b6d4,stroke:#0891b2,color:#fff,stroke-width:2px
```

## Practical Example: Process Flow with Styling

```mermaid
flowchart TD
    Start([Start Process]):::startEnd --> Input[/User Input/]:::io
    Input --> Validate{Valid?}:::decision
    Validate -->|Yes| Process[[Process Data]]:::process
    Validate -->|No| Error[Display Error]:::error
    Error --> Input
    Process --> Save[(Save to DB)]:::database
    Save --> Success[Success Message]:::success
    Success --> End([End]):::startEnd

    classDef startEnd fill:#90EE90,stroke:#006400,stroke-width:3px,color:#000
    classDef io fill:#E6E6FA,stroke:#9370DB,stroke-width:2px
    classDef decision fill:#FFD700,stroke:#FFA500,stroke-width:2px
    classDef process fill:#87CEEB,stroke:#4682B4,stroke-width:2px
    classDef error fill:#FFB6C1,stroke:#DC143C,stroke-width:2px
    classDef success fill:#90EE90,stroke:#228B22,stroke-width:2px
    classDef database fill:#DDA0DD,stroke:#9370DB,stroke-width:2px
```

## Resources

- [Mermaid.js Documentation](https://mermaid-js.github.io/mermaid/#/)
- [Mermaid Styling Documentation](https://mermaid.js.org/syntax/flowchart.html#styling-and-classes)
- [CSS Colors Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value)
