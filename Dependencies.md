# Dependencies

## Common Dependencies

- References to Module B - Script 1 can be found anywhere in a Module A scattered amongst scripts
- If Module A is moved each of these references has to be repointed

```mermaid
graph LR
A[Module A - Script 1] -- Calls --> E[Module B - Script 1] 
B[Module A - Script 2] -- Calls --> F[Module B - Script 1]
C[Module A - Script 3] -- Calls --> G[Module B - Script 1]
```

## Frameworks Dependencies

- References to Module B - Script 1 can be found in one place in Module A
- If Module A is moved only this reference has to be repointed

```mermaid
graph LR
A[Module A - Script 1] -- Calls --> F[Module B - Script 1] 
B[Module A - Script 2] -- Calls --> F
C[Module A - Script 3] -- Calls --> F
```

[Back](Introduction.md) - [Next](Script_Functions_And_Types.md)

[TOC](TOC.md)
