# Files

## Script Organization

- There are two types of script folders in the FX Framework:
  - Non-Module folders, (aka Containers???)
    - Schedules
    - Import
    - Triggers
  - Module folders
    - Layouts
    - Regular

## Container Folders

- Schedules
  - Called by the Script Scheduler within FileMaker Server which has no way to filter or sort scripts.
      - Therefore putting this Non-Module folder first sorts all these scripts on top
  - Contains no subfolders
  - Contain no logic
  - NOT versioned
  - Call scripts in this file's > Regular Module's > Public subfolders
 
- Import
  - Contains subfolders (only one level deep)
    - one for each External file 
  - Contain no logic
  - NOT versioned
  - Call scripts in and external file's > Regular Module's > External subfolders

- Triggers
  -  File-level script triggers
  -  Contains no subfolders
  -  Can contain logic
  -  Can be versioned
  -  Call scripts in this file's > Regular Module's > Public subfolders
  - Handles/Diplays errors

## Module Folders

- ### Layout
- ### Regular

## Custom Functions
