# Files

- An FX Framework file consists of a few elements:
  - Scripts organized in a certain way
  - Custom Functions 

## Script Organization

- There are two types of script folders in the FX Framework:
  - Container folders (aka Non-Module)
    - Schedules
    - Import
    - Triggers
  - Module folders
    - Layouts
    - Regular

### Container Folders

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
  - File-level script triggers
  - Contains no subfolders (Is this true???)
  - Can contain logic
  - Can be versioned
  - Call scripts in this file's > Regular Module's > Public subfolders
  - Diplays errors

### Module Folders

- Layouts
  - A Module of individual Layout Modules
  - Each layout Module handles things specific to that layout
- Regular
  - These are the standard Module folder that provide specific functionality
  - There can be any number of these

## Custom Functions

- Avoid duplication of code
- If error encountered return "?"
  - This is expected behavior for FileMaker's built in Custom Functions 
- Named with "Fx." prefix to differentiate from:
  - FileMakers included Custom Functions
  - Custom Functions that may have been added as part of a Plugin
    - Troi File plugin adds "TrFile_"... Custom Functions, like "TrFile_CopyFile"
- Named in TitleCase so they support type-ahead in calculation window
  - "Fx.DoSomethingCool" can be entered by typing "fdsc"
    - "Fx.do_something_cool" cannot
- with a certain convention to indicate where and how they are used
- They are 
