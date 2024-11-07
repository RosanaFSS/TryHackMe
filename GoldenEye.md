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
<h2>Task 1. Intro & Enumeration<a id='1'></a></h2>
<p>This room will be a guided challenge to hack the James Bond styled box and get root.</p>
<p>Credit to <a href="https://www.vulnhub.com/author/creosote,584/">creosote</a> for creating this VM. <strong>This machine is used here with the explicit permission of the creator <3</strong>.</p>
<p>So.. Lets get started!</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 1.1. <em>First things first, connect to our <a href="https://tryhackme.com/r/access">network</a> and deploy the machine.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 1.2. <em>Use nmap to scan the network for all ports. How many ports are open?</em><br><a id='1.2'></a>
>> <code><strong>4</strong></code>

<br>

> 1.3. <em>Take a look on the website, take a dive into the source code too and remember to inspect all scripts!</em><br><a id='1.3'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 1.4. <em>Who needs to make sure they update their default password?</em><br><a id='1.4'></a>
>> <code><strong>boris</strong></code>

<br>

> 1.5. <em>Whats their password?</em><br><a id='1.5'></a>
>> <code><strong>InvincibleHack3r</strong></code>

<br>

> 1.6. <em>Now go use those credentials and login to a part of the site.</em><br><a id='1.5'></a>
>> <code><strong>No answer needed</strong></code>

<br>
<h2>Task 2. Its mail time ...<a id='2'></a></h2>
<p>Onto the next steps.. </p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 2.1. <em>Take a look at some of the other services you found using your nmap scan. Are the credentials you have re-usable? </em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 2.2. <em>If those creds don't seem to work, can you use another program to find other users and passwords? Maybe Hydra?Whats their new password?</em><br><a id='2.2'></a>
>> <code><strong>secret1!</strong></code>

<br>

> 2.3. <em>Inspect port 55007, what services is configured to use this port?</em><br><a id='2.3'></a>
>> <code><strong>telnet</strong></code>

<br>

> 2.4. <em>Login using that service and the credentials you found earlier.</em><br><a id='2.4'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 2.5. <em>What can you find on this service?</em><br><a id='2.5'></a>
>> <code><strong>emails</strong></code>

<br>

> 2.6. <em>What user can break Boris' codes?</em><br><a id='2.6'></a>
>> <code><strong>natalya</strong></code>
