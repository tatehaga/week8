# Project 8 - Pentesting Live Targets

Time spent: 2 hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: Session Hijacking/Fixation
Codepath provides tools for changing a given phpsessionid.  Using those tools, we can change a phprequest id for a different session and still gain access using a valid phpsessionid with no other credentials.  In my example I used session hijacking.


Vulnerability #2: SQL Injection
The edit user url has a vulnerable field, by setting php=##, we can replace the ## with ' OR SLEEP(5)=0--' to perform an SQL attack.


## Green

Vulnerability #1: XSS
The feedback field of the contact page is vulnerable to javascript injection, so any staff member that tries to view the feedback will activate any javascript in the database.

Vulnerability #2: Username Enumeration
If an attacker inputs a username that is in the database but has an incorrect password, the data returns a bold "Log in is not successful" message, when if the username is not in the database the message is in bold.  To counteract this, the other sites do not treat incorrect logins differently than logins not in the database.


## Red

Vulnerability #1: IDOR
An attacker can view any salesperson in the system even if they're not listed in the salesperson page by changing the id number in the web address "https://35.184.88.145/red/public/salesperson.php?id=##" where id is a low number.


Vulnerability #2: Cross-site Request Forgery
By sending a post request to a valid user through the feedback field and having them issue the post request by clinking on the link and open the attacking html file, then an attacker can make changes to the website that only people with valid logins have access to.


## Notes

Describe any challenges encountered while doing the work

