
 #Day 46

 

<h2>Task 1. Getting Started!<a id='1'></a></h2>

> 1.1 - <em>Let's get started!</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>

<br>
<h2>Task 2. Web Explotation | [Easy] Bruteforce Me!<a id='2'></a></h2>

<br>
<h2>Task 3. Web Explotation | [Easy] Endpoint!<a id='3'></a></h2>

<br>
<h2>Task 4. Web Explotation | [Easy] Notepad Online<a id='4'></a></h2>

<br>
<h2>Task 5. Web Explotation | [Easy] Scanner<a id='5'></a></h2>

<br>
<h2>Task 6. Web Explotation | [Easy] Time Travel<a id='6'></a></h2>

<br>
<h2>Task 7. Web Explotation | [Medium] Arcanum Travel<a id='7'></a></h2>

<br>
<h2>Task 8. Web Explotation | [Medium] What Does the Cow say?<a id='8'></a></h2>

<br>
<h2>Task 9. Web Explotation | [Hard] The Sequel<a id='9'></a></h2>

<br>
<h2>Task 10. Cryptography | [Easy] B4sed<a id='10'></a></h2>

<br>
<h2>Task 11. Cryptography | [Easy] Exam<a id='11'></a></h2>

<br>
<h2>Task 12. Cryptography | [Easy] CrackMyPass 1<a d='12'></a></h2>

<br>
<h2>Task 13. Cryptography | [Medium] CrackMyPass 2<a id='13'></a></h2>

<br>
<h2>Task 14. Cryptography | [Hard] CrackMyPass 3<a id='14'></a></h2>

<br>
<h2>Task 15. Foresincs | [Easy] Eggciting Recovery<a id='15'></a></h2>

<br>
<h2>Task 16. Foresincs | [Easy] FootPrints<a id='16'></a></h2>

<br> 
<h2>Task 17. Foresincs | [Easy] Maldoom's Revenge<a id='17'></a></h2>

<br>
<h2>Task 18. Foresincs | [Easy] Phishy<a id='18'></a></h2>

<br>
<h2>Task 19. Foresincs | [Medium] Stolen FootPrints<a id='19'></a></h2>

<br>
<h2>Task 20. Foresincs | [Hard] Mayhem<a id='20'></a></h2>

<br>
<h2>Task 21. OSINT | [Easy] TryFindMe<a id='21'></a></h2>

<br>
<h2>Task 22. OSINT | [Easy] Operation Slither 1<a id='22'></a></h2>

<br>
<h2>Task 23. OSINT | [Easy] Operation Slither 2<a id='23'></a></h2>

<br>
<h2>Task 24. OSINT | [Medium] Operation Slither 3<a id='24'></a></h2>

<br>
<h2>Task 25. Linux Command Line | [Easy] Get That Flag Out<a id='25'></a></h2>

<br>
<h2>Task 26. Linux Command Line | [Easy] Arcives<a id='26'></a></h2>

<br>
<h2>Task 27. Boot2Root | [Medium] Admin Panel<a id='27'></a></h2>

<br>
<h2>Task 28. Boot2Root | [Medium] A Window Opens<a id='28'></a></h2>





<br>
<p align="center">While the king of dreams was imprisoned, his home fell into ruins.<br>
Can you help Sandman restore his kingdom?</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 1.1. <em>What is the Lucien Flag?</em><br><a id='2'></a>
>> <code><strong>THM{TH3_L1BR4R14N}</strong></code><br><br>

<pre><code>root@ip-[Attack_IP]:~/Dreaming# nmap -sC -sV [Target_IP]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-07 02:50 GMT
Nmap scan report for ip-[Target_IP].eu-west-1.compute.internal ([Target_IP])
Host is up (0.00037s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.9 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
MAC Address: 02:EB:CF:87:A9:37 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.56 seconds
root@ip-[Attack_IP]:~/Dreaming# 
</code></pre>

<br>
