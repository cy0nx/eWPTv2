![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.001.png)

![ref1]
<table><tr><th colspan="1"><b>Name</b> </th><th colspan="1">Attacking Basic Auth with Burp Suite </th></tr>
<tr><td colspan="1" rowspan="2"><b>URL</b> </td><td colspan="1" valign="bottom"><https://attackdefense.com/challengedetails?cid=1896> </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">Webapp Pentesting Basics </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

**Step 1:** Determining the IP address of the target machine. **Command:** ifconfig ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.004.jpeg)

The IP address of the host machine is 192.253.50.2 Therefore, the target machine has IP address 192.253.50.3 **Step 2:** Scan the target machine using nmap. 

**Command:** nmap 192.253.50.3 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.005.png)

We have discovered that HTTP and MYSQL services are running on the target machine. ![ref2]**Step 3:** Checking the application available on port 80 of the target machine. 

**URL:** http://192.253.50.3 


![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.006.png)

bWAPP application is hosted on the target machine. Access the /basic directory: ![ref2]

**URL:** http://192.253.50.3/basic 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.007.png)

Enter some random username - password combination. ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.008.png)

Since the credentials were incorrect, the same login prompt would appear again: 

Click on the “Cancel” button: ![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.009.jpeg)![ref2]

![ref1]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.010.jpeg)

**Step 3:** Using Burp Suite to crack the Basic Auth: 

Click on the FoxyProxy plugin icon on the top-right of the browser. ![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.011.png)

Select Burp Suite option from the list: ![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.012.png)![ref2]

Start Burp Suite: ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.013.jpeg)


![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.014.png)

Click Next ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.015.jpeg)

![ref1]

Click on Start Burp 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.016.jpeg)

Burp Suite is opened. Now, access the /basic directory again. 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.017.jpeg)

Notice that Burp window comes into focus as it has intercepted the request. ![ref2]


![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.018.png)

Notice that the Proxy button in Burp Suite lit up (orange). Click on the Proxy button 

Notice the request being made by the browser. ![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.019.jpeg)![ref2]

![ref1]

Forward the above intercepted request and switch back to the browser window: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.020.jpeg)

Notice that the application is prompting for credentials. Enter some random credentials and press Ok. 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.021.jpeg)

Intercepted request: ![ref2]


![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.022.png)

Notice the Authorization header. The “/basic” directory uses Basic Auth. Send the intercepted request to intruder. ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.023.jpeg)

![ref1]

Navigate to the Intruder tab in Burp Suite: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.024.png)

Navigate to the Positions sub-tab in the Intruder tab ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.025.jpeg)

Base64 decode the Basic Auth: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.026.jpeg)

Right click and decode the base64 encoded basic auth: ![ref2]


![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.027.png)

The credentials passed to the login prompt are shown. Replace the credentials with a parameter to be substituted: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.028.jpeg)

Click on the Add Button on the right side: ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.029.png)

Navigate to the Payloads tab and load the 100-common-passwords.txt list 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.030.png)

![ref1]

Click on the Load button to load the password list located at /root/Desktop/wordlists/100-common-passwords.txt: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.031.jpeg)

In the Payload Processing section click on the “Add” button. ![ref2]


![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.032.png)

Select “Add Prefix” 

Set the Prefix to “admin:”: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.033.png)

So, now “admin:” would be appended to each password from the list. ![ref2]

Add another Payload Processing option to encode the payload to base64: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.034.png)

Select the Encode Rule as Base64-encode Next, click on the “Start Attack” button: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.035.jpeg)

This would start the dictionary attack against the target webapp: 

![ref1]

Check the Status codes of the requests and check the payload for the request with a different status code: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.036.png)

Notice that there is one request with the status code of 301. Double click on the request entry: ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.037.jpeg)


![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.038.png)

Select the credentials in the Authorization header field and send them to the Decoder tab. 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.039.jpeg)

URL decode the credentials followed by base64-decode: ![ref2]

![ref1]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.040.jpeg)

**Username:** admin **Password:** cookie1 

Now, turn off the intercept mode in Burp Suite: ![ref2]

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.041.png)

Pass the credentials to the application: 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.042.jpeg)

Click OK 

![](Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.043.png)

The login was successful and the Flag is displayed: **Flag:** d25db4ce54b60b49dfd7b32c52ed8d26 

**References: ![ref2]**

1\. Burp Suite (<https://portswigger.net/support/burp-suite-tools>) 

[ref1]: Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.002.png
[ref2]: Aspose.Words.198a91bb-36c1-4930-8679-e7a035cf7d2d.003.png
