# FX Frameworks Documentation

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
- Code searching / tree view
  - FileMaker development environment does not support searching for code elements across codebase, nor support tree view branching
- Unit testing 
  - Unit Testing functions and methodologies are not natively present in FileMaker and have to be built and maintained separately
- Updating and patching deployed systems
  - Most FileMaker systems contain too many dependencies to rapidly update without breaking a ton of connections


## Goals

The overall goal of the FX Framework is to build on FileMaker's strengths and lessen or eliminate the weaknesses.

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

### JSON Parameters / Data Structures
  - JSON parsing, typing, constructing are all natively supported in new versions of FileMaker
    - Previously to this, no consistently supported options
      - XML
        - Can function similarly to JSON
        - No native functions
        - Is data typing not supported???  
        - More actual text to express the same data as JSON, therefore less human readable
      - Global Variables
        - Prevented excessive creation of fields
        - Might not be assigned / cleared correctly
        - Cluttered up Data Viewer when debugging
    - JSON is default standard for web APIs
      - this increases likelihood of any given developer being familiar

### Error-Handling
  - If Errors are consistent and informative, it leads to better code, because users can avoid common mistakes
  - Correct way is hard, wrong way is easy
  - Lower tolerance for wrong

### Version / Updating
  - Standard code very hard to update and experiment with versioning
  - If you can update code without breaking things, you can iterate over and over
  - Coding with any Framework is a balance between freedom and advantages
    - What do you give up versus what do you get
    - For example, if you have to provide parameters in JSON, that is a limitation, but the advantage is a subscript might have a JSON parsing routine to parse out parameters easily

### Dependencies
  - Managing Dependencies
  - Predictable
  - Possible ???
  - Scalable
  - Concept of exponential growth of dependencies
    - How quickly dependencies grow
    - Identify then fix
    - Limited breakage
    - Prevent resolving incorrectly
      - FileMaker Themes and Styles are example of this ???


## FX Framework System Design

- The FX Framework is a system of FileMaker practices that provide stable functionality for developers to leverage. 
- The framework is contains a group of Modules which have a backbone of:
  - Functional script organization and naming
  - Extensive libraries of code
  - Complimentary Custom Functions

### Script Organization / Naming
- The Framework uses Modules which is a method of script organization using a specific script folder/subfolder structure.
  - Modules provide a specific set of tools and functionality to the developer
    - For example, the Layouts Module handles anything related to Layout navigation 
  - Certain Modules can be found in almost every file
    - Like the Triggers Module for example
  - Modules contain subfolders which correspond to organizational paradigms
    - Modules typically contain subfolders one level deep
      - Except the Layouts Module which itself contains Layout Modules for each layout in the file
- Scripts within every Module have a 3-letter prefix which determines **how** they should be called
  - Excluding scripts in ScriptMenu module which are user-facing
  - Script prefixes meaning:
    - btn > Button
    - trg > Trigger
    - sub > Subscript 
    - dpr > Deprecated (is this true?)
    - (BLANK) > Scripts Menu (since they need to be human readable and not too many words)
- The script call stack will pass parameters down and results or errors up using consistent JSON structures
-  Any top level script initiated by a user (Button, Trigger, Script Menu scripts) will all display any returned error to the user.

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
- As much as practicable, code that can be centralized to one location, is centralized.
  - This makes it simpler to debug issues, because there are fewer places to check. 

### Libraries of Custom Functions
- Custom Functions in the FX Framework have a specify naming convention:
  - Broad Functionality
  - Module (if part of a module)
  - Specific task 
- Designed to simplify and support FX Framework methodologies. For example:
  - JSON parsing/building functions for parameter building and script return parsing
  - Error generating and handling functions
- Since Custom Functions exist on the file level, any Custom Function associated with a specify module will be named accordingly
