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

Ctrl - C  = gets you back to the command line

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
> - send an output from a command to another place
    - echo hey > welcome
      - will create a new file called welcome (that has "hey" written into it)
      - if welcome already exists as a file, it will be overwritten
>> - adds the output at the end of an existing file (instead of overwriting)

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
