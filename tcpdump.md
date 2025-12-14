libpcap - packet capture library used with wireshark, tcpdump, etc
  - built with C programming language for packet sniffing
  - It provides a standard API for capturing network packets at the link layer (Ethernet, Wi-Fi, etc.).

- A command such as ip address show (or merely ip a s) would list the available network interfaces.
- saving a packet capture to a file using -w FILE
    - can later be put into wireshark for viewing
 
- to read a file, use -r FILE
 
- You can specify the number of packets to capture by specifying the count using -c COUNT. Without specifying a count, the packet capture will continue till you interrupt it, for example, by pressing CTRL-C

  ### DNS - Domain Name System
    - basically a global phone book
    - DNS forward lookup - example.com -> 142.250.190.78
        - forward DNS stores the mapping of domain name to IP address
    - DNS reverse lookup - 142.250.190.78 → lga25s79-in-f14.1e100.net
        - controlled by whoever owns the IP
        - so it might give you the cloud owner's address, not the domain owner's ip 
          
  ### tcpdump does reverse lookups by default, which is why it can pause

 * Why DNS lookups can be a problem
  - Slow (can stall packet capture)
  - Inaccurate (reverse DNS often misleading)
  - Generates extra DNS traffic
  - Can change output mid-capture

- forward and reverse don't have to match because they're managed by different entities
- Email servers sometimes require forward and reverse DNS to match for spam checks.

### So, cyber analysts usually use -n to disable reverse DNS and look at traffic patterns instead of names (which reverse DNS prints)
- tcpdump -i any -nn
    - captures packets on all interfaces and displays them on screen without domain name (-n) or protocol resolution (-nn).

PTR - "pointer"
  - points an address back to a hostname

### IP addresses are controlled by ISP's (internet service providers) and cloud providers 
  - ex. 45.113.0.203.in-addr.arpa.  PTR  myhost.example.com.
  - 
- below saves the tcpdump file from example.com to a file named "http.pcap"
  sudo tcpdump host example.com -w http.pcap

- Captures live traffic
  tcpdump -n icmp | wc -l
- Captures traffic from the specific traffic.pcap file
tcpdump -n -r traffic.pcap icmp | wc -l

"wc" - used to count the lines by piping the output through this command (-1 is line by line)  

- When a host wants the MAC address for an IP on the local network, it sends an ARP request  
- In order to find out what the MAC address is that's inquiring, use:  
   - tcpdump -n -r traffic.pcap arp
- Below command will filter DNS traffic (which is always on port 53)
   - tcpdump -n -r traffic.pcap port 53
 
### man pcap-filter   ---> will show manual list for all possible filters

- Below command will filter packets that only have reset flags (tcp-rst) --> don't forget the piping command!!
tcpdump -n -r traffic.pcap 'tcp[tcp-flags] == tcp-rst' | wc -l

- Below command will filter pakcets that have more than 15000 bytes
 tcpdump -n -r traffic.pcap greater 15000
- Below command will find the MAC address of who sent an ARP request
tcpdump -n -e -r traffic.pcap arp

Tcpdump is a rich program with many options to customize how the packets are printed and displayed. We have selected to cover the following five options:  
  -q: Quick output; print brief packet information  
  -e: Print the link-level header  
  -A: Show packet data in ASCII  
  -xx: Show packet data in hexadecimal format, referred to as hex  
  -X: Show packet headers and data in hex and ASCII  
