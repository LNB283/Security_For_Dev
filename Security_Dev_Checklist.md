# Secutiry Dev Checklist
We cover a set of essential points to improve the security on Server side , Client side , Repository , 3rd party 
## Server Side

## Client Side
|Item | Description| 
| -------------- | :--------- |
|Encryption|Verify that all URLs exclusively use HTTPS|
|Encryption|Verify that all URLs returned in responses use HTTPS|
|Encryption|Verify that any authentication tokens/credentials were specifically created **only** for use with our app(s) and cannot be created by or used for other applications|
|Sensitive Information|Verify there are **no** references to internal tools, test environments or test accounts in the apps given/available to the public|
|Sensitive Information|Verify there are **no** references to features which haven't been publicly announced in the apps given/available to the public|
|Sensitive Information|Verify there are **no** *secrets*, *credentials*, *passwords*, *passphrases* for third-parties or internal systems stored in the apps given/available to the public|
|Sensitive Information|Verify that logging is well-formatted (*using standard library*), limited to **only exact values required** (no logging of unknown contents, full objects which could contain sensitive information, etc) and **free of any sensitive information**, such as x-auth-tokens, passwords, credentials, dates of birth, email addresses,etc.|
|Sensitive Information|Verify that **only information necessary** for proper operation is persisted on a client, sensitive information is **cleared on logout and/or encrypted**|
|Sensitive Information|Verify that all test code, debug code, default code, documentation, unnecessary code, jokes, etc. have **all been removed from the final code**|
|Sensitive Information|Verify all experiment names, or code supporting testing of functionality, which is still present in the production code/app, are aliased as to **prevent inadvertent disclosure** of their purpose and/or any unreleased features|
|Sensitive Information|Verify that **no sensitive information** is ever contained in the URL itself to avoid leaking data in proxies and referer headers|
|Session Token Management|Verify that all sessions are **properly terminated server-side** when a user logs out or the session is otherwise terminated/expired|
|Certificate Management|Verify that we have not disabled HTTPS (aka x.509, TLS) certificate validation in any way|
|Remotely Access|Verify there is **no** remotely included Javascript (**unless explicitely approved**)|
|Vulnerability review|Verify there are **no** vulnerabilities rated **Medium** (CVSS >4) or above in any 3rd party, including open-source and/or code we use|
|Design|Verify that any use of the Window.postMessage function is implemented securely|
|Design|Verify that all users are required to confirm any state changing or redirect action before it proceeds|
--------------------------
## Repository
|Item | Description| 
| -------------- | :--------- |
|Sensitive information|Verify there are **no** *secrets*,*credentials*,*passwords*,*passphrases* stored in the project's source code repository|
|Vulnerability review|Verify there are **no** vulnerabilities rated **Medium** (CVSS >4) or above in any 3rd party, including open-source and/or code we use|
--------------------------
## 3rd Party
|Item | Description| 
| -------------- | :--------- |
|Sensitive information|Verify that no requests to 3rd parties are tighly controlled and will never include sensitive information (*not previously approved*), even when programmatic errors occur|
|Encryption|Verify that all requests to 3rd parties use **exclusively https**|
|Access control|Implement and test ability to respond to a user revoking your permission to access their data, including password resets, for 3rd party integrations|
|Uniform Resource Identifier (*URI*)|Explicitely defined any OAuth redirect_uri paths, check the URI don't perform redirects themselves, and are explicitely limited in the 3rd party console, *if possible*|
|Access Control|Verify that all code repositories are **private** with **access controls enabled**|
--------------------------
