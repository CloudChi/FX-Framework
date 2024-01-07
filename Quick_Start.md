
### FX Framework

#### What is it?

FX Framework is a FileMaker Add-on scripting structure and methodology which is transactional, extensible, and fully error-trapped. It contains a library of commonly-needed functions which allow the developer to concentrate on building out the business logic, instead of rewriting an error-trapping field setter for each file (for example).

#### Why use it?

FX Framework has many advantages over the common FileMaker scripting methodologies:
- Scripts are easily versioned and can also be rolled back to earlier versions easily
- Results are returned in a predictable JSONObject format
- Errors are consistently trapped and returned in a predictable JSONObject format
	- Any trapped errors include the full error stack — from the calling script all the way down to the subscript that encountered the error.
- Data editing functions are fully transactional and able to be rolled back if they encounter an error
-  // ??? Any existing FX Framework Add-on can easily be copied from one file to another ???
- The FX Framework Add-on can be installed on any number of files in a solution.
#### How do I use it?

The FX Framework can be added to any new or existing FileMaker file as an Add-on, which will install some clearly labelled tables and relationships, layouts, custom functions and scripting.

Instructions:
- Open the FX Framework file and run the Make Add-on  script which will ask from which window to create the app (type for example, "Fx Library v3")  [Make Add-on](/Users/marstonchickering/Desktop/FX - Make Add-on.png)
- [[]]
- Choose to replace UUID, and confirm it. %% (Is this correct Kaz?) %%
- Open the destination file
- Enter Layout Mode
- Enable the left pane and click the Add-ons tab
- Click the "+" button 