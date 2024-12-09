<h1>Daily Bugle</h1>


<br>

<pre><code>root@[THM AttackBox]:~/DailyBugle# nmap -sV [Target]
Starting Nmap 7.80 ( https://nmap.org ) at 2024-12-09 01:29 GMT
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.00032s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.4 (protocol 2.0)
80/tcp   open  http    Apache httpd 2.4.6 ((CentOS) PHP/5.6.40)
3306/tcp open  mysql   MariaDB (unauthorized)
MAC Address: 02:24:5A:22:50:D5 (Unknown)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 17.24 seconds
root@ip-10-10-38-201:~/DailyBugle# 
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/4bf5f9a9-9a21-40f4-93ef-6bc0eadfc221)

<br>

![image](https://github.com/user-attachments/assets/2083f2d2-7b76-4e90-adf2-4ae5a2f439dc)


<p><code>SpiderMan</code></p>

<br>

<pre><code>root@[THM AttackBox]:~/DailyBugle# gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u http://[Target]
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target]
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/images               (Status: 301) [Size: 235] [--> http://10.10.41.192/images/]
/templates            (Status: 301) [Size: 238] [--> http://10.10.41.192/templates/]
/media                (Status: 301) [Size: 234] [--> http://10.10.41.192/media/]
/modules              (Status: 301) [Size: 236] [--> http://10.10.41.192/modules/]
/bin                  (Status: 301) [Size: 232] [--> http://10.10.41.192/bin/]
/plugins              (Status: 301) [Size: 236] [--> http://10.10.41.192/plugins/]
/includes             (Status: 301) [Size: 237] [--> http://10.10.41.192/includes/]
/language             (Status: 301) [Size: 237] [--> http://10.10.41.192/language/]
/components           (Status: 301) [Size: 239] [--> http://10.10.41.192/components/]
/cache                (Status: 301) [Size: 234] [--> http://10.10.41.192/cache/]
/libraries            (Status: 301) [Size: 238] [--> http://10.10.41.192/libraries/]
/tmp                  (Status: 301) [Size: 232] [--> http://10.10.41.192/tmp/]
/layouts              (Status: 301) [Size: 236] [--> http://10.10.41.192/layouts/]
/administrator        (Status: 301) [Size: 242] [--> http://10.10.41.192/administrator/]
/cli                  (Status: 301) [Size: 232] [--> http://10.10.41.192/cli/]
Progress: 220557 / 220558 (100.00%)
===============================================================
Finished
===============================================================
root@[THM AttackBox]:~/DailyBugle# 
</code></pre>


<br>

![image](https://github.com/user-attachments/assets/2645fb28-89d8-42e8-9016-ba3ec8dd5917)

<br>

![image](https://github.com/user-attachments/assets/49fbb6fe-3ce0-459f-8e6b-5752e9eaf43a)


<br>



<pre><code>root@[THM AttackBox]:~/DailyBugle/ 
git clone https://github.com/rezasp/joomscan.git
root@[THM AttackBox]:~/DailyBugle/joomscan# perl joomscan.pl -u http://[Target]
...
[++] Joomla 3.7.0

...
...

[++] Admin page : http://[Target]/administrator/

[+] Checking robots.txt existing
[++] robots.txt is found
path : http://[Target]/robots.txt 

...
</code></pre>

<br>

<pre><code>https://github.com/XiphosResearch/exploits/tree/master/Joomblah
https://github.com/XiphosResearch/exploits/blob/master/Joomblah/joomblah.py
...

</code></pre>

![image](https://github.com/user-attachments/assets/2177abc8-80d6-447f-b24a-a9ea45129a2e)

<br>

![image](https://github.com/user-attachments/assets/08250356-8f16-4a11-8673-ec795f0c7071)

<br>


![image](https://github.com/user-attachments/assets/29f0cc0c-7630-4436-b86a-74ba3358cbfc)

<br>

<pre><code>apt install sqlmap
...
...
  
</code></pre>





