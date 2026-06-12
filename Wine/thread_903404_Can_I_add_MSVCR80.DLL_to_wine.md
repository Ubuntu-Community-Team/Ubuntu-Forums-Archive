---
title: "Can I add MSVCR80.DLL to wine?"
date: 2008-08-28
forum: Wine
---

### Post by bmwman on 2008-08-28
I installed MS Communicator 2007 which I need to use for work. It installed fine but when I try to launch it, it gets error and saying that MSVCR80.DLL is missing. I looked in the wine configuration and that library wasn't listed in there. I downloaded it online and copied in the System32 folder but when I go to the wine configuration again it's still not listed. Still can't launch the Communicator 2007.

Is there a way to add that .DLL ?

Thanks.

---

### Post by bmwman on 2008-08-28
After few tries and downloaded couple of missing library files to System32 it launched but still gets error. It says "Microsoft Visual C++ Runtime Library - Runtime error"

Any way to make it work?

---

### Post by liquidfire_24 on 2008-08-28
what the error code that shows up with it ?

---

### Post by bmwman on 2008-08-29
> **liquidfire_24 said:**
> what the error code that shows up with it ?

It says Runtime error R6034 "An application has made an attempt to load the C runtime library incorrectly"

Here is what's in the terminal if it's helpful:

bmw-man@bmw-man-desktop:~$ env WINEPREFIX="/home/bmw-man/.wine" wine "C:\Program Files\Microsoft Office Communicator\communicator.exe" 
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a060 0x1001818 1 0x33fe78 (null) (null) 0x100a068
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a080 0x1001808 1 0x33fe78 (null) (null) 0x100a088
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0a0 0x10017f8 1 0x33fe78 (null) (null) 0x100a0a8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0c0 0x10017e8 1 0x33fe78 (null) (null) 0x100a0c8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0e0 0x10017d8 1 0x33fe78 (null) (null) 0x100a0e8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a100 0x10017c8 1 0x33fe78 (null) (null) 0x100a108
fixme:win:RegisterDeviceNotificationW (hwnd=0x127938, filter=0x7e42e90c,flags=0x00000001), STUB!
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office Communicator\\communicator.exe" failed, status c0000142


Thank you

---

### Post by bmwman on 2008-09-02
Any ideas?

---

### Post by b0b138 on 2008-09-02
Try going to ms site and downloading the c++ redistributable package.

[http://www.microsoft.com/downloads/details.aspx?FamilyID=9b2da534-3e03-4391-8a4d-074b9f2bc1bf&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=9b2da534-3e03-4391-8a4d-074b9f2bc1bf&DisplayLang=en)

---

### Post by liquidfire_24 on 2008-09-02
its a manifesting error same problem i was having with CS3 ... best answer i can give you right now... sadly... install Virtual box--> your choice of windows and run it in windows untill someone finds a fix for it.

---

### Post by bmwman on 2008-09-03
> **b0b138 said:**
> Try going to ms site and downloading the c++ redistributable package.

[http://www.microsoft.com/downloads/details.aspx?FamilyID=9b2da534-3e03-4391-8a4d-074b9f2bc1bf&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=9b2da534-3e03-4391-8a4d-074b9f2bc1bf&DisplayLang=en)

I do have the C++ package installed. I used that winetricks script. 

And I do have a VMware server with XP installed but i really don't feel like firing up Windows every time I need to use my work IM. That's what I'm doing right now but I was hoping there is a way to get this thing working with wine.

---

### Post by aot2002 on 2008-11-24
I'm on the same issue, I've installed and tried 1.1.9 still no luck

---

### Post by cogadh on 2008-11-25
I know this is a little late, but you can manually add a library override, even if it isn't listed in the drop-down in winecfg. All you need to do is simply type the file name in the drop-down field.

---

