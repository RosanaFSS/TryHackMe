

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

<br>

 1.4. <em>What are the last 10 digits of n? (where 'n' is the modulus for the public-private key pair)</em><br><a id='1.4'></a>
>> <strong><code>1225222383</code></strong><br>
<p><br></p>

![image](https://github.com/user-attachments/assets/fd762c99-254b-4676-aa57-c798c147cc98)

<br>
pycryptodome

<br>

pip install pycryptodome<br>
pip install gmpy2


<br>

este.py

<br>

from Crypto.PublicKey import RSA

f = open("id_rsa.pub", "r")

key = RSA.importKey(f.read())

n = key.n
e = key.e

last = str(n)[-10:]

print(f"----------- Analyzing the Public-Private Key Pair\n\n")

print(f"n =  {n}\n\n")

print(f"the last 10 digits of n =    {last}\n\n")

print(f"e =  {e}\n\n") 


<br>

![image](https://github.com/user-attachments/assets/3a419da0-e15c-4c44-ad02-d7247e4722c5)



<br>

> 1.5. <em>Factorize n into prime numbers p and q</em><br><a id='1.5'></a>
>> <strong><code>No answer needed</code></strong><br>
<p><br></p>

<br>

1.6. <em>What is the numerical difference between p and q?</em><br><a id='1.6'></a>
>> <strong><code>____</code></strong><br>
<p><br></p>

<br>

1.7. <em>Generate the private key using p and q (take e = 65537)</em><br><a id='1.7'></a>
>> <strong><code>_______</code></strong><br>
<p><br></p>

<br>

1.8. <em>Generate the private key using p and q (take e = 65537)</em><br><a id='1.7'></a>
>> <strong><code>No answer needed</code></strong><br>
<p><br></p>


<br>

1.9. <em>What is the flag?</em><br><a id='1.7'></a>
>> <strong><code>________</code></strong><br>
<p><br></p>















