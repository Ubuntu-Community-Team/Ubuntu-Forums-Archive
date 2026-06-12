---
title: "wine uninstall list"
date: 2008-04-22
forum: Wine
---

### Post by Tim0miT on 2008-04-22
after uninstalling some wine apps, i find that they remain in the un-install section, how would i go about removing these, even re-installing wine doesnt help, i did read somewhere how to dit it, but i cant remember it and cant find it again...

---

### Post by cogadh on 2008-04-22
You need to manually delete them from Wine's registry files. I'm not on my Linux machine at the moment, so I can't confirm which registry file you need to look in for it, but if you open each registry file with your favorite text editor, it should be relatively easy to find the right entries. Do yourself a favor and make a backup of any file you intend to edit, just in case.

---

### Post by Tim0miT on 2008-04-23
someone tell me what i need to edit please!!

---

### Post by cogadh on 2008-04-23
I did tell you, you'll need to make some effort to find the problem entries yourself. Since I am on my Linux machine now and I am feeling generous, I can tell you that the registry file you'll need to edit is the ~/.wine/system.reg file. You will need to look through that file yourself for the specific uninstall entry that you need to delete. Just look for the section that starts with ```
[Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall]
``` and the specific uninstall entry should be somewhere underneath that.

---

### Post by Tim0miT on 2008-04-23
have u looked at that, theres 1000s of lines...

---

### Post by schtufbox on 2008-04-23
is it so hard to use the search function in your text editor?
Just use it and search for "Windows\\CurrentVersion\\Uninstall"  you'll probably see the entries below that..

---

### Post by cogadh on 2008-04-23
> **Tim0miT said:**
> have u looked at that, theres 1000s of lines...
Of course I've looked at it, but without actually knowing what specific software entries you need to remove and without having installed it myself, I can't look through my registry files to find the entry you need. You are going to have to do some of the work yourself. Welcome to Linux.

EDIT - If you are unwilling to work through the registry files with a text editor, then try using regedit. You should be able to browse the registry to ```
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall
``` and look through all of the keys listed for each installed app to find the one(s) you need to delete.

EDIT2 - If you are unwilling to use regedit as well, then you can just delete your entire .wine directory and start fresh. You will need to configure a new .wine directory and any apps that you had installed will need to be reinstalled.

---

### Post by Tim0miT on 2008-04-24
ok, sorted, thanks alot :guitar:

---

