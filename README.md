**Wireshark Capture Summary and Protocol Analysis**

**1. Capture Details**

I successfully performed a network packet capture on my active interface ([e.g., Wi-Fi adapter or Ethernet]) for approximately one minute. The capture generated [Insert the Total Packet Count here] packets of data. To create relevant traffic, I initiated a basic network activity, such as browsing a website and/or running a ping command. The raw data has been exported as a .pcapng file for future reference.

**2. Identified Protocols**

By filtering the captured traffic, I confirmed the presence of the following three essential network protocols, which validate typical internet communication flow:
Protocol	OSI Layer	Observation/Purpose in Capture
DNS	Application	Found numerous Query and Response packets, confirming the initial step of resolving a domain name (e.g., google.com) to its corresponding IP address.
TCP	Transport	This protocol was dominant. I observed the fundamental Three-Way Handshake (SYN, SYN-ACK, ACK), which signifies the reliable connection establishment necessary for web browsing and other high-level services.
HTTP/ICMP	Application/Internet	I identified HTTP (GET requests and 200 OK responses) related to the browsing activity, confirming data retrieval. (Alternatively, if I used ping: I identified ICMP Echo Request and Echo Reply packets, confirming basic connectivity and latency).

**3. Detailed Packet Analysis (Layer Breakdown)**

To understand the communication process at a granular level, I drilled down into a specific HTTP (or TCP) packet. This process confirmed the OSI layer encapsulation:

    Layer 2 (Data Link - Frame/Ethernet): The packet shows the physical transfer details, including my network adapter's Source MAC Address and the router's Destination MAC Address.

    Layer 3 (Network - IP): This layer revealed the logical addressing: my Source IP Address (local network IP) and the final server's Destination IP Address (public IP).

    Layer 4 (Transport - TCP): The TCP header specified the dynamic Source Port used by my machine and the standard Destination Port (e.g., Port 80 for unencrypted HTTP), confirming the service being accessed.

    Layer 7 (Application - HTTP): This top layer contained the actual content payload, such as the GET / request, which is what my browser sent to the server.

The analysis provided a clear visual confirmation of how various protocols work together to form a complete network conversation.
