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

Get-ComputerInfo - cmdlet retrieves comprehensive system information, including operating system information, hardware specifications, BIOS details, and more. 

Get-LocalUser - lists all the local user accounts on the system

Get-NetIPConfiguration = provides detailed information about the network interfaces on the system, including IP addresses, DNS servers, and gateway configurations.
  - same as ipconfig in CLI

Get-NetIPAddress = cmdlet will show details for all IP addresses configured on the system, including those that are not currently active.

Get-Process = provides a detailed view of all currently running processes, including CPU and memory usage, making it a powerful tool for monitoring and troubleshooting.

Get-Service = allows the retrieval of information about the status of services on the machine, such as which services are running, stopped, or paused. It is used extensively in troubleshooting by system administrators, but also by forensics analysts hunting for anomalous services installed on the system.

Get-NetTCPConnection = displays current TCP connections, giving insights into both local and remote endpoints. This cmdlet is particularly handy during an incident response or malware analysis task, as it can uncover hidden backdoors or established connections towards an attacker-controlled server.

Get-FileHash = generates file hashes, which is particularly valuable in incident response, threat hunting, and malware analysis, as it helps verify file integrity and detect potential tampering.

### Scripting is the process of writing and executing a series of commands contained in a text file, known as a script, to automate tasks that one would generally perform manually in a shell, like PowerShell.

Invoke-Command = is essential for executing commands on remote systems, making it fundamental for system administrators, security engineers and penetration testers.
  What is the syntax to execute the command Get-Service on a remote computer named "RoyalFortune"? Assume you don't need to provide credentials to establish the connection. [for the sake of this question, avoid the use of quotes (" or ') in your answer]  
    Invoke-Command -ComputerName RoyalFortune -ScriptBlock { Get-Service }  
