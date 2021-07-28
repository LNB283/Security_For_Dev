# Secutiry Dev Checklist
We cover a set of essential points to improve the security on Server side , Client side , Repository , 3rd party 
## Server Side
## Client Side
## Repository
|Item | Description| 
| -------------- | :--------- |
|Sensitive information|Verify there are **no** *secrets*,*credentials*,*passwords*,*passphrases* stored in the project's source code repository|
|Vulnerability review|Verify there are **no** vulnerabilities rated **Medium** (CVSS >4) or above in any 3rd party, including open-source and/or code we use|
## 3rd Party
|Item | Description| 
| -------------- | :--------- |
|Sensitive information|Verify that no requests to 3rd parties are tighly controlled and will never include sensitive information (*not previously approved*), even when programmatic errors occur|
|Encryption|Verify that all requests to 3rd parties use **exclusively https**|
|Access control|Implement and test ability to respond to a user revoking your permission to access their data, including password resets, for 3rd party integrations|
|Uniform Resource Identifier (*URI*)|Explicitely defined any OAuth redirect_uri paths, check the URI don't perform redirects themselves, and are explicitely limited in the 3rd party console, *if possible*|
|Access Control|Verify that all code repositories are **private** with **access controls enabled**|
