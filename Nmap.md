<p><h3> Welcome to the <em>TryHackMe</em></h3>
<h1>JrPenetration Tester learning path> Network Security</h1>
<h2>Nmaps Basic Port Scans</h2>
<p>Learn in-depth how nmap TCP connect scan, TCP SYN port scan, and UDP port scan work.</p>
<br>
October 20, 2024<br><br>
Type: Easy<br>
Link: https://tryhackme.com/r/room/nmap02</p><br>
Estimated time to solve: 120 mon

![image](https://github.com/user-attachments/assets/98d40464-d228-45b7-81cd-2f7881ef1cd3)



<p><h2>Task 1 - Initial Access</h2>

![image](https://github.com/user-attachments/assets/d7beaef3-c7f9-40af-87a2-4c8d7c35ef0d)

In this room, we'll learn how to exploit a common misconfiguration on a widely used automation server(Jenkins - This tool is used to create continuous integration/continuous development pipelines that allow developers to automatically deploy their code once they made changes to it). After which, we'll use an interesting privilege escalation method to get full system access. <br><br>
Since this is a Windows application, we'll be using <strong>Nishang</strong> to gain initial access. The repository contains a useful set of scripts for initial access, enumeration and privilege escalation. In this case, we'll be using the <strong>reverse shell scripts</strong>.<br><br>
Please note that this machine <strong>does not respond to ping</strong> (ICMP) and may take a few minutes to boot up.

In the following link you´ll find more information about Nishang.https://github.com/samratashok/nishang<br>
And in tis other link we will find more abour reverse shell scripts. https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1</p>

<p><br></p>

> 1.1 - <em>How many ports are open? (TCP only)?</em><br>
>> <strong>3</strong><br><br>
>> Performing Nmap I identified 3 ports open: 80/http, 3389/ssl, and 8080/http.<br>
>> <code>nmap -Pn -sC -sV -sS -p- -T4 10.10.30.67</code><br>

![image](https://github.com/user-attachments/assets/b73da9a5-0b5e-4f75-9a58-ce2df7996060)<br>

>> <code>nmap -sCV -sT -Pn -v 10.10.30.67</code><br>

![image](https://github.com/user-attachments/assets/0c391498-4259-43af-9a86-26b4a6dd0c16)
