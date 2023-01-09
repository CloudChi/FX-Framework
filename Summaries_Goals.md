# FX Frameworks Scripts Documentation

## Genesis

### FileMaker is a programming language that incorporates

  - Data layer back end
  - Business logic mid layer
  - UI/UX front end
 
### FileMaker can be set up to work on
 
  - Client app
  - Browser
  - Mobile device
  - API interface (allowing script calls and returning results)

### FileMaker Strengths
- Code element naming updates
  - For example, if you change the name of a field in a table it will propagate throughout the system
- Frictionless interaction between layers
  - Because of code element naming updates above, no need to, for example, rename a field in the UI or Business Logic layer if you change the name in the data layer
- Rapid development
  - Path from prototyping to deployment is very fast
- Flexibility of deployment method
  - Even within same code base, can have different configurations for different interfaces
    - For example, data entry screens for iOS devices alongside reporting screens visible on the web for remote sales staff 

### FileMaker Weaknesses
- Error handling and passing
  - Although errors can be trapped, there is no common way of exiting script upon an error and maintaining that error
  - Errors can be quickly lost, if not coded for specifically
  - Passing errors up through the script stack is not built in
- Variable data types
  - Variables can be cast as a type, but typing is not natively enforced
- Parameter / Result data types
  - Can be passed using JSON element types, but these types are not connected to internal FileMaker variable types 
- Code Documentation
  - Comments can be added to fields, scripts, custom functions and calculations, but cannot be extracted as documentation
  - Comments are not directly linked to code, so they can get out of sync unless manually maintained
- Code searching / treeview
  - FileMaker development environment does not support searching for code elements across codebase, nor support treeview branching
- Unit testing 
  - Unit Testing functions and methodologies are not natively present in FileMaker and have to be built and maintained separately

## Goals

- Modularity
  - Modules can be ripped out a replaced with minimal repointing necessary
  - Modules can be convertted to Add-Ons fairly easily
- Interchangeability / Portability 
  - Greatest strategic threat to an installed FileMaker solution is inability to update code without unintended consequences
  - Importing replacement modules will only require a few repoints in an expected location
  - Portability is a sliding scale with the FX Framework requiring minimal changes when ported
  - Two areas that require file/module specificity are:
    - table references
      - handled in the Framework by abstracting calls to fields and tables
    - Custom Functions
      -  handled by including module name in Custom Function name
- Fault-tolerant
  - If an FX Framework file or Module is missing, the system will be able to handle it and report any errors generated

## FX Framework System Design

- The FX Framework is a group of FileMaker files that have a backbone of:
  - Functional script organization
  - Extensive libraries of code
  - Complimentary Custom Functions

### Script Organization
- The Framework script organization uses a specific Script folder/subfolder structure.
  - Each Framework folder, called a Module, handles a specific group of tasks.
    - For example, the Layouts Module handles anything related to Layout navigation 
  - Certain Modules can be found in almost every file
    - Like the Layout Module for example
- Scripts within the Framework have a 3-letter prefix which determines **how** they should be called
  - Excluding scripts in ScriptMenu module which are user-facing
- Script stack will pass parameters down and results or errors up using a consistent JSONObject structure
-  Any top level script initiated by a user (Button, Trigger, Script Menu scripts) will all display the error to the user.

### Libraries of code
- The Framework contains multiple libraries for core coding activities
  - Navigating to layouts
  - Doing Finds
  - Creating new records
  - Setting fields
  - Sending emails 
  - Transactions for data entry
  - Displaying errors
  - Commenting and documenting code

### Libraries of Custom Functions
- Designed to simplify and support FX Framework methodologies
- JSON parsing/building functions for parameter building and script return parsing
- Error generating and handling functions
- 
