# Script Organization

- All scripts are responsible for capturing and returning:
  - Any errors they encounter
  - Any results they generate
- All Scripts use JSONObjects to:
  - Accept parameters
  - Return results, or any errors
  - Except Trigger scripts – which return True or False (to Proceed with or Cancel calling trigger, respectively)
- Scripts are divided into two basic types:
  - Subscripts
    - Will NOT display results or errors to the user
  - Non-Subscripts 
    - WILL display any returned result or error to the user
    - These include the following script types:
      - Button
      - Trigger
      - Script Menu
