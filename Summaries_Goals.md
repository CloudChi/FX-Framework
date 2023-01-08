# FX Frameworks Scripts Documentation

## Genesis

- FileMaker sucks at error handling
  - Most FileMaker scripting practices do not support capturing all errors, maintaining the error state long enough to pass up to calling script
- FileMaker can use JSON for parameters and results, which supports variable data types, but has no native way of converting these JSON variable types to FileMaker data types
- FileMaker has no native method for documenting scripts
  - If there is documentation, there is no way of knowing if it is up-to-date
  - There is no way to access it without having access to read a script (unlike a "man" call to a UNIX funtion)
- FileMaker has no native method for searching through existing code for every place a certain layout or script is called
- FileMaker has no methodology for Unit Testing, so refactored code cannot easily be tested 


## Goals

1) Modularity
2) Interchangeability / Portability 
3) Fault-tolerant

## Summary

- The Framework is a group of FileMaker files that have a backbone of functional script organization, extensive libraries of code, and complimentary custom Functions.
- The Framework script organization uses a specific Script folder/subfolder structure.
  - Each Framework folder, called a Module, handles a specific group of tasks.
    - For example, the Layouts Module handles anything related to Layout navigation 
  - Certain Modules can be found in almost every file
    - Like the Layout Module for example
- Scripts within the Framework have a 3-letter prefix which determines **how** they should be called
  - Excluding scripts in ScriptMenu module which are user-facing
- Script stack will pass parameters down and results or errors up using a consistent JSONObject structure
-  Any top level script initiated by a user (Button, Trigger, Script Menu scripts) will all display the error to the user.
