# Modules
- Modules are script folders
- Modules contain subfolders
- Each subfolder type serves a specific purpose
- Some Modules contain sub-Modules, but never more than one layer deep
- A Module presents certain tools to the developer

## Module Subfolder Structure

- Module
  - Buttons
  - Scripts Menu
  - Triggers
  - Export
  - Public
  - Protected
  - Private
  - Dependencies
  - Config
  - Templates
  - Deprecated 

## Subfolder Details

### Scripts in these folders have the following characteristics

- Buttons
  - Do not contain logic
  - Call scripts in Public or Protected subfolders
  - Display errors to the user
  - Only called by buttons on layouts

- Scripts Menu
  - Do not contain logic
  - Call scripts in Public or Protected subfolders
  - Display errors to the user
  - Only called from Scripts Menu
    - Should be human-readable and clearly named 


- Triggers
  - Can contain logic
  - Call scripts in Public or Protected subfolders
  - Display errors to the user
  - Only called by Script Triggers
  - Can be versioned
  - Return "False" if an error occurs
  - Return JSONObject if they succeed

- Export
  - Do not contain logic
  - Call scripts in Public or Protected subfolders
  - Only called by scripts in an External file's Import Module

- Public
  - Contain logic for versions
  - Call versioned scripts in Private subfolder
  - Callable from inside or outside the Module

- Protected
  - Contain logic for versions
  - Call versioned scripts in Private subfolder
  - Callable only from inside the Module
    - Promoted to Public subfolder if access is needed outside Module

- Private
  - Can contain logic
  - Do the majority of the work (how do we say this???)
  - Versioned as needed
    - Allows developers to test new code
    - Revert to old code by just calling older version
  - Call external scripts via Dependencies subfolder
  - Callable either from Public or Protected subfolders, not both

- Dependencies
  - Do not contain logic
  - Call scripts in another Module's Public subfolder
    - Modules copied to another file need to repoint these scripts

- Config
  - Can contain logic
  - Can contain consumer-coded sub-Modules
    - Only subfolder that can contain Modules
  - Can contain simple scripts that only return a JSONObject of hardcoded values
  - Can be modified by consumers (not just Framework developers)

- Templates
  - Specific to this module
  - Work in conjunction with scripts in Config folder
  - Commonly, there is a Protected style script that calls additional versioned Private scripts

- Deprecated
  - No longer being used 
  - Kept here temporarily instead of deleted, in case they need to be referenced
