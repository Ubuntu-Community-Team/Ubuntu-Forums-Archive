---
title: "Trying to download some software, Wine won't let me"
date: 2012-01-21
forum: Wine
---

### Post by S Man on 2012-01-21
Hey guys you probably get this a lot. I'm trying to download some software from Etrade with Wine and this is what I get: The file '/tmp/ETRADE TT_TRADER 7.9.4 OneClick.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I've tried reading up on it but I don't know how to make it executable.

---

### Post by sudodus on 2012-01-21
Have you installed wine? In that case, try from terminal
```
wine '/tmp/ETRADE TT_TRADER 7.9.4 OneClick.exe'
```

---

### Post by S Man on 2012-01-21
Says "CreateProcess Failed"

It was a good idea though, it looked like it was going to work at first.

---

### Post by howefield on 2012-01-21
Thread moved to the "*Wine*" forum.

---

### Post by S Man on 2012-01-21
Thank you for moving it to the proper place.

---

### Post by sudodus on 2012-01-21
> **S Man said:**
> Says "CreateProcess Failed"

It was a good idea though, it looked like it was going to work at first.
It is only a small fraction of all Windows programs that actually run under wine. Sometimes the installer works, but the program itself won't work, sometimes not even the installer works.

---

### Post by S Man on 2012-01-21
> **sudodus said:**
> It is one a small fraction of all Windows programs that actually run under wine. Sometimes the installer works, but the program itself won't work, sometimes not even the installer works.

Anything else I can do to get the program working? Or is this a dud and try finding something else?

---

### Post by sudodus on 2012-01-21
> **S Man said:**
> Anything else I can do to get the program working? Or is this a dud and try finding something else?

1. Dual boot windows and ubuntu

2. Run windows in a virtual machine for example VirtualBox. This  way you need not reboot to run the windows-specific programs.

---

### Post by S Man on 2012-01-21
> **sudodus said:**
> 


1. Dual boot windows and ubuntu

No idea how to do that

2. Run windows in a virtual machine for example VirtualBox. This  way you need not reboot to run the windows-specific programs.

I've tried doing it before but failed spectacularly

---

### Post by sudodus on 2012-01-21
> **S Man said:**
> I've tried doing it before but failed spectacularly
There are several current threads about it in the Ubuntu Forums, where you will find good tips. With a little help it is really not that difficult either way.

---

### Post by snowpine on 2012-01-21
First copy the .exe from /tmp (a system folder for temporary files, your user does not have rights to this folder and therefore cannot specify the file as executable) to your /home. 

Then you can make it executable by right-clicking, choosing Properties, and then Permissions. You should see the check box for "run as executable" (or something like that).

I do not see your app listed in the winehq.org app database so there is no guarantee it will run well under wine. :(

---

