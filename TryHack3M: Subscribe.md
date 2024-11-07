<p align="center">November 7, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{185}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TryHack3M: Subscribe &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Can you help Hack3M reach 3M subscribers?</p>
<p align="center">Access this TryHackMe Room clicking <a href="https://tryhackme.com/r/room/subscribe">TryHack3M: Subscribe</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/6cdf59cf-c516-48a5-882d-2e065f1afd28">
  <img height="150px" src="https://github.com/user-attachments/assets/b2505fa7-11f9-47bd-b32c-4e75bac1da1e">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [A Public Computer with a VPN](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Connected Tables](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Unlisted](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [From DB to OS](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp;[Finding a Needle in a Malwarestack](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [User Flag](#7) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Operation Defang](#8)  &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room Complete](#9) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My Journey](#10)

<br>
<br>
<br>
<h2>Task 1. A Public Computer with a VPN<a id='1'></a></h2>

![image](https://github.com/user-attachments/assets/fe7e8d48-51e9-4ca7-ab34-05505786f770)

<p>After weeks of meticulous observation and planning, we pinpointed the public computer that the suspect uses to access their website. The computer is located in a quiet corner of the local library. Although the computer has a warning sign that <strong>all computer activity is monitored</strong>, the suspect doesn’t seem to care. They only check for installed key loggers before establishing a VPN connection and logging in to their criminal marketplace. This time, we were ready:</p>

<ul style="list-style-type:square">
    <li>We have set the browser to log the session’s TLS keys; this logging was achieved by adding an extra option to the browser shortcut. Executing <code>chromium --ssl-key-log-file=~/ssl-key.log</code> dumps the TLS keys to the <code>ssl-key.log</code> file.</li>
    <li>We were capturing all traffic on that computer.</li>
</ul></p>

<p>By the time they finished, we had a log of used TLS keys and an encrypted packet capture. You can access these files by clicking the <strong>Download Task Files</strong> button or navigating to <code>/root/Rooms/TryHack3M/sch3MaD3Mon</code> on the AttackBox. Using the TLS key log file, Wireshark should be able to decrypt all exchanged traffic.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 1.1. <em>What is the suspect’s username?.</em><br><a id='1.1'></a>
>> <code><strong>lannister</strong></code>

<br>

> 1.2. <em>What is the suspect’s password?</em><br><a id='1.2'></a>
>> <code><strong>hrpTfL42wMv3</strong></code>

<br>

<h2>Task 2. Connected Tables<a id='2'></a></h2>
<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 2.1. <em>What does RDBMS stand for?</em><br><a id='2.1'></a>
>> <code><strong>Relational Database Management System</strong></code>

<br>

> 2.2. <em>What does CRUD stand for?</em><br><a id='2.2'></a>
>> <code><strong>Create Read Update Delete</strong></code>

<br>

> 2.3. <em>What does SQL stand for?</em><br><a id='2.2'></a>
>> <code><strong>Structured Query Language</strong></code>

<br>

<h2>Task 3. Unlisted<a id='3'></a></h2>
<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>

> 3.1. <em>What's the hidden path?</em><br><a id='3.1'></a>
>> <code><strong>os_sqli.php</strong></code>

<br>

<h2>Task 4. From DB to OS<a id='4'></a></h2>
<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>


> 4.1. <em>What is the output of pwd when run via an SQL injection attack?</em><br><a id='4.1'></a>
>> <code><strong>/var/lib/mysql</strong></code>

<br>

<h2>Task 5. Finding a Needle in a Malwarestack<a id='5'></a></h2>
<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>


> 5.1. <em>What is the malware’s location?</em><br><a id='5.1'></a>
>> <code><strong>/home/products/malware/4sale/pal4t1n3/MisterMeist3r/2DC6C0</strong></code>

<br>

<h2>Task 6. Operation Defang<a id='6'></a></h2>
<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 6.1. <em>What programming language was used to develop the malware?</em><br><a id='6.1'></a>
>> <code><strong>nim</strong></code>

<br>

> 6.2. <em>Reading the source code, what file type is added to the end of encrypted files?</em><br><a id='6.2'></a>
>> <code><strong>.boogey</strong></code>

<br>

> 6.3. <em>What is the flag that appears after compiling the defanged malware?</em><br><a id='6.2'></a>
>> <code><strong>THM{3FDbU2nNy2FW7yMvMoH6WTMMM}</strong></code>

<br>


<h2>Room Complete<a id='9'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/445eb4bd-cae7-4f87-9baf-ae2d1e85783a)

<h2>My Journey<a id='10'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 7, 2024  | 185      |       1,286ª |          28ª |      4,298ª |        60ª | 53,942   |       405 |

![image](https://github.com/user-attachments/assets/269011a6-5ffa-477c-9ebf-c1afaed0a69e)


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
