### Powershell - a powerful tool from Microsoft designed for task automation and configuration management
  - combines a command-line interface and a scripting language built on the .NET framework.

### Powershell Core - can run on mac and Linux

### an object represents an item with properties (characteristics) and methods (actions).
  - An object in PowerShell can contain file names, usernames or sizes as data (properties), and carry functions (methods) such as copying a file or stopping a process.

Command lets (cmdlets) - Cmdlets follow a consistent Verb-Noun naming convention. This structure makes it easy to understand what each cmdlet does. The Verb describes the action, and     the Noun specifies the object on which action is performed.
      outputs objects that you can inspect or pass to other cmdlets:

### Get-Command - will list all commands

Get-Command -CommandType "Function" - will use the -commandtype "Function" to filter out only specific property values (Function)  
          * commandtype is a property name  
Get-Help - provides detailed information about cmdlets, including usage, parameters, and examples.   
          * Get-Help New-Localuser -example   = will output ecamples for new-localuser  
Get-Alias - lists command names that correspond to regular CLI commands  
Find-Module - search for modules (collections of cmdlets) in online repositories like the PowerShell Gallery  
Get-Childitem - lists files and directories  
          * basically the same as "dir" or "ls"  
          * Get-Childitem -path Documents = will display the contents of the Documents directory, but not take you there
Set-Location -path ".\documents" - will go to that folder
  - cd can still be used to go back and forth, but within Powershell it's easier for others to understand Set-location (Powershell is used for writing scripts that do repetitive tasks)

New-Item - used to create a new file (you must identify the path where it will be created and what type of file)
  - New-Item -Path ".\captain\documents\wardrobe" Item-Type "Directory"
       - the directory wardrobe will be created
    
Remove-Item - used to remove directories and files (in a normal CLI, you use rmdir for directories and del for files)  
Copy-Item - used to copy  
Move-Item - used to move  
Get-Content - used to read and display the contents of a file (as in "type" in CLI)  

### Piping
  - In PowerShell, piping is even more powerful because it passes objects rather than just text. These objects carry not only the data but also the properties and methods that describe and interact with the data.  
        *  Get-ChildItem | Sort-Object Length = get a list of files in a directory and then sort them by size

Where-Object = will return only objects that meet criteria  
  - Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"  
        - will list only objects with a .txt extension  
        - "-eq" means "equal to"

Get-ChildItem | Where-Object -Property "Name" -like "ship*"  
    -like =  objects can also be filtered by selecting properties that match a specified pattern  

-ne: "not equal". This operator can be used to exclude objects from the results based on specified criteria.  
-gt: "greater than". This operator will filter only objects which exceed a specified value. It is important to note that this is a strict comparison, meaning that objects that are         equal to the specified value will be excluded from the results.  
-ge: "greater than or equal to". This is the non-strict version of the previous operator. A combination of -gt and -eq.  
-lt: "less than". Like its counterpart, "greater than", this is a strict operator. It will include only objects which are strictly below a certain value.  
-le: "less than or equal to". Just like its counterpart 
-ge, this is the non-strict version of the previous operator. A combination of -lt and -eq.  

Get-ChildItem | Select-Object Name,Length   
  Select-Object, is used to select specific properties from objects or limit the number of objects returned. It’s useful for refining the output to show only the details one needs.

Get-ChildItem | Sort-Object Length -Descending | Select-Object -First 1  
  - will sort the objects so that the largest length is first, and then only output the first item (which is the largest)

Select-string = This cmdlet searches for text patterns within files, similar to grep in Unix-based systems or findstr in Windows Command Prompt. It’s commonly used for finding           specific content within log files or documents.
      - Select-String -Path ".\captain-hat.txt" -Pattern "hat" 

