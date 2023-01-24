# Custom Functions

## Purpose

- Avoid duplication of code
- Constantly refine specific calculations
- If error encountered return "?"
  - This is expected behavior for FileMaker's built in Custom Functions 

## Naming

- "Fx." prefix to differentiate from:
  - FileMakers included Custom Functions
  - Custom Functions that may have been added as part of a Plugin
    - Troi File plugin adds "TrFile_"... Custom Functions, like "TrFile_CopyFile"
- TitleCase so they support type-ahead in calculation window
  - "Fx.DoSomethingCool" can be entered by typing "fdsc"
    - "Fx.do_something_cool" cannot
- Standardized Format
  - Clearly linked to Modules
  - User can guess how they would be used by reading name alone
  - Format (each section separated by ".")
    - "Fx"
    - Module Name
    - subModule(s)
    - Function / Use
    - For example: "Fx.Email.SMTPSettings.Verify"
