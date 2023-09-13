# FX Framework Reference

## TOC

- [Genesis](#Genesis)
- [Introduction](##Introduction)
  - [Error Trapping and Returning](#Error-Trapping-Returning)
  - [Versions and Updating](#Versions-Updating)
  - [Dependencies](#Dependencies)
  - [Modular Code](#Modular-Code)
- [Script Functions and Types](#Script-Functions-And-Types)
- [Script Folders - Non-Module](#Script-Folders-Non-Module)
- [Script Folders - Module](#Script-Folders-Module)
- [Script Naming](#Script-Naming)
- [Custom Functions](#Custom-Functions)
- [Why use JSON?](#Why-JSON)

## Genesis

### FileMaker is a full development platform consisting of:

- UI front-end accessible via: client app, mobile app, or a web browser
- Business logic mid-layer accessible via: UI front-end or Data API
- Database back-end accessible via: mid-layer, Data API, or ODBC
- Debugging capabilities
- Ability to serve files

#### FileMaker Strengths
- Code element naming updates will automatically propagate throughout the system
  - For example, if you change the name of a field in a table it will be updated wherever it appears 
- Frictionless interaction between layers
  - Because of code element naming updates above, no need to, for example, rename a field in the UI or Business Logic layer if you change the name in the data layer
- Rapid development
  - Path from prototyping to deployment is very fast
- Flexibility of deployment method
  - Even within same code base, can have different configurations for different interfaces
    - For example, data entry screens for iOS devices alongside reporting screens visible on the web for remote sales staff 

#### FileMaker Weaknesses
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
- Code searching / tree view
  - FileMaker development environment does not support searching for code elements across codebase, nor support tree view branching
- Unit testing 
  - Unit Testing functions and methodologies are not natively present in FileMaker and have to be built and maintained separately
- Updating and patching deployed systems
  - Most FileMaker systems contain too many dependencies to rapidly update without breaking a ton of connections


## Goals

The overall goal of the FX Framework is to build on FileMaker's strengths and lessen or eliminate the weaknesses.

[Back](#toc)

[Next](###modularity)

### Modularity
  - Modules can be removed and replaced/updated with minimal breakage that will be contained in very specific, easy-to-fix areas
  - Modules can be converted to Add-Ons fairly easily
    - Which will further eliminate many of the remaining breakage points

### Interchangeability / Portability 
  - Greatest strategic threat to an installed FileMaker solution is inability to update code without unintended consequences
  - Importing replacement modules will only require a few repoints in an expected location
  - Portability is a sliding scale with the FX Framework requiring minimal changes when ported

### Fault-tolerant
  - If an FX Framework Module is missing, the system will be able to:
    - Report a meaningful error about the missing module
    - Continue to function with the missing module, even in a limited way 
      - For example, if a jet plane loses an engine, the pilot is alerted to the situation, but more importantly the plane can continue to fly, albeit in a limited and temporary way.


## Philosophies / Principles

### Error Trapping Returning
### Versions Updating
### Dependencies
### Modular Code
## Script Functions And Types
## Script Folders Non Module
## Script Folders Module
## Script Naming
## Custom Functions
## Why JSON
[TOP](##FX-Framework-Reference)
