<p align="center">December 8, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{216}}$$-day-streak in  <a href="https://tryhackme.com/">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Ice}}$$
</h1>
<p align="center">Deploy & hack into a Windows machine, exploiting a very poorly secured media server.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/ice">Ice</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/26afa9d5-2b53-4897-aa55-b9d2a89958d6">
  <img height="150px" src="https://github.com/user-attachments/assets/b1ea024d-c327-42a8-a048-90019761d1b3">
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
>> <code><strong>________</strong></code>

<br>

> 3.3. <em>Now that we've found our vulnerability, let's find our exploit. For this section of the room, we'll use the Metasploit module associated with this exploit. Let's go ahead and start Metasploit using the command `msfconsole`</em><br><a id='3.3'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.4. <em>After Metasploit has started, let's search for our target exploit using the command 'search icecast'. What is the full path (starting with exploit) for the exploitation module? If you are not familiar with metasploit, take a look at the Metasploit module.`</em><br><a id='3.4'></a>
>> <code><strong>________</strong></code>

<br>

> 3.5. <em>Let's go ahead and select this module for use. Type either the command `use icecast` or `use 0` to select our search result.</em><br><a id='3.5'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.6. <em>Following selecting our module, we now have to check what options we have to set. Run the command `show options`. What is the only required setting which currently is blank?</em><br><a id='3.6'></a>
>> <code><strong>________</strong></code>

<br>

> 3.7. <em>First let's check that the LHOST option is set to our tun0 IP (which can be found on the access page). With that done, let's set that last option to our target IP. Now that we have everything ready to go, let's run our exploit using the command `exploit`</em><br><a id='3.7'></a>
>> <code><strong>No answer needed</strong></code>


<br>
<br>
<h2>Task 4. Escalate<a id='3'></a></h2>

<p align="center"> <img width="200px" src="https://github.com/user-attachments/assets/458c28bf-9d68-44d0-b420-6136ff40ea6f"> </p>

<p>Enumerate the machine and find potential privilege escalation paths to gain Admin powers!</p>




