---
title: "Cannot access Internet with 9.10"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by sdpiowa on 2009-10-30
After I installed Ubuntu 9.10, I cannot really access the Internet.  Firefox just spins and never really loads the page.  The "Update Manager" found updates the first time, but cannot connect anymore.  I haven't had any problems like this with 9.04, and did a clean install for 9.10.  I have reinstalled 9.10 once, and this didn't fix the problem.  The software center isn't showing the 'download' button because it cannot connect.

Any ideas?


Oh, sometimes Firefox will pull up a frame of a website, but not any images.

---

### Post by sadahalli on 2009-10-30
Do you check your network connection??. (I am sure you did ). Try installing another browser..

---

### Post by KinKiac on 2009-10-30
Sounds like your network manager is not configured properly.

---

### Post by sdpiowa on 2009-10-30
The network connection is fine (I have at least 4 other computers connected).  I can't install another browser because it can't access the internet.

I just reloaded the OS again, so we'll see how that goes.


Oh, and it STARTS connecting (like when I typed 'gmail.com', the status bar started loading 'mail.google.com'), but that's about it.

---

### Post by sdpiowa on 2009-10-30
Some additional information:
I can ping internet domains successfully, and the built-in WHOIS check works.

---

### Post by sdpiowa on 2009-10-30
PROBLEM FIXED:
I had to manually edit the DNS servers to get the internet working.  I left DHCP turned on, but manually added our DNS server.

Thanks for the help!

---

### Post by lindude on 2009-10-31
[QUOTE=sdpiowa;8202184]PROBLEM FIXED:
I had to manually edit the DNS servers to get the internet working.  I left DHCP turned on, but manually added our DNS server.

I have the same problem, how did you manually edit DNS?

I also can't access the propriety drivers. they show up on when using the live CD but after install it just blank doesn't search for them and no list.
I've reinstalled 3 times but the same problems keep appearing.
Thanks

---

### Post by sdpiowa on 2009-10-31
Open "Network Connections" under "System>>Preferences" and double-click the "Auto eth0" connection.  Go to the "IPv4" tab and change it from "DHCP" to "Automatic (DHCP) addresses only".  Add the following IP address to your domain servers box: 208.67.222.222 (that's the IP address for OpenDNS, by the way).

Try that, that should work.

---

### Post by sdpiowa on 2009-10-31
> **lindude said:**
> 
I also can't access the propriety drivers. they show up on when using the live CD but after install it just blank doesn't search for them and no list.
I've reinstalled 3 times but the same problems keep appearing.
Thanks

What are you trying to install proprietary drivers for?

---

