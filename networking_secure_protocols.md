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

    
