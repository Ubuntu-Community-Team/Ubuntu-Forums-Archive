---
title: "Difference between launching with bash and double clicking"
date: 2011-07-25
forum: Wine
---

### Post by xir_ on 2011-07-25
Hi everyone

I am running an application which works by double clicking/unity launching (with the default command being wine), but when I try an launch it via the command line i receive a ton of path errors.

Can anyone tell me if there are additional variables set by the graphical method of execution.

Thanks for any and all help.

ninja edit: this is wine-1.3.24 on ubuntu 11.04

---

### Post by disabledaccount on 2011-07-25
In such case it would be helpful if You provide some details, like command from launcher (from its properties dialog window) and errors from cmdline.

---

### Post by xir_ on 2011-07-26
> **tomazzi said:**
> In such case it would be helpful if You provide some details, like command from launcher (from its properties dialog window) and errors from cmdline.

Sure thing. The launching command would nomally use is 

```
wine /home/bennie/.wine/drive_c/g09w/gview.exe 

```
The launcher command is:

```
env WINEPREFIX="/home/bennie/.wine/" wine "C:\g09w\gview.exe"

```

The reason i didn't include it in the OP is because running this command in the terminal doesn't work any better.

The errors i am seeing are during the run are 
```
fixme:imm:ImmReleaseContext (0x5028c, 0x1455e8): stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x153fac 0x3a297aa4 0x32fa08 - stub
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
fixme:advapi:GetEffectiveRightsFromAclW 0x1e1bec 0x3a297aa4 0x32f834 - stub
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
wine: Unhandled page fault on read access to 0x00000008 at address 0x7e751ae8 (thread 0038), starting debugger...
WineDbg starting on pid 0037
Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x7e751ae8).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e751ae8 ESP:0032fc10 EBP:0032fc28 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:019d5940 EBX:7e7f0ff4 ECX:00110064 EDX:00000000
 ESI:0021d578 EDI:00000000
Stack dump:
0x0032fc10:  019d5940 00000000 0021d6e8 7e7f0ff4
0x0032fc20:  0021d610 0021d608 0032fc88 7e776ef9
0x0032fc30:  0021d578 00000000 0021d6a8 7ecfefc1
0x0032fc40:  000c0280 00000000 001b6428 00000000
0x0032fc50:  00000001 00110000 00000001 7bc342d1
0x0032fc60:  7e7e017a 00000000 00000000 0021d610
Backtrace:
=>0 0x7e751ae8 in ole32 (+0x41ae8) (0x0032fc28)
  1 0x7e776ef9 in ole32 (+0x66ef8) (0x0032fc88)
  2 0x7e7291b4 in ole32 (+0x191b3) (0x0032fcd8)
  3 0x7e72a882 CoUninitialize+0x131() in ole32 (0x0032fd08)
  4 0x7e7531e3 OleUninitialize+0x82() in ole32 (0x0032fd28)
0x7e751ae8: call	*0x8(%edx)

```

---

### Post by disabledaccount on 2011-07-26
You shouldn't have to use WINEPREFIX, because ~/.wine is default location...

First try to change dir to program's location - this should solve problems with missing paths. Then, if app will hung again use tee command to provide full log of what happened:
[I]>cd <program path>
>wine[/I] <program_path/app> 2>&1 | *tee* ~/*wine.log*

---

### Post by xir_ on 2011-07-26
Hi 

I executed from the directory and this was the result from tee (same as before):
 

```
fixme:imm:ImmReleaseContext (0x20030, 0x143cb0): stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x152b34 0x3a297aa4 0x32fa08 - stub
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
fixme:advapi:GetEffectiveRightsFromAclW 0x1e1d34 0x3a297aa4 0x32f834 - stub
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
wine: Unhandled page fault on read access to 0x00000008 at address 0x7e73eae8 (thread 0009), starting debugger...
WineDbg starting on pid 0008
Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x7e73eae8).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e73eae8 ESP:0032fc10 EBP:0032fc28 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:01ae28b8 EBX:7e7ddff4 ECX:00110064 EDX:00000000
 ESI:0021dcb0 EDI:00000000
Stack dump:
0x0032fc10:  01ae28b8 00000000 0021de20 7e7ddff4
0x0032fc20:  0021dd48 0021dd40 0032fc88 7e763f29
0x0032fc30:  0021dcb0 00000000 0021dde0 7ecf3fc1
0x0032fc40:  00050060 00000000 001b5f90 00000000
0x0032fc50:  00000001 00110000 00000001 7bc342d1
0x0032fc60:  7e7cd1ba 00000000 00000000 0021dd48
Backtrace:
=>0 0x7e73eae8 in ole32 (+0x3eae8) (0x0032fc28)
  1 0x7e763f29 in ole32 (+0x63f28) (0x0032fc88)
  2 0x7e7161b4 in ole32 (+0x161b3) (0x0032fcd8)
  3 0x7e717882 CoUninitialize+0x131() in ole32 (0x0032fd08)
  4 0x7e7401e3 OleUninitialize+0x82() in ole32 (0x0032fd28)
0x7e73eae8: call	*0x8(%edx)
Wine-dbg>
```


There must be some environmental variable set by the graphical method of launching that i need to pass to the command line.

---

### Post by disabledaccount on 2011-07-26
I've never heard of such env var - I suppose this can be bug in wine and/or ubuntu.
Have You installed any dll overrides? (trough winetricks?)

---

### Post by xir_ on 2011-07-27
> **tomazzi said:**
> I've never heard of such env var - I suppose this can be bug in wine and/or ubuntu.
Have You installed any dll overrides? (trough winetricks?)

There are some direct x overrides, but i cant seeing it being the cause of the problem. It doesn't make any sense that executing it via a double lick or the unity launcher has no issues but execution via the command line causes lots of path problems.

Maybe i should try and cross post this to the wine forums.

cheers for the help

---

### Post by disabledaccount on 2011-07-27
I've asked about dll overrides because it seems that crash is not caused due to different environment. It looks like different config was used (eg. without necessary dll overrides). You can try to run winecfg from terminal and check what overrides are active.

---

