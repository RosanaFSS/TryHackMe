<p align="left">November 6, 2024 - Hey there, fellow lifelong learner!<br>
I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure. It´s part of my $$\textcolor{#FF69B4}{\textbf{184}}$$-day-streak in  <a href="https://tryhackme.com/r/p/Rosana">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp; CTF collection Vol.2}}$$
</h1>

<p align="center">Sharpening up your CTF skill with the collection. The second volume is about web-based CTF.<br>
                  Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/ctfcollectionvol2">CTF collection VOl.2</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/6628e1a4-ea67-4e69-b719-702b2fc07e4c">
  <img height="150px" src="https://github.com/user-attachments/assets/88772c45-e475-4d0a-a8cb-c1c1440725d7">
</p>

<h2>Task 1 - Author note</h2>

<p>Welcome, welcome and welcome to another CTF collection. This is the second installment of the CTF collection series. For your information, the second serious focuses on the web-based challenge. There are a total of 20 easter eggs a.k.a flags can be found within the box. Let see how good is your CTF skill.<br>

Now, deploy the machine and collect the eggs!</p>

<p>Warning: The challenge contains seizure images and background. If you feeling uncomfortable, try removing the background on <style> tag.</p>

Note: All the challenges flag are formatted as THM{flag}, unless stated otherwise</p>

<pre><code>$ rustscan -a 10.10.157.196 -- -sV
.----. .-. .-. .----..---.  .----. .---.   .--.  .-. .-.
| {}  }| { } |{ {__ {_   _}{ {__  /  ___} / {} \ |  `| |
| .-. \| {_} |.-._} } | |  .-._} }\     }/  /\  \| |\  |
`-' `-'`-----'`----'  `-'  `----'  `---' `-'  `-'`-' `-'
The Modern Day Port Scanner.
________________________________________
: https://discord.gg/GFrQsGy           :
: https://github.com/RustScan/RustScan :
 --------------------------------------
\U0001f30dHACK THE PLANET\U0001f30d

[~] The config file is expected to be at "/home/rustscan/.rustscan.toml"
[~] File limit higher than batch size. Can increase speed by increasing batch size '-b 1048476'.
Open 10.10.157.196:22
Open 10.10.157.196:80
[~] Starting Script(s)
[>] Script to be run Some("nmap -vvv -p {{port}} {{ip}}")

[~] Starting Nmap 7.80 ( https://nmap.org ) at 2024-11-06 21:27 UTC
NSE: Loaded 45 scripts for scanning.
Initiating Ping Scan at 21:27
Scanning 10.10.157.196 [2 ports]
Completed Ping Scan at 21:27, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 21:27
Completed Parallel DNS resolution of 1 host. at 21:27, 0.00s elapsed
DNS resolution of 1 IPs took 0.00s. Mode: Async [#: 1, OK: 1, NX: 0, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 21:27
Scanning ip-10-10-157-196.eu-west-1.compute.internal (10.10.157.196) [2 ports]
Discovered open port 80/tcp on 10.10.157.196
Discovered open port 22/tcp on 10.10.157.196
Completed Connect Scan at 21:27, 0.00s elapsed (2 total ports)
Initiating Service scan at 21:27
Scanning 2 services on ip-10-10-157-196.eu-west-1.compute.internal (10.10.157.196)
Completed Service scan at 21:28, 6.09s elapsed (2 services on 1 host)
NSE: Script scanning 10.10.157.196.
  SE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 21:28
Completed NSE at 21:28, 0.03s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 21:28
Completed NSE at 21:28, 0.04s elapsed
Nmap scan report for ip-10-10-157-196.eu-west-1.compute.internal (10.10.157.196)
Host is up, received syn-ack (0.00050s latency).
Scanned at 2024-11-06 21:27:53 UTC for 7s

PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    syn-ack Apache httpd 2.2.22 ((Ubuntu))
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 7.01 seconds
</code></pre>

![image](https://github.com/user-attachments/assets/7cf7a060-19c7-4740-9d08-d7c85c32c93f)

<pre><code>root@ip-10-10-146-248:~# gobuster dir -u http://10.10.157.196 -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.157.196
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/login                (Status: 301) [Size: 314] [--> http://10.10.157.196/login/]
/index                (Status: 200) [Size: 94328]
/button               (Status: 200) [Size: 39148]
/static               (Status: 200) [Size: 253890]
/cat                  (Status: 200) [Size: 62048]
/small                (Status: 200) [Size: 689]
/who                  (Status: 200) [Size: 3847428]
/robots               (Status: 200) [Size: 430]
/iphone               (Status: 200) [Size: 19867]
/game1                (Status: 301) [Size: 314] [--> http://10.10.157.196/game1/]
/egg                  (Status: 200) [Size: 25557]
/dinner               (Status: 200) [Size: 1264533]
/ty                   (Status: 200) [Size: 198518]
/ready                (Status: 301) [Size: 314] [--> http://10.10.157.196/ready/]
/saw                  (Status: 200) [Size: 156274]
/game2                (Status: 301) [Size: 314] [--> http://10.10.157.196/game2/]
/wel                  (Status: 200) [Size: 155758]
/free_sub             (Status: 301) [Size: 317] [--> http://10.10.157.196/free_sub/]
/nicole               (Status: 200) [Size: 367650]
/server-status        (Status: 403) [Size: 294]
Progress: 135446 / 220561 (61.41%)^C
[!] Keyboard interrupt detected, terminating.
Progress: 136330 / 220561 (61.81%)
===============================================================
Finished
===============================================================
root@ip-10-10-146-248:~# 
</code></pre>


> 1.1 - <em>Fact: Eggs contain the highest quality protein you can buy.</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>



<h2>Task 2 - Easter egg</h2>

<p>Submit all your easter egg right here. Gonna find it all!</p>

> 2.1 - <em>Easter 1</em><br>
>> <strong>THM{4u70b07_r0ll_0u7}</strong><br>
<p></p>

![image](https://github.com/user-attachments/assets/80d5876a-803a-4afe-be31-e0c21c0004ad)

![image](https://github.com/user-attachments/assets/710449d5-e0fa-4547-873a-d689be15fc48)

<br>

> 2.2 - <em>Easter 2</em><br>
>> <strong>THM{f4ll3n_b453}</strong><br>
<p><br></p>

> 2.3 - <em>Easter 3</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.4 - <em>Easter 4</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.5 - <em>Easter 5</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.6 - <em>Easter 6</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.7 - <em>Easter 7</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.8 - <em>Easter 8</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.9 - <em>Easter 9</em><br>
>> <strong>______</strong><br>
<p><br></p>

> .2.10 - <em>Easter 10</em><br>
>> <strong>______</strong><br>
<p><br></p>






