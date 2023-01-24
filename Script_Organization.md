# Script Organization

- All scripts are responsible for handling and passing back:
  - Any errors they encounter
  - Any results they generate
- All Scripts use JSONObjects or JSONArrays to:
  - Pass parameters down
  - Pass results back up
  - Or pass any errors up
- Scripts are divided into two basic types:
  - Subscripts
    - Will NOT display results or errors to the user
  - Top level scripts 
    - WILL display any returned result or error to the user
    - These include the following script types:
      - Button
      - Trigger
      - Script Menu
