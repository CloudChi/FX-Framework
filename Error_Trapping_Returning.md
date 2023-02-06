# Error Trapping and Returning

## Common Coding

In common coding practices:
- Subscript has an error
- Error is **NOT** passed to calling script
- Calling script proceeds as if subscript performed as expected
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
## Frameworks Coding

In Frameworks coding practices:
- Subscript has an error
- Error passed to calling script as JSONObject error package
- Short circuits any calling scripts
  - Which add their script name to JSONObject
  - Then pass JSONObject to their calling script 
- Top script calls error display script which:
  - parses JSONObject error package
  - displays human-readable and actionable error text
  - including full path of error through scripts
    - not just script that had error

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
    A --> H(Displays Error Dialog to User)    
```

[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
