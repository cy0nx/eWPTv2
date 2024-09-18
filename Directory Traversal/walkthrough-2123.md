![](Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.001.png)

![ref1]
<table><tr><th colspan="1"><b>Name</b> </th><th colspan="1">Directory Traversal </th></tr>
<tr><td colspan="1" rowspan="2"><b>URL</b> </td><td colspan="1" valign="bottom"><https://www.attackdefense.com/challengedetails?cid=2123>  </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">OWASP Top 10 : Broken Access Control </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

**Objective:** Directory Traversal attack. 

**Solution:**  

**Step 1:** Start a terminal and check the IP address of the host. **Command:** ip addr 

![](Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.003.jpeg)

**Step 2:** Run Nmap scan on the target IP to find open ports. ![ref2]**Note:** The target IP will be 192.150.21.3 

**Command:** nmap 192.150.21.3 

![](Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.005.png)

Port 80 and 3306 are open 

**Step 3:** Start firefox and navigate to the target IP. 

![](Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.006.jpeg)

An instance of bWAPP is running at port 80 of the target. ![ref2]**Step 4:** Log in to the application using **bee:bug** credentials. 


![](Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.007.png)

**Step 5:** From the Choose your bug dropdown, Select “**Directory Traversal - Directories**” exercise. Click on ‘Hack’. 

![](Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.008.jpeg)

**Step 6:** Modify the directory parameter and add “../” in the URL ![ref2]

![ref1]

![](Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.009.jpeg)

Modify the directory parameter to “../etc/” to display the contents of /etc directory. 

The Directory Traversal attack was successful. ![ref2]**References:** 

1\. bWAPP (<http://www.itsecgames.com/>) 

[ref1]: Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.002.png
[ref2]: Aspose.Words.7d333c78-7c6c-4f0d-b0ad-9e934f93e1fb.004.png
