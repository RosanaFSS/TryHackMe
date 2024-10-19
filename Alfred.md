<p><h3> Welcome to the <em>TryHackMe</em></h3>
<h1>Offensive Pentesting learning path> Advanced Exploitation</h1>
<h2>Alfred</h2>
<p>Exploit Jenkins to gain an initial shell, then escalate your privileges by exploiting Windows authentication token.</p><br>
<br>
October 19, 2024<br><br>
Type: Easy<br>
Link: https://tryhackme.com/r/room/alfred</p><br>

![image](https://github.com/user-attachments/assets/89ba97a4-d79a-4c6d-8c86-dab1becb8e05)
<br>


<p><h2>Task 1 - Initial Access</h2>
In this room, we'll learn how to exploit a common misconfiguration on a widely used automation server(Jenkins - This tool is used to create continuous integration/continuous development pipelines that allow developers to automatically deploy their code once they made changes to it). After which, we'll use an interesting privilege escalation method to get full system access. <br><br>
Since this is a Windows application, we'll be using <strong>Nishang</strong> to gain initial access. The repository contains a useful set of scripts for initial access, enumeration and privilege escalation. In this case, we'll be using the <strong>reverse shell scripts</strong>.<br><br>
Please note that this machine <strong>does not respond to ping</strong> (ICMP) and may take a few minutes to boot up.

<ul>
  <li> What is Powershell</li>
  <li> Basic Powershell commands</li>
  <li> Windows enumeration skills</li>
  <li> Powershell scripting </li>
</ul> 
