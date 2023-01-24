# Script Organization

- All scripts are responsible for capturing and returning:
  - Any errors they encounter
  - Any results they generate
- All Scripts use JSONObjects to:
  - Accept parameters
  - Return results, or any errors
  - Except Trigger scripts – which return True or False (to Proceed with or Cancel calling trigger, respectively)
- Scripts are divided into two basic types:
  - Subscripts
    - Generally do not display results or errors to the user
    - Types:
      - Public
      - Protected
      - Private
    - Context Independent
      - Mode (Browse, Find, etc)
      - Layout / Tables / Fields
      - Either:
        - Handles being called from any Context
        - Returns error if not in right Context   
  - Non-Subscripts 
    - Often display any returned errors
    - Types:
      - Schedule
      - Export
      - Import
      - Button
      - Trigger
      - Script Menu
    - Carbon copies of each other 





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

