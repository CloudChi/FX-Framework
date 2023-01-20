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
  - Call scripts within this Module's Public or Protected subfolders.
  - Handle any error they encounter and display it to the user.
  - ONLY scripts that a button on the layout should call.

- Scripts Menu
  - D not contain logic
  - Call scripts within this Module's Public or Protected subfolders.
  - Handle any error they encounter and display it to the user.
  - ONLY scripts that a non-button procedure should call. For example, Menu Items in a Custom Menu.


- Triggers
  - Scripts in this subfolder can contain logic
  - Scripts call scripts within this Module's Public or Protected subfolders.
  - Scripts handle any error they encounter and display it to the user.
  - Script Trigger should ONLY call scripts in this subfolder.
  - Scripts in this subfolder can be versioned (independently of the Private scripts' versioning)
  - Scripts return "False" if an error occurred (and maybe set an $ERROR global variable?)
  - Scripts return JSONObject if they succeed

- Export
  - Scripts in this subfolder do not contain logic
  - Scripts call scripts within this Module's Public or Protected subfolders.
  - Scripts in this Module can only be called by scripts in an External file's Import Module

- Public
  - Scripts in this subfolder do not contain logic
  - Contains any script that is addressable from INSIDE or OUTSIDE the Module
  - Scripts within this subfolder call specifically-versioned scripts within the Private subfolder

- Protected
  - Scripts in this subfolder do not contain logic
  - Contains any script that is addressable from INSIDE the Module
  - Scripts within this subfolder call specifically-versioned scripts within the Private subfolder
  - Typically a script will start as Protected, and will get promoted to the Public subfolder if access to it is needed outside the Module.

- Private
  - Scripts in this folder can contain logic
  - These scripts do the majority of the work
  - Scripts are versioned as changes are needed
  - Versioning allows developers to test new code and revert to old code by just calling a newer or older version from scripts within the Public or Protected subfolders
  - Any script in this subfolder that needs to reference a script within this Module calls a Protected script
  - Any script in this subfolder that needs to reference a script outside this Module calls a script in the Dependencies subfolder which calls an external script using that Module's Public scripts
  - The scripts in this subfolder should ONLY be addressed by scripts in this Module's Public and Protected subfolders

- Dependencies
  - Scripts in this subfolder do not contain logic
  - The scripts in this subfolder ONLY call scripts in another Module's Public subfolder
  - The advantage to this, is if you copy this Module from one file to another, you only have to repoint these scripts.

- Config
  - Scripts/Modules in this subfolder can contain logic
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
