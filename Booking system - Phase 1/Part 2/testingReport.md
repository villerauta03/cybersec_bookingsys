# Testing report 08-03-2025
This second part of the assignment was surprisingly difficult to find any vulnerabilities on, not only because of the new table structure in the database but also because zaproxy couldn't find any of the vulnerabilities that were present in the previous section.
The main objective of this testing was to discover any and all new vulnerabilities in the shared program, as well as confirm the existence of any of the old ones from the previous iteration.
I was unable to discover any glaring errors with this version. In addition to that, I was also surprised because the database table structure was completely different from the previous version, being multiple tables starting with "zephyr" and me being unable to even see any of the new added usernames put into "zephyr_users" made it a bit difficult to try and think up of how to bypass it.
At the end, the only real warnings I got were 12 cases of User Agent Fuzzer with a blue flag, not constituting any serious issue.
It seems the security of the program has been severely increased from the previous iteration. That, or I ran the tests incorrectly.
