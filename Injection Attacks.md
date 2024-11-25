<h1>Application-Based Attacks</h1>


<table class="center">



| *OWASP Category*   | Acronym        | Stands for                             |  Weakness                                 | Prevention                                 |
| :--------------- | :------------- | :------------------------------------- | :---------------------------------------- | :----------------------------------------  |
| API7:2023        | SSRF           | Server Side Request Forgery            |  occur when an API is fetching a remote resource without validating the user-supplied URL. It enables an attacker to coerce the application to send a crafted request to an unexpected destination, even when protected by a firewall or a VPN. | - Isolate the resource fetching mechanism in your network: usually these features are aimed to retrieve remote resources and not internal ones.<br>- Whenever possible, use allow lists<br>- Disable HTTP redirections.<br>- Use a well-tested and maintained URL parser to avoid issues caused by URL parsing inconsistencies.<br>- Validate and sanitize all client-supplied input data.<br>- Do not send raw responses to clients.|
| Injection        | SQL            | Structured Query Language              |
| Injection        | NoSQL          | No Structured Query Language           |
| Injection        | Command        | -                                      |
| Injection        | XSS            | Cross-Site Scripting                   |
| Injection        | LDAP           | Lightweight Directory Access Protocol  |
| Injection        | SSTI           | Server-Server Template                 |
| Injection        | ORM            |                                        |

</table>

<br>

:::{list-table} Frozen Delights!
:widths: 15 10 30
:header-rows: 1

*   - Treat
    - Quantity
    - Description
*   - Albatross
    - 2.99
    - On a stick!
*   - Crunchy Frog
    - 1.49
    - If we took the bones out, it wouldn't be
 crunchy, now would it?
*   - Gannet Ripple
    - 1.99
    - On a stick!
:::


