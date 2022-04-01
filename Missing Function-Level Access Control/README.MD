# Missing Function Level Access Control
  The missing function-level access control vulnerability refers to the flaws in the authorization logic. By exploiting it, an attacker, who could be an existing user of the application, is able to escalate privileges and access restricted functionalities. For example, the restricted administrator-level features are often a target for this attack.
  ##### Attack Mechanics
  
  Attackers exploit this vulnerability primarily by manipulating URLs. For example, consider these URLs provided by an application:

> example.com/account/view

> example.com/account/remove

Although both require authenticated users, let’s assume that the **/remove** endpoint should be available only to the admin user. If an unauthenticated or an authenticated nonadmin user could access the **/remove** endpoint, this is a missing function-level access control flaw.

#### Discription

  Access control enforces policy such that users cannot act outside of their intended permissions. Failures typically lead to unauthorized information disclosure, modification or destruction of all data, or performing a business function outside of the limits of the user. Common access control vulnerabilities include:
* Bypassing access control checks by modifying the URL, internal application state, or the HTML page, or simply using a custom API attack tool.
* Allowing the primary key to be changed to another’s users record, permitting viewing or editing someone else’s account.
* Elevation of privilege. Acting as a user without being logged in, or acting as an admin when logged in as a user.
* Metadata manipulation, such as replaying or tampering with a JSON Web Token (JWT) access control token or a cookie or hidden field manipulated to elevate privileges, or abusing JWT invalidation.
* CORS misconfiguration allows unauthorized API access.
* Force browsing to authenticated pages as an unauthenticated user or to privileged pages as a standard user. Accessing API with missing access controls for POST, PUT and DELETE.

#### Example Attack Scenarios

  **Scenario #1**: The application uses unverified data in a SQL call that is accessing account information:
  > **pstmt.setString(1, request.getParameter("acct"));**
 
  > **ResultSet results = pstmt.executeQuery( );**

  An attacker simply modifies the ‘acct’ parameter in the browser to send whatever account number they want. If not properly verified, the attacker can access any user’s account.
  
  > **http://example.com/app/accountInfo?acct=notmyacct**

  **Scenario #2**: An attacker simply force browses to target URLs. Admin rights are required for access to the admin page.
  > **http://example.com/app/getappInfo**
  
  > **http://example.com/app/admin_getappInfo**

  If an unauthenticated user can access either page, it’s a flaw. If a non-admin can access the admin page, this is a flaw.
  
 #### Missing Function Level Access Control
   * Reported by [kiraak-boy](https://hackerone.com/kiraak-boy)
  
   * Reported to [Dashlane](https://hackerone.com/dashlane)
   
   * https://hackerone.com/reports/152407
  
### References

  1. [OWASP Access Control](https://owasp.org/www-project-top-ten/2017/A5_2017-Broken_Access_Control)
  2. [O'Reilly Missing Function-Level Access Control](https://www.oreilly.com/library/view/securing-node-applications/9781491982426/ch07.html#:~:text=The%20missing%20function%2Dlevel%20access,privileges%20and%20access%20restricted%20functionalities.)
