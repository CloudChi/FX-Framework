# FX-documentation

## Summary

The Framework system is organized into Modules which handle specific tasks or areas of tasks. 

## Module Structure

1. Modules are folders within the Script Manager. 
2. Modules can contain sub-Modules, but only one level deep.
3. Modules contain Structure subfolders, but only one level deep.
4. Structure subfolders are in no particular order within the Module folder.
  1. Not all Modules will have all the Structure subfolder types, which are only added as needed.
5. Modules are transferable between files with minimal connections required.
6, Modules can be addressed by other Modules and they can address other Modules.
7. Module scripts use consistently structured JSON for Parameters and Results.
8. Module scripts can receive errors (in JSON format) from called subscripts.
9. All Module scripts pass errors up to calling scripts, except scripts in the Button, Procedures or Triggers Structure subfolders.
