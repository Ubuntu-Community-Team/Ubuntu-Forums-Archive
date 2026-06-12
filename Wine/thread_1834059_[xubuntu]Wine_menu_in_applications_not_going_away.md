---
title: "[xubuntu]Wine menu in applications not going away"
date: 2011-08-27
forum: Wine
---

### Post by WubiAR on 2011-08-27
Hello,

I deleted PlayOnLinux and winetricks but when I go to the applications menu, I see the Wine menu with the following:

Wine > Programs > Microsoft Office > 
Microsoft Excel 2007
Microsoft Word 2007
Microsoft PowerPoint 2007
Microsoft Office Tools > 
...

I installed those Microsoft office programs before but now I want to remove them.How can I delete this menu from my applications bar, and delete all Microsoft office programs?

---

### Post by dino99 on 2011-08-27
the coming 1.3.27 version should fix this.

[http://www.winehq.org/announce/1.3.27](http://www.winehq.org/announce/1.3.27)

should be into ubuntu ppa repo on Monday/Thusday

if you cant wait, then create a new bottle

---

### Post by WubiAR on 2011-08-27
> **dino99 said:**
> the coming 1.3.27 version should fix this.

[http://www.winehq.org/announce/1.3.27](http://www.winehq.org/announce/1.3.27)

should be into ubuntu ppa repo on Monday/Thusday

if you cant wait, then create a new bottle

What do you mean by "creating a new bottle"?

---

### Post by kyletstrand on 2011-08-28
> **WubiAR said:**
> Hello,

I deleted PlayOnLinux and winetricks but when I go to the applications menu, I see the Wine menu with the following:

Wine > Programs > Microsoft Office > 
Microsoft Excel 2007
Microsoft Word 2007
Microsoft PowerPoint 2007
Microsoft Office Tools > 
...

I installed those Microsoft office programs before but now I want to remove them.How can I delete this menu from my applications bar, and delete all Microsoft office programs?

Did you want to remove Wine completely?

If you just deleted winetricks and POL, then you will still need to remove wine as the programs will still be installed in the wine subfolders as well as wine itself.  By deleting those two, you just deleted the front ends that access wine.

```
sudo apt-get remove wine
```

If I misunderstood what you said, just disregard.  I'm tired :-?

---

### Post by dino99 on 2011-08-28
> **WubiAR said:**
> What do you mean by "creating a new bottle"?

[http://wiki.winehq.org/ThirdPartyApplications](http://wiki.winehq.org/ThirdPartyApplications)

bottle: generic word to name either: .wine, .playonlinux, ...

---

### Post by Dlambert on 2011-08-29
Go to your home folder. View Hidden files. Then go to .config/menus/applications-merged/ and delete the wine files you don't need. Then go to ./local/share/applications/wine/ and delete the folders you don't need.


:)

---

### Post by Dlambert on 2011-08-29
Also alacarte is the command to edit menus if I remember

---

### Post by WubiAR on 2011-08-30
> **Dlambert said:**
> Go to your home folder. View Hidden files. Then go to .config/menus/applications-merged/ and delete the wine files you don't need. Then go to ./local/share/applications/wine/ and delete the folders you don't need.


:)

Thank you very much. This worked.

---

### Post by Dlambert on 2011-08-30
Your welcome, please mark this thread as solved

---

