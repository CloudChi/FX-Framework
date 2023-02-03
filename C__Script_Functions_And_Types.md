# Script Functions and Types

- All scripts are responsible for capturing and returning:
  - Any errors they encounter
  - Any results they generate
- All Scripts use JSONObjects to:
  - Accept parameters
  - Return results, or any errors
    - Except Trigger scripts – which return True or False (to Proceed with or Cancel calling trigger, respectively)
- Scripts are divided into two basic types:
  - ## Subscripts
    - Generally do not display results or errors to the user
      - Errors can be displayed if user needs to make decision or provide data in middle of call stack
        - For example, placing an order for a Customer on Credit Hold, Salesperson can decide to let this one order go through
    - Types:
      - Public
      - Protected
      - Private
      - Config
      - Template (sometimes)
    - Context Independent
      - Mode (Browse, Find, etc)
      - Layout / Tables / Fields
      - Either:
        - Handles being called from any Context
        - Returns error if not in right Context   
  - ## Non-Subscripts 
    - Often display any returned errors
    - Within a given Type they are often copies of each other
    - Types:
      - Schedule
      - Export
      - Import
      - Button
      - Trigger
      - Procedures
      - Template (sometimes)
  
[Next](D__Script_Folders_Non_Module.md)
