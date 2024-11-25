<h1>Application-Based Attacks</h1>
<br>

<h1 align="center">
  $$\textcolor{#3bd62d}{\textnormal{XSS, Cross Site Scripting}}$$
</h1>
<p> XSS is a vulnerability that allows an attacker to inject malicious scripts into a web page viewed by another user. Consequently, they bypass the Same-Origin Policy (SOP); SOP is a security mechanism implemented in modern web browsers to prevent a malicious script on one web page from obtaining access to sensitive data on another page. XSS dodges SOP as it is executing from the same origin.</p>
<br>

<p>Prerequisites<br>
- HTTP in Detail<br>
- How the Web Works<br>
- Intro to Cross-site scripting<br>
- JavaScript Basics<br>
- Python Basics</p>

<table class="center">

|Category       |Acronym       |Stands for                    |Weakness                 |
|:--------------|:-------------|:-----------------------------|:------------------------|
| Injection        | Reflected XSS  | Reflected Cross Site Scripting         | Reflected attacks are those where the injected script is reflected off the web server, such as in an error message, search result, or any other response that includes some or all of the input sent to the server as part of the request. Reflected attacks are delivered to victims via another route, such as in an e-mail message, or on some other website. When a user is tricked into clicking on a malicious link, submitting a specially crafted form, or even just browsing to a malicious site, the injected code travels to the vulnerable web site, which reflects the attack back to the user’s browser. The browser then executes the code because it came from a “trusted” server. Reflected XSS is also sometimes referred to as Non-Persistent or Type-I XSS (the attack is carried out through a single request / response cycle). |
| Injection        | Stored XSS     | Stored Cross Site Scripting            | Stored attacks are those where the injected script is permanently stored on the target servers, such as in a database, in a message forum, visitor log, comment field, etc. The victim then retrieves the malicious script from the server when it requests the stored information. Stored XSS is also sometimes referred to as Persistent or Type-II XSS. |
| Injection        | DOM Based XSS  | DOM Based Cross Site Scripting         | Is a subset of Client XSS.<br>The consequence of an XSS attack is the same regardless of whether it is stored or reflected or DOM Based XSS. |
| Injection        | Blind XSS      | Blind Cross Site Scripting             | Blind Cross-site Scripting is a form of persistent XSS. It generally occurs when the attacker’s payload saved on the server and reflected back to the victim from the backend application. For example in feedback forms, an attacker can submit the malicious payload using the form, and once the backend user/admin of the application will open the attacker’s submitted form via the backend application, the attacker’s payload will get executed. Blind Cross-site Scripting is hard to confirm in the real-world scenario but one of the best tools for this is XSS Hunter. |

<br>

|Category       |Acronym       |Stands for                    |Weakness                 |
|:--------------|:-------------|:-----------------------------|:------------------------|
| API7:2023     | SSRF         | Server Side Request Forgery  | Occur when an API is fetching a remote resource without validating the user-supplied URL. It enables an attacker to coerce the application to send a crafted request to an unexpected destination, even when protected by a firewall or a VPN.|

|Category       |Acronym       |Stands for                    |Weakness                 |
|:--------------|:-------------|:-----------------------------|:------------------------|
| Injection        | SQL            | Structured Query Language              |
| Injection        | NoSQL          | No Structured Query Language           |
| Injection        | Command        | -                                      |
| Injection        | DOM Based XSS  | DOM Based Cross Site Scripting         | Is a subset of Client XSS.<br>The consequence of an XSS attack is the same regardless of whether it is stored or reflected or DOM Based XSS. || 
| Injection        | LDAP           | Lightweight Directory Access Protocol  |
| Injection        | SSTI           | Server-Server Template                 |
| Injection        | ORM            |                                        |

</table>

<br>



