<p align="center">November 7, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{185}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; GoldenEye &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Bond, James Bond. A guided CTF.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/goldeneye">GoldenEye</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://tryhackme-images.s3.amazonaws.com/room-icons/77b55a2ac1ac79ca534d6fc003c042b3.png">
  <img height="150px" src="https://github.com/user-attachments/assets/42c32412-a499-4375-aec1-6f7065cad18b">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Intro & Enumeration](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Its mail time ...](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [GoldenEye Operators Training](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Privilege Escalation](#4) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room Complete](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My Journey](#6)

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

