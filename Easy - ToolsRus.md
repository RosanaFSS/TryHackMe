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
  <img width="700px" src="https://github.com/user-attachments/assets/5927c511-20c2-4006-84ea-8034eb8d3173">
</p>

<br>

<h2>Task 1. Deploy and get hacking<a id='1'></a></h2>

> 1.1. <em>What directory can you find, that begins with a "g"?</em><br><a id='1.1'></a>
>> <strong>guidelines</strong><br>
<p><br></p>

<h3><strong>Gobuster</strong></h3>

<pre><code>root@ip-[THM AttackBox]:~/ToolsRus# gobuster dir -u http://[Target]/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
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

<pre><code>root@ip-[THM AttackBox]:~/ToolsRus# gobuster dir -u http://[Target]/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
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

![image](https://github.com/user-attachments/assets/b3d7fa2f-e09a-4fdf-af5b-7d8c2cdae079)

<br>

> 1.7. <em>Use Nikto with the credentials you have found and scan the /manager/html directory on the port found above. How many documentation files did Nikto identify?</em><br><a id='1.7'></a>
>> <strong>5</strong><br>
<p><br></p>


![image](https://github.com/user-attachments/assets/281d61bf-f022-4f06-97d1-ad24a52b6de5)



<h3><strong>Nmap</strong></h3>

<pre><code>root@[THM AttackBox]:~/ToolsRus# nmap -Pn --script vuln [Target]
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

<br>

![image](https://github.com/user-attachments/assets/d2e79e8b-edee-4bae-bc23-299f5b69a43a)


<br>

![image](https://github.com/user-attachments/assets/b7a118fa-8cf5-435b-97c4-68b618ffe9b6)

<br>

![image](https://github.com/user-attachments/assets/f8e460ab-90ce-411e-ba95-3b519910689f)


<br>

> 1.8. <em>What is the server version?</em><br><a id='1.8'></a>
>> <strong>Apache/2.4.18</strong><br>
<p><br></p>

![image](https://github.com/user-attachments/assets/d52eb656-c078-473a-a948-56732ff21309)


> 1.9. <em>What version of Apache-Coyote is this service using?</em><br><a id='1.9'></a>
>> <strong>1.1</strong><br>
<p><br></p>


![image](https://github.com/user-attachments/assets/54108b8c-fc88-4bf6-af13-e95dfc607684)

> 1.10. <em>Use Metasploit to exploit the service and get a shell on the system. What user did you get a shell as?</em><br><a id='1.10'></a>
>> <strong>root</strong><br>
<p><br></p>

<br>

<pre><code>root@[THM AttackBox]:~/ToolsRus# msfconsole
Metasploit tip: Use sessions -1 to interact with the last opened session
                                                  
     ,           ,
    /             \
   ((__---,,,---__))
      (_) O O (_)_________
         \ _ /            |\
          o_o \   M S F   | \
               \   _____  |  *
                |||   WW|||
                |||     |||


       =[ metasploit v6.4.38-dev-                         ]
+ -- --=[ 2460 exploits - 1266 auxiliary - 430 post       ]
+ -- --=[ 1468 payloads - 49 encoders - 11 nops           ]
+ -- --=[ 9 evasion                                       ]

Metasploit Documentation: https://docs.metasploit.com/

msf6 >
</code></pre>

<br>

<pre><code>
msf6 > search tomcat
  
Matching Modules
================

   #   Name                                                                       Disclosure Date  Rank       Check  Description
   -   ----                                                                       ---------------  ----       -----  -----------
   0   auxiliary/dos/http/apache_commons_fileupload_dos                           2014-02-06       normal     No     Apache Commons FileUpload and Apache Tomcat DoS
...
  
</code></pre>

> 1.11. <em>What flag is found in the root directory?</em><br><a id='1.11'></a>
>> <strong>root</strong><br>
<p><br></p>





<h2>Room Completed<a id='4'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/34b60717-7eb8-4df8-aa36-7aae437ddd46)


<h2>My Journey<a id='5'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 5, 2024  | 213      |     1,032 nd |        22 nd |    2,610 th |      35 th | 59,272   |       453 |



<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>

![image](https://github.com/user-attachments/assets/18b1b189-b852-40f1-b7a8-18b4d73392d6)
