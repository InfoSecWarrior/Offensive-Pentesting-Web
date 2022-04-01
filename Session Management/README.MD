# SESSION MANAGEMENT

## What is Session Management?
A web session is a sequence of network HTTP request and response transactions associated with the same user. Modern and complex web applications require the retaining of information or status about each user for the duration of multiple requests. Therefore, sessions provide the ability to establish variables – such as access rights and localization settings – which will apply to each and every interaction a user has with the web application for the duration of the session.

  - Session Hijacking
 
    - Types of Session Hijacking

      - Session ID / Tokens sniffing

        - Example 1.
        - Example 2.
 
      - Session fixation
      - Session donation
      - Session ID / Tokens brute force

## Session Hijacking

The Session Hijacking attack consists of the exploitation of the web session control mechanism, which is normally managed for a session token.

Because http communication uses many different TCP connections, the web server needs a method to recognize every user’s connections. The most useful method depends on a token that the Web Server sends to the client browser after a successful client authentication. A session token is normally composed of a string of variable width and it could be used in different ways, like in the URL, in the header of the http requisition as a cookie, in other parts of the header of the http request, or yet in the body of the http requisition.

The Session Hijacking attack compromises the session token by stealing or predicting a valid session token to gain unauthorized access to the Web Server.

## Session ID / Tokens sniffing

# Example 1.  
![Screenshot from 2022-03-31 14-41-54](https://user-images.githubusercontent.com/101032811/161021190-0d08b552-4dc2-4a90-8f87-913da1340a1e.png)

# Example 2.
## Cross-site script attack
    <SCRIPT>alert(document.cookie);</SCRIPT>
![Cross-Site_Scripting](https://user-images.githubusercontent.com/101032811/161023314-0f61b6a2-0c15-4a5b-8b60-dd68fea88e95.png)

## Session Fixation

Session Fixation is an attack that permits an attacker to hijack a valid user session. The attack explores a limitation in the way the web application manages the session ID, more specifically the vulnerable web application. When authenticating a user, it doesn’t assign a new session ID, making it possible to use an existent session ID. The attack consists of obtaining a valid session ID (e.g. by connecting to the application), inducing a user to authenticate himself with that session ID, and then hijacking the user-validated session by the knowledge of the used session ID. The attacker has to provide a legitimate Web application session ID and try to make the victim’s browser use it.

![5](https://user-images.githubusercontent.com/101032811/161234484-1036e61a-21bf-40bc-bc2e-fd47b57b4f91.png)

## Session Donation

![Session_Donation1](https://user-images.githubusercontent.com/101032811/161236381-8a4f1091-4ce3-4566-a059-5d2a1a5df472.png)

## Session ID / Tokens brute force

![Session_ID1](https://user-images.githubusercontent.com/101032811/161240781-7a2e910e-5e1f-42f7-a506-411729fd1de5.png)

# References

[OWASP](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)
