
## FX Framework Quick Start Guide

### Introduction 
The FX Framework elevates the development experience with the following critical functions:

- Easy installation into any number of FileMaker files as an Add-on
- Fully documented code that is ALWAYS in sync with functionality and easily called via parameters
- Predictable JSONObjects & JSONArrays for parameters, results, and returned errors to simplify data parsing and error handling
- Fully transactional data manipulation which can be rolled back if errors are encountered
	- If Order Items error out while entering a new Order for example, the whole transaction can be rolled back
- Errors returned with full call stack — from the subscript that encounted the error, up to the initial calling script
- Foolproof script version management with effortless deployment and rollbacks

These functions enable developers to focus more on developing the business logic, instead of having to rebuild commonly-needed scripts. The Framework provides (*in descending order of frequency*):

- Scripting
- Custom functions
- Tables & Relationships
- Layouts

### Installation Verification

To confirm the Add-on was installed correctly, check for the FX folder structure in the Script Workspace.

![](Screenshots/Script_Folders.png)

### Documentation Access

Documentation for **any** FX Framework script can be called with the parameter shown below:

```
Perform Script [Specified: From list; "sub: set all fields (fxp)" ; Parameter: JSONSetElement ( "{}" ; "fx_options" ; True ; JSONBoolean ) ]
```

Which will return the documentation as a JSONObject:

```
{
	"begin" : 
	{
		"allow_abort" : false,
		"capture_errors" : true
	},
	"end" : {},
	"error_handling" : 
	{
		"display" : false,
		"revert" : false
	},
	"parameters" : 
	{
		"paths" : 
		{
			"fields" : 
			{
				"description" : "Object of local fields to set.",
				"save_to_variable" : "$fields",
				"type" : "JSONObject",
				"variable_type" : "text"
			},
			"portal_name" : 
			{
				"description" : "name of the active portal we're setting fields in, using internally for recursion.",
				"save_to_variable" : "$portal_name",
				"type" : "JSONString",
				"variable_type" : "text"
			},
			"portals" : 
			{
				"description" : "Array of portal objects to set.",
				"save_to_variable" : "$portals",
				"type" : "JSONArray",
				"variable_type" : "text"
			}
		},
		"required_paths" : []
	},
	"script" : 
	{
		"description" : "Script to transactionally set fields. will also update related records in portals. capable of matching related rows based upon an id.",
		"id" : "63",
		"name" : "sub: set all fields (fxp) v1",
		"type" : "subscript"
	},
	"updates" : 
	[
		"created on 2022-12-28 by Kaz",
		"updated YYYY-MM-DD by DEVELOPER NAME: changed x, y, and z."
	]
}
```

NOTE >> the script uses the documentation for its parameters, so they will always be in sync.

### How to incorporate the Framework

