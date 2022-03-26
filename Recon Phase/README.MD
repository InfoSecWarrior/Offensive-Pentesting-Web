# Recon Phase

What is Recon Phase? In the recon phase we recon all the resources from where we can get access into the web applications without having its credentials.
So check out these options mentioned below :

   		1.	 Resolve dns names using dig
		2.	 IP to Location
		3.	 Nmap don't ping scan
		4.	 Nmap Service Version Detection
		5. 	 Enumerated supported HTTP methods using nmap
		6. 	 Checking SSL and TLS version using nmap
		7. 	 Host Header Injection
		8. 	 waybackurls
		9.  	 whatweb
		10.	 Find Hidden Web Directories with Dirsearch
    11.  Do some of the dorks.
		

		
# 1. Resolve DNS names using DIG
    
  	  # dig google.com
 
  	  # dig google.com @64.6.64.6
 
 	  # dig google.com A
 
 	  # dig google.com AAAA
 
 	  # dig google.com NS

      # dig google.com MX
    
      # dig google.com SOA
    
    
   # Resolve DNS Websites :

	   https://www.dnsqueries.com/en/dns_lookup.php

	   https://www.digwebinterface.com/

	   https://toolbox.googleapps.com/apps/dig/

	   https://mxtoolbox.com/DNSLookup.aspx

	   https://dns.google/query
   
   
   
  # 2. IP to Location
   

    https://www.iplocation.net/

    https://iplocation.com/

    https://tools.keycdn.com/geo

    https://ipinfo.io/
   
   
   # 3. Nmap don’t ping scan
   
    # nmap -Pn domain/ip
   
   
   # 4. Nmap service version detection

    # nmap -sT -sV 192.168.1.102
    
    
   # 5. Enumerated supported HTTP methods using nmap
    
     # nmap --script http-methods --script-args http-methods.url-path='/website' IP
     
     
   # 6. Checking SSL and TLS Versions using nmap
     
     # nmap --script ssl-enum-ciphers domain/ip
     
     
   # 7. Host Header Injection

   
![host-header-attacks](https://user-images.githubusercontent.com/95084876/156526081-71363ef9-8f32-4794-9ae3-d04fb5c66b70.jpg)


     
     What is Host Header Injection - https://portswigger.net/web-security/host-header
     
     Check vulnerable or not : 
     
     nmap -sV --script=http-headers domain/ip
     
   # 8. Waybackurls

	   # waybackurls https://google.com

     
   # 9. Whatweb

	   # whatweb https://google.com


   #  10. Find Hidden Web Directories with Dirsearch

	   # dirb https://google.com 
	   
	   

  # 11. Now do some of the dorks:
    Google
    Github
    Shodan
    
## Google Dork :
    site:https://amazon.com file:pdf
    site:https://amazon.com file:backup
    site:https://amazon.com "index.of"
   ![google dock](https://user-images.githubusercontent.com/95084876/157067975-dc8f55dd-cab5-4b7e-be88-57e3d75cb15c.png)
    
## Github Dork:
    "Amazon.com"
   ![amazon dock](https://user-images.githubusercontent.com/95084876/157067684-9f9c5294-4b12-467e-9ac2-d53bc5ca2862.jpg)
   
## Shodan Dork:
   ssl.cert.subject.cn:"*.amazon.com"
 
 ![shodan dock](https://user-images.githubusercontent.com/95084876/157068557-6923d9b8-0ae7-4a06-8563-af44cba6e99d.png) 
 
 
## Resources to Understand Recon Methodology in Better way :

https://www.boxpiper.com/posts/google-dork-list

https://forum.bugcrowd.com/t/are-google-dorks-often-leveraged/2095/6

https://malavsharma.medium.com/magic-of-shodan-15dd17854099

https://www.bugcrowd.com/resources/webinars/github-recon-and-sensitive-data-exposure/

https://hackerone.com/reports/397527

https://mavericknerd.github.io/knowledgebase/nahamsec/recon_session_1/

https://tillsongalloway.com/finding-sensitive-information-on-github/index.html

https://www.hackerone.com/ethical-hacker/how-recon-and-content-discovery

 
 
  
   
    
