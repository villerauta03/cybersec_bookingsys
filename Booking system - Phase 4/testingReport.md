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
We started testing the application by first going over the Phase 3 authorization table, and updating it through testing the application. We went to each page in the autrhorization table and checked the functionalities, and updated the table as needed. We then proceeded to add the new pages in the application to the table and checked each of the functionalities present in them. We noted things such as the code throwing an error if the user tries to register an account under 15 years old and a password less than 8 characters.

To find new pages within the application, we ran a zaproxy test (which also helped us find the answers to some of the GDPR table questions) at https://github.com/villerauta03/cybersec_bookingsys/blob/main/Booking%20system%20-%20Phase%204/2025-04-16-ZAP-Report-.md including a spider and an AJAX spider.
We also ran a wfuzz command against the common wordlist to check for any pages and api calls. We were able to find `/api/users` and `/api/account` this way. 
For SQL Injection testing we used sqlmap and we checked the request and response headers with Burp suite to check for CSRF protections.

We were not able to discover any admin panel or anything of the sort.

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


# GDPR Compliance Checklist – Web-based Booking System

| **Result** | **Personal data mapping and minimization** |
| :----: | :--- |
| &nbsp;✅ / ⚠️email and password are collected and saved (password is hashed) &nbsp; | Have all personal data collected and processed in the system been<br> identified? (e.g., name, email, age, username) |
| &nbsp;✅&nbsp; | Have you ensured that only necessary personal data is collected (data minimization)? |
| &nbsp;✅ /⚠️ The user age is checked but not otherwise saved &nbsp; | Is user age recorded to verify that the booker is over 15 years old? |

---

| **Result** | **User registration and management** |
| :----: | :--- |
| &nbsp;❌ /⚠️ The page exists but no policy is written there &nbsp; | Does the registration form (page) include GDPR-compliant consent for processing<br> personal data (e.g., acceptance of the privacy policy)?|
| &nbsp;❌/⚠️ The users can view their information but they cannot edit it &nbsp; | Can users view, edit, and delete their own personal data via their account? |
| &nbsp;❌/⚠️ No administrator panel or anything of that kind exists within the confines of the system &nbsp; | Is there a mechanism for the administrator to delete a reserver in<br> accordance with the "right to be forgotten"? |
| &nbsp;✅/⚠️ An account cannot be created if the user selects a date of birth which would make them under 15 years of age. &nbsp; | Is underage registration (under 15 years) and booking functionality restricted? |

---

| **Result** | **Booking visibility** |
| :----: | :--- |
| &nbsp;✅ &nbsp; | Are bookings visible to non-logged-in users only at the resource level<br> (without any personal data)? |
| &nbsp;✅ &nbsp; | Is it ensured that names, emails, or other personal data of bookers are not exposed<br> publicly or to unauthorized users? |

--- 

| **Result** | **Access control and authorization** |
| :----: | :--- |
| &nbsp;❌/⚠️ Any user is able to modify or add resources and bookings. Deletion is not possible even for administrators. &nbsp; | Have you ensured that only administrators can add, modify, and delete<br> resources and bookings? |
| &nbsp;✅ &nbsp; | Is the system using role-based access control (e.g., reserver vs. administrator)? |
| &nbsp;✅/⚠️ Administrators seem to have all the same permissions as regular users for the most part. &nbsp; | Are administrator privileges limited to ensure GDPR compliance (e.g., administrators<br> cannot use data for unauthorized purposes)? |

---

| **Result** | **Privacy by Design Principles** |
| :----: | :--- |
| &nbsp;✅ &nbsp; | Has Privacy by Default been implemented (e.g., collecting the minimum data by default)? |
| &nbsp;❌/⚠️ Logs do not appear to be implemented at all, unless the /api/ pages count. &nbsp; | Are logs implemented without unnecessarily storing personal data? |
| &nbsp;✅ &nbsp; | Are forms and system components designed with data protection in mind<br> (e.g., secured login, minimal fields)? |

---

| **Result** | **Data security** |
| :----: | :--- |
| &nbsp;✅/⚠️ CSRF token in request header,<br> XSS flaws not detected with Zaproxy,<br> SQL injection not possible as tested with sqlmap &nbsp; | Are CSRF, XSS, and SQL injection protections implemented? |
| &nbsp;✅&nbsp; | Are passwords securely hashed using a strong algorithm (e.g., bcrypt, Argon2)? |
| &nbsp;❌/⚠️ From what I can tell no data backup or recovery processes exist in the application &nbsp; | Are data backup and recovery processes GDPR-compliant? |
| &nbsp;❌/⚠️ The data appears to be stored locally in the user's computer &nbsp; | Is personal data stored in data centers located within the EU? |

---

| **Result** | **Data anonymization and pseudonymization** |
| :----: | :--- |
| &nbsp;❌/⚠️The only personal data collected and stored is the email address, which is plaintext and viewable. &nbsp; | Is personal data anonymized where possible? |
| &nbsp;❌ &nbsp; | Are pseudonymization techniques used to protect data while maintaining its utility? |

---

| **Result** | **Data subject rights** |
| :----: | :--- |
| &nbsp;❌&nbsp; | Can users download or request all personal data related to them (data access request)? |
| &nbsp;❌&nbsp; | Is there an interface or process for users to request the deletion of their personal data? |
| &nbsp;❌&nbsp; | Can users withdraw their consent for data processing? |

---

| **Result** | **Documentation and communication** |
| :----: | :--- |
| &nbsp;❌/⚠️ The privacy policy page exists, but no actual policy is in place. &nbsp; | Is there a privacy policy available to users during registration and easily accessible? |
| &nbsp;❌&nbsp; | Are administrators and developers provided with documented data protection practices <br>and processing activities? |
| &nbsp;❌&nbsp; | Is there a documented data breach response process (e.g., how to notify authorities <br>and users of a breach)? |

---

**Symbols used:**  
✅ Pass (a note can be added)  
❌ Fail (a note can be added)  
⚠️ Attention (a note can be added)
