# Windows Fundamentals

- NTFS - New Technology File System
    - the newest journaling file system (older ones were FAT16/FAT32, HPFS, which are still used in usb devices, etc)
    - the file system can automatically repair folders/files on disk using information stored in a log file (not possible with FAT)
- User Account Control (UAC) - when an administrator logs into a system, it doesn't actually run with elevated permissions and instead will prompt you to
  confirm running a higher operation

### Ctrl+Shift+Esc - opens Task Manager (System Configuration)
 - also msconfig in the search (magnifying glass) tab

### Computer Management (compmgmt)
  - System Tools, Storage, and Services and Applications.
  - System Tools
         - Task Scheduler
            - can create tasks to run apps, scripts to run at any point and on repeat
         - Event Viewer
            - can view a record of events on the computer (logs, etc)

### System Information (msinfo32)
  - hardware, resources, components, etc
### Resource Monitor (resmon)
  - displays per process CPU, memory, network usage information
### Command Line Prompt (cmd)
  - ipconfig - will output current IP settings
## - /? - added after a command will output help manual for the specific command
  - ipconfig /? - will ouptput help manual

cls - clears the screen
ipconfig - outputs personal IP settings
netstat - shows current connections, listening ports with others
    - also good for troubleshooting connectivity issues
    - can be run with parameters like: netstat -a     or netstat -n
                        - -a displays all connections and listening ports
net - just displays some of the subcommands you can use
    - net help    - to access the help menu, the /? doesn't work for this....
        - then with a sub command use "net help user"
                - so the help goes in between

regedit - registry

Windows Defender Smartscreen - app and browser control to help stop phishing and malware website & apps

### Trusted Platform Model (TPM) - is a hardware chip on windows computers that helps with security functions.
  - it's a crypto-processor designed to carry out cryptographic operations

    Bitlocker - a windows security feature that locks drives, 
         - uses either a startup key (on a usb drive) or a password or PIN, in order to unlock the computer

    Volume Shadow Copy Service (VSS) - used to create a snapshot of a drive, but not an actual backup. just metadata&pointers
        - used so you can compare any changes that happen afterward
        - always written on the same drive (unless otherwise specified), so if the entire drive is lost, so is this backup

### Microsoft's Active Directory
 - Windows Domain - a group of users and computers under the administration of a given business
       - the main idea is to centralise the administration of common components of a Windows computer network in a single repository
   - Active Directory - the name for a single repository
   - Domain Controller - the server that runs the active directory services
   - the benefits of an active directory
         - centralised management
         - security principles can be configured from an active directory and applied to all
