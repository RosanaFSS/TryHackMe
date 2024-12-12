<p align="center">December 12, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{220}}$$-day-streak in  <a href="https://tryhackme.com/">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Retro}}$$

</h1>
<p align="center">New high score!</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/overpass2hacked">Retro</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/549ef432-b001-4fe3-8c8b-3d2e75c0349a">
  <img width="800px" src="https://github.com/user-attachments/assets/728dd9a8-0a75-4a1c-9ece-4a0073abfec6">
</p>

<br>

<h2>Task 1. Pwn</h2>

<p align="center">
  <img width="150px" src="https://github.com/user-attachments/assets/a89030d4-3184-425d-8ae9-bf2a78830054">
</p>

<p align="center">Can you time travel? If not, you might want to think about the next best thing.<br>

Please note that this machine does not respond to ping (ICMP) and may take a few minutes to boot up.<br>

-------------------------------------</p>

<p align="center"><em></em>There are two distinct paths that can be taken on Retro. One requires significantly less trial and error, however, both will work. Please check writeups if you are curious regarding the two paths. An alternative version of this room is available in it's remixed version Blaster.</em></p>


<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 1.1. <em>A web server is running on the target. What is the hidden directory which the website lives on??</em><br><a id='1.1'></a>
>> <code><strong>___________________</strong></code>

<br>

> 1.2. <em>user.txt</em><br><a id='1.2'></a>
>> <code><strong>___________________</strong></code>

<br>

> 1.3. <em>user.txt</em><br><a id='1.3'></a>
>> <code><strong>___________________</strong></code>

<br>

<br>

<br>

<pre><code># nmap -Pn --script vuln [Target]</code></pre>

<br>

![image](https://github.com/user-attachments/assets/b0bc69a8-860c-48ca-a6a1-a50ea17cc153)

<br>

<pre><code># nmap -sC -sV -Pn [Target]</code></pre>

<br>

![image](https://github.com/user-attachments/assets/3a80b505-b292-4726-a10f-bba6db3acd01)

<br>

<pre><code>echo [Target] retro.thm >> /etc/hosts</code></pre>


<br>

![image](https://github.com/user-attachments/assets/4bb82a14-47d0-4866-bf86-e99c0d0d9b4b)

<br>

<pre><code>gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http:/[Target]</code></pre>

<br>

![image](https://github.com/user-attachments/assets/7e514192-db3e-4ea7-aa80-4f0164fa5600)

<br>

<pre><code>gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http:/[Target]/retro</code></pre>

<br>

![image](https://github.com/user-attachments/assets/d6db8c7d-17b6-4fe2-a368-0c294753ee01)


<br>

<pre><code>gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http:/[Target]/retro</wp-contentcode></pre>

<br>

![image](https://github.com/user-attachments/assets/f9b327ac-b8d3-4548-87f7-47186c2d0297)

<br>

<pre><code>gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http:/[Target]/retro</wp-contentcode></pre>
















