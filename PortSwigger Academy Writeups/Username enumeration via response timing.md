# **Authentication Labs**

## **Aim:**

This lab is vulnerable to username enumeration using its response times. To solve the lab, enumerate a valid username, brute-force this user's password, then access their "My account" page. 

(Pre-tip: As the lab has protection against IP-based brute-force protection, the bypass header **X-Forwarded-For:** can be used)

## **Steps to solve the lab:**

1. Access the **'Username enumeration via response timing'** lab.

2. Enter any username and password and capture the request in Burp.

3. Send the request to the Intruder Tab. 
   (Tip: Dont Forward or Drop the request in Proxy tab, let it be.)

4. At Intruder, select the Attack Type as **Pitchfork.**

5. Add the header **X-Forwarded-For:** and select it accordingly for payload brute-forcing [Payload 1].
   (Example: X-Forwarded-For: $000$ )
   
6. Then select the username field for payload brute-forcing [Payload 2].

7. For Payload 1, select the type as Numbers [From: 0; To: 100; Step: 1]

8. For Payload 2, select the type as Simple List, paste the usernames from given list.

9. Enter random text in password field (upto ~100 characters) and start the attack.

10. In Intruder attack window, enable the column 'Response received' and sort that column to find the username which has higher response time.
   (Tip: The valid username, takes higher response time than the incorrect one. Repeat the attack to confirm the username)
   
11. As the username is enumerated, again prepare for an Pitchfork based attack at Intruder.

12. Enter the enumerated username from previous result, let the settings of Payload 1 be the same but the set the Payload 2 to password field and paste the given passwords in payload tab, and start the attack.

13. Sort the the attack results by Status code. The payload which has the code 301 is the correct password.

14. On knowing both the username & password, use them to login.

15. If the protection prevents you from login, intercept and add the X-Forwarded-For header with a numerical value.


## **If you find this useful, STAR the repo as much more will be coming...**
