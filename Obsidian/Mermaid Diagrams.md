
Mermaid allows you to create diagrams using text directly inside Markdown. Obsidian supports Mermaid natively.

---
## **1. Basic Syntax**

Use a `mermaid` code block:

````markdown
```mermaid
flowchart TD
    A[Start] --> B[Process]
    B --> C[End]
```
````

---

## **2. Flowcharts**

### **Direction**

```text
TD = Top → Down
TB = Top → Bottom
LR = Left → Right
RL = Right → Left
BT = Bottom → Top
```

Example:

````markdown
```mermaid
flowchart LR
    A[Client] --> B[API]
    B --> C[Database]
```
````

---

## **3. Node Shapes**

```text
A[Rectangle]

A(Rounded Rectangle)

A([Stadium])

A((Circle))

A{Diamond / Decision}

A[(Database)]

A[[Subroutine]]

A>Asymmetric]
```

Example:

````markdown
```mermaid
flowchart TD
    A[Client] --> B(API)
    B --> C{Valid?}
    C -->|Yes| D[(Database)]
    C -->|No| E[Error]
```
````

---

## **4. Arrows and Connections**

### **Normal Arrow**

```text
A --> B
```

### **Line**

```text
A --- B
```

### **Dashed Arrow**

```text
A -.-> B
```

### **Thick Arrow**

```text
A ==> B
```

### **Arrow with Label**

```text
A -->|Request| B
```

### **Dashed Arrow with Label**

```text
A -.->|Event| B
```

Example:

````markdown
```mermaid
flowchart LR
    Client -->|HTTP Request| API
    API -.->|Async Event| Kafka
    Kafka ==> Consumer
```
````

---

## **5. Decision / Conditional Flow**

Use a diamond `{}` for decisions.

````markdown
```mermaid
flowchart TD
    A[Request] --> B{Authenticated?}

    B -->|Yes| C{Valid Request?}
    B -->|No| D[401 Unauthorized]

    C -->|Yes| E[Process Request]
    C -->|No| F[400 Bad Request]

    E --> G[Return Response]
```
````

---

## **6. Subgraphs**

Use `subgraph` to group components.

````markdown
```mermaid
flowchart LR

    subgraph ClientLayer
        Client[Client]
    end

    subgraph Backend
        API[API]
        Handler[Handler]
    end

    subgraph Database
        DB[(YugabyteDB)]
        Redis[(Redis)]
    end

    Client --> API
    API --> Handler
    Handler --> DB
    Handler --> Redis
```
````

---

## **7. Sequence Diagrams**

Use sequence diagrams when you want to show **who communicates with whom and in what order**.

````markdown
```mermaid
sequenceDiagram
    participant Client
    participant API
    participant DB

    Client->>API: Send Request
    API->>DB: Query Database
    DB-->>API: Return Result
    API-->>Client: Send Response
```
````

### **Common arrows**

```text
->>     Solid message
-->>    Dashed response
-)      Async message
-->>    Dashed response
```

---

## **8. Sequence Diagram with Conditions**

Use `alt` for different outcomes.

````markdown
```mermaid
sequenceDiagram
    Client->>API: POST /users
    API->>DB: Create User

    alt User already exists
        DB-->>API: Duplicate Error
        API-->>Client: 409 Conflict
    else User created
        DB-->>API: Success
        API-->>Client: 201 Created
    end
```
````

---

## **9. Sequence Diagram with Optional Flow**

Use `opt` for optional behavior.

````markdown
```mermaid
sequenceDiagram
    Client->>API: Request

    opt Authentication required
        API->>Auth: Validate Token
        Auth-->>API: Valid
    end

    API-->>Client: Response
```
````

---

## **10. Loops**

Use `loop` when something happens repeatedly.

````markdown
```mermaid
sequenceDiagram
    Client->>API: Request

    loop Retry
        API->>Service: Request
        Service-->>API: Response
    end

    API-->>Client: Final Response
```
````

