<p align="center">October 30, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{177}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>
 
<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Anthem &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Exploit a Windows machine in this beginner level challenge.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/anthem">Anthem</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/3341c357-cc46-4547-ad4d-2eda43e5a114">
  <img height="150px" src="https://github.com/user-attachments/assets/7af381a4-a33e-4514-bb47-24ebc8b31290">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Website Analysis](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Spot the flags](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Final stage](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room complete](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#5)


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

<p>I wanted more details so I run a specific type of nmap, a very valuable one.</p>
<pre><code>$ nmap -Pn --script vuln [Target]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-30 23:05 GMT
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.015s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE
80/tcp   open  http
| _ http-aspnet-debug: ERROR: Script execution failed (use -d to debug)
|   http-csrf: 
|   Spidering limited to: maxdepth=3; maxpagecount=20; withinhost=ip-[Target].eu-west-1.compute.internal
|     Found the following possible CSRF vulnerabilities: 
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal:80/
|     Form id: 
|     Form action: /search
|      
|     Path: http://ip-[Target].eu-west-1.compute.internal/
|     Form id: 
|     Form action: /search
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal/archive/a-cheers-to-our-it-department/
|     Form id: 
|     Form action: /search
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal/search
|     Form id: 
|     Form action: /search
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal/archive/we-are-hiring/
|     Form id: 
|     Form action: /search
|      
|     Path: http://ip-[Target].eu-west-1.compute.internal/categories
|     Form id: 
|     Form action: /search
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal/tags
|     Form id: 
|     Form action: /search
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal/authors/jane-doe/
|     Form id: 
|     Form action: /search
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal/rss/{link}
|     Form id: 
|     Form action: /search
|     
|     Path: http://ip-[Target].eu-west-1.compute.internal/authors/jane-doe/THM{L0L_WH0_D15}
|     Form id: 
|     Form action: /search
| _ http-dombased-xss: Couldn't find any DOM based XSS.
| http-enum: 
|   /blog/: Blog
|   /rss/: RSS or Atom feed
|   /robots.txt: Robots file
|   /categories/viewcategory.aspx: MS Sharepoint
|   /categories/allcategories.aspx: MS Sharepoint
|   /authors/: Potentially interesting folder
|_  /search/: Potentially interesting folder
|_http-stored-xss: Couldn't find any stored XSS vulnerabilities.
3389/tcp open  ms-wbt-server
|_sslv2-drown: 
MAC Address: 02:27:A8:B9:66:9F (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 683.64 seconds
</code></pre><br>

> 1.2. <em>What port is for the web server?</em><br><a id='1.2'></a>
>> <code><strong>80</strong></code>
<p><br></p>

> 1.3. <em>What port is for remote desktop service?</em><br><a id='1.3'></a>
>> <code><strong>3389</strong></code><br>
<p><br></p>

> 1.4. <em>What is a possible password in one of the pages web crawlers check for?</em><br><a id='1.4'></a>
>> <code><strong>UmbracoIsTheBest!</strong></code><br>
<p></p>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/38936281-2570-4296-a009-cb5667601a6c"> </p>
<br>

> 1.5. <em>What CMS is the website using?</em><br><a id='1.5'></a>
>> <code><strong>Umbraco</strong></code><br>
<p></p>
<h4>Googling Umbraco I learned that it is an open-source management system (CMS) platform for publishing content on the World Wide Web and intranetes.</h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/08db55f3-3579-4b17-a790-b3fbb858bb94"> </p>
<br>

<h4>Decided to run another gobuster now that I now about Umbraco.</h4>
<pre><code>
Lorem Ypsum
</code></pre>


> 1.6. <em>What is the domain of the website?</em><br><a id='1.6'></a>
>> <code><strong>anthem.com</strong></code><br>
<p></p>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/4985f771-6aa7-42a1-8e7a-22b155630766"> </p>
<br>

> 1.7. <em>What's the name of the Administrator?</em><br><a id='1.7'></a>
>> <code><strong>Solomon Grundy</strong></code><br>
<p></p>
<h4 align="left"> $$\textcolor{white}{\textnormal{I run gobuster for directory enumeration.}}$$ </h4>
<pre><code>$gobuster dir -u http://[Target] -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target]
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
search               (Status: 200) [Size: 3414]
/blog                 (Status: 200) [Size: 5389]
/sitemap              (Status: 200) [Size: 1035]
/rss                  (Status: 200) [Size: 1869]
/archive              (Status: 301) [Size: 123] [--> /blog/]
/categories           (Status: 200) [Size: 3536]
/authors              (Status: 200) [Size: 4110]
/Search               (Status: 200) [Size: 3464]
/tags                 (Status: 200) [Size: 3589]
/install              (Status: 302) [Size: 126] [--> /umbraco/]
/RSS                  (Status: 200) [Size: 1869]
/Blog                 (Status: 200) [Size: 5389]
/Archive              (Status: 301) [Size: 123] [--> /blog/]
/SiteMap              (Status: 200) [Size: 1035]
/siteMap              (Status: 200) [Size: 1035]
/INSTALL              (Status: 302) [Size: 126] [--> /umbraco/]
/Sitemap              (Status: 200) [Size: 1035]
/1073                 (Status: 200) [Size: 5389]
/Rss                  (Status: 200) [Size: 1869]
/Categories           (Status: 200) [Size: 3536]
/1074                 (Status: 301) [Size: 123] [--> /blog/]
/*checkout*           (Status: 400) [Size: 3420]
/1078                 (Status: 200) [Size: 6192]
Progress: 7777 / 220561 (3.53%)[ERROR] Get "http://[Target]/1481": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
[ERROR] Get "http://[Target]/maryland": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
[ERROR] Get "http://[Target]/rhel": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
[ERROR] Get "http://[Target]/Website": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
[ERROR] Get "http://[Target]/Clothing": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
Progress: 7782 / 220561 (3.53%)[ERROR] Get "http://[Target]/new-york": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
[ERROR] Get "http://[Target]/nebraska": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
[ERROR] Get "http://[Target]/problem": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
Progress: 7785 / 220561 (3.53%)[ERROR] Get "http://[Target]/tennessee": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
[ERROR] Get "http://[Target]/nyt": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
/Authors              (Status: 200) [Size: 4110]
/1075                 (Status: 200) [Size: 4110]
/1079                 (Status: 200) [Size: 6252]
/1076                 (Status: 500) [Size: 3420]
/Install              (Status: 302) [Size: 126] [--> /umbraco/]
/*docroot*            (Status: 400) [Size: 3420]
/AUTHORS              (Status: 200) [Size: 4110]
/*                    (Status: 400) [Size: 3420]
Progress: 18058 / 220561 (8.19%)[ERROR] Get "http://[Target]/con": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
/SEARCH               (Status: 200) [Size: 3414]
/http%3A%2F%2Fwww     (Status: 400) [Size: 3420]
...
</code></pre>

<h4 align="left"> $$\textcolor{white}{\textnormal{Then I started researching by /archive.}}$$ </h4>
<h4 align="left"> $$\textcolor{#4575d6}{\textnormal{/archive/we-are-hiring/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/8af5b827-cabc-473a-bb03-9088c43fd807"> </p>
<h4 align="left"> $$\textcolor{#4575d6}{\textnormal{/archive/a-cheers-to-our-it-department/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/97651592-0142-4d65-ba48-77e54579ed1c"> </p>
<h4 align="left"> $$\textcolor{white}{\textnormal{Googling the poem, I found Solomon Grundy as its author.}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/f6d62594-e056-41e8-a20f-972e6e437bbc"> </p>
<p><br></p>

> 1.8. <em>Can we find the email address of the administrator?</em><br><a id='1.8'></a>
>> <code><strong>SD@anthem.com</strong></code><br>
<p></p>
<h4>Since Jane Doe´s email is JD@anthem.com I guessed that Solomon Grundy´s email is SG@anthem.com.  It worked!</h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/3e41245f-36d5-4b12-a02f-311654a07ab2"> </p>
<br>

<h2>Task 2. Spot the flags<a id='2'></a></h2>
<p>Our beloved admin left some flags behind that we require to gather before we proceed to the next task.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 2.1. <em>What is flag 1?</em><br><a id='2.1'></a>
>> <code><strong>THM{L0L_WH0_US3S_M3T4}</strong></code><br>
<p></p>
<h4 align="left"> $$\textcolor{#0cf0dd}{\textnormal{/archive/we-are-hiring/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/b60d8668-295c-429f-8cf4-35d44f3c0590"> </p>
<br>

> 2.2. <em>What is flag 2?</em><br><a id='2.2'></a>
>> <code><strong>THM{G!T_G00D}</strong></code><br>
<p></p>
<h4 align="left"> $$\textcolor{#0cf0dd}{\textnormal{/categories/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/ea5eeb4a-1b7f-4b5f-8f24-6cd64e57ca54"> </p>
<br>

> 2.3. <em>What is flag 3?</em><br><a id='2.3'></a>
>> <code><strong>THM{L0L_WH0_D15}</strong></code><br>
<p></p>
<h4 align="left"> $$\textcolor{#0cf0dd}{\textnormal{/authors/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/ce7b3313-7d54-48c1-99d6-6e1586c15b88"> </p>
<h4>We did not even need to access /authors/.  It was just take a glimpse in our second nmap and the answer was there.</h4>
<br>

> 2.4. <em>What is flag 4?</em><br><a id='2.4'></a>
>> <code><strong>THM{AN0TH3R_M3TA}</strong></code><br>
<p></p>
<h4 align="left"> $$\textcolor{#0cf0dd}{\textnormal{/archive/a-cheers-to-our-it-department/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/7132f4ca-e857-4039-a324-dd0809495fd8"> </p>
<br>

<h2>Task 3. Final stage<a id='3'></a></h2>
<p>Let's get into the box using the intel we gathered.</p>
<br>
<h4>Port 3389 is used to access Windows remotely through Rrmote Desktop Protocol (RDP).</h4>

<pre><code>$gobuster dir -u http://[Target] -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
</code></pre>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

<pre><code>$ cat /etc/hosts
...
[Target]     anthem.thm
...
</code></pre>

> 3.1. <em>Let's figure out the username and password to log in to the box.(The box is not on a domain)</em><br><a id='3.1'></a>
>> <code><strong>No answer needed</strong></code><br>
<p></p>

> 3.2. <em>Gain initial access to the machine, what is the contents of user.txt?</em><br><a id='3.2'></a>
>> <code><strong>THM{N00T_NO0T}</strong></code><br>
<p><br></p>

<h4>Using the credentials we discovered in Task 2, I got here ...</h4>

![image](https://github.com/user-attachments/assets/905df27e-9382-4186-93f4-8adf557b7915)

<h4>But ir was useless.  So I decided to use <code>rdesktop</code></h4>

<pre><code>$ apt-get install rdesktop
</code></pre>

<pre><code>$ rdesktop -u SG -p UmbracoIsTheBest! 10.10.201.104
Autoselected keyboard map en-gb
ERROR: CredSSP: Initialize failed, do you have correct kerberos tgt initialized ?
Connection established using SSL.
WARNING: Remote desktop does not support colour depth 24; falling back to 16
</code></pre>

![image](https://github.com/user-attachments/assets/b6e50e97-7cfe-43d6-9527-c4a438965403)

![image](https://github.com/user-attachments/assets/6bfa1f5d-42b4-461c-9dcf-4d94638fe513)

<br>

> 3.3. <em>Can we spot the admin password?</em><br><a id='3.3'></a>
>> <code><strong>ChangeMeBaby1MoreTime</strong></code><br>

![image](https://github.com/user-attachments/assets/40336db5-c60a-45f3-86d2-d27c6d44b074)

![image](https://github.com/user-attachments/assets/a1bb828c-98b4-4fa8-aa74-57214f8563ef)

![image](https://github.com/user-attachments/assets/b3158b9e-f984-4ffe-a5c4-c0680c1b2518)

![image](https://github.com/user-attachments/assets/dd7da222-652c-48a0-8fe7-85d6c7ef6f74)

![image](https://github.com/user-attachments/assets/5892086c-1257-46e1-a246-a81408719054)

![image](https://github.com/user-attachments/assets/f2bc822f-8073-4df6-9a1b-60d4c457e78a)

![image](https://github.com/user-attachments/assets/9ef2ac45-b106-4cc7-8812-ccbed711c793)


<p><br></p>

> 3.4. <em>Escalate your privileges to root, what is the contents of root.txt?</em><br><a id='3.4'></a>
>> <code><strong>THM{Y0U_4R3_1337}</strong></code><br>
<p><br></p>

![image](https://github.com/user-attachments/assets/f60c3810-a945-4992-83af-a8849467f441)

![image](https://github.com/user-attachments/assets/ef9fd12d-b5bf-4050-aafb-82dab938f7cf)


<h2>Room Complete<a id='4'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/b87ba565-47ee-4919-a81f-7db32ff5b56e)

<h2>My Journey<a id='5'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

![image](https://github.com/user-attachments/assets/2bcd9e83-e381-438e-ade2-d7a9c0fe5e9c)

<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
