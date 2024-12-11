

![image](https://github.com/user-attachments/assets/dc74112a-6edf-45cb-83f5-ad991dec30b1)


![image](https://github.com/user-attachments/assets/99c13be2-c47c-4398-93b5-a24ebee639dd)

<br>
<h2>Task 1. Introduction</h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

>> <code><strong>No answer needed</strong></code>

<br>

<br>
<h2>Task 2. Hash Identification</h2>
<p>Often the first thing you will need when you encounter a hash, is trying to identify which kind of hash it is.
There are a lot of hash types, some are very famous like MD5 or SHA1 but other are less and there are several hash types possible for a given character set and length.</p>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 2.1. <em>Haiti is a CLI tool to identify the hash type of a given hash. Install it.</em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 2.2. <em>Launch Haiti on this hash:</em><br><a id='2.2'></a>
> <code>741ebf5166b9ece4cca88a3868c44871e8370707cf19af3ceaa4a6fba006f224ae03f39153492853</code><br>
> What kind of hash it is?
>> <code><strong>RIPEMD-320</strong></code>

<br>

<pre><code>sudo apt-get install rubygems</code></pre>

<br>

<pre><code>gem install haiti-hash</code></pre>

<br>

<pre><code> haiti 741ebf5166b9ece4cca88a3868c44871e8370707cf19af3ceaa4a6fba006f224ae03f39153492853</code></pre>

<br>

> 2.3. <em>Launch Haiti on this hash:</em><br><a id='2.3'></a>
> <code>1aec7a56aa08b25b596057e1ccbcb6d768b770eaa0f355ccbd56aee5040e02ee</code><br>
>> <code><strong>No answer needed</strong></code>

<br>

<pre><code> haiti 1aec7a56aa08b25b596057e1ccbcb6d768b770eaa0f355ccbd56aee5040e02ee </code></pre>

<br>

> 2.4. <em>What is Keccak-256 Hashcat code?</em><br><a id='2.4'></a>
>> <code><strong>17800</strong></code>

![image](https://github.com/user-attachments/assets/e3fa018d-bcab-4602-85c2-5174708608a6)

<br>

![image](https://github.com/user-attachments/assets/04068217-eb77-492a-a274-9e705000298c)

<br>

> 2.5. <em>What is Keccak-256 John the Ripper code?</em><br><a id='2.5'></a>
>> <code><strong>raw-keccak-256</strong></code>


<p>Reference the hands-on related to the previous challenge</p>

<br>
<h2>Task 3. Wordlists</h2>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 3.1. <em>RockYou is a famous wordlist contains a large set of commonly used password sorted by frequency.<br>
To search for this wordlist with wordlistclt run:<br>
<code>wordlistctl search rockyou</code></em><br><a id='3.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 3.2. <em>Which option do you need to add to the previous command to search into local archives instead of remote ones?</code></em><br><a id='3.2'></a>
>> <code><strong>-l</strong></code>

<br>

![image](https://github.com/user-attachments/assets/a69defe0-18d1-4748-86d2-a55ce07ce3f1)

<br>

![image](https://github.com/user-attachments/assets/8e03d26c-01b6-4895-a34f-be36c05ed8d4)

<br>

<pre><code>wordlistctl search -l rockyou</code></pre>

<br>


<p>I am used to search wordlists as following ...</p>

<pre><code># locate rockyou.txt
/usr/share/wordlists/rockyou.txt
</code></pre>

<br>

> 3.3. <em>Download and install rockyou wordlist by running this command: <code>wordlistctl fetch -l rockyou</code></em><br><a id='3.3'></a>
>> <code><strong>No answer needed</strong></code>

<br>


> 3.4. <em>Now search again for rockyou on your local archive with <code>wordlistctl search -l rockyou</code></em><br>
You should see that the wordlist is deployed at <code></usr/share/wordlists/passwords/rockyou.txt.tar.gz/code><br>
But the wordlist is compressed in a tar.gz archive, to decompress it run <code>wordlistctl fetch -l rockyou -d</code>.<br>
If you run  <code>wordlistctl search -l rockyou</code>  one more time, what is the path where is stored the wordlist?<a id='3.4'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<pre><code>git clone https://github.com/BlackArch/wordlistctl.git</code></pre>

<br>

<pre><code># ls
bash-completion  Dockerfile  LICENSE  man  README.md  repo.json  requirements.txt  wordlistctl.py
...
...
cat wordlistctl.py | grep local
...
...
python3 wordlistctl.py search -l rockyou
</code></pre>

<br>

![image](https://github.com/user-attachments/assets/7b8425b4-7466-4c19-b5f0-6ac615f807d2)

<br>

![image](https://github.com/user-attachments/assets/77584e8a-4b49-4afa-b4ff-f4a148d87c5a)

<br>


<br>

> 3.5. <em>You can search for a wordlist about a specific subject (eg. facebook) <code>wordlistctl search facebook</code> or list all wordlists from a category (eg. fuzzing) <code>wordlistctl list -g fuzzing</code>.<br>
What is the name of the first wordlist in the usernames category?</em><br><a id='3.3'></a>
>> <code><strong>No answer needed</strong></code>



![image](https://github.com/user-attachments/assets/72673c1a-a0f2-4166-a6a7-23e902de238d)










<br>
<h2>Task 4. Cracking tools, models & rules</h2>

<br>
<h2>Task 5. Custom wordlist generation</h2>

<br>
<h2>Task 6. It´s time to crack hashes</h2>

<br>
<h2>Task 7. Avout the author</h2>

<br>
<h2>Room Completed</h2>

<br>
<h2>My Journey</h2>


