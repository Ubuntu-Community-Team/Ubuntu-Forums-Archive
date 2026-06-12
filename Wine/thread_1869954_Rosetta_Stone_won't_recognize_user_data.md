---
title: "Rosetta Stone won't recognize user data"
date: 2011-10-26
forum: Wine
---

### Post by Tk007LwZFJW5ej on 2011-10-26
I have wine 1.3.15 and RS 3.4.7. I just updated to this version of wine,  and it broke RS, so I deleted the prefix and reinstalled. I saved the  tracking.db3 file from my previous installation, and copied it into the  appropriate folder after I reinstalled, but RS is not recognizing any of  my previous settings. It keeps asking me to create a new user. The  program seems to work fine otherwise. This is the terminal output when I  run it:

```

err:menubuilder:init_xdg error looking up the desktop directory
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
fixme:win:EnumDisplayDevicesW ((null),0,0x32f740,0x00000000), stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW  L"C:\\Program Files\\Common Files\\Macrovision Shared\\FLEXnet  Publisher\\\\fnp_registrations.xml" 1 4 (nil) (nil) 0x3583640 (nil)
fixme:psapi:EnumDeviceDrivers ((nil), 0, 0x32cdcc): stub
fixme:psapi:EnumDeviceDrivers (0xab0fcc0, 0, 0x32cdcc): stub
fixme:psapi:EnumDeviceDrivers ((nil), 0, 0x32cb70): stub
fixme:psapi:EnumDeviceDrivers (0xab0df28, 0, 0x32cb70): stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c10
fixme:wbemprox:wbem_locator_ConnectServer  0x1a4b88, L"root\\cimv2", (null), (null), (null), 0x00000000, (null),  (nil), 0xb21e9a4)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer  0x1a4ec0, L"root\\cimv2", (null), (null), (null), 0x00000000, (null),  (nil), 0xb31e974)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:urlmon:InternetBindInfo_GetBindString not supported string type 12
fixme:wininet:InternetLockRequestFile STUB
fixme:urlmon:InternetBindInfo_GetBindString not supported string type 12
fixme:wininet:InternetLockRequestFile STUB


C:\Program Files\Rosetta Stone\Rosetta Stone Version 3\support\bin\win\\RosettaStoneLtdServices.exe [v072420082200] 

fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR

```

---

