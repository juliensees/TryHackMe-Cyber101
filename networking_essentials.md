- whenever you want to access a network, you need to configure:
    - ip address with subnet mask
    - router (or gateway)
    - DNS server

Dynamic Host Configuration Protocol (DHCP) - application-level protocol that relies on UDP
  - basically used to give devices on a network their IP addresses and other network settings so they can communicate without manual configuration
        - also used to find out the DNS server and default route on a network automatically
  - the server listens on UDP port 67, and the client sends from UDP port 68  
  - smartphone and laptop are configured to use DCP by default  
 - follows 4 steps: Discover, Offer, Request, and Acknowledge (DORA)  
     - DHCP Discover: The client broadcasts a DHCPDISCOVER message seeking the local DCP server if one exists
     - DHCP Offer: The server responds with a DHCPOFFER message with an IP address available for the client to accept
     - DHCP Request: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP
     - DHCP Acknowledge: The server responds with a DHCPACK message to confirm the offered IP address is now assigned to           this client
        - 255.255.255.255 is the destination IP address a client uses when it first sends the DHCP Discover packet
        - 0.0.0.0 is the source IP address a client uses when trying to get IP network configuration over DHCP
      
  Address Resolution Protocol (ARP) - used to map a device's IP address (the logical, layer 3 address) to its MAC               address (the physical layer 2 address)    
    - basically to determine the destination MAC address for a given destination IP address, so your device can send the             ethernet frame (the data container used on a local network (layer 2) that travels across the ethernet cable                 (like an envelope that carries higher-level data like IP packets, TCP segements)  
    - ff:ff:ff:ff:ff:ff - broadcast MAC address used in an ARP request 

Internet Control Message Protocol (ICMP) - used for network diagnostics and error reporting
  - ping: the command uses ICMP to test connectivity to a target system and measures the round-trip time (RTT)
      - a ping might not return if the target system is offline or shut down, or a firewall may block it
      - ping 192.168.11.1 -c 4 == will ping 4 packets only before it stops
  - traceroute: this command is called traceroute on Linux and Unix-likie systems and tracert on MS Windows systems
        - it uses ICMP to discover the route from your host to the target
        - basically shows you the path your packets take to reach a destination (every router it goes through)
      TTL (Time to Live) - traceroute uses this in an IP packet in order to determine the number of routers
        - starts with 64-255, and decreases by 1 each time it "finds" a router

Network Address Translation (NAT) - a technique used by some routers and firewalls to map private IP addresses inside a       local network to a single (or a few) public IP addresses on the internet    
    - basically due to IPv4 only allowing 4.3 billion possible public IP addresses, NAT allows thousands of devices in   
      a private network to share one public IP  
      - so NAT rewrites outgoing packets so they appear to come from the p ublic IP, and rewrites incoming packets so             they reach the correct internal device   
          - the world only sees your router's public IP (like 203.0.113.10), not your private address (192.168.1.2)  
          - each public IP has about 64-65k ports

### FTP (File Transfer Protocol)

- with FTP login, you don't need to specify a port when signing in
          - "ftp 10.201.3.66"

    - USER is used to input the username  
    - PASS is used to enter the password  
    - RETR (retrieve) is used to download a file from the FTP server to the client.  
    - STOR (store) is used to upload a file from the client to the FTP server.  

FTP server listens on TCP port 21 by default; data transfer is conducted via another   connection from the client to the server.

### SMTP (Simple Mail Transfer Protocol)

- Use telnet to connect to a server and access with HELO or EHLO
          - HELO client.thm

- HELO or EHLO initiates an SMTP session  
- MAIL FROM specifies the sender’s email address  
- RCPT TO specifies the recipient’s email address  
- DATA indicates that the client will begin sending the content of the email message  
- "." is sent on a line by itself to indicate the end of the email message  

### Mail is retrieved using POP3

Since the POP3 server listens on TCP port 110 by default, the command to connect to the TELNET port is telnet 10.201.3.66 110. 

- Some common POP3 commands are:

    - USER <username> identifies the user  
    - PASS <password> provides the user’s password   
    - STAT requests the number of messages and total size  
    - LIST lists all messages and their sizes  
    - RETR <message_number> retrieves the specified message  
    - DELE <message_number> marks a message for deletion    
    - QUIT ends the POP3 session applying changes, such as deletions    

 
### Must put in each command for POP3 using telnet. "auth", "user strategos", "pass Pa$$123"           
user@TryHackMe$ telnet 10.201.3.66 110  
Trying 10.201.3.66...  
Connected to 10.201.3.66.  
Escape character is '^]'.  
+OK [XCLIENT] Dovecot (Ubuntu) ready.  
AUTH  
+OK  
PLAIN  
.  
USER strategos  
+OK  
PASS   
+OK Logged in.  
STAT  
+OK 3 1264  
LIST  
+OK 3 messages:  
1 407  
2 412  
3 445  
.  
RETR 3  
+OK 445 octets    
Return-path: <user@client.thm>  
Envelope-to: strategos@server.thm  
Delivery-date: Thu, 27 Jun 2024 16:19:35 +0000  
Received: from [10.11.81.126] (helo=client.thm)  
        by example.thm with smtp (Exim 4.95)  
        (envelope-from <user@client.thm>)  
        id 1sMrpq-0001Ah-UT  
        for strategos@server.thm;  
        Thu, 27 Jun 2024 16:19:35 +0000  
From: user@client.thm  
To: strategos@server.thm  
Subject: Telnet email  

Hello. I am using telnet to send you an email!  
.  
QUIT  
+OK Logging out.  
Connection closed by foreign host.  

 ### IMAP (Internet Message Access Protocol)

- IMAP allows synchronizing read, moved, and deleted messages. IMAP is quite convenient when you check your email via multiple clients. Unlike POP3, which tends to minimize server storage as email is downloaded and deleted from the remote server, IMAP tends to use more storage as email is kept on the server and synchronized across the email clients.

- The IMAP protocol commands are more complicated than the POP3 protocol commands. We list a few examples below:

    - LOGIN <username> <password> authenticates the user  
    - SELECT <mailbox> selects the mailbox folder to work with  
    - FETCH <mail_number> <data_item_name> Example fetch 3 body[] to fetch message number  
              3, header and body.  
    - MOVE <sequence_set> <mailbox> moves the specified messages to another mailbox  
    - COPY <sequence_set> <data_item_name> copies the specified messages to another mailbox  
    - LOGOUT logs out  

- Knowing that the IMAP server listens on TCP port 143 by default, we will use telnet to   connect to 10.201.3.66’s port 143 and fetch the message we sent in an earlier task.  
        
   ### Default port numbers

  Protocol 	Transport Protocol 	Default Port Number  
TELNET 	           TCP 	                23  
DNS 	           UDP or TCP 	        53  
HTTP 	            TCP 	            80  
HTTPS 	            TCP 	            443  
FTP 	            TCP 	            21  
SMTP 	            TCP 	            25  
POP3 	            TCP 	            110  
IMAP 	            TCP 	            143
