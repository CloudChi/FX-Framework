# Script Naming

- Script names start with a 3-letter prefix which determines **HOW** they should be called:
  - sched > Schedule
    - Called by FileMaker server
    - Compatible with running on Server 
      - For example, no elements requiring user actions
  - exp > Export
    - Called from another file's Import folder scripts
      - Versus Protected subscripts which are called from any of the same file's Modules scripts
  - imp > Import
    - Calls scripts in another files Export folder
    - All Modules/scripts in external files are accessed in this one point
  - btn > Button
    - Called by Buttons on Layouts
    - Typically displays errors
  - trg > Trigger
    - Called by Script Triggers
    - Typically displays errors
    - Returns "False" if errors
    - Returns "True" if no error
  - sub > Subscript
    - Called as a subscript
    - Never called as top level 
    - Passes back results or errors in JSON format
    - May not display errors
    - Found in various Module subfolders (unlike other prefixes)
      - Export
      - Protected
      - Public
      - Private
      - Config
      - Dependencies
  - dpr > Deprecated
    - Should not be called by any NEW scripts
    - May still be called by EXISTING scripts
      - When modifying existing scripts try to replace any calls to deprecated scripts
      - Eventually replace deprecated scripts in everywhere
    - Can be any type previously
    - For example: "dpr: sub: set all fields v3"
  - (No Prefix) > Procedures
    - Called by Scripts Menu > Menu Items
    - They need to be human readable, so therefore no Prefix
    - Typically displays errors

[Back](Script_Folders_Module.md) - [Next](Custom_Functions.md)

[TOC](TOC.md)
