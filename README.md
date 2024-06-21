<h1>Wireshark Network Analysis</h1>

<h2>Description:</h2>
This project involves using Wireshark to capture and analyze network packets. Wireshark is a powerful network protocol analyzer that enables you to see what’s happening on your network at a microscopic level. It is widely used for network troubleshooting, analysis, software and protocol development, and education.

<h2>Key Objectives:</h2>

Install and Run Wireshark on Kali Linux: Start Wireshark and select a network interface to capture packets.
Capture Network Traffic: Capture packets on a selected network interface (eth1).
Analyze HTTP Traffic: Filter and analyze HTTP packets to identify unsecure websites.
Apply Filters: Use Wireshark filters to isolate specific types of traffic (e.g., TCP port 80).
Understand Packet Details: Examine detailed packet information for protocols like HTTP, TCP.
Explore SIP and RTP: Use Wireshark’s Telephony features to analyze SIP and RTP streams in a sandbox environment.
Configure Coloring Rules: Modify packet colorization for better visual analysis.
<h2>Utilities Used:</h2>

Utilities: Wireshark, Kali Linux
Tools: Terminal, Wireshark GUI
<h2>Environments Used:</h2>

Operating Systems: Kali Linux
Hardware: Virtual Machines
Tools: Wireshark, Web Browser
<h2>Program Walk-through:</h2>
Open up Kali linux and Run Wireshark on Kali Linux:
<img src="https://i.imgur.com/WN98Hk2.png">
Open terminal.
Input the command: wireshark.
<Img src="https://i.imgur.com/dmZmibT.png">
Capture Network Traffic:
In Wireshark GUI, select the network interface eth1.
Start capturing packets.
<img src="https://i.imgur.com/N586ef3.png">
When Wireshark opens, you will see the main window with several key components:
Menu Bar: Provides access to various functions like File, Edit, View, etc.
Toolbar: Contains quick access buttons for common actions like starting/stopping captures.
Capture Interfaces: Lists available network interfaces you can use to capture traffic.
Main Window: Initially shows a welcome screen, then displays captured packets.
Analyze HTTP Traffic:
<img src="https://i.imgur.com/keG8pZA.png"> 
Pause the capture.
Open a web browser and visit an HTTP website, seen in the screenshot i opened a unsecure HTTP.
<img src="https://i.imgur.com/NwrafhW.png"> <img src="https://i.imgur.com/iZpuK7W.png">
Resume the capture, then pause again after some traffic is generated.
Apply the filter http in the Wireshark filter bar.
<img src="https://i.imgur.com/CuqEFbX.png">
Examine Packet Details:
<img src="https://i.imgur.com/LhMnVNH.png">
Select an HTTP packet.
View the detailed breakdown of the packet, including Frame, Ethernet, IP, TCP, and HTTP layers, you can see the HTTP i visited.
Right-click on an HTTP packet, go to Follow > HTTP Stream to see the entire HTTP conversation.
Apply Filters:
<img src="https://i.imgur.com/tsKor6c.png">
When you select a packet and use the "Follow HTTP Stream" feature in Wireshark, you can view the entire HTTP conversation between the client and server. This includes all HTTP requests and responses associated with the selected packet. Here's a breakdown of what is shown:

HTTP Requests and Responses:

Displays all HTTP requests made by the client (e.g., GET, POST).
Displays all HTTP responses from the server (e.g., status codes, headers).
Headers and Data:

Shows the HTTP headers (e.g., Host, User-Agent, Content-Type).
Includes the actual data sent in the requests and responses, such as HTML content, JSON payloads, etc.
Color Coding:

Requests are usually colored differently from responses to easily differentiate them.
Commonly, client requests are displayed in red text, and server responses in blue text.
Complete Conversation:

Provides a holistic view of the entire conversation between the client and server, making it easier to diagnose issues related to HTTP transactions, such as missing resources, incorrect data sent, or server errors.
<img src="https://i.imgur.com/xL2q5N6.png">
Use tcp.port == 80 to filter HTTP traffic.
The filter tcp.port == 80 in Wireshark is used to display all TCP packets that are either sent to or received from port 80. Port 80 is the default port for HTTP traffic, which means this filter is commonly used to analyze web traffic. This helps in monitoring and troubleshooting HTTP communications between a web server and clients.
<img src="https://i.imgur.com/qW984pt.png">
To change packet colors, go to View > Coloring Rules.
Color Meanings in Wireshark
Wireshark uses color coding to help users quickly identify different types of traffic and issues. Here are some common color codes and their meanings:

Light Blue (TCP Traffic)

Description: Indicates TCP traffic. This is the default color for TCP packets that don't match more specific rules.
Green (HTTP Traffic)

Description: Indicates HTTP traffic. This helps to quickly identify web traffic.
Dark Blue (DNS Traffic)

Description: Indicates DNS traffic. This is useful for identifying name resolution issues.
Yellow (Warnings)

Description: Indicates packets with warnings, such as retransmissions or duplicate ACKs in TCP traffic.
Red (Errors)

Description: Indicates packets with errors, such as malformed packets or checksum errors.
Black (Expert Info)

Description: Indicates packets flagged by Wireshark's expert information system for potential issues.#
<Img src="https://i.imgur.com/vd0B6hm.png">
Explore Advanced Filters:
<Img src="https://i.imgur.com/YoovpgC.png">
Apply the filter tcp.flags.syn==1 to view SYN packets.
tcp.flags.syn==1:

Use Case: Troubleshooting connection issues where clients are unable to establish a connection with a server.
What You'll See: All SYN packets, representing attempts to initiate a TCP connection.
<img src="https://i.imgur.com/T9JDjqO.png">
Apply the filter tcp.analysis.flags to view packets with TCP analysis flags.
tcp.analysis.flags:

Use Case: Diagnosing performance problems or errors in a network communication session.
What You'll See: Packets marked with various TCP analysis flags, indicating potential issues like retransmissions, duplicate ACKs, etc.
Apply the filter tcp.flags.reset==1 to view TCP reset packets.
<img src="https://i.imgur.com/ROLowUR.png">
tcp.flags.reset==1:

Use Case: Investigating unexpected connection terminations or server errors.
What You'll See: All RST packets, representing instances where a connection was reset.
<img src="https://i.imgur.com/IM5EFza.png">
SIP and RTP Analysis:

Access the Wireshark sandbox for SIP and RTP.
Download and open the sandbox capture file in Wireshark.
<img src="https://i.imgur.com/0mOLc2o.png">
Go to Telephony > RTP > RTP Streams.
<img src="https://i.imgur.com/dPWkjBm.png">
Explain RTP streams, SIP call, RTP g711 codec.
RTP Streams:

RTP streams represent the actual media content being transferred, such as audio or video. Each stream has a source and a destination IP address and port, indicating the endpoints of the communication.
SIP Call:

A SIP call involves signaling and controlling multimedia communication sessions. SIP manages the setup and teardown of these sessions, but the actual media exchange (voice or video) happens through RTP streams.
SIP uses multiple types of messages like INVITE, ACK, BYE, etc., to control the communication sessions.
RTP g711 Codec:

The g711 codec is a commonly used audio codec in VoIP communications. It is an uncompressed codec providing high-quality audio.
The g711 codec operates at 64 kbps and is widely used due to its compatibility and standardization in telecommunication systems
<img src="https://i.imgur.com/wdQ4zPr.png">
Click on a source address and then click on play streams
<h2>[Watch the video on Imgur](https://imgur.com/8gLsrtj)</h2>
<h2>[Watch the video on Imgur](https://imgur.com/VVXixXH)</h2>
