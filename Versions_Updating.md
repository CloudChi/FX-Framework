# Versions and Updating

## Common Versioning and Updating

- Developers have to update every location the script is called from
  - If they miss a location, the system might behave differently there
  - If they need to roll back after a bug was discovered they have to reverse the process correctly 
- As files grow in size and complexity and as a script gets used more and more, this gets more and more difficult
  - If versioning gets too complicated, developers just move onto creating a new script and using it in any new place they code. 
    - Therefore, the script versions become like an archeological dig and an historical marker

```mermaid
graph LR
    A[Script 1] -- Calls --> F[Subscript V1] 
    B[Script 2] -- Calls --> F
    C[Script 3] -- Calls --> F
    D[Script 4] -- Calls --> F
    E[Script 5] -- Calls --> F
```

```mermaid
graph LR
    A[Script 1] -. Transition To. -> G[Subscript V2] 
    B[Script 2] -. Transition To. -> G 
    C[Script 3] -. Transition To. -> G 
    D[Script 4] -. Transition To. -> G 
    E[Script 5] -. Transition To. -> G 
```
## Frameworks Versioning and Updating

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
