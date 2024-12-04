<h5 align="center">December 4, 2024<br>
Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{211}}$$-day-streak in  <a href="https://tryhackme.com/">TryHackMe</a>.</h5>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{Advent of Cyber 2024}}$$</h1>

<h5 align="center">Dive into the wonderful world of cyber security by engaging<br>
in festive beginner-friendly exercises every day in the lead-up to Christmas!</h5>

<p align="center">
<img height="90px" hspace="20" src="https://github.com/user-attachments/assets/0d8d7f29-525a-49ad-85ba-9223bdec089b">
<img width="500px" src="https://github.com/user-attachments/assets/57999429-f784-46a1-81ab-4d68041f470f"></p>

<p align="center">Access this 🆓 TryHackMe CTF challenge clicking <a href="https://tryhackme.com/r/room/adventofcyber2024">Advent of Cyber 2024</a>.</p>

<h2 align="center"> $$\textcolor{yellow}{\textnormal{Day 4 - Atomic Red Team}}$$<br>
$$\textcolor{yellow}{\textnormal{I’m all atomic inside!}}$$</h2>

<p align="center"><img width="700px" src="https://github.com/user-attachments/assets/c81cd5bb-2ded-4166-9a45-45bed67cd3dd"></p>

<p>SOC-mas is approaching! And the town of Warewille started preparations for the grand event.<br>

Glitch, a quiet, talented security SOC-mas engineer, had a hunch that these year's celebrations would be different. With looming threats, he decided to revamp the town's security defences. Glitch began to fortify the town's security defences quietly and meticulously. He started by implementing a protective firewall, patching vulnerabilities, and accessing endpoints to patch for security vulnerabilities. As he worked tirelessly, he left "breadcrumbs," small traces of his activity.<br>

Unaware of Glitch's good intentions, the SOC team spotted anomalies: Logs showing admin access, escalation of privileges, patched systems behaving differently, and security tools triggering alerts. The SOC team misinterpreted the system modifications as a sign of an insider threat or rogue attacker and decided to launch an investigation using the Atomic Red Team framework.</p>


<p align="center"><img src="https://github.com/user-attachments/assets/f054e181-2496-4ace-bb46-244099d02cae" width="400"></p>

<h3><strong>Learning Objectives</strong></h3>
<p>While it might seem like using the SOC superpower makes things super easy, that is not always the case. There are cases which can act as Kryptonite to the SOC superpower
    
<ul style="list-style-type:square">
    <li>Learn how to identify malicious techniques using the MITRE ATT&CK framework.</li>
    <li>Learn about how to use Atomic Red Team tests to conduct attack simulations.</li>
    <li>Understand how to create alerting and detection rules from the attack tests.</li>
</ul></p>

<h3><strong>Connecting to the Machine</strong></h3>

<p>Before moving forward, review the questions in the connection card below:</p>

<p align="center"><img width="300px" src="https://github.com/user-attachments/assets/cddb96af-873f-4217-815f-d108c56fcea8"></p>

<p>Click on the green <code>Start Machine</code> button below to start the virtual machine machine and wait 1-2 minutes for the system to boot completely in a split-screen view.</p>

<p><code>Start Machine</code></p>

<p>YIf the virtual machine isn't visible, use the blue <code>Show Split View</code> button at the top of the page.<br>

Additionally, if you wish to connect to the machine via RDP, use the credentials below:</p>

<p align="center"><img width="300px" src="https://github.com/user-attachments/assets/278d53a8-148f-4323-bec8-dfdc94cd205b"></p>

<p>The VM has Atomic Red Team and Sysmon installed. This will allow us to emulate an attack using TTPs described in the MITRE ATT&CK framework.</p>

<br>
<br>
<h2><strong>Detection Gaps</strong></h2>
<p>While it might be the utopian dream of every blue teamer, we will rarely be able to detect every attack or step in an attack kill chain. This is a reality that all blue teamers face: there are gaps in their detection. But worry not! These gaps do not have to be the size of black holes; there are things we can do to help make these gaps smaller.<br>

Detection gaps are usually for one of two main reasons:</p>

- <code>Security is a cat-and-mouse game</code>. As we detect more, the threat actors and red teamers will find new sneaky ways to thwart our detection. We then need to study these novel techniques and update our signature and alert rules to detect these new techniques.
- <code>The line between anomalous and expected behaviour is often very fine and sometimes even has significant overlap</code>. For example, let's say we are a company based in the US. We expect to see almost all of our logins come from IP addresses in the US. One day, we get a login event from an IP in the EU, which would be an anomaly. However, it could also be our CEO travelling for business. This is an example where normal and malicious behaviour intertwine, making it hard to create accurate detection rules that would not have too much noise.

<p>Blue teams constantly refine and improve their detection rules to close the gaps they experience due to the two reasons mentioned above. Let's take a look at how this can be done!</p>


<br>
<br>
<h2><strong>Cyber Attacks and the Kill Chain</strong></h2>

<br>
<br>
<h2><strong>MITRE ATT&CK</strong></h2>

<br>
<br>
<h2><strong>Detecting the Atomic</strong></h2>

<br>
<br>
<h2><strong>Alerting on the Atomic</strong></h2>

<br>
<br>
<h2><strong>Challenge</strong></h2>
<p>As Glitch continues to prepare for SOC-mas and fortifies Wareville's security, he decides to conduct an attack simulation that would mimic a ransomware attack across the environment. He is unsure of the correct detection metrics to implement for this test and asks you for help. Your task is to identify the correct atomic test to run that will take advantage of <code>a command and scripting interpreter</code>, conduct the test, and extract valuable artefacts that would be used to craft a detection rule.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 1.1. <em>What was the flag found in the .txt file that is found in the same directory as the PhishingAttachment.xslm artefact?</em><br><a id='1.1'></a>
>> <code><strong>________</strong></code>

<br>

> 1.2. <em>What ATT&CK technique ID would be our point of interest?</em><br><a id='1.2'></a>
>> <code><strong>________</strong></code>

<br>

> 1.3. <em>What ATT&CK subtechnique ID focuses on the Windows Command Shell?</em><br><a id='1.3'></a>
>> <code><strong>________</strong></code>

<br>

> 1.4. <em>What is the name of the Atomic Test to be simulated?</em><br><a id='1.4'></a>
>> <code><strong>________</strong></code>

<br>

> 1.5. <em>What is the name of the file used in the test?</em><br><a id='1.5'></a>
>> <code><strong>________</strong></code>

<br>

> 1.6. <em>What is the flag found from this Atomic Test?</em><br><a id='1.6'></a>
>> <code><strong>________</strong></code>

<br>

> 1.7. <em>Learn more about the Atomic Red Team via the linked room.?</em><br><a id='1.7'></a>
>> <code><strong>No answer needed</strong></code>

<br>


<br>
<br>

<h2>Task Completed<a id='2'></a></h2>
<p>Keep learning, keep growing!<br>

<h3 align="center"> <img width="900px" src=""> </h3>

<h2>My Journey<a id='3'></a></h2>
<p></p>Following I share the status of my journey in TryHackMe.</p>

<div align="center">

| Date              | Streak   | All Time     | All Time     | Monthly     | Monthly    | Points   | Rooms     |
| :---------------: | :------- | :----------- | :----------- | :---------- | :--------- | :------  | :-------- |
|                   |          | WorldWide    | Brazil       | WorldWide   | Brazil     |          | Completed |
| November 4, 2024  | 211      |     1, th |        22 nd |     th |      44 th |    |       450 |

</div>

<h3 align="center"> <img width="900px" src=""> </h3>
