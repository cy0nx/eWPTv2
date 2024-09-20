![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.001.png)

![ref1]
<table><tr><th colspan="1"><b>Name</b> </th><th colspan="1">CVE-2015-6522 </th></tr>
<tr><td colspan="1" rowspan="2"><b>URL</b> </td><td colspan="1" valign="bottom"><https://www.attackdefense.com/challengedetails?cid=967> </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">Webapp CVEs : 2015 </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

**Solution:**  

The web application is vulnerable to CVE-2015-6522 

**Step 1:** Inspect the web application. ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.003.jpeg)![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.005.jpeg)

**Step 2:** Search on google “CVE-2015-6522 exploit”. 

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.006.jpeg)

The exploit db link contains the steps to be followed to exploit the vulnerability. ![ref2]**Exploit DB Link: <https://www.exploit-db.com/exploits/37824>** 

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.007.jpeg)

**Step 3:** Navigate to the vulnerable URL provided at exploit db. Intercept the request with burp suite. 

To configure Burp Suite check the Appendix. 

**URL: ![ref2]**http://hr18cmxzg275f61us0ypmf7y1.mumbaix.attackdefenselabs.com/wp-content/plugins/wp-sy mposium/get\_album\_item.php?size=version%28%29%20;%20-- 

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.008.jpeg)

**Step 4:** Right click and select “Send to Repeater”, navigate to repeater tab. 

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.009.jpeg)

**Step 5:** Click on the Send button. ![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.010.jpeg)

The version of mysql has been retrieved by exploiting the vulnerability. **References:**  

1. Wordpress (<http://wordpress.org/>) ![ref2]
1. WordPress Plugin WP Symposium (<http://exploit-db.com/exploits/37824http://www.wpsymposium.com/>)  
1. CVE-2015-6522 (<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-6522>)  
1. WordPress Plugin WP Symposium 15.1 - 'get\_album\_item.php' SQL Injection (<https://www.exploit-db.com/exploits/37824>)  

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

Google Chrome Settings page will appear. ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.011.jpeg)![ref2]**Step 2:** Search for “proxy” in the search box. 

**Step 3:** Upon clicking on “Open proxy settings”, Windows “Internet Properties” settings dialog box will appear. Click on “LAN settings” button. ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.012.jpeg)![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.013.png)

**Step 4:** Select the checkbox “Use a proxy server for your LAN (These settings will not apply to dial-up or VPN connections)”. And  enter “127.0.0.1” and “8080” in “Address” textbox and “Port” textbox respectively.  

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.014.png)

Click “OK” on the “Local Area Network (LAN) Settings” dialog box and close the “Internet Properties” dialog box. 

**Step 5:** Start Burp suite. 

**Step 6:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. 

All the HTTP request made by Google Chrome will be intercepted by Burp Suite.  ![ref3]![ref2]

![ref1]

**A.2 Mozilla Firefox with burp suite (Windows OS) ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.016.jpeg)![ref2]**

**Step 1:** Open Mozilla Firefox and navigate to the URL given below. **URL:** about:preferences 

**Step 2:** Scroll down to the bottom of the page and click on “Settings” button under “Network Settings” section. ![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.017.jpeg)

**Step 3:**  Enter “127.0.0.1” and “8080” in “HTTP Proxy” textbox and “Port” textbox respectively. 

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.018.jpeg)

Click on the OK button.  ![ref2]

![ref1]

**Step 4:** Start Burp suite. 

**Step 5:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref4]![ref3]

All the HTTP request made by Mozilla Firefox will be intercepted by Burp Suite.  ![ref2]
![ref1]

**Appendix B ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.020.jpeg)**

**B.1 Google Chrome with Burp Suite (Kali OS)** 

**Step 1:** Open Google Chrome and navigate to the URL given below. **URL:** chrome://settings 

Google Chrome Settings page will appear. ![ref2]**Step 2:** Search for “proxy” in the search box. 


![ref1]

**Step 3:** Upon clicking on “Open proxy settings”, The “Networks” settings window will appear. Click on Network Proxy option. ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.021.jpeg)![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.022.jpeg)

**Step 4:** Enter “127.0.0.1” in “HTTP Proxy” textbox and enter 8080 as port.  

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.023.jpeg)

