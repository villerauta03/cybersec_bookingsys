# Testing report 18-02-2025
I noticed a few vulnerabilities when testing out the web page. After running the initial tests with zaproxy, (and some manual tests with the Burp environment) the first obvious issue that came to notice was that the passwords were being saved into the database unencrypted. The zaproxy code outlined a myriad number of safety concerns with the usernames and passwords it was allowed to insert within the app, including SQL statements, a various number of various injections (SQL, SSI, XSS), system commands, proxy URLs, etc. The fact all of these were even allowed to be inputted into the app in the first place displays that there is **no validation or sanitization** in the usernames/passwords process, making the app incredibly weak towards injection.
The tests also outlined the possibility of path traversal, being able to access other sections of the webpage by simple manipulation of the file path, potentially giving malicious actors access to sensitive data. The ZAP report also outlines the lack of a CSP (Content Security Policy) header, making the page incredibly vulnerable towards data injection and cross-site scripting (XSS) attacks. 
Some other various vulnerabilities include:
- **No Anti-clickjacking header**: Attackers can trick users into performing actions on the site without their knowledge because of the lack of a proper CSP header.
- **Application error disclosure**: The application doesn't hide it's error messages and they are free to be looked at, potentially revealing even deadlier vulnerabilities.
- **MIME-sniffing vulnerability**: The lack of an X-Content-Type-Options header exposes the vulnerability to MIME-sniffing, revealing even more vulnerabilities in the system.

There are a various number of steps to take to secure the application better. 
- Validate and sanitize all user input.
- Configure proper HTTP-headers to prevent various risks like XSS, Clickjacking, and MIME-sniffing.
- Block sensitive information from being seen by just anyone, implement proper error handling.
- Apply the principle of least privilege.
