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
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/3e41245f-36d5-4b12-a02f-311654a07ab2"> </p>
<h4 align="left"> $$\textcolor{white}{\textnormal{Since Jane Doe´s email is JD@anthem.com I guessed that Solomon Grundy´s email is SG@anthem.com.  It worked!}}$$ </h4>


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
>> <code><strong>____________</strong></code><br>
<p><br></p>
<h4 align="left"> $$\textcolor{#0cf0dd}{\textnormal{/authors/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/ce7b3313-7d54-48c1-99d6-6e1586c15b88"> </p>
<br>

> 2.4. <em>What is flag 4?</em><br><a id='2.4'></a>
>> <code><strong>THM{AN0TH3R_M3TA}</strong></code><br>
<p></p>
<h4 align="left"> $$\textcolor{#0cf0dd}{\textnormal{/archive/a-cheers-to-our-it-department/}}$$ </h4>
<p align="left"> <img width="700px" src="https://github.com/user-attachments/assets/7132f4ca-e857-4039-a324-dd0809495fd8"> </p>
<br>

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
