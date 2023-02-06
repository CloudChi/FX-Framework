# Versions and Updating

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
```
## Frameworks Coding

In Frameworks coding practices:
- Error is thrown by a subscript
- **IS** caught
- Packaged in JSONObject
  - Including script name
- Short circuits any calling scripts
  - Which add their script name to error stack
  - Pass error to their calling script 
- Displays a meaningful error to the user
  - showing human-readable and actionable error text
  - showing full path of error through scripts
    - not just script that threw error

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Subscript 1] 
    B -- Calls --> C[Subscript 2]  
```

[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
