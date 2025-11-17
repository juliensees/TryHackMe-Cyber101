### Wireshark

- open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP)
    - Detecting and troubleshooting network problems, such as network load failure points and congestion.  
    - Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.  
    - Investigating and learning protocol details, such as response codes and payload data.
 
  - View --> Coloring Rules" menu to create permanent colouring rules. The "Colourise Packet List" menu activates/deactivates the colouring rules.  
    Temporary packet colouring is done with the "right-click menu" or "View --> Conversation Filter" menu, which is covered in TASK-5.

* Wireshark has two types of filtering approaches: capture and display filters.

  ### Color Codes
  Severity / 	Colour  /	Info  
   Chat   /	   Blue / 	Information on usual workflow.  
   Note   /	   Cyan / 	Notable events like application error codes.  
   Warn   / 	 Yellow / 	Warnings like unusual error codes or problem statements.  
   Error  / 	 Red  / 	  Problems like malformed packets.  

### Hash - represents the unique contents of the file
- in the terminal, you can use
  - "md5sum file.txt"
      - this will generate the hash of the specific file requested 

Why do we use an MD5 hash?
1. Integrity check

If two people compute MD5 on the same file, the hashes should match.
If they don’t → the file was changed or corrupted.
