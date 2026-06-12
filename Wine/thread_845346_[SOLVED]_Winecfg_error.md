---
title: "[SOLVED] Winecfg error"
date: 2008-06-30
forum: Wine
---

### Post by BlackSwordD2 on 2008-06-30
ok i recently found i cant access my winecfg (either in terminal or from menu) and it might have had something to do with the recent wine update

winecfg run from the menu does nothing while winecfg command in the terminal returns this output 

```
 blackswordd2@ubuntu:~$ winecfg
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x33f030) stub
fixme:advapi:LsaOpenPolicy ((null),0x33efd8,0x00000001,0x33eff4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x4b0150,L"Server",L"\\\\ubuntu",0x1348e8,0xac,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x4b0150,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"PDF"
err:winspool:CUPS_LoadPrinters printer 'PDF' not added by AddPrinterA (error 1801)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17 
```

games will still run in wine but i need to do tweaking for others any suggestions?

---

### Post by lawwills on 2008-07-01
I'm having exactly the same problem! i've tried un-installing it and it still don't work

---

### Post by BlackSwordD2 on 2008-07-01
well i guess we just have to though it out then for a few weeks till the next update comes along to fix it...

---

### Post by craigchambers on 2008-07-02
I'm having this problem too.  I tried rolling back the version of Wine to a previous version and that still fails to work.

I also can't access any of my Windows apps (i.e. games).
```

fixme:ntoskrnl:KeInitializeSpinLock 0x4577a4
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32f030) stub
fixme:advapi:LsaOpenPolicy ((null),0x32efd8,0x00000001,0x32eff4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x4a0160,L"Server",L"\\\\craigchambers-d",0x15b7b0,0xa8,0x00000001,0x00000001,(nil),0,1,0x75bfb4f8)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x4a0160,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"PDF"
err:winspool:CUPS_LoadPrinters printer 'PDF' not added by AddPrinterA (error 1801)
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x4a0160,L"Server",L"\\\\craigchambers-d",0x15b7b0,0xa8,0x00000001,0x00000001,(nil),0,1,0x75bfb4f8)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x4a0160,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"Stylus_CX3200"
err:winspool:CUPS_LoadPrinters printer 'Stylus_CX3200' not added by AddPrinterA (error 1801)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
```


/Craig

---

### Post by BlackSwordD2 on 2008-07-03
ok i have strong reason to believe i have found the answer

i bet both of you, like me, installed a game recently that needed some DLL's and you just went to your nearest windows machine and did the good ol' copy and paste to get it over and done with. and also cause we didn't feel like waiting just hit the "replace all" button cause what would go wrong right?

turns out thats our problem

this file
```

wineps.drv

```
was deleated/rewritten/overwritten/whatever so that its the windows version and not the wine version


but now that we know the problem we could perhaps fix it?

one possible way would be to deleate the .wine folder and try running winecfg again...or deleate and re-install because the re-installation isn't touching that folder cept to acess it

right now im trying my other comp's wine and im going to more or less fix the error by doing the same mistake backwards (2 wrongs make a right?)

---

### Post by BlackSwordD2 on 2008-07-03
I AM JACK'S EXUBERANT JOY!!!

i have found the culprit to our problems!!

go to where your DLL files are located and hunt down this DLL

```

localspl.dll

```

delete it and it fixed all of my problems, i can run winecfg, and play ll my games wooo!!!

---

### Post by craigchambers on 2008-07-04
I am Jack's sense of gratitude.

Worked for me.  Thanks BlackSwordD2.

My Wine config is basically piggybacked on my old Windoze install.  Probably highly discouraged, but it works for me.
As I don't use Windoze any more I'm not fussed if I break it.  The DLL was in my old C:\Windows\system32 folder.  Renaming it did the trick.

/Craig

---

### Post by mickeyknox on 2009-09-14
Thanks really a lot, i installed the programs via Wine-Doors, but Flash and Dreamweaver stoped to work after the first start, complaining bout something with the printer too. I tried to edit the register (wine regedit) but seems like wine dont save the changes i've made.  Now all are working fine, i just deleted the DLL too and everything is okay now! Thanks and big hug from Brazil!

---

