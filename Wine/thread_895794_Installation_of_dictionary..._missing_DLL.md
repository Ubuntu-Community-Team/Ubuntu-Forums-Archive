---
title: "Installation of dictionary... missing DLL?"
date: 2008-08-20
forum: Wine
---

### Post by smain on 2008-08-20
Hi all
I really need help on this one. I have a dansih-english dictionary which I try to run through wine. But when I do I just get this message:
```
Run-Time error '-2147221166 (80040152)'
Automation error
```

I have also tried running it in the terminal and then I get this output:
```
fixme:ole:OleLoadPictureEx (0xc111f4,2246,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fae8), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x12c110)->(0x12eb68, 0, (nil)), hacked stub.
fixme:ole:OleLoadPictureEx (0xc11ed4,251078,1,{00020400-0000-0000-c000-000000000046},x=0,y=0,f=0,0x32f8f0), partially implemented.
fixme:ole:OleLoadPictureEx (0xc12d1c,4030,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f88c), partially implemented.
fixme:ole:OleLoadPictureEx (0xc17aac,3267,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f4d8), partially implemented.
fixme:ole:OleLoadPictureEx (0xc12d1c,1726,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f85c), partially implemented.
fixme:ole:OleLoadPictureEx (0xc12d1c,1726,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f85c), partially implemented.
fixme:ole:OleLoadPictureEx (0xc12d1c,726944,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f85c), partially implemented.
fixme:ole:OleLoadPictureEx (0xc12d1c,408064,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f85c), partially implemented.
fixme:ole:OleLoadPictureEx (0xc12d1c,203064,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f85c), partially implemented.
fixme:ole:OleLoadPictureEx (0xc12d1c,1548,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f85c), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x16dd90)->(0x1cd318, 0, (nil)), hacked stub.
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\scrrun.dll"
err:ole:create_server class {0d43fe01-f093-11cf-8940-00a0c9054228} not registered
err:ole:CoGetClassObject no class object {0d43fe01-f093-11cf-8940-00a0c9054228} could be created for context 0x5
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}

```

Please someone tell me what to do to get it working

Smain

---

### Post by cmay on 2008-08-20
you have to find that dll on the internet to get it to work.
a dll is a dynamic linked libray which is microsoft specifik.
a dynamic linked libray in unix mac linux is called .so as extension.
it is not sure you can get it to work i think. but no harm in trying.
hope it helps

---

### Post by smain on 2008-08-20
hmm well I found the scrrun.dll, but how do i install it in wine. I have tried to put it in the system, system32, and drive_c folder. also the DLL does not show up in winecfg in the libraries section :confused:... any ideas?

---

### Post by cmay on 2008-08-20
> hmm well I found the scrrun.dll, but how do i install it in wine. I have tried to put it in the system, system32, and drive_c folder. also the DLL does not show up in winecfg in the libraries section ... any ideas? 
its so long i had tried wine as i dont use it. but i thinnk there was a 
option in the menu to add libray or override the ones being used as default.
it must be there you should add the dll.
and the reason i say it might not work is becouse some dll from microsoft i suspect whitout knowing ot for sure is not freely distributable.
try to install the wine utils if you have not done so far yet.

hope it helps.

---

### Post by smain on 2008-08-21
by wine-utils do you mean winetricks?... I have tried to add/override... But I have to choose which file to override... and there i s no built-in version of scrrun.dll so i can't override it :S

---

### Post by qwertymn on 2008-08-21
you just have to put that scrrun.dll in ~/.wine/drive_c/windows/system32/

No need to override anything , as wine does not implement this dll. What you have to do though is register the dll as well:

'regsvr32 scrrun'

---

### Post by smain on 2008-08-21
where do i run that command?

[EDIT]: I found out... but now I get a error message saying something about the microsoft jet database...

---

### Post by chrnobel on 2008-09-01
Hej.

I assume that the dictionary you are speaking about is Politikens ordbog.

I copied all the ekstra dll's from the System32 directory on the CD to the System32 directory.

Also you need to change permissions on the files in the Polob32\EngDanEng directory, so that you also can write to the egneord.mdb

This works for me.

Regards
Christian

---