Close the dialog box.  **Step 5:** Start Burp suite. 

**Step 6:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref5]![ref2]

All the HTTP/HTTPS request made by Google Chrome will be intercepted by Burp Suite.  ![ref6]![ref2]

**B.2 Mozilla Firefox with burp suite (Kali OS) ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.026.jpeg)**

**Step 1:** Open Mozilla Firefox and navigate to the URL given below. **URL:** about:preferences** 

**Step 2:** Click on “Advanced” tab on the left panel and then click on “Settings” button under “Network” tab. ![ref2]

**Step 3:**  Enter “127.0.0.1” and “8080” in “HTTP Proxy” textbox and “Port” textbox respectively. ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.027.jpeg)![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.028.jpeg)

![ref1]

**Step 4:** Start Burp suite. 

**Step 5:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref5]

All the HTTP request made by Mozilla Firefox will be intercepted by Burp Suite.  ![ref6]![ref2]
![ref1]

**Appendix C** 

**C.1 FoxyProxy on Google Chrome with Burp Suite** 

**Step 1:** Installing FoxyProxy. 

FoxyProxy Standard plugin for Google Chrome can be installed from the URL given below: 

**URL: [https://chrome.google.com/webstore/detail/foxyproxy-standard/gcknhkkoolaabfmlnjonogaaifnjlfn p?hl=en](https://chrome.google.com/webstore/detail/foxyproxy-standard/gcknhkkoolaabfmlnjonogaaifnjlfnp?hl=en)** 

After installing FoxyProxy, a small fox icon will appear on the right side of the address bar.  

**Step 2:** Click on the FoxyProxy icon and click on Options. ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.029.png)![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.030.png)


![ref1]

**Step 3:** Click on the “Add New Proxy” Button.  

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.031.jpeg)

**Step 4:** Enter “127.0.0.1” in “Host or IP Address” textbox and enter “8080” in Port textbox. ![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.032.jpeg)

Click on the Save button. ![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.033.jpeg)

The configured proxy will appear in the proxies table. 

**Step 5:** Enable the proxy. 

Click on the FoxyProxy icon and select the option “Use proxy 127.0.0.1:8080 for all URLs” 

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.034.png)

The FoxyProxy icon will change its color (In this case it is blue). ![ref2]

**Step 6:** Start Burp suite. 

**Step 7:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080”. ![ref4]

All the HTTP/HTTPS request made by Google Chrome will be intercepted by Burp Suite.  ![ref3]![ref2]


**C.2 FoxyProxy on Mozilla Firefox with Burp Suite ![ref1]**

**Step 1:** Installing FoxyProxy. 

FoxyProxy Standard plugin for Mozilla Firefox can be installed from the URL given below: **URL: <https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/>** 

After installing FoxyProxy, a small fox icon will appear on the right side of the address bar.  

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.035.png)

**Step 2:** Click on the FoxyProxy icon and click on Options. ![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.036.png)

**Step 3:** Click on the add button on the left panel ![ref1]![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.037.jpeg)

**Step 4:** Enter “127.0.0.1” in “IP Address, DNS name, server name” textbox and enter “8080” in Port textbox. ![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.038.jpeg)

Click on the Save button. ![ref2]

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.039.png)

The proxy will appear in the proxies table. **Step 5:** Enable the proxy. 

Click on the FoxyProxy icon and select the option “Use proxy 127.0.0.1:8080 for all URLs (ignore patterns)” 

![](Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.040.jpeg)

The FoxyProxy icon will change its color (In this case it is green). ![ref2]

**Step 6:** Start Burp suite. ![ref1]

**Step 7:** Navigate to “Options” tab under “Proxy” tab and verify that the “running” checkbox is selected for the interface “127.0.0.1:8080” ![ref4]

All the HTTP/HTTPS request made by Mozilla Firefox will be intercepted by Burp Suite.  ![ref3]![ref2]

[ref1]: Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.002.png
[ref2]: Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.004.png
[ref3]: Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.015.jpeg
[ref4]: Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.019.jpeg
[ref5]: Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.024.jpeg
[ref6]: Aspose.Words.b965a82c-0b64-4cc4-9024-5b5fc17cb736.025.jpeg
