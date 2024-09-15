![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.001.png)

![ref1]
<table><tr><th colspan="1"><b>Name</b> </th><th colspan="1">CiMe Citas Medicas </th></tr>
<tr><td colspan="1" rowspan="2"><b>URL</b> </td><td colspan="1" valign="bottom"><https://www.attackdefense.com/challengedetails?cid=476>  </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">Real World Webapps : SQL Injection </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

**Solution:**  

**Step 1:** Inspect the web application. 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.003.png)

**Step 2:** Search on google “CiMe Citas Medicas sql injection” and look for publically available exploits.**  

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.004.jpeg)

The exploit db link contains the information about the vulnerable parameter. ![ref2]**Exploit DB Link: <https://www.exploit-db.com/exploits/31350>** 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.006.jpeg)

**Step 3:** Enter any credentials in the login form, click “Entrar” and intercept the request with burp suite.  

Check Appendix to learn how to configure Burp Suite. ![ref2]

Intercepted Request:  ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.007.jpeg)![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.008.jpeg)![ref2]

Copy the request and save it in a file named “request”. **Command:** cat request 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.009.jpeg)

**Step 4:** Find the payload using sqlmap. 

**Vulnerable parameter:**  username** 

**Command:** sqlmap -r request -p username 

Enter the following answers when asked for questions. 

“y” for “Do you want to skip test payloads specific for other DBMSes?” ![ref2]

“y” for “do you want to include all tests for 'MySQL' extending provided level (1) and risk (1) values?” 

“n” for “Do you want to keep testing the others (if any)?” 


![ref1]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.010.jpeg)

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.011.jpeg)

![ref1]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.012.jpeg)

**Payload:** username=admin' AND SLEEP(5) AND 'nGdY'='nGdY&password=password **Step 5:** Send the intercepted request to Repeater. 

Right click on the intercepted request and select the option “Send to Repeater”, the same can be achieved by pressing “CTRL+R”. ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.013.jpeg)

Repeater Tab: 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.014.jpeg)

**Step 6:** Send the original request and check the response time. Request section in the Repeater tab. ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.015.jpeg)

Response section in the Repeater tab. 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.016.jpeg)

It took 267 ms to receive the response. (The time is displayed on the right bottom corner) ![ref2]

**Step 7:** Inject the time based payload in POST data and check the response time.  **Before:** username=admin&password=password 

**After:** username=admin' AND SLEEP(5) AND 'nGdY'='nGdY&password=password Request section in the Repeater tab: 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.017.jpeg)

Response section in the Repeater tab: ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.018.jpeg)

The injected time based SQLI payload was executed and the response was received with 5 second delay. ![ref2]

**Step 8:** Increase the sleep time in payload to 10 and check the response time. **Before:** username=admin' AND SLEEP(5) AND 'nGdY'='nGdY&password=password **After:** username=admin' AND SLEEP(10) AND 'nGdY'='nGdY&password=password Request section in the Repeater tab: 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.019.jpeg)

Response section in the Repeater tab: ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.020.jpeg)

The response was received with 10 second delay.  **References:**  

1. CiMe - Citas Médicas (<https://sourceforge.net/projects/cime/>) ![ref2]
1. CiMe Citas Médicas - Multiple Vulnerabilities (<https://www.exploit-db.com/exploits/31350>)  
1. Sqlmap (<http://sqlmap.org/>)  

**Appendix**

**Appendix A: Configuration for Windows OS** 

`     `A.1 Google Chrome with Burp Suite      A.2 Mozilla Firefox with Burp Suite 

**Appendix B: Configuration for Kali OS** 

`                `B.1 Google Chrome with Burp Suite 

`    `B.2 Mozilla Firefox with Burp Suite 

**Appendix C: Configuration for FoxyProxy Standard plugin ![ref2]**

`    `C.1 FoxyProxy on Google Chrome with Burp Suite 

`    `C.2 FoxyProxy on Mozilla Firefox with Burp Suite** 

**Appendix A** 

**A.1 Google Chrome with Burp Suite (Windows OS)** 

**Step 1:** Open Google Chrome and navigate to the URL given below. **URL:** chrome://settings 

Google Chrome Settings page will appear. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.021.jpeg)![ref3]**Step 2:** Search for “proxy” in the search box. 

**Step 3:** Upon clicking on “Open proxy settings”, Windows “Internet Properties” settings dialog box will appear. Click on “LAN settings” button. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.023.jpeg)![ref2]


![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.024.png)

**Step 4:** Select the checkbox “Use a proxy server for your LAN (These settings will not apply to dial-up or VPN connections)”. And  enter “127.0.0.1” and “8080” in “Address” textbox and “Port” textbox respectively.  ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.025.png)

Click “OK” on the “Local Area Network (LAN) Settings” dialog box and close the “Internet Properties” dialog box. 

**Step 5:** Start Burp suite. 

**Step 6:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref4]![ref2]

![ref1]

All the HTTP request made by Google Chrome will be intercepted by Burp Suite.  ![ref5]

**A.2 Mozilla Firefox with burp suite (Windows OS) ![ref2]**

**Step 1:** Open Mozilla Firefox and navigate to the URL given below. 

**URL:** about:preferences ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.028.jpeg)

