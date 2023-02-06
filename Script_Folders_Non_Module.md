# Script Folders - Non-Module

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

- ## Triggers
  - File-level script triggers
  - Contains no subfolders (Is this true???)
  - Can contain logic
  - Can be versioned
  - Often diplays errors
  - Returns True or False, so Script Trigger can proceed or is cancelled

[Back](Script_Functions_And_Types.md) - [Next](Script_Folders_Module.md)

[TOC](TOC.md)
