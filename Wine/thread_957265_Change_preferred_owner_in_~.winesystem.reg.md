---
title: "Change preferred owner in ~/.wine/system.reg"
date: 2008-10-24
forum: Wine
---

### Post by sundaresanmani on 2008-10-24
I installed ubuntu 8.10 and wine.when i open msoffice application(MSoffice 2000) i get this msg Change preferred owner in ~/.wine/system.reg.

Can any one help me.

Thanks in advance.

---

### Post by michiel33 on 2008-12-26
I get the same error. I edited that file (~/.wine/system.reg) to put in my name. But each time I start MS Word, the same error reappears. The system.reg file gets *overwritten* with the text:

[Software\\Microsoft\\Windows\\CurrentVersion] 1230288575
"CommonFilesDir"="C:\\Program Files\\Common Files"
"FirstInstallDateTime"=hex:21,81,7c,23
"ProductId"="12345-oem-0000001-54321"
"ProgramFilesDir"="C:\\Program Files"
"ProgramFilesPath"=str(2):"%ProgramFiles%"
"RegisteredOrganization"="Change preferred organization in ~/.wine/system.reg"
"RegisteredOwner"="Change preferred owner in ~/.wine/system.reg"



> **sundaresanmani said:**
> I installed ubuntu 8.10 and wine.when i open msoffice application(MSoffice 2000) i get this msg Change preferred owner in ~/.wine/system.reg.

Can any one help me.

Thanks in advance.

---

### Post by JoshuaJamZ on 2009-05-07
You need to change it here:

```
[Software\\Microsoft\\Windows NT\\CurrentVersion] 1240886117
"CSDVersion"="Service Pack 2"
"CurrentBuildNumber"="2600"
"CurrentType"="Uniprocessor Free"
"CurrentVersion"="5.1"
"RegisteredOrganization"="Heliopolis"
"RegisteredOwner"="JoshuaJamZ"
"SystemRoot"="C:\\windows"

```

There are two instances in ~/.wine/system.reg

---

### Post by cogadh on 2009-05-07
If you are using a current version of Wine, you don't have to "hack" the registry to do this. Just run winecfg and go to the "About" tab. You can enter your user information there. Also, next time check the date of a post before you respond, this thread is well past its expiration date.

---

### Post by JoshuaJamZ on 2009-05-07
I realized this was an old thread, however I thought it would be nice to post the information for the next person who might stumble upon this... that seems to be the idea here, to share information... this at least brings this thread to a point... and my current version 1.0.1-0ubuntu6 does not have an entry field in the about section.

---

### Post by cogadh on 2009-05-07
1.0.1 is not the current version of Wine, it is the *stable* version. The current version is 1.1.20 and the About tab has had this functionality for the last few versions prior to it.

---

### Post by PADSIEMENS on 2009-06-09
I, for one, am glad that the full technical information was here. I accidentally moved some Registry entries from WINE to a real Windows system, and was wondering why the "Change preferred organization..." string was appearing in IE. No "winecfg" is available here.

---

