# Framework

- An FX Framework file consists of a few elements:
  - Scripts organized in a certain way
  - Custom Functions 

## Script Organization

- There are two types of script folders in the FX Framework:
  - Non-Module folders
    - Schedules
    - Import
    - Triggers
  - Module folders
    - Layouts
    - Modules

### Non-Module Folders

- Schedules
  - Called by the Script Scheduler within FileMaker Server which has no way to filter or sort scripts.
      - Therefore putting this Non-Module folder first sorts all these scripts on top
  - Contains no subfolders
  - Contain no logic
  - NOT versioned
  - Call scripts in this file's > Module's > Public subfolders
 
- Import
  - Contains subfolders (only one level deep)
    - one for each External file 
  - Contain no logic
  - NOT versioned
  - Call scripts in and external file's > Module's > External subfolders

- Triggers
  - File-level script triggers
  - Contains no subfolders (Is this true???)
  - Can contain logic
  - Can be versioned
  - Call scripts in this file's > Module's > Public subfolders
  - Often diplays errors

### Module Folders

- Layouts
  - A Module of individual Layout Modules
  - Each layout Module handles things specific to that layout
- Modules
  - These are the standard Module folder that provide specific functionality
  - There can be any number of these
