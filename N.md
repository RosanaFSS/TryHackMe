

<h2>Tor<a id='1'></a></h2>
<p>- <code>Tor</code>  is a free and open-source software for enabling anonymous communication.<br>
- <code>Tor</code> directs Internet traffic through a free, worldwide, volunteer overlay network consisting of more than seven thousand relays to conceal a user's location and usage from anyone conducting network surveillance or traffic analysis. <br>
- Using <code>Tor</code>code> makes it more difficult to trace Internet activity to the user: this includes "visits to Web sites, online posts, instant messages, and other communication forms".<br>
- <code>Tor</code>code>'s intended use is to protect the personal privacy of its users, as well as their freedom and ability to conduct confidential communication by keeping their Internet activities unmonitored.<br><br>
- In penetration testing, there might be a need to conduct a full-fledged black-box test. This is a form of testing in which security professionals have to deal with such things as firewalls and other mechanisms of restriction on the customer’s side. In this case, the Tor network can be used in order to constantly change IP and DNS addresses and therefore successfully overcome any restrictions.
</p>

<br>

<p>Install <code>Tor</code> <pre><code>apt-get install tor</code></pre></p>

<br>

<p>Start <code>Tor</code></p>
<pre><code>service tor start</code></pre>

<br>

<p>Check <code>Tor</code>´s availability</p>
<pre><code>service tor statu</code></pre>

<br>

<p>Stop <code>Tor</code> service</p>
<pre><code>service tor stop</code></pre>

<br>

<br>



<h2>Gobuster<a id='2'></a></h2>
<pre><code>gobuster dir -u http:/[Target IP] -w /usr/share/dirb/wordlists/common.txt</code></pre>


<h2>WPA<a id='3'></a></h2>
- <code>WPA</code> stands for <code>W</code>i-Fi <code>P</code>rotected <code>A</code>ccess.<br>
- <code>WPA</code> is a security standard for computing devices equipped with wireless internet connections.<br>
- The Wi-Fi Alliance intended <code>WPA</code> as an intermediate measure to take the place of <code>WEP</code>.<br>
- <code>WEP</code> = <code>W</code>ierd <code>E</code>quivalent <code>P</code>rivacy was shown to be insecure and can be broken by capturing enough packets to guess the key via statistical methods.<br>
- <code>WPA2</code> replaced<code> WPA</code>.<br>
- <code>WEP</code>, <code>WPA</code>, <code>WPA2</code>, and the latest <code>WPA3</code> are the four types of wireless network security protocols, each with increasing levels of security.<br>

<br>
<h2>WPA2</h2>
- The <code>core of WPA2</code> authentication is the <code>4 way handshake</code>.<br>
- Most home WiFi networks, and many others, use <code>WPA2 personal</code>.<br>
- If you have to <code>log in with a password</code> and it's not WEP, then it's <code>WPA2 personal</code> = <code>WPA2-EAP</code>.<br>
- <code>WPA2-EAP</code> uses RADIUS servers to authenticate, so if you have to enter a username and password in order to connect then it's probably that.<br>
- The minimum lenght of <code>WPA2-EAP</code> OR  <code>WPA2 Personal Password</code> is 8.<br>
- You can perform <code>brute force</code>attack on the encryption on <code>WPA2 personal</code>.<br>
- <code>Brute force</code> can not be used to attack <code>WPA2-EAP</code> handshakes. <br><br>

<br>
<h2>WPA2-PSK</h2>
- <code>WPA2-PSK</code> refer to Wifis network that you connect to by providing a password that's the same for everyone.
- It refers to the <em>wifi code/ password/ passphrase</em>.<br>
