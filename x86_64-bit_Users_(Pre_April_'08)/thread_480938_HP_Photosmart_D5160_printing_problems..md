---
title: "HP Photosmart D5160 printing problems."
date: 2007-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmail524 on 2007-06-21
Hello,  I have a Hewlett-Packard Photosmart D5160 printer that no longer prints correctly.  It did work fine for about 2 weeks, but now it est prints garbage.  The output that I am getting looks like the printer's control language.

     $!PS-Adobe-3.0
                                 %%Title: PPR Test Page
                                                                            %%DocumentNeededResources: font Helvetica
                                                                                                                                                                   %%F

I have tried removing my printers and re-installing them.  Also, I tried installing the latest version of HPLIP (Verison 1.7.4a).  I have combed through my settings in printer's control panel, HP Device Manager and CUPS.  I'm just not sure what happened.

I have another HP Printer (DeskJet 6122) and it is still working properly.  No problems with that printer.  I'm not sure what to try next.  Any help is greatly appreciated.  Thank you.

(Ubuntu Feisty 7.04 AMD64, HPLIP 1.7.4a)

---

### Post by tgalati4 on 2007-06-21
Try a different cable.  It could be that the printer's rendering engine quit.  HP's are known to be wonky.  Do a google search on your model number and you will see all sorts of issues.

You could remove CUPS (via synaptic) and then reinstall.  It may be a freak software problem, but I would put money on the hardware crapping out.

It's unfortunate that the printer manufacturer with the best Linux support also puts out the crappiest printers quality wise.

---

### Post by jmail524 on 2007-06-22
tgalati4, thanks for the reply.

I took it upon your suggestion to swap out the USB cable, unfortunately it did not make any difference.  I also hooked up the printer to a WIndows XP machine and the printer seems to function properly.  Also, I hooked up the printer to my laptop which is running Ubuntu Feisty 7.04 (i386) and it seems to function properly on that machine.  I have tried uninstalling and reinstalling CUPS, but to no avail, the problem continues.  I am wondering if I had gotten an update for CUPS that may have broken support for this printer.  I am going to see if I can possibly back-up CUPS to a previous version. (I am not sure what version I was running when it was working properly or if it has any bering on the problem.)

(Hmm... It's kind of funny that the latest version of HPLIP and CUPS work on my i386 laptop but not my AMD64 desktop.)

Thanks.

---

### Post by morequarky on 2007-08-16
I also have this D5160 printer.  

My problem is it isn't listed in the HP CUPS supported drivers.  So which driver should I choose.

Thanks.

---

