---
title: "Iburst modem not working in karmic"
date: 2009-12-12
forum: Za Team - South Africa
---

### Post by Axel777 on 2009-12-12
Good day people,
I have a friend who have a USB iburst modem that worked great under Jaunty. He upgraded to 9.10 and he cannot seem to get it working with the same driver. Have anyone got an iburts USB modem working under 9.10? 
Thanks in advance.

---

### Post by Junkieman on 2009-12-13
Hi there! 

No I haven't tried iburst specifically, but AFAIK that is just the service name. What you need to do is [look on the modem]("http://www.iburst.co.za/default.aspx?link=hardware_modems") for make/model info on the device.

This will help us find any issues with that particular hardware for Karmic :)

Connect the modem wait for it to settle and run this command in a terminal to see the log messages, and post the output here:

```
dmesg | tail
```

---

### Post by Quint_ishbuntu on 2010-02-09
iburst modem is it only usb or ethernet aswell if it is usb only google ibdriver if it is both then update the packages well the package update worked on my netbook remix version

---

### Post by Zadeet on 2010-06-11
Hi there!!

See this topic has been quiet for a while, but if u havnt yet come right, what about using an ethernet connection from iburst terminal direct to the nic on your computer?

Just set up a new connection in Gnome network manager using PPPOE as connection type and specify your iburst username (user@iburst.co.za) and password and you should be set.

I can give you some screenshots of the setup process if needed. This method has worked for me before and as far back as ubuntu 8.04 - not only with iburst but with an ADSL modem as well. It also seems to be more reliable then usb connection..

Just my two cents worth. Hope it might help..

Craig..

---

### Post by laylow45 on 2010-09-14
> **Zadeet said:**
> Hi there!!
 
See this topic has been quiet for a while, but if u havnt yet come right, what about using an ethernet connection from iburst terminal direct to the nic on your computer?
 
Just set up a new connection in Gnome network manager using PPPOE as connection type and specify your iburst username (user@iburst.co.za) and password and you should be set.
 
I can give you some screenshots of the setup process if needed.  
Just my two cents worth. Hope it might help..
 
Craig..
 
Hi Craig
 
Can u help with the screenshots of the setup process? I am on Karmic UE 2.5 64 bit, need to get the iBurst USB going. Assistance will be appreciated.
 
Johan

---

