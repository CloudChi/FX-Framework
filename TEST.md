# Error Trapping and Returning

## Common Coding

- Error thrown by subscript
- **NOT** caught
- Therefore doesn't shortcircuit any calling scripts
  - Which may have unexpected outcomes

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
## Frameworks Coding

- Error is thrown by a subscript
- **IS** caught
- Error information packaged in JSONObject
  - Including script name
- Short circuits any calling scripts
  - Which add their script name to JSONObject Error Package
  - Pass error to their calling script 
- Top script parses JSONObject Error Package into
  - Human-readable and actionable error text
  - Full path of error through scripts
    - not just script that threw error
  - Displays to user

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Subscript 1] 
    B -- Calls --> C[Subscript 2] 
    C -- Calls --> D[Subscript 3] 
    D -- Throws --> E{{Error}}
    E -- Builds --> F[JSONObject Error Package]
    F --> D
    D -- Short Circuits --> C
    C -- Short Circuits --> B
    B -- Short Circuits --> A
    A -- Parses --> G[JSONObject Error Package w/full path]
    G -- Displays --> H(Error Dialog to User)    
```
[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
