---
title: "CUPS causing Wine problems"
date: 2008-05-13
forum: Wine
---

### Post by cezmunsta on 2008-05-13
Hi,

I appear to have some kind of problem between Wine and CUPS. Whenever I start an application using Wine, I am getting the following output:

```
[SIZE="1"]fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32ef20) stub
fixme:advapi:LsaOpenPolicy ((null),0x32eebc,0x00000001,0x32eeb8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x670158,L"Server",L"\\\\cerwil",0x13f130,0xb0,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x670158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"MINOLTA_C350"
err:winspool:CUPS_LoadPrinters printer 'MINOLTA_C350' not added by AddPrinterA (error 1801)
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x670158,L"Server",L"\\\\cerwil",0x13f130,0xb0,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x670158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
err:winspool:CUPS_LoadPrinters printer 'PDF_file_generator' not added by AddPrinterA (error 1797)
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x670158,L"Server",L"\\\\cerwil",0x13f130,0xb0,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x670158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"Phaser_6350DX"
err:winspool:CUPS_LoadPrinters printer 'Phaser_6350DX' not added by AddPrinterA (error 1801)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
[/SIZE]
```

The problem goes away if I remove printers from CUPS. Does anyone have an idea what the precise cause of the problem may be, as application can't start under Wine? This wasn't a problem yesterday, so far as I am aware, and the only thing that has changed over night is the fact that I have relocated /home on to a different partition.

[ADDED] Wine version = 0.9.59, CUPS version = 1.3.2, Ubuntu 7.10

Thanks,

Cez

---

