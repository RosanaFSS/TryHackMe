<h3> Welcome to the <em>TryHackMe ...</em></h3>
<h1>Learn</h1>
<h2>Agent Sudo</h2>
<p>You found a secret server located under the deep sea. Your task is to hack inside the server and reveal the truth.</p>
<p>October 20, 2024<br></p>

<div style="display: flex; justify-content: center; align-items: center;">
    <img src="https://github.com/user-attachments/assets/e78f69eb-2323-47d4-9684-7b478c5d8041" width="150px" height="150px"/>
</div>
<br>

![image](https://github.com/user-attachments/assets/119bac7c-5666-4044-a539-528b6ddaea64)

<p>Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure. TryHackMe classified this CTF as Easy. It´s key part of my 166-day-streak. Let´s get started!!<br><br>
Access this TryHackMe Room clicking <a href="https://tryhackme.com/r/room/agentsudoctf)">Agent Sudo</a></p>

<h2>Task 1 - IAuthor note</h2>

<p>Welcome to another THM exclusive CTF room. Your task is simple, capture the flags just like the other CTF room. Have Fun!<br><br>

If you are stuck inside the black hole, post on the forum or ask in the TryHackMe discord.<br>

> 1.1 - <em>Deploy the machine.</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>

<h2>Task 2 - Enumerate</h2>

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
