---
title: "non booting g3"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by erniewinner on 2006-03-10
hi,

i was looking forward to ubuntu on an old biege g3 mac, but i can't get the live cd or install disk to boot. any help out there please? thanks.

---

### Post by linear on 2006-03-10
The Beige G3 won't boot directly from a Linux disk. You will need to use the method described here:
 
[https://wiki.ubuntu.com/Installation/OldWorldMacs](https://wiki.ubuntu.com/Installation/OldWorldMacs)

---

### Post by erniewinner on 2006-03-10
mmm... that looks a little complex for me. i will give it a go later. is there any info if dapper is going to be an easier mac install? and will it support the biege g3 at all. i  hope so.

---

### Post by stuporglue on 2006-03-10
> mmm... that looks a little complex for me. i will give it a go later. is there any info if dapper is going to be an easier mac install? and will it support the biege g3 at all. i hope so.

I'm pretty sure that it won't be. From the colored iMacs on use a different boot method than the beige and older. The colored ones and newer are refered to as "New World" Macs and are tons easier to get Linux on to. Getting Linux on the beije Macs is a bit of a process. 

I think that even long-time Mac Linux maker Yellow Dog dropped Old World support in their latest version. You could probably still grab Yellow Dog 3, and it shouldn't be too hard to get working.

---

### Post by jdp on 2006-03-10
We can show support for [EMILE](http://emile.sf.net) and maybe someday we'll have a boot loader that works for OldWorld machines.

---

### Post by erniewinner on 2006-03-31
ok i messed with bootx and had various issues... only the one version would unpack. i think a better way of getting bootx to work is using the yellow dog cd that has it on the cd. once bootx is installed i'm assuming i will have no problems? [http://www.terrasoftsolutions.com/support/installation/ydl3.0_guide-single.pdf](http://www.terrasoftsolutions.com/support/installation/ydl3.0_guide-single.pdf) this gives good instructions and the latest bootx. but will i have problems picking and using a different kernal for install? and will ubuntu work ok with the other kernal? i haven't got to try it yet... :-?

---

### Post by erniewinner on 2006-03-31
:cool:  ha! i got yellow dog installed and then understood the basics of what i was doing... then had a go using stuporglues webguide. although i find the link as i saved it to disk. i think it was slightly different to the other guide? anyway i'm happy i've got it installing... but i'm lost on the last step??? what next?;)

---

### Post by erniewinner on 2006-04-02
"Please be aware that you will have to copy the Linux kernel and RAM disk image from /boot on your new Ubuntu installation to the "Linux Kernels" folder in the Macintosh System Folder before you can boot into the newly installed Ubuntu system."

well this is the last step... i booted macos and the linux disk isn't seen! i was hoping to drag and drop it? rather rhan being stuck at the command line. is there anyway to make it seen or by use of another program? :rolleyes: 

thanks.

---

### Post by Yimmy on 2006-04-11
I'm in the same boat.  I followed the instructions for copying the kernel and boot img file on the wiki how to on installing oldworld macs.  It didn't work for me.  So now I have a partially installed ubuntu sitting on a partition that I can't get too.  Is there a place we can download the ubuntu kernel and boot img?  Copying it over seems to be nearly impossible.

James

---

### Post by erniewinner on 2006-04-11
i think you have to use the kernal made by the installation for your machine... i got it going in the end i used the live cd. look here i hope it helps! (but ended up with other issues.)

[http://www.ubuntuforums.org/showthread.php?t=154434](http://www.ubuntuforums.org/showthread.php?t=154434)

---

### Post by Yimmy on 2006-04-11
What were your other issues ... just so I can brace myself?  I've heard other people mention problems, but no specifics.

---

### Post by erniewinner on 2006-04-11
oh nothing major... but i think perhaps pc is the best way to go with ubuntu as faster machines are cheap. my issues were specific to me and what i needed to do:

[http://www.ubuntuforums.org/showthread.php?t=156125](http://www.ubuntuforums.org/showthread.php?t=156125)
[http://www.ubuntuforums.org/showthread.php?t=157437](http://www.ubuntuforums.org/showthread.php?t=157437)

---

### Post by Yimmy on 2006-04-11
I was just wondering.  I've actually got Ubuntu running on an old Inspiron 3800 laptop just fine.  I happen to have this old Powermac 7500 that I'd toyed with in the past.  It's a nice machine really.  It's got a 450mhz G4 upgrade card, 512megs of ram and a 32 meg ATI radeon video card in it.  I've also got a burner and a 120 gig hard drive in it.  So I hate to waste it.  I really just want to turn it into a file server and not really worry about the desktop aspect of it at all.  It would be nice to have as an extra though.

---

### Post by erniewinner on 2006-04-11
sounds like a better spec than mine and more worthwhile. but i'm not sure how ppc support is going... i know it isn't up there with the pc development and what with the new intel macs... i don't know if that'll change things. oldworld macs aren't officially supported but if you get breezy going you've got a good while to use it as far as that release goes. but i don't think anyone here has succsesfully got dapper going??? it's a fun project and if i change my mind, i did get it working in the end... :rolleyes:

---

