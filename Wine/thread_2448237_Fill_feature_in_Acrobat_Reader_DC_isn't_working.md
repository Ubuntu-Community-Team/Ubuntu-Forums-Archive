---
title: "Fill feature in Acrobat Reader DC isn't working"
date: 2020-08-04
forum: Wine
---

### Post by itamarm2 on 2020-08-04
Hi,

I have follow those [simple instructions]("https://linuxconfig.org/how-to-install-adobe-acrobat-reader-dc-wine-on-ubuntu-20-04-focal-fossa-linux") to install acrobat reader on my Ubuntu 20.04.1 LTS
acrobat works but the right menu is not showing the labels of the icons. 
[ATTACH=CONFIG]286604[/ATTACH]
when I choose the fill function its showing a blank page:
[ATTACH=CONFIG]286605[/ATTACH]
I have encounter same behavior (blank page / blank window) on additional application which not uses wine (the app is dialer-app - I have posted [here]("https://ubuntuforums.org/showthread.php?t=2448235")) but I dont know if its related.

syslog if it helps:
```

ug  4 22:05:57 IMPC01 systemd[1919]: Started Application launched by gnome-shell.
Aug  4 22:05:57 IMPC01 kernel: [ 4094.700320] kauditd_printk_skb: 7 callbacks suppressed
Aug  4 22:05:57 IMPC01 kernel: [ 4094.700321] audit: type=1400 audit(1596567957.424:5140): apparmor="DENIED" operation="open" profile="snap.acrordrdc.acrordrdc" name="/proc/scsi/scsi" pid=9662 comm="wine" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug  4 22:05:57 IMPC01 kernel: [ 4094.703999] audit: type=1326 audit(1596567957.428:5141): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4094.882372] audit: type=1326 audit(1596567957.608:5142): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4094.895125] audit: type=1326 audit(1596567957.620:5143): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4094.908231] audit: type=1326 audit(1596567957.632:5144): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4094.914185] audit: type=1326 audit(1596567957.640:5145): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4095.084422] audit: type=1326 audit(1596567957.812:5146): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4095.137152] audit: type=1326 audit(1596567957.864:5147): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4095.137637] audit: type=1326 audit(1596567957.864:5148): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:05:57 IMPC01 kernel: [ 4095.137747] audit: type=1326 audit(1596567957.864:5149): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:06:02 IMPC01 kernel: [ 4099.943359] kauditd_printk_skb: 80 callbacks suppressed
Aug  4 22:06:02 IMPC01 kernel: [ 4099.943361] audit: type=1326 audit(1596567962.668:5230): auid=1000 uid=1000 gid=1000 ses=3 pid=9665 comm="wineserver" exe="/snap/acrordrdc/8/wine-platform/wine-stable/bin/wineserver" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7f1bc860a069 code=0x50000
Aug  4 22:06:04 IMPC01 acrordrdc_acrordrdc.desktop[9662]: 0009:err:ntdll:NtQueryInformationToken Unhandled Token Information class 11!

```

actually comments doesn't works too and warning window before closing unsaved file doesn't show labels on the buttons 

Please advice

---

### Post by TheFu on 2020-08-05
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=32266](https://appdb.winehq.org/objectManager.php?sClass=version&iId=32266)
Be certain to let adobe know about the problem.

---

### Post by itamarm2 on 2020-08-06
[COLOR=#000000][FONT=&amp].[/FONT][/COLOR]

---

### Post by itamarm2 on 2020-08-06
Thanks TheFu for the link

Seems the issues are already known:
[COLOR=#000000]
"[/COLOR][COLOR=#000000]What does not[/COLOR][COLOR=#000000]Cannot use the signature tool[/COLOR]
[COLOR=#000000]Dialogues and preference screens do not have text[/COLOR]
[COLOR=#000000]Workarounds[/COLOR]
[COLOR=#000000]For the signature it's possible use an image of the signature and then just use the stamp tool to paste it. Not the most secure option but it's a choice[/COLOR]
[COLOR=#000000]Dialogues and preference screens without text can be fixed by installing microsoft fonts, especially the sego* fonts."[/COLOR]

---

### Post by TheFu on 2020-08-06
Would a non-Adobe tool work?  There are a number native Linux PDF tools, like Xournal, which can handle many needs. There are some commercial PDF editors too which will support most things required by a business if the free options don't do what's needed.
[https://alternativeto.net/software/adobe-acrobat/](https://alternativeto.net/software/adobe-acrobat/) - just pick Linux as the OS.  

Long ago, my business needed to edit huge numbers of PDF files. I was able to script the editing so that no GUI tool was needed. The run took days, but that was much better than me spending 6+ months manually.

---

### Post by mastablasta on 2020-08-07
foxit reader could work. it's been a while but some time ago i made some forms, then i decided to remove acrobat (on windows PC) and it read them well when i used it (on win). and they have linux version which should work in the same way.

i use Sumatra pdf reader as portable reader on windows but it could be it doesn't have all functions.

Libre office Draw can edit PDF files and does it quite well. just throwing it out there in case you also need to edit the files. also Master PDF editor, but i haven't tried that one.

---

### Post by TheFu on 2020-08-07
> **mastablasta said:**
>  Libre office Draw can edit PDF files and does it quite well. just throwing it out there in case you also need to edit the files. also Master PDF editor, but i haven't tried that one.

LibreOffice can only modify specific, "nice", PDFs.  There are many that are just scanned images (often TIFF) wrapped in a PDF container which cannot be modified. How a PDF was created matters. Nothing can edit a TIFF PDF in any meaningful way.

---

### Post by scpatl4now on 2020-08-19
I have used Xournal for inserting a signature into a PDF file.  It wasn't that hard to do.  I created a PNG transparent file with my signature and Xournal annotate the PDF and saves it in that format.

---

