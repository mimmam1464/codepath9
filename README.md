# Project 8 - Pentesting Live Targets

Time spent: 4 hours spent in total

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

Vulnerability #1: SQLI. /blue/public/salesperson.php?id=%27%20OR%20SLEEP(5)=0--%27 accepts the input and puts it into sql without any sanitization.
VIDEO: SQLI.mp4

Vulnerability #2: Session Hijacking/Fixation The login system in the blue site does not use proper session management. After logging into the green site with username and password one does not require authentication in the blue site.
VIDEO: SESSION.mp4

## Green

Vulnerability #1: username enumeration when a random username and password is used, the login unsuccessful text appears in regular text. However when pperson is used ( a known existing username ) the unsucessful message is shown in bold.
VIDEO: User Enumeration.mp4

Vulnerability #2:  Cross-Site Scripting. On the green site when feedback is provided with xss scripts injected in the input, the script gets executed whenever the view feed back page is loaded in https://35.184.88.145/green/public/staff/feedback/index.php
VIDEO: XSS.mp4

## Red

Vulnerability #1:  Insecure Direct Object Reference. Going to salesperson page allows user to compromise and view the territories covered by them by just changing the id number.
VIDEO: IDOR.mp4

Vulnerability #2: Cross-Site Request Forgery. The Red site does not require the csrf token to match before processing the post request. It accepts any post request and executes input.
VIDEO: CSRF.mp4

## Notes

Describe any challenges encountered while doing the work

-IDOR attack was the easiest to perform from an attacker's point of view.

-The user enumaration flaw detection was easiest to capture. The first step in preventing username enumeration in an application is to identify all of the relevant attack surface. This includes not only the main login but also all of the more peripheral authentication functionality such as account registration, password change and account recovery. We should never treat recognized user and unrecognized user differently in the front end. The only message sent to the front end should be the login failed with not much reasoning.

-CMS was not made fimiliar in our course. I have not used or interacted with it.

-YES it is possible to execute a SQL injection with AND. It all depends on the situation DB structure and you designing the attack. All we have to do is form a logic that returns true for the information that we need.

-The XSS attacks depends on when a user uses the infected portion of the site. Therefore the attacker will necessarily need some information or notification tool that notifies him or her that the attack has been executed.

-Incorporate the self-submitting form into something that he usually trusts and browse into almost everyday.

-Obtaining a session token via packet sniffing or another attack channel seems more likely to be achievable than establishing a session with a service and connecting the victim to that session and hoping the service does not have countermeasures.



