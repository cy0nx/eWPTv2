![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.001.png)

![ref1]
<table><tr><th colspan="1"><b>Name</b> </th><th colspan="1">Scanning Web Application with ZAProxy </th></tr>
<tr><td colspan="1" rowspan="2"><b>URL</b> </td><td colspan="1" valign="bottom"><https://attackdefense.com/challengedetails?cid=1888> </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">Webapp Pentesting Basics </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

**Objective:**  Scan the web application with ZAProxy and identify the possible vulnerabilities. 

**Step 1:** Identifying IP address of the target machine **Command:** ip addr 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.003.jpeg)

The IP address of the attacker machine is 192.210.1412. The target machine is located at the IP address 192.210.1413 ![ref2]

**Step 2:** Identifying open ports. **Command:** nmap 192.210.1413  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.005.png)

Port 80 and 3306 are open. 

**Step 3:** Starting Burp Suite. Click on the Menu, Navigate to "Web Application Analysis" and click on "owasp-zap". 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.006.jpeg)

ZAP:  ![ref2]


![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.007.png)

**Step 4:** Click on "Manual Explore", enter the target IP address in the Input field and click on "Launch Browser". 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.008.jpeg)

A browser session will be started with ZAP HUD. ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.009.png)

**Step 5:** Click on "Continue to your target".  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.010.png)

![ref1]

**Step 6:** Login to the web application, the login credentials are mentioned on the login page.  

**Username:** bee **Password:** bug 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.011.jpeg)

**Step 7:** Access various web pages.**  From the Choose your bug dropdown, select "HTML Injection - Reflected (GET)" and click on the Hack button. ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.012.png)

HTML Injection - Reflected (GET): 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.013.jpeg)

**Step 8:** Enter any values in the input field and click Go ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.014.jpeg)

The entered input will appear below the Go button 

**Step 9:** From the Choose your bug dropdown, Select "HTML Injection - Reflected (POST)" and click on the Hack button. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.015.png)

HTML Injection - Reflected (POST) 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.016.jpeg)

**Step 10:** Enter any values in the input field and click Go ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.017.jpeg)

The entered input will appear below the Go button 

**Step 11:** From the Choose your bug dropdown, Select "HTML Injection - Stored (Blog)" and click on the Hack button. ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.018.png)

**Step 12:** Enter any values in the input field and click Submit. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.019.jpeg)

The entered value will appear in the table.  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.020.jpeg)

**Step 13:** From the Choose your bug dropdown, Select "SQL Injection (GET/Search)" and click on the Hack button. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.021.jpeg)

SQL Injection (GET/Search) ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.022.jpeg)

**Step 14:** Enter "Joe" and click on the Search button. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.023.jpeg)

1 result will appear. 

**Step 15:** From the Choose your bug dropdown, Select "SQL Injection (GET/Select)" and click on the Hack button. ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.024.jpeg)

SQL Injection (GET/Select) ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.025.jpeg)


**Step 16:** "G.I. Joe: Retaliation" is the default selected option. Click on the "Select" button. ![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.026.jpeg)![ref1]

1 result will appear. 

**Step 17:** Configuring ZAProxy to use authenticated session. In ZAProxy, navigate to the sitemap and find the login request.  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.027.jpeg)

**Step 18:** Right click on the POST request, navigate to "Include in Context" and select on "Default Context". ![ref2]

![ref1]

![ref3]

The session Properties window will appear.  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.029.jpeg)

**Step 19:** Click on the Authentication tab under Default Context menu and select "Form-based Authentication" for the selected method.  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.030.jpeg)

Authentication Section:  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.031.jpeg)

**Step 20:** Click on the Select button and select the POST login request.  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.032.png)

The form fields will automatically be filled.  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.033.jpeg)


**Step 21:** Set the Username parameter to "login" and Enter "Login" in the "Regex pattern identified in Logged Out response messages". ![ref1]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.034.jpeg)

**Step 22:** Click on the Users tab.  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.035.jpeg)

![ref1]

**Step 23:** Click on the "Add" button and add a new user with username "bee" and password "bug" 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.036.png)

**Step 24:** Click on the "OK" button. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.037.jpeg)

**Step 25:** Click on the User lock icon.  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.038.png)

**Step 26:** Right click on the Site (http://192.210.141.3), navigate to "Include in Context" and select on "Default Context". 

![ref3]

Session Properties window will appear.  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.039.jpeg)

**Step 27:** Click on the "OK" button. Right click on the Site (http://192.210.141.3), navigate to Attack and select "Spider". 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.040.png)

**Step 28:** A dialog box will appear, select the "bee" user and click on "Start Scan" button. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.041.jpeg)

Scan Result:  ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.042.jpeg)

202 URLs were found.  

**Step 29:** Right click on the Site (http://192.210.141.3), navigate to Attack and select "Active Scan". ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.043.png)

**Step 30:** A dialog box will appear, select the "bee" user and click on "Start Scan" button. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.044.jpeg)

**Step 31:** After the scan completes, click on the "Alerts" tab. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.045.jpeg)

There are 3 critical alerts.  ![ref2]

**Step 32:** Click on Cross Site Scripting (Persistent)  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.046.jpeg)

The information regarding the URL, payload, description about the vulnerability will be displayed.  

**Step 33:** Navigate to the URL, Inject the XSS payload and click on Submit button. **URL:** http://192.210.141.3/htmli\_stored.php 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.047.png)

The XSS payload will be triggered.  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.048.jpeg)

**Step 34:** Navigate to the right side and access the Alert section of the ZAP HUD. ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.049.jpeg)

ZAP HUD:  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.050.jpeg)

**Step 35:** Click on the "Cross Site Scripting (Reflected)" and click on the first URL. ![ref2]

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.051.jpeg)

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.052.jpeg)

**Step 36:** Click on the URL on the dialog box.  

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.053.jpeg)

The XSS payload will be triggered.  ![ref2]

**Step 37:** Expand the SQL Injection Section from the Alerts section of ZAP HUD 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.054.jpeg)

**Step 38:** Click on the First URL. 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.055.jpeg)

**Step 39:** Navigate to the URL ![ref2]

**URL:** http://192.210.141.3/sqli\_1.php?action=search&title=ZAP'+AND+'1'%3D'1'+--+ 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.056.jpeg)

No Records will appear.  ![ref2]

**Step 40:** In the URL, change the AND condition into OR.  

**URL: [http://192.210.141.3/sqli_1.php?action=search&title=ZAP'+OR+'1'%3D'1'+--+](http://192.210.141.3/sqli_1.php?action=search&title=ZAP%27+OR+%271%27%3D%271%27+--+)** The Payload to use is also mentioned on the Vulnerablity information window (step 38). 

![](Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.057.jpeg)

All the records present in the table will be dumped on the web page.  **References:**  

1. OWASP Zed Attack Proxy (<https://www.zaproxy.org/>)  ![ref2]
1. bWAPP (<http://www.itsecgames.com/>) 

[ref1]: Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.002.png
[ref2]: Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.004.png
[ref3]: Aspose.Words.cbaf6519-e428-40a8-b313-af0820ea0196.028.png
