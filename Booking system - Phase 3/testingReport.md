# The Booking System Project → Phase 3
In this part of the booking system project, we are aiming to test access control rules, horizontal privilege escalation, and vertical privilege escalation.  
The main steps of this exercise focus on checking authorization rules and protections, making sure that guest users can only do x things, logged in users y things, admin users z things, and so on. We will be confirming the measures taken to protect the authorization of the application.

## The Authorization Table of the Application
| **Page / Feature** | **Guest** | **Reserver** | **Administrator** |
|:----|:----:|:----:|:----:|
| `/` (index)                |✅| ✅ | ✅ |
| └─ Viewing reservations | ✅ | ✅ | ✅ |
| └─ Viewing the emails of users who made the reservations | ❌ | ✅ | ✅ |
| `/reservation` | ❌ | ✅ | ✅ |
| └─ Creating a reservation | ❌ | ✅ * Only if the user's date of birth is 15 years or older | ✅ |
| `/reservation?id=` (individual reservation page)| ❌| ✅ | ✅ |
| └─ Edit own reservation | ❌ | ✅ | ✅ |
| └─ Edit others' reservations | ❌ | ✅ (access through address bar) | ✅ |
| `/resources`| ✅ (through address bar) | ✅ | ✅ |
| └─ Creating a resource | ✅ | ✅ | ✅ |
| `/resources?id=` (individual resource page) | ❌ (redirects to resource creation) | ✅ | ✅ |
| └─ Edit own resource | ❌ | ✅ | ✅ |
| └─ Edit other's resource | ❌ | ✅ (access through address bar) | ✅ |
| `/login` | ✅ | ✅ | ✅ |
| └─ Login as "reserver" user | ✅ | ✅ | ✅ |
| └─ Login as "administrator" user | ✅ | ✅ | ✅ |
| `/register` | ✅ | ✅ | ✅ |
| └─ Create a user with "reserver" role | ✅ | ❌`Invalid CSRF Token` | ❌`Invalid CSRF Token` |
| └─ Create a user with "administrator" role | ✅ | ❌`Invalid CSRF Token` | ❌`Invalid CSRF Token` |
| `/api/users` |✅|✅|✅|
| `/api/resources` |✅|✅|✅|

During the test we will go over each functionality and each page in the application, and check if the user in question is able to perform that specific functionality or access that specific page. For this purpose we will fill out the table above as we proceed, adding notes as needed.    
To fill out the table, we will test out a number of security testing techniques, including manual review through the browser, ZAP, as well as wfuzz & http. Finally, we can have a look through the source code for the application to implement some manual code review, as is needed.

## Testing Technique 1 - Manual Browser Review of the Application
### Before Zaproxy
I started testing the application's authorizations by going over each page granted to me in the interface. The ones I could access directly were the login page, registration page, and the index page. With the login and registration pages I could login to a user's account and create a user with one of two roles: "Reserver" and "Administrator". 
There was no significant difference between the accounts at this point except for the administrator account being able to edit reservations made on other accounts, while the regular reserver accounts were only able to edit their own reservations.  Also, the reservation account was infact able to create their own reservations, but only if they were over the age of 15. User younger than 15 was still able to create resources though.

However, I did find an error in the application. When editing your own reservation on a reserver account, you are able to change the reserver's email to that of the administrator account and save it. After saving the edit, you as the reserver are now no longer able to edit the reservation despite being the one who made it.
Another notable factor was the fact that the administrator and reserver account emails were both fully available to be viewed by anyone logged in as a reserver, which I would expect to be a significant security risk.

Also, as the last thing I tried to do was to access pages through the address bar. First I tried to go to /login and /register on my own in the search bar. There were no buttons or links on the website after you are loggin in that would redirect you to these websites, but editing the address in the search bar could get me to these pages, where the login and registration functionalities worked the exact same way as they did when I wasn't logged in.    
When I was logged in as a user, went into the `/login` page, then left it and clicked on "Log Out", and then proceeded to hit the "Previous Page" button on the browser window a few times until I reached the `/login` page again, attempting to input my information and click "Login" gave me the error `Invalid CSRF Token`. The same thing happened with registration, though unlike with the login page, just going to the registration page and attempting to register an account was enough to trigger this.  

Afterwards, I tested the `/reservation?id=` and `/resrouces?id=` individual pages for each resource and reservation. After rigorous logging in and out and testing, I was able to confirm a few oddities.   
- First of all, a guest user on the website who is not logged in can enter `/resources` to create a new resource for the website, but is not able to edit already created resources. Trying to enter into a `/resources?id=` page, for example `/resources?id=1` will just redirect you to the `/resources` page, where you will still be able to create a resource.
- As a guest user who is not signed in, trying to enter `/reservation` to create a reservation, or an individual reservation page like `/reservation?id=1` will show the message "Unauthorized access".
- As a signed in reserver user, entering `/reservation?id=1` or `/resources?id=1` will allow you to edit the reservation or resource at ID 1 regardless of whether or not the user created the reservaton or resource.

### After Zaproxy
The only new pages we were able to find where the API calls. Things such as `/api/users` where we can inspect each user and their hashed passwords added to the page, and `/resources`, where we can see all of the IDs of the resources. We are not particularly able to do much here but to see all of this information so we have added it to the table regardless.

## Testing Technique 2 - ZAP Report of the Application
After the initial runs of the `/index`, `/login`, `/register` and both of the form pages were complete, I opened zaproxy to run some automatic tests on the software and maybe reveal any new webpages. The full ZAP report can be found in this link: 
The ZAP report revealed no new pages to inspect, other than API endpoints to see the users and resources. 
## Testing Technique 3 - WFUZZ & HTTP
text here...

## Manual Code Review of the Application
text here...
