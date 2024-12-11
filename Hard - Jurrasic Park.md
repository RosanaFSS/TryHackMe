<h1>Jurrasic Park</h1>
<h3>219-day-streak</h3>

<br>

![image](https://github.com/user-attachments/assets/b717ffa4-cb1c-4daa-8ad7-b1223facc961)

<br>

![image](https://github.com/user-attachments/assets/59e91b57-b389-42a5-be27-c74ce6b0cdf4)

<br>

<h2>Task 1. Jurassic Park CTF</h2>

![image](https://github.com/user-attachments/assets/1a9cd97d-0cc1-4b51-95a1-9504c9a86493)

<br>

<p>This medium-hard task will require you to enumerate the web application, get credentials to the server and find four flags hidden around the file system. Oh, Dennis Nedry has helped us to secure the app too.<br>

You'll also want to turn up your device's volume (firefox is recommended). So, deploy the VM and get hacking.<br>

Please connect to our network before deploying the machine.</p>

<br>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 1.1. <em>What is the name of the SQL database serving the shop information?</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 1.2. <em>How many columns does the table have?</em><br><a id='1.2'></a>
>> <code><strong>____</strong></code>


<br>

![image](https://github.com/user-attachments/assets/cb6a330a-2a15-4fea-843b-d97535e0037e)

<br>

![image](https://github.com/user-attachments/assets/a8d4c1a8-7956-4507-8048-12cf4b9b47a9)


<br>

![image](https://github.com/user-attachments/assets/81ccef22-78fa-42f1-b504-e3e99f79a0aa)

<br>

![image](https://github.com/user-attachments/assets/1764a424-d928-4aad-9384-6dd91769012e)


<br>

<p>We have here an</p>

![image](https://github.com/user-attachments/assets/e334d7ce-26a2-4eca-9141-f1ea031600e7)

<br>

![image](https://github.com/user-attachments/assets/246732de-e61c-4e51-aabd-65f365846c04)

<br>

![image](https://github.com/user-attachments/assets/b8a10fb8-91be-4198-8a89-b0d294cec868)

<br>

<p>Dennis is mentinoned in <code>?id=5</code>.  Maybe it is a username?!</p>

![image](https://github.com/user-attachments/assets/8c346ec3-ce19-484a-9635-ee398e48dc4f)

<br>

<p>Let´s try <code>’ or 1=1</code>.</p>

<br>

![image](https://github.com/user-attachments/assets/0817fa73-100f-477a-a75b-39894433fb0f)

<br>

<p>Scrolling down ... </p>

<br>


![image](https://github.com/user-attachments/assets/a5cd1bf1-d168-46ca-afdb-6a515b64988f)

<br>

<p>So it is about <code>SQL Injection</code>!</p>

<br>

![image](https://github.com/user-attachments/assets/4a029447-c6b2-46ae-8fa6-8e31bb09ca2c)

<br>

<p><code>' or 1=1 order by 1,2</code> did not work.<br>
<code>' or 1=1 order by 1,2,3</code> did not work.<br>
<code>' or 1=1 order by 1,2,3,4</code> did not work.<br>
<code>' or 1=1 order by 1,2,3,4,5</code> did not work.<br><br>
But guess what?  .... with <code>' or 1=1 ORDER BY 1,2,3,4,5,6</code> the output wass ...</p>

<br>


![image](https://github.com/user-attachments/assets/62412608-4a88-4c2e-8efd-37ef9247a743)
























