# IS2545 - DELIVERABLE 5: Security Testing

Jinrong Liu (jil181@pitt.edu)

For this assignment, I use OWASP Zed Attack Proxy (ZAP) as the testing tool for finding vulnerabilities in web application.

The URL that I choose to attack is http://demo.testfire.net/.

##Vulnerability 1 - SQL Injection

1. Since SQL databases generally hold sensitive data, this vulnerability attacks confidentiality most frequently. It is also possible to modify or delete information by using SQL commands, and the change of information will cause the loss of integrity.

2. Interception and modification can exploit this vulnerability.

3. Attacks that exploit this vulnerability can be both passive and active. If attacks only browse sensitive data and do not modify any information, the attacks should be passive. If attacks did any modification, the attacks should be active. 

4. By exploiting this vulnerability, there will be some risks which include data loss or corruption, unauthorized access, and denial of access.

5. To fix this vulnerability, do not trust client side input, even if there is client side validation in place. In general, type check all data on the server side.

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

1. This vulnerability attacks on integrity by injecting untrusted snippets of JavaScript in the the web application without validation.

2. Modificaion and Fabrication can exploit this vulnerability.

3. Attacks that exploit this vulnerability are active.

4. By exploiting this vulnerability, there will be risks including retrieval of data from the target web application,  modification of content on the target page, and redirection victims to another malicious or spoof site. These risks will cause data loss, denial of service, etc.

5. To fix this vulnerability:
 - Use vetted Library or framework.
 - Set all cookies using HttpOnly attribute, protect the cookie from accessible to malicious client side scripts that use document.cookies.
 - Set input validation, assume all inputs from external sources are malicious.

####URL: http://demo.testfire.net/default.aspx

####Exploit Cross-Site Scripting

- Go to the homepage of the test website and find the seach field.
- Input "\<script>alert(678);\</script>" in the search field.
- Click on "Go" button or press enter.

####Screenshot:
![screenshot3](https://github.com/lajbrc/Deliverable5/blob/master/Screenshots/Vulnerability2.png?raw=true)


##Vulnerability 3 - Directory Browsing

1. This vulnerability mainly attacks confidentiality, because by browsing the directory, sensitive information may be exposed to the attacker.

2. Interception can exploit this vulnerability.

3. Attacks that exploit this vulnerability are passive.

4. There will be data loss and unauthorized access due to exploiting this vulnerability.

5. To fix this vulnerability: disable directory browsing. If this is required, make sure the listed files do not induce risks.

####URL: http://demo.testfire.net/bank/

####Exploit Directory Browsing

- Go to the URL listed above.

####Screenshot:
![screenshot4](https://github.com/lajbrc/Deliverable5/blob/master/Screenshots/Vulnerability3.png?raw=true)


##Reference
1. [OWASP Top 10 Vulnerabilities by IBM Security](https://www.youtube.com/watch?v=02mLrFVzIYU&index=1&list=PLoyY7ZjHtUUVLs2fy-ctzZDSPpawuQ28d)

2. [Hacking Altoro Mutual](http://blog.dornea.nu/2013/05/06/hacking-altoro-mutual/#0b6275b4fd4340d418195012eb027c55)

