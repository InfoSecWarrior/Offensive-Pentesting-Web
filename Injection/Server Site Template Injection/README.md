# SSTI (Server Side Template Injection)
Some web applications use template engines to separate the visual presentation (HTML, CSS…) from the application logic (PHP, Python…). These engines allow the creation of template files in the application. Templates are a mixture of fixed data (layout) and dynamic data (variables). When the application is used, the template engine will replace the variables contained in a template with values and will transform the template into a web page (HTML) and then send it to the client.

A server-side template injection (SSTI) vulnerability occurs when user data is embedded directly in a template and then interpreted by the template engine. This allows attackers to inject arbitrary directives to manipulate the template engine.

  - The source of the problem is that the data transmitted by users is  interpreted directly by the template engine (as dynamic data), instead  of being integrated as fixed data.
				
- This type of vulnerability is most often found on sites that want to  offer advanced customisation features such as wikis, blogs, marketing  applications or CMS.

- An SSTI vulnerability usually occurs when a template is modified to  obtain a customised result for a specific need and users have access to  the template modification functions.

### How it works

  ![image](image.png)

### Server Side Template Injection Payloads

	{{4*4}}[[5*5]]
	{{7*'7'}} would result in 7777777
	{{config.items()}}
[More Payloads..](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection)

#### Server Side Template Injection Reports

Report 1:

- Reported by [zombiehelp54](https://hackerone.com/zombiehelp54)

- Reported to [Shopify](https://hackerone.com/shopify)

- https://hackerone.com/reports/423541

Report 2:

- Reported by [yaworsk](https://hackerone.com/yaworsk)

- Reported to [Unikrn](https://hackerone.com/unikrn)

- https://hackerone.com/reports/164224


#### References
 1. [OWASP Server Side Template Injection](https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/07-Input_Validation_Testing/18-Testing_for_Server_Side_Template_Injection)
 2. [VAADATA SSTI](https://www.vaadata.com/blog/server-side-template-injection-vulnerability-what-it-is-how-to-prevent-it/)
 3. [Payload All The Things:SSTI Payloads](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection)
