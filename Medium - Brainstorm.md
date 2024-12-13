<h1>Brainstorom</h1>

<p>50%</p>

<br>

<pre><code> nmap -Pn -sC -sV -oA Brainstorm [Target]
Starting Nmap 7.80 ( https://nmap.org ) at 2024-12-13 01:17 GMT
Nmap scan report for [Target].eu-west-1.compute.internal ([Target])
Host is up (0.00048s latency).
Not shown: 997 filtered ports
PORT     STATE SERVICE    VERSION
21/tcp   open  ftp        Microsoft ftpd
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|_  SYST: Windows_NT
3389/tcp open  tcpwrapped
|_ssl-date: 2024-12-13T01:20:16+00:00; 0s from scanner time.
9999/tcp open  abyss?
| fingerprint-strings: 
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, Help, JavaRMI, RPCCheck, RTSPRequest, SSLSessionReq, TerminalServerCookie: 
|     Welcome to Brainstorm chat (beta)
|     Please enter your username (max 20 characters): Write a message:
|   NULL: 
|     Welcome to Brainstorm chat (beta)
|_    Please enter your username (max 20 characters):
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
...
SF:rname\x20\(max\x2020\x20characters\):\x20Write\x20a\x20message:\x20")%r
...
SF:se\x20enter\x20your\x20username\x20\(max\x2020\x20characters\):\x20Writ
SF:e\x20a\x20message:\x20");
MAC Address: 02:0D:5A:0B:E2:C5 (Unknown)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 251.80 seconds
</code></pre>

<br>

<pre><code>root@~# ftp [Target]
Connected to [Target].
220 Microsoft FTP Service
Name ([Target]:root): anonymous
331 Anonymous access allowed, send identity (e-mail name) as password.
Password:
230 User logged in.
Remote system type is Windows_NT.
ftp> ls
200 PORT command successful.
125 Data connection already open; Transfer starting.
08-29-19  07:36PM       <DIR>          chatserver
226 Transfer complete.
ftp> cd chatserver
250 CWD command successful.
ftp> ls
200 PORT command successful.
125 Data connection already open; Transfer starting.
08-29-19  09:26PM                43747 chatserver.exe
08-29-19  09:27PM                30761 essfunc.dll
226 Transfer complete.
ftp> mget
(remote-files) *
mget chatserver.exe? y
200 PORT command successful.
125 Data connection already open; Transfer starting.
WARNING! 45 bare linefeeds received in ASCII mode
File may not have transferred correctly.
226 Transfer complete.
43747 bytes received in 0.09 secs (472.8674 kB/s)
mget essfunc.dll? y
200 PORT command successful.
125 Data connection already open; Transfer starting.
WARNING! 32 bare linefeeds received in ASCII mode
File may not have transferred correctly.
226 Transfer complete.
30761 bytes received in 0.00 secs (19.0370 MB/s)
...
...
ftp> bin
200 Type set to I.
ftp> mget
(remote-files) *
mget chatserver.exe? y
200 PORT command successful.
125 Data connection already open; Transfer starting.
226 Transfer complete.
43747 bytes received in 0.00 secs (36.0903 MB/s)
mget essfunc.dll? y
200 PORT command successful.
125 Data connection already open; Transfer starting.
226 Transfer complete.
30761 bytes received in 0.00 secs (122.2332 MB/s)
ftp> quit
221 Goodbye.
 
</code></pre>

<br>

<pre><code># nc -nv [Target] 9999
Connection to [Target] 9999 port [tcp/*] succeeded!
Welcome to Brainstorm chat (beta)
Please enter your username (max 20 characters): Rose
Write a message: Hello!


Thu Dec 12 17:25:36 2024

Rose said: Hello!


Write a message:  help


Thu Dec 12 17:25:53 2024

Rose said: help


Write a message:  chicken


Thu Dec 12 17:27:08 2024

Rose said: chicken
</code></pre>

<br>



<p> .... Need to practice more to move further ....</p>
