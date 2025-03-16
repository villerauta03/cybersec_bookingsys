# Testing report 15-03-2025
The initial results of testing were about the same as with Phase 1 Part 2, Zaproxy was not able to find any glaring errors in the program. After running "whatweb http://localhost:8000" I was able to confirm that there is now a Content Security Policy in place to protect against XSS attacks, X-Content-Type-Options against MIME-sniffing, and X-Frame-Options:DENY to stop clickjacking. gobuster only found open endpoints in /login and /register so there is no instant glaring error in an open admin panel. The email field is also being validated properly to only accept email addresses so it is not vulnerable to SQL Injection. I was able to make the password into an SQL statement, but trying to implement SQL Injection through the password didn't work, so I can assume there is some level of password validation.  
Running sqlmap on level 5 risk 3 also returned: "[CRITICAL] all tested parameters do not appear to be injectable.", confirming no SQL injection on the login page.  
Getting the hashed passwords and emails was taking me a good amount of trouble originally because the SQL connection was not recognizing my statements for some reason. I was able to input "SELECT * FROM zephyr_users;" and get a list of all of the accounts in the database, and their hashed passwords. I then downloaded the rockyou.txt file present inside of the Kali Linux system and ran it against the hashed passwords with hashcat against MD5 with the command "hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt.gz". This let me get the unhashed versions of 4 of the passwords:
- d50ba4dd3fe42e17e9faa9ec29f89708:iamironman -- *Password for genius@starkindustries.com*
- a0e8402fe185455606a2ae870dcbc4cd:carrots123 -- *Password for whatsupdoc@looneytunes.tv*            
- d730fc82effd704296b5bbcff45f323e:donuts4life -- *Password for doh@springfieldpower.net*            
- 706ab9fc256efabf4cb4cf9d31ddc8eb:darkside42 -- *Password for iamyourfather@deathstar.gov*  

For the other passwords, I bruteforced each one by one. Since I now knew the hashes to be in MD5-format, I could use hashcat to bruteforce them and unhash each missing password one-by-one. It was a very long process, though.  
I will list each password I found by bruteforcing, as well as the time it took to unhash them in the table below:
| Email | Hashed Password | Unhashed Password | Time |
|---|---|---|---|
| darkknight@gothamwatch.com | 735f7f5e652d7697723893e1a5c04d90 | iamvengeance | 10 sec |
| chimichanga@fourthwall.com | 7cb56c2b86150b797cff32eaef97f338 | breaking4thwall | 1 sec |
| elementary@221bbaker.uk | 12c9cef0bfb6b91c42b363b4cf02d8bb | deduction221B | 1 sec |
| whysoserious@gothamchaos.net | f158d479ee181aac68b000a60e7a3d7a | chaos123! | 1 sec |
| quackattack@duckburg.org | ea261222d4867b3ebdfadbe2b35e19d5 | mickeyisjealous | 1 sec |
| ruhroh@mysterymachine.com | ad17fbd845000b11678ccbf94e135b56 | snacks4scooby | 11 sec |

I did use the tips the teacher gave us on the ItsLearning platform for bruteforcing the passwords, as otherwise it could have taken days to crack some of the more complicated ones. This lead to the bruteforcing taking significantly shorter than it would have in a real situation, where I would not have had any help and would have had to wait for hashcat to slowly iterate over each combination.  
Using hashcat mask attacks, I was able to unhash all of the other 6 passwords to complete the assignment.  

*I did have some trouble trying to figure out how to run the hashcats so it would check for multiple things in the same character (like checking if a character is uppercase, then checking if the same character is lowercase, etc.) but I was able to figure out the command for it eventually (ex. hashcat -m 0 -a 3 hash.txt -1 ?u?l?s?d chaos?1?1?1!). The table lists how long it took for the hashcat command to find the passwords, not how long I personally took to figure out each command.*

### The complete table of all emails, hashed passwords, and unhashed passwords:
| Email | Hashed Password | Unhashed Password | Cracking method |
|---|---|---|---|
| whatsupdoc@looneytunes.tv | a0e8402fe185455606a2ae870dcbc4cd | carrots123 | Dictionary attack |
| doh@springfieldpower.net | d730fc82effd704296b5bbcff45f323e | donuts4life | Dictionary attack |
| darkknight@gothamwatch.org | 735f7f5e652d7697723893e1a5c04d90 | iamvengeance | Bruteforce |
| chimichanga@fourthwall.com | 7cb56c2b86150b797cff32eaef97f338 | breaking4thwall | Bruteforce |
| iamyourfather@deathstar.gov | 706ab9fc256efabf4cb4cf9d31ddc8eb | darkside42 | Dictionary attack |
| elementary@221bbaker.uk | 12c9cef0bfb6b91c42b363b4cf02d8bb | deduction221B | Bruteforce |
| genius@starkindustries.com | d50ba4dd3fe42e17e9faa9ec29f89708 | iamironman | Dictionary attack |
| whysoserious@gothamchaos.net | f158d479ee181aac68b000a60e7a3d7a | chaos123! | Bruteforce |
| quackattack@duckburg.org | ea261222d4867b3ebdfadbe2b35e19d5 | mickeyisjealous | Bruteforce |
| ruhroh@mysterymachine.com | ad17fbd845000b11678ccbf94e135b56 | snacks4scooby | Bruteforce |
