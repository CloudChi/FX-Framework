# FX Frameworks Scripts Documentation

## Summary

- The Framework system is comprised of multiple FileMaker files which are primarily organized using a specific Script folder/subfolder structure.
  - Each Framework folder handles a specific group of tasks.
    - For example, the Layouts Module handles anything related to Layout navigation 
- Scripts within the Framework have a 3-letter prefix which determines **how** they should be called
  - Excluding scripts in ScriptMenu module which are user-facing

## Script folder categories (organized in this order)

- ### Non-Module folders
  - Schedules
  - Triggers (file level)
  - Import
- ### Module folders
  - Layout
  - Regular

## Non-Module Folders

- ### Schedules
  - Scripts will be called by the Script Scheduler within FileMaker Server which has no way to filter or sort scripts.
      - Therefore putting this Non-Module folder first sorts all these scripts on top.
  - Contains no subfolders
  - Scripts contain no logic
  - Scripts are **not** versioned
  - Scripts can only call scripts in:
    - This file's
      - Regular Module's
        - Public subfolder

- ### Triggers
  -  Place for all file-level script triggers
  -  Contains no subfolders
  -  Scripts contain logic
  -  Scripts are versioned
  -  Scripts can only call scripts in:
    - This file's
      - Regular Module's
        - Public subfolder
  - Handles/Diplays errors
 
- ### Import
  - Contains subfolders (only one level deep)
    - one for each External file 
  - Scripts contain no logic
  - Scripts are **not** versioned
  - Scripts can only call scripts in:
    - An External file's 
      - Regular Module's
        - External subfolder.

## Module Folders

- ### Layout
- ### Regular
- Contains sub-Modules (only one level deep)
- Structure subfolders are in no particular order within the Module folder.
  - Not all Modules will have all the Structure subfolder types, which are only added as needed.  
- Modules are transferable between files with minimal connections required.
- Modules can be addressed by other Modules and they can address other Modules.
- Module scripts use consistently structured JSON for Parameters and Results.
- Module scripts can receive errors (in JSON format) from called subscripts.
- All Module scripts pass errors up to calling scripts, except scripts in the Button, Procedures or Triggers Structure subfolders.


## Script Prefixes
- sub
  - Any script that **must** be called by another script
    - In the following Module Types
      - Public
      - Protected
      - Private  
  - Passes errors
  - Doesn't handle/display errors 
- dep
- btn
  - Called by buttons on layouts
  - Doesn't pass errors
  - Handles/Diplays errors
- trg
  - Called by triggers on layouts
  - Doesn't pass errors
  - Handles/Diplays errors
- cfg???


## Subfolder types (in Regular Modules):

Buttons
Procedures
Triggers
Export
Public
Protected
Private
Dependencies
Config
Templates


Buttons
Scripts in this subfolder do not contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts handle any error they encounter and display it to the user.
Scripts in this subfolder are the ONLY scripts that a button on the layout should call.

Procedures
Scripts in this subfolder do not contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts handle any error they encounter and display it to the user.
Scripts in this subfolder are the ONLY scripts that a non-button procedure should call. For example, Menu Items in a Custom Menu.


Triggers
Scripts in this subfolder can contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts handle any error they encounter and display it to the user.
Script Trigger should ONLY call scripts in this subfolder.
Scripts in this subfolder can be versioned (independently of the Private scripts' versioning)
Scripts return "False" if an error occurred (and maybe set an $ERROR global variable?)
Scripts return JSONObject if they succeed

Export
Scripts in this subfolder do not contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts in this Module can only be called by scripts in an External file's Import Module

Public
Scripts in this subfolder do not contain logic
Contains any script that is addressable from INSIDE or OUTSIDE the Module
Scripts within this subfolder call specifically-versioned scripts within the Private subfolder

Protected
Scripts in this subfolder do not contain logic
Contains any script that is addressable from INSIDE the Module
Scripts within this subfolder call specifically-versioned scripts within the Private subfolder
Typically a script will start as Protected, and will get promoted to the Public subfolder if access to it is needed outside the Module.

Private 
Scripts in this folder can contain logic
These scripts do the majority of the work
Scripts are versioned as changes are needed
Versioning allows developers to test new code and revert to old code by just calling a newer or older version from scripts within the Public or Protected subfolders
Any script in this subfolder that needs to reference a script within this Module calls a Protected script
Any script in this subfolder that needs to reference a script outside this Module calls a script in the Dependencies subfolder which calls an external script using that Module's Public scripts
The scripts in this subfolder should ONLY be addressed by scripts in this Module's Public and Protected subfolders

Dependencies
Scripts in this subfolder do not contain logic
The scripts in this subfolder ONLY call scripts in another Module's Public subfolder
The advantage to this, is if you copy this Module from one file to another, you only have to repoint these scripts.

Config
Scripts/Modules in this subfolder can contain logic
Can contain consumer-coded sub-Modules
Can contain simple scripts that only return a JSONObject of hardcoded values.
Scripts or Modules in this folder can be modified by consumers (not just Framework developers)

Templates
Scripts in this subfolder are specific to this module
Scripts in this subfolder can also work in conjunction with scripts in Config folder
Commonly, there is a Protected style script that calls additional versioned Private scripts
<<.  Should we have Protected and Private folder contained within?   >>
