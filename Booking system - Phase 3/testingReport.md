# The Booking System Project → Phase 3
In this part of the booking system project, we are aiming to test access control rules, horizontal privilege escalation, and vertical privilege escalation.  
The main steps of this exercise focus on checking authorization rules and protections, making sure that guest users can only do x things, logged in users y things, admin users z things, and so on. We will be confirming the measures taken to protect the authorization of the application.

## The Authorization Table of the Application
| **Page / Feature** | **Guest** | **Reserver** | **Administrator** |
|:----|:----:|:----:|:----:|
| `/` (index)                | | | |
| └─ View resource form      | ❌ | ✅ | ✅ |
| └─ Create new resource     | ❌ | ❌ | ✅ |

During the test we will go over each functionality and each page in the application, and check if the user in question is able to perform that specific functionality or access that specific page. For this purpose we will fill out the table above as we proceed, adding notes as needed.    
To fill out the table, we will test out a number of security testing techniques, including manual review through the browser, ZAP, as well as wfuzz & http. Finally, we can have a look through the source code for the application to implement some manual code review, as is needed.

## Testing Technique 1 - Manual Browser Review of the Application
text here...

## Testing Technique 2 - ZAP Report of the Application
text here...

## Testing Technique 3 - WFUZZ & HTTP
text here...

## Manual Code Review of the Application
text here...
