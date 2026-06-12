---
title: "Networked Printer Partially Works"
date: 2009-06-05
forum: x86 64-bit Users
---

### Post by Steve R. on 2009-06-05
Since originally posting, I was basically able to solve the problem of printing from a VISTA64 laptop to a Canon PIXMA printer attached to a UBUNTU desktop by changing the string "*guest ok = no*" to "*guest ok = yes*" in the SAMBA sections [print$] and [pinters].

While the print job is now successful, I still get the error message: "access denied, unable to connect".  Is there a way to eliminate this error message? 

Below is the "old" post, consider it **deleted**.
> We have a Canon PIXMA iP5000 hooked up to a computer running UBUNTU 9.04. The printer prints from the UBUNTU computer. We can also print over the home LAN from a WindowsXP computer.  

We now have a laptop that is using VISTA64, it "*sees*" the available printer and it will print over the LAN from Open Office.  However, it will NOT print other print jobs (such as a webpage under Chrome).  We also get an error message" Access Denied, Unable to Connect".

The UBUNTU computer that the printer is connected to, is set to share.  Clearly we can share since some print jobs do go through.

Any idea of where the hang-up could be occurring?

---