**Step 2:** Scroll down to the bottom of the page and click on “Settings” button under “Network Settings” section. ![ref2]


![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.029.png)

**Step 3:**  Enter “127.0.0.1” and “8080” in “HTTP Proxy” textbox and “Port” textbox respectively. ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.030.png)

Click on the OK button.  ![ref2]**Step 4:** Start Burp suite. 

![ref1]

**Step 5:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref4]

All the HTTP request made by Mozilla Firefox will be intercepted by Burp Suite.  ![ref5]![ref2]


**Appendix B ![ref1]![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.031.jpeg)**

**B.1 Google Chrome with Burp Suite (Kali OS)** 

**Step 1:** Open Google Chrome and navigate to the URL given below. **URL:** chrome://settings 

Google Chrome Settings page will appear. ![ref2]**Step 2:** Search for “proxy” in the search box. 

![ref1]

**Step 3:** Upon clicking on “Open proxy settings”, The “Networks” settings window will appear. Click on Network Proxy option. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.032.jpeg)![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.033.jpeg)


**Step 4:** Enter “127.0.0.1” in “HTTP Proxy” textbox and enter 8080 as port.  ![ref1]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.034.jpeg)

Close the dialog box.  **Step 5:** Start Burp suite. 

**Step 6:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref6]![ref2]

![ref1]

All the HTTP/HTTPS request made by Google Chrome will be intercepted by Burp Suite.  ![ref7]![ref2]


**B.2 Mozilla Firefox with burp suite (Kali OS) ![ref1]![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.037.jpeg)**

**Step 1:** Open Mozilla Firefox and navigate to the URL given below. **URL:** about:preferences** 

**Step 2:** Click on “Advanced” tab on the left panel and then click on “Settings” button under “Network” tab. ![ref2]

![ref1]

**Step 3:**  Enter “127.0.0.1” and “8080” in “HTTP Proxy” textbox and “Port” textbox respectively. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.038.jpeg)![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.039.jpeg)

**Step 4:** Start Burp suite. 

**Step 5:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref6]

All the HTTP request made by Mozilla Firefox will be intercepted by Burp Suite.  ![ref7]![ref2]

**Appendix C** 

**C.1 FoxyProxy on Google Chrome with Burp Suite** 

**Step 1:** Installing FoxyProxy. 

FoxyProxy Standard plugin for Google Chrome can be installed from the URL given below: 

**URL: [https://chrome.google.com/webstore/detail/foxyproxy-standard/gcknhkkoolaabfmlnjonogaaifnjlfn p?hl=en](https://chrome.google.com/webstore/detail/foxyproxy-standard/gcknhkkoolaabfmlnjonogaaifnjlfnp?hl=en)** 

After installing FoxyProxy, a small fox icon will appear on the right side of the address bar.  

**Step 2:** Click on the FoxyProxy icon and click on Options. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.040.png)![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.041.png)

**Step 3:** Click on the “Add New Proxy” Button.  

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.042.jpeg)

**Step 4:** Enter “127.0.0.1” in “Host or IP Address” textbox and enter “8080” in Port textbox. ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.043.jpeg)

Click on the Save button. ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.044.jpeg)

The configured proxy will appear in the proxies table. 

**Step 5:** Enable the proxy. 

Click on the FoxyProxy icon and select the option “Use proxy 127.0.0.1:8080 for all URLs” 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.045.png)

The FoxyProxy icon will change its color (In this case it is blue). ![ref2]

**Step 6:** Start Burp suite. 

**Step 7:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.046.jpeg)

All the HTTP/HTTPS request made by Google Chrome will be intercepted by Burp Suite.  ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.047.jpeg)![ref2]

**C.2 FoxyProxy on Mozilla Firefox with Burp Suite** 

**Step 1:** Installing FoxyProxy. 

FoxyProxy Standard plugin for Mozilla Firefox can be installed from the URL given below: **URL: <https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/>** 

After installing FoxyProxy, a small fox icon will appear on the right side of the address bar.  

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.048.png)

**Step 2:** Click on the FoxyProxy icon and click on Options. ![ref2]

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.049.png)

**Step 3:** Click on the add button on the left panel ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.050.jpeg)

**Step 4:** Enter “127.0.0.1” in “IP Address, DNS name, server name” textbox and enter “8080” in Port textbox. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.051.jpeg)

Click on the Save button. ![ref2]

The proxy will appear in the proxies table. ![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.052.jpeg)**Step 5:** Enable the proxy. 

Click on the FoxyProxy icon and select the option “Use proxy 127.0.0.1:8080 for all URLs (ignore patterns)” 

![](Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.053.jpeg)

The FoxyProxy icon will change its color (In this case it is green). ![ref2]

**Step 6:** Start Burp suite. 

**Step 7:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080” ![ref4]

All the HTTP/HTTPS request made by Mozilla Firefox will be intercepted by Burp Suite.  ![ref5]![ref2]

[ref1]: Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.002.png
[ref2]: Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.005.png
[ref3]: Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.022.png
[ref4]: Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.026.jpeg
[ref5]: Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.027.jpeg
[ref6]: Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.035.jpeg
[ref7]: Aspose.Words.80e94011-2a8e-41f1-804c-81597aa0a459.036.jpeg