---

## **11. Notes in Sequence Diagrams**

````markdown
```mermaid
sequenceDiagram
    Client->>API: Request
    Note over API: Validate request
    API->>DB: Query
    DB-->>API: Result
    API-->>Client: Response
```
````

You can use:

```text
Note over A
Note over A,B
Note right of A
Note left of A
```

---

## **12. State Diagrams**

Use state diagrams to represent the lifecycle of an object.

````markdown
```mermaid
stateDiagram-v2
    [*] --> Open
    Open --> InProgress
    InProgress --> Resolved
    Resolved --> Closed
    Closed --> [*]
```
````

### **With transitions**

````markdown
```mermaid
stateDiagram-v2
    [*] --> Pending

    Pending --> Processing: Start
    Processing --> Success: Complete
    Processing --> Failed: Error

    Failed --> Processing: Retry
    Success --> [*]
```
````

---

## **13. Entity Relationship Diagrams**

Use `erDiagram` to represent database relationships.

````markdown
```mermaid
erDiagram
    USER ||--o{ ISSUE : creates
    USER {
        int id
        string name
        string email
    }

    ISSUE {
        int id
        string title
        string status
    }
```
````

### **Common relationship symbols**

```text
||     Exactly one

o|     Zero or one

|{     One or many

o{     Zero or many
```

Example:

```text
USER ||--o{ ISSUE
```

means:

```text
One USER can have zero or many ISSUES.
```

---

## **14. Class Diagrams**

Useful for representing classes and their relationships.

````markdown
```mermaid
classDiagram

    class User {
        +String name
        +String email
        +login()
        +logout()
    }

    class Account {
        +String accountId
        +create()
        +delete()
    }

    User --> Account
```
````

---

## **15. Git Graphs**

Mermaid can represent Git workflows.

````markdown
```mermaid
gitGraph
    commit
    commit
    branch feature
    checkout feature
    commit
    commit
    checkout main
    commit
    merge feature
    commit
```
````

Useful for documenting:

- Feature branches
- Release branches
- Hotfixes
- Merge workflows

---

## **16. Kafka Architecture Example**

````markdown
```mermaid
flowchart LR

    Producer[Producer] --> Topic[Kafka Topic]

    subgraph Kafka
        Topic --> P0[Partition 0]
        Topic --> P1[Partition 1]
        Topic --> P2[Partition 2]
    end

    P0 --> C1[Consumer 1]
    P1 --> C2[Consumer 2]
    P2 --> C3[Consumer 3]

    C1 --> DB[(Database)]
    C2 --> DB
    C3 --> DB
```
````

---

## **17. API Architecture Example**

````markdown
```mermaid
flowchart LR

    Client[Client] --> API[API Gateway]

    API --> Auth[Authentication]
    API --> Handler[Request Handler]

    Handler --> DB[(Database)]
    Handler --> Redis[(Redis)]
    Handler --> Kafka[Kafka]

    Kafka --> Consumer[Consumer]
    Consumer --> DB
```
````

---

## **18. API Request Flow Example**

````markdown
```mermaid
sequenceDiagram

    participant Client
    participant API
    participant Handler
    participant DB
    participant Kafka

    Client->>API: POST /proactive-engagement
    API->>Handler: Validate Request

    alt Invalid Request
        Handler-->>API: Validation Error
        API-->>Client: 400 Bad Request
    else Valid Request
        Handler->>DB: Create Engagement
        DB-->>Handler: Created

        Handler->>Kafka: Publish Event
        Kafka-->>Handler: ACK

        Handler-->>API: Success
        API-->>Client: 201 Created
    end
```
````

---

## **19. Debugging Flow Example**

