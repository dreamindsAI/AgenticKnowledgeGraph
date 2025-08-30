# Agentic Knowledge Graph

---

To transform structured and unstructured data into the knowledge graph, you first need to decide the graph schema, what types of entities or nodes you can extract from the data and what relationships exists between them.

## What is a Knowledge Graph?

```mermaid

graph LR
    %% Persons inside a subgraph
    subgraph Persons
        A["Person A"]
        B["Person B"]
    end

    %% Person-Product combinations
    subgraph PersonProducts
        AChair["A-Chair"]
        ATable["A-Table"]
        BTable["B-Table"]
        BChair["B-Chair"]
        BLamp["B-Lamp"]
    end

    %% Products inside a subgraph
    subgraph Products
        Chair["Chair"]
        Table["Table"]
        Lamp["Lamp"]
    end

    %% Relationships
    A --> AChair --> Chair
    A --> ATable --> Table
    B --> BTable --> Table
    B --> BChair --> Chair
    B --> BLamp --> Lamp
    %% Styles
    %% Persons (A, B)
    style A fill:#cce5ff,stroke:#004080,stroke-width:2px
    style B fill:#cce5ff,stroke:#004080,stroke-width:2px

    %% A's Products
    style AChair fill:#d4edda,stroke:#155724,stroke-width:2px
    style ATable fill:#d4edda,stroke:#155724,stroke-width:2px

    %% B's Products
    style BTable fill:#ffe5b4,stroke:#cc8400,stroke-width:2px
    style BChair fill:#ffe5b4,stroke:#cc8400,stroke-width:2px
    style BLamp fill:#ffe5b4,stroke:#cc8400,stroke-width:2px

    %% Final Products
    style Chair fill:#ffcccc,stroke:#666666,stroke-width:2px
    style Table fill:#ffcccc,stroke:#666666,stroke-width:2px
    style Lamp fill:#ffcccc,stroke:#666666,stroke-width:2px
```

We could construct a recomender system from this. We know what `A` purchases. We know who else purchases the product that `A` purchases. We also know the additional products that they purchases. Based on this, we can recommend new products to `A`.

```mermaid
graph LR

    A["Person : A"]
    B["Person : B"]
    Chair["Product : Chair"]
    Table["Product : Table"]
    Lamp["Product : Lamp"]

    %% Relationships
    A--Purchased-->Chair
    A--Purchased-->Table
    B--Purchased-->Chair
    B--Purchased-->Table
    B--Purchased-->Lamp


    %% Styles
    %% Persons (A, B)
    style A fill:#cce5ff,stroke:#004080,stroke-width:2px
    style B fill:#cce5ff,stroke:#004080,stroke-width:2px


    %% Final Products
    style Chair fill:#ffcccc,stroke:#666666,stroke-width:2px
    style Table fill:#ffcccc,stroke:#666666,stroke-width:2px
    style Lamp fill:#ffcccc,stroke:#666666,stroke-width:2px
```

```
Knoweledge graph is a kind of database that represents information as nodes representing things like people, products, blogs and relationships that add information about pairs of things like purchased, authored, liked.
```

Query Language : `Cipher`, for quering from the graph.

Example : root-cause analysis

A furniture manufaturer trying understand the complaints.

- Which products have the most issues?
- What part of the product is the problem?
- Is there a problem with the part itself?
