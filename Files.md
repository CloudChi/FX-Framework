# Files

## Script Organization

- There are two types of script folders in the FX Framework:
  - Non-Module folders, aka Containers
    - Schedules
    - Import
    - Triggers
  - Module folders
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
 
- ### Import
  - Contains subfolders (only one level deep)
    - one for each External file 
  - Scripts contain no logic
  - Scripts are **not** versioned
  - Scripts can only call scripts in:
    - An External file's 
      - Regular Module's
        - External subfolder.

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

## Module Folders

- ### Layout
- ### Regular

## Custom Functions
