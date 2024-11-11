
![image](https://github.com/user-attachments/assets/4ddd782f-997a-4745-9916-f79913fb1762)

![image](https://github.com/user-attachments/assets/e58ba1cd-a88c-4da9-b525-d221a8dee925)


<h2>Task 1. Pwn</h2>

![image](https://github.com/user-attachments/assets/62596890-c2b8-41c6-af3d-892e6872998a)

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
root@ip-10-10-29-125:~/anonymous# 

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
>> <code><strong>_____</strong></code>

<br>

> 1.6. <em>root.txt</em><br><a id='1.6'></a>
>> <code><strong>_____</strong></code>

<br>
  


