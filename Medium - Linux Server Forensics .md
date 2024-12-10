<h1>Linux Server Forensics</h1>

<br>
<h2>Task 1. Deploy the first VM</h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 1.1. <em>Deploy the machine and log in to the VM using the provided credentials.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<br>
<h2>Task 2. Apache Log Analysis I </h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 2.1. <em>Navigate to /var/log/apache2</em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

![image](https://github.com/user-attachments/assets/b1165a89-bda6-4b95-bfcf-73618fabe02b)

<br>


> 2.2. <em>Navigate to /var/log/apache2</em><br><a id='2.2'></a>
>> <code><strong>______________</strong></code>

<br>

> 2.3. <em>Name a path requested by Nmap.</em><br><a id='2.3'></a>
>> <code><strong>/nmaplowercheck1618912425</strong></code>

<br>

<pre><code>$ cat access.log | grep nmap</code></pre>

![image](https://github.com/user-attachments/assets/d51f87d6-7296-4930-a899-95da1aeeb252)



<br>
<h2>Task 3. Web Server Analysis</h2>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 3.1. <em>What page allows users to upload files?</em><br><a id='3.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

![image](https://github.com/user-attachments/assets/aa3f9c3b-c5a7-4766-8db9-63ce4b35c2ed)

<br>

![image](https://github.com/user-attachments/assets/8675fa7f-61d3-4d3f-9085-03683c9a1565)

<br>

![image](https://github.com/user-attachments/assets/28bd18b6-e183-4831-ba41-40ed656d061d)


<br>

> 3.2. <em>What IP uploaded files to the server?</em><br><a id='3.2'></a>
>> <code><strong>192.168.56.24</strong></code>

<br>

<pre><code>$ cat access.log | grep 'POST'</code></pre>

![image](https://github.com/user-attachments/assets/1451a7e4-be76-4400-b2ea-7a64cfb98bad)

<br>

> 3.3. <em>Who left an exposed security notice on the server?</em><br><a id='3.2'></a>
>> <code><strong>Fred</strong></code>

<br>

![image](https://github.com/user-attachments/assets/1a26ca11-aabb-4279-bc3a-f2d67e92057b)

<br>


<br>
<h2>Task 4. Persistence Mechanisms I</h2>
<p>﻿It looks like our attacker got in via Remote File Inclusion (RFI). It's best to look around the system itself now for any evidence of persistence.</p>
- cron<vr></vr>
- Services/systemd<br>
- bashrc<br>
- Kernel modules <br>
- SSH keys<br>

<p>Cron is one of the more common methodologies, so it's probably best to start there.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 4.1. <em>What command and option did the attacker use to establish a backdoor?</em><br><a id='4.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

![image](https://github.com/user-attachments/assets/71db52e9-b41a-460b-87d1-2c561f68bbaf)














