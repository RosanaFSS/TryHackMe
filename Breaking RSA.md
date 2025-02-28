

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 1.1. <em>How many services are running on the box?</em><br><a id='1.1'></a>
>> <strong><code>2</code></strong><br>
<p><br></p>

nmap<br>

![image](https://github.com/user-attachments/assets/5cd475ae-11f8-419b-b46c-04722928757f)

<br>

> 1.2. <em>What is the name of the hidden directory on the web server? (without leading '/')</em><br><a id='1.2'></a>
>> <strong><code>development</code></strong><br>
<p><br></p>

gobuster<br>

![image](https://github.com/user-attachments/assets/fec7eb17-88bd-4157-908d-4e5e0c8c246d)

<br>

> 1.3. <em>What is the length of the discovered RSA key? (in bits)</em><br><a id='1.3'></a>
>> <strong><code>4096</code></strong><br>
<p><br></p>

http://breaking<br>

![image](https://github.com/user-attachments/assets/6185f1bf-7dab-4c1c-8591-f75c3cd46461)

<br>

http://breaking/development<br>

![image](https://github.com/user-attachments/assets/791aeed1-2f8c-4c56-a877-76d58ce27154)

<br>
http://breaking/development/log.txt<br>

![image](https://github.com/user-attachments/assets/213f6c52-923c-45cf-9fbc-8faa4bb48023)

<br>

<br>
http://breaking/development/id_rsa.pub<br>


![image](https://github.com/user-attachments/assets/f7149fd3-b707-40f5-94d6-38ed6de615aa)

<br>

<br>
ssh-keygen

![image](https://github.com/user-attachments/assets/c36ee36e-021b-4c97-8384-ad9ff2c4f868)

<br

![image](https://github.com/user-attachments/assets/fd762c99-254b-4676-aa57-c798c147cc98)

<br>
pycryptodome

<br>

pip install pycryptodome<br>
pip install gmpy2



<br>













