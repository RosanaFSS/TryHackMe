<p><h3> Welcome to the <em>TryHackMe</em></h3>
<h1>Jr Penetration Tester learning path> Network Security</h1>
<h2>Nmap Basic Port Scans</h2>
<p>Learn in-depth how nmap TCP connect scan, TCP SYN port scan, and UDP port scan work.</p>
<p>October 20, 2024<br></p>

<div style="display: flex; justify-content: center; align-items: center;">
    <img src="https://github.com/user-attachments/assets/5a8a95a4-4200-467c-a50f-546d8b2481b1" width="200px" height="200px"/>
</div>
<br>

![image](https://github.com/user-attachments/assets/119bac7c-5666-4044-a539-528b6ddaea64)

<p><br></p>
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
>> <strong>POP3</strong><br>
<p><br></p>

<h2>Task 5 - TCP SYN Scan</h2>

<p>Unprivileged users are limited to connect scan. However, the default scan mode is SYN scan, and it requires a privileged (root or sudoer) user to run it. SYN scan does not need to complete the TCP 3-way handshake; instead, it tears down the connection once it receives a response from the server. Because we didn’t establish a TCP connection, this decreases the chances of the scan being logged. We can select this scan type by using the <code>-sS</code> option. The figure below shows how the TCP SYN scan works without completing the TCP 3-way handshake.</p>

![image](https://github.com/user-attachments/assets/11843f51-c1b7-4f78-9a9e-fc88ebc1ef68)

<p>The following screenshot from Wireshark shows a TCP SYN scan. The behaviour in the case of closed TCP ports is similar to that of the TCP connect scan.</p>

![image](https://github.com/user-attachments/assets/ca374b12-5fbc-4d91-9794-5f086d623b9a)

<p> To better see the difference between the two scans, consider the following screenshot. In the upper half of the following figure, we can see a TCP connect scan <code>-sT</code> traffic. Any open TCP port will require Nmap to complete the TCP 3-way handshake before closing the connection. In the lower half of the following figure, we see how a SYN scan <code>-sS</code> does not need to complete the TCP 3-way handshake; instead, Nmap sends an RST packet once a SYN/ACK packet is received.</p>

![image](https://github.com/user-attachments/assets/12c08cf6-6c60-4493-94ae-469679dc0795)

<p>TCP SYN scan is the default scan mode when running Nmap as a privileged user, running as root or using sudo, and it is a very reliable choice. It has successfully discovered the open ports you found earlier with the TCP connect scan, yet no TCP connection was fully established with the target.</p>

![image](https://github.com/user-attachments/assets/24345f09-0474-461b-b941-228af0eeda43)

<p><br></p>

> 5.1 - <em>Launch the VM. Some new server software has been installed since the last time we scanned it. On the AttackBox, use the terminal to execute <code>nmap -sS 10.10.240.191</code>. What is the new open port?</em><br>
>> <strong>6667</strong><br>

<p>I could not find 6667 port open.  As new ports open I found 993 and 995.</p>

![image](https://github.com/user-attachments/assets/76efded2-ff62-4986-8764-09c4debab5d8)

![image](https://github.com/user-attachments/assets/67faf5bc-2eac-455d-8723-01c103b1a3ee)

<p>I scanned ports 1000 until 10000, and also did not fing 6667 port open.</p>

![image](https://github.com/user-attachments/assets/b6a722b3-258b-40b9-b565-ead53d6f779d)

<p><br></p>

> 5.2 - <em>What is Nmap’s guess of the service name?</em><br>
>> <strong>irc</strong><br>
<p><br></p>

<h2>Task 6 - UDP Scan</h2>

<p>UDP is a connectionless protocol, and hence it does not require any handshake for connection establishment. We cannot guarantee that a service listening on a UDP port would respond to our packets. However, if a UDP packet is sent to a closed port, an ICMP port unreachable error (type 3, code 3) is returned. You can select UDP scan using the <code>-sU</code> option; moreover, you can combine it with another TCP scan.<br><br>

The following figure shows that if we send a UDP packet to an open UDP port, we cannot expect any reply in return. Therefore, sending a UDP packet to an open port won’t tell us anything..</p>

![image](https://github.com/user-attachments/assets/229abe82-a7b3-46d1-8e0b-c83a9fc197f8)

<p>However, as shown in the figure below, we expect to get an ICMP packet of type 3, destination unreachable, and code 3, port unreachable. In other words, the UDP ports that don’t generate any response are the ones that Nmap will state as open.</p>

![image](https://github.com/user-attachments/assets/e63cb762-90d2-451e-8c25-e8a4ecfe9768)

<p>In the Wireshark capture below, we can see that every closed port will generate an ICMP packet destination unreachable (port unreachable).</p>

![image](https://github.com/user-attachments/assets/d5f22b64-1324-4942-b1b8-62e17f475482)

<p>Launching a UDP scan against this Linux server proved valuable, and indeed, we learned that port 111 is open. On the other hand, Nmap cannot determine whether UDP port 68 is open or filtered.</p>

![image](https://github.com/user-attachments/assets/02221774-eec5-42c9-b455-5c4f20b17375)

<p><br></p>

> 6.1 - <em>Launch the VM. On the AttackBox, use the terminal to execute <code>nmap -sU -F -v 10.10.240.191</code>. A new service has been installed since the last scan. What is the UDP port that is now open?</em><br>
>> <strong>53</strong><br>

![image](https://github.com/user-attachments/assets/a3937acb-180d-4b4c-be2f-6aeb934ccbcf)

<p>I run twice and did not discover 53 port open.</p>

![image](https://github.com/user-attachments/assets/6028afda-83a2-499c-9302-1f76520b876a)

<p>Then I run the following command line instead <code>sudo nmap -sU 10.10.240.191. Also did not find port 52 open.<br>
And then I run nmap again as following .. guess what?  Also did not find port 53 open.</p>

![image](https://github.com/user-attachments/assets/5a2ace35-c1f1-4709-a183-4c375ee04a1e)

<p></p>

> 6.2 - <em>What is the service name according to Nmap?</em><br>
>> <strong>domain</strong><br>
<p><br></p>

<h2>Task 7 - Fine-Tuning Scope and Performance</h2>

<p>You can specify the ports you want to scan instead of the default 1000 ports. Specifying the ports is intuitive by now. Let’s see some examples:.<br>
<ul style="list-style-type:square;">
  <li>port list: <code>-p22,80,443</code>c will scan ports 22, 80 and 443.</li>
  <li>port range: <code>-p1-1023</code> will scan all ports between 1 and 1023 inclusive, while <code>-p20-25</code> will scan ports between 20 and 25 inclusive.</li>
</ul><br>
You can request the scan of all ports by using <code>-p-</code>, which will scan all 65535 ports. If you want to scan the most common 100 ports, add <code>-F</code>. Using <code>--top-ports 10</code>code> will check the ten most common ports.<br><br>

You can control the scan timing using <code>-T<0-5></code>. <code>-T0</code> is the slowest (paranoid), while <code>-T5</code> is the fastest. According to Nmap manual page, there are six templates:<br>
<ul style="list-style-type:square;">
  <li>paranoid (0)</li>
  <li>sneaky (1)</li>
  <li>polite (2)</li>
  <li>normal (3)</li>
      <li>polite (2)</li>
  <li>normal (3)</li>
</ul><br>
<p> To avoid IDS alerts, you might consider <code>-T0</code> or <code>-T1</code>. For instance, <code>-T0</code> scans one port at a time and waits 5 minutes between sending each probe, so you can guess how long scanning one target would take to finish. If you don’t specify any timing, Nmap uses normal <code>-T3</code>. Note that <code>-T5</code> is the most aggressive in terms of speed; however, this can affect the accuracy of the scan results due to the increased likelihood of packet loss. Note that <code>-T4</code> is often used during CTFs and when learning to scan on practice targets, whereas -T1 is often used during real engagements where stealth is more important.<br><br>

Alternatively, you can choose to control the packet rate using <code>--min-rate <number></code> and <code>--max-rate <number></code>. For example, <code>--max-rate 10</code> or <code>--max-rate=10</code> ensures that your scanner is not sending more than ten packets per second.<br><br>

Moreover, you can control probing parallelization using <code>--min-parallelism <numprobes></code> and <code>--max-parallelism <numprobes></code>. Nmap probes the targets to discover which hosts are live and which ports are open; probing parallelization specifies the number of such probes that can be run in parallel. For instance, <code>--min-parallelism=512</code> pushes Nmap to maintain at least 512 probes in parallel; these 512 probes are related to host discovery and open ports.</p>
<p><br></p>

> 7.1 - <em>What is the option to scan all the TCP ports between 5000 and 5500?</em><br>
>> <strong>-p-5000-5500</strong><br>

<p><br></p>

> 7.2 - <em>How can you ensure that Nmap will run at least 64 probes in parallel?</em><br>
>> <strong>--min-parallelism=64</strong><br>

<p><br></p>

> 7.3 - <em>What option would you add to make Nmap very slow and paranoid?</em><br>
>> <strong>-T0</strong><br>
<p><br></p>


<h2>Task 8 - Summary</h2>

<p>This room covered three types of scans.</p>

![image](https://github.com/user-attachments/assets/61254dac-fded-40fa-b68a-6d09757c16e8)

<p>These scan types should get you started discovering running TCP and UDP services on a target host.</p>

![image](https://github.com/user-attachments/assets/94de1145-0023-4382-9a3e-a9bf941ed8af)

<p></p>

> 8.1 - <em>Ensure you have taken note of all the scan options covered in this room. It is time to learn more advanced port scanning techniques by joining the <a href="https://tryhackme.com/r/room/nmap03">Nmap Advanced Port Scans</a> room.</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>

<h2>Room completed</h2>

![image](https://github.com/user-attachments/assets/9cc99fac-c925-4564-936b-ed231feb9a18)





