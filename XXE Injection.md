<p align="center">November 20, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{197}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{XXE Injection}}$$
</h1>
<p align="center">Exploiting XML External Entities.</p>
<p align="center">Access this TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/xxeinjection">XXE Injection</a>.</p><br>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/a5324ef3-8fd6-4015-88c8-f415c54edebc">
  <img height="150px" src="https://github.com/user-attachments/assets/48edd5a2-bfc3-43a6-aae5-cdfee04b9a9b">
</p>
<br>
<p align="center">Summary</p>

<br>

<pre><code>root@[THMAttackBox]:~# gobuster dir -u http://[Target]/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://[Target]/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/uploads              (Status: 301) [Size: 314] [--> http://[Target]/uploads/]
/javascript           (Status: 301) [Size: 317] [--> http://[Target]/javascript/]
/phpmyadmin           (Status: 301) [Size: 317] [--> http://[Target]/phpmyadmin/]
/server-status        (Status: 403) [Size: 9]
Progress: 220557 / 220558 (100.00%)
===============================================================
Finished
===============================================================
</code></pre>

<h2>Task 4.  Exploiting XXE - In-Band<a id='1'></a></h2>

<br>
<h3>In-Band vs Out-of-Band XXE</h3>

<p>In-band XXE refers to an XXE vulnerability where the attacker can see the response from the server. This allows for straightforward data exfiltration and exploitation. The attacker can simply send a malicious XML payload to the application, and the server will respond with the extracted data or the result of the attack.

Out-of-band XXE, on the other hand, refers to an XXE vulnerability where the attacker cannot see the response from the server. This requires using alternative channels, such as DNS or HTTP requests, to exfiltrate data. To extract the data, the attacker must craft a malicious XML payload that will trigger an out-of-band request, such as a DNS query or an HTTP request.</p>

<br>
<h3>In-Band XXE Exploitation</h3>
<p>We will be using Burp for this room. To demonstrate this vulnerability, go to http://10.10.18.162/contact.php, and fill out the form.</p>

![image](https://github.com/user-attachments/assets/0c8415df-d059-4346-956a-d07afbb133e9)

<p>Click the submit button and intercept the request.</p>

![image](https://github.com/user-attachments/assets/99f73232-bac6-4b34-a0b4-a037c3536a5d)

<p>The submitted data is processed by contact_submit.php, which contains a vulnerable PHP code designed to return the value of the name parameter when a user submits a message in the form. Below is the vulnerable code:</p>

<pre><code>libxml_disable_entity_loader(false);

if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    $xmlData = file_get_contents('php://input');

    $doc = new DOMDocument();
    $doc->loadXML($xmlData, LIBXML_NOENT | LIBXML_DTDLOAD); 

    $expandedContent = $doc->getElementsByTagName('name')[0]->textContent;

    echo "Thank you, " .$expandedContent . "! Your message has been received.";
}
</code></pre>

<p>Since the application returns the value of the name parameter, we can inject an entity that is pointing to /etc/passwd to disclose its values.</p>

![image](https://github.com/user-attachments/assets/0f156bea-9ebe-4a25-8926-eb6075397055)

<p>Using the payload above, replace the initial XML data submitted to contact_submit.php and resend the request.</p>

![image](https://github.com/user-attachments/assets/58e81427-a150-4b62-aff9-4fcc34890026)

<br>
<h3>XML Entity Expansion</h3>
<p>XML Entity Expansion is a technique often used in XXE attacks that involves defining entities within an XML document, which the XML parser then expands. Attackers can abuse this feature by creating recursive or excessively large entities, leading to a Denial of Service (DoS) attack or defining external entities referencing sensitive files or services. This method is central to both in-band and out-of-band XXE, as it allows attackers to inject malicious entities into the XML data. For example:</p>

![image](https://github.com/user-attachments/assets/34f34513-739c-4ffb-9727-0b37e765ff84) 

<p>In the payload above, &xxe; is expanded wherever it appears. Attackers can use entity expansion to perform a Billion Laughs attack, where a small XML document recursively expands to consume server resources, leading to a denial of service.</p>

![image](https://github.com/user-attachments/assets/5407e2fd-7b56-4115-b520-63f0c2d60d65)

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the questions below}}$$ </h3>

<br>

> 4.1. <em>What XXE vulnerability occurs when the server's response is immediately disclosed to the attacker without the use of external channels?</em><br><a id='4.1'></a>
>> <strong>In-Band XXE</strong><br>
<p><br></p>


> 4.2. <em>What is the content of the file 14232d6db2b5fd937aa92e8b3c48d958.txt in the /opt directory?</em><br><a id='4.2'></a>
>> <strong>THM{1N_b4Nd_1$_34sYY}</strong><br>
<p><br></p>

![image](https://github.com/user-attachments/assets/53e2b635-6567-43c9-b046-819959d5d8b2)

![image](https://github.com/user-attachments/assets/360c7fa8-3b8e-4a67-bebf-635d22ebe578)

![image](https://github.com/user-attachments/assets/81205eb8-00d0-400c-a34a-187a4906dd1c)

![image](https://github.com/user-attachments/assets/25cb6287-639e-4953-a359-e39e3a81707b)

![image](https://github.com/user-attachments/assets/a43b9e26-ee85-4fe6-8ecc-122ba82ed00e)

<br>
<h2>Task 5.  Exploiting XXE - Out-of-Band<a id='5'></a></h2>

<br>
<h3>Out-Of-Band XXE</h3>
<p>On the other hand, to demonstrate this vulnerability, go to http://10.10.18.162/index.php. The application uses the below code when a user uploads a file:</p>

<pre><code>libxml_disable_entity_loader(false);
$xmlData = file_get_contents('php://input'); 

$doc = new DOMDocument();
$doc->loadXML($xmlData, LIBXML_NOENT | LIBXML_DTDLOAD);

$links = $doc->getElementsByTagName('file');

foreach ($links as $link) {
    $fileLink = $link->nodeValue;
    $stmt = $conn->prepare("INSERT INTO uploads (link, uploaded_date) VALUES (?, NOW())");
    $stmt->bind_param("s", $fileLink);
    $stmt->execute();
    
    if ($stmt->affected_rows > 0) {
        echo "Link saved successfully.";
    } else {
        echo "Error saving link.";
    }
    
    $stmt->close();
}
</code></pre>

<p>The code above doesn't return the values of the submitted XML data. Hence, the term Out-of-Band since the exfiltrated data has to be captured using an attacker-controlled server.<br>

For this attack, we will need a server that will receive data from other servers. You can use Python's http.server module, although there are options out there, like Apache or Nginx. Using AttackBox or your own machine, start a Python web server by using the command:</p>

![image](https://github.com/user-attachments/assets/b7d9e9ed-a71f-4c7c-a1b6-7ade0120d921)

<p>Upload a file in the application and monitor the request that is sent to submit.php using your Burp. Forward the request below to Burp Repeater.</p>

![image](https://github.com/user-attachments/assets/aa7916ce-2c43-4214-9e4f-304c21ae7da6)

<p>Using the payload below, replace the value of the XML file in the request and resend it. Note that you have to replace the ATTACKER_IP variable with your own IP.</p>

![image](https://github.com/user-attachments/assets/b221aa20-6bd1-4206-ab50-9bc732ebff0b)

<p>Send the modified HTTP request.</p>

![image](https://github.com/user-attachments/assets/b1ed89d1-ac40-4662-bfbd-60239bdab0ee)

<p>After sending the modified HTTP request, the Python web server will receive a connection from the target machine. The establishment of a connection with the server indicates that sensitive information can be extracted from the application.</p>

![image](https://github.com/user-attachments/assets/fdb2fb1e-240e-44ad-b503-7c137ffd7752)

<p>We can now create a DTD file that contains an external entity with a PHP filter to exfiltrate data from the target web application.<br>

Save the sample DTD file below and name it as sample.dtd. The payload below will exfiltrate the contents of /etc/passwd and send the response back to the attacker-controlled server:</p>

![image](https://github.com/user-attachments/assets/45fd7041-848e-47a5-b9ef-aff2a54c5070)

<h3>DTD Payload Explained</h3>
<p>The DTD begins with a declaration of an entity %cmd that points to a system resource. The %cmd entity refers to a resource within the PHP filter protocol php://filter/convert.base64-encode/resource=/etc/passwd. It retrieves the content of /etc/passwd, a standard file in Unix-based systems containing user account information. The convert.base64-encode filter encodes the content in Base64 format to avoid formatting problems. The %oobxxe entity contains another XML entity declaration, exfil, which has a system identifier pointing to the attacker-controlled server. It includes a parameter named data with %cmd, representing the Base64-encoded content of /etc/passwd. When %oobxxe; is parsed, it creates the exfil entity that connects to an attacker's server (http://ATTACKER_IP:1337/). The parameter ?data=%cmd sends the Base64-encoded content from %cmd.<br>

Go back to the repeater and change your payload to:</p>

![image](https://github.com/user-attachments/assets/be015bdf-3939-47f4-b1dc-cb935d7f92f1)

![image](https://github.com/user-attachments/assets/db35d666-7ebc-446a-ab4d-98c495262e6e)

<p>Resend the request and check your terminal. You will receive two (2) requests. The first is the request for the sample.dtd file, and the second is the request sent by the vulnerable application containing the encoded /etc/passwd.</p>

![image](https://github.com/user-attachments/assets/5c52a2e8-f6e4-424c-9703-7b52f67ba37d)


<p>Decoding the exfiltrated base64 data will show that it contains the base64 value of /etc/passwd.</p>

![image](https://github.com/user-attachments/assets/d91ff244-6083-42f4-af2f-7c3cc461a27e)


<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 5.1. <em>What kind of XXE vulnerability occurs when the response of the server is not visible to the attacker?</em><br><a id='5.1'></a>
>> <strong>Out-Band XXE</strong><br>
<p><br></p>

<br>
<h2>Task 6.  SSRF + XXE<a id='6'></a></h2>

<p>Server-Side Request Forgery (SSRF) attacks occur when an attacker abuses functionality on a server, causing the server to make requests to an unintended location. In the context of XXE, an attacker can manipulate XML input to make the server issue requests to internal services or access internal files. This technique can be used to scan internal networks, access restricted endpoints, or interact with services that are only accessible from the server’s local network.</p>

<h3>Internal Network Scanning</h3>
<p>Consider a scenario where a vulnerable server hosts another web application internally on a non-standard port. An attacker can exploit an XXE vulnerability that makes the server send a request to its own internal network resource.<br>

For example, using the captured request from the in-band XXE task, send the captured request to Burp Intruder and use the payload below:</p>

![image](https://github.com/user-attachments/assets/23ab7275-22d1-40e5-9d95-ec509e8bfb6b)


<p>The external entity is set to fetch data from http://localhost:§10§/. Intruder will then reiterate the request and search for an internal service running on the server.</p>

<h4>Steps to brute force for open ports:</h4>
<p>1. Once the captured request from the In-Band XXE is in Intruder, click the Add § button while highlighting the port.</p>

![image](https://github.com/user-attachments/assets/f3c2a4f0-5d6d-4890-a3fc-83561f128f4b)


<p>2. In the Payloads tab, set the payload type to Numbers with the Payload settings from 1 to 65535.</p>

![image](https://github.com/user-attachments/assets/1ab76d0c-5d79-419b-9423-d00c0b885b7d)




<p>3. Once done, click the Start attack button and click the Length column to sort which item has the largest size. The difference in the server's response size is worth further investigation since it might contain information that is different compared to the other intruder requests.</p>

![image](https://github.com/user-attachments/assets/f19cd60d-6755-44bc-85de-a8300001673d)

![image](https://github.com/user-attachments/assets/9ab7ed5e-78e0-4596-a8c7-e2c2f7897566)

<br>
<h4>How the Server Processes This:</h4>
<p>The entity &xxe; is referenced within the <name> tag, triggering the server to make an HTTP request to the specified URL when the XML is parsed. The response of the requested resource will then be included in the server response. If an application contains secret keys, API keys, or hardcoded passwords, this information can then be used in another form of attack, such as password reuse.</p>

<br>
<h3>Potential Security Implications</h3>
- Reconnaissance: Attackers can discover services running on internal network ports and gain insights into the server's internal architecture.<br>
- Data Leakage: If the internal service returns sensitive information, it could be exposed externally through errors or XML data output.<br>
- Elevation of Privilege: Accessing internal services could lead to further exploits, potentially escalating an attacker's capabilities within the network.<br>


<p></p>

