
## FX Framework Add-on

#### Overview 
The FX Framework is a FileMaker Add-on which provides developers with a scripting structure that supports the following critical functions for any coding environment:

- stacked transactions
- script version testing and simple 
- full error trapping / returning

These strengths enable developers to focus on their business logic, rather than constantly having to rebuilding common scripts. The Framework Add-on only installs:

- Tables
- Relationships
- Layouts
- Custom Functions
- Scripting

#### Benefits

FX Framework has many advantages over common FileMaker scripting structures and methodologies:
- The FX Framework is installed as an Add-on for every file in a new or existing solution.
- Data editing functions are fully transactional and able to be rolled back if they encounter any errors
- Results are returned in a predictable JSONObject format.
- Errors are consistently trapped and returned in a predictable JSONObject format.
	- Any trapped errors include the full error stack — from the calling script all the way down to the subscript that encountered the error.
- Scripts are easily versioned and can also be rolled back if testing proves the new version is not working as expected.

#### Was the Add-on installed?

In the Script Workspace, look for an FX folder with many subfolders to confirm that the Add-on was installed successfully.

![](Screenshots/Script_Folders.png)

#### RTFM!

The scripts in the FX Framework are fully self-documenting by calling any of them with this parameter:

```
JSONSetElement ( "{}" ; "fx_options" ; True ; JSONBoolean ) 
```

For example:

```
Perform Script [Specified: From list; "sub: simple email (fxp)" ; Parameter: JSONSetElement ( "{}" ; "fx_options" ; True ; JSONBoolean ) ]
```

Which will produce a documentation JSONObject:

```
{
	"begin" : {},
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
			"attachment_path" : 
			{
				"description" : "path to the item to attach",
				"save_to_variable" : "$attachment_path",
				"type" : "JSONString",
				"variable_type" : "text"
			},
			"bcc" : 
			{
				"description" : "blind carbon copy recipients. can be array of strings",
				"save_to_variable" : "$bcc",
				"type" : [ "JSONString", "JSONArray" ],
				"variable_type" : "text"
			},
			"cc" : 
			{
				"description" : "carbon copy recipients. can be array of strings",
				"save_to_variable" : "$cc",
				"type" : [ "JSONString", "JSONArray" ],
				"variable_type" : "text"
			},
			"message" : 
			{
				"description" : "text of the message to email.",
				"save_to_variable" : "$message",
				"type" : "JSONString",
				"variable_type" : "text"
			},
			"smtp_settings" : 
			{
				"custom_type" : "{{$smtp_definition}}",
				"description" : "smtp settings",
				"save_to_variable" : "$smtp_settings",
				"type" : [ "JSONString", "JSONObject" ],
				"variable_type" : "text"
			},
			"subject" : 
			{
				"description" : "message subject.",
				"save_to_variable" : "$subject",
				"type" : "JSONString",
				"variable_type" : "text"
			},
			"to" : 
			{
				"description" : "recipients. can be array of strings",
				"save_to_variable" : "$to",
				"type" : [ "JSONString", "JSONArray" ],
				"variable_type" : "text"
			}
		},
		"required_paths" : [ "message", "subject", "to" ]
	},
	"script" : 
	{
		"description" : "simple email sending script. sends text over smtp. cannot send HTML emails.",
		"id" : "59",
		"name" : "sub: simple email (fxp) v1",
		"type" : "subscript"
	},
	"updates" : 
	[
		"created on 2022-12-28 By Kaz",
		"updated 2022-12-27 updated to use self-documenting framework."
	]
}
```

#### How to incorporate the Framework

