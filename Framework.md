# Framework

- The FX Framework consists of a few key elements:
  - [Script Functions and Types](Script_Functions_And_Types.md)
  - [Script Folders - Non-Module](Script_Folders_Non_Module.md)
  - [Script Folders - Module](Script_Folders_Module.md)
  - [Script Naming](Script_Naming.md)
  - [Custom Functions](Custom_Functions.md)

## Script Organization and Naming

- There are two types of script folders in the FX Framework:
  - Non-Module folders
    - Schedules
    - Import
    - Triggers
  - Module folders
    - Modules 
    - Grouped Modules

### Non-Module Folders

- Schedules
  - Called by the Script Scheduler within FileMaker Server which has no way to filter or sort scripts.
      - Therefore putting this Non-Module folder first sorts all these scripts on top
  - Contains no subfolders
  - Contain no logic
  - NOT versioned
  - Call scripts in this file's Public subfolders
 
- Import
  - Contains subfolders
    - one for each External file 
  - Contain no logic
  - NOT versioned
  - Call scripts in an external file's External subfolders

- Triggers
  - File-level script triggers
  - Contains no subfolders (Is this true???)
  - Can contain logic
  - Can be versioned
  - Often diplays errors
  - Returns True or False, so Script Trigger can proceed or is cancelled

### Module Folders

- Modules
  - These are the standard Module folder that provide specific functionality
  - There can be any number of these
- Grouped Modules
  - Contain:
    - Individual Sub-Modules
    - Shared Dependencies folder
      - Removes Dependencies folders inside each Sub-Module
  - Example of this is Layouts module which looks like this:
    - Layouts
      - Dependencies
      - Layout A
      - Layout B
      - Layout C
  - Sub-Modules can use Dependencies of Parent Module
