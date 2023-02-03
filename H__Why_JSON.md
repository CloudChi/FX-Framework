# Why use JSON for Parameters, Results, and Data Structures


## JSON
- JSON setting, getting, and typing are all natively supported in FileMaker
  - Previously to this, no consistently supported options
   ![JSON_Functionst](Screenshot_JSON_Functions.png)
- JSON is default standard for web APIs
  - Broader range of developers are familiar
  - Easier to call and receive data from APIs external to FileMaker
- JSON more human readable and fewer characters (64 characters)
```
{
	"oldMasterStatus" : "Inactive",
	"old_master_id" : "123456"
}
```

## XML
- Can function similarly to JSON
- No native functions
- XML less human readable and more characters (108 characters)
```
"<xml>"
 	"<old_master_id>Inactive</old_master_id>"
 	"<oldMasterStatus>123456</oldMasterStatus>"
 "</xml>"
```

## Global Variables
- Pro: Prevented excessive creation of fields
- Might not be assigned / cleared correctly
- Cluttered up Data Viewer when debugging
- Unless strict naming convention, origin might be unclear
  - $$Type is unclear
  - $$Type_Customer is more clear 
![Global Variables](Screenshot_GlobalVariables.png)

## Let function
- Variables only exist inside function
- No real way to step through calculation and see data 

## Global Fields
- Data fields get intermingled with business function fields
- No native way to represent data structures without duplicating data table with table of global fields
- Realistically limited to relationship starting points or simple data entry start screens
