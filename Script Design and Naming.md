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
- The script call stack will pass parameters down and results or errors up using consistent JSON structures
-  Any top level script initiated by a user (Button, Trigger, Script Menu scripts) will all display any returned error to the user.
