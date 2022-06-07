# Connecting Commands Together and Mastering Objects

- Powershell can be terminated with semi-colon
  - but used for multiple commands on a single line
  - don't pipe multiple commands
  - eg. <command_1>;<command_2>


- keeping objects as long as you can(for pipelining)
  - Powershell returns object not strings
  - to see object properties, methods
    - <command> | get-member
  - {$_} -> each object in the pipeline
  - filter as far left as you can to reduce computation

- Some commands return strings
- Variables start with '$'
  - e.g. $var1 



## Pipeline

- can get type of object using:
  - <object>.getType().name
  - <var>.getType().name
- modifying object for input and outputs to other commands
  - using select-object command
  - if the input to another command is expecting some property that the output of the previous command doesn't provide
    - you can add the property using select-object and some manipulation
    - eg. get-process | select-object -property name, @{name='procid';expression={$_id}}
      - add procid property to the Process object in the pipeline and get it ready for the next command
- The end of a pipeline is typically sent to a screen
- Various Out verb cmdlets
  - Out-Printer
  - Out-Null -> to suppress
  - Out-GridView -> GUI
  - Out-Default which directs to Out-Host


- Redirect to file
  - <command> > <filename>
  - eg. get-process > procs.txt
  - which is an alias for "get-process | out-file procs.txt"

- Exporting to other formats
  - <command> | Format-Table/Format-List
  - or to files
    - <command> | Export-csv <path>
    - <command> | Export-clixml <path>

- Import from other formats
  - but it comes back as a custom object
  - import-clixml(returns a deserialized object) or import-csv
  - has no live link to the object

- Limit Objects
- get-eventlog -> not in core but in normal powershell
- Try to filter within the command itself if possible, else use select command
  - This makes it more efficient
- Compare objects
  - compare-object -> compare two sets of data
  - using -property <name> flag -> to compare properties

- Advanced output
  - HTML
  - JSON
  - CSV
  - XML
  - Secure String
  - could output to a file 

- "-PassThru" flags -> pass the object through the pipeline
- "-confirm" and "-whatif" flags
  - added to other commands
  - confirm will prompt before doing a command
  - whatif will show what the commands will do without doing it
- Every cmdlet has an impact level
  - if the impact-level is equal or higher than the confirmation preference setting user will be prompted for confirmation
    - $confirmpreference variable
  - Setting the confirm flag kills the process if you want
- "$_" -> represents current pipeline object
  - can access the property of a piped object
  - alias is $psitem
  - or skip the whole curly braces
- "?" is just an alias for where object


## Commands

- clip -> put in clip board
- measure-object -> count number of objects returned
- get-help <command> -full -> checks the command input and output

