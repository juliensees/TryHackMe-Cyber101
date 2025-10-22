### OSI (Open Systems Interconnection) Model - defines a framework for computer network communications
 - theoretical model

7 Layers:   
    Physical Layer  
    Data Link Layer  
    Network Layer  
    Transport Layer  
    Session Layer  
    Presentation Layer  
    Application Layer  

Layer 1: Physical Layer
  - includes physical connections like the medium (wire), and the definition of the binary units (0 and 1)
      - ethernet cable, optical fibre cable, wifi radio bands (2.4ghz, 5ghz, and 6ghz bands)

Layer 2: Data Link Layer
  - represents the protocol that enables data transfer between nodes on the same network segment
      - it describes an agreement between the different systems on the same network segment on how to communicate
          - network segment refers to a group of networked devices using a shared medium/channel
  - examples of layer 2: ethernet (802.3), wifi (802.11)
      - MAC address (Media Access Control) - expressed in hexadecimal format with colons separating each hexa digits
      - a4:c3:f0:86:ac:2d
        - first 3 on the left identify the vendor (Intel), the 3 hexadecimals on the right is the unique address for the interface
       
Layer 3: Network Layer
  - concerned with sending data between different networks
      - handles logical addressing & routing, finding a path to transfer network packets
        -examples are Internet Protocol (IP), Internet Control Message Protocol (ICMP), Virtual Private Network (VPN) like IPSEC and SSL/TLS VPN

Layer 4: Transport Layer
  - enables end-to end communication between running applications on different hosts
      - the web browser is connected to the tryhackme web server over the transport layer
          - examples are Transmission Control Protocol (TCP) and User Datagram Protocol (UDP)

Layer 5: Session Layer 
  - responsible for establishing, maintining, and synchronising communication between applications running on different hosts
      - establishing a session means initiating communication between applications and negotiating the necessary parameters for the session
      - data sychronisation ensures that data is transmitted in the correct order and provides mechanisms for recovery
          - examples are Network File System (NFS) and Remote Procedure Call (RPC)
       
Layer 6: Presentation Layer 
  - ensures the data is delivered in a form the application layer can understand
      - handles data encoding (ASCII or Unicode), compression, and encryption
      - ex. when sending an e-mail, this layer uses MIME (Multipurpose Internet Mail Extensions) to encode a binary file using 7-bit ASCII characters (when attaching a file to an e-mail)
          - also JPEG, PNG, MPEG (in terms of compression)
   
Layer 7: Application Layer
  - provides network services directly to end-user applications
      - web browser uses HTTP protocol to request a file, submit a form, or upload a file
      - ex. HTTP, FTP, DNS, POP3, SMTP, and IMAP
   
### TCP/IP Model (RFC 1122)

- Created by the department of defense in the 1970's
- this model allows a network to continue to function as parts of it are out of service because of its design of the routing protocols to adapt as the newtork topology changes

Application Layer: the OSI application, presentation, & session layers are grouped into this model
Transport Layer: Layer 4
Internet Layer: Layer 3, called network layer in OSI model
Link Layer: Layer 2

IP Addresses
 - comprised of four octets (up to 32 bits)
      - the 0 and 255 are reserved for the network & broadcast addresses
      - 192.168.1.0 is the network address
      - 192.168.1.255 is the broadcast address
        ### sending to the broadcast address targets all the hosts on the network

Private IP Addresses
  - cannot reach or be reached from the outside world. can only access the internet if the router has a public IP address and supports Network Address Translation (NAT)
  - RFC 1918 defines the following 3 ranges of private IP Addresses
  - 10.0.0 - 10.255.255.255 (10/8)
  - 172.16.0.0-172.31.255.255 (172.16/12)
  - 192.168.0.0-192.168.255.255 (192.168/16)

Router
  - forwards data packets to the proper network
      - functions at layer 3, inspecting the IP address and forwarding the packet to the best network (router) so the packet gets closer to its destination

IP protocol allows you to reach a destination host on the network; the host is identified by its IP address. 
 - protocols enable processes on networked hosts to communicate with each other 

Transport Procols 
 UDP (User Datagram Protocol) - a connectionless protocol that operates at the transport layer that allows you to reach a specific process on the target host
   - a connectionless protocol means it doesn't actually establish a connection, but just sends whatever you wanted
      - they are faster than TCP in delivery, but they don't provide any info on whether the packet was delivered

 TCP (Transmission Control Protocol) - a connection oriented transport protocol
   - requires the establishment of a TCP connection before any data can be sent
   - each data octet has a sequence number so that the receiver can acknowledge the reception of data with an acknowledgement number specifying the last received octet
      - a TCP connection is established using a 3-way handshake; using 2 flags:
         - SYN (Synchronise)
         - ACK (Acknowledgement)

        1. SYN Packet: The client initiates the connection by sending a SYN packet to the server (contains the client's ranodmly chosen initial sequence number)
         2. SYN-ACK Packet: The server responds to the SYN  packe twith a SYN-ACK packet, which adds the initial sequence number randomly chosen by the server
         3. ACK Packet: The 3-way handshake is completed as the client sends an ACK packe to acknowledge the reception of the SYN-ACK packet
       
       ### Both UDP & TCP identifies the process of initiating or waiting (listening) for a connection using ports
      ### Valid port number ranges between 1 and 65535 (port 0 is reserved)

Encapsulation - refers to the process of every layer adding a header (and sometimes a trailer) to the received unit of data and sending the "ecapsulated" unit to the layer below
  - starts at the Application layer, where a user inputs data they want to send into the application (e-mail/msg)
  - transport layer adds a TCP or UDP header to create a TCP segment or UDP datagram
  - network layer, it adds the proper IP  header to get an IP packet that can be routed over the internet
  - link layer, adds the appropriate header and trailer to get a wifi or ethernet frame
     ### this process is then reversed on the receiving end until the application data is extracted

TELNET (Teletype Network) - a network protocol for remote terminal connections
 - initially used for remote admin, telnet can connect to any server listening on a TCP port number
  - CTRL +] - is to quit (though you need to then type quit, and enter)
  - 
