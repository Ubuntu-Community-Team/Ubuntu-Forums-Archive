---
title: "WINE install messages (winecfg)"
date: 2015-01-08
forum: Wine
---

### Post by oygle on 2015-01-08
I have installed WINE from the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=2258533&p=13197424#post13197424")

Is using the ppa 'safe', or is there a more stable release. I mention that because of [Newer versions of Wine (Not Recommended)]("https://help.ubuntu.com/community/Wine") ?

When I ran **wincfg** for the first time, these messages appeared ..

> $ winecfg
wine: created the configuration directory '/home/******/.wine'
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:iphlpapi:NotifyAddrChange (Handle 0x275e148, overlapped 0x275e160): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:iphlpapi:NotifyAddrChange (Handle 0x246e7b0, overlapped 0x246e7bc): stub
wine: configuration in '/home/*****/.wine' has been updated.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

I wanted to test running WINE for 2 Windows applications, see [here]("http://www.selectronic.com.au/sppro/splink.htm")

If I try to install one of those programs after downloading it ..

> :~/Downloads$ **wine** SP_LINK_Monitor.msi
wine: Bad EXE format for Z:\home\******\Downloads\SP_LINK_Monitor.msi.

Edit:  Found out how to run msiexec properly
> $ **wine msiexec** /i SPLINK_Monitor.msi

No error messages. But where did it install the .EXE ??

---

### Post by ajgreeny on 2015-01-08
It's a long time since I used wine for anything, but when I last did so, all installed applications were buried deep in the hidden **~/.wine** folder in my /home, and that is where I imagine they will now be on your system.

To see hidden items in the file manager hit Ctrl+H, and all those files and folders that start with a dot such as your **.wine** folder will appear.

---

### Post by oygle on 2015-01-08
Thanks for that suggestion. I always show hidden files and can see everything under ~/.wine

I have installed the latest stable release of WINE - 1.6.2 , but still am unable to 'extract' the files in the .msi file

---

### Post by oygle on 2015-01-09
Have been able to install the software using WINE from a Dolphin window. However, the Win software needs to access a USB port, and I'm _pretty_ WINE can't do that. So, no go.   :(

---

