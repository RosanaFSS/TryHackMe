
<p align="center">December 5, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{213}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Advent of Cyber 2023, Day 13, Instrusion Detection}}$$

</h1>
<p align="center">Get started with Cyber Security in 24 Days - Learn the basics by doing a new, beginner friendly security challenge every day leading up to Christmas.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/adventofcyber2023">Advent of Cyber 2023</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/8d077e24-767e-4ac1-83f9-808a1dc8c077">
  <img height="150px" src="https://github.com/user-attachments/assets/7ac61c46-f39b-40f6-8315-30ae61a8a8e9">

</p>

<h2>[Day 13] Intrusion Detection, To the Pots, Through the Walls<a id='1'></a></h2>

<p align="center">
  <img width="700px" src="https://github.com/user-attachments/assets/ecce579a-b7b9-40ab-9e86-57dd5dfb57fe">
</p>

<p>The proposed merger and suspicious activities have kept all teams busy and engaged. So that the Best Festival Company's systems are safeguarded in the future against malicious attacks, McSkidy assigns The B Team, led by McHoneyBell, to research and investigate mitigation and proactive security.<br>

The team's efforts will be channelled into the company's defensive security process. You are part of the team – a security researcher tasked with gathering information on defence and mitigation efforts.</p>

<h3>Learning Objectives</h3>
<p>https://github.com/user-attachments/assets/ecce579a-b7b9-40ab-9e86-57dd5dfb57fe</p>
- Learn to understand incident analysis through the Diamond Model.<br>
- Identify defensive strategies that can be applied to the Diamond Model.<br>
- Learn to set up firewall rules and a honeypot as defensive strategies.<br>

<h3>Accessing the Machine</h3>
<p>Before moving forward, review the questions in the connection card shown below:</p>

<p align="center">
  <img height="200px" src="https://github.com/user-attachments/assets/350234f2-679e-4929-9f10-6baccc5c9b0f">
</p>

<p>Launch the virtual machine by pressing the green <code>Start Machine</code> button at the top–right of this task and the AttackBox by pressing the Start AttackBox button on the upper right of this page. Use the SSH credentials below to access the VM and follow along the practical sections of the task.</p>

<p align="center">
  <img height="200px" src="https://github.com/user-attachments/assets/f6d903b4-794f-4d3f-8b41-7d29c5765bfd">
</p>

<h3>Introduction</h3>
<p>Intrusion detection and prevention is a critical component of cyber security aimed at identifying and mitigating threats. When set up early, intrusion detection becomes a proactive security measure. However, in our story, the Best Festival Company has to develop ways to improve their security, given the magnitude of the recent breaches.<br>

In this epic task, we'll embark on a thrilling journey through fundamental concepts, detection strategies, and the application of the Diamond Model of Intrusion Analysis in defensive security.</p>

<h3>Incident Analysis</h3>
<p>Consider the cyber threat events that have recently taken place within the Best Festival Company and AntarctiCrafts. We have identified clues and artefacts, but we're yet to piece them together to lead us to the attacker. We need a framework to profile the attacker, understand their moves, and help us strengthen our defences.</p>

<p align="center">
  <img width="100px" src="https://github.com/user-attachments/assets/d87f0e71-7b75-478a-98ef-d2df6737290b">
</p>

<p>The DiamondModel is a security analysis framework that seasoned professionals use to unravel the mysteries of adversary operations and identify the elements used in an intrusion. It comprises four core facets, interconnected to form a well-orchestrated blueprint of the attacker's plans:</p>
- Adversary<br>
- Victim<br>
- Infrastructure<br>
- Capability<br>

<p>We'll wield the knowledge we gained from the previous days of Advent of Cyber to unlock the secrets hidden within these core features.</p>

<h4>Adversary</h4>

<h4>Victim</h4>

<h4>Infrastructure</h4>

<h4>Capability</h4>

<h3>Defensive Diamond Model</h3>

<h3>Van Twinkle´s Challenge</h3>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 1.1. <em>Which security model is being used to analyse the breach and defence strategies?</em><br><a id='1.1'></a>
>> <code><strong>Diamond Model</strong></code>

<br>

> 1.2. <em>Which defence capability is used to actively search for signs of malicious activity?</em><br><a id='1.2'></a>
>> <code><strong>Threat hunting</strong></code>

<br>

> 1.3. <em>What are our main two infrastructure focuses? (Answer format: answer1 and answer2)</em><br><a id='1.3'></a>
>> <code><strong>Firewall and Honeypot</strong></code>

<br>

> 1.4. <em>What is the name of the layer between the Input and Output layers of a Neural Network?</em><br><a id='1.4'></a>
>> <code><strong>Hidden Layer</strong></code>

<br>

> 1.5. <em>Which firewall command is used to block traffic?</em><br><a id='1.5'></a>
>> <code><strong>Deny</strong></code>

<br>

> 1.6. <em>There is a flag in one of the stories. Can you find it?</em><br><a id='1.6'></a>
>> <code><strong>________</strong></code>

<br>

> 1.7. <em>If you enjoyed this task, feel free to check out the Network Device Hardening room.</em><br><a id='1.6'></a>
>> <code><strong>No answer needed</strong></code>

<br>

![image](https://github.com/user-attachments/assets/6d1609d6-5293-48b7-88f3-5bb7255c226e)

<br>

<pre><code>
vantwinkle@ip-10-10-23-150:~$ pwd
/home/vantwinkle
vantwinkle@ip-10-10-23-150:~$ sudo ufw status
[sudo] password for vantwinkle: 
Status: inactive
vantwinkle@ip-10-10-23-150:~$ 
</code></pre>

<br>

<pre><code>vantwinkle@[Target]:~$ sudo su
root@[Target]:/home/vantwinkle# ufw default allow outgoing
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)
</code></pre>

<b>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# ufw default deny incoming
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
</code></pre>

<br>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# ufw allow 22/tcp
Rules updated
Rules updated (v6)
</code></pre>

<br>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# ufw deny from [Specific IP 1]
Rules updated
</code></pre>

<br>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# ufw deny in on eth0 from [Specific IP 2]
Rules updated</code></pre>


<br>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
</code></pre>

<br>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere                  
Anywhere                   DENY IN     [Specific IP 1]           
Anywhere on eth0           DENY IN     [Specific Ip 2]            
22/tcp (v6)                ALLOW IN    Anywhere (v6)</code></pre>

<br>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# fw reset
Resetting all rules to installed defaults. This may disrupt existing ssh
connections. Proceed with operation (y|n)? y
Backing up 'user.rules' to '/etc/ufw/user.rules.[Redacted]'
Backing up 'before.rules' to '/etc/ufw/before.rules.[Redacted]'
Backing up 'after.rules' to '/etc/ufw/after.rules.[Redacted]'
Backing up 'user6.rules' to '/etc/ufw/user6.rules.[Redacted]'
Backing up 'before6.rules' to '/etc/ufw/before6.rules.[Redacted]'
Backing up 'after6.rules' to '/etc/ufw/after6.rules.[Redacted]'
</code></pre>

<br>

<pre><code>vantwinkle@[Target]:/home/vantwinkle# </code></pre>












<h2>Task Complete<a id='2'></a></h2>
<p>Keep learning, keep growing!<br>

<h3 align="center"> <img width="900px" src=""> </h3>


<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

<h3 align="center"> <img width="900px" src=""> </h3>
