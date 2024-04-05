---
Title: SWS101 Flipped Class 3
categories: [SWS101, Flipped_class3]
tags: [SWS101]
---

# Topic: OWASP top 10 vulnerabilities

![owasp](/pictures/SWS_pictures/owasp10.png)

## Introduction
OWASP stands for open web application security project. OWASP TOP 10 vulnerabilities is a list of the 10 most common web application security risks. They are;
1. Broken access control
2. Cryptographic failures
3. Injection
4. Insure design 
5. Security misconfiguration
6. Vulnerable and outdated component
7. identification and authentication failures
8. Software and data integrity failures
9. Security login and monitoring failures
10. Server-side request forgery(SSRF)

To learn cyber security is to practice, so i am going to do the tryhackme owasp top 10 room.

### Broken access control
To keep our house secure we have a lock on the door. If our lock is not that strong or if we forget to lock the door, strangers can easily get inside our house and steal things or mess around in our house. Just like that, broken access control allows attackers to bypass authorisation, allowing them to view sensitive data or perform tasks they aren't supposed to.

__Task 4__: Broken Access Control(IDOR challenge)

**What is the flag?**

I paste the machine ip address in the browser and I was given the login form as shown below.

![owasp](/pictures/SWS_pictures/thmlogin.png)
 
It was already given in the instruction that username is noot and password is test1234. So I just entered this username and password.

![owasp](/pictures/SWS_pictures/thmgiven.png)

I was successfully logged in but I didn't get the flag and then I viewed the hint and it said “The URL contains ?note_id=1 - I wonder what happens if you change the parameter value? You might be able to access another user's notes.” Then I changed that number to 2 3 4 and so on until I got the flag. The flag was in ?note_id=0.

__Ans__: flag{fivefourthree}.

### Cryptographic failures
A cryptographic failure refers to any vulnerability arising from the misuse of cryptographic algorithms for protecting sensitive information. 

![owasp](/pictures/SWS_pictures/crypto.png)

Let's take an example.There was a couple Wangpo and Yuden. One day Wangpo asked Yuden for a facebook account. Yuden, who is concerned about security, sends her phone number and password in the special code(it is like a secret key) which Wangpo understands. Cryptographic failure is when that special code gets broken. And there comes the man in the middle attack who takes advantage of the cryptographic failure. 

__Task 8__: Cryptographic failure(Challenge)

