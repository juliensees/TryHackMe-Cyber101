- SSL (Secure Sockets Layer) was created to secure communication on the WWW. Eventually TLS (Transport Layer   Security) was created that improved on the security measures  
    - TLS is a cryptographic protocol operating at the OSI model's transport layer  
        - it allows secure communication between a client and a server over an insecure network so that no one             can read or modify the exchanged data
        - many protocols have received security upgrades with the addition of TLS (HTTP, DNS, MQTT, & SIP, SMTP,           POP3, AND IMAP)  
     
  Step 1: the server (or client) that needs to identify itself will create a CSR (Cerificate Signing Request (CSR)  
  Step 2: the CA (Certificate Authority) that receives the request verifies it and issues a digital certificate  

  ### HTTP Over TLS

  - requesting a page over HTTPS will require 3 steps (after resolving the domain name)  
      - Establish a TCP three-way handshake with the target server  
      - Establish a TLS session   
      - Communicate using the HTTP protocol; for example, issue HTTP requests, such as GET /HTTP/1.1  
   
        - The first 2 steps are known as TLS negotiation and establishment
       
    ### Port Numbers Change When Adding TLS to SMTP, POP3, & IMAP

    HTTP (80)  
    HTTPS (443)  
    SMTP (25)  
    SMTPS (465 & 587)  
    POP3 (110)  
    POP3S (995)  
    IMAP (143)  
    IMAP3 (993)  

  ### OpenSSH
  - Benefits  
        - Secure authentication: Besides password-based authentication, SSH supports public key and two-factor                       authentication.  
        - Confidentiality: OpenSSH provides end-to-end encryption, protecting against eavesdropping. Furthermore, it                   notifies you of new server keys to protect against man-in-the-middle attacks.  
        - Integrity: In addition to protecting the confidentiality of the exchanged data, cryptography also protects                   the integrity of the traffic.  
        - Tunneling: SSH can create a secure “tunnel” to route other protocols through SSH. This setup leads to a  
            VPN-like connection.  
        - X11 Forwarding: If you connect to a Unix-like system with a graphical user interface, SSH allows you to use               the graphical application over the network.

    - the TELNET server will listen on port 23, but the SSH server will listen on port 22
    - connect using the command "ssh username@hostname" or IP address
    - the argument -X is required to support running GUI
          - ssh 192.168.124.148 -X
   
    ### SFTP (SSH File Transfer Protocol)
    - uses port 22
    - use command "sftp username@hostname"
    - is newer than FTPS (used in legacy systems, windows servers, etc)
          - unless a business partner or legacy system requires FTPS, use SFTP
      - a lot of banks use FTPS, among other legacy systems
     
    ### VPN (Virtual Private Network)

- You must put in a ssl log key, in order to decrypt in wireshark so that it's in plain text.
      - right click on one of the items that is a TLS, Protocol Preferences, Transport layer Security, Open Transport Layer Security.
               - add the SSL key to the "Pre-Master Secret Log filename"
