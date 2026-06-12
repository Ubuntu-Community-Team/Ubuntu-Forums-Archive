---
title: "Where did my Compiz &quot;Advanced&quot; settings go ?"
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by High_Yield on 2008-01-17
Hi-

In my 32 bit version of Gutsy, I had an "Advanced Settings" menu item which allowed me to change all the detailed Compiz options.  Now that I have a fresh install of the 64 bit version - I do not see such a thing but really want it back.

Any ideas ?

Thanks - B

---

### Post by lian1238 on 2008-01-17
Can you try running (Alt+F2) ccsm?

---

### Post by High_Yield on 2008-01-17
> **lian1238 said:**
> Can you try running (Alt+F2) ccsm?

Well, I tried but the system said it couldn't find the file.

So, I searched for anything ccsm and found only two files.
ccsm.desktop
ccsm.png

both in usr/share/app-install...

The funny thing is that compiz seems to work great ;) - just no settings manager ;(

Any other thoughts ?

---

### Post by Yellow Pasque on 2008-01-17
Try:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by High_Yield on 2008-01-17
> **Temüjin said:**
> Try:
```
sudo apt-get install compizconfig-settings-manager
```

Thank you - a one liner and worked instantly.  Even added the menu item to the main menu.

Should I post the fact that it does not install as a bug or something ????
It installed fine in 32 bit land.

- B

---

### Post by Yellow Pasque on 2008-01-17
You're Welcome. I don't think it's a bug, the package just doesn't come pre-installed. Do you remember how you got that package installed on 32bit or was it actually pre-installed from a fresh Ubuntu install?

---

### Post by High_Yield on 2008-01-17
Well, as you can tell I'm somewhat of a noob so I HIGHLY doubt at the time I went and apt-got anything.

I just remember going into the APPEARANCE options and making changes.

Sorry I can;t be of more assistance but as best I can remember - compiz and its detailed settings manager were there in full by default.

Regards and HTH - B

---

### Post by lian1238 on 2008-01-18
Hehe, I like that. "apt-got". :)
In Ubuntu 7.10, compiz and the settings manager comes pre-installed. Well, at least in 32-bit.

---

### Post by andrewski on 2008-06-11
No, it's part of Universe: [http://packages.ubuntu.com/gutsy/compizconfig-settings-manager](http://packages.ubuntu.com/gutsy/compizconfig-settings-manager).

---

