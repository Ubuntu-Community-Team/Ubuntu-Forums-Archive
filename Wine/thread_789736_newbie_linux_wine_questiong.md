---
title: "newbie linux wine questiong?"
date: 2008-05-10
forum: Wine
---

### Post by evilnone on 2008-05-10
Ok I dont know if this a minor problem via a setting or tag im not setting or what.... but let me explain this real quick.

I am new to linux and the only thing I have not been able to get working yet is a program I have to use for work.. The program is called Teletracker online and it is a sales tracking program.

[http://www.teletracker.com/downloads/413/ttsetupfull.exe](http://www.teletracker.com/downloads/413/ttsetupfull.exe)

thats a link to it if it helps with my problem.

When I install it during the install a lot of messages where you would normally enter settings at are just blank... the text boxes are there when you scroll through them but there is no text on it anywhere.  The buttons for next and back are also missing.  If you continue on with the install (which I did thinking it would work afterwords) you are greeted with a program that loads up but has no text to setup.

I know I am new so I am asking for help (i did a lot of searching today too and have found nothing).  All I did to install that was download the setup file double click it and have it open through wine.  I have no other info to give unless you tell me how to get it... Can someone PLEASE help me this is the LAST thing I need to migrate to linux completely.

---

### Post by cogadh on 2008-05-10
Instead of double-clicking it, run it from the terminal. That way, Wine will output any error messages to the terminal, which may explain what is going on:
```
cd /path/to/install/executable
wine install.exe
```

---

### Post by evilnone on 2008-05-10
ok im getting alot of fixme stuff so i will just post it and see if you know what I need to do....

```
~ $ wine ttsetupfull.exe
fixme:shell:IShellLinkA_fnGetPath (0x79a688): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x79a688): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x79a688): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x79a688): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Common Files\\Microsoft Shared\\DAO\\dao2535.tlb" failed with error 2
fixme:atl:AtlModuleInit SEMI-STUB (0x1038e100 0x1019e888 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x660112f8 0x6600e2b8 0x66000000)
fixme:ole:DllRegisterServer stub
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"mscorlib"
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"mscorlib"
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"mscorlib"
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"mscorlib"
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"mscorlib"
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"mscorlib"

```


thats all of it...

---

### Post by cogadh on 2008-05-10
The "fixme" messages are usually just developer notes about incomplete or unimplemented functions in Wine. There is usually nothing you can do about them and most applications will get some of them every time they are run. The only actual error you got was this:
```
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Common Files\\Microsoft Shared\\DAO\\dao2535.tlb" failed with error 2
```
It is looking for a database component that is not present in Wine. I think it is a rather old DB component as well (like circa 1997). You probably just need to install MDAC. I'd advise using WineTricks to do that:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by evilnone on 2008-05-10
ok when i try to do that i dont think it is going to fix my problems...

here is a screenshot

[[IMG]http://img147.imageshack.us/img147/4595/snapshot1oq7.th.png[/IMG]](http://img147.imageshack.us/my.php?image=snapshot1oq7.png)

any idea why I can't even see the text?

---

### Post by cogadh on 2008-05-10
Ah, I see you have some desktop effects enabled. Wine doesn't play nice with that, which could explain the missing text. Turn off all desktop effects and try running the original install again.

---

### Post by evilnone on 2008-05-10
ok i turned off all visual effects (compiz at least not sure what else as u can tell im using sabayon and it comes preinstalled with a lot)

i still cannot see the text on the installs as well as can not see the text on winecfg... i am going to run this command after google...

rm -fr ~/.wine && winecfg

then reinstall if needed

---

### Post by cogadh on 2008-05-10
Just an FYI, I tried running the install myself and I was able to get full text on all the install dialogs, so I don't think it is a problem with Wine itself. The source of the problem is likely either something in your Wine configuration or your system configuration.

---

### Post by evilnone on 2008-05-10
well thats great.... how do i completely remove wine? and what settings should i be using for it?  I thought I had it setup ok... i guess not...

edit:

when i do an emerge wine i get some warnings... looks like fonts... think thats the problem?

```
warning: MS Sans Serif 20: missing glyph for char 0099
warning: MS Sans Serif 20: missing glyph for char 009a
warning: MS Sans Serif 20: missing glyph for char 009b
warning: MS Sans Serif 20: missing glyph for char 009c
warning: MS Sans Serif 20: missing glyph for char 009f
warning: MS Sans Serif 20: missing glyph for char 0e01
warning: MS Sans Serif 20: missing glyph for char 0e02
warning: MS Sans Serif 20: missing glyph for char 0e03
warning: MS Sans Serif 20: missing glyph for char 0e04
warning: MS Sans Serif 20: missing glyph for char 0e05
warning: MS Sans Serif 20: missing glyph for char 0e06
warning: MS Sans Serif 20: missing glyph for char 0e07
warning: MS Sans Serif 20: missing glyph for char 0e08
warning: MS Sans Serif 20: missing glyph for char 0e09
warning: MS Sans Serif 20: missing glyph for char 0e0a
warning: MS Sans Serif 20: missing glyph for char 0e0b
warning: MS Sans Serif 20: missing glyph for char 0e0c
warning: MS Sans Serif 20: missing glyph for char 0e0d
warning: MS Sans Serif 20: missing glyph for char 0e0e
warning: MS Sans Serif 20: missing glyph for char 0e0f
warning: MS Sans Serif 20: missing glyph for char 0e10
warning: MS Sans Serif 20: missing glyph for char 0e11
warning: MS Sans Serif 20: missing glyph for char 0e12
warning: MS Sans Serif 20: missing glyph for char 0e13
warning: MS Sans Serif 20: missing glyph for char 0e14
warning: MS Sans Serif 20: missing glyph for char 0e15
warning: MS Sans Serif 20: missing glyph for char 0e16
warning: MS Sans Serif 20: missing glyph for char 0e17
warning: MS Sans Serif 20: missing glyph for char 0e18
warning: MS Sans Serif 20: missing glyph for char 0e19
warning: MS Sans Serif 20: missing glyph for char 0e1a
warning: MS Sans Serif 20: missing glyph for char 0e1b
warning: MS Sans Serif 20: missing glyph for char 0e1c
warning: MS Sans Serif 20: missing glyph for char 0e1d
warning: MS Sans Serif 20: missing glyph for char 0e1e
warning: MS Sans Serif 20: missing glyph for char 0e1f
warning: MS Sans Serif 20: missing glyph for char 0e20
warning: MS Sans Serif 20: missing glyph for char 0e21
warning: MS Sans Serif 20: missing glyph for char 0e22
warning: MS Sans Serif 20: missing glyph for char 0e23
warning: MS Sans Serif 20: missing glyph for char 0e24
warning: MS Sans Serif 20: missing glyph for char 0e25
warning: MS Sans Serif 20: missing glyph for char 0e26
warning: MS Sans Serif 20: missing glyph for char 0e27
warning: MS Sans Serif 20: missing glyph for char 0e28
warning: MS Sans Serif 20: missing glyph for char 0e29
warning: MS Sans Serif 20: missing glyph for char 0e2a
warning: MS Sans Serif 20: missing glyph for char 0e2b
warning: MS Sans Serif 20: missing glyph for char 0e2c
warning: MS Sans Serif 20: missing glyph for char 0e2d
warning: MS Sans Serif 20: missing glyph for char 0e2e
warning: MS Sans Serif 20: missing glyph for char 0e2f
warning: MS Sans Serif 20: missing glyph for char 0e30
warning: MS Sans Serif 20: missing glyph for char 0e31
warning: MS Sans Serif 20: missing glyph for char 0e32
warning: MS Sans Serif 20: missing glyph for char 0e33
warning: MS Sans Serif 20: missing glyph for char 0e34
warning: MS Sans Serif 20: missing glyph for char 0e35
warning: MS Sans Serif 20: missing glyph for char 0e36
warning: MS Sans Serif 20: missing glyph for char 0e37
warning: MS Sans Serif 20: missing glyph for char 0e38
warning: MS Sans Serif 20: missing glyph for char 0e39
warning: MS Sans Serif 20: missing glyph for char 0e3a
warning: MS Sans Serif 20: missing glyph for char 0e3f
warning: MS Sans Serif 20: missing glyph for char 0e40
warning: MS Sans Serif 20: missing glyph for char 0e41
warning: MS Sans Serif 20: missing glyph for char 0e42
warning: MS Sans Serif 20: missing glyph for char 0e43
warning: MS Sans Serif 20: missing glyph for char 0e44
warning: MS Sans Serif 20: missing glyph for char 0e45
warning: MS Sans Serif 20: missing glyph for char 0e46
warning: MS Sans Serif 20: missing glyph for char 0e47
warning: MS Sans Serif 20: missing glyph for char 0e48
warning: MS Sans Serif 20: missing glyph for char 0e49
warning: MS Sans Serif 20: missing glyph for char 0e4a
warning: MS Sans Serif 20: missing glyph for char 0e4b
warning: MS Sans Serif 20: missing glyph for char 0e4c
warning: MS Sans Serif 20: missing glyph for char 0e4d
warning: MS Sans Serif 20: missing glyph for char 0e4e
warning: MS Sans Serif 20: missing glyph for char 0e4f
warning: MS Sans Serif 20: missing glyph for char 0e50
warning: MS Sans Serif 20: missing glyph for char 0e51
warning: MS Sans Serif 20: missing glyph for char 0e52
warning: MS Sans Serif 20: missing glyph for char 0e53
warning: MS Sans Serif 20: missing glyph for char 0e54
warning: MS Sans Serif 20: missing glyph for char 0e55
warning: MS Sans Serif 20: missing glyph for char 0e56
warning: MS Sans Serif 20: missing glyph for char 0e57
warning: MS Sans Serif 20: missing glyph for char 0e58
warning: MS Sans Serif 20: missing glyph for char 0e59
warning: MS Sans Serif 20: missing glyph for char 0e5a
warning: MS Sans Serif 20: missing glyph for char 0e5b
warning: System 16: missing glyph for char 0402
warning: System 16: missing glyph for char 0403
warning: System 16: missing glyph for char 0453
warning: System 16: missing glyph for char 0409
warning: System 16: missing glyph for char 040a
warning: System 16: missing glyph for char 040c
warning: System 16: missing glyph for char 040b
warning: System 16: missing glyph for char 040f
warning: System 16: missing glyph for char 0452
warning: System 16: missing glyph for char 0459
warning: System 16: missing glyph for char 045a
warning: System 16: missing glyph for char 045c
warning: System 16: missing glyph for char 045b
warning: System 16: missing glyph for char 045f
warning: System 16: missing glyph for char 0408
warning: System 16: missing glyph for char 0458
warning: System 16: missing glyph for char 0405
warning: System 16: missing glyph for char 0455
warning: System 16: missing glyph for char 05b0
warning: System 16: missing glyph for char 05b1
warning: System 16: missing glyph for char 05b2
warning: System 16: missing glyph for char 05b3
warning: System 16: missing glyph for char 05b4
warning: System 16: missing glyph for char 05b5
warning: System 16: missing glyph for char 05b6
warning: System 16: missing glyph for char 05b7
warning: System 16: missing glyph for char 05b8
warning: System 16: missing glyph for char 05b9
warning: System 16: missing glyph for char 05bb
warning: System 16: missing glyph for char 05bc
warning: System 16: missing glyph for char 05bd
warning: System 16: missing glyph for char 05be
warning: System 16: missing glyph for char 05bf
warning: System 16: missing glyph for char 05c0
warning: System 16: missing glyph for char 05c1
warning: System 16: missing glyph for char 05c2
warning: System 16: missing glyph for char 05c3
warning: System 16: missing glyph for char 05f0
warning: System 16: missing glyph for char 05f1
warning: System 16: missing glyph for char 05f2
warning: System 16: missing glyph for char 05f3
warning: System 16: missing glyph for char 05f4
warning: System 16: missing glyph for char 200e
warning: System 16: missing glyph for char 200f
warning: System 16: missing glyph for char 067e
warning: System 16: missing glyph for char 0679
warning: System 16: missing glyph for char 0686
warning: System 16: missing glyph for char 0698
warning: System 16: missing glyph for char 0688
warning: System 16: missing glyph for char 06af
warning: System 16: missing glyph for char 06a9
warning: System 16: missing glyph for char 0691
warning: System 16: missing glyph for char 200c
warning: System 16: missing glyph for char 200d
warning: System 16: missing glyph for char 06ba
warning: System 16: missing glyph for char 060c
warning: System 16: missing glyph for char 06be
warning: System 16: missing glyph for char 061b
warning: System 16: missing glyph for char 061f
warning: System 16: missing glyph for char 06c1
warning: System 16: missing glyph for char 0621
warning: System 16: missing glyph for char 0622
warning: System 16: missing glyph for char 0623
warning: System 16: missing glyph for char 0624
warning: System 16: missing glyph for char 0625
warning: System 16: missing glyph for char 0626
warning: System 16: missing glyph for char 0627
warning: System 16: missing glyph for char 0628
warning: System 16: missing glyph for char 0629
warning: System 16: missing glyph for char 062a
warning: System 16: missing glyph for char 062b
warning: System 16: missing glyph for char 062c
warning: System 16: missing glyph for char 062d
warning: System 16: missing glyph for char 062e
warning: System 16: missing glyph for char 062f
warning: System 16: missing glyph for char 0630
warning: System 16: missing glyph for char 0631
warning: System 16: missing glyph for char 0632
warning: System 16: missing glyph for char 0633
warning: System 16: missing glyph for char 0634
warning: System 16: missing glyph for char 0635
warning: System 16: missing glyph for char 0636
warning: System 16: missing glyph for char 0637
warning: System 16: missing glyph for char 0638
warning: System 16: missing glyph for char 0639
warning: System 16: missing glyph for char 063a
warning: System 16: missing glyph for char 0640
warning: System 16: missing glyph for char 0641
warning: System 16: missing glyph for char 0642
warning: System 16: missing glyph for char 0643
warning: System 16: missing glyph for char 0644
warning: System 16: missing glyph for char 0645
warning: System 16: missing glyph for char 0646
warning: System 16: missing glyph for char 0647
warning: System 16: missing glyph for char 0648
warning: System 16: missing glyph for char 0649
warning: System 16: missing glyph for char 064a
warning: System 16: missing glyph for char 064b
warning: System 16: missing glyph for char 064c
warning: System 16: missing glyph for char 064d
warning: System 16: missing glyph for char 064e
warning: System 16: missing glyph for char 064f
warning: System 16: missing glyph for char 0650
warning: System 16: missing glyph for char 0651
warning: System 16: missing glyph for char 0652
warning: System 16: missing glyph for char 200e
warning: System 16: missing glyph for char 200f
warning: System 16: missing glyph for char 06d2
warning: System 16: missing glyph for char 0156
warning: System 16: missing glyph for char 0157
warning: System 16: missing glyph for char 0100
warning: System 16: missing glyph for char 0112
warning: System 16: missing glyph for char 0122
warning: System 16: missing glyph for char 0136
warning: System 16: missing glyph for char 012a
warning: System 16: missing glyph for char 013b
warning: System 16: missing glyph for char 0145
warning: System 16: missing glyph for char 014c
warning: System 16: missing glyph for char 0101
warning: System 16: missing glyph for char 0113
warning: System 16: missing glyph for char 0123
warning: System 16: missing glyph for char 0137
warning: System 16: missing glyph for char 012b
warning: System 16: missing glyph for char 013c
warning: System 16: missing glyph for char 0146
warning: System 16: missing glyph for char 014d
warning: System 16: missing glyph for char 0082
warning: System 16: missing glyph for char 0084
warning: System 16: missing glyph for char 0086
warning: System 16: missing glyph for char 0087
warning: System 16: missing glyph for char 0089
warning: System 16: missing glyph for char 008b
warning: System 16: missing glyph for char 0099
warning: System 16: missing glyph for char 009b
warning: System 16: missing glyph for char 0e01
warning: System 16: missing glyph for char 0e02
warning: System 16: missing glyph for char 0e03
warning: System 16: missing glyph for char 0e04
warning: System 16: missing glyph for char 0e05
warning: System 16: missing glyph for char 0e06
warning: System 16: missing glyph for char 0e07
warning: System 16: missing glyph for char 0e08
warning: System 16: missing glyph for char 0e09
warning: System 16: missing glyph for char 0e0a
warning: System 16: missing glyph for char 0e0b
warning: System 16: missing glyph for char 0e0c
warning: System 16: missing glyph for char 0e0d
warning: System 16: missing glyph for char 0e0e
warning: System 16: missing glyph for char 0e0f
warning: System 16: missing glyph for char 0e10
warning: System 16: missing glyph for char 0e11
warning: System 16: missing glyph for char 0e12
warning: System 16: missing glyph for char 0e13
warning: System 16: missing glyph for char 0e14
warning: System 16: missing glyph for char 0e15
warning: System 16: missing glyph for char 0e16
warning: System 16: missing glyph for char 0e17
warning: System 16: missing glyph for char 0e18
warning: System 16: missing glyph for char 0e19
warning: System 16: missing glyph for char 0e1a
warning: System 16: missing glyph for char 0e1b
warning: System 16: missing glyph for char 0e1c
warning: System 16: missing glyph for char 0e1d
warning: System 16: missing glyph for char 0e1e
warning: System 16: missing glyph for char 0e1f
warning: System 16: missing glyph for char 0e20
warning: System 16: missing glyph for char 0e21
warning: System 16: missing glyph for char 0e22
warning: System 16: missing glyph for char 0e23
warning: System 16: missing glyph for char 0e24
warning: System 16: missing glyph for char 0e25
warning: System 16: missing glyph for char 0e26
warning: System 16: missing glyph for char 0e27
warning: System 16: missing glyph for char 0e28
warning: System 16: missing glyph for char 0e29
warning: System 16: missing glyph for char 0e2a
warning: System 16: missing glyph for char 0e2b
warning: System 16: missing glyph for char 0e2c
warning: System 16: missing glyph for char 0e2d
warning: System 16: missing glyph for char 0e2e
warning: System 16: missing glyph for char 0e2f
warning: System 16: missing glyph for char 0e30
warning: System 16: missing glyph for char 0e31
warning: System 16: missing glyph for char 0e32
warning: System 16: missing glyph for char 0e33
warning: System 16: missing glyph for char 0e34
warning: System 16: missing glyph for char 0e35
warning: System 16: missing glyph for char 0e36
warning: System 16: missing glyph for char 0e37
warning: System 16: missing glyph for char 0e38
warning: System 16: missing glyph for char 0e39
warning: System 16: missing glyph for char 0e3a
warning: System 16: missing glyph for char 0e3f
warning: System 16: missing glyph for char 0e40
warning: System 16: missing glyph for char 0e41
warning: System 16: missing glyph for char 0e42
warning: System 16: missing glyph for char 0e43
warning: System 16: missing glyph for char 0e44
warning: System 16: missing glyph for char 0e45
warning: System 16: missing glyph for char 0e46
warning: System 16: missing glyph for char 0e47
warning: System 16: missing glyph for char 0e48
warning: System 16: missing glyph for char 0e49
warning: System 16: missing glyph for char 0e4a
warning: System 16: missing glyph for char 0e4b
warning: System 16: missing glyph for char 0e4c
warning: System 16: missing glyph for char 0e4d
warning: System 16: missing glyph for char 0e4e
warning: System 16: missing glyph for char 0e4f
warning: System 16: missing glyph for char 0e50
warning: System 16: missing glyph for char 0e51
warning: System 16: missing glyph for char 0e52
warning: System 16: missing glyph for char 0e53
warning: System 16: missing glyph for char 0e54
warning: System 16: missing glyph for char 0e55
warning: System 16: missing glyph for char 0e56
warning: System 16: missing glyph for char 0e57
warning: System 16: missing glyph for char 0e58
warning: System 16: missing glyph for char 0e59
warning: System 16: missing glyph for char 0e5a
warning: System 16: missing glyph for char 0e5b
In file included from capability.c:30:
gphoto2_i.h:28:3: warning: #warning "gphoto2 support in twain needs jpeg development headers"
In file included from ds_ctrl.c:28:
gphoto2_i.h:28:3: warning: #warning "gphoto2 support in twain needs jpeg development headers"
In file included from ds_image.c:33:
gphoto2_i.h:28:3: warning: #warning "gphoto2 support in twain needs jpeg development headers"
In file included from gphoto2_main.c:30:
gphoto2_i.h:28:3: warning: #warning "gphoto2 support in twain needs jpeg development headers"
In file included from ui.c:38:
gphoto2_i.h:28:3: warning: #warning "gphoto2 support in twain needs jpeg development headers"
sql.y: conflicts: 3 reduce/reduce
main.c:153: warning: ‘process_detach’ defined but not used

```

---

### Post by cogadh on 2008-05-10
If fonts are screwed up in Wine, that would definitely explain what is happening. I've never used Sabayon, so I have no idea how their package management system works or how you would go about removing/reinstalling Wine.

---

### Post by evilnone on 2008-05-10
ok well just an FYI they use portage just like gentoo (its based off gentoo)

I am now able to get the fonts showing but I am running into another problem... basically when I log on to it, I get lag like crazy... I am thinking it has to do with that DB u said I need.  I am going to try to reinstall winetricks i suppose

I will let you know though

---

### Post by evilnone on 2008-07-03
just an update.... the personal I was installing this for decided they liked Vista better so this is no longer being used or looked into.  I do however think that wine1.0 runs this if i remember correctly not sure though there is a reports feature... anyways not needed but ty very much for the help

---

