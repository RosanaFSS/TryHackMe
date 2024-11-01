<p align="center">October 31, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{178}}$$-day-streak in  <a href="https://tryhackme.com/r/p/Rosana">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Git Happens &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}}$$
</h1>
<p align="center">Boss wanted me to create a prototype, so here it is! We even used something called "version control" that made deploying this really easy!.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/githappens">Git Happens</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/cd2de457-e1bb-4619-96e1-4cd7d0173d0b">
  <img height="150px" src="https://github.com/user-attachments/assets/f086c6a1-74ff-4564-ba91-39adfcabed0f">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Walkthrough](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Super Secret Password](#1.1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [Room complete](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [My journey](#3)


<h2>Task 1. Capture the flag<a id='1'></a></h2>

<p>Can you find the password to the application?</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<p>I started enumerating with nmap.</p>

<ul style="list-style-type:square">
    <li><code>-sC</code>: run all the default scripts.</li>
    <li><code>-sV</code>: Find the version of services running on the target.</li>
    <li><code>-T4</code>: Aggressive scan to provide faster results.</li>
</ul></p>

<pre><code># sudo nmap -sC -sV -T4 [Target]

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-31 22:37 GMT
Nmap scan report for ip-[Target].eu-west-1.compute.internal ([Target])
Host is up (0.0010s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.14.0 (Ubuntu)
| http-git: 
|   [Target]:80/.git/
|     Git repository found!
|_    Repository description: Unnamed repository; edit this file 'description' to name the...
|_http-server-header: nginx/1.14.0 (Ubuntu)
|_http-title: Super Awesome Site!
MAC Address: 02:90:A7:6B:80:09 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.80 seconds
</code></pre><br>

<p>The port scan shows that the http service is running on <code>port 80</code> and a git repository can be accessed through [Target]<code>:80/.git/</code>!</p>
<br>
<p>Accessing [Target] we will find this ....</p>

![image](https://github.com/user-attachments/assets/f5f8f176-500a-46dc-af0e-2a3f5a99437c)

<p>This login page do not provide data entry.</p>

<p>Accessing [Target]<code>:80/.git/</code> we will find some folders exposed in <code>.git directory</code>.</p>

![image](https://github.com/user-attachments/assets/127315d6-15ca-4452-9507-1ef5a56cae7c)

<p>After a bit of research I learned that gitdumper.sh is adequate for this study case.</p>

<pre><code># root@ip-[Attack]:/GitHappens# git clone https://github.com/internetwache/GitTools/
Cloning into 'GitTools'...
remote: Enumerating objects: 242, done.
remote: Counting objects: 100% (33/33), done.
remote: Compressing objects: 100% (23/23), done.
remote: Total 242 (delta 9), reused 27 (delta 7), pack-reused 209 (from 1)
Receiving objects: 100% (242/242), 56.46 KiB | 2.57 MiB/s, done.
Resolving deltas: 100% (88/88), done.
</code></pre><br>


<pre><code># root@ip-[Attack]:/GitHappens# ls
GitTools
root@ip-[Attack]:/GitHappens# cd GitTools
root@ip-[Attack]:/GitHappens/GitTools# ls
Dumper  Extractor  Finder  LICENSE.md  README.md
root@ip-[Attack]:/GitHappens/GitTools# cd Dumper
root@ip-[Attack]:/GitHappens/GitTools/Dumper# ls
gitdumper.sh  README.md
root@ip-[Attack]:/GitHappens/GitTools/Dumper# chmod +x gitdumper.sh
root@ip-[Attack]:/GitHappens/GitTools/Dumper# ./gitdumper.sh http://[Target]/.git/ GitHappens
###########
# GitDumper is part of https://github.com/internetwache/GitTools
#
# Developed and maintained by @gehaxelt from @internetwache
#
# Use at your own risk. Usage might be illegal in certain circumstances. 
# Only for educational purposes!
###########


*] Destination folder does not exist
[+] Creating GitHappens/.git/
[+] Downloaded: HEAD
[-] Downloaded: objects/info/packs
[+] Downloaded: description
[+] Downloaded: config
[-] Downloaded: COMMIT_EDITMSG
[+] Downloaded: index
[+] Downloaded: packed-refs
[+] Downloaded: refs/heads/master
[-] Downloaded: refs/remotes/origin/HEAD
[-] Downloaded: refs/stash
[+] Downloaded: logs/HEAD
[+] Downloaded: logs/refs/heads/master
[-] Downloaded: logs/refs/remotes/origin/HEAD
[-] Downloaded: info/refs
[+] Downloaded: info/exclude
[-] Downloaded: /refs/wip/index/refs/heads/master
[-] Downloaded: /refs/wip/wtree/refs/heads/master
[+] Downloaded: objects/d0/b3578a628889f38c0affb1b75457146a4678e5
[-] Downloaded: objects/00/00000000000000000000000000000000000000
[+] Downloaded: objects/b8/6ab47bacf3550a5450b0eb324e36ce46ba73f1
[+] Downloaded: objects/77/aab78e2624ec9400f9ed3f43a6f0c942eeb82d
...
</code></pre><br>

<pre><code># root@ip-[Attack]:/GitHappens/GitTools/Dumper# ls
gitdumper.sh  GitHappens  README.md
root@ip-[Attack]:/GitHappens/GitTools/Dumper# cd GitHappens
root@ip-[Attack]:/GitHappens/GitTools/Dumper/GitHappens# ls
root@ip-[Attack]:/GitHappens/GitTools/Dumper/GitHappens# ls -la
total 12
drwxr-xr-x 3 root root 4096 Oct 31 23:17 .
drwxr-xr-x 3 root root 4096 Oct 31 23:17 ..
drwxr-xr-x 6 root root 4096 Oct 31 23:17 .git
root@ip-[Attack]:/GitHappens/GitTools/Dumper/GitHappens# 
</code></pre><br>

<pre><code># root@ip-[Attack]:/GitHappens/GitTools/Dumper/GitHappens# git log
commit d0b3578a628889f38c0affb1b75457146a4678e5 (HEAD -> master, tag: v1.0)
Author: Adam Bertrand <hydragyrum@gmail.com>
Date:   Thu Jul 23 22:22:16 2020 +0000

    Update .gitlab-ci.yml

commit 77aab78e2624ec9400f9ed3f43a6f0c942eeb82d
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Fri Jul 24 00:21:25 2020 +0200

    add gitlab-ci config to build docker file.

commit 2eb93ac3534155069a8ef59cb25b9c1971d5d199
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Fri Jul 24 00:08:38 2020 +0200

    setup dockerfile and setup defaults.

commit d6df4000639981d032f628af2b4d03b8eff31213
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Thu Jul 23 23:42:30 2020 +0200

    Make sure the css is standard-ish!

commit d954a99b96ff11c37a558a5d93ce52d0f3702a7d
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Thu Jul 23 23:41:12 2020 +0200

    re-obfuscating the code to be really secure!
commit bc8054d9d95854d278359a432b6d97c27e24061d
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Thu Jul 23 23:37:32 2020 +0200

    Security says obfuscation isn't enough.
    
    They want me to use something called 'SHA-512'

commit e56eaa8e29b589976f33d76bc58a0c4dfb9315b1
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Thu Jul 23 23:25:52 2020 +0200

    Obfuscated the source code.
    
    Hopefully security will be happy!

commit 395e087334d613d5e423cdf8f7be27196a360459
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Thu Jul 23 23:17:43 2020 +0200

    Made the login page, boss!

commit 2f423697bf81fe5956684f66fb6fc6596a1903cc
Author: Adam Bertrand <hydragyrum@gmail.com>
Date:   Mon Jul 20 20:46:28 2020 +0000

    Initial commit

</code></pre><br>


<p>In the last step I found the message ‘Made the login page, boss!’. Its ID is <code>395e087334d613d5e423cdf8f7be27196a360459</code>.
<p>Used <code>git show [ID].</code></p>

<pre><code># root@ip-[Attack]:/GitHappens/GitTools/Dumper/GitHappens# git show 395e087334d613d5e423cdf8f7be27196a360459
commit 395e087334d613d5e423cdf8f7be27196a360459
Author: Hydragyrum <hydragyrum@gmail.com>
Date:   Thu Jul 23 23:17:43 2020 +0200

    Made the login page, boss!

diff --git a/css/style.css b/css/style.css
...

+body:before {
+  content: "";
+  position: absolute;
+  top: 0;
+  left: 0;
+  height: 100%;
+  width: 100%;
+  background-image: url(data:image/png;base64,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);
+  opacity: 0.3;
  }
+
+.login-form {
...
+::-webkit-input-placeholder {
+  color: #8f8f8f;
diff --git a/dashboard.html b/dashboard.html
new file mode 100644
index 0000000..e38d9df
--- /dev/null
+++ b/dashboard.html
...
+  </head>
+  <body onload="checkCookie()">
+    <p class="rainbow-text">Awesome! Use the password you input as the flag!</p>
...
+<!DOCTYPE html>
+<html lang="en">
+  <head>
+    <meta charset="UTF-8" />
+    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
+    <title>Super Awesome Site!</title>
+    <link rel="stylesheet" href="/css/style.css">
...
+
+   
+
+    <script>
+      function login() {
+        let form = document.getElementById("login-form"); 
+        console.log(form.elements);
+        let username = form.elements["username"].value;
+        let password = form.elements["password"].value;
+        if (
+          username === "admin" &&
+          password === "Th1s_1s_4_L0ng_4nd_S3cur3_P4ssw0rd!" ----------------------------------------------
+        ) {
+          document.cookie = "login=1";
+          window.location.href = "/dashboard.html";
+        } else {
+          document.getElementById("error").innerHTML =
+            "INVALID USERNAME OR PASSWORD!";
+            "INVALID USERNAME OR PASSWORD!";
+        }
+      }
+    </script>
+  </body>
+</html>
(END)
</code></pre>

> 1.1. <em>Find the Super Secret Password.</em><br><a id='1.1'></a>
>> <code><strong>Th1s_1s_4_L0ng_4nd_S3cur3_P4ssw0rd!____</strong></code>

<br>

<h2>Room Complete<a id='2'></a></h2>
<p>Keep learning, keep growing!<br>

![image](https://github.com/user-attachments/assets/c856d2a2-e606-45ed-9c82-297f5498d80d)

<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

![image](https://github.com/user-attachments/assets/02ff2922-6122-4568-b4b1-852b863fae99)


<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
