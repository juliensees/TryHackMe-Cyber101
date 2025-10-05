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

   Active Directory Domain Service (ADDS) - a catalogue that holds all the objects for everything: users, groups, machines, printers, shares, etc.
   
- ### Active Directory Users and Computers - used to configure AD's

   Security Principle - an object that can be assigned privileges over resources on the network (like files and printers)

   ### Users - one of the most common security principles
    - People - users will generally represent persons in your organisation that need to access the network, like employees.
    - Services - you can also define users to be used by services like IIS or MSSQL. Every single service requires a user to                 run, but service users are different from regular users as they will only have the privileges needed to run their                     specific service.
   ### Machines - another type of object within Active Directory that is also considered a security principal
    -  for every computer that joins the Active Directory domain, a machine object will be created and assigned an account just         as any regular user. This account has somewhat limited rights within the domain itself.

    - The machine accounts themselves are local administrators on the assigned computer, they are generally not supposed to be             accessed by anyone except the computer itself, but as with any other account, if you have the password, you can use it to             log in.
        - Machine Account passwords are automatically rotated out and are generally comprised of 120 random characters.
        - Machine account name is always followed by the $ sign, so DC01$ means it is a machine account
          
### Groups - also security principals, and assigns privileges to everyone in the group (users or machines or other groups)
   -
      Domain Admins: Users of this group have administrative privileges over the entire domain. By default, they can administer             any computer on the domain, including the DCs.
      Server Operators:	Users in this group can administer Domain Controllers. They cannot change any administrative group                 memberships.
      Backup Operators:	Users in this group are allowed to access any file, ignoring their permissions. They are used to perform             backups of data on computers.
      Account Operators:	Users in this group can create or modify other accounts in the domain.
      Domain Users:	Includes all existing user accounts in the domain.
      Domain Computers:	Includes all existing computers in the domain.
      Domain Controllers: Includes all existing DCs on the domain.

   Organizational Units (OU) - container objects that allow you to classify users and machines
       - sort of like a folder, but only within the Active Directory and used to organize objects, not files
       - can reset passwords within OU objects
       - a user can only be in one OU at a time
   
   Default Containers that come with Windows:
        Builtin: Contains default groups available to any Windows host.
        Computers: Any machine joining the network will be put here by default. You can move them if needed.
        Domain Controllers: Default OU that contains the DCs in your network.
        Users: Default users and groups that apply to a domain-wide context.
        Managed Service Accounts: Holds accounts used by services in your Windows domain.

   OU's vs Groups
       OUs - used for applying policies to users and computers, which include specific configurations that pertain to sets of                 users depending on their particular role in the enterprise. Remember, a user can only be a member of a single OU at a             time, as it wouldn't make sense to try to apply two different sets of policies to a single user.
       Security Groups - are used to grant permissions over resources. For example, you will use groups if you want to allow some                 users to access a shared folder or network printer. A user can be a part of many groups, which is needed to grant                     access to multiple resources.

### TO DELETE OU's - Must go to "View" and "Advanced Features" , and then go to properties for specific OU to then deselect the safety feature because it is purposefully made difficult to accidentally delete things

Delegation - used to give specific users control over OU's, so you don't need a Domain Admin to step in

By default, all the machines that join a domain (except for the DCs) will be put in the container called "Computers".

Group Policy Objects (GPO's) - a collection of settings that can be applied to OUs. GPOs can contain policies aimed at either         users or computers, allowing you to set a baseline on specific machines and identities.
### Group Policy Management Tool - used to configure GPO's
 - Security Filtering - used to only apply to specific users/groups (Authenticated Users is default)
 - Settings Tab - gives full breakdown of configurations
       - must separately specify computer and user configurations within each GPO
   To change password length minimum - "edit"
       - Computer Configurations -> Policies -> Windows Setting -> Security Settings -> Account Policies -> Password Policy

    GPO Distribution - distributed to the network via a network share called SYSVOL, which is stored in the Default Container
       - All users in a domain should typically have access to this share over the network to sync their GPOs periodically. The             SYSVOL share points by default to the C:\Windows\SYSVOL\sysvol\ directory on each of the DCs in our network.
            - Once a change has been made to any GPOs, it might take up to 2 hours for computers to catch up.
               - Can force a computer to update by using: C:\> gpupdate /force

### Domain Controllers
 - all credentials are stored here
 - when asking to authenticate credentials, the domain controller is used to verify it is correct using a protocol
       - Kerberos is the newer protocol that sends an authentication ticket back
           - NetNTLM is the legacy model that still works, in case people are using older windows models

   Key Distributing Center (KDC) - a service installed on the domain controller that distributes kerberos tickets
       - creates and sends back a Ticket Granting Ticket (TGT), so the user can use it for other services after this initial authentication, and also gives a Session Key
           - this is in return for the username and a timestamp encrypted using a key derived from their password

   ### the encrypted TGT includes a copy of the Session Key as part of its contents, and the KDC has no need to store the Session Key as it can recover a copy by decrypting the TGT if needed.

   When a user wants to connect to a service on the network like a share, website or database, they will use their TGT to ask the KDC for a Ticket Granting Service (TGS)
       - To request a TGS, the user will send their username and a timestamp encrypted using the Session Key, along with the TGT and a Service Principal Name (SPN)
       - As a result, the KDC will send us a TGS along with a Service Session Key, which we will need to authenticate to the service we want to access. The TGS is encrypted using a key derived from the Service Owner Hash. The Service Owner is the user or machine account that the service runs under. The TGS contains a copy of the Service Session Key on its encrypted contents so that the Service Owner can access it by decrypting the TGS.
           - The TGS can then be sent to the desired service to authenticate and establish a connection. The service will use its configured account's password hash to decrypt the TGS and validate the Service Session Key.

   Service Principal Name (SPN) - indicates the service and server name we intend to access.
   Ticket Granting Service (TGS) - tickets that allow connection only to the specific service they were created for.

   ### Enterprise Admins Group - grants a user administrative privileges over all sides of an enterprise domain
       - enterprise domain usually refers to the main domain used by the company — the central one where most employees’ accounts live.

   Tree - when you have multiple domains that share the same namespace (thm.local)
   Forest - The union of several trees with different namespaces into the same network

   Trust Relationship - when trees and forests are joined together
       One-Way Trust Relationship - if Domain AAA trusts Domain BBB, this means that a user on BBB can be authorised to access resources on AAA
           - The direction of the one-way trust relationship is contrary to that of the access direction.
               - Domain AAA is giving trust to the direction of Domain BBB, who in turn accesses info from the opposite direction

   Two-way trust relationships - can also be made to allow both domains to mutually authorise users from the other. By default, joining several domains under a tree or a forest will form a two-way trust relationship.

