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
