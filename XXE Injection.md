


<h2>Task 4.Exploiting XXE - In-Band<a id='1'></a></h2>



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

<h3>In-Band XXE Exploitation</h3>

![image](https://github.com/user-attachments/assets/53e2b635-6567-43c9-b046-819959d5d8b2)

![image](https://github.com/user-attachments/assets/360c7fa8-3b8e-4a67-bebf-635d22ebe578)


![image](https://github.com/user-attachments/assets/81205eb8-00d0-400c-a34a-187a4906dd1c)


<h3>XML Entity Expansion</h3>

![image](https://github.com/user-attachments/assets/25cb6287-639e-4953-a359-e39e3a81707b)


> 4.1. <em>What XXE vulnerability occurs when the server's response is immediately disclosed to the attacker without the use of external channels?</em><br><a id='4.1'></a>
>> <strong>____</strong><br>
<p><br></p>


> 4.2. <em>What is the content of the file 14232d6db2b5fd937aa92e8b3c48d958.txt in the /opt directory?</em><br><a id='4.2'></a>
>> <strong>____</strong><br>
<p><br></p>





