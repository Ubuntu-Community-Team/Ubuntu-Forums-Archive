---
title: "[SOLVED] Wine problem - Installed fine but no icons in the menu and not working"
date: 2008-05-29
forum: Wine
---

### Post by bmwman on 2008-05-29
Hi,

I just installed Wine 1.0 RC2. It isntalled fine and I did the winecfg, etc. The problem is that there're no icons listed in the Applications menu and i cant access the C: drive that it creates or run anything. I tried running a program from terminal but that didnt work either. I removed it and reinstalled multiple times using all different ways that I can think of. Removed from Synaptics, from sudo apt-get remove wine etc. Reinstalled manually or from the depositories - same thing. Installs fine but doesnt create shortcuts and i think it doesnt work.

Any ideas what should I do?
Thanks

---

### Post by cogadh on 2008-05-29
What exactly happened when you tried running the program from the terminal (i.e. what was output to the terminal)? Have you logged out or rebooted since installing Wine (sometimes the menu items don't appear until you do that)? The "C:" drive that it creates is actually in a hidden directory in your home folder. Fire up Nautilis, hit CTRL+H to show hidden files and look for ".wine", you will find the "C:" drive (labeled "drive_c") in there.

---

### Post by bmwman on 2008-05-29
I rebooted after every install/reinstall and installing does complete succesfully. Now that I found Drive_C i tried to run IE6 which is the only thing i have installed right now and nothing happens. Also I dont have any icons in the APPs menu like i used to. On my laptop installed just fine and everything runs fine. Dunno what the problem is here.

---

### Post by arnabt on 2008-05-29
wine does tend to create some weird issues. hmmmmm. but its' good overall though.

---

### Post by sdowney717 on 2008-05-29
I just installed the rc and when I run winecfg get this
```

scott@scott-desktop:~$ winecfg
err:service:load_reg_multisz Error 1804 while reading value L"DependOnService"
err:service:scmdatabase_load_services Error 1804 reading registry key for service L"TVersityMediaServer" - skipping
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32f030) stub
fixme:advapi:LsaOpenPolicy ((null),0x32efd8,0x00000001,0x32eff4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x4a0158,L"Server",L"\\\\scott-desktop",0x138908,0xac,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x4a0158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"DeskJet-880C"
err:winspool:CUPS_LoadPrinters printer 'DeskJet-880C' not added by AddPrinterA (error 1801)
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x4a0158,L"Server",L"\\\\scott-desktop",0x138908,0xac,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x4a0158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"LaserJet-4000"
err:winspool:CUPS_LoadPrinters printer 'LaserJet-4000' not added by AddPrinterA (error 1801)
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x4a0158,L"Server",L"\\\\scott-desktop",0x138908,0xac,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x4a0158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"PDF"
err:winspool:CUPS_LoadPrinters printer 'PDF' not added by AddPrinterA (error 1801)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
scott@scott-desktop:~$ 



```

---

### Post by bmwman on 2008-05-30
I figured it :)

 Originally Posted by mc4man  View Post
i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
Code:

<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>

remove the <Deleted/>
maybe kde does the same thing

and just reinstall wine. Everything is back to normal.

---

### Post by jackhe22 on 2008-05-30
Simply,

Go to Applications - Click Add/Remove. Select All Apps from the menu. Search Wine.
Install it from Add/Remove.
Reboot.
Go to Applications - Terminal
Type winefile
Here you go! The Windows File Manager

---

