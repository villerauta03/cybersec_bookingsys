# The Booking System Project → Phase 4
In this fourth section of the Booking System Project, we will be testing for GDPR compliance of the website in question, and compiling the things we find into the tables pasted under "GDPR Compliance Checklist". The GDPR is the European Union's general personal data use law, 
and all webpages which utilize personal information in any manner must comply with it's standards.  
We will also be utilizing some information from the table we made in our last assignment, Booking Project Phase 3.

In addition, if they do not exist within the appropriate filepaths, we are to define and create the a privacy policy, terms of service, as well as the cookie policy for the application. 

## The initial scenario for the application:
**You are a novice penetration tester at a company. Your company should implement the following application (specs):**  

1. The system is accessed via a web browser.  
2. Users can register and, after registration, log in to the system.  
3. A registered and logged-in user acts as either a resource reserver or an administrator.  
4. The administrator can add, remove, and modify resources and reservations.  
5. The administrator can delete the reserver.  
6. A reserver can book a resource if they are over 15 years old.  
7. Resources can be booked on an hourly basis.  
8. The booking system displays booked resources without requiring login, but does not show the reserver's identity  
9. The client, your company, requires that the system complies with GDPR regulations.  
10. The system provider has stated that the software is developed following the Privacy by Design (PbD) principle.  

## Documentation of the testing process
We started testing the application by first going over the Phase 3 authorization table, and updating it through testing the application. We went to each page in the authorization table and checked the functionalities, and updated the table as needed. We then proceeded to add the new pages in the application to the table and checked each of the functionalities present in them. We noted things such as the code throwing an error if the user tries to register an account under 15 years old and a password less than 8 characters.

**The GDPR Checklist 📋 tables have been compiled in a separate .md file:**

📌 [GDPR checklist](https://github.com/villerauta03/cybersec_bookingsys/blob/main/Booking%20system%20-%20Phase%204/gdpr_checklist.md)

To find new pages within the application, we ran a zaproxy test (which also helped us find the answers to some of the GDPR table questions), including a spider and an AJAX spider.

📌 [Zaproxy Report](https://github.com/villerauta03/cybersec_bookingsys/blob/main/Booking%20system%20-%20Phase%204/2025-04-16-ZAP-Report-.md)

We also ran a wfuzz command against the common wordlist to check for any pages and api calls. We were able to find `/api/users` and `/api/account` this way. 
For SQL Injection testing we used sqlmap and we checked the request and response headers with Burp suite to check for CSRF protections.

We were not able to discover any admin panel or anything of the sort.

After the initial exploration of the service, we completed the second part of the assignment, which is creating the cookie policy, terms of service, and privacy policy of the application. We have compiled each into their own .md files in this folder. 
- 📌 [Terms of Service](https://github.com/villerauta03/cybersec_bookingsys/blob/main/Booking%20system%20-%20Phase%204/termsofservice.md)
- 📌 [Privacy Policy](https://github.com/villerauta03/cybersec_bookingsys/blob/main/Booking%20system%20-%20Phase%204/privacypolicy.md)
- 📌 [Cookie Policy](https://github.com/villerauta03/cybersec_bookingsys/blob/main/Booking%20system%20-%20Phase%204/cookiepolicy.md)

  
## The Authorization Table of the Application (updated from Phase 3)
| **Page / Feature** | **Guest** | **Reserver** | **Administrator** |
|:----|:----:|:----:|:----:|
| `/` (index)                |✅| ✅ | ✅ |
| └─ Viewing reservations | ✅ | ✅ | ✅ |
| └─ Viewing the emails of users who made the reservations | ❌ | ✅ | ✅ |
| `/reservation` | ❌ | ✅ | ✅ |
| └─ Creating a reservation | ❌ | ✅ * Reservation end date cannot be later than reservation start date | ✅ * Reservation end date cannot be later than reservation start date |
| `/reservation?id=` (individual reservation page)| ❌| ✅ | ✅ |
| └─ Edit own reservation | ❌ | ✅ | ✅ |
| └─ Edit others' reservations | ❌ | ✅ | ✅ |
| `/resources`| ❌ | ✅ | ✅ |
| └─ Creating a resource | ❌ | ✅ | ✅ |
| `/resources?id=` (individual resource page) | ❌ | ✅ | ✅ |
| └─ Edit own resource | ❌ | ✅ | ✅ |
| └─ Edit other's resource | ❌ | ✅ | ✅ |
| `/login` | ✅ | ✅ | ✅ |
| └─ Login as "reserver" user | ✅ | ✅ | ✅ |
| └─ Login as "administrator" user | ✅ | ✅ | ✅ |
| `/register` | ✅ | ✅ | ✅ |
| └─ Create a user with "reserver" role | ✅ * User password must be longer than 8 characters | ✅ (Sometimes `Invalid CSRF Token` but must intentionally try to achieve it) | ✅ (Sometimes `Invalid CSRF Token` but must intentionally try to achieve it) |
| └─ Create a user with "administrator" role | ✅ * User password must be longer than 8 characters | ✅ (Sometimes `Invalid CSRF Token` but must intentionally try to achieve it) | ✅ (Sometimes `Invalid CSRF Token` but must intentionally try to achieve it) |
| `/account` | ✅ | ✅ | ✅ |
| └─ Logout with the "Log out"-button | ✅ | ✅ | ✅ |
| `/logout` | ✅ | ✅ | ✅ |
| `/privacypolicy` | ✅ | ✅ | ✅ |
| `/cookiepolicy` | ✅ | ✅ | ✅ |
| `/terms` | ✅ | ✅ | ✅ |
| `/api/users` |❌|✅|✅|
| `/api/resources` |❌|✅|✅|
| `/api/session` |❌|✅|✅|
| `/api/reservations` |✅|✅|✅|
| `/api/account` |❌|✅|✅|
