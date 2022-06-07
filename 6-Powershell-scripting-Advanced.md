# Powershell scripting - Advanced

-  lazy parameters
  - parameters don't have to be defined
  - args can be stored into default variables
    - stored in $args variable
  - but it's better to use named parameters

- types of parameter
  - Switch parameter -> using switches
    - Get-ChildItem -Recurse
  - Parameter with Option
    - Get-ChildItem -Filter *.txt
  - Positional Parameter with Arguments
    - Get-ChildItem *.txt

- Can have multiple parameters
- can also have implicit names for parameters
- can explicitly put names for parameters
- alias names can be used for parameters
- switches can also be used
  - usually true or false
  - when present, it is true else it is false
  - does tab complete
- can accept values from pipeline to script, but 2 conditions must be met
  - must add [cmdletbinding()]
  - and ValuefromPipeline=$true
- Add get help for scripts
  - using comments to add extra info to scripts
  - how to use script
- Can be debugged
- write-verbose for adding verbose data
- write-debug for debugging data
- try-and-catch to handle errors


- Create your own modules
  - stores in Documents/Powershell/Modules
  - save modules as ".psm1" file
  - save the module in a folder with the same name 
    - CompInfo/CompInfo.psm1
  - this folder is stored in $env:psmodulepath
    - path with all the modules
  - core and powershell don't share the same module path
    - they behave differently
  - psmodulepath is a system environment variable
    - not inherited by core

- functions
  - can be called elsewhere in the code
  - can accept input and output data
  - can use $args or named parameters
  - there is default $input for all data sent to it

- Signing your script
  - certificate for code signing
  - set-executionpolicy allsigned
    - make sure all scripts are signed before running them