# Secutiry Dev Checklist
We cover a set of essential points to improve the security on Server side , Client side , Repository , 3rd party 
## Server Side
|Item | Description| Reference|
| -------------- | :--------- |:--------- |
|Input Validation|Restricting the size of inputs helps to directly prevent issues such as buffer overflows, resource exhaustion  and/or denial of service. Further, inputs which are properly size limited can indirectly prevent other types of attacks, as they can prevent attackers from being able to fully develop their malicious input. Examples of inputs are headers, cookies, POST/GET parameters, file uploads, etc.|[Link](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)|
|Data Type Validation|The most common web application security weakness is the failure to properly validate input from the client or environment. This weakness leads to almost all of the major vulnerabilities in applications, such as Interpreter Injection, locale/Unicode attacks, file system attacks and buffer overflows. Data from the client should never be trusted for the client has every possibility to tamper with the data.|[Link](https://www.owasp.org/index.php/Data_Validation)|
|File Type Validation|**If Applicable** Magic numbers give you a more robust way to verify the filetype. Never rely on file extension, as this can be easily spoofed. The file types allowed to be uploaded should be restricted to only those that are necessary for business functionality.|[Link](https://www.owasp.org/index.php/Unrestricted_File_Upload)|
|Pattern Validation|The most common web application security weakness is the failure to properly validate input from the client or environment.This weakness leads to almost all of the major vulnerabilities in applications, such as Interpreter Injection, locale/Unicode attacks, file system attacks and buffer overflows. Data from the client should never be trusted for the client has every possibility to tamper with the data.Note: Use of parsers is typically preferred over regular expressions|N/A|
|Numbers Input|Application should limit the quantity of inputs they accept to only what is needed. Developers need to be careful when extracting parameters from requests,too many or duplicate parameters may cause unexpected application behaviors, which can result in security issues.|[Link](https://www.owasp.org/index.php/Testing_for_HTTP_Parameter_pollution_(OTG-INPVAL-004))|
|Accepted Characters|Limit the set of acceptable characters for each user-supplied input to only what is specifically expected. Failure to do so opens an application up to various types of attack, particularly when control characters are allowed.|[Link](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)|
|File metadata|**If Applicable** File metadata is generally provided by the transport, such as HTTP multi-part encoding. You must validate the metadata extremely carefully before using it.|[Link](https://wp-rocket.me/blog/image-metadata-can-impact-web-performance-security/)|
|URL Validation|Avoid use of incompletely specified endswith(domain.com), to prevent foodomain.com, and startswith(domain.com) to prevent domain.comfoo.com abuse|[Link](https://mathiasbynens.be/demo/url-regex),[Link](https://gist.github.com/gruber/8891611)|
|Encryption|**All URLs exclusively use HTTPS**|N/A|
|Encryption|HTTP Strict Transport Security (also named HSTS) is an opt-in security enhancement that is specified by a web application through the use of a special response header.Once a supported browser receives this header that browser will prevent any communications from being sent over HTTP to the specified domain and will instead send all communications over HTTPS. |[Link](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)|
|Header|The X-Frame-Options HTTP response header can be used to indicate whether or not a browser should be allowed to render a page in a <frame> or <iframe>. Sites can use this to avoid Clickjacking attacks, by ensuring that their content is not embedded into other sites.|[Link](https://cheatsheetseries.owasp.org/cheatsheets/Clickjacking_Defense_Cheat_Sheet.html)|
|Header| Content-Type header returned and properly set to match the actual content returned on all responses|[Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)|
|Header|Content-Type header tells the client what the content type of the returned content actually is. Browsers will do MIME sniffing in some cases and will not necessarily follow the value of this header; to prevent this behavior, the header X- Content-Type-Options can be set to nosniff.|[Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)|
|Header|The HTTP X-XSS-Protection response header is a feature of Internet Explorer, Chrome and Safari that stops pages from loading when they detect reflected cross-site scripting (XSS) attacks.|[Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-XSS-Protection)|
|CSP|Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks.|[Link](https://csp-evaluator.withgoogle.com),[Link](https://developers.google.com/web/fundamentals/security/csp/)|
|Access Control|The Access-Control-Allow-Origin header should only return trusted origins.Access-Control-Allow-Origin must return either a single accepted origin or dynamically generate the header based on a white-list of acceptable domains.|[Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin)|
|Sensitive Information|Referrer-Policy is properly configured to not leak data or send sensitive information over plain-text HTTP.The Referrer-Policy HTTP header governs which referrer information, sent in the Referer header, should be included with requests made.|[Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy)|
|Sensitive Information|Fuzzy birthday (correct format): the date and month should be within a few days of the current date and the date would contain seconds.Example of real birth date which must NOT be sent to the client: "birth_date": "1980-11-16T00:00:00.000Z”|N/A|
|Ping Time|The last active or "ping" time, for a user other than the currently authenticated one|N/A|
|Sensitive Information|Internal routes, IP addresses, or server headers that contain version information.**This information must not be sent to the client.**|N/A|
|Firebase ID Tokens|To do so securely, after a successful sign-in, send the user's ID token to your server using HTTPS. Then, on the server, verify the integrity and authenticity of the ID token and retrieve the uid from it. You can use the uid transmitted in this way to securely identify the currently signed-in user on your server.|[Link](https://firebase.google.com/docs/auth/admin/verify-id-tokens)|
|Sensitive Information|Any user's User Number, including their own|N/A|
|Cookies|We have verified that the the Secure flag is set on all cookies|[Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie)|
|Sensitive Information|Do not point CNAMEs under your domains to a third-party.The basic premise of a subdomain takeover is a host that points to a particular service not currently in use, which an adversary can use to serve content on the vulnerable subdomain by setting up an account on the third-party service. **Please note** that having a CNAME that points to a third-party service is NOT inherently a security vulnerability.|[Link](https://www.hackerone.com/blog/Guide-Subdomain-Takeovers)|
|3rd Party JS|We have verified that no proxying of third-party sites (or content) under the your domains occurs|[Link](https://www.owasp.org/index.php/3rd_Party_Javascript_Management_Cheat_Sheet)|
|Cookies|The domain and path settings on the cookie are correctly configured to not send the cookie to other subdomains and/or on paths that don't require it|[Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie)|
|Access Control|We have verified that only authenticated users can make any successful request to any endpoints in the project|[Link](https://www.owasp.org/index.php/Forced_browsing)|
|Sensitive Information|We have verified that any email collected is verified before being trusted for use|N/A|
|User Exp.|**If Applicable** We have verified that any user action which should only be performed by a limited number of users, cannot be performed by other users|N/A|
|Logs|We have verified Carriage Return and Line Feed characters are sanitized prior to being written to logs (Prevent CLRF injection)|[Link](https://www.owasp.org/index.php/Log_Injection)|
|Logging|Logging **must be** well-formatted (standard libraries), limited to only exact values required (no logging of unknown contents, full objects which could contain sensitive information, etc) and free of any sensitive information.||
|URL Format|To prevent Homograph attack, we have verified that all URLs that contain mixed language characters are expanded to their punycode versions before being returned to clients|N/A|
|Sensitive Information|We have verified that all test code, debug code, default code documentation, unnecessary code, jokes, etc. have all been removed from the final code/app|N/A|
|Design|We have fuzzed all route/paths and parameters to verify that no errors/responses contain unintended functionality|N/A|
|Design|We have rate-limited requests to all endpoints by IP and/or session, to prevent abuse and denial of service attacks|[Link](https://cheatsheetseries.owasp.org/cheatsheets/Denial_of_Service_Cheat_Sheet.html)|
|Privacy|We have verified that all deleted items (messages, photos, profile updates, etc) are immediately made inaccessible to all users, so they cannot have any CRUD operations performed on them.|N/A|


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
|Check npm package|Bundlephobia help dev to determine the performance impactof adding npm package to front-end - [Link](https://bundlephobia.com)|
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
