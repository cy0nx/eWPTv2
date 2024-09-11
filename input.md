<img src="./sjqtb0kp.png"
style="width:6.36458in;height:8.98958in" />

||
||
||
||
||

> <img src="./ax4jrzyt.png"
> style="width:8.47917in;height:1.85481in" /><img src="./vxqur3ci.png"
> style="width:7.38542in;height:3.17708in" /><img src="./lhtkazjb.png"
> style="width:8.48958in;height:0.85417in" />**Important** **Note:**
> This document illustrates all the important steps required to complete
> this lab. This is by no means a comprehensive step-by-step solution
> for this exercise. This is only provided as a reference to various
> commands needed to complete this exercise and for your further
> research on this topic. Also, note that the IP addresses and domain
> names might be different in your lab.
>
> **Q1.** **How** **many** **A** **Records** **are** **present** **for**
> **witrap.com** **and** **its** **subdomains?**
>
> **Answer:** 9
>
> **Command:** dig axfr witrap.com @192.60.177.3

<img src="./rolyuv05.png"
style="width:8.47917in;height:1.85481in" /><img src="./u3kcpcvu.png"
style="width:7.30208in;height:3.41667in" /><img src="./cx1zoa4k.png"
style="width:8.48958in;height:0.85417in" />**Q2.** **What** **is**
**the** **IP** **address** **of** **machine** **which** **support**
**ldap** **over** **TCP** **on** **witrap.com?**

**Answer:** 192.168.62.111

**Command:** dig axfr witrap.com @192.60.177.3

**Q3.** **Can** **you** **find** **the** **secret** **flag** **in**
**TXT** **record** **of** **a** **subdomain** **of** **witrap.com**
**?**

**Answer:** my_s3cr3t_fl4g

**Command:** dig axfr witrap.com @192.60.177.3

<img src="./h4jc0jx2.png"
style="width:8.47917in;height:1.85481in" /><img src="./id4zn15p.png"
style="width:7.29167in;height:3.39583in" /><img src="./vvfbura2.png"
style="width:8.48958in;height:0.85417in" />**Q4.** **What** **is**
**the** **subdomain** **for** **which** **only** **reverse** **dns**
**entry** **exists** **for** **witrap.com?** **witrap** **owns** **the**
**ip** **address** **range:** **192.168.\*.\***

**Answer:** temp.witrap.com

**Command:** dig axfr -x 192.168 @192.60.177.3

<img src="./fnpdegew.png"
style="width:8.47917in;height:1.85481in" /><img src="./42hjcfr2.png" style="width:7.23958in;height:3in" /><img src="./4vabhsj1.png"
style="width:7.35417in;height:3.05208in" /><img src="./j00t2wcb.png"
style="width:8.48958in;height:0.85417in" />**Q5.** **How** **many**
**records** **are** **present** **in** **reverse** **zone** **for**
**witrap.com** **(excluding** **SOA)?** **witrap** **owns** **the**
**ip** **address** **range:** **192.168.\*.\***

**Answer:** 12

**Command:** dig axfr -x 192.168 @192.60.177.3

<img src="./a0g0buuj.png"
style="width:8.47917in;height:1.85481in" /><img src="./s5n4bwm4.png"
style="width:8.48958in;height:0.85417in" />**References:**

> 1\. Bind 9
> ([<u>https://www.isc.org/downloads/bind/</u>](https://www.isc.org/downloads/bind/))
> 2. nslookup
> ([<u>https://linux.die.net/man/1/nslookup</u>](https://linux.die.net/man/1/nslookup))
> 3. dig
> ([<u>https://linux.die.net/man/1/dig</u>](https://linux.die.net/man/1/dig))
