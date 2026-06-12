---
title: "XSANE crashes after installing Unified Driver from Samsung disk"
date: 2008-12-16
forum: x86 64-bit Users
---

### Post by Ziv Kohav on 2008-12-16
Ubuntu 8.10, just did a clean install on AMD64. Connected a SAMSUNG SCX-4500 and installed the Unified Driver. The printer works well but XSANE crashes when I start it. Before I installed the Unified Driver XSANE opened and said there are no connected devices. Now a box appears for 2 seconds and then it disappears and nothing happens. The SAMSUNG configurator doesn't see the scanner. 
I'd appreciate your suggestions.
Thanks,
Ziv

---

### Post by Sef on 2008-12-16
> Connected a SAMSUNG SCX-4500 and installed the Unified Driver

1) Did you check the SCX-4500 and see if it worked before you installed the Unified Driver?

2) Have you tried uninstalling the drivers that you downloaded?

3) Can you provide a link from where you got the drivers from.

---

### Post by Ziv Kohav on 2008-12-17
1. Yes, I ran XSANE before I installed the Unified Driver- it ran ok, but didn't identify any connected scanners. The printer printed fine, just with a generic driver.
2. I didn't try it this time, but I tried it many times before I reinstalled Ubuntu, and it didn't change. In fact, XSANE kept on crashing after the first time I installed the Unified Driver, even after I uninstalled the driver through the uninstall program.
3. I got the driver from the supplied CD. But I've tried a few times before the new Ubuntu installation to download the driver from the Samsung site and it did the same thing exactly. This is at [http://www.samsung.com/il/support/download/supportDownDetail.do?group=printer&type=printer&subtype=multi_functionprinter&model_nm=SCX-4500%2FXEU&disp_nm=SCX-4500&language=&cate_type=all&mType=DR&dType=D&vType=R&cttID=2044297&prd_ia_cd=06010300](http://www.samsung.com/il/support/download/supportDownDetail.do?group=printer&type=printer&subtype=multi_functionprinter&model_nm=SCX-4500%2FXEU&disp_nm=SCX-4500&language=&cate_type=all&mType=DR&dType=D&vType=R&cttID=2044297&prd_ia_cd=06010300)

---

### Post by Ziv Kohav on 2008-12-17
I now uninstalled it, downloaded (I think) the same file from Samsung's UK site and installed it but the problem remains. Is there any general problem with the Samsung driver and XSANE that anyone knows of (and preferably knows how to fix)?

---

### Post by Dustout on 2009-05-28
I have also attempted to install the samsung universal print drivers and i would strongly advise against it as it leaves quite a mess in your applications bar. However as for getting the scanner working i am still troubleshooting :(

---

### Post by shazbut on 2009-05-29
Have you tried the repos made by helpful forum member tweedledee, [here]("http://ubuntuforums.org/showthread.php?t=341621")?  I just used the method decribed in section IId to get the scan driver working on my Xerox WC3119 (rebadged SCX-4200).  Much easier than a manual install, and you don't end up with a mess of configurator icons littering the desktop, or busted permissions all through your filesystem.

---

