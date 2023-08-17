# Script Folders - Non-Module
- Non-Module script folders exist on the File level and **not** within Modules
- They perform file specific tasks
- There is one Non-Module folder type per file
- Non-Module folders are not designed to be movable to another file 

- ## Schedules
  - Called by the Script Scheduler within FileMaker Server which has no way to filter or sort scripts.
      - Therefore putting this Non-Module folder first sorts all these scripts on top
  - Contains no subfolders
  - Contain no logic
  - NOT versioned
  - Call scripts in this file's Public subfolders
 
- ## Import
  - Contains subfolders
    - one for each External file 
  - Contain no logic
  - NOT versioned
  - Call scripts in an external file's External subfolders
  - For example the Import folder in File A:
    - Import
      - File B Import
      - File C Import
      - File D Import 

- ## File Triggers
  - File-level script triggers
  - Can contain subfolders
  - Can contain logic
  - Can be versioned

> Why are they versioned instead of calling versioned scripts in Public folders?

  - Often diplays errors
  - Returns True or False, so Script Trigger can proceed or is cancelled

  > For File Triggers, which module subfolderss do they call scripts in, Public?

[Back](Script_Functions_And_Types.md) - [Next](Script_Folders_Module.md)

[TOC](TOC.md)
