# Error Trapping and Returning

## Common Coding

In common coding practices:
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

In Frameworks coding practices:
- Error is thrown by a subscript
- **IS** caught
- Returned as JSONObject Error Package (aka JEP)
  - Includes script name
  - Human-readable error
  - FileMaker error code
- Short circuits any calling scripts
  - Which add their script name to JEP
  - Pass JEP to their calling script 
- Top script calls JEP parsing rountine
- Then calls a routine which displays:
  - showing human-readable and actionable error text
  - showing full path of error through scripts
    - not just script that threw error

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

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Subscript 1] 
    B -- Calls --> C[Subscript 2] 
    C -- Calls --> D[Subscript 3] 
    D -- Throws --> E{{Error}}
    E -- Builds JSONObject Error Package --> D
    D -- Short Circuits --> C
    C -- Short Circuits --> B
    B -- Short Circuits --> A
    A -- Parses JSONObject Error Package w/full path --> H(Displays Error Dialog to User)    
```

[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
