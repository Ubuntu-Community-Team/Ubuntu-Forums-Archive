---
title: "Problem installing Windows XP on VMware Server"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by OsakaWilson on 2007-06-01
I successfully installed VMware Server on Feisty 64bit. I want to install Windows XP, but when I start up the virtual machine, I get the following message:

The master boot record (MBR) of this virtual machine's hard disk does not contain valid bootstrap code. It is likely that the MBR was corrupted by an incorrect guest operating system installation or some other reason.  The virtual machine cannot continue and will now power off. (For advanced users: the MBR is the last disk sector accessed by the virtual machine before the error.) Please consult our Web site at "http://www.vmware.com/info?id=18" for common troubleshooting help.

I went to the url in the message, but that page is no longer there. Does anyone know what I can do about  this?

---

### Post by dmfield on 2007-06-08
When you created the XP Virtual Machine, how did you do it? did you pre allocate the space? I had a similar problem when i created a Windows XP VM and didn't preallocate the space. 

If you delete the Virtual machine (not VM Ware) and recreate it does the same problem happen?

Just as a tip as well, if you have the space, create an ISO of the WinXP CD and have VMware boot from the ISO rather than the CD.. its a little quicker.

---

### Post by awilki01 on 2008-06-07
I get a fatal error when installing Windows XP in VMWare on Gutsy 7.10.  The Windows XP installation goes fine for some time - everything seems normal.  Then, after a few minutes, the XP installation pops up with a fatal error.  

The fatal error details start out with:

```

Error:
SXS.DLL: Syntax error in manifest or policy file "D:\I386\asms\10100\MSFT
\WINDOWS\GDIPLUS\GDIPLUS.MAN" on line 4.

***

Error:
Installation Failed: D:\I386\asms. Error Message: The device is not ready.

***

Fatal Error:
One of the components that Windows needs to continue setup could not be installed.

The device is not ready.

```

Any ideas?

---

### Post by awilki01 on 2008-06-08
Figured it out doing some Google'ing.  It was just a corrupted file.  I put another XP CD in there and it worked fine.

Thanks for the assistance!

---

