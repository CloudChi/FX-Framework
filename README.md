# FX-documentation

## Summary

The Framework system is organized into Modules which handle specific tasks or areas of tasks. 

## Module Structure

1. Modules are folders within the Script Manager. 
2. Modules can contain sub-Modules, but only one level deep.
3. Modules contain Structure subfolders, but only one level deep.
4. Structure subfolders are in no particular order within the Module folder.
Not all Modules will have all the Structure subfolder types, which are only added as needed.  
5. Modules are transferable between files with minimal connections required.
6, Modules can be addressed by other Modules and they can address other Modules.
7. Module scripts use consistently structured JSON for Parameters and Results.
8. Module scripts can receive errors (in JSON format) from called subscripts.
9. All Module scripts pass errors up to calling scripts, except scripts in the Button, Procedures or Triggers Structure subfolders.


## MODULE TYPES

A Module in a file can be one of 3 types:

Schedules (first Module in file)
Import (second Module in file)
Regular Modules (no particular order in file)
Layout Module


Schedules
Scripts in this Module do not contain logic
Contain no subfolders
This Module contains any script that will be called by the script scheduler within FileMaker Server which has no way to filter or sort scripts. Putting the Module on top just makes it easier to find the scripts needed.
Scripts in this Module can only call scripts in the Public subfolder of any Regular Modules within the same file.


Import
Scripts in this Module do not contain logic
Contain no subfolders
Scripts in this Module can only call scripts in an External file's Regular Module's External subfolder.


Structure subfolder types (in Regular Modules):

Buttons
Procedures
Triggers
Export
Public
Protected
Private
Dependencies
Config
Templates

Scripts in Modules and Structure subfolders all have prefixes that match their purpose (just a guess)

Modules
Schedules - sch
Import - imp
Regular Modules - (no prefix, because all scripts within Structure subfolders listed below)

Structure subfolders
Buttons - btn
Procedures - ???
Triggers - trg
Export - exp
Public - pub
Protected - pro
Private - pri
Dependencies - dep
Config - cfg
Templates - tem


Buttons
Scripts in this subfolder do not contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts handle any error they encounter and display it to the user.
Scripts in this subfolder are the ONLY scripts that a button on the layout should call.

Procedures
Scripts in this subfolder do not contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts handle any error they encounter and display it to the user.
Scripts in this subfolder are the ONLY scripts that a non-button procedure should call. For example, Menu Items in a Custom Menu.


Triggers
Scripts in this subfolder can contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts handle any error they encounter and display it to the user.
Script Trigger should ONLY call scripts in this subfolder.
Scripts in this subfolder can be versioned (independently of the Private scripts' versioning)
Scripts return "False" if an error occurred (and maybe set an $ERROR global variable?)
Scripts return JSONObject if they succeed

Export
Scripts in this subfolder do not contain logic
Scripts call scripts within this Module's Public or Protected subfolders.
Scripts in this Module can only be called by scripts in an External file's Import Module

Public
Scripts in this subfolder do not contain logic
Contains any script that is addressable from INSIDE or OUTSIDE the Module
Scripts within this subfolder call specifically-versioned scripts within the Private subfolder

Protected
Scripts in this subfolder do not contain logic
Contains any script that is addressable from INSIDE the Module
Scripts within this subfolder call specifically-versioned scripts within the Private subfolder
Typically a script will start as Protected, and will get promoted to the Public subfolder if access to it is needed outside the Module.

Private 
Scripts in this folder can contain logic
These scripts do the majority of the work
Scripts are versioned as changes are needed
Versioning allows developers to test new code and revert to old code by just calling a newer or older version from scripts within the Public or Protected subfolders
Any script in this subfolder that needs to reference a script within this Module calls a Protected script
Any script in this subfolder that needs to reference a script outside this Module calls a script in the Dependencies subfolder which calls an external script using that Module's Public scripts
The scripts in this subfolder should ONLY be addressed by scripts in this Module's Public and Protected subfolders

Dependencies
Scripts in this subfolder do not contain logic
The scripts in this subfolder ONLY call scripts in another Module's Public subfolder
The advantage to this, is if you copy this Module from one file to another, you only have to repoint these scripts.

Config
Scripts/Modules in this subfolder can contain logic
Can contain consumer-coded sub-Modules
Can contain simple scripts that only return a JSONObject of hardcoded values.
Scripts or Modules in this folder can be modified by consumers (not just Framework developers)

Templates
Scripts in this subfolder are specific to this module
Scripts in this subfolder can also work in conjunction with scripts in Config folder
Commonly, there is a Protected style script that calls additional versioned Private scripts
<<.  Should we have Protected and Private folder contained within?   >>
