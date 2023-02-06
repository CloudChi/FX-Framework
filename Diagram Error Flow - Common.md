# Error Trapping and Returning

## Common Coding

In common coding practices:
- Error is thrown by a subscript it is **NOT** caught and therefore doesn't shortcircuit any calling scripts

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
- Error is thrown by a subscript it **IS** caught, short circuits any calling scripts, and displays a meaningful error to the user.

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Subscript 1] 
    B -- Calls --> C[Subscript 2] 
    C -- Calls --> D[Subscript 3] 
    D -- Throws --> E{{Error}}
    E --> F{JSONObject Error Package}
    F --> D
    D -- Short Circuits --> C
    C -- Short Circuits --> B
    B -- Short Circuits --> A
    A -- Displays --> G(Error Dialog to User)
```
