# Powershell scripting

- Regions(just like sections) in scripting environment 
  - have nothing to do with the execution of the code
  - grouped together commands in section

- Signed Scripts
  - Get-ExecutionPolicy
  - Set-ExecutionPolicy
    - Remotesigned(default), Allsigned, Unrestricted
  - Manage what type of scripts can be run
  - must be elevated(as administrator)


- Script
  - ends with ".ps1" extension
  - you can't just execute a script file(by clicking or type in command line)
  - you have to use ".\<script-name>" or use full path

- Write-Output vs Write-Host
  - out writes to the pipeline
  - host and out don't do the same thing
  - The goal of powershell is to pass data along powershell objectflow engine(pipeline)
    - out writes to the pipeline
    - host sends it to the host not the pipeline
  - Avoid using Write-host
    - can do pretty-formatting

- Difference between ' and "
  - generally use single quotes
  - double quotes
    - for variable interpolation
    - string delimitation
    - for escape characters

- Backtick is for newline continuation(escapes newline)
  
- Prompting user
  - Read-Host -> try to avoid using this
  - -AsSecureString for security
    - don't display value on screen


- Script with mandatory input vs default input 
  - it prompts the user
- can ask for multiple inputs in array


- Get-Error or $Error variable
  -> shows last error
- Writing errors to variables
  - "-ErrorVariable <var_name>"

- Try-catch block
  - error handling
  - it catches a terminating error by default
  - Add "-ErrorAction Stop" to make your errors terminating for catch block to show error
    - There are different error actions -> Silentlycontinue
  - Add extra info to exception

- $ErrorActionPreference 
  - usually continue by default
  - for when you can't set ErrorAction flag
  - don't just change it, put it back
  - for stopping an error
  - use finally block

- CmdletBinding in script
  - add verbose and debug flags to script
  - for debugging your code
  - add extra output for your code
  - add write-verbose and write-debug in your code