---
title: "The Witcher and The Failing DLL"
date: 2008-10-05
forum: Wine
---

### Post by Sugi on 2008-10-05
I installed The Witcher EE and patch to 1.4 and then ran witcher.exe but I was missing some dlls. So, I download Microsoft.VC80.CRT.zip and extracted it to the The Witcher EE/System. I ran witcher.exe again and it said it was having issues with MSVCR80.dll. So I got a new MSVCR80.dll from dll-download.com or something like that. But now I am getting the following error within the terminal:

SPEC:
Ubuntu Hardy Heron
Wine 1.1.5 Compiled
The Witcher Enhanced Edition
Patch 1.4 English

fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"H:\\.bin\\wine1.1.5_withcer\\drive_c\\Program Files\\The Witcher Enhanced Edition\\System\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"H:\\.bin\\wine1.1.5_withcer\\drive_c\\Program Files\\The Witcher Enhanced Edition\\System\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"H:\\.bin\\wine1.1.5_withcer\\drive_c\\Program Files\\The Witcher Enhanced Edition\\System\\witcher.exe" failed, status c0000142

Thanks,
Sugi

---

### Post by Sugi on 2008-10-07
Bump

---

### Post by Sugi on 2008-10-08
bUMP

---

### Post by david_kt on 2008-10-08
> **Sugi said:**
> I installed The Witcher EE and patch to 1.4 and then ran witcher.exe but I was missing some dlls. So, I download Microsoft.VC80.CRT.zip and extracted it to the The Witcher EE/System. I ran witcher.exe again and it said it was having issues with MSVCR80.dll. So I got a new MSVCR80.dll from dll-download.com or something like that. But now I am getting the following error within the terminal:

SPEC:
Ubuntu Hardy Heron
Wine 1.1.5 Compiled
The Witcher Enhanced Edition
Patch 1.4 English


According to below:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9593](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9593)

You must:

Open terminal and run regedit 

and add the following key and string values: [HKEY_CURRENT_USER\Software\Wine\Direct3D] OffscreenRenderingMode = fbo PixelShaderMode = enabled UseGLSL = enabled VideoMemorySize = 256.

DK

---

### Post by Sugi on 2008-10-08
I have added those reg keys to my wine before posting.
OffscreenRenderingMode = fbo 
PixelShaderMode = enabled 
UseGLSL = enabled 

But I did forget this one.  I kinda doubt it will do anything to help my game, but I will report back in.
VideoMemorySize = 256.

Thanks,
Sugi

---

### Post by Sugi on 2008-10-11
After corrently adding the keys to the regedit, i got a new crash and a new error.

When I start the game, i get the following error. "you must be administrator"  It wants to install some Tages or something.
[http://bugs.winehq.org/show_bug.cgi?id=10264](http://bugs.winehq.org/show_bug.cgi?id=10264)

Is there a workaround for this?

Thanks,
Sugi

---

### Post by david_kt on 2008-10-11
> **Sugi said:**
> After corrently adding the keys to the regedit, i got a new crash and a new error.

When I start the game, i get the following error. "you must be administrator"  It wants to install some Tages or something.
[http://bugs.winehq.org/show_bug.cgi?id=10264](http://bugs.winehq.org/show_bug.cgi?id=10264)

Is there a workaround for this?

Thanks,
Sugi

According to the link you cive, it works on wine 49 only:
```

screenshot from Witcher 1.0 with Wine 0.9.49

I finally runned the game.

1) Install Witcher 1.0 from the CD
2) Install winetricks as mentioned in Comment 17
3) Put d3dx9_35.dll into windows/system32
4) Use (russian) no-cd patch for 1.0

The game runs, even on highest quality (!!!) and looks super-cool. Beside of
the characters. As presented on the screenshot, all characters are represented
as rag dolls. They do not move or animate, and some things, like swords, eyes,
jaws moves independently from those dolls. You can move around, and, look at
the shadow. Shadow is dynamic and animates perfectly, only the real character
is freezed.
```

or at least it will pass the tag installation. You could install many wines at the same time, use wine 49 to make sure it pass installation, and then use latest wine to run etc. What you have to do is see below thread to have multiple wine installed and how to use it:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

DK

---

### Post by Sugi on 2008-10-11
Thanks for the tip, I did see that within appdb.  I guess I will be compiling 49. Thanks and I will keep you updated on my results.

Sugi

---

