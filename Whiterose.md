<p align="center">November 1, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{179}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Whiterose &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Yet another Mr. Robot themed challenge.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/whiterose">Whiterose</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/88ac3eb9-f35d-40c1-8257-142e1d609ee4">
  <img height="150px" src="https://github.com/user-attachments/assets/425d878f-2071-4ff1-bc3a-5ececfcc53ae">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Welcome!](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Spot the flags](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Final stage](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room complete](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#5)


<h2>Task 1. Welcome!<a id='1'></a></h2>
<h3>Welcome to Whiterose</h3>
<p>This challenge is based on the Mr. Robot episode "409 Conflict". Contains spoilers!<br>
Go ahead and start the machine, <strong>it may take a few minutes to fully start up</strong>.<br>
And oh! I almost forgot! - You will need these: <code>Olivia Cortez:olivi8</code></p>

![image](https://github.com/user-attachments/assets/11555e82-c3a7-4fa2-a9ee-07718afb0599)

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
> 1.1. <em>What's Tyrell Wellick's phone number?</em><br><a id='1.1'></a>

<h2 align="left"> $$\textcolor{#e691c9}{\textbf{Olivia Cortez:olivi8}}$$</h2>

<p>Running Nmap I found ports 22/ssh and 80/http open.</p>

<pre><code>$ nmap -sC -sV -Pn -A [Target]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-01 20:03 GMT
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.00043s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 b9:07:96:0d:c4:b6:0c:d6:22:1a:e4:6c:8e:ac:6f:7d (RSA)
|   256 ba:ff:92:3e:0f:03:7e:da:30:ca:e3:52:8d:47:d9:6c (ECDSA)
|_  256 5d:e4:14:39:ca:06:17:47:93:53:86:de:2b:77:09:7d (EdDSA)
80/tcp open  http    nginx 1.14.0 (Ubuntu)
|_http-server-header: nginx/1.14.0 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
MAC Address: 02:6B:C9:F5:90:8F (Unknown)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.60%E=4%D=11/1%OT=22%CT=1%CU=39567%PV=Y%DS=1%DC=D%G=Y%M=026BC9%T
OS:M=6725341B%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=10C%TI=Z%CI=Z%TS=A
OS:)OPS(O1=M2301ST11NW7%O2=M2301ST11NW7%O3=M2301NNT11NW7%O4=M2301ST11NW7%O5
OS:=M2301ST11NW7%O6=M2301ST11)WIN(W1=F4B3%W2=F4B3%W3=F4B3%W4=F4B3%W5=F4B3%W
OS:6=F4B3)ECN(R=Y%DF=Y%T=40%W=F507%O=M2301NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S
OS:=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%R
OS:D=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=
OS:0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U
OS:1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DF
OS:I=N%T=40%CD=S)

Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.43 ms ip-[Target].eu-west-1.compute.internal ([Target])

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 24.00 seconds 
</code></pre><br>

<h2 align="left">
  $$\textcolor{#e691c9}{\textbf{Olivia Cortez:olivi8}}$$ <br>
  $$\textcolor{#e691c9}{\textbf{Open Ports = 22 and 80}}$$
</h2>

<p>Then I added [Target] ehich is to <code>/etc/hosts</code></p>

![image](https://github.com/user-attachments/assets/6bbc710e-ff49-4dc2-8324-c6e6b7a01d72)

<br>
<p>As a next step I tried to open [Target] in the web browser. I was redirected to <code>cyprusbank.thm</code>, National Bank of Cyprus and the following message:<code>We are currntly under maintenance, than you for your patience.</code></p>

![image](https://github.com/user-attachments/assets/dd53b8d0-a07d-47f4-88f3-4067eb50636c)

<h2 align="left">
  $$\textcolor{#e691c9}{\textbf{Olivia Cortez:olivi8}}$$ <br>
  $$\textcolor{#e691c9}{\textbf{Open Ports = 22 and 80}}$$ <br>
  $$\textcolor{#e691c9}{\textbf{Domain = cyprusbank.thm}}$$<br>
</h2>

<pre><code>$ ffuf -H "HOST: FUZZ.cyprusbank.thm" -u http://cyprusbank.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-110000.txt -fw 1

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1
________________________________________________

 :: Method           : GET
 :: URL              : http://cyprusbank.thm
 :: Wordlist         : FUZZ: /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-110000.txt
 :: Header           : Host: FUZZ.cyprusbank.thm
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Response words: 1
________________________________________________

www                     [Status: 200, Size: 252, Words: 19, Lines: 9]
admin                   [Status: 302, Size: 28, Words: 4, Lines: 1]
WWW                     [Status: 200, Size: 252, Words: 19, Lines: 9]
ADMIN                   [Status: 302, Size: 28, Words: 4, Lines: 1]
:: Progress: [114532/114532] :: Job [1/1] :: 10460 req/sec :: Duration: [0:00:15] :: Errors: 0 :: 
</code></pre><br>


<pre><code>$ nmap -sC -sV -Pn -A [Target]

</code></pre><br> sudo /etc/hosts


> 1.1. <em>What's Tyrell Wellick's phone number?</em><br><a id='1.1'></a>
>> <code><strong>______</strong></code><br><br>

<p>Take things a step further and compromise the machine.</p>

> 1.2. <em>What is the user.txt flag?</em><br><a id='1.2'></a>
>> <code><strong>______</strong></code>
<p><br></p>

> 1.3. <em>What is the root.txt flag?</em><br><a id='1.3'></a>
>> <code><strong>______</strong></code><br>
<p><br></p>



<h2>Room Complete<a id='4'></a></h2>
<p>Keep learning, keep growing!<br>



<h2>My Journey<a id='5'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
