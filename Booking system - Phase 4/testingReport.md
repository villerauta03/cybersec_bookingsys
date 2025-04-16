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

## The Authorization Table of the Application (updated from Phase 3)
| **Page / Feature** | **Guest** | **Reserver** | **Administrator** |
|:----|:----:|:----:|:----:|
| `/` (index)                |✅| ✅ | ✅ |
| └─ Viewing reservations | ✅ | ✅ | ✅ |
| └─ Viewing the emails of users who made the reservations | ❌ | ✅ | ✅ |
| `/reservation` | ❌ | ✅ | ✅ |
| └─ Creating a reservation | ❌ | ✅ * Reservation end date cannot be later than reservation start date | ✅ |
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
| └─ Create a user with "reserver" role | ✅ * User password must be longer than 8 characters | ❌`Invalid CSRF Token` | ❌`Invalid CSRF Token` |
| └─ Create a user with "administrator" role | ✅ * User password must be longer than 8 characters | ❌`Invalid CSRF Token` | ❌`Invalid CSRF Token` |
| `/logout` | ✅ | ✅ | ✅ |
| `/api/users` |❌|✅|✅|
| `/api/resources` |❌|✅|✅|
| `/api/session` |❌|✅|✅|


# GDPR Compliance Checklist – Web-based Booking System

| **Result** | **Personal data mapping and minimization** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Have all personal data collected and processed in the system been<br> identified? (e.g., name, email, age, username) |
| &nbsp;✅/❌/⚠️&nbsp; | Have you ensured that only necessary personal data is collected (data minimization)? |
| &nbsp;✅/❌/⚠️&nbsp; | Is user age recorded to verify that the booker is over 15 years old? |

---

| **Result** | **User registration and management** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Does the registration form (page) include GDPR-compliant consent for processing<br> personal data (e.g., acceptance of the privacy policy)?|
| &nbsp;✅/❌/⚠️&nbsp; | Can users view, edit, and delete their own personal data via their account? |
| &nbsp;✅/❌/⚠️&nbsp; | Is there a mechanism for the administrator to delete a reserver in<br> accordance with the "right to be forgotten"? |
| &nbsp;✅/❌/⚠️&nbsp; | Is underage registration (under 15 years) and booking functionality restricted? |

---

| **Result** | **Booking visibility** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Are bookings visible to non-logged-in users only at the resource level<br> (without any personal data)? |
| &nbsp;✅/❌/⚠️&nbsp; | Is it ensured that names, emails, or other personal data of bookers are not exposed<br> publicly or to unauthorized users? |

--- 

| **Result** | **Access control and authorization** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Have you ensured that only administrators can add, modify, and delete<br> resources and bookings? |
| &nbsp;✅/❌/⚠️&nbsp; | Is the system using role-based access control (e.g., reserver vs. administrator)? |
| &nbsp;✅/❌/⚠️&nbsp; | Are administrator privileges limited to ensure GDPR compliance (e.g., administrators<br> cannot use data for unauthorized purposes)? |

---

| **Result** | **Privacy by Design Principles** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Has Privacy by Default been implemented (e.g., collecting the minimum data by default)? |
| &nbsp;✅/❌/⚠️&nbsp; | Are logs implemented without unnecessarily storing personal data? |
| &nbsp;✅/❌/⚠️&nbsp; | Are forms and system components designed with data protection in mind<br> (e.g., secured login, minimal fields)? |

---

| **Result** | **Data security** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Are CSRF, XSS, and SQL injection protections implemented? |
| &nbsp;✅/❌/⚠️&nbsp; | Are passwords securely hashed using a strong algorithm (e.g., bcrypt, Argon2)? |
| &nbsp;✅/❌/⚠️&nbsp; | Are data backup and recovery processes GDPR-compliant? |
| &nbsp;✅/❌/⚠️&nbsp; | Is personal data stored in data centers located within the EU? |

---

| **Result** | **Data anonymization and pseudonymization** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Is personal data anonymized where possible? |
| &nbsp;✅/❌/⚠️&nbsp; | Are pseudonymization techniques used to protect data while maintaining its utility? |

---

| **Result** | **Data subject rights** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Can users download or request all personal data related to them (data access request)? |
| &nbsp;✅/❌/⚠️&nbsp; | Is there an interface or process for users to request the deletion of their personal data? |
| &nbsp;✅/❌/⚠️&nbsp; | Can users withdraw their consent for data processing? |

---

| **Result** | **Documentation and communication** |
| :----: | :--- |
| &nbsp;✅/❌/⚠️&nbsp; | Is there a privacy policy available to users during registration and easily accessible? |
| &nbsp;✅/❌/⚠️&nbsp; | Are administrators and developers provided with documented data protection practices <br>and processing activities? |
| &nbsp;✅/❌/⚠️&nbsp; | Is there a documented data breach response process (e.g., how to notify authorities <br>and users of a breach)? |

---

**Symbols used:**  
✅ Pass (a note can be added)  
❌ Fail (a note can be added)  
⚠️ Attention (a note can be added)
