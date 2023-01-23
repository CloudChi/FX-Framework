# Script Naming and Functions

## Script Naming

- Script names start with a 3-letter prefix which determines **how** they should be called
  - Script prefix definitions:
    - btn
      - Called by Buttons on Layouts
      - Display errors
    - trg
      - Called by Script Triggers
      - Returns False if errors
      - Returns JSON if no error 
        - (Why is this, since it should be top level???)
    - sub
      - Called as subscripts
      - Never called as top level 
      - Pass back results or errrors in JSON format
      - Do not display errors
      - Can be found in various Module subfolders (unlike other prefixes)
        - Private
        - Protected
        - Public
        - Export
        - Dependencies
        - Import (Is this a subfolder or a file level folder???)
    - dpr > Deprecated (is this true?)
      - These scripts should NEVER be called by any other script
      - Not of any specific type, otherwise
    - (BLANK)
      - Called by Scripts Menu > Menu Items
      - They need to be human readable, so therefore no Prefix
      -  - Display errors

## Script Functions

- All scripts are responsible for handling and passing back:
  - Any errors they encounter
  - Any results they generate
- All Scripts use JSONObjects or JSONArrays to:
  - Pass parameters down
  - Pass results back up
  - Or pass any errors up
- Any subscript will pass JSON back and forth but will NOT display results or errors to the user
- Any top level script WILL display any returned result or error to the user. 
  - These include the following script types:
    - Button
    - Trigger
    - Script Menu
