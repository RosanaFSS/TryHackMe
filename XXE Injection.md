<p align="center">November 20, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{197}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{XXE Injection}}$$
</h1>
<p align="center">Exploiting XML External Entities.</p>
<p align="center">Access this TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/xxeinjection">XXE Injection</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/a5324ef3-8fd6-4015-88c8-f415c54edebc">
  <img height="150px" src="https://github.com/user-attachments/assets/48edd5a2-bfc3-43a6-aae5-cdfee04b9a9b">
</p>

<p align="center">Summary</p>



<pre><code>root@[THMAttackBox]:~# gobuster dir -u http://[Target]/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target]/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/uploads              (Status: 301) [Size: 314] [--> http://[Target]/uploads/]
/javascript           (Status: 301) [Size: 317] [--> http://[Target]/javascript/]
/phpmyadmin           (Status: 301) [Size: 317] [--> http://[Target]/phpmyadmin/]
/server-status        (Status: 403) [Size: 9]
Progress: 220557 / 220558 (100.00%)
===============================================================
Finished
===============================================================
</code></pre>

<h2>Task 4.  Exploiting XXE - In-Band<a id='1'></a></h2>

<h3>In-Band vs Out-of-Band XXE</h3>

<p>In-band XXE refers to an XXE vulnerability where the attacker can see the response from the server. This allows for straightforward data exfiltration and exploitation. The attacker can simply send a malicious XML payload to the application, and the server will respond with the extracted data or the result of the attack.

Out-of-band XXE, on the other hand, refers to an XXE vulnerability where the attacker cannot see the response from the server. This requires using alternative channels, such as DNS or HTTP requests, to exfiltrate data. To extract the data, the attacker must craft a malicious XML payload that will trigger an out-of-band request, such as a DNS query or an HTTP request.</p>

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





