# Search Skills
### Linux]
 - first created in 1991
 - The ss command (socket statistics) is part of the iproute2 utility suite and is faster and more efficient than netstat, especially when dealing with a large number of connections. It provides detailed socket information and is now the preferred tool on modern Linux distributions. While netstat is still available on some systems, it's considered obsolete.

Some of netstat's functionality, particularly for routing tables, is now handled by the ip command.

 - Manual pages - "man page"

### Webpage searching
- quotes for exact phrase
- site:tryhackme.com success stories
    - will search the specific site for the words success stories
- pyramids -tourism
    - the "-" minus sign before tourism will make sure that pages returned don't include anything with "tourism" in them
- filetype:pdf cyber security
    - will show sites with pdf's about cyber security
+ Shodan.io
    - a search engine for devices connected to the internet
      - specific types and versions of servers, networking equipment, industrial control systems, and IoT devices
+ Censys
    - search.censys.io
    - focuses on Internet-connected hosts, websites, certificates, and other Internet assets.
    - you can check domains in ause, auditing open ports, and discovering rogue assets within a network
+ VirusTotal.com
    - website that provides a virus scanning service for files by uploading or providing URL's

- Common Vulnerabilities and Exposures (CVE) program is a dictionary of vulnerabilities
    - provides a standardized identifier for vulnerabilities with an ID like CVE-2024-29988
Exploit Database
  https://www.exploit-db.com/
  - used by red teams to find working exploit codes to pen tests systems

### Linux Commands

Ctrl - C  = gets you back to the command line (interrupts any processes currently happening)
Ctrl - X = exits 
"q" - stops a process from running

