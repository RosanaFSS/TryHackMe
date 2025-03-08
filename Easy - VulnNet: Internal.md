March 8, 2025<br>
Day 305<br>

<h2>VulNet: Internal</h2>
<p>VulnNet Entertainment learns from its mistakes, and now they have something new for you...</p>

<br>

```bash
:~/VulnNetInternal# echo 'Target_IP vulnet-internal' >> /etc/hosts
```

<br>

<p>Ran <code>nmap</code>, and discovered 13 ports open.<br>
- 22,ssh<br>
- 111,rpcbind<br></p>
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

```bash
~/VulnNetInternal# nmap -sC -sV -sS -A -O -p- -T5 vulnet-internal
...
Not shown: 65522 closed ports
PORT      STATE    SERVICE     VERSION
22/tcp    open     ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 5e:27:8f:48:ae:2f:f8:89:bb:89:13:e3:9a:fd:63:40 (RSA)
|   256 f4:fe:0b:e2:5c:88:b5:63:13:85:50:dd:d5:86:ab:bd (ECDSA)
|_  256 82:ea:48:85:f0:2a:23:7e:0e:a9:d9:14:0a:60:2f:ad (ED25519)
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



```bash

___________________

:~/Empline# wfuzz -u empline.thm -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -H "Host: FUZZ.empline.thm" --hc 404 --hw 914
...
// Discovered job --> job/.empline.thm

___________________

// updated /etc/hosts

___________________

:~/Empline# searchsploit opencats




```
