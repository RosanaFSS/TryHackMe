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

> 2.1. <em>Navigate to <code>/var/log/apache2</code></em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

![image](https://github.com/user-attachments/assets/b1165a89-bda6-4b95-bfcf-73618fabe02b)

<br>


> 2.2. <em>How many different tools made requests to the server?</em><br><a id='2.2'></a>
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
>> <code><strong>contact.php</strong></code>

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

![image](https://github.com/user-attachments/assets/dfd6be77-e61b-4bea-b716-66bb07de8a4a)

<br>

![image](https://github.com/user-attachments/assets/b6ce7ddf-4334-4ce4-ab75-24158709f95c)


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
>> <code><strong>sh -i</strong></code>

<br>

![image](https://github.com/user-attachments/assets/71db52e9-b41a-460b-87d1-2c561f68bbaf)

<br>

<br>
<h2>Task 5. User Accounts</h2>
<p>It looks like the command from the previous task was set up to run under the root2 account. This account doesn't make any sense as there should only be one root account. Wonder how it got there?<br>

There are a couple of locations where account information is stored on Linux distributions, including:</p>

<br>

<p>1. /etc/passwd  - contains the names of most of the accounts on the system.  Should have open read permissions and should not contain password hashes. <br>
2. /etc/shadow -  contains names but should also contain password hashes.  Should have strict permissions.</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 5.1. <em>What is the password of the second root account?</em><br><a id='5.1'></a>
>> <code><strong>sh -i</strong></code>

<br>

![image](https://github.com/user-attachments/assets/1d0c37aa-09bc-4720-8000-79dcdab44c75)

<p>If there is a x after the first colon, then it means that the password hash is stored in the /etc/shadow file</p>





















