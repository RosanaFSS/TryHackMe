<p><h3> Welcome to the <em>TryHackMe</em></h3>
<h1>Jr Penetration Tester learning path> Network Security</h1>
<h2>Nmaps Basic Port Scans</h2>
<p>Learn in-depth how nmap TCP connect scan, TCP SYN port scan, and UDP port scan work.</p>
<p>October 20, 2024<br></p>

![image](https://github.com/user-attachments/assets/4ef64337-781b-4c57-83cc-bb94140b8d5c)

<p>Type: Easy<br>
Access this TryHackMe Room clicking <a href="https://tryhackme.com/r/room/nmap02">Nmap Basic Port Scans</a>
<p><br></p>

<h2>Task 1 - Introduction</h2>

<p>This room is the second in the Nmap series (part of the <em>Introduction to Network Security module</em>).<br>
<ol type="1. ">
    <li><a href="https://tryhackme.com/r/room/nmap01">Nmap Live Host Discover</a></li>
    <li><a href="https://tryhackme.com/r/room/nmap02">Nmap Basic Port Scans</a></li>
    <li><a href="https://tryhackme.com/r/room/nmap03">Nmap Advanced Port Scans</a></li>
    <li><a href="https://tryhackme.com/r/room/nmap04">Nmap Post Port Scans</a>)</li>
</ol></p>
<p>In the previous room, we focused on discovering online systems. So far, we have covered three steps of a Nmap scan:<br>
<ol type="1. ">
  <li>Enumerate targets</li>
  <li>Discover live hosts</li>
  <li>Reverse-DNS lookup</li>
</ol></p>

