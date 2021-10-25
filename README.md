# Project 8 - Pentesting Live Targets

### Project Stack and Significance
Software Security Course Assignment

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


MOHAMMAD A IMMAM


---


# Project 7 - WordPress Pentesting

#Mohammad A Immam- github: mimmam1464

Time spent: **5** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Username not Found on admin
  - [ ] Summary: On the login page, when a user attempts to login with an incorrect password, the application mentions that the password for the account is incorrect or username not found. This exposes that the account exists and potential attackers can now only worry about password.
    - Vulnerability types: exposure to the existence of username when not needed.
    - Tested in version: latest
    - Fixed in version: *
    - [ ] Steps to recreate: Go to site, type in an existing username and an incorrect password.
    - [ ] GIF: https://storage.googleapis.com/sdcismp1forms/useraccount.GIF
    - [ ] Affected source code: https://core.trac.wordpress.org/browser/trunk/src/wp-login.php
    - [Link 1](http://wpdistillery.vm/wp-login.php)
2. IDOR open to public for uploads page
  - [ ] Summary: user (with malicious intentions) can access the uploads directory without authorization
    - Vulnerability types: Direct Access or Object Reference
    - Tested in version: 4.2
    - Fixed in version: ?
  - [ ] GIF Walkthrough: https://storage.cloud.google.com/sdcismp1forms/idor.GIF?authuser=1 
  - [ ] Steps to recreate: The link is open to all for viewing all uploaded content as a direct object reference.
  - [ ] Affected source code:
    - [Link 1](http://wpdistillery.vm/wp-content/uploads/2020/)
3. Malicious Redirect to sites
  - [ ] Summary: allows attackers to redirect users to random web sites and conduct phishing malformed URL
    - Vulnerability types:Phishing
    - Tested in version:4.2
    - Fixed in version: 4.4.2
    - CVE-2016-2221
  - [ ] Steps to recreate: Use the inspect elements tool to add an a tag with an external link.
4. Stored XSS by Theme File
  - [ ] Summary: Downloading a theme from online, and renaming it to blank and packing it as a fake theme file allows achievement of an XSS attack whenever the user goes to the themes tab.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.6.2
  - [ ] Steps to recreate: Download the Theme file, keep index and css. Rename the theme to any scripting as desired. Change directory name to the same. Zip and upload the theme. Click on themes tab.
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright 2020 Mohammad A Immam
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.



