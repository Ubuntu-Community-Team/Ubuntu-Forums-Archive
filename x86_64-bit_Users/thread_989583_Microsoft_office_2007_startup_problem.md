---
title: "Microsoft office 2007 startup problem"
date: 2008-11-21
forum: x86 64-bit Users
---

### Post by pspmasterpro on 2008-11-21
I'm using the 64-bit version of Ubuntu 8.04 and I'm using wine version 1.1.9 to run Microsoft office 2007. I managed to install it with this guide:
[http://anotherubuntu.blogspot.com/2008/05/microsoft-office-2007-on-ubuntu.html](http://anotherubuntu.blogspot.com/2008/05/microsoft-office-2007-on-ubuntu.html)

```


   1. Install Wine - sudo apt-get install wine
   2. Follow the instructions here, I suggest making the permanent file change as else you'll have to run it after every reboot
   3. At the terminal run winecfg and change the under libraries change rpcrt4.dll and msxml3.dll to Windows native.
   4. Go to /home/username/.wine/drive_c/windows/system32 and delete the two dll's above
   5. Add this dll to the folder above
   6. Get this text, save it to a file locally and run the file by sh filename
   7. When this runs, select the 3 msxml options and let the installs for these run
   8. Now run setup.exe from your Office 2007 installation disk
   9. Following this, run the winetricks script from before again and run dotnet2
  10. All being well, success!

```

But for step 9 I couldn't find dotnet2 I only found dotnet11 and dotnet20 so I installed them both and then when I load MS word 07 is gives me and error on boot it says:

Microsoft Office Word has encountered a problem and needs to close. We are sorry for the inconvenience. and then if gives to options Debug and close. any help here?

EDIT: O.K. I ran it using the terminal and it gives me this:
```

psplegendpro@psplegendpro-desktop:~$ wine .wine/drive_c/Program\ Files/Microsoft\ Office/Office12/WINWORD.EXE
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:CheckTokenMembership ((nil) 0x13bbf8 0x32e918) stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x32f2ac,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x146cf0,(nil)): stub
err:eventlog:ReportEventW L"Microsoft Office Word"
err:eventlog:ReportEventW L"Word failed to start correctly last time.  Starting Word in safe mode will help you correct or isolate a startup problem in order to successfully start the program.  Some functionality may be disabled in this mode.\n\nDo you want to start Word in safe mode?"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x00001b5b,(nil),0x0004,0x00000000,0x32ee58,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:ole:marshal_object object doesn't expose interface {e19c7100-9709-4db7-9373-e7b518b47086}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:NdrCorrelationInitialize (0x7dc2b7f0, 0x7dc2b3f0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:system:SetProcessDPIAware stub!
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:msxml:DllCanUnloadNow 
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:ole:NdrCorrelationFree (0x7dc2b7f0): stub
fixme:msi:MsiReinstallFeatureW L"{90120000-0030-0000-0000-0000000FF1CE}" L"WORDFiles" 128
fixme:advapi:LookupAccountNameW (null) L"psplegendpro" (nil) 0x32dec0 (nil) 0x32dec4 0x32deb8 - stub
fixme:advapi:LookupAccountNameW (null) L"psplegendpro" 0x179438 0x32dec0 0x1795d8 0x32dec4 0x32deb8 - stub
fixme:reg:GetNativeSystemInfo (0x33f0b4) using GetSystemInfo()
fixme:powrprof:DllMain (0x7d480000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33f0dc 0x33f0d0
fixme:advapi:CheckTokenMembership ((nil) 0x195838 0x33f0b8) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x195838 0x33f0b8) stub!
fixme:powrprof:DllMain (0x7d480000, 0, (nil)) not fully implemented
fixme:msxml:DllCanUnloadNow 

```

---

### Post by inobe on 2008-11-21
crossover pro will run that.

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

---

