<h3> Welcome to the <em>TryHackMe ...</em></h3>
<h1>Learn</h1>
<h2>Agent Sudo</h2>
<p>You found a secret server located under the deep sea. Your task is to hack inside the server and reveal the truth.</p>
<p>October 21, 2024<br></p>

<div style="display: flex; justify-content: center; align-items: center;">
    <img src="https://github.com/user-attachments/assets/e78f69eb-2323-47d4-9684-7b478c5d8041" width="150px" height="150px"/>
</div>
<br>

![image](https://github.com/user-attachments/assets/85de77d1-55cb-403c-aa9d-e86ca373f287)


<p>Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure. TryHackMe classified this CTF as Easy. It´s key part of my 167-day-streak. Let´s get started!!<br><br>
Access this TryHackMe Room clicking <a href="https://tryhackme.com/r/room/agentsudoctf)">Agent Sudo</a></p>

<h2>Task 1 - Author note</h2>

<p>Welcome to another THM exclusive CTF room. Your task is simple, capture the flags just like the other CTF room. Have Fun!<br><br>

If you are stuck inside the black hole, post on the forum or ask in the TryHackMe discord.<br>

> 1.1 - <em>Deploy the machine.</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>

<h2>Task 2 - Enumerate</h2>

<p>Enumerate the machine and get all the important information.</p>
<p><br></p>

![image](https://github.com/user-attachments/assets/d546fa08-249c-4ed0-a4f9-334345317574)

![image](https://github.com/user-attachments/assets/ee588800-45e4-4284-9fbe-750bfc2f242e)

![image](https://github.com/user-attachments/assets/b4293f1d-28db-4ca8-b39c-513437299700)

![image](https://github.com/user-attachments/assets/95ed8ed9-f97a-4e47-9fa7-cc16b5a258d4)

![image](https://github.com/user-attachments/assets/9d512800-b9a7-4bd2-be45-311c6538a19b)

![image](https://github.com/user-attachments/assets/62c1ac57-7b62-4a7d-8c82-7fcfedb2248c)

![image](https://github.com/user-attachments/assets/9b37b066-0628-40cc-be7c-0ecba764696e)

![image](https://github.com/user-attachments/assets/15f6cdf6-8569-43fa-808e-8451892b3624)

![image](https://github.com/user-attachments/assets/24157b66-2e18-4f31-8a99-b02c72423b87)


-----

![image](https://github.com/user-attachments/assets/44ea2993-a978-4630-96ff-ddf2dd417319)

![image](https://github.com/user-attachments/assets/a71644c1-a923-4e81-9de5-9ae63c717b38)

![image](https://github.com/user-attachments/assets/8b5e3c9a-3eec-4e10-872a-3334c15effb3)

![image](https://github.com/user-attachments/assets/1b7e090c-2b71-4886-95f3-d36eb6c1f72b)





chris<br>
crystal

![image](https://github.com/user-attachments/assets/590adc6f-f46c-4f18-ae43-c33c1df46ae4)

<p> FTP and downloaded 3 files </P>

![image](https://github.com/user-attachments/assets/213047eb-243a-4861-ba40-9c55027b2cef)

![image](https://github.com/user-attachments/assets/ecedcbd4-53a0-4f64-9d09-f8574637ca9c)


<p> To_agentJ.txt  content.</p>

![image](https://github.com/user-attachments/assets/63ade370-a69f-4891-99cb-efb5f95bb75b)

<p> exiftool cutie.png</p>

![image](https://github.com/user-attachments/assets/122d1496-9fcf-444a-bfe2-3da61f605a06)

<p>using <code>binwalk</code> I did not find anything juicy in <code>cute-alien.jpg</code>.</p>

![image](https://github.com/user-attachments/assets/29d8701a-f5a4-43a2-bf70-48fcf5397d6c)

<p>When using <code>binwalk</code> to <code>cutie.png</code>, I found something interesting: reference to <code>To_agentR.txt</code> </p>

<p> So here I found a hidden zip file hidden in the image, which hides a txt file called To_agentR.txt.</p>

<p>Let´s extract the file by running the same command, together with the -e flag.</p>

<code>binwalk -e cutie.png</code>

![image](https://github.com/user-attachments/assets/3d62e27d-620a-490d-89a5-f55acd2ac63e)

![image](https://github.com/user-attachments/assets/81f70c5f-76b9-4926-ac21-10f06b72b240)

![image](https://github.com/user-attachments/assets/80b844a8-a05a-472d-b9d7-72a1c597c727)

![image](https://github.com/user-attachments/assets/174b7857-ff82-41a7-9e2b-519980cf0a31)

![image](https://github.com/user-attachments/assets/e2dce9c8-aef8-40cd-8b59-3f55216019f4)

![image](https://github.com/user-attachments/assets/be553b6a-8c59-4b00-8df2-1551ac9b30a3)

<p>I used Decoder feature of Burp Suite, and found somthing interesting.</p>

![image](https://github.com/user-attachments/assets/6fd90439-07c4-459c-ac33-ed6a9aaec5be)


![image](https://github.com/user-attachments/assets/12af0b68-e68d-4775-b87b-9a609e3d991f)

![image](https://github.com/user-attachments/assets/e65a71a6-5837-492c-868d-4f9dffd0f819)

![image](https://github.com/user-attachments/assets/cee7616a-dc5b-4a00-bbda-253f6945684e)







![image](https://github.com/user-attachments/assets/4c35e570-94bd-4c2f-8334-7beaf09b7468)











![image](https://github.com/user-attachments/assets/0d3f990c-19ec-4085-85bb-354894d66b1a)

<p>As it wa mentioned about <code>Trailer data after PNG IEND chunk</code>, i decided to dump the file to hex format by using <code>xxd</code>.</p>


<code>xxd cutie.png</code>

![image](https://github.com/user-attachments/assets/6b7674fe-5c8d-49be-8516-5967954cec70)



<h2>Task 4 - Capture the user flag</h2>

<p>You know the drill.<br><br>




















> 2.1 - <em>How many ports are open?.</em><br>
>> <strong>3</strong><br>
<p><br></p>

> 2.2 - <em>How you redirect yourself to a secret page?</em><br>
>> <strong>user-agent</strong><br>
<p><br></p>

> 2.3 - <em>What is the agent name?</em><br>
>> <strong>chris</strong><br>
<p><br></p>


<h2>Task 3 - TCP Flags</h2>

> 3.1 - <em>What is the user flag?</em><br>
>> <strong>No answer needed</strong><br>
<p></p>

> 3.2 - <em>What is the incident of the photo called?</em><br>
>> <strong>No answer needed</strong><br>
<p><br></p>


james

hackerrules!

![image](https://github.com/user-attachments/assets/56a797ad-3358-45f8-b39a-840d6b072e46)

![image](https://github.com/user-attachments/assets/8f563418-92b8-4a1f-b3ce-83565b2091f2)

b03d975e8c92a7c04146cfa7a5a313c7

<p><code>sudo scp james@<target ip>:Alien_autospy.jpg ~/</code></p>

![image](https://github.com/user-attachments/assets/ab2ed312-51c7-48ce-9c66-420a79c98f1b)




![image](https://github.com/user-attachments/assets/7518fac4-6481-4d10-b8a7-4db7434e8f53)




![image](https://github.com/user-attachments/assets/f39f629d-c1ca-4831-b72b-d9ed1a4d5580)

![image](https://github.com/user-attachments/assets/e717e0a5-c8cf-49f7-a5cd-c74977b2dd77)

![image](https://github.com/user-attachments/assets/de4dc09e-c181-437a-ae55-94ad4d1b5885)

![image](https://github.com/user-attachments/assets/9d38d7d9-66da-4070-a019-e3664f0582b2)

![image](https://github.com/user-attachments/assets/c3fdf1f3-3145-4329-aa82-879732ae342a)

![image](https://github.com/user-attachments/assets/873ea0ea-ea34-4b3f-b389-f0aed795e9c3)

![image](https://github.com/user-attachments/assets/794ffd1f-1027-4662-b549-133c941a405c)

![image](https://github.com/user-attachments/assets/de0d68e6-0f24-45e6-8d0b-60ba09b640ad)













![image](https://github.com/user-attachments/assets/97a30231-95c8-4a62-9cb6-d96f3a9339fe)