echo - outputs any text that is provided
whoami - find out what user you're logged in as
ls - list
cd - change directory
cat - concatenate; which outputs the content of files
pwd - print working directory; shows you where you are (listing all the folders you're now in)
find - used to search for things much better/faster
  find -name *.txt
    - finds any texts that exist
grep - command used to search the contents of files for specific values that you're looking for
  grep "81.143.211.90" access.log
    - searches through the access log for this specific ip address
-a = all files (including hidden files
  * ls -a        will list all files
ls --help
  - creates a list of commands (as a quick reminder)
man ls
  - creates a full breakdown of commands


touch - create file
mkdir - create a folder (make a directory)
cp - copy a file or folder
mv - move a file or folder
rm - remove a file or folder
file - determine the type of file
rm -R mydirectory
 * removes the mydirectory folder (need the -R for folders)

### Linux Operators

& - allows you to execute commands in the background
  - good for a large file that will take a while, whilst you do other things
&& - used to make a list of commands to run
  - command1 && command2
  - will only run if command1 was successful, otherwise command2 won't happen  
 ">" - send an output from a command to another place
    - echo hey > welcome
      - will create a new file called welcome (that has "hey" written into it)
      - if welcome already exists as a file, it will be overwritten  
 ">>" - adds the output at the end of an existing file (instead of overwriting)

### SSH
 - Secure Shell
 - a protocol between devices in an encrypted form
    - it allows us to remotely execute commands on another device remotely
    - any data sent between the devices is encrypted when it is sent over a network
    - ssh tryhackme@10.201.103.108
       - ssh is used to login with usernmae tryhackme @10.201.103.108 ip address

    
### Command Usage

cp note note2
    - copies the "note" contents to "note2"
mv note2 note3
    - technically "moves" note2's contents into note3
ls -lh
    - this lists the permissions of each user
- rwx rwx rwx cinematic cinematic
  - first group is read, write, and execute permissions for all other users
  - second group is read, write, and execute permissions for the group owner of the file
  - third group is read, write, and execute permissions for the file owner
    * the initial dash indicates a regular file, while a "d" would indicate it's a directory
    * next word (cinematic) is file owner, and then group owner
su - substitute user (changes users)
/etc - pronounced "etsy", but it's short for etcetera
  - a commonplace location to store system files
/var - short for variable data, is one of the main root folders ono a linux install
  - the folder stores data that is frequently acccessed or written by services or apps running on the system, like log files
/root - the home directory for the "root" user
/tmp - short for temporary
  - is volatile and used to store data that is only needed to be accessed once or twice. it is cleared once the computer is restarted
  - good place to store things like enumeration scripts for pentesters

### Terminal Text Editors

Nano - used to create or edit a new or existing file within the nano text editor
 nano myfile - will open the editor for a file named myfile
Vim - a more advanced text editor
wget - used to download files from the internet
  wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt       - will download the file from this link
SCP - allows you to transfer files between two computers using the SSH protocol to provide both authentication and encryption
- Copy a file on a local machine to a remote machine
 * scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
    - "important.txt" is the name of the file we want to copy from our machine
    - ubuntu is the user on the remote system
    - 192.168.1.30 is the ip address of the remote system
    - /home/ubuntu/transferred.txt is the folder to copy to, and "Transferred.txt" is the name of the new file we want to create with the copied txt
- Copy a file from a remote machine to my local machine that i'm logged into
 * scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
    - the command of SSH is the username and ip address of the remote computer
    - separated by a colon
    - then the location of the "documents.txt" file
    - then copying that data to our current working directory, with the title of "notes.txt"
  
 ### Connecting to the internet in a terminal
 python3 -m http.server
    - starts a simple HTTP web server on your machine
    - uses port 8000
    * then i can open a new tab in ubuntu, and use: wget http://10.201.59.122:8000/.flag.txt     - to download the .flag.txt file 

 ### Processes 101
 - processes are programs that are running on your machine
 -  They are managed by the kernel, where each process will have an ID associated with it, also known as its PID.
 -  The PID increments for the order in which the process starts. I.e. the 60th process will have a PID of 60.
   * "ps" command - will provide a list of the running processes
   * "ps aux" command - to see the processes run by other users and those that don't run from a session (i.e. system processes)
   * " ps aux | less " - will give a more detailed version of each process. printing the full line
   * "top" command - gives real-time statistics about the processes running on your system (they will automatically refresh every 10 seconds, or when using arrow keys)
   * kill command - terminates a process
      - kill 1337    - will kill PID 1337
       - SIGTERM - Kill the process, but allow it to do some cleanup tasks beforehand
       - SIGKILL - Kill the process - doesn't do any cleanup after the fact
       - SIGSTOP - Stop/suspend a process

 systemd - one of the first processes to start when a system boots up. 
    - it usually has a PID of 0 because it's one of the first
    - Any program or piece of software that we want to start will start as what's known as a child process of systemd. This means that it is controlled by systemd, but will run as its own process (although sharing the resources from systemd) to make it easier for us to identify 

 systemctl command
  - start, stop, enable, disable
  "systemctl start apache" - will start apache

  ### Foreground & Backgrounding

  echo "Hi THM"       - will output "Hi THM" in the terminal (just runs in the foreground)  
  echo "Hi THM" &     - the ampersand makes the command run/process in the background so you can continue with other tasks   
                      - will just output the ID of the echo process (not the text)

   * great for things like copying files, so that it happens in the background
   * with scripts, you can use Ctrl + Z to specifically background a process
   * Ctrl + Z also will pause a current script or command

- "fg" command brings processes back to the foreground

* If we were to launch a process where the previous ID was "300", what would the ID of this new process be?
   - it would be 301 because increments by 1, everytime we run a new process

### Automation

Cron process - used to schedule actions, using crontabs
  - started during the boot process

crontab - e
      - used to edit crontabs within the terminal
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
    - first * is minutes, 12 is hours, next is day of the month, month, day of the week, and then the command:
        - copy "cmnatic's" "Documents" every 12 hours
- "@reboot" means to run the task immediately after reboot, BUT ONLY ONCE!, not on repeat for every reboot
    - so could be @reboot vncserver :1 -depth 24 -geometry 1900x1200
