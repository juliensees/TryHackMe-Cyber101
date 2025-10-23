- whenever you want to access a network, you need to configure:
    - ip address with subnet mask
    - router (or gateway)
    - DNS server

Dynamic Host Configuration Protocol (DHCP) - application-level protocol that relies on UDP
  - basically used to give devices on a network their IP addresses and other network settings so they can communicate without manual configuration  
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

