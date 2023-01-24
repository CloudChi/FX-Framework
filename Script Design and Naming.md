# Script Design and Naming

## Script Design

- All scripts are responsible for handling and passing back:
  - Any errors they encounter
  - Any results they generate
- All Scripts use JSONObjects or JSONArrays to:
  - Pass parameters down
  - Pass results back up
  - Or pass any errors up
- Scripts are divided into two basic types:
  - Subscripts
    - Will NOT display results or errors to the user
  - Top level scripts 
    - WILL display any returned result or error to the user
    - These include the following script types:
      - Button
      - Trigger
      - Script Menu

## Script Naming

- Script names start with a 3-letter prefix which determines **how** they should be called
  - Script prefix definitions:
    - btn
      - Called by Buttons on Layouts
      - Displays errors
    - trg
      - Called by Script Triggers
      - Returns False if errors
      - Returns JSON if no error 
        - (Why is this, since it should be top level???)
    - sub
      - Called as a subscript
      - Never called as top level 
      - Passes back results or errors in JSON format
      - Does not display errors
      - Can be found in various Module subfolders (unlike other prefixes)
        - Private
        - Protected
        - Public
        - Export
        - Dependencies
      - Can be found in various file Component folders (unlike other prefixes)
        - Schedules
        - Import
        - Triggers (file level)
    - dpr
      - Deprecated, so should NEVER be called by any other script
      - Can be any type previously
    - (BLANK)
      - Called by Scripts Menu > Menu Items
      - They need to be human readable, so therefore no Prefix
      - Displays errors