````markdown
```mermaid
flowchart TD

    A[Error Occurs] --> B[Check Logs]

    B --> C{Error Found?}

    C -->|Yes| D[Identify Root Cause]
    C -->|No| E[Check Metrics]

    E --> F{Issue Identified?}

    F -->|Yes| D
    F -->|No| G[Reproduce Locally]

    D --> H[Implement Fix]
    H --> I[Add Test]
    I --> J[Deploy]
    J --> K[Verify]
```
````

---

## **20. Mermaid Comments**

You can add comments using:

```text
%% This is a Mermaid comment
```

Example:

````markdown
```mermaid
flowchart LR
    %% Client sends request
    Client --> API

    %% API processes request
    API --> DB
```
````

---

## **21. Styling Nodes**

You can apply custom styles.

````markdown
```mermaid
flowchart LR
    A[Client] --> B[API]
    B --> C[(Database)]

    style A fill:#f9f
    style B fill:#bbf
    style C fill:#bfb
```
````

For most notes, you don’t need custom styling. Keeping diagrams simple makes them easier to maintain.

---

## **22. Linking Mermaid Diagrams to Obsidian Notes**

Mermaid itself doesn’t replace Obsidian links, so use Mermaid for the visual relationship and normal Obsidian links around it.

Example:

````markdown
# Kafka Architecture

See also:

- [[Kafka Producer]]
- [[Kafka Consumer]]
- [[Kafka Topic]]
- [[Kafka Partition]]

```mermaid
flowchart LR
    Producer --> Topic
    Topic --> Partition
    Partition --> Consumer
```
````

---

## **23. Which Mermaid Diagram Should I Use?**

|**Requirement**|**Mermaid Type**|
|---|---|
|System architecture|`flowchart`|
|Component relationships|`flowchart`|
|API request flow|`sequenceDiagram`|
|Kafka message flow|`flowchart` / `sequenceDiagram`|
|Database relationships|`erDiagram`|
|Object/class relationships|`classDiagram`|
|Lifecycle|`stateDiagram-v2`|
|Git workflow|`gitGraph`|
|Decision tree|`flowchart`|
|Debugging flow|`flowchart`|

---

## **24. Quick Cheat Sheet**

### **Flowchart**

````markdown
```mermaid
flowchart LR
    A --> B
```
````

### **Node**

```text
A[Rectangle]
A((Circle))
A{Decision}
A[(Database)]
```

### **Arrow**

```text
A --> B
A -->|Label| B
A -.-> B
A ==> B
```

### **Sequence**

````markdown
```mermaid
sequenceDiagram
    A->>B: Request
    B-->>A: Response
```
````

### **State**

````markdown
```mermaid
stateDiagram-v2
    [*] --> Pending
    Pending --> Complete
    Complete --> [*]
```
````

### **Database**

````markdown
```mermaid
erDiagram
    USER ||--o{ ISSUE : creates
```
````

### **Git**

````markdown
```mermaid
gitGraph
    commit
    branch feature
    checkout feature
    commit
    checkout main
    merge feature
```
````

---

## **25. Recommended Pattern for Your Technical Notes**

For a technical topic, structure your note like this:

````markdown
# Kafka

## Overview

What is Kafka?

## Architecture

```mermaid
flowchart LR
    Producer --> Kafka
    Kafka --> Consumer
    Consumer --> Database
````

## **Request / Message Flow**

```mermaid
sequenceDiagram
    Producer->>Kafka: Publish message
    Kafka->>Consumer: Deliver message
    Consumer->>Database: Store data
```

## **Components**

- [[Kafka Producer]]
- [[Kafka Consumer]]
- [[Kafka Topic]]
- [[Kafka Partition]]

## **Common Problems**

…

## **Debugging**

```mermaid
flowchart TD
    Error --> Logs
    Logs --> RootCause
    RootCause --> Fix
```

````
### Quick rule to remember

```text
Architecture      → flowchart
Communication     → sequenceDiagram
Lifecycle         → stateDiagram-v2
Database          → erDiagram
Classes           → classDiagram
Git workflow      → gitGraph
````