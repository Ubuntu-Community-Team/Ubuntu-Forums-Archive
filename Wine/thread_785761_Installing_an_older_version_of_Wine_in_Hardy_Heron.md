---
title: "Installing an older version of Wine in Hardy Heron"
date: 2008-05-07
forum: Wine
---

### Post by seuzy13 on 2008-05-07
I am trying to get Photoshop Elements 6.0 to work in wine. I read in the wine app database that older versions of wine work better. I have witnessed this myself. I first installed it on Gutsy with I think it was the second latest version of wine. Install went smoothly, but I had a problem at the registration window as described in the app database, and never got it to work. When I upgraded wine to the latest version and also upgraded to Hardy Heron, it did not work at all (no registration window). Should I try a clean install? Downgrade wine? 

I ask about downgrading wine specifically, because I found the wine packages [here]("http://wine.budgetdedicated.com/archive/index.html"), and only two were listed under Hardy Heron. Does this mean that the others do not work? 

Thanks.

This is the error I get when I run it from the terminal.

root@Larry:/home/username# wine "C:\Program Files\Adobe\Photoshop Elements 6.0\Photoshop Elements 6.0.exe"
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x15580c 0x155818 0x1558f8 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x15580c 0x155818 0x1558f8 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x15580c 0x155818 0x1558f8 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x14ba8c 0x14ba98 0x155b30 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x15580c 0x155818 0x155b30 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x15580c 0x155818 0x155b30 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x15580c 0x155818 0x155b30 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dba1a08, overlapped 0x7dba19ec): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data\\Adobe\\Updater5" 1 4 (nil) (nil) 0x135ae0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data\\Adobe\\Updater5\\AdobeESDGlobalApps.xml" 1 4 (nil) (nil) 0x135ae0 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x135a0c 0x135a18 0x135a60 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x135a0c 0x135a18 0x135a60 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x135a0c 0x135a18 0x135a60 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x135a0c 0x135a18 0x135a60 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\root\\Local Settings\\Application Data\\Adobe\\Updater5\\AUTrans.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\root\\Local Settings\\Application Data\\Adobe\\Updater5\\AUTrans.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\root\\Local Settings\\Application Data\\Adobe\\Updater5\\AUTrans.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:systray:wine_notify_icon unhandled tray message: 3
fixme:systray:handle_incoming unhandled tray message: 3
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\root\\Local Settings\\Application Data\\Adobe\\Updater5\\AUTrans.xml" 1 4 (nil) (nil) (nil) (nil)
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  61 (X_ClearArea)
  Resource id in failed request:  0x4200006
  Serial number of failed request:  618
  Current serial number in output stream:  626
fixme:shell:DllCanUnloadNow stub

---

### Post by shae on 2008-05-09
That does not mean that they do not work.  It is just that those older versions were not build for hardy so the packages will not work in hardy.  You can however grab and older source package and build it yourself.

---

### Post by logos34 on 2008-05-09
> **shae said:**
> That does not mean that they do not work.  It is just that those older versions were not build for hardy so the packages will not work in hardy.  You can however grab and older source package and build it yourself.

Well, that's funny, I'm using Wine version .47 (Gutsy) on my Hardy install.  

I had to downgrade because the newer versions of Wine refuse to correctly detect my cdrom drive. 

Works fine now.

---

