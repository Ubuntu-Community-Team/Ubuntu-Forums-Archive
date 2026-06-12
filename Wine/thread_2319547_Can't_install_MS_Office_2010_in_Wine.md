---
title: "Can't install MS Office 2010 in Wine"
date: 2016-04-05
forum: Wine
---

### Post by GeneralFailer on 2016-04-05
I'm trying to install Russian MS Office 2010 Pro Plus to a clean Wine prefix on 15.10 and consistently get an error message about corrupted or missing files almost immediately. Here's the console output:
```
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:storage:create_storagefile Storage share mode not implemented.
err:secur32:SECUR32_initSchannelSP TLS library not found, SSL connections will fail
fixme:iphlpapi:NotifyAddrChange (Handle 0x10ee8b0, overlapped 0x10ee8bc): stub
wine: configuration in '/home/nastya/.wine' has been updated.
err:secur32:SECUR32_initSchannelSP TLS library not found, SSL connections will fail
fixme:advapi:RegisterTraceGuidsA (0x2e034e56, 0x2e0b3d78, {8736922d-e8b2-47eb-8564-23e77e728cf3}, 1, 0x33fcf8, (null), (null), 0x2e0b3d78,): stub
fixme:process:GetSystemDEPPolicy stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:advapi:RegisterTraceGuidsA (0x101f577c, 0x103a5908, {8736922d-e8b2-47eb-8564-23e77e728cf3}, 1, 0x33ee34, (null), (null), 0x103a5908,): stub
fixme:system:SetProcessDPIAware stub!
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:richedit:REExtendedRegisterClass semi stub
fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
err:msxml:doparse Opening and ending tag mismatch: Setting line 29 and Configuration
err:msxml:doparse Premature end of data in tag PIDKEY line 27
err:msxml:doparse Premature end of data in tag Configuration line 25
err:msxml:doparse Premature end of data in tag Configuration line 1
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
err:msxml:doparse Document is empty
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
err:msxml:doparse Document is empty
fixme:ole:NdrCorrelationInitialize (0x33cef0, 0x33cfcc, 1024, 0x0): stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
```

---

### Post by Bucky Ball on 2016-04-05
*Thread moved to **Wine**.*

---

### Post by QDR06VV9 on 2016-04-05
I always run a VM with windows for such needs.. but see if this gets you what you need
[http://www.liberiangeek.net/2012/06/how-to-install-microsoft-office-suite-2010-in-ubuntu-12-04-using-wine-1-5/](http://www.liberiangeek.net/2012/06/how-to-install-microsoft-office-suite-2010-in-ubuntu-12-04-using-wine-1-5/)
Good Luck.
Edit: To be sure... please read the whole page and comments.
Kind Regards

---

### Post by GeneralFailer on 2016-04-05
I guess I'll have to use the WIne PPA. This is kinda frustrating considering it installed fine in Arch pretty much out of the box.
[http://ubuntuforums.org/showthread.php?t=2292761](http://ubuntuforums.org/showthread.php?t=2292761)
[https://askubuntu.com/questions/674692/installing-office-2010-on-ubuntu-15-04-using-wine](https://askubuntu.com/questions/674692/installing-office-2010-on-ubuntu-15-04-using-wine)

---

### Post by GeneralFailer on 2016-04-06
So the PPA version also doesn't work even though winetricks stopped asking for Mono now. I've used the guide from AskUbuntu mentioned above.

EDIT: The system is 64-bit, by the way.

---

### Post by mastablasta on 2016-04-07
odd. 2010 should install fine.

is office 32 bit? I guess that wineprefix is set for 32 bit?!

I used playonlinux to install it to my dad's PC on 14.04.

---

### Post by GeneralFailer on 2016-04-07
OK, so nevermind. Something seems to have gone wrong when unpacking the disk image (I know that this tends to be not recommended).

EDIT: And thanks for the help.

---

