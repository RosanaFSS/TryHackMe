<p align="center">December 5, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{213}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<p align="center"> <img width="300px" src="https://github.com/user-attachments/assets/87bfefb2-3a82-45ae-a685-941e80cf7917"></p>


<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{ToolsRus}}$$
</h1>
<p align="center">Practise using tools such as dirbuster, hydra, nmap, nikto and metasploit</p>
<p align="center">Access this TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/toolsrus">Lookup</a>.</p>
<p align="center">Note tat only subscribers can deploy virtual machines in this room.</p>

                                                              
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/dac4e4d6-5e6f-4a31-af37-ce5e784700f4">
  <img width="900px" src="https://github.com/user-attachments/assets/9a173985-757f-4dc9-9b61-f47f599a84a8">
</p>

<br>

<h2>Task 1. Deploy and get hacking<a id='1'></a></h2>

> 1.1. <em>What directory can you find, that begins with a "g"?</em><br><a id='1.1'></a>
>> <strong>guidelines</strong><br>
<p><br></p>

<h3><strong>Gobuster</strong></h3>

<pre><code>oot@ip-[THM AttackBox]:~/ToolsRus# gobuster dir -u http://[Target]/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target]/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/guidelines           (Status: 301) [Size: 315] [--> http://[Target]/guidelines/]
/protected            (Status: 401) [Size: 458]
Progress: 87664 / 87665 (100.00%)
===============================================================
Finished
===============================================================
</code></pre>

<br>
<br>

> 1.2. <em>Whose name can you find from this directory?</em><br><a id='1.2'></a>
>> <strong>bob</strong><br>
<p><br></p>

![image](https://github.com/user-attachments/assets/fea45692-c4fd-46f6-b897-712ed62ea7d4)

<br>
<br>


> 1.3. <em>What directory has basic authentication?</em><br><a id='1.3'></a>
>> <strong>protected</strong><br>
<p><br></p>

<h3><strong>Gobuster</strong></h3>

<pre><code>oot@ip-[THM AttackBox]:~/ToolsRus# gobuster dir -u http://[Target]/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target]/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/guidelines           (Status: 301) [Size: 315] [--> http://[Target]/guidelines/]
/protected            (Status: 401) [Size: 458]
Progress: 87664 / 87665 (100.00%)
===============================================================
Finished
===============================================================
</code></pre>

<br>
<br>

> 1.4. <em>What is bob's password to the protected part of the website?</em><br><a id='1.4'></a>
>> <strong>bubbles</strong><br>
<p><br></p>

<br>

![image](https://github.com/user-attachments/assets/c142d908-fc47-4407-a88a-01918c9ce7a4)

<br>

![image](https://github.com/user-attachments/assets/5593ce7f-1a62-4d5d-8d34-7d3204b29acf)

<br>

> 1.5. <em>What other port that serves a webs service is open on the machine?</em><br><a id='1.5'></a>
>> <strong>1234</strong><br>
<p><br></p>

<p>check Nmap</p>

<br>

> 1.6. <em>What is the name and version of the software running on the port from question 5?</em><br><a id='1.6'></a>
>> <strong>Apache Tomcat/7.0.88</strong><br>
<p><br></p>

<br>

![image](https://github.com/user-attachments/assets/b3d7fa2f-e09a-4fdf-af5b-7d8c2cdae079)

<br>

> 1.7. <em>Use Nikto with the credentials you have found and scan the /manager/html directory on the port found above. How many documentation files did Nikto identify?</em><br><a id='1.7'></a>
>> <strong>____</strong><br>
<p><br></p>




<h3><strong>Nmap</strong></h3>

<pre><code>oot@[THM AttackBox]:~/ToolsRus# nmap -Pn --script vuln [Target]
Starting Nmap 7.80 ( https://nmap.org ) at 2024-12-05 04:24 GMT
Pre-scan script results:
| broadcast-avahi-dos: 
|   Discovered hosts:
|     [Redacted]
|   After NULL UDP avahi packet DoS (CVE-2011-1002).
|_  Hosts are all up (not vulnerable).
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.00027s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
|_clamav-exec: ERROR: Script execution failed (use -d to debug)
80/tcp   open  http
|_clamav-exec: ERROR: Script execution failed (use -d to debug)
|_http-csrf: Couldn't find any CSRF vulnerabilities.
|_http-dombased-xss: Couldn't find any DOM based XSS.
| http-enum: 
|_  /protected/: Potentially interesting folder (401 Unauthorized)
| http-slowloris-check: 
|   VULNERABLE:
|   Slowloris DOS attack
|     State: LIKELY VULNERABLE
|     IDs:  CVE:CVE-2007-6750
|       Slowloris tries to keep many connections to the target web server open and hold
|       them open as long as possible.  It accomplishes this by opening connections to
|       the target web server and sending a partial request. By doing so, it starves
|       the http server's resources causing Denial Of Service.
|       
|     Disclosure date: 2009-09-17
|     References:
|       http://ha.ckers.org/slowloris/
|_      https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6750
|_http-stored-xss: Couldn't find any stored XSS vulnerabilities.
1234/tcp open  hotline
|_clamav-exec: ERROR: Script execution failed (use -d to debug)
8009/tcp open  ajp13
|_clamav-exec: ERROR: Script execution failed (use -d to debug)
MAC Address: 02:CB:20:AD:D4:FD (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 346.53 seconds
</code></pre>

<br>



![image](https://github.com/user-attachments/assets/f5689d66-904d-4b4d-a8c8-7ebceb67812f)

<br>


![image](https://github.com/user-attachments/assets/b3d7fa2f-e09a-4fdf-af5b-7d8c2cdae079)



