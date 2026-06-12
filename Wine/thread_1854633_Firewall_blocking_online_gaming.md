---
title: "Firewall blocking online gaming"
date: 2011-10-04
forum: Wine
---

### Post by murderd2death on 2011-10-04
I've tried installing both League of Legends and Lord of the Rings online and before the install even starts the installshield tries connecting to the internet and says that a connection was not made, and its possibly due to a firewall. I know of no firewall that i've set up that would block any signals to the gaming servers, is there anything else that is native to ubuntu (natty) that would be doing this that i can get rid of?

update:
I have firestarter installed, but i have not configured it or set it up.

this is the error message I get:
> 
"your system is currently not allowing access to our servers. Check your Firewall and/or security setting to allow PMD.exe to run/ Visit the help page or contanct us at downloader @pandonetworks.com for further assistance. would you like to retry the connection?"

---

### Post by lcman on 2011-10-06
> **murderd2death said:**
> I've tried installing both League of Legends and Lord of the Rings online and before the install even starts the installshield tries connecting to the internet and says that a connection was not made, and its possibly due to a firewall. I know of no firewall that i've set up that would block any signals to the gaming servers, is there anything else that is native to ubuntu (natty) that would be doing this that i can get rid of?

update:
I have firestarter installed, but i have not configured it or set it up.

this is the error message I get:

Ubuntu comes with preconfigured ufw firewall.
```
https://help.ubuntu.com/8.04/serverguide/C/firewall.html
```You might wanna check your router's hardware firewall as well if you have one!

---

### Post by murderd2death on 2011-10-06
> **lcman said:**
> Ubuntu comes with preconfigured ufw firewall.
```
https://help.ubuntu.com/8.04/serverguide/C/firewall.html
```You might wanna check your router's hardware firewall as well if you have one!

I checked that out and i allowed all and even disabled it to know avail. I'll check out the hardware when i get home but i never had this problem on m windows OS's.

---

### Post by proxy.qtz on 2011-10-06
Remember, Ubuntu isn't windows, so you will find things that are different. You may want to try fully disabling the firewall, just to check if that makes any difference.

---

### Post by murderd2death on 2011-10-06
> **proxy.qtz said:**
> Remember, Ubuntu isn't windows, so you will find things that are different. You may want to try fully disabling the firewall, just to check if that makes any difference.

i've tried disabling it and i get the same response.

---

