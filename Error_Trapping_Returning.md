# Error Trapping and Returning

## Without Framework

- Subscript has an error
- Error is **NOT** passed to calling script
  - Or error is passed to calling script, but calling script does not check for it and does not handle it
- Calling scripts then proceed normally
  - This can have unintended consequences

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Top script] 
    B -- Calls --> C[Subscript 2] 
    C -- Calls --> D[Subscript 2] 
    D -- Throws --> E{{Error}}
    E -.Fails to return error.-> D
    D -- Returns --> C
    C -- Returns --> B
    B -- Returns --> A
```
## With Frameworks

- Subscript has an error
- Error passed up to calling script as JSONObject error package
- Error short circuits calling script with two possible options:
  - Display error to user (sometimes with option to correct and continue)
  - Or just pass the error up to its calling script

```mermaid
graph LR
    A[/User Action/] -- Calls --> B[Top script] 
    B -- Calls --> C[Subscript 1] 
    C -- Calls --> D[Subscript 2] 
    D -- Throws --> E{{Error}}
    E -- Returns Error --> D
    D -- Short Circuits - passes error up --> C
    C -- Short Circuits - passes error up --> B
    B -.-> H[Handles Error - Displaying is most common option]
```
## Summary

- In Frameworks, Errors are captured in subscripts, passed up subscript stack, and are handled by stopping normal execution and displaying error to user if appropriate.

[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
