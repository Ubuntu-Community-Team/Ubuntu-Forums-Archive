---
title: "Wine Updating DirectX, Adding Winetricks Override, And Adding Keys To Wine Registry"
date: 2014-03-08
forum: Wine
---

### Post by ryan61 on 2014-03-08
Hello Forum! I have made an old thread about how to install Final Fantasy XIV. I have a problem where I cannot update DirectX. I also have been reading up about it. I need to add Overrides and Keys to the Registry. I unfortunately don't know how to do that. I need to know how to Update DirectX, Put in overrides, and Add keys to the registry.

Thank You For You Time.
ryan61:D

---

### Post by MikeCyber on 2014-03-09
I would not go beyond DX 9c and use regedit as on Windows. DX10/11 are not yet as good implemented.

---

### Post by ryan61 on 2014-03-09
Okay, I need to put these items in to my this windows programs work but I do not know how.

[COLOR=#000000][FONT=bitstream vera sans]Required winetricks overrides:[/FONT][/COLOR]

[LIST]
[*]d3dx9
[*]devenum
[*]ie8
[*]quartz
[*]wininet
[*]winhttp
[*]xact_jun2010
[*]wmp10
[/LIST]
[COLOR=#000000][FONT=bitstream vera sans]Add these keys to registry:[/FONT][/COLOR]
[INDENT][HKEY_CLASSES_ROOT\CLSID\{7D8AA343-6E63-4663-BE90-6B80F66540A3}]
@="VMR ImageSync"

[HKEY_CLASSES_ROOT\CLSID\{7D8AA343-6E63-4663-BE90-6B80F66540A3}\InprocServer32]
@="C:\\WINDOWS\\system32\\quartz.dll"
"ThreadingModel"="Both"

[HKEY_CLASSES_ROOT\CLSID\{99D54F63-1A69-41AE-AA4D-C976EB3F0713}]
@="VMR Allocator Presenter"

[HKEY_CLASSES_ROOT\CLSID\{99D54F63-1A69-41AE-AA4D-C976EB3F0713}\InprocServer32]
@="C:\\WINDOWS\\system32\\quartz.dll"
"ThreadingModel"="Both"


[SIZE=2][FONT=arial]Thanks for your time! [/FONT][/SIZE][/INDENT]

---

### Post by MikeCyber on 2014-03-09
How about google winetricks and read the wiki? Click twice ok in winetricks to select above dlls to install. Dead simple and same for the registry as described in the wine app database (the link was given to you previously).
Good luck

---

### Post by sffvba[e0rt on 2014-03-09
*Thread moved to **Wine**.*

---

