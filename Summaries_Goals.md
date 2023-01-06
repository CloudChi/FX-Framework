# FX Frameworks Scripts Documentation

## Genesis

- FileMaker sucks at error handling


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
