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
    - Generally do not display results or errors to the user, but they are not prevented from doing so
    - Accept parameters in JSON format
    - Return results or errors in JSON format
    - Subscripts contain MOST of the logic in the Framework module
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
        - Handles being called from any context
        - Returns error if not in right context  

  - ## Non-Subscripts 
    - Often display any returned errors
    - Accept parameters in JSON format
    - Within a given Type they are often copies of each other
    - Types:
      - Schedule
      - Export
      - Import
      - Button
      - Trigger
      - Procedures
      - Template (sometimes)

[TOC](TOC.md)
