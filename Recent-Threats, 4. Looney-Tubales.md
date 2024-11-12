<p align="center">November 11, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{189}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{ Looney Tunables }}$$ </h1>
<p align="center">CVE-2023-4911: That's all Sec-Folks!s.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/looneytunes">GitLab CVE-2023-7028</a>.</p>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/2701eded-3213-4aa9-9919-720579b58a44"><br>
  <img height="150px" src="https://github.com/user-attachments/assets/684afecc-06b7-464c-abfe-eee8c72c461e">
</p>


<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [1. Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [2. How Does It Work](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [3. How to Exploit](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [4. Detection and Mitigation](#4) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[5. Conclusions](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp;  [6. Room Complete](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [7. My Journey](#7)

<br>
<br>
<br>
<h2 align="center">Task 1. Introduction<a id='1'></a></h2>
<p>GitLab is a renowned and widely adopted web-based repository manager that provides a comprehensive platform for source code management, continuous integration, and collaboration in software development projects. Per the <a href="https://bluelight.co/blog/best-ci-cd-tools">latest stats</a>, the platform ranks first for <a href="https://tryhackme.com/r/room/introtopipelineautomation">CI/CD</a> and DevOps tools, surpassing other vital platforms like GitHub, Azure, Jenkins, etc. In Jan 2024, the platform identified a critical vulnerability in its <code>Community (CE)</code> and <code>Enterprise Edition (EE)</code>code> that allows unauthorised <code>users to take over user accounts</code>, potentially including administrator accounts, without any interaction from the victim. The vulnerability was identified by <a href="https://hackerone.com/asterion04?type=user">asterion04</a> through a private bug bounty program and was assigned the severity <code>Critical</code> and CVE-ID <code>2023-7028</code>.</p>

<p align="center"> <img width="550px" src="https://github.com/user-attachments/assets/694731e6-ee0c-4427-9b88-ecbbbdc897f2"></p>

<h3>Learning Objectives</h3>
<ul style="list-style-type:square">
    <li>Exploit a GitLab CE instance through CVE 2023-7028</li>
    <li>How the exploit works</li>
    <li>Protection and mitigation measures</li>
</ul></p>

<h3>Room Prerequisites</h3>
<p>Understanding the following topics is recommended before starting the course:</p>
<ul style="list-style-type:square">
    <li><a href="https://tryhackme.com/r/room/protocolsandservers">HTTP Protocols & Methods</a></li>
    <li><a href="https://tryhackme.com/r/room/owasptop10">OWASP top 10 web vulnerabilities</a></li>
    <li>Executing Python code</li>
</ul></p>

<br>

<p>Let´s begin!</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 1.1. <em>I am ready to explore the room.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>



![image](https://github.com/user-attachments/assets/6b78e5bf-9d3f-46a8-9c3a-731f37fc6999)



