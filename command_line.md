### Advantages of a CLI (Command Line Interface)

- Lower resource usage: CLIs require fewer system resources than graphics-intensive GUIs. In other words, you can run your CLI system on older hardware or systems with limited             memory. If you are using cloud computing, your system will require lower resources, which in turn will lower your bill.
- Automation: While you can automate GUI tasks, creating a batch file or script with the commands you need to repeat is much easier.
- Remote management: CLI makes it very convenient to use SSH to manage a remote system such as a server, router, or an IoT device. This approach works well on slow network                 speeds and systems with limited resources.

### CMD Line 

set - checks the path where MS Windows line will execute commands (Path=)
ver - checks the version of windows
systeminfo - basic system info (OS information, system details, processor and memory)
cls - clears the command line screen
| more - used after another term (driverquery | more), so that it only shows a page, and you can increase line by line by pressing enter
CTRL + C - will exit a "| more" query 
ipconfig - IP address, subnet mask, and default gateway.
ipconfig /all - shows even more extensive info
ping " " - sends a specific ICMP packet and listen for a response. (ex. ping google.com)
tracert " " - stands for "trace route"
  - traces the network route traversed to reach the target. it expects the routers on the path to notify us if they drop a packet because its time-to-live (TTL) has reached zero.
nslookup " " - looks up a host or domain and returns its IP address. (ex. nslookup google.com)
netstat - displays current network connections and listening ports.
  - netstat -h   = help page for netstat
dir /a - Displays hidden and system files
dir /s - Displays files in the current directory and all subdirectories.
mkdir - used to create a new directory
rmdir - used to remove a directory
del OR erase - used to delete a file
* - used for multiple files, so copy *.md C:/markdown , will copy all files ending with .md to that markdown folder
tasklist - basically a task manager (within CLI), that shows all processes that are running
  tasklist /? = shows "help/filter" options for tasklist
  tasklist /FI "imagename eq sshd.exe" - searches for tasks related to sshd.exe
  taskkill /PID 4567 - used to kill the process with PID 4567 or change for whichever you choose
chkdsk - checks the file system and disk volumes for errors and bad sectors.
driverquery - displays a list of installed device drivers.
sfc /scannow - scans system files for corruption and repairs them if possible.

shutdown /s - shutdown a system
shutdown /r - restart a system
shutdown /a - abort a shutdown
