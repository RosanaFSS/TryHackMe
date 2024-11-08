<p align="center">November 7, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{185}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TryHack3M: Subscribe &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Can you help Hack3M reach 3M subscribers?</p>
<p align="center">Access this TryHackMe Room clicking <a href="https://tryhackme.com/r/room/subscribe">TryHack3M: Subscribe</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/6cdf59cf-c516-48a5-882d-2e065f1afd28">
  <img height="150px" src="https://github.com/user-attachments/assets/b2505fa7-11f9-47bd-b32c-4e75bac1da1e">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Storyline](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Exploitation](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Detection](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Conclusion](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room Complete](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My Journey](#6)

<br>
<br>
<br>
<h2>Task 1. Storyline<a id='1'></a></h2>
<h3>Incident Storyline</h3>

<p>We have good news and bad news! The good news is that we are about to hit 3 million users on our platform, and the bad news is;<br>

Well, last night, the UnderGround (UG) Hackers attacked our website, <code>hackme.thm</code>, and took complete control. They were able to turn off the signup page, so there won't be any new registrations. Given this, our user count is stuck at <code>2.99 Million</code>.<br>
Can you help us restore the registration panel on our site to reach our 3 million user milestone?</p>

<p align="center">
  <img width="750px" src="https://github.com/user-attachments/assets/fb37b395-5715-491c-b9d5-6afebec6e2c1">
</p>

<h3>Room Objectives</h3>

<ul style="list-style-type:square">
    <li>Explore the web server and find the attack vectors leveraged by the attacker.</li>
    <li>Regain access and restore the signup functionality for the new users.</li>
    <li>Investigate the web application logs and track down the root cause.</li>
</ul></p>

<h3>Lab Connection</h3>
<p>Before moving forward, start the lab by clicking the <code>Start Machine</code> button. It will take 3-5 minutes to load properly.<br>

We can't wait to get our site restored and resume our 3M celebrations!<br>
Good luck!</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 1.1. <em>I have successfully started the machine.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<h2>Task 2. Exploitation<a id='2'></a></h2>
<p><em>Sometimes, the attacker leaves footprints that allow you to regain access to the server.  Can you help HackM3 restore server access and get 3M subscribers?</em></p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 2.1. <em>What is the invite code for the hackme.thm website?</em><br><a id='2.1'></a>
>> <code><strong>VkXgo:Invited30MnUsers</strong></code>

<br>

<h3><em>Reconnaissance</em></h3>

<pre><code>:~~/subscribe# nano /etc/hosts
</code></pre>

<p>Let´s start with a Nmap scan.<br><br>
We will find six ports open: 22, 80, 8000, 8089, 8191 and 40009.</p>

<pre><code>root@ip-[Attack_IP]:~/subscribe# nmap -p- [Target_IP] -T4

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-08 00:18 GMT
Nmap scan report for subscribe.thm ([Target_IP])
Host is up (0.00060s latency).
Not shown: 65529 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
8000/tcp  open  http-alt
8089/tcp  open  unknown
8191/tcp  open  limnerpressure
40009/tcp open  unknown
MAC Address: 02:F4:54:9A:1F:AF (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 1301.84 seconds
</code></pre>

<p>Next let´s run a Nmap service and script scan.<br>
We will find the following [port open] [service] [version]:</p>

<ul style="list-style-type:square">
    <li>[22] [ssh][OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)]</li>
    <li>[80] [http] [Apache httpd 2.4.41 ((Ubuntu))]</li>
    <li>[8000] [http] [Splunkd httpd]</li>
    <li>[8089] [http] [SSplunkd httpd (free license; remote login disabled)]</li>
    <li>[8191] [tcp] [limnerpressure?]</li>
    <li>[40009] [http] [Apache httpd 2.4.41]</li>
</ul></p>

<pre><code>root@ip-[Attack_IP]:~/subscribe# nmap -sC -sV -p22,80,8000,8089,8191,40009 [Target_IP] -T4

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-08 00:36 GMT
Nmap scan report for subscribe.thm ([Target_IP])
Host is up (0.00035s latency).

PORT      STATE SERVICE         VERSION
22/tcp    open  ssh             OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp    open  http            Apache httpd 2.4.41 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Hack3M | Cyber Security Training
8000/tcp  open  http            Splunkd httpd
| http-robots.txt: 1 disallowed entry 
|_/
|_http-server-header: Splunkd
| http-title: Site doesn't have a title (text/html; charset=UTF-8).
|_Requested resource was http://subscribe.thm:8000/en-US/account/login?return_to=%2Fen-US%2F
8089/tcp  open  ssl/http        Splunkd httpd (free license; remote login disabled)
| http-auth: 
| HTTP/1.1 401 Unauthorized\x0D
|_  Server returned status 401 but no WWW-Authenticate header.
|_http-server-header: Splunkd
|_http-title: Site doesn't have a title (text/xml; charset=UTF-8).
| ssl-cert: Subject: commonName=SplunkServerDefaultCert/organizationName=SplunkUser
| Not valid before: 2024-04-05T11:00:59
|_Not valid after:  2027-04-05T11:00:59
8191/tcp  open  limnerpressure?
| fingerprint-strings: 
|   FourOhFourRequest, GetRequest: 
|     HTTP/1.0 200 OK
|     Connection: close
|     Content-Type: text/plain
|     Content-Length: 85
|_    looks like you are trying to access MongoDB over HTTP on the native driver port.
40009/tcp open  http            Apache httpd 2.4.41
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: 403 Forbidden
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
...
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 57.61 seconds
</code></pre>

<br>
<p>Accessing our Target Machine on port 80 we find a sing-up page.  Registration is disabled.</p>

![image](https://github.com/user-attachments/assets/67fdce5f-5be8-460d-810e-b4a27a5de72b)

<br>
<p>Visualizing the source code we find information about the <code>Invite Code</code>.</p>


<pre><code><script src="/js/invite.js"></script> </code></pre>

![image](https://github.com/user-attachments/assets/96349aeb-7be6-4a8f-b694-0a00a643db9b)

![image](https://github.com/user-attachments/assets/effa6238-f3dc-440a-af35-64098c0f88ff)

<br>
<p>Visiting <code>[Target_IP]/js/invite.js</code> we find some code.</p>

![image](https://github.com/user-attachments/assets/d4222e3e-94af-48c4-af3e-54da9be90420)

<br>
<p>I used <a href="https://beautifier.io/">Beuatifier.io</a>.</p>

<p align="center"> <img width="400x" src="https://github.com/user-attachments/assets/84cd2deb-4d23-48fd-a16e-68706af9fee2"> </p>

<pre><code>
function e() {
    var e = window.location.hostname;
    if (e === "capture3millionsubscribers.thm") {
        var o = new XMLHttpRequest;
        o.open("POST", "inviteCode1337HM.php", true);
        o.onload = function() {
            if (this.status == 200) {
                console.log("Invite Code:", this.responseText)
            } else {
                console.error("Error fetching invite code.")
            }
        };
        o.send()
    } else if (e === "hackme.thm") {
        console.log("This function does not operate on hackme.thm")
    } else {
        console.log("Lol!! Are you smart enought to get the invite code?")
    }
}
</code></pre>


> 2.2. <em>What is the password for the user guest@hackme.thm?</em><br><a id='2.2'></a>
>> <code><strong>wedidit1010</strong></code>

<br>

> 2.3. <em>What is the secure token for accessing the admin panel?</em><br><a id='2.3'></a>
>> <code><strong>______________________</strong></code>

<br>

> 2.4. <em>What is the flag value after enabling the registration feature and getting 3M subscribers on the platform?</em><br><a id='2.4'></a>
>> <code><strong>______________________</strong></code>

<br>

<h2>Task 3. Detection<a id='3'></a></h2>
<h3>Investigating the Attack</h3>
<p>Our security department detected an alert about a web attack on the 4th of April, 2024. They have ingested the logs into Splunk, which can be accessed using the following credentials:</p>

<p align="center">
  <img width="300px" src="https://github.com/user-attachments/assets/94b1b4c9-b911-4639-b3af-0ee46473f2e9">
</p>

<br>

<p align="center">
  <img width="750px" src="https://github.com/user-attachments/assets/53e89b2e-b665-4f36-9fe7-a637d50c83b5">
</p>

<br>
<p>Your task is to analyse the logs and track the attacker's footprints.<br>

Good luck.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 3.1. <em>How many logs are ingested in the Splunk instance?</em><br><a id='3.1'></a>
>> <code><strong>______________</strong></code>

<br>

> 3.2. <em>What is the web hacking tool used by the attacker to exploit the vulnerability on the website?</em><br><a id='3.2'></a>
>> <code><strong>______________</strong></code>

<br>

> 3.3. <em>How many total events were observed related to the attack?</em><br><a id='3.3'></a>
>> <code><strong>______________</strong></code>

<br>

> 3.4. <em>What is the observed IP address of the attacker?</em><br><a id='3.4'></a>
>> <code><strong>______________</strong></code>

<br>

> 3.5. <em>How many events were observed from the attacker's IP?</em><br><a id='3.5'></a>
>> <code><strong>______________</strong></code>

<br>

> 3.6. <em>What is the table used by the attacker to execute the attack?</em><br><a id='3.6'></a>
>> <code><strong>______________</strong></code>

<br>

<h2>Task 4. Conclusion<a id='4'></a></h2>
<br>
<p>Congratulations on making it this far! You have clearly completed the challenge and helped HackM3 reach 3M subscribers. We are thrilled that you've had the opportunity to learn some fascinating exploitation techniques while gaining valuable detection insights for this kind of attack. Keep up the great work!<br>

Let us know your thoughts on this room on our <a href="https://discord.com/invite/tryhackme">Discord channel</a> or <a href="https://x.com/realtryhackme">X account</a>. See you around.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>

> 4.1. <em>I have successfully completed the room.</em><br><a id='4.1'></a>
>> <code><strong>No answer needed</code>

<br>

<h2>Room Complete<a id='5'></a></h2>
<p>Keep learning, keep growing!<br>



<h2>My Journey<a id='6'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 7, 2024  | 185      |       1,286ª |          28ª |      4,298ª |        60ª | 53,942   |       405 |


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