![image](https://github.com/user-attachments/assets/320e3fd4-3334-4107-b771-7db4dc694c61)

<p>The next step would be checking which ports are open and listening and which ports are closed. Therefore, in this room and the next one, we focus on port scanning and the different types of port scans used by <strong>nmap</strong>. This room explains:</p>
<ol type="1. ">
  <li>TCP connect port scan</li>
  <li>TCP SYN port scan</li>
  <li>UDP por scan</li>
</ol>

<p>Moreover, we discuss the different options to specify the ports, the scan rate, and the number of parallel probes.</p>

> 1.1 - <em>Launch the AttackBox by using the Start AttackBox button. You will launch different types of scans against the target VM to gain a solid knowledge of Nmap basic scan types.</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>

<h2>Task 2 - TCP and UDP ports</h2>

<p>In the same sense that an IP address specifies a host on a network among many others, <strong>a TCP port or UDP port is used to identify a network service running on that host</strong>.<br>

A server provides the network service, and it adheres to a specific network protocol. Examples include providing time, responding to DNS queries, and serving web pages. A port is usually linked to a service using that specific port number. For instance, an HTTP server would bind to TCP port 80 by default; moreover, if the HTTP server supports SSL/TLS, it would listen on TCP port 443. (TCP ports 80 and 443 are the default ports for HTTP and HTTPS; however, the webserver administrator might choose other port numbers if necessary.) Furthermore, no more than one service can listen on any TCP or UDP port (on the same IP address).<br><br>
At the risk of oversimplification, <strong>we can classify ports in two states</strong>:</p>
<ol type="1. ">
  <li><strong><em>Open port</em></strong> indicates that <strong><em>there is SOME service listening on that port</em></strong>.</li>
  <li><strong><em>Closed port</em></strong> indicates that <strong><em>there is NO service listening on that port</em></strong>.</li>
</ol>
<p></p>
<p>However, in practical situations, we need to consider the impact of firewalls. For instance, a port might be open, but a firewall might be blocking the packets. Therefore, Nmap considers the following <strong>six states</strong>:</p>
<ol type="1. ">
  <li><strong><em>Open</em></strong>:         indicates that a service is listening on the specified port.</li>
  <li><strong><em>Closed</em></strong>:       indicates that no service is listening on the specified port, although the port is accessible. By accessible, we mean that it is reachable and is not blocked by a firewall or other security appliances/programs.</li>
  <li><strong><em>Filtered</em></strong>:     means that Nmap cannot determine if the port is open or closed because the port is not accessible. This state is usually due to a firewall preventing Nmap from reaching that port. Nmap’s packets may be blocked from reaching the port; alternatively, the responses are blocked from reaching Nmap’s host.</li>
  <li><strong><em>Unfiltered</em></strong>:    means that Nmap cannot determine if the port is open or closed, although the port is accessible. This state is encountered when using an ACK scan <code>-sA</code>.</li>
  <li><strong><em>Open|Filtered</em></strong>: means that Nmap cannot determine whether the port is open or filtered.</li>
  <li><strong><em>Closed|Filtered</em></strong>: means that Nmap cannot decide whether a port is closed or filtered.</li>
</ol>
<p><br></p>

> 2.1 - <em>Which service uses UDP port 53 by default?.</em><br>
>> <strong>DNS</strong><br>
<p><br></p>

> 2.2 - <em>Which service uses TCP port 22 by default?</em><br>
>> <strong>SSH</strong><br>
<p><br></p>

> 2.3 - <em>How many port states does Nmap consider?</em><br>
>> <strong>6</strong><br>
<p><br></p>

> 2.4 - <em>Which port state is the most interesting to discover as a pentester?</em><br>
>> <strong>Open</strong><br>
<p><br></p>

<h2>Task 3 - TCP Flags</h2>

<p>Nmap supports different types of TCP port scans. To understand the difference between these port scans, we need to review the TCP header. The TCP header is the first 24 bytes of a TCP segment. The following figure shows the TCP header as defined in <a href="https://datatracker.ietf.org/doc/html/rfc793.html">RFC 793</a>. This figure looks sophisticated at first; however, it is pretty simple to understand. In the first row, we have the source TCP port number and the destination port number. We can see that the port number is allocated 16 bits (2 bytes). In the second and third rows, we have the sequence number and the acknowledgement number. Each row has 32 bits (4 bytes) allocated, with six rows total, making up 24 bytes.</p>

![image](https://github.com/user-attachments/assets/0a33593e-e232-432d-8a38-00ec8ac6978e)

<p>In particular, we need to focus on the flags that Nmap can set or unset. We have highlighted the TCP flags in red. Setting a flag bit means setting its value to 1. From left to right, the TCP header flags are:</p>
<ol type="1. ">
  <li><strong><em>URG</em></strong>:        Urgent flag indicates that the urgent pointer filed is significant. The urgent pointer indicates that the incoming data is urgent, and that a TCP segment with the URG flag set is processed immediately without consideration of having to wait on previously sent TCP segments.</li>
  <li><strong><em>ACK</em></strong>:       Acknowledgement flag indicates that the acknowledgement number is significant. It is used to acknowledge the receipt of a TCP segment.</li>
  <li><strong><em>PSH</em></strong>:      Push flag asking TCP to pass the data to the application promptly.</li>
  <li><strong><em>RST</em></strong>:    Reset flag is used to reset the connection. Another device, such as a firewall, might send it to tear a TCP connection. This flag is also used when data is sent to a host and there is no service on the receiving end to answer.</li>
  <li><strong><em>SYN</em></strong>: Synchronize flag is used to initiate a TCP 3-way handshake and synchronize sequence numbers with the other host. The sequence number should be set randomly during TCP connection establishment.</li>
  <li><strong><em>FIN</em></strong>: The sender has no more data to send.</li>
</ol>
<p><br></p>

> 3.1 - <em>What 3 letters represent the Reset flag?.</em><br>
>> <strong>RST</strong><br>
<p><br></p>

> 3.2 - <em>Which flag needs to be set when you initiate a TCP connection (first packet of TCP 3-way handshake)?</em><br>
>> <strong>SYN</strong><br>
<p><br></p>

<h2>Task 4 - TCP Connect Scan</h2>

<p>TCP connect scan works by completing the TCP 3-way handshake. In standard TCP connection establishment, the client sends a TCP packet with SYN flag set, and the server responds with SYN/ACK if the port is open; finally, the client completes the 3-way handshake by sending an ACK.</p>

![image](https://github.com/user-attachments/assets/e20af675-05d4-408d-a288-aef5f3371d71)

<p>We are interested in learning whether the TCP port is open, not establishing a TCP connection. Hence the connection is torn as soon as its state is confirmed by sending a RST/ACK. You can choose to run TCP connect scan using <code>-sT</code>.</p>

![image](https://github.com/user-attachments/assets/9ed50528-3498-448a-a17a-6adaeb20ecce)

<p>It is important to note that <strong><em>if you are not a privileged user (root or sudoer), a TCP connect scan is the only possible option to discover open TCP ports</em></strong>.<br><br>
    
In the following Wireshark packet capture window, we see Nmap sending TCP packets with SYN flag set to various ports, 256, 443, 143, and so on. By default, Nmap will attempt to connect to the 1000 most common ports. A closed TCP port responds to a SYN packet with RST/ACK to indicate that it is not open. This pattern will repeat for all the closed ports as we attempt to initiate a TCP 3-way handshake with them.</p>

![image](https://github.com/user-attachments/assets/21973052-6dea-4cc9-af96-17d51a346a4f)

<p>We notice that port 143 is open, so it replied with a SYN/ACK, and Nmap completed the 3-way handshake by sending an ACK. The figure below shows all the packets exchanged between our Nmap host and the target system’s port 143. The first three packets are the TCP 3-way handshake being completed. Then, the fourth packet tears it down with an RST/ACK packet.</p>

![image](https://github.com/user-attachments/assets/f0070c1f-1a50-48e1-a49d-229f1f1d2798)

<p>To illustrate the <code>-sT</code> (TCP connect scan), the following command example returned a detailed list of the open ports.<br></p>

![image](https://github.com/user-attachments/assets/ccde1a0d-9b15-48b7-8dd4-46a91d6a9aa0)

<p>Note that we can use <code>-F</code> to enable fast mode and decrease the number of scanned ports from 1000 to 100 most common ports.<br><br>
<p><br></p>

> 4.1 - <em>Launch the VM. Open the AttackBox and execute <code>nmap -sT 10.10.240.191</code> via the terminal. A new service has been installed on this VM since our last scan. Which port number was closed in the scan above but is now open on this target VM?</em><br>
>> <strong>110</strong><br>

![image](https://github.com/user-attachments/assets/4bf8187d-ea55-4465-988c-16db3c6db99d)
<p></p>

> 4.2 - <em>What is Nmap’s guess about the newly installed service?</em><br>
>> <strong>pop3</strong><br>
<p><br></p>

<h2>Task 5 - TCP SYN Scan</h2>

<p>Unprivileged users are limited to connect scan. However, the default scan mode is SYN scan, and it requires a privileged (root or sudoer) user to run it. SYN scan does not need to complete the TCP 3-way handshake; instead, it tears down the connection once it receives a response from the server. Because we didn’t establish a TCP connection, this decreases the chances of the scan being logged. We can select this scan type by using the <code>-sS</code> option. The figure below shows how the TCP SYN scan works without completing the TCP 3-way handshake.</p>


<p>The following screenshot from Wireshark shows a TCP SYN scan. The behaviour in the case of closed TCP ports is similar to that of the TCP connect scan.</p>

<p> To better see the difference between the two scans, consider the following screenshot. In the upper half of the following figure, we can see a TCP connect scan <code>-sT</code> traffic. Any open TCP port will require Nmap to complete the TCP 3-way handshake before closing the connection. In the lower half of the following figure, we see how a SYN scan <code>-sS</code> does not need to complete the TCP 3-way handshake; instead, Nmap sends an RST packet once a SYN/ACK packet is received.</p>

<p>TCP SYN scan is the default scan mode when running Nmap as a privileged user, running as root or using sudo, and it is a very reliable choice. It has successfully discovered the open ports you found earlier with the TCP connect scan, yet no TCP connection was fully established with the target.</p>
<p><br></p>

> 5.1 - <em>Launch the VM. Some new server software has been installed since the last time we scanned it. On the AttackBox, use the terminal to execute <code>nmap -sS 10.10.240.191</code>. What is the new open port?</em><br>
>> <strong>RST</strong><br>
<p><br></p>

> 5.2 - <em>What is Nmap’s guess of the service name?</em><br>
>> <strong>SYN</strong><br>
<p><br></p>

<h2>Task 6 - UDP Scan</h2>








>> Performing Nmap I identified 3 ports open: 80/http, 3389/ssl, and 8080/http.<br>
>> <code>nmap -Pn -sC -sV -sS -p- -T4 10.10.30.67</code><br>


