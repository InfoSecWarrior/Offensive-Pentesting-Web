# OS-command Injection
An OS command injection is a web security vulnerability that enables the execution of unauthorized operating system commands. An OS command injection vulnerability arises when a web application sends unsanitized, unfiltered system commands to be executed. Due to the insufficient input validation an attacker could inject their own commands to be operated on the shell level. The attacker introduces operating system commands via user- supplied data such as cookies, forms or HTTP headers.

# Types of Command Injection

  <ol>
  <li><a href=#result-based-command-injection>Result based command injection</a></li>
  <li><a href=#blind-command-injection>Blind command injection</a>
    <ul>
      <li><a href=#the-time-based-technique-blind>The time-based technique (Blind)</a></li>
      <li><a href=#the-file-based-technique-semi-blind>The file-based technique (Semi blind)</a></li>
    </ul>
    </li>
  </ol>
  
  # Result based command Injection
  
  The output of the executed command would be visible in the response.In this attack an attacker can view the results of the command executed was success or not.
  
  <b>Scenario</b>: The application executes a shell command containing user-supplied product and store IDs, and returns the raw output from the command in its response.\
  <b>Output</b>: Here the vulnerable parameter is stored.\
  <b>Explanation</b>: Here we have used the command whoami. It displays the name of the current user.
  
  ![image](https://user-images.githubusercontent.com/94695985/157230206-42e6b172-f3aa-4ad7-93e5-c980e4e93887.png)
  <br>
  <br>
  <br>
  <br>
  <br>
  
  
  # Blind command Injection
  
  The output of the executed command is not visible in the response. In this attack an attacker cannot view the results of the command executed.
  
  ## The time-based technique (Blind) 
  
   This technique is based on time delays
      
   <b>Scenario</b>: The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response.\
   <b>Output</b>: Here the vulnerable parameter is an email address.
   
   ![image](https://user-images.githubusercontent.com/94695985/157255763-d7a0c26e-1b08-47ef-9272-7d8fe6dd21af.png)
  <ul><b>As seen in the snapshot, we have captured the request of the feedback form.</b></ul>
  <br>
  <br>
  <br>
  <br>
  <br>
  
  ![image](https://user-images.githubusercontent.com/94695985/157256015-2055c66d-4ca8-4324-82d1-c505bdb1742c.png)
  <ul><b>As seen in the snapshot, the email parameter is vulnerable to blind command injection.</b></ul>
  <br>
  <br>
  <br>
  <br>
  <br>
  
  
   ## The file-based technique (Semi blind)
  
   This technique is used when we are not able to view the results of the command injection, but we can write it to a file accessible by us.
    
   <b>Scenario</b>: The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response. You can use output redirection to capture the output from the command. There is a writable folder at: /var/www/images/ \
   <b>Output</b>: Here the vulnerable parameter is an email address.
   
   ![image](https://user-images.githubusercontent.com/94695985/157257571-8d18b6a8-8474-4816-9502-58e683cec0d3.png)
   <ul><b> As seen in the snapshot, the email parameter is vulnerable and the output is written in the output.txt file.</b></ul>
   <br>
  <br>
  <br>
  <br>
  <br>
  
   
   ![image](https://user-images.githubusercontent.com/94695985/157257719-0b784c6c-8c37-4871-a203-0c17a527325e.png)
   <ul><b> As seen in the snapshot, we are clicking on view details of the image and capturing the request.</b></ul>
   <br>
  <br>
  <br>
  <br>
  <br>
  
   
   ![image](https://user-images.githubusercontent.com/94695985/157257843-748c6eba-0049-4dd9-9e31-71e87f076bba.png)
   <ul><b> Capturing the request we observe filename parameter specifies the image name.</b></ul>
   <br>
  <br>
  <br>
  <br>
  <br>
  
   
   ![image](https://user-images.githubusercontent.com/94695985/157258105-4a6c1b9f-96f6-46ab-acaa-3624793771e2.png)
   <ul><b> we are replacing the original value of the filename with the one having the output of the command specified. i.e output.txt</b></ul>
   <br>
  <br>
  <br>
  
   
  <b> Explanation</b>: Here we are redirecting the output of the command in a file that is accessible to us.
   
   <dl>
  <dt><b>What if the web server’s root directory is not writable or accessible?</b></dt>
  <dd>- We can use temporary directories (“/tmp” or “/var/tmp/”) to store the output of injecting commands.</dd>
  </dl>
  
  <b>Limitation</b> : Usually, we cannot read files located in temp directories through web applications.
  
  <b>Bypass of the limitation :</b>
  <ul>
  <li> Apply the time-based technique to read the content of the files</li>
  <li>It is also referred to as tempfile based technique</li>
  </ul>
  
  # Useful Commands

<table border="0" cellpadding="0" cellspacing="0" width="396">
<tbody>
<tr>
	<td valign="top">
		<p><strong>Purpose of command</strong></p>
	</td>
	<td valign="top">
		<p><strong>Linux</strong></p>
	</td>
	<td valign="top">
		<p><strong>Windows</strong></p>
	</td>
</tr>
<tr>
	<td valign="top">
		<p>Name of current user</p>
	</td>
	<td valign="top">
		<p>whoami</p>
	</td>
	<td valign="top">
		<p>whoami</p>
	</td>
</tr>
<tr>
	<td valign="top">
		<p>Operating system</p>
	</td>
	<td valign="top">
		<p>uname -a</p>
	</td>
	<td valign="top">
		<p>ver</p>
	</td>
</tr>
<tr>
	<td valign="top">
		<p>Network configuration</p>
	</td>
	<td valign="top">
		<p>ifconfig</p>
	</td>
	<td valign="top">
		<p>ipconfig /all</p>
	</td>
</tr>
<tr>
	<td valign="top">
		<p>Network connections</p>
	</td>
	<td valign="top">
		<p>netstat -an</p>
	</td>
	<td valign="top">
		<p>netstat -an</p>
	</td>
</tr>
<tr>
	<td valign="top">
		<p>Running processes</p>
	</td>
	<td valign="top">
		<p>ps -ef</p>
	</td>
	<td valign="top">
		<p>tasklist</p>
	</td>
</tr>
</tbody>
</table>

# Payloads
  
  <ol>
  <li><a href="https://github.com/illupak/Offensive-Pentesting-Web/blob/main/Injections/OS-command%20Injection/Unix%20command%20injection%20payloads.txt" >Unix</a></li>
  <li><a href="https://github.com/illupak/Offensive-Pentesting-Web/blob/main/Injections/OS-command%20Injection/Windows%20command%20injection%20payloads.txt" >Windows</a></li>
  </ol>
  
# Labs For Practice

  https://portswigger.net/web-security/os-command-injection#:~:text=What%20is%20OS%20command%20injection%3F,application%20and%20all%20its%20data.
  
# Top Finding
 
  https://hackerone.com/reports/303061
  
  https://hackerone.com/reports/295841
  
  https://hackerone.com/reports/363815
  
  https://hackerone.com/reports/298873
  
  https://hackerone.com/reports/497312
  

# References
 
  https://www.whitehatsec.com/glossary/content/os-command-injection#:~:text=An%20OS%20command%20injection%20is,system%20commands%20to%20be%20executed.
  
  https://www.indusface.com/learning/what-is-command-injection/ 
  
  https://github.com/payloadbox/command-injection-payload-list
