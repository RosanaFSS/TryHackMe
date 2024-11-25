<h1>Application-Based Attacks</h1>

<br>

| OWASP Category   | Acronym        | Stands for                             |  Weakness                                 | Prevention                                 |
| :--------------- | :------------- | :------------------------------------- | :---------------------------------------- | :----------------------------------------  |
| API7:2023        | SSRF           | Server Side Request Forgery            |  occur when an API is fetching a remote resource without validating the user-supplied URL. It enables an attacker to coerce the application to send a crafted request to an unexpected destination, even when protected by a firewall or a VPN. | - Isolate the resource fetching mechanism in your network: usually these features are aimed to retrieve remote resources and not internal ones. - Whenever possible, use allow lists <br>
- Disable HTTP redirections. <br>
- Use a well-tested and maintained URL parser to avoid issues caused by URL parsing inconsistencies.<br>
- Validate and sanitize all client-supplied input data.<br>
- Do not send raw responses to clients.|
| Injection        | SQL            | Structured Query Language              |
| Injection        | NoSQL          | No Structured Query Language           |
| Injection        | Command        | -                                      |
| Injection        | XSS            | Cross-Site Scripting                   |
| Injection        | LDAP           | Lightweight Directory Access Protocol  |
| Injection        | SSTI           | Server-Server Template                 |
| Injection        | ORM            |                                        |

