# Custom Functions

## Purpose

- Avoid duplication of code
- Constantly refine specific calculations
- If error occurs:
  - Currently returns error(s) as Array of Strings
    - Additional Custom Functions can parse to Error JSONObject 
  - In the future, may return "?"
    - This is expected behavior for FileMaker's built in Functions 

## Naming

- "Fx." prefix to differentiate from:
  - FileMakers included Functions
  - Plugin Functions
    - Troi File plugin adds "TrFile_" Functions, like "TrFile_CopyFile"
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
    - For example: "Fx.Email.Smtp.Verify"
  - When moving a module from one file to another
    - Move any Custom Funtion that starts with "Fx.Module..."
    - For example if moving the "DoSomethingCool" Module
      - Also move the Custom Functions that start with "Fx.DoSomethingCool..."
