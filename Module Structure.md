# FX Framework - Script Organization

## Folder Overview
Each FX Framework file can have up to 5 types of Script folders

  - File-level folders
    - Schedules folder 
    - Import folder
    - Trigger folder
    - Layouts
    - Regular Modules

  - Regular Module folders 
    - Buttons
    - Procedures
    - Triggers
    - Export
    - Public
    - Protected
    - Private
    - Dependencies
    - Config
    - Templates
    - Deprecated 

## Folder Detail

    - Schedules folder
      - Scripts which are called by the FileMaker Server
        - The Server has no way to filter scripts in a file, therefore this folder is on top to make finding these scripts easier on FileMaker Server   
    - Import folder
      - Scripts which call scripts outside of THIS file
    - Trigger folder
      - Scripts which are called by file-level Triggers and therefore have to be on the file level
        - OnFirstWindowOpen
        - OnLastWindowClose
        - OnWindowOpen
        - OnWindowClose
        - OnFileAVPlayerChange    