To do this challenge I have to connect to the web application (http://machine_ip:81).

**What is the name of the mentioned directory?**

After seeing the question I was blank but I got the hint “Have a look at the source code on the /login page.” Then I clicked on the login and inspected the source code. The developer has left themselves a note in a comment, indicating that there is sensitive data in a specific directory.

![owasp](/pictures/SWS_pictures/assest.png)

__Ans__: /pictures

**Navigate to the directory you found in question one. What file stands out as being likely to contain sensitive data?**

![owasp](/pictures/SWS_pictures/webappdb.png)

__Ans__: webapp.db

**Use the supporting material to access the sensitive data. What is the password hash of the admin user?**

To open the webapp.db file we need sqlite3.

![owasp](/pictures/SWS_pictures/sqlite3.png)

With little knowledge on sql i could get the password hash for user admin.

__Ans__:6eea9b7ef19179a06954edd0f6c05ceb

**Crack the hash. What is the admin's plaintext password?**

Crackstation website is extremely good for cracking weak password hashes. So I used the crackstation website to crack password hash for admin.

![owasp](/pictures/SWS_pictures/crackstation.png)

__Ans__: qwertyuiop

**Log in as the admin. What is the flag?**

### Injection
Injection attacks occur when attackers exploit vulnerabilities in web applications that accept untrusted data. 
Some common example include : 

***SQL injection***: This occurs when user-controlled input is passed to SQL queries. As a result, an attacker can pass in SQL queries to manipulate the outcome of such queries.

***OS command injection***: This occurs when user input is passed to system commands. As a result, an attacker can execute arbitrary system commands on application servers, potentially allowing them to access users' systems.

__Task 10__: Command injection

I will take advantage of a bash feature called "inline commands". To execute inline commands, I need to enclose them in the following format $(your_command_here). 

**What strange text file is in the website's root directory?**

To list the file in that directory we use the ‘ls’ command. When exploiting command injection, we should give commands in $(ls) format.

![owasp](/pictures/SWS_pictures/cowsay1.png)

__Ans__: drpepper.txt

**How many non-root/non-service/non-daemon users are there?**

I use the command $(cat /etc/passwd) to list the users.

![owasp](/pictures/SWS_pictures/no_non_root.png)

There are no non-root/non-service/non-daemon users.

__Ans__: 0

**What user is this app running as?**

With the ‘whoami’ command I can get the user who is in that app. 

![owasp](/pictures/SWS_pictures/apache.png)

__Ans__: apache

**What is the user's shell set as?**

I  scrolled down to the bottom and found the user’s [apache] shell [/sbin/nologin].

![owasp](/pictures/SWS_pictures/sbin.png)

__Ans__: /sbin/nologin

**What version of Alpine Linux is running?**

Hint: The version can be found in "/etc/alpine-release".
So I ran the command “$(cat /etc/alpine-release)”.

![owasp](/pictures/SWS_pictures/version.png)

__Ans__: 3.16.0

### Insure design 
Insecure design refers to vulnerabilities which are inherent to the application's architecture.
It's like building a house without considering fire escapes or a strong foundation. Insecure design happens when developers don't prioritize security throughout the creation process. They might focus on functionality first, leaving security as an afterthought.
Try to reset joseph's password. Keep in mind the method used by the site to validate if you are indeed joseph.
I don't know the password of Joseph so I am going to click on i forgot password.

![owasp](/pictures/SWS_pictures/josep.png)

When I clicked on forget, I was asked to answer the following question.

![owasp](/pictures/SWS_pictures/joseph1.png)

Luckily the username is joseph.

![owasp](/pictures/SWS_pictures/joseph2.png)

From the security question, “what’s your favorite color?” is the only question that i can solve with brute force. Finally I guess correctly, it is green. By the way, it is case-sensitive.

![owasp](/pictures/SWS_pictures/joseph3.png)

So the new temporary password has been generated. With that password I can login now.

**What is the value of the flag in joseph's account?**

![owasp](/pictures/SWS_pictures/joseph4.png)

There are three folders and the flag is in a private folder.

__Ans__: THM{Not_3ven_c4tz_c0uld_sav3_U!}

### Security misconfiguration
It occurs when security could have been appropriately configured but was not. Security misconfiguration is like having an alarm system in your house but forgetting to set it, or having a complex lock with the key left in it. This vulnerability can often lead to more vulnerabilities.
Werkzeug is a vital component in Python-based web applications as it provides an interface for web servers to execute the Python code. 

**What is the database file name (the one with the .db extension) in the current directory?**

In the werkzeug console, I pasted the following python code to execute the ls -l command on the server.
import os; print(os.popen("ls -l").read())

![owasp](/pictures/SWS_pictures/werk.png)

__Ans__: todo.db

**Modify the code to read the contents of the app.py file, which contains the application's source code. What is the value of the secret_flag variable in the source code?**

Here I just need to modify this code to read the content of app.py.
import os; print(os.popen("ls -l").read())
To display the content of a file the command is “cat” so the modified code is, <br> <ins>import os; print(os.popen("cat app.py").read()).

![owasp](/pictures/SWS_pictures/werk2.png)

__Ans__: THM{Just_a_tiny_misconfiguration}

### Vulnerable and outdated component
A vulnerable and outdated component is a software component that is no longer being supported by the developer, making it susceptible to security vulnerabilities.

__Task 15__: Vulnerable and Outdated Components - Lab 

**What is the content of the /opt/flag.txt file?** <br>
Hint: You know it's a bookstore application. You should check for recent unauthenticated bookstore apps RCEs.

On the Exploit-DB site, I searched for the keyword ‘online book store’ and I filtered it by showing only verified ones.

![owasp](/pictures/SWS_pictures/expbypass.png)

There are lots of unverified EDB. Downloads the verified one which is for online bookstores.

![owasp](/pictures/SWS_pictures/expDb.png)

To exploit I ran this command on the terminal <br>
<ins> Python3 47887.py http://machine_ip:84/  <br>

47887.py is the exploit file.

![owasp](/pictures/SWS_pictures/expflag.png)

__Ans__:  THM{But_1ts_n0t_my_f4ult!}

### Identification and authentication failures
Authentication allows users to gain access to web applications by verifying their identities. The most common form of authentication is using a username and password mechanism. This failure occurs when a system or application isn't able to correctly identify or authenticate a user.

__Task 17__: Identification and Authentication Failures Practical
I have opened the given link http://10.10.158.236:8088.

Instruction  <br>
Try to register with darren as your username. You'll see that the user already exists, so try to register " darren" instead.

![owasp](/pictures/SWS_pictures/darren.png)

darren username already exists so as instructed I will register darren with space at the beginning.

![owasp](/pictures/SWS_pictures/darren1.png)

In this way I can register darren. Now I can login as darren with the password I set up during registration.

![owasp](/pictures/SWS_pictures/darren2.png)

**What is the flag that you found in darren's account?**

__Ans__: fe86079416a21a3c99937fea8874b667

**What is the flag that you found in arthur's account?**
To get the flag from arthur’s account it is the same as how I did in darren.

![owasp](/pictures/SWS_pictures/arhtur.png)

__Ans__: d9ac0f7db4fda460ac3edeb75d75e16e

### Software and data integrity failures
This vulnerability arises from code or infrastructure that uses software or data without using any kind of integrity checks. Since no integrity verification is being done, an attacker might modify the software or data passed to the application, resulting in unexpected consequences. There are mainly two types of vulnerabilities in this category:

***Software Integrity Failures***

__Task 19__<br>
**What is the SHA-256 hash of https://code.jquery.com/jquery-1.12.4.min.js?**<br>
There are many online tools to generate hashes one of it is SRI hash generator.

![owasp](/pictures/SWS_pictures/hash.png)

__Ans__: sha256-ZosEbRLbNQzLpnKIkEdrPv7lOy9C27hHQ+Xp8a4MxAQ=

***Data Integrity Failures***<br>
The structure of a JWT token is formed of 3 parts:

![owasp](/pictures/SWS_pictures/jwt.png)

__Task 20__<br>
Try logging into the application as guest. What is guest's account password?
Hint: Try logging in with the wrong credentials.

![owasp](/pictures/SWS_pictures/cookies.png)

Now I know that both username and password is guest.

![owasp](/pictures/SWS_pictures/cookielogin.png)

I have successfully logged in as a guest but only the admin can access the flag.

__Ans__: guest

**What is the name of the website's cookie containing a JWT token?**<br>
Now I have successfully logged in, I might have JWT stored as a cookie in your browser. So I click on inspect to open developer tools. 

![owasp](/pictures/SWS_pictures/Jwttoken.png)

In the storage tab there are cookies and all the details are there.

__Ans__: jwt-session

**Use the knowledge gained in this task to modify the JWT token so that the application thinks you are the user "admin".** <br>
Copy the value from the value column and decode the header and payload separately.

![owasp](/pictures/SWS_pictures/decode1.png)

![owasp](/pictures/SWS_pictures/decode2.png)

Copy the output string and encode it by changing the ‘HS256’ to ‘none’ and username ‘guest’ to ‘admin’ separately. 

![owasp](/pictures/SWS_pictures/encode1.png)

![owasp](/pictures/SWS_pictures/encode2.png)

Then copy paste that output Base64 of both header and payload together back into the value column in cookies and then refresh the browser.<br>
Don't forget to put full stop at the end of our output base64.
<ins>eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=.eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzExODA2MTQ3fQ==.

**What is the flag presented to the admin user?**

__Ans__: THM{Dont_take_cookies_from_strangers}


### Security login and monitoring failures

__Task 21__<br>
**What IP address is the attacker using?**

![owasp](/pictures/SWS_pictures/dwtask.png)

Inside the download task file I could see that 49.99.13.16 has tried to login many times but failed. That could be the ip address of an attacker.

__Ans__: 49.99.13.16

**What kind of attack is being carried out?**<br>
Hint: What do you call trying combinations of usernames and passwords to gain access to users' accounts?

__Ans__: Brute force

Attackers have tried every combination of username and password.

### Server-side request forgery(SSRF)
Server-side request forgery is a web security vulnerability that allows an attacker to cause the server-side application to make requests to an unintended location. 

__Task 22__<br>
Head to the given site(http://10.10.158.236:8087/), where you'll find a simple web application.

**Explore the website. What is the only host allowed to access the admin area?**<br>

![owasp](/pictures/SWS_pictures/website.png)

I clicked on the three bars at the upper right corner.

![owasp](/pictures/SWS_pictures/adminarea.png)

There I found the admin area section and when I clicked on it, it says ‘Admin interface only available from localhost’.

![owasp](/pictures/SWS_pictures/localhost.png)

__Ans__: localhost

**Check the "Download Resume" button. Where does the server parameter point to?**
When I hover on the Downloads Resume button the server parameter points to secure-file-storage.com .

![owasp](/pictures/SWS_pictures/severpoint.png)

__Ans__: secure-file-storage.com

**Using SSRF, make the application send the request to your AttackBox instead of the secure file storage. Are there any API keys in the intercepted request?**

__Ans__: THM{Hello_Im_just_an_API_key}

## Conclusion
After completion of this room I learned about the top 10 owasp, how they occurred, and how it  can be exploited. I came across many online tools that help in hacking. They are Crackstation, Werkzeug console, Exploit DB site, SRI hash generator, Base64 encoder and decoder. There is a famous quote by Douglas MacArthur, “There is no security on this earth; there is only opportunity.”
