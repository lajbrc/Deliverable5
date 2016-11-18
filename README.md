# IS2545 - DELIVERABLE 5: Security Testing

Jinrong Liu (jil181@pitt.edu)

For this assignment, I use OWASP Zed Attack Proxy (ZAP) as the testing tool for finding vulnerabilities in web application.

The URL that I choose to attack is http://demo.testfire.net/.

##Vulnerability 1 - SQL Injection

1. Since SQL databases generally hold sensitive data, this vulnerability attacks confidentiality most frequently. 
It is also possible to modify or delete information by using SQL commands, and the change of information will cause the loss of integrity.

2. Interception and modification can exploit this vulnerability.

3. Attacks that exploit this vulnerability can be both passive and active. 
If attacks only browse sensitive data and do not modify any information, the attacks should be passive. 
If attacks did any modification, the attacks should be active. 

4. By exploiting this vulnerability, there will be some risks which include data loss or corruption, unauthorized access, and denial of access.

5. To fix this vulnerability, do not trust client side input, even if there is client side validation in place. 
In general, type check all data on the server side.

####URL: http://demo.testfire.net/bank/login.aspx

####Exploit SQL Injection:

- Go to the login webpage.
- Enter a random username (e.g., “admin”) in Username field.   
- Then enter [ZAP' OR '1'='1' -- ] in Password field.     
- Then click on “Login”.

####Screenshots:
![screenshot1](https://github.com/lajbrc/Deliverable5/blob/master/Screenshots/Vulnerability1_1.png?raw=true)
![screenshot2](https://github.com/lajbrc/Deliverable5/blob/master/Screenshots/Vulnerability1_2.png?raw=true)


##Vulnerability 2 - Cross-Site Scripting (Reflected)

1. This vulnerability attacks on integrity.

2. Fabrication can exploit this vulnerability.

3. Attacks that exploit this vulnerability are active.

4. By exploiting this vulnerability, there will be risks including retrieval of data from the target web application, 
modification of content on the target page, and redirection victims to another malicious or spoof site.

5. To fix this vulnerability:
 - Use vetted Library or framework.
 - Set all cookies using HttpOnly attribute, protect the cookie from accessible to malicious client side scripts that use document.cookies.
 - Set input validation, assume all inputs from external sources are malicious.

####URL: http://demo.testfire.net/default.aspx

####Exploit Cross-Site Scripting

- Go to the homepage of the test website and find the seach field.
- Input "<script>alert(678);</script>" in the search field.
- Click on "Go" button or press enter.

####Screenshot:
![screenshot3](https://github.com/lajbrc/Deliverable5/blob/master/Screenshots/Vulerability2.png?raw=true)


##Vulnerability 3 - Directory Browsing

1. This vulnerability mainly attacks confidentiality, because by browsing the directory, sensitive information may be exposed to the attacker.

2. Interception can exploit this vulnerability.

3. Attacks that exploit this vulnerability are passive.

4. There will be data loss and unauthorized access due to exploiting this vulnerability.

5. To fix this vulnerability: disable directory browsing. 
If this is required, make sure the listed files do not induce risks.

####URL: http://demo.testfire.net/bank/

####Exploit Directory Browsing

- Go to the URL listed above.

####Screenshot:
![screenshot4](https://github.com/lajbrc/Deliverable5/blob/master/Screenshots/Vulnerability3.png?raw=true)
