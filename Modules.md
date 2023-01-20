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
    - Therefore should be human-readable and clearly named 


- Triggers
  - Can contain logic
  - Call scripts in Public or Protected subfolders
  - Display errors to the user
  - Only called by Script Triggers
  - Can be versioned (independently of the Private scripts' versioning)
  - Return "False" if an error occurs
  - Return JSONObject if they succeed

- Export
  - Do not contain logic
  - Call scripts in Public or Protected subfolders
  - Only called by scripts in an External file's Import Module

- Public
  - Only contain logic for version choosing
  - Contains any script that is addressable from INSIDE or OUTSIDE the Module
  - Scripts within this subfolder call specifically-versioned scripts within the Private subfolder

- Protected
  - Only contain logic for version choosing
  - Contains any script that is addressable from INSIDE the Module
  - Scripts within this subfolder call specifically-versioned scripts within the Private subfolder
  - Typically script will start as Protected, and get promoted to the Public subfolder if access to it is needed outside the Module

- Private
  - Can contain logic
  - Do the majority of the work
  - Versioned as changes are needed
    - Allows developers to test new code
    - Revert to old code by just calling a newer or older version from scripts within the Public or Protected subfolders
  - Any script in this subfolder that needs to reference a script within this Module calls a Protected script
  - Any script in this subfolder that needs to reference a script outside this Module calls a script in the Dependencies subfolder which calls an external script using that Module's Public scripts
  - Only addressed by scripts in this Module's Public and Protected subfolders

- Dependencies
  - Do not contain logic
  - Call scripts in another Module's Public subfolder
    - If you copy this Module from one file to another, you only have to repoint these scripts.

- Config
  - Can contain logic
  - Can contain consumer-coded sub-Modules
  - The only subfolder that can contain Modules
  - Can contain simple scripts that only return a JSONObject of hardcoded values.
  - Scripts or Modules in this folder can be modified by consumers (not just Framework developers)

- Templates
  - Scripts in this subfolder are specific to this module
  - Scripts in this subfolder can also work in conjunction with scripts in Config folder
  - Commonly, there is a Protected style script that calls additional versioned Private scripts

- Deprecated
  - XXX
