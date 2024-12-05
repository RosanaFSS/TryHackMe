<p align="center">December 5, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{213}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<p align="center"><img width="200px src="https://github.com/user-attachments/assets/87bfefb2-3a82-45ae-a685-941e80cf7917"></p>


<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Lookup}}$$
</h1>
<p align="center">Test your enumeration skills on this boot-to-root machine..</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/lookup">Lookup</a>.</p>
                                                              
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/2376cf84-25a4-43bb-92de-9968126ac191">
  <img width="900px" src="https://github.com/user-attachments/assets/17d98591-20c5-496e-a202-b95313ffcac6">
</p>

<br>



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
