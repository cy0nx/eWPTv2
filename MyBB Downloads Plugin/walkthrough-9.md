![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.001.png)

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.002.png)
<table><tr><th colspan="1" valign="top"><b>Name</b> </th><th colspan="1" valign="top">MyBB Downloads Plugin </th></tr>
<tr><td colspan="1" rowspan="2" valign="top"><b>URL</b> </td><td colspan="1" valign="bottom"><https://www.attackdefense.com/challengedetails?cid=9> </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">Real World Webapps : Stored XSS </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

**Solution:**  

**Step 1:** Inspect the web application. 

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.003.jpeg)

**Step 2:** Search on google “MyBB Downloads Plugin vulnerability” and look for publicly available exploits. ![ref1]

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.005.jpeg)

The exploit db link contains the payload required to exploit the vulnerability. **Exploit DB Link: <https://www.exploit-db.com/exploits/44400>** ![ref1]

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.006.jpeg)

**Step 3:** The user has to authenticate in order to exploit the vulnerability. The login credentials are provided in the challenge description. 

**URL:** http://ocgvy1ejrur9vzo2zxsi0e3u1.mumbaix.attackdefenselabs.com/member.php?action=login 

**Credentials:** 

- **Username:** test2 
- **Password:** password 

**Login Page** 

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.007.jpeg)

**Admin Dashboard ![ref1]**

**Step 4:** Navigate to the downloads page. ![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.008.jpeg)

**URL:** http://ocgvy1ejrur9vzo2zxsi0e3u1.mumbaix.attackdefenselabs.com/downloads.php 

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.009.jpeg)

**Step 5:** Click on the General button. ![ref1]

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.010.jpeg)

**Step 6:** Click on New Download button. 

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.011.jpeg)

**Step 7:** Inject the payload in the title field and enter any data in Short description, Download description, Title page field. 

**Payload:** <BODY ONLOAD=alert('XSS')> ![ref1]

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.012.jpeg)

Click on Publish Download button. ![ref1]

![](Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.013.jpeg)

The XSS payload triggered successfully. **References:**  

1. MyBB (<https://mybb.com/>) ![ref1]
1. MyBB Plugin Downloads (<https://community.mybb.com/mods.php?action=view&pid=854>)  
1. MyBB Plugin Downloads 2.0.3 - Cross-Site Scripting (<https://www.exploit-db.com/exploits/44400>)  

[ref1]: Aspose.Words.430ac682-afc1-48df-ab32-3a71a88f1eec.004.png
