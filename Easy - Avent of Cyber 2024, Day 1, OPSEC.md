<h5 align="center">December 1, 2024<br>
Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{209}}$$-day-streak in  <a href="https://tryhackme.com/">TryHackMe</a>.</h5>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{Advent of Cyber 2024}}$$</h1>

<h5 align="center">Dive into the wonderful world of cyber security by engaging<br>
in festive beginner-friendly exercises every day in the lead-up to Christmas!</h5>

<p align="center">
<img height="90px" hspace="20" src="https://github.com/user-attachments/assets/0d8d7f29-525a-49ad-85ba-9223bdec089b">
<img width="500px" src="https://github.com/user-attachments/assets/8ca4206f-a1e7-48d8-ba17-d8e304613a2c"></p>

<p align="center">Access this 🆓 TryHackMe CTF challenge clicking <a href="https://tryhackme.com/r/room/adventofcyber2024">Advent of Cyber 2024</a>.</p>

<h2 align="center"> $$\textcolor{yellow}{\textnormal{Day 1 - OPSEC}}$$<br>
$$\textcolor{yellow}{\textnormal{Maybe SOC-mas music, he thought, doesn't come from a store?}}$$</h2>

![image](https://github.com/user-attachments/assets/d02fbb62-4680-46c6-b7e4-48308275a0cc)

<p><em>McSkidy tapped keys with a confident grin,<br>
A suspicious website, now where to begin?<br>
She'd seen sites like this, full of code and of grime,<br>
Shady domains, and breadcrumbs easy to find.</em></p>

<p>McSkidy's fingers flew across the keyboard, her eyes narrowing at the suspicious website on her screen. She had seen dozens of malware campaigns like this. This time, the trail led straight to someone who went by the name "Glitch."<br>

"Too easy," she muttered with a smirk.<br>

"I still have time," she said, leaning closer to the screen. "Maybe there's more."<br>

Little did she know, beneath the surface lay something far more complex than a simple hacker's handle. This was just the beginning of a tangled web unravelling everything she thought she knew.</p>

![image](https://github.com/user-attachments/assets/a8dc2b40-c3ae-4a6f-94ba-060d705b94f0)

<h3>Learning Objectives</h3>
- Learn how to investigate malicious link files.<br>
- Learn about OPSEC and OPSEC mistakes.<br>
- Understand how to track and attribute digital identities in cyber investigations.<br>


<h3>Connecting to the Machine</h3>
<p>Before moving forward, review the questions in the connection card shown below and start the virtual machine by pressing the <code>Sart Machine</code> button. The VM should be fully loaded in 3 minutes. Additionally, you will need the AttackBox, which can be launched by clicking the <code>Strat AttakBox</code> button at the top of the page.</p>

<h4>NOTE:</h4>
<p>If you’re clicking "Start Machine" and encountering an issue launching it, don’t worry—it’s just the high demand. What can you do?</p>
- Keep trying! Machines are becoming available as demand fluctuates.<br>
- If you’re still having trouble, come back a little later when it’s less busy.

![image](https://github.com/user-attachments/assets/e35c0bcc-0716-4909-94ee-7201728e4457)

<h3>Investigating the Website</h3>
<p>The website we are investigating is a Youtube to MP3 converter currently being shared amongst the organizers of SOC-mas. You've decided to dig deeper after hearing some concerning reports about this website.</p>

![image](https://github.com/user-attachments/assets/1978784b-55a6-4c86-bb6b-04c212e37615)

<p>From your AttackBox, access the website by visiting MACHINE_IP using the web browser.<br>

At first glance, the website looks legit and presentable. The About Page even says that it was made by "The Glitch ". How considerate of them to make our job easier!<br>

Scrolling down, you'll see the feature list, which promises to be "Secure" and "Safe." From our experience, that isn't very likely.</p>

<h3>Youtube to MP3 Converter Websites</h3>
<p>These websites have been around for a long time. They offer a convenient way to extract audio from YouTube videos, making them popular. However, historically, these websites have been observed to have significant risks, such as:</p>
- <strong>Malvertising</strong>: Many sites contain malicious ads that can exploit vulnerabilities in a user's system, which could lead to infection.<br>
- <strong>Phishing scams</strong>: Users can be tricked into providing personal or sensitive information via fake surveys or offers.<br>
- <strong>Bundled malware</strong>: Some converters may come with malware, tricking users into unknowingly running it.

<p>What nefarious thing does this website have in store for us?</p>

<h3>Getting Some Tunes</h3>
<p>Let's find out by pasting any YouTube link in the search form and pressing the "Convert" button. Then select either <code>mp3 or mp4</code> option. This should download a file that we could use to investigate. For example, we can use <code>https://www.youtube.com/watch?v=dQw4w9WgXcQ</code>, a classic if you ask me.<br>

Once downloaded, navigate to your Downloads folder or if you are using the AttackBox, to your /root/ directory. Locate the file named <code>download.zip</code>, right-click on it, and select <code>Extract To</code>. In the dialog window, click the <code>Extract</code> button to complete the extraction.</p>

![image](https://github.com/user-attachments/assets/e5c65d7b-6d5e-4965-b98f-7955f9ffb101)

<p>You'll now see two extracted two files: song.mp3 and somg.mp3.<br>

To quickly determine the file's contents, double-click on the "Terminal" icon on the desktop then run the file command on each one. First, let's try checking song.mp3.</p>

![image](https://github.com/user-attachments/assets/14dff988-1c51-4cba-b4c1-c6498cd1f232)

<p>There doesn't seem to be anything suspicious, according to the output. As expected, this is just an MP3 file.<br>

How about the second file somg.mp3? From the filename alone, we can tell something is not right. Still, let's confirm by running the file command on it anyway.</p>

![image](https://github.com/user-attachments/assets/98a421a7-f468-4bdb-bdea-654284f87718)

<p>Now, this is more interesting!

The output tells us that instead of an MP3, the file is an "MS Windows shortcut", also known as a .lnk file. This file type is used in Windows to link to another file, folder, or application. These shortcuts can also be used to run commands! If you've ever seen the shortcuts on a Windows desktop, you already know what they are.<br>

There are multiple ways to inspect .lnk  files to reveal the embedded commands and attributes. For this room, however, we'll use ExifTool, which is already installed on this machine.<br>

To do this, go back to your Terminal and type:</p>

![image](https://github.com/user-attachments/assets/6363a001-477b-4101-8c8f-7650f770dbf1)

<p>Look through the output to locate the command used as a shortcut in the somg.mp3 file. If you scroll down through the output, you should see a PowerShell command.</p>

![image](https://github.com/user-attachments/assets/2030d438-81cd-464e-9b42-1813006f3974)

<p>What this PowerShell command does:</p>
- The -ep Bypass -nop flags disable PowerShell's usual restrictions, allowing scripts to run without interference from security settings or user profiles.<br>
- The DownloadFile method pulls a file (in this case, IS.ps1) from a remote server (https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1) and saves it in the C:\\ProgramData\\ directory on the target machine.<br>
- Once downloaded, the script is executed with PowerShell using the iex command, which triggers the downloaded s.ps1 file.

<p>If you visit the contents of the file to be downloaded using your browser (https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1), you will see just how lucky we are that we are not currently using Windows.</p>

![image](https://github.com/user-attachments/assets/fe8281dd-335c-4e39-b559-056f5ffc86b1)

<p>The script is designed to collect highly sensitive information from the victim's system, such as cryptocurrency wallets and saved browser credentials, and send it to an attacker's remote server.</p>

<p><em>Disclaimer: All content in this room, including CPP code, PowerShell scripts, and commands, is provided solely for educational purposes. Please do not execute these on a Windows host.</em></p>

<p>This looks fairly typical of a PowerShell script for such a purpose, with one notable exception: a signature in the code that reads.</p>

<h5>Created by the one and only M.M.</h5>

<h3>Searching the Source</h3>

<p>.................</p>

<h3>Introduction to OPSEC</h3>
<p>This is a classic case of OPSEC failure.<br>

Operational Security (OPSEC) is a term originally coined in the military to refer to the process of protecting sensitive information and operations from adversaries. The goal is to identify and eliminate potential vulnerabilities before the attacker can learn their identity.<br>

In the context of cyber security, when malicious actors fail to follow proper OPSEC practices, they might leave digital traces that can be pieced together to reveal their identity. Some common OPSEC mistakes include:</p>

- Reusing usernames, email addresses, or account handles across multiple platforms. One might assume that anyone trying to cover their tracks would remove such obvious and incriminating information, but sometimes, it's due to vanity or simply forgetfulness.<br>
- Using identifiable metadata in code, documents, or images, which may reveal personal information like device names, GPS coordinates, or timestamps.<br>
- Posting publicly on forums or GitHub (Like in this current scenario) with details that tie back to their real identity or reveal their location or habits.<br>
- Failing to use a VPN or proxy while conducting malicious activities allows law enforcement to track their real IP address.

- <p>You'd think that someone doing something bad would make OPSEc their top priority, but they're only human and can make mistakes, too.<br>

For example, here are some real-world OPSEC mistakes that led to some really big fails:</p>


<h3>AlphaBay Admin Takedown</h3>

<p>..............</p>


<h3>Chinese Military Hacking Group (APT1)</h3>

<p>..........</p>

<h3>Uncovering MM</h3>

<p>......</p>

<h3>Whats Next?</h3>

<p>...</p>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 1.1. <em>Looks like the song.mp3 file is not what we expected! Run "exiftool song.mp3" in your terminal to find out the author of the song. Who is the author?</em><br><a id='1.1'></a>
>> <code><strong>______________</strong></code>

<br>

> 1.2. <em>The malicious PowerShell script sends stolen info to a C2 server. What is the URL of this C2 server?</em><br><a id='1.2'></a>
>> <code><strong>______________</strong></code>

<br>


> 1.3. <em>Who is M.M? Maybe his Github profile page would provide clues?</em><br><a id='1.3'></a>
>> <code><strong>______________</strong></code>

<br>

> 1.4. <em>What is the number of commits on the GitHub repo where the issue was raised?</em><br><a id='1.4'></a>
>> <code><strong>______________</strong></code>

<br>

> 1.5. <em>If you enjoyed this task, feel free to check out the OPSEC room!</em><br><a id='1.5'></a>
>> <code><strong>______________</strong></code>

<br>

> 1.6. <em>What's with all these GitHub repos? Could they hide something else?</em><br><a id='1.6'></a>
>> <code><strong>______________</strong></code>

<br>



<h2>Task Complete<a id='2'></a></h2>
<p>Keep learning, keep growing!<br>

<h3 align="center"> <img width="900px" src=""> </h3>

<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

<h3 align="center"> <img width="900px" src=""> </h3>


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
