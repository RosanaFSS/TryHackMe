<p align="center">October 31, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{178}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Git Happens &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Boss wanted me to create a prototype, so here it is! We even used something called "version control" that made deploying this really easy!.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/githappens">Git Happens</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/cd2de457-e1bb-4619-96e1-4cd7d0173d0b">
  <img height="150px" src="https://github.com/user-attachments/assets/9be20102-0d60-4dfa-85eb-44f93b1e4abd">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Capture the flag](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room complete](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#5)


<h2>Task 1. Capture the flag<a id='1'></a></h2>

<p>Can you find the password to the application?</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<p>I started enumerating with nmap.</p>

<ul style="list-style-type:square">
    <li><code>-sC</code>: run all the default scripts.</li>
    <li><code>-sV</code>: Find the version of services running on the target.</li>
    <li><code>-T4</code>: Aggressive scan to provide faster results.</li>
</ul></p>

<pre><code># sudo nmap -sC -sV -T4 [Target]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-31 22:37 GMT
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.0010s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.14.0 (Ubuntu)
| http-git: 
|   [Target]:80/.git/
|     Git repository found!
|_    Repository description: Unnamed repository; edit this file 'description' to name the...
|_http-server-header: nginx/1.14.0 (Ubuntu)
|_http-title: Super Awesome Site!
MAC Address: 02:90:A7:6B:80:09 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.80 seconds
</code></pre><br>

<p>The port scan shows that the http service is running on <code>port 80</code> and a git repository can be accessed through <code>[Target]:80/.git/</code>!</p>
<br>
<p>Accessing [Target] we will find this ....</p>

![image](https://github.com/user-attachments/assets/f5f8f176-500a-46dc-af0e-2a3f5a99437c)

<p>This login page do not provide data entry.</p>

<p>Accessing [Target]<code>[Target]:80/.git/</code> we will find some folders exposed in <code>git directory</code>.</p>

![image](https://github.com/user-attachments/assets/127315d6-15ca-4452-9507-1ef5a56cae7c)



> 1.1. <em>Find the Super Secret Password.</em><br><a id='1.1'></a>
>> <code><strong>____</strong></code><br><br>



<pre><code>$ 


</code></pre><br>



<h2>Room Complete<a id='4'></a></h2>
<p>Keep learning, keep growing!<br>



<h2>My Journey<a id='5'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>



<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
