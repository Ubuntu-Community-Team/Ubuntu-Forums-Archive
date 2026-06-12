---
title: "Photoshop CS2 user privileges error"
date: 2008-05-06
forum: Wine
---

### Post by Scooter7 on 2008-05-06
Hi,

I installed Photoshop CS2 in wine earlier today, and I've been using it fine.   But I started it again to do some more graphics work a few minutes ago, and I got this error:

> Adobe Activation: You are not allowed to continue because your account does not have the proper privileges.

This is odd, because I've already activated, and it was working fine for me all day.   I'm thinking this might have something to do with the fact that I had just installed Dreamweaver 8 before opening PS, but I don't see how this could be the case.   All I can find on the error talks about Vista security, and obviously that won't help me.

Any suggestions?

---

### Post by Scooter7 on 2008-05-07
*bump*

I've discovered that I only get the error if I'm running Dreamweaver before I start Photoshop.   After I open Dreamweaver, I'll keep getting the error in Photoshop until I restart my computer.   This is really annoying... does anyone know of a possible solution?

Edit: I managed to get Photoshop running from the command line, but after I tried it again just to be sure it was working, I got the error again.   Here is the output:

```
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
err:ole:create_server class {a1f4e726-8cf1-11d1-bf92-0060081ed811} not registered
err:ole:CoGetClassObject no class object {a1f4e726-8cf1-11d1-bf92-0060081ed811} could be created for context 0x4
fixme:keyboard:UnregisterHotKey (0x10026,99): stub
fixme:keyboard:RegisterHotKey (0x10026,99,0x00000000,27): stub
fixme:font:WineEngRemoveFontResourceEx :stub
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:ole:CoResumeClassObjects stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data\\Adobe\\Updater\\AdobeESDGlobalApps.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data\\Adobe\\Updater\\AdobeESDGlobalApps.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data\\Adobe\\Updater\\AdobeESDGlobalApps.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data\\Adobe\\Updater\\AdobeESDGlobalApps.xml" 1 4 (nil) (nil) (nil) (nil)
err:ntdll:RtlpWaitForCriticalSection section 0x1502750 "?" wait timed out in thread 0054, blocked by 0009, retrying (60 sec)
fixme:ole:CoSuspendClassObjects 
fixme:font:WineEngRemoveFontResourceEx :stub

```

That's from the first time I ran it in the terminal, without the error.

The second time (with error):

```
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
err:ole:create_server class {a1f4e726-8cf1-11d1-bf92-0060081ed811} not registered
err:ole:CoGetClassObject no class object {a1f4e726-8cf1-11d1-bf92-0060081ed811} could be created for context 0x4
fixme:keyboard:UnregisterHotKey (0x4003c,99): stub
fixme:keyboard:RegisterHotKey (0x4003c,99,0x00000000,27): stub
fixme:font:WineEngRemoveFontResourceEx :stub
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:ole:CoResumeClassObjects stub
err:ntdll:RtlpWaitForCriticalSection section 0x1502750 "?" wait timed out in thread 0045, blocked by 004b, retrying (60 sec)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data\\Adobe\\Updater\\AdobeESDGlobalApps.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:ole:CoSuspendClassObjects 
fixme:font:WineEngRemoveFontResourceEx :stub
[email]vertimyst@shadowgate-lt1:~/.wine[/email]/drive_c/Program Files/Adobe/Adobe Photoshop CS2$ fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
```

---

### Post by WiseTroll on 2008-06-19
I solved this installing DCOM 98 and Visual C++ runtime libraries from wine-doors.

---

### Post by Luinfana on 2010-01-20
> **WiseTroll said:**
> I solved this installing DCOM 98 and Visual C++ runtime libraries from wine-doors.

EXCELLENT! Thank you for this - this solved it for me too.

For anyone looking to install wine-doors, at least on Karmic, it's not very straightforward so I figured I'd share how I did it. Use the .tar.gz from [here]("http://wddb.wine-doors.org/downloads") rather than the .deb (which conflicts with the renaming of the new "wine" packages to "wine1.2"). Extract the package, cd into it, and run

```
python setup.py install
```

You will probably also need to install the "orange" package - it was the only requisite one that didn't come with Ubuntu.

After that, just run Wine-Doors from the Wine menu, and search for DCOM 98 and the Visual C++ runtime libraries. They may take some time to install and the app may look frozen, but they will work.

---

