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


















