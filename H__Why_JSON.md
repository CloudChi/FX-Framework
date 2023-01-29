# Why use JSON for Parameters, Results and data structures

## JSON Parameters / Data Structures
  - JSON parsing, typing, constructing are all natively supported in new versions of FileMaker
    - Previously to this, no consistently supported options
      - XML
        - Can function similarly to JSON
        - No native functions
        - More actual text to express the same data as JSON, therefore less human readable
      - Global Variables
        - Prevented excessive creation of fields
        - Might not be assigned / cleared correctly
        - Cluttered up Data Viewer when debugging
    - JSON is default standard for web APIs
      - this increases likelihood of any given developer being familiar
