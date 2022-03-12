# CRLF injection

CRLF injections are vulnerabilities where the attacker is able to inject CR (carriage return, ASCII 13) and LF (line feed, ASCII 10) characters into the web application. This lets the attacker add extra headers to HTTP responses or even make the browser ignore the original content and process injected content instead.
</br>
###### What is CRLF - Carriage return/Line Feed</br>
CR - Carriage Return, referred also as cartridge return, which moves the cursor position to the beginning of the line.</br>
LF - Means new line or one line down from current line.</br>
Together they act in moving the cursor to the beginning of new line.</br>


        ASCII control characters:
         00 NULL (Null character) 
         01 SOH (Start of Header) 
         02 STX (Start of Text) 
         03 ETX (End of Text)
         04 EOT (End of Trans.) 
         05 ENQ (Enquiry) 
         06 ACK (Acknowledgement) 
         07 BEL (Bell) 
         08 BS (Backspace) 
         09 HT (Horizontal Tab)
         10 LF Line feed) 
         11 VT (Vertical Tab) 
         12 FF (Form feed) 
         13 CR (Carriage return)
         14 SO (Shift Out) 
         15 SI (Shift In)
 
CRLF Used in HTTP to separate HTTP headers from Body


![CRLF-1](https://user-images.githubusercontent.com/83446765/157963846-977da293-8ac4-4ca5-8fe7-06559016171d.png)


###### What is CRLF Injection Attack?

CRLF is used in the HTTP for separating the Headers from the body and this helps the HTTP Server or Client to understand where the headers end and where the body of the request/response starts.

In CRLF attack, the attacker inserts CRLF combinations in the input fed (normally URL) to the server in the HTTP request, thus by creating a confusion to the web server in identifying Headers and body.

Any extra CRLF's in the HTTP response are misread by clients/proxies/caches or any consumer of the response and might trick them into believing the end of header or packet.



###### HTTP response splitting also known as CRLF:

HTTP response splitting occurs when:

• Data enters a web application through an untrusted source, mostfrequently an HTTP request.
• The data is included in an HTTP response header sent to a web userwithout being validated for malicious characters.

HTTP response splitting is a means to an end, not an end in itself. At its root, the attack is straightforward: an attacker passes malicious data to a vulnerable application, and the application includes the data in an HTTP response header.

To mount a successful exploit, the application must allow input that contains CR (carriage return, also given by %0d or \r) and LF (line feed, also given by %0a or \n)characters into the header AND the underlying platform must be vulnerable to the injection of such characters. These characters not only give attackers control of the remaining headers and body of the response the application intends to send, but also allow them to create additional responses entirely under their control.



</br>
</br>
</br>
</br>
</br>
</br>
</br>
Refrences:
<p><a href="https://owasp.org/www-community/attacks/HTTP_Response_Splitting">Refrence1</a> / <a href="https://www.youtube.com/watch?v=8E5vEkqeQII">Refrence2</a></p>
