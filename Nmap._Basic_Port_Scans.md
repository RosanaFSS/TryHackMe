<p><h3> Welcome to the <em>TryHackMe</em></h3>
<h1>Jr Penetration Tester learning path> Network Security</h1>
<h2>Nmaps Basic Port Scans</h2>
<p>Learn in-depth how nmap TCP connect scan, TCP SYN port scan, and UDP port scan work.</p>
<br>
October 20, 2024<br><br>
Type: Easy<br>
Link: https://tryhackme.com/r/room/nmap02</p>

![image](https://github.com/user-attachments/assets/4ef64337-781b-4c57-83cc-bb94140b8d5c)

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
</ol><br></p>

![image](https://github.com/user-attachments/assets/320e3fd4-3334-4107-b771-7db4dc694c61)

<p>The next step would be checking which ports are open and listening and which ports are closed. Therefore, in this room and the next one, we focus on port scanning and the different types of port scans used by <strong>nmap</strong>. This room explains:</p>
<ol type="1. ">
  <li>TCP connect port scan</li>
  <li>TCP SYN port scan</li>
  <li>UDP por scan</li>
</ol>

<p>Moreover, we discuss the different options to specify the ports, the scan rate, and the number of parallel probes.</p>
<p><br></p>

> 1.1 - <em>Launch the AttackBox by using the Start AttackBox button. You will launch different types of scans against the target VM to gain a solid knowledge of Nmap basic scan types.</em><br>
>> <strong>No answer needed</strong><br><br>
<p><br></p>

<h2>Task 2 - TCP and UDP ports</h2>

<p>In the same sense that an IP address specifies a host on a network among many others, <strong>a TCP port or UDP port is used to identify a network service running on that host</strong>.<br><br>

A server provides the network service, and it adheres to a specific network protocol. Examples include providing time, responding to DNS queries, and serving web pages. A port is usually linked to a service using that specific port number. For instance, an HTTP server would bind to TCP port 80 by default; moreover, if the HTTP server supports SSL/TLS, it would listen on TCP port 443. (TCP ports 80 and 443 are the default ports for HTTP and HTTPS; however, the webserver administrator might choose other port numbers if necessary.) Furthermore, no more than one service can listen on any TCP or UDP port (on the same IP address).<br><br>
At the risk of oversimplification, <strong>we can classify ports in two states</strong>:</p>
<ol type="1. ">
  <li>Open port indicates that there is some service listening on that port.</li>
  <li>Closed port indicates that there is no service listening on that port.</li>
</ol>
<p><br></p>
<p>However, in practical situations, we need to consider the impact of firewalls. For instance, a port might be open, but a firewall might be blocking the packets. Therefore, Nmap considers the following <strong>six states</strong>:</p>
<ol type="1. ">
  <li><strong>Open</strong>: indicates that a service is listening on the specified port.</li>
  <li><strong>Closed</strong>: indicates that no service is listening on the specified port, although the port is accessible. By accessible, we mean that it is reachable and is not blocked by a firewall or other security appliances/programs.</li>
</ol>
<p><br></p>



>> Performing Nmap I identified 3 ports open: 80/http, 3389/ssl, and 8080/http.<br>
>> <code>nmap -Pn -sC -sV -sS -p- -T4 10.10.30.67</code><br>


