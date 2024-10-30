<p align="center">October 30, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{177}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Anthem &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Exploit a Windows machine in this beginner level challenge.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/anthem">Anthem</a>.</p><br>
<p align="center">
  <img height="160px" hspace="20" src="https://github.com/user-attachments/assets/3341c357-cc46-4547-ad4d-2eda43e5a114">
  <img height="160px" src="https://github.com/user-attachments/assets/7a56d2ff-2477-4574-a13b-4e40a4fb849c">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Website Analysis](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [User flag](#1.1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Root flag](#1.2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room complete](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#3)


<h2>Task 1. Website Analysis<a id='1'></a></h2>

<br>
<p align="center">This task involves you, paying attention to details and finding the 'keys to the castle'.<br>
This room is designed for beginners, however, everyone is welcomed to try it out!<br>
Enjoy the Anthem.<br>
In this room, you don't need to brute force any login page. Just your preferred browser and Remote Desktop.<br>
Please give the box up to 5 minutes to boot and configure.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>
> 1.1. <em>Let's run nmap and check what ports are open.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code><br><br>
<p>There are two ports open: 80/http and 3389/ms-wbt-server</p>
<pre><code>$ nmap -sS -sV -A [Target]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-30 20:53 GMT
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.020s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| ssl-cert: Subject: commonName=WIN-LU09299160F
| Not valid before: 2024-10-29T20:21:13
|_Not valid after:  2025-04-30T20:21:13
|_ssl-date: 2024-10-30T20:54:17+00:00; 0s from scanner time.
MAC Address: 02:27:A8:B9:66:9F (Unknown)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: specialized
Running (JUST GUESSING): AVtech embedded (87%)
Aggressive OS guesses: AVtech Room Alert 26W environmental monitor (87%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE
HOP RTT      ADDRESS
1   19.74 ms ip-[Target].eu-west-1.compute.internal ([Target])

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 115.65 seconds
</code></pre><br>

> 1.2. <em>What port is for the web server?</em><br><a id='1.2'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 1.3. <em>What port is for remote desktop service?</em><br><a id='1.3'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 1.4. <em>What is a possible password in one of the pages web crawlers check for?</em><br><a id='1.4'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 1.5. <em>What CMS is the website using?</em><br><a id='1.5'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 1.6. <em>What is the domain of the website?</em><br><a id='1.6'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 1.7. <em>What's the name of the Administrator?</em><br><a id='1.7'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 1.8. <em>Can we find find the email address of the administrator?</em><br><a id='1.8'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

<h2>Task 2. Spot the flags<a id='2'></a></h2>
<p>Our beloved admin left some flags behind that we require to gather before we proceed to the next task.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 2.1. <em>What is flag 1?</em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code><br>
<p><br></p>

> 2.2. <em>What is flag 2?</em><br><a id='2.2'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 2.3. <em>What is flag 3?</em><br><a id='2.3'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 2.4. <em>What is flag 4?</em><br><a id='2.4'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>


<h2>Task 3. Final stage<a id='3'></a></h2>
<p>Let's get into the box using the intel we gathered.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 3.1. <em>What is flag 1?</em><br><a id='3.1'></a>
>> <code><strong>No answer needed</strong></code><br>
<p><br></p>

> 3.2. <em>What is flag 2?</em><br><a id='3.2'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 3.3. <em>What is flag 3?</em><br><a id='3.3'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>

> 3.4. <em>What is flag 4?</em><br><a id='3.4'></a>
>> <code><strong>____________</strong></code><br>
<p><br></p>





<pre><code>
Lorem Ypsum
</code></pre>



<h2>Room Complete<a id='4'></a></h2>
<p>Keep learning, keep growing!<br>




<h2>My Journey<a id='5'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>



<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
