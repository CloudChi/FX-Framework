# Error Trapping and Returning

## Without Framework

- Subscript has an error
- Error is **NOT** passed to calling script
- Calling scripts proceed normally
  - This can have unintended consequences

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Subscript 1] 
    B -- Calls --> C[Subscript 2] 
    C -- Calls --> D[Subscript 3] 
    D -- Throws --> E{{Error}}
    E -.Fails to return error.-> D
    D -- Returns --> C
    C -- Returns --> B
    B -- Returns --> A
```
## With Frameworks

- Subscript has an error
- Error passed to calling script as JSONObject error package
- Calling scripts short circuit
- Top script displays human-readable and actionable error text

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Subscript 1] 
    B -- Calls --> C[Subscript 2] 
    C -- Calls --> D[Subscript 3] 
    D -- Throws --> E{{Error}}
    E -- Returns Error --> D
    D -- Short Circuits --> C
    C -- Short Circuits --> B
    B -- Short Circuits --> A
    A --> H(Displays Error)    
```

[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
