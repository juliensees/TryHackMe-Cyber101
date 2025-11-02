
- Domain Name System (DNS), which is responsible for properly mapping a domain name to an IP address

- DNS operates at the Application Layer, i.e., Layer 7 of the ISO OSI model. DNS traffic uses UDP port 53 by default and TCP port 53 as a default fallback. There are many types of DNS records; however, in this task, we will focus on the following four:

   - A record: The A (Address) record maps a hostname to one or more IPv4 addresses. For example, you can set example.com to resolve to                   172.17.2.172.  
   - AAAA Record: The AAAA record is similar to the A Record, but it is for IPv6. Remember that it is AAAA (quad-A), as AA and AAA would                   refer to a battery size; furthermore, AAA refers to Authentication, Authorization, and Accounting; neither falls under DNS.  
   - CNAME Record: The CNAME (Canonical Name) record maps a domain name to another domain name. For example, www.example.com can be mapped  
              to example.com or even to example.org.  
   - MX Record: The MX (Mail Exchange) record specifies the mail server responsible for handling emails for a domain.  
