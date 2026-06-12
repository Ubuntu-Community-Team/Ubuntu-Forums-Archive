---
title: "Microsoft Office 2007 on Linux with Wine"
date: 2007-12-17
forum: Wine
---

### Post by twickline on 2007-12-17
Microsoft Office 2007 on Linux with Wine

full[ article here with screenshots]("http://wine-review.blogspot.com/2007/12/microsoft-office-2007-on-linux-with.html")

---

### Post by sethfc on 2007-12-30
is there a "how-to" yet?!

---

### Post by etful on 2009-02-20
hi guys, i just got it wrong cause when i moved rpcrt4 to system32 i deleted the old version and put the new with no backup. How can i restore the old one?
thanks!!!

---

### Post by drummer42 on 2009-03-17
Hey there! I got Office 2007 (ALL PROGRAMS) to install and run in Ubuntu!! I wrote up a quick tutorial here:

[http://programmerfish.com/roffice-2007-in-linux](http://programmerfish.com/roffice-2007-in-linux)

It's quick, easy, and, best of all, IT WORKS!!!!!!!

---

### Post by illmatic on 2009-03-17
you don't need winetricks, you just need the latest wine release to install
and afterwords you need to change 2 things in the winecfg that's all

---

### Post by citybird on 2009-03-19
Hello all. I am following the instructions from here:
[http://www.programmerfish.com/roffice-2007-in-linux](http://www.programmerfish.com/roffice-2007-in-linux)

and I am running into an error when running wine setup.exe

as a normal user i got:```

fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0×2a496c4): stub
fixme:sfc:SFC_3 0
err:ole:create_server class {000c101c-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {000c101c-0000-0000-c000-000000000046} could be created for context 0×4
fixme:advapi:RegisterEventSourceA ((null),”MsiInstaller”): stub
fixme:advapi:RegisterEventSourceW (L”",L”MsiInstaller”): stub
fixme:advapi:ReportEventA (0xcafe4242,0×0002,0×0000,0×000003f7,(nil),0×0006,0×00000000,0×2b7c6e8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0×0002,0×0000,0×000003f7,(nil),0×0006,0×00000000,0×229d410,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:NdrCorrelationInitialize (0×2a4d44c, 0×2a4d04c, 1024, 0×0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:advapi:CheckTokenMembership (0xac 0×21fad0 0×9be5d0) stub!
fixme:ole:NdrCorrelationFree (0×2a4d44c): stub
fixme:ole:NdrCorrelationInitialize (0×2a4d40c, 0×2a4d00c, 1024, 0×0): stub
err:rpc:I_RpcReceive we got fault packet with status 0×1c010003
fixme:ole:NdrCorrelationInitialize (0×2a4d3ac, 0×2a4cfac, 1024, 0×0): stub
fixme:ole:NdrCorrelationInitialize (0×2a4d38c, 0×2a4cf8c, 1024, 0×0): stub
err:rpc:RpcAssoc_BindConnection rejected bind for reason 0
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
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
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:powrprof:DllMain (0×7de60000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0×32f0dc 0×32f0d0
fixme:advapi:CheckTokenMembership ((nil) 0×19de98 0×32f0b8) stub!
fixme:advapi:CheckTokenMembership ((nil) 0×19de98 0×32f0b8) stub!
fixme:powrprof:DllMain (0×7de60000, 0, (nil)) not fully implemented
```

When installing as root user I got:
```
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msi:ACTION_CallDllFunction Custom action (L"C:\\windows\\temp\\msi1bbe.tmp":L"OfficeDataLockPermissions") caused a page fault: c0000005
err:ntdll:RtlpWaitForCriticalSection section 0x7e606b78 "handle.c: MSI_object_cs" wait timed out in thread 0024, blocked by 00bd, retrying (60 sec)
wine: Critical section 7e606b78 wait failed at address 0x7bc3c090 (thread 0024), starting debugger...
Unhandled exception: wait failed on critical section 0x7e606b78
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3c090
root@bearing:/home/citybird/Desktop/Office2007pro_eng# Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000c 
	0000001f    0
	0000000e    0
	0000000d    0
0000000f 
	00000010    0
0000001c 
	00000022    0
	00000021    0
	0000001e    0
	0000001d    0
0000002a 
	00000032    0
	00000031    0
	0000002c    0
	0000002b    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
```

illmatic: can you please explain what 2 things you need to change in the winecfg???

Thanks in advance.

---

### Post by illmatic on 2009-03-19
> **citybird said:**
> Hello all. I am following the instructions from here:
[http://www.programmerfish.com/roffice-2007-in-linux](http://www.programmerfish.com/roffice-2007-in-linux)

and I am running into an error when running wine setup.exe

as a normal user i got:```

fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0×2a496c4): stub
fixme:sfc:SFC_3 0
err:ole:create_server class {000c101c-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {000c101c-0000-0000-c000-000000000046} could be created for context 0×4
fixme:advapi:RegisterEventSourceA ((null),”MsiInstaller”): stub
fixme:advapi:RegisterEventSourceW (L”",L”MsiInstaller”): stub
fixme:advapi:ReportEventA (0xcafe4242,0×0002,0×0000,0×000003f7,(nil),0×0006,0×00000000,0×2b7c6e8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0×0002,0×0000,0×000003f7,(nil),0×0006,0×00000000,0×229d410,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:NdrCorrelationInitialize (0×2a4d44c, 0×2a4d04c, 1024, 0×0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:advapi:CheckTokenMembership (0xac 0×21fad0 0×9be5d0) stub!
fixme:ole:NdrCorrelationFree (0×2a4d44c): stub
fixme:ole:NdrCorrelationInitialize (0×2a4d40c, 0×2a4d00c, 1024, 0×0): stub
err:rpc:I_RpcReceive we got fault packet with status 0×1c010003
fixme:ole:NdrCorrelationInitialize (0×2a4d3ac, 0×2a4cfac, 1024, 0×0): stub
fixme:ole:NdrCorrelationInitialize (0×2a4d38c, 0×2a4cf8c, 1024, 0×0): stub
err:rpc:RpcAssoc_BindConnection rejected bind for reason 0
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
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
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:powrprof:DllMain (0×7de60000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0×32f0dc 0×32f0d0
fixme:advapi:CheckTokenMembership ((nil) 0×19de98 0×32f0b8) stub!
fixme:advapi:CheckTokenMembership ((nil) 0×19de98 0×32f0b8) stub!
fixme:powrprof:DllMain (0×7de60000, 0, (nil)) not fully implemented
```

When installing as root user I got:
```
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msi:ACTION_CallDllFunction Custom action (L"C:\\windows\\temp\\msi1bbe.tmp":L"OfficeDataLockPermissions") caused a page fault: c0000005
err:ntdll:RtlpWaitForCriticalSection section 0x7e606b78 "handle.c: MSI_object_cs" wait timed out in thread 0024, blocked by 00bd, retrying (60 sec)
wine: Critical section 7e606b78 wait failed at address 0x7bc3c090 (thread 0024), starting debugger...
Unhandled exception: wait failed on critical section 0x7e606b78
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3c090
root@bearing:/home/citybird/Desktop/Office2007pro_eng# Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000c 
	0000001f    0
	0000000e    0
	0000000d    0
0000000f 
	00000010    0
0000001c 
	00000022    0
	00000021    0
	0000001e    0
	0000001d    0
0000002a 
	00000032    0
	00000031    0
	0000002c    0
	0000002b    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
```

illmatic: can you please explain what 2 things you need to change in the winecfg???

Thanks in advance.

you got a pm

---

### Post by rmayer32 on 2009-03-19
Nice, I am going to give this one a try.

---

### Post by mdrobnak on 2009-03-19
Could you post the two items please? I'm trying to use 1.1.9 on a volume license install, and it's not working.. I'd rather try 1.1.17 as it's newer.

Thanks.

-Matt

---

### Post by illmatic on 2009-03-19
> **mdrobnak said:**
> Could you post the two items please? I'm trying to use 1.1.9 on a volume license install, and it's not working.. I'd rather try 1.1.17 as it's newer.

Thanks.

-Matt

> hi,

first of all you obivously can't install office 07 with wine 1.17

The 2 things you need to change aren't necessary to install office 2007.
With wine 1.16 you can install it out of box.
But if you want to start office after the installation you need to add following things in the winecfg
so following steps need to be done:
1.winecfg
2.go to library tab
3.add new dll and just type riched 20
4. riched 20 appears press it and add it to the library
5. click on edit and make it (Native, Windows)

6. repeat 3-4 with usp10
7. click on edit and make it (Native, Builtin)

Now office should work
Hf

regards
Illmatic
In fact that's how it worked for me :), though I didn't install all programmes (e.g. Access)
How you'll get access to work you can read here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

---

### Post by gatorbrit on 2009-03-19
When I followed the instructions I ended up with wine version 1.1.17 and as noted it doesn't work.  How do I install an earlier version of wine?

Thanks

EDIT: OK I got the earlier version 1.1.9 from here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
I uninstalled wine, winetricks and deleted the folders in my home dir.   

Then I followed the instructions and I get the error from the office setup that i am trying to use a windows 3.1 installer.

Any suggestions? 
thanks

---

### Post by illmatic on 2009-03-20
> **gatorbrit said:**
> When I followed the instructions I ended up with wine version 1.1.17 and as noted it doesn't work.  How do I install an earlier version of wine?

Thanks

EDIT: OK I got the earlier version 1.1.9 from here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
I uninstalled wine, winetricks and deleted the folders in my home dir.   

Then I followed the instructions and I get the error from the office setup that i am trying to use a windows 3.1 installer.

Any suggestions? 
thanks
hm,
just try 1.1.16 that should really work o.O

---

### Post by gatorbrit on 2009-03-20
Even with wine 1.1.16 the office installer fails claiming that I am using a win 3.1 installer.

---

### Post by illmatic on 2009-03-20
> **gatorbrit said:**
> Even with wine 1.1.16 the office installer fails claiming that I am using a win 3.1 installer.

Did you try simply to isntall windows installer through wine?
In winetricks ther's only version 2.1

---

### Post by kamitsukai on 2009-03-20
Can you copy & Paste images into word 2007 yet? as this was a problem when I last use it, only the address to the image would be pasted...

---

### Post by illmatic on 2009-03-21
The import of pictures from the desktop for example works for me ;)

---

### Post by hyperdude111 on 2009-03-21
You do realise this tread is over a year old and the new versions of wine 1.01-1.17 all support MSoffice from install.

---

