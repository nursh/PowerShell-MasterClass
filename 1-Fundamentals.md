# Fundamentals

- Before PowerShell was the command prompt
  - it had built-in commands
  - dir.exe does not exist
  - ipconfig.exe exists because it is external
  - Batch files for performing tasks
  - Piping of commands was limited
  - passing text strings

- PowerShell - regular Desktop
  - solves a lot of the problems
  - execute live commands and create powerful scripts
  - built using .NET framework on .NET Core
  - outputs an object on commands
  - Uses a common-syntax, a verb-noun pair command naming scheme
    - eg. Get-Process, New-Object
  - ease of use for commandlets
  - focused on least cognitive distance
  - Remote management is enabled by default
  - no new innovations


- PowerShell (ISE) -> Integrated Scripting Environment
  - no future development
  - replaced by VSCode extension
  - useful for scripting desktop command line(powershell not core)
  - requires Windows Presentation Framework
    - does not work on server
    - takes longer to start
- PowerShell Core - pwsh.exe in Task manager
  - original part of nano server(thin version of windows)
  - small version and run on multiple platforms
  - not part of windows right now
  - new features will be on here

- dir works in Powershell core
  - but the switches don't work
  - It is an alias for Get-Item

- Things that work from command-prompt work as aliases
  - the intrinsic commands -> cd, ls, dir etc.
  - don't use aliases in scripts

- PowerShell Modules
  - contain pwsh functionalities such as cmdlets
  - can be installed and updated


## Commands

- Get Version of shell
  - Get-Host(careful with this on VS-Code)
  - $PSVersionTable
  - $PSVersionTable.psversion -> attribute on psversiontable
- Get aliases for commands
  - Get-Alias -> show all aliases
  - Get-Alias <alias> -> show what the alias maps to
- See all modules
  - Get-Module -> show all modules available
- Help
  - Get-Help <cmdlet>
  - get-command -noun <process> -> show what I can do to a noun
