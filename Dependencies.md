# Dependencies

## Common Dependencies

- Found anywhere in a Module scattered amongst scripts

```mermaid
graph LR
A[Module A - Script 1] -- Calls --> F[Module B - Script 1] 
B[Module A - Script 2] -- Calls --> F
C[Module A - Layout 1] -- Calls --> F
```

## Frameworks Dependencies

- XXX

```mermaid
graph LR
    A[Script 1] -- Calls --> F[Public script] -- Calls --> G[Private script V1]
    B[Script 2] -- Calls --> F
    C[Script 3] -- Calls --> F
    D[Script 4] -- Calls --> F
    E[Script 5] -- Calls --> F
```

[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
