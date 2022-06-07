# Remote Powershell

- Run commands on multiple machines at the same time
- The goal of powershell is to provide centralized management on an entire IT environment
- RPC(Remote Procedure Call) was used for remote interaction
  - used many different ports
  - firewalls had to be disabled(bad for security)
- Windows is moving away from RPC and moving towards WinRM(windows implementation of WS-MAN)
  - WS-MAN is a standard protocol for remote management using HTTP and HTTPS
  - it doesn't use 80 or 443 because of clashing problems
  - it uses 5985 for HTTP and 5986 for HTTPS(when used)
  - HTTPS is encouraged for production

- WinRM has to be enable on client operating system but is on by default on servers
- Each command executed on a remote machine is its own session
  - sessions are not persisted between commands unless you explicitly set it up yourself
- Data is serialized into XML when sent back, they are deserialized back to objects in local session
  - the object is not preserved, it has been altered
  - it is computationally expensive
  - filter should be done as far left as possible(in the remote as possible )
- operation have to be done on the remote machine
  - you can't kill a process from your machine
  - because you only have a snapshot of the object
- Default of 32 machines at a time



## Sessions

- can have one to one(one command per session)
- or create a session and perform commands in it
- Sessions can be initiated on multiple machines
- You can import a module from a remote computer
  - but it will have a different naming type for the module
  - Manifest vs Script, cmdlet vs function
  - The command is running remotely not on your local
  - The result is then deserialized and returned to your local machine
  - can be useful for multiple machines
    - can be used to install different versions of a module on each remote(usually not possible)


## Compatibility
- using core and normal powershell commands
  - usually some commands exist in one and not the other
- creates a session to itself(localhost) and runs it like a remote import

## Alternate Endpoints
- Just enough Administration(JEA)
  - minimum privileges to get work done
  - create limited set of commands and features to be used


## Authentication
- you can't hop your credentials in your remote machine
  - using your credentials to access others services that need credentials from your remote
  - uses Kerberos by default
- In order to hop, use CredSSP
  - enable CredSSP in the remote and localhost
  - allow delegation of fresh credentials
- Kerberos resource based delegation can also be used for hopping authentication
- Certificate authentication can be used for SSL


- Powershell core embraces cross-platform
 

## Commands

- Invoke-Command
  - used for WinRM
- Measure-command
  - measure the time taken for a command to be executed

- & -> is the execution command parameter


## Resources
- Secrets of powershell remoting