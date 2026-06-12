---
title: "Problem running Age of Mythology with wine"
date: 2008-06-15
forum: Wine
---

### Post by MsTiggy on 2008-06-15
I am running the most recent version of wine and ubuntu, and trying to install Age of Mythology.

When I run "wine aom.exe" from the terminal, this is what I get:

```
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 2/11/2008, dlt (d/m/y): 9/03/2008
fixme:imm:ImmGetDefaultIMEWnd ((nil) - (nil) 0x7f023cd8 ): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x80044, 0x7f023cd8): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x7f023cd8): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21ef28,0x00000000), stub!
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb7f4abad
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7e8dc690,0x7f5a664a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7f01a190,0x7f5a664a): stub
err:eventlog:ReportEventW L"3"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7e8dc690,0x7f5a66c2): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7f01a190,0x7f5a66c2): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x7e8dc690,0x7f5a7b4a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x7f01a190,0x7f5a7b4a): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

In the game window, it says "Cannot create log file.  Please make sure that you have full file rights on the directory you installed Age of Mythology into, and that you have available disk space.  Error: sharing violation"

I've got 16 gigs of free space, so that's not the problem, and I think I have full file permissions on the file.

Any suggestions?

---

### Post by cogadh on 2008-06-15
First, you need to get rid of those preloader errors:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

After taking care of that, run the install again and see what happens.

---

### Post by MsTiggy on 2008-06-15
Thanks for responding so quickly!

Ok, so I got rid of the preloader errors, and I'm still having the same problem.  Here's the new code:

```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 2/11/2008, dlt (d/m/y): 9/03/2008
fixme:imm:ImmGetDefaultIMEWnd ((nil) - (nil) 0x133cd8 ): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0xb0042, 0x133cd8): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x133cd8): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef28,0x00000000), stub!
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb7f43bad
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7e8ef690,0x67664a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x12a190,0x67664a): stub
err:eventlog:ReportEventW L"3"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7e8ef690,0x6766c2): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x12a190,0x6766c2): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x7e8ef690,0x677b4a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x12a190,0x677b4a): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

Thanks for the help!

---

### Post by cogadh on 2008-06-15
Well, according to the game's [AppDB page](http://appdb.winehq.org/appview.php?iAppId=1979), you need to copy a MFC42.dll file from a Windows machine, place it in Wine's system32 directory and apply a library override for it in winecfg. It also says you need to install MSXML 4 from the game's CD, but I recommend using [winetricks](http://wiki.winehq.org/winetricks) to do that instead.

---

### Post by Meow27 on 2008-06-15
a cracked .exe might help as well

---

### Post by MsTiggy on 2008-06-15
Ok, I installed msxml4 via winetricks, worked fine.  I have mfc42.dll in the system32 file, and applied the override in the winecfg library tab.

It's still coming up with the same error.

Here's the code now:

```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 2/11/2008, dlt (d/m/y): 9/03/2008
fixme:imm:ImmGetDefaultIMEWnd ((nil) - (nil) 0x133cd8 ): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x11005c, 0x133cd8): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x133cd8): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef28,0x00000000), stub!
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb7ef7bad
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7e8ee690,0x67664a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x12a190,0x67664a): stub
err:eventlog:ReportEventW L"3"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7e8ee690,0x6766c2): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x12a190,0x6766c2): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x7e8ee690,0x677b4a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x12a190,0x677b4a): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

---

### Post by MsTiggy on 2008-06-15
> **Meow27 said:**
> a cracked .exe might help as well

I'm sorry, I'm kind of a noob, what does that mean? :confused:

---

### Post by cogadh on 2008-06-16
I can't believe I didn't notice this before, you said you were trying to install the game, but you also said you are trying to "wine aom.exe". Usually, an install executable is named something like setup.exe or install.exe, while the actual game executable would be named something like aom.exe. You may be trying to run the wrong executable.

EDIT - Oh, almost forgot, a cracked executable is a modified executable for the game that has had the copy protection removed. Technically, they are illegal, but since many copy protection schemes don't actually work in Wine, it may be necessary to use one to run your game.

---

### Post by rkdperil on 2011-06-03
I faced this issue earlier, I copied DLL Files from untrusted source and that caused the error. Then as instructed in this website [http://www.bytechip.com/2011/06/how-to-solve-dll-problems-in-wine/](http://www.bytechip.com/2011/06/how-to-solve-dll-problems-in-wine/) I used winetricks to install the DLLs and the problem got solved.

---

