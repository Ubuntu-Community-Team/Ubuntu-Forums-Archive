---
title: "M.D. Software Error"
date: 2008-06-28
forum: Wine
---

### Post by Darkade on 2008-06-28
Hey! My aunt is a medic and is just sick of vista. so I setup for her a dual boot so that she could tryout ubuntu. The main problem is migration, she's open to migrate but some of her software just runs in windows. After a couple hours I've managed to use wine to install everything she uses, except one piece of software, (It's not know, one of those freeware that some pharmaceutical labs use) but she really likes it and find it usefull. so I've post the wine output. any Ideas why this is happening?

```
$ wine Medix.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:ole:OleLoadPictureEx (0x7f96060c,7286,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x7f21fae8), partially implemented.
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id 191, flags 0x8!
fixme:ole:OLEPictureImpl_SaveAsFile (0x7f01af28)->(0x7f03f120, 0, (nil)), hacked stub.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!

```

---

### Post by Fred_E _krugar on 2008-06-29
Well if you cant use wine to run it have you thought about running Windows in a Virtual machine just to run that single program??

---

### Post by Darkade on 2008-06-29
Yes, I have consider that. But I really never have used a Virtual Machine so I don't know how much will windows take to load. Because if it's the same time it takes to boot then there's no much of a point in making the switch to ubuntu

---

### Post by Darkade on 2008-06-29
Can you tell me how does a virtual machine works or a link to a virtual machine how to please?

---

### Post by Fred_E _krugar on 2008-06-29
[http://ubuntuforums.org/showthread.php?t=183209&highlight=Virtual+box](http://ubuntuforums.org/showthread.php?t=183209&highlight=Virtual+box)

---

