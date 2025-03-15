# Testing report 15-03-2025
The initial results of testing were about the same as with Phase 1 Part 2, Zaproxy was not able to find any glaring errors in the program. After running "whatweb http://localhost:8000" I was able to confirm that there is now a Content Security Policy in place to protect against XSS attacks, X-Content-Type-Options against MIME-sniffing, and X-Frame-Options:DENY to stop clickjacking. gobuster only found open endpoints in /login and /register so there is no instant glaring error in an open admin panel. The email field is also being validated properly to only accept email addresses so it is not vulnerable to SQL Injection. I was able to make the password into an SQL statement, but trying to implement SQL Injection through the password didn't work, so I can assume there is some level of password validation.  
Running sqlmap on level 5 risk 3 also returned: "[CRITICAL] all tested parameters do not appear to be injectable.", confirming no SQL injection on the login page.  
Getting the hashed passwords and emails was taking me a good amount of trouble originally because the SQL connection was not recognizing my statements for some reason. I was able to input "SELECT * FROM zephyr_users;" and get a list of all of the accounts in the database, and their hashed passwords. I then downloaded the rockyou.txt file present inside of the Kali Linux system and ran it against the hashed passwords with hashcat against MD5 with the command "hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt.gz". This let me get the unhashed versions of 4 of the passwords:
- d50ba4dd3fe42e17e9faa9ec29f89708:iamironman -- *Password for genius@starkindustries.com*
- a0e8402fe185455606a2ae870dcbc4cd:carrots123 -- *Password for whatsupdoc@looneytunes.tv*            
- d730fc82effd704296b5bbcff45f323e:donuts4life -- *Password for doh@springfieldpower.net*            
- 706ab9fc256efabf4cb4cf9d31ddc8eb:darkside42 -- *Password for iamyourfather@deathstar.gov*  

1234
