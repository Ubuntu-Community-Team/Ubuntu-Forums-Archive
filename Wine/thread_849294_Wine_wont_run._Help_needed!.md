---
title: "Wine wont run. Help needed!"
date: 2008-07-04
forum: Wine
---

### Post by ioniviil on 2008-07-04
Hi everyone, I've been using wine for some time until now, but not lately, nevertheless, I upgraded it every time  that the update manager found one (I am using the official repository of Wine, to get the latest Version). Yesterday I wanted to use it and I found out that it doesn't run. not even winecfg!.
I'll put here some outputs:

-This output I got when trying to run winecfg:

```
ioniviil@ioniviil-desktop:~$ winecfg
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32f030) stub
fixme:advapi:LsaOpenPolicy ((null),0x32efd8,0x00000001,0x32eff4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0xde0160,L"Server",L"\\\\ioniviil-deskto",0x150be8,0xac,0x00000001,0x00000001,(nil),0,1,0x75ebb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0xde0160,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"PDF"
err:winspool:CUPS_LoadPrinters printer 'PDF' not added by AddPrinterA (error 1801)
ALSA lib ../../../src/pcm/pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
```

-This output I got when trying to run a program:

```
ioniviil@ioniviil-desktop:~$ '/media/sda1/Archivos de programa/Garena/Garena.exe' 
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32f030) stub
fixme:advapi:LsaOpenPolicy ((null),0x32efd8,0x00000001,0x32eff4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x1250160,L"Server",L"\\\\ioniviil-deskto",0x151ec8,0xbc,0x00000001,0x00000001,(nil),0,1,0x75ebb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x1250160,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"PDF"
err:winspool:CUPS_LoadPrinters printer 'PDF' not added by AddPrinterA (error 1801)
ALSA lib ../../../src/pcm/pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
```


I am completely clueless about the errors it is getting, just in case it helps somehow, I've never used dll override, nor anything complex.
Any help is appreciated!

---

### Post by brazemcee on 2008-07-04
Hm...
I'm not a Wine specialist ahhauhauahua
but I think it must something related to a recently installed printer. Try reinstalling it again (Wine and your printer).

See you.

---

### Post by ioniviil on 2008-07-05
Ok, thought I've never plugged a printer to this machine, I tried reinstalling wine, completely, that is complete remove fist, then install, and the very exact problem persist the same. It gives the exact output when I try running winecfg.
Any other suggestion?

---

### Post by kdorf on 2008-07-05
Try deleting your Wine prefix directory (~/.wine) and running it again. Be warned that this will delete everything you have installed in Wine (unless you're using different Wine prefixes) so you might want to back things up first.

---

### Post by zapree on 2008-07-06
im still new 2 ubuntu what would be the code for deleting it?

---

### Post by kdorf on 2008-07-06
Type "rm -rf ~/.wine" at the terminal (without quotes) and that should do it for you.

Remember this will delete programs installed in Wine, as well as remove their settings, but it might fix things for you. Alternatively, if you want to back things up, you can just move the directory.

"mv ~/.wine .winebackup"

It'll put your backup stuff in .winebackup.

A word of caution: be careful when using "rm -rf" because if you mistype, you could delete a bunch of stuff from your home directory. Double check everything before you hit enter, and if you see that you mistyped it hit "Ctrl-C" to cancel the operation. That way it won't delete everything :P

---

### Post by zapree on 2008-07-06
hmmm it doesnt do anything.... a new line just pops up... Any idea what thats about?

---

### Post by kdorf on 2008-07-06
If the new line is blank, it's working. Just give it time. When it shows the prompt and lets you type again, it's done. If you want to see it actually work you could type

"rm -rfv ~/.wine"

---

### Post by Hubbins on 2008-07-06
I have the exact same problem when running winecfg. However I can still run programs with wine. I have no idea as to the cause or solution but I did file a bug report with wine so hopefully they'll fix it.

---

