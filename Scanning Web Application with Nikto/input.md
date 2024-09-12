<img src="./lxscrvbm.png"
style="width:6.36458in;height:8.98958in" />

||
||
||
||
||

> <img src="./mq2hub1p.png"
> style="width:8.47917in;height:1.85479in" /><img src="./cqybafjr.png"
> style="width:6.16667in;height:4.57292in" /><img src="./mvo4k45k.png"
> style="width:8.48958in;height:0.85417in" />**Important** **Note:**
> This document illustrates all the important steps required to complete
> this lab. This is by no means a comprehensive step-by-step solution
> for this exercise. This is only provided as a reference to various
> commands needed to complete this exercise and for your further
> research on this topic. Also, note that the IP addresses and domain
> names might be different in your lab.
>
> **Step** **1:** Determining the IP address of the target machine.
>
> **Command:** ifconfig

<img src="./homgdzfx.png"
style="width:8.47917in;height:1.85479in" /><img src="./jv55doxr.png"
style="width:5.60417in;height:2.33333in" /><img src="./evcbftwj.png"
style="width:8.48958in;height:0.85417in" />The IP address of the host
machine is 192.230.148.2

Therefore, the target machine has IP address 192.230.148.3

**Step** **2:** Scan the target machine using nmap.

**Command:** nmap 192.230.148.3

HTTP and MYSQL services are running on the target machine.

**Step** **3:** Checking the application available on port 80 of the
target machine.

Open the following URL in firefox:

**URL:** [<u>http://192.230.148.3</u>](http://192.88.244.3/)

**Note:** Make sure to supply the correct IP address

<img src="./u2rbmb00.png"
style="width:8.47917in;height:1.85479in" /><img src="./zmnllm4j.png"
style="width:8.08065in;height:4.29167in" /><img src="./miz20vow.png"
style="width:8.48958in;height:0.85417in" />Notice that OWASP Mutillidae
II is running on the target machine.

**Step** **3:** Using nikto to scan the discovered webapp.

Return back to the terminal and type nikto to view the usage help for
the tool.

**Command:** nikto

<img src="./zhhqxqau.png"
style="width:8.47917in;height:1.85479in" /><img src="./hodn3tma.png"
style="width:7.30208in;height:5.375in" /><img src="./5ce4k235.png"
style="width:8.48958in;height:0.85417in" />Notice that there are some
interesting options like **-host**, **-Tuning**, and a more elaborate
help can be displayed using the **-Help** option.

Displaying the full help text:

**Command:** nikto -Help

> <img src="./vw1uddpx.png"
> style="width:8.47917in;height:1.85479in" /><img src="./vbpxljy0.png"
> style="width:7.15625in;height:3.35417in" /><img src="./i1wb0eiz.png"
> style="width:7.34375in;height:1.33333in" /><img src="./nqotkemq.png"
> style="width:6.94792in;height:2.9375in" /><img src="./eom4xu3l.png"
> style="width:8.48958in;height:0.85417in" />...
>
> ...
>
> <img src="./igem3rgv.png"
> style="width:8.47917in;height:1.85479in" /><img src="./uc105hnv.png"
> style="width:7.36458in;height:2.41667in" /><img src="./lc0tgosh.png"
> style="width:7.40625in;height:3.03125in" /><img src="./ays2tjnv.png"
> style="width:8.48958in;height:0.85417in" />...

Scan the target using nikto:

**Command:** nikto -h http://192.230.148.3

Notice that the output indicates that:

**Target** **server:** Apache version 2.4.7 **Backend:** PHP version
5.5.9 built on Ubuntu

The interesting bits of information are highlighted in yellow.

> <img src="./kgkpigzr.png"
> style="width:8.47917in;height:1.85479in" /><img src="./je4dopt2.png"
> style="width:7.38542in;height:3.35417in" /><img src="./ofrbsd23.png"
> style="width:7.39583in;height:1.77083in" /><img src="./x00f4oo2.png"
> style="width:8.48958in;height:0.85417in" />...

Some more information in the output is highlighted.

**Step** **4:** Scanning the target application for LFI vulnerability.

Back in the webapp, copy the URL for LFI (Local File Inclusion) page.
For that, click on the left side:

“OWASP 2017” \> “A5: Broken Access Control” \> “Insecure Direct Object
References” \> “Local File Inclusion”

<img src="./0sjxshd5.png"
style="width:8.47917in;height:1.85479in" /><img src="./mijwfw2d.png"
style="width:7.38542in;height:3.35417in" /><img src="./bpdkbr5o.png"
style="width:7.375in;height:3.26606in" /><img src="./43ohywc4.png"
style="width:8.48958in;height:0.85417in" />**URL:**
[<u>http://192.230.148.3/index.php?page=arbitrary-file-inclusion.php</u>](http://192.88.244.3/index.php?page=arbitrary-file-inclusion.php)

Check for the Remote File Retrieval in verbose mode:

**Command:** nikto -h
http://192.230.148.3/index.php?page=arbitrary-file-inclusion.php -Tuning
5 -Display V

> <img src="./zaoz5vth.png"
> style="width:8.47917in;height:1.85479in" /><img src="./pnw05zl1.png"
> style="width:7.40625in;height:1.80208in" /><img src="./rrmqpodr.png"
> style="width:8.48958in;height:0.85417in" />...

All the requests with the response code 200 are listed in the verbose
mode

The highlighted line indicates that the LFI vulnerability was detected

Saving the scan result as an HTML file:

**Command:** nikto -h
http://192.230.148.3/index.php?page=arbitrary-file-inclusion.php -Tuning
5 -o nikto.html -Format htm

> ...

<img src="./x2kfrbmq.png"
style="width:8.47917in;height:1.85479in" /><img src="./4ybqwvsd.png"
style="width:7.38542in;height:1.40625in" /><img src="./1hvy4c5d.png"
style="width:5.80208in;height:1.14583in" /><img src="./gdm4x0gj.png"
style="width:8.48958in;height:0.85417in" />The scan has been completed.

Check the files in the current directory.

**Command:** ls -l

Open it using firefox:

**URL:** file:///root/nikto.html

> <img src="./co2atoll.png"
> style="width:8.47917in;height:1.85479in" /><img src="./jztkycqq.png"
> style="width:7.40625in;height:5.70833in" /><img src="./sq41uvxx.png"
> style="width:7.375in;height:3.45833in" /><img src="./sgj2crqb.png"
> style="width:8.48958in;height:0.85417in" />...

<img src="./myb0u02g.png"
style="width:8.47917in;height:1.85479in" /><img src="./1nagu1ts.png"
style="width:7.33333in;height:2.57292in" /><img src="./wxwbysq5.png" style="width:6.5in;height:2.03125in" /><img src="./eo3i5qr2.png"
style="width:8.48958in;height:0.85417in" />Click on the highlighted URL
in the above image to view the contents of the /etc/passwd file of the
target machine.

Returning back to the HTML report:

In the end, there is the section on “Host Summary” and “Scan Summary”:

Here, the stats and the CLI options used to info the tool and some other
information related to the time elapsed, etc are provided.

**References:**

> 1\. Nikto [<u>(https://cirt.net/Nikto2)</u>](https://cirt.net/Nikto2)
>
> 2\. Mutillidae II
> [<u>(https://sourceforge.net/projects/mutillidae/</u>](https://sourceforge.net/projects/mutillidae/))
