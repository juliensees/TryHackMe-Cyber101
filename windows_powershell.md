### Powershell - a powerful tool from Microsoft designed for task automation and configuration management
  - combines a command-line interface and a scripting language built on the .NET framework.

### Powershell Core - can run on mac and Linux

### an object represents an item with properties (characteristics) and methods (actions).
  - An object in PowerShell can contain file names, usernames or sizes as data (properties), and carry functions (methods) such as copying a file or stopping a process.

Command lets (cmdlets) - Cmdlets follow a consistent Verb-Noun naming convention. This structure makes it easy to understand what each cmdlet does. The Verb describes the action, and     the Noun specifies the object on which action is performed.
      outputs objects that you can inspect or pass to other cmdlets:

### Get-Command - will list all commands

Get-Command -CommandType "Function" - will use the -commandtype "Function" to filter out only specific property values (Function)
        - commandtype is a property name
Get-Help - provides detailed information about cmdlets, including usage, parameters, and examples. 
  Get-Help New-Localuser -example   = will output ecamples for new-localuser
Get-Alias - lists command names that correspond to regular CLI commands
Find-Module - search for modules (collections of cmdlets) in online repositories like the PowerShell Gallery
