<p align="center">December 10, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{218}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Linux Server Forensics}}$$
</h1>
<p align="center">Learn about digital forensics artefacts found on Linux servers by analysing a compromised server.</p>
<p align="center">Access this FREE TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/linuxserverforensics">Linux Server Forensics</a>.</p>

                                                              
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/3851418f-e786-4491-a101-372a873735ef">
  <img width="700px" src="https://github.com/user-attachments/assets/52026e78-4de5-4691-a9ff-5c8d96bb1ac0">
</p>

<br>


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
>> <code><strong>2</strong></code>

<br>

<pre><code>$ cat access.log | more</code></pre>

<br>

<pre><code>$ cat access.log | more</code></pre>

<br>

![image](https://github.com/user-attachments/assets/ebca6d80-9300-4cf3-8bd5-a70f7c9a402d)

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
>> <code><strong>mrcake</strong></code>

<br>

![image](https://github.com/user-attachments/assets/1d0c37aa-09bc-4720-8000-79dcdab44c75)

<p>If there is a x after the first colon, then it means that the password hash is stored in the /etc/shadow file</p>

<br>

![image](https://github.com/user-attachments/assets/74693f33-76d8-42b0-8820-6e4625b034fe)

<br>

<pre><code>root2:WVLY0mgH0RtUI:0:0:root:/root:/bin/bash</code></pre>

<br>

<pre><code>WVLY0mgH0RtUI</code></pre>

<br>

<pre><code>$ nano root2.txt
$ john root2.txt
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/7ea5f634-dcf2-4d2c-a133-761777151122)


<br>
<h2>Task 6. Deploy the second VM</h2>
<p>Wow, it looks like they got hacked again! Better have another look; the credentials are the same as last time:</p>

<p>1. [Target IP<br>
2. 'fred'<br>
3. 'FredRules!'</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 6.1. <em> Deploy the second machine and log in to the VM using the provided credentials.</em><br><a id='6.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>
<h2>Task 7. Apache Log Analysis II</h2>

<p>The log file is a lot smaller this time around, so it looks like our attacker was a little more subtle. There also don't appear to be obvious user agents anymore. Fortunately, there are a few other ways of identifying traffic originating from scanners. The time between each request is a good metric for most tools. You can also identify individual tools from signatures left in the requests; for example, Nmap will send HTTP requests with a random non-standard method when performing certain enumeration tasks. More aggressive tools can also be identified simply from the number of requests sent during any given attack; directory brute-forcing tools are a perfect example of this and are likely to fall foul of banning systems like fail2ban.<br>

A poorly designed site may also freely grant valuable information without the need for aggressive tools. In this case, the site uses sequential IDs for all of the products making. It easily scrapes every single product or finds the total size of the product database by simply increasing the product ID until a 404 error occurs.</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 7.1. <em>Name one of the non-standard HTTP Requests..</em><br><a id='7.1'></a>
>> <code><strong>GXWR</strong></code>

<br>

![image](https://github.com/user-attachments/assets/18cc88bb-27ca-4db1-bad3-aab8e53f89b1)

<br>


![image](https://github.com/user-attachments/assets/782bc026-083d-487a-93d0-a15736ada355)


<br>

> 7.2. <em>At what time was the Nmap scan performed? (format: HH:MM:SS)</em><br><a id='7.2'></a>

![image](https://github.com/user-attachments/assets/05108547-861a-4e63-87ad-c51b43958ec3)


<br>

![image](https://github.com/user-attachments/assets/f2efeac4-9ba8-4ce5-9143-b2560613617f)

<br>
<h2>Task 8. Persistence Mechanisms II</h2>
<p>The adversary has been a little smarter this time around. If any backdoor exists, it's likely to be more subtle. SSH-keys are another excellent way of maintaining access, so it might be worth looking for additions to the authorized_keys file. </p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 8.1. <em>What username and hostname combination can be found in one of the authorized_keys files? (format: username@hostname)</em><br><a id='8.1'></a>
>> <code><strong>GXWR</strong></code>

<br>

![image](https://github.com/user-attachments/assets/a0ba386d-cbbe-464a-9c6c-8e3a50b11120)

<br>


![image](https://github.com/user-attachments/assets/704f89e0-99a9-4726-83d3-8565e1e98704)

<br>

![image](https://github.com/user-attachments/assets/03bb3330-4a25-478c-982a-f823cabf134b)

<br>
<h2>Task 9. Program Execution History</h2>
<p>Of course, adding a public key to root's authorized_keys requires root-level privileges so, it may be best to look for more evidence of privilege escalation. In general, Linux stores a tiny amount of programme execution history when compared to Windows but, there are still a few valuable sources, including:</p>

<p>1. bash_history - Contains a history of commands run in bash; this file is well known, easy to edit and sometimes disabled by default.<br>
2. auth.log - Contains a history of all commands run using sudo.<br>
3. history.log (apt) - Contains a history of all tasks performed using apt - is useful for tracking programme installation and removal.</p>

<p>systemd services also keep logs in the journald system; these logs are kept in a binary format and have to be read by a utility like journalctl. This binary format comes with some advantages; however, each journal is capable of validating itself and is harder to modify.</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 9.1. <em>What is the first command present in root's bash_history file?</em><br><a id='9.1'></a>
>> <code><strong>nano /etc/passwd</strong></code>

<br>

![image](https://github.com/user-attachments/assets/3d2f6f4d-c260-4bc9-9d13-5e43a2a52dbb)

<br>

<br>
<h2>Task 10. Deploy Teh Final VM</h2>
<p>This is getting a little annoying now. The credentials are still the same:</p>

<p>1. [Target IP<br>
2. 'fred'<br>
3. 'FredRules!'</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 10.1. <em>Deploy the final machine and log in to the VM using the provided credentials.</em><br><a id='10.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>
<h2>Task 11. Persistance Mechanisms III</h2>
<p>Malware can also maintain persistence using systemd as scripts run under systemd can run in the background and restart whenever the system is booted or whenever the script crashes. It is also relatively easy to conceal malicious scripts as they can blend in with other services. systemd services are defined in .service files which can contain:</p>

<p>1. The command that runs whenever the service starts<br>
2. The user the service runs as<br>
3. An optional description <br></p>

<p>In this case, the malware is pretty obvious as it seems to be printing errors to the screen so, there is no way that it is dormant. Running systemctl will list all of the services loaded into the system. And much like Windows, there's usually a lot of them. It might be worth adding --type=service --state=active to the command as it will reduce the list to services that are running. Once the name of a suspicious service is found, more information can then be extracted by running systemctl status <code>service name</code> . </p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 11.1. <em>Deploy the final machine and log in to the VM using the provided credentials.</em><br><a id='11.1'></a>
>> <code><strong>gh0st_1n_the_machine</strong></code>

<br>

![image](https://github.com/user-attachments/assets/98ab1e68-f703-4897-b5a0-15b8c93e02ea)

<pre><code>rt /etc/cron.monthly )                                                         
#                                                                              
                                                                               
                                                                               
Hmm nothing here either
                                                                               
fred@acmeweb:~$                                                                                
Seems to be running all the time, so it could be a broken service.
                                                                               
                                                                               
It might be worth running systemctl -l and, looking for things out of the ordinary
                                                                               
                                                                               
Oh by they way your computer isn't sentient, it's just haunted so there's nothing to worry about
                                                                               
                                                                               
                                                                               
                                                                               
INFO!:  RETICULATING SPLINES
                                                                               
                                                                               
INFO!:  RETICULATING SPLINES
                                                                               
                                                                               
\u8abf\u8a66!: \u5982\u679c\u767c\u751f\u5806\u68e7\u885d\u7a81\uff0c\u5247\u7121\u6cd5\u555f\u7528\u5806\u68e7!!!
                                                                               

fred@acmeweb:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  1.6  0.8 159512  8764 ?        Ss   04:57   0:05 /sbin/init maybe-ubiquity
root         2  0.0  0.0      0     0 ?        S    04:57   0:00 [kthreadd]
root         4  0.0  0.0      0     0 ?        I<   04:57   0:00 [kworker/0:0H]
root         5  0.0  0.0      0     0 ?        I    04:57   0:00 [kworker/u30:0]
root         6  0.0  0.0      0     0 ?        I<   04:57   0:00 [mm_percpu_wq]
root         7  0.0  0.0      0     0 ?        S    04:57   0:00 [ksoftirqd/0]
root         8  0.0  0.0      0     0 ?        I    04:57   0:00 [rcu_sched]
root         9  0.0  0.0      0     0 ?        I    04:57   0:00 [rcu_bh]
root        10  0.0  0.0      0     0 ?        S    04:57   0:00 [migration/0]
root        11  0.0  0.0      0     0 ?        S    04:57   0:00 [watchdog/0]
root        12  0.0  0.0      0     0 ?        S    04:57   0:00 [cpuhp/0]
root        13  0.0  0.0      0     0 ?        S    04:57   0:00 [kdevtmpfs]
root        14  0.0  0.0      0     0 ?        I<   04:57   0:00 [netns]
root        15  0.0  0.0      0     0 ?        S    04:57   0:00 [rcu_tasks_kthre]
root        16  0.0  0.0      0     0 ?        S    04:57   0:00 [kauditd]
root        17  0.0  0.0      0     0 ?        S    04:57   0:00 [khungtaskd]
root        18  0.0  0.0      0     0 ?        S    04:57   0:00 [oom_reaper]
root        19  0.0  0.0      0     0 ?        I<   04:57   0:00 [writeback]
root        20  0.0  0.0      0     0 ?        S    04:57   0:00 [kcompactd0]
root        21  0.0  0.0      0     0 ?        SN   04:57   0:00 [ksmd]
root        22  0.0  0.0      0     0 ?        SN   04:57   0:00 [khugepaged]
root        23  0.0  0.0      0     0 ?        I<   04:57   0:00 [crypto]
root        24  0.0  0.0      0     0 ?        I<   04:57   0:00 [kintegrityd]
root        25  0.0  0.0      0     0 ?        I<   04:57   0:00 [kblockd]
root        26  0.0  0.0      0     0 ?        I<   04:57   0:00 [ata_sff]
root        27  0.0  0.0      0     0 ?        I<   04:57   0:00 [md]
root        28  0.0  0.0      0     0 ?        I<   04:57   0:00 [edac-poller]
root        29  0.0  0.0      0     0 ?        I<   04:57   0:00 [devfreq_wq]
root        30  0.0  0.0      0     0 ?        I<   04:57   0:00 [watchdogd]
root        31  0.0  0.0      0     0 ?        I    04:57   0:00 [kworker/0:1]
root        32  0.0  0.0      0     0 ?        I    04:57   0:00 [kworker/u30:1]
root        34  0.0  0.0      0     0 ?        S    04:57   0:00 [kswapd0]
root        35  0.0  0.0      0     0 ?        I<   04:57   0:00 [kworker/u31:0]
root        36  0.0  0.0      0     0 ?        S    04:57   0:00 [ecryptfs-kthrea]
root        78  0.0  0.0      0     0 ?        I<   04:57   0:00 [kthrotld]
root        79  0.0  0.0      0     0 ?        I<   04:57   0:00 [acpi_thermal_pm]
root        80  0.0  0.0      0     0 ?        S    04:57   0:00 [xenbus]
root        81  0.0  0.0      0     0 ?        S    04:57   0:00 [xenwatch]
root        82  0.0  0.0      0     0 ?        S    04:57   0:00 [scsi_eh_0]
root        83  0.0  0.0      0     0 ?        I<   04:57   0:00 [scsi_tmf_0]
root        84  0.0  0.0      0     0 ?        S    04:57   0:00 [scsi_eh_1]
root        85  0.0  0.0      0     0 ?        I<   04:57   0:00 [scsi_tmf_1]
root        86  0.0  0.0      0     0 ?        I    04:57   0:00 [kworker/u30:2]
root        87  0.0  0.0      0     0 ?        I    04:57   0:00 [kworker/u30:3]
root        91  0.0  0.0      0     0 ?        I<   04:57   0:00 [ipv6_addrconf]
root       100  0.0  0.0      0     0 ?        I<   04:57   0:00 [kstrp]
root       117  0.0  0.0      0     0 ?        I<   04:57   0:00 [charger_manager]
root       170  0.0  0.0      0     0 ?        I    04:57   0:00 [kworker/0:2]
root       198  0.0  0.0      0     0 ?        I<   04:57   0:00 [ttm_swap]
root       212  0.0  0.0      0     0 ?        I<   04:57   0:00 [kdmflush]
root       214  0.0  0.0      0     0 ?        I<   04:57   0:00 [bioset]
root       299  0.0  0.0      0     0 ?        I<   04:57   0:00 [raid5wq]
root       353  0.0  0.0      0     0 ?        S    04:57   0:00 [jbd2/dm-0-8]
root       354  0.0  0.0      0     0 ?        I<   04:57   0:00 [ext4-rsv-conver]
root       407  0.0  0.0      0     0 ?        I<   04:57   0:00 [kworker/0:1H]
root       424  0.2  1.2  94728 12452 ?        S<s  04:57   0:00 /lib/systemd/systemd-journald
root       441  0.0  0.0      0     0 ?        I<   04:57   0:00 [iscsi_eh]
root       443  0.0  0.1 105912  1928 ?        Ss   04:57   0:00 /sbin/lvmetad -f
root       448  0.0  0.0      0     0 ?        I<   04:57   0:00 [ib-comp-wq]
root       449  0.0  0.0      0     0 ?        I<   04:57   0:00 [ib-comp-unb-wq]
root       450  0.0  0.0      0     0 ?        I<   04:57   0:00 [ib_mcast]
root       451  0.0  0.0      0     0 ?        I<   04:57   0:00 [ib_nl_sa_wq]
root       452  0.0  0.0      0     0 ?        I<   04:57   0:00 [rdma_cm]
root       453  0.4  0.4  45492  4384 ?        Ss   04:57   0:01 /lib/systemd/systemd-udevd
root       595  0.0  0.0      0     0 ?        S    04:57   0:00 [jbd2/xvda2-8]
root       596  0.0  0.0      0     0 ?        I<   04:57   0:00 [ext4-rsv-conver]
systemd+   621  0.0  0.2 141788  2972 ?        Ssl  04:57   0:00 /lib/systemd/systemd-timesyncd
systemd+   727  0.0  0.5  79916  5040 ?        Ss   04:57   0:00 /lib/systemd/systemd-networkd
systemd+   741  0.0  0.5  70496  5048 ?        Ss   04:57   0:00 /lib/systemd/systemd-resolved
root       827  0.0  0.1  95548  1620 ?        Ssl  04:58   0:00 /usr/bin/lxcfs /var/lib/lxcfs/
root       840  0.2  1.6 169104 17084 ?        Ssl  04:58   0:00 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers
root       848  0.0  0.5  70452  5828 ?        Ss   04:58   0:00 /lib/systemd/systemd-logind
root       849  0.0  0.6 286260  6744 ?        Ssl  04:58   0:00 /usr/lib/accountsservice/accounts-daemon
root       854  0.0  1.4 1236728 14952 ?       Ssl  04:58   0:00 /usr/bin/amazon-ssm-agent
daemon     855  0.0  0.2  28340  2476 ?        Ss   04:58   0:00 /usr/sbin/atd -f
message+   856  0.0  0.4  50064  4568 ?        Ss   04:58   0:00 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
syslog     878  0.0  0.4 263044  4056 ?        Ssl  04:58   0:00 /usr/sbin/rsyslogd -n
root       885  0.0  0.3  30036  3188 ?        Ss   04:58   0:00 /usr/sbin/cron -f
root       895  0.2  1.9 185952 19984 ?        Ssl  04:58   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
root       908  0.0  0.2  14672  2364 ttyS0    Ss+  04:58   0:00 /sbin/agetty -o -p -- \u --keep-baud 115200,38400,9600 ttyS0 vt220
root       914  0.0  0.1  14896  2000 tty1     Ss+  04:58   0:00 /sbin/agetty -o -p -- \u --noclear tty1 linux
root       928  0.0  0.7 291452  7208 ?        Ssl  04:58   0:00 /usr/lib/policykit-1/polkitd --no-debug
root       935  0.0  0.5  72308  5568 ?        Ss   04:58   0:00 /usr/sbin/sshd -D
root       942  0.3  2.8 1177752 28768 ?       Sl   04:58   0:01 /usr/bin/ssm-agent-worker
root       964  0.0  1.7 333728 17232 ?        Ss   04:58   0:00 /usr/sbin/apache2 -k start
www-data   971  0.0  0.9 338128  9280 ?        S    04:58   0:00 /usr/sbin/apache2 -k start
www-data   975  0.0  0.9 338128  9280 ?        S    04:58   0:00 /usr/sbin/apache2 -k start
www-data   976  0.0  0.9 338128  9280 ?        S    04:58   0:00 /usr/sbin/apache2 -k start
www-data   977  0.0  0.9 338128  9280 ?        S    04:58   0:00 /usr/sbin/apache2 -k start
www-data   978  0.0  0.9 338128  9280 ?        S    04:58   0:00 /usr/sbin/apache2 -k start
root      1302  0.0  0.7 105696  7120 ?        Ss   05:01   0:00 sshd: fred [priv]
fred      1314  0.0  0.7  76516  7388 ?        Ss   05:01   0:00 /lib/systemd/systemd --user
fred      1320  0.0  0.2 193492  2272 ?        S    05:01   0:00 (sd-pam)
fred      1448  0.0  0.5 107992  5532 ?        S    05:01   0:00 sshd: fred@pts/0
fred      1449  0.0  0.5  21464  5044 pts/0    Ss   05:01   0:00 -bash
root      1465  0.0  0.5  13496  5152 ?        Ss   05:01   0:00 /bin/bash /etc/network/ZGtsam5hZG1ua2Fu.sh
root      1672  0.0  0.0   6184   788 ?        S    05:03   0:00 sleep 10
fred      1673  0.0  0.3  38380  3592 pts/0    R+   05:03   0:00 ps aux
</code></pre>

<br>

<pre><code>/bin/bash /etc/network/ZGtsam5hZG1ua2Fu.sh</code></pre>

<br>

<pre><code>fred@acmeweb:~$ cat /etc/network/ZGtsam5hZG1ua2Fu.sh
##[gh0st_1n_the_machine]
## 
declare -a error_messages
error_messages[1]='ATTENTION!: THE BITBUCKET IS ALMOST FULL'
error_messages[2]='ACHTUNG!: DAS KOMPUTERMASCHINE IS NICHT GUD'
error_messages[3]='WARNING!: THE RAM FLANGES ARE IN THE OFF POSITION SAFE OPERATION OF RAM DRIVER IS NOT GUARANTEED!'
error_messages[4]='ERROR!: THE STACK ARRANGER IS NOT ENABLED BEWARE OF STACK COLLISIONS'
error_messages[5]='\u8abf\u8a66!: \u5982\u679c\u767c\u751f\u5806\u68e7\u885d\u7a81\uff0c\u5247\u7121\u6cd5\u555f\u7528\u5806\u68e7!!!'
error_messages[6]='INFO!:  PURGING RAM BITS'
error_messages[7]='INFO!:  NODE GRAPH OUT OF DATE REBUILDING'
error_messages[8]='INFO!:  RETICULATING SPLINES'
error_messages[9]='WARNING!: DIHYDROGEN MONOXIDE DETECTED IN ATMOSPHERE'
error_messages[10]='INFO!: VENTING OXYGEN'
error_messages[11]='WARNING!: /dev/null IS 95% UTILIZED'
error_messages[12]='METTERE IN GUARDIA!: LE FLANGE DEL RAM SONO IN POSIZIONE OFF IL FUNZIONAMENTO SICURO DEL RAM DRIVER NON È GARANTITO!'


print_errors(){
    for i in {1..10000}; do
    tput setaf 1; wall -n "${error_messages[RANDOM%11]}" ; tput setaf  7;
    sleep 10
    if [[ $i -eq 3 ]]; then
        introduce_self
    fi
    done
}

introduce_self(){
    wall -n "Wow this system is really broken huh?"
    sleep 4
    wall -n "Wonder if I can fix it"
    sleep 4
    wall -n "Gonna borrow your shell for a second"
    sleep 4
    wall -n "root@acmeweb:~# ls"
    ls -al ~ | wall -n
    sleep 4
    wall -n "Hmm"
    sleep 4
    wall -n "Nothing suspicious here"
    wall -n "root@acmeweb:~# ps"
    ps
    wall -n "Nothing strange here either."
    sleep 4
    wall -n "root@acmeweb:~# cd /etc"
    sleep 2
    wall -n "root@acmeweb:/etc/# ls -al"
    ls -al /etc/ | wall -n
    sleep 4
    wall -n "Wonder if theres anyting in the crontab"
    sleep 4
    wall -n "root@acmweb:/etc/ cat crontab"
    cat /etc/crontab | wall -n
    sleep 4
    wall -n "Hmm nothing here either"
    sleep 4 
    wall -n "Seems to be running all the time, so it could be a broken service."
    sleep 4
    wall -n "It might be worth running systemctl -l and, looking for things out of the ordinary"
    sleep 4
    wall -n "Oh by they way your computer isn't sentient, it's just haunted so there's nothing to worry about"
    sleep 4
    cowsay -f ghostbusters "Just don't call these guys" | wall -n
}
print_errors
fred@acmeweb:~$                                                                                
INFO!:  NODE GRAPH OUT OF DATE REBUILDING
</code></pre>

<br>

<br>
<h2>Room Completed</h2>
<p>Keep learning, keep growing!<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/846af7ae-e0d2-4c29-bb55-fef9f05eb39d"></p>


<br>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/0e260d01-ea16-45bc-b289-156a46b0c819"></p>


<br>
<h2>My Journey</h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 10, 2024 | 218      |       977 th |        20 th |    2,369 th |      27 th | 60,430   |       463 |



<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>

<p align="center"> <img width="800px" src="https://github.com/user-attachments/assets/4696ffdd-1f8f-4c72-928a-d3ddfe4013f8"></p>

