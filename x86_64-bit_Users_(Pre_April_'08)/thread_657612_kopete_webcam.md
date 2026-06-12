---
title: "kopete webcam"
date: 2008-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by TWFJR on 2008-01-03
My Logitech 4000 webcam is not recognized by kopete.  Instead my HDTV card is the recognized, default, video source.  No webcam choice in kopete configure.  How does one get kopete to recognize the webcam? I am running 7.10 64 bit/32 bit emulation for Firefox. Using IcedTea-java7. Tried Java 6, not a solution. Tried:  tom@ubuntufiechtl:/dev$ sudo chmod 666 /dev/video0
tom@ubuntufiechtl:/dev$ sudo chmod 666 /dev/video1
tom@ubuntufiechtl:/dev$

Above commands did nothing to resolve cam not working in kopete. Ekiga still works with cam. Cam is Logitech, USB device, 4000 model.

Did noting either to resolve webcam problem. Nor did updating IcedTea.

tom@ubuntufiechtl:/dev$ ls -la /dev/video*

crw-rw---- 1 root video 81, 0 2007-12-19 10:52 /dev/video0

crw-rw---- 1 root video 81, 1 2007-12-28 12:54 /dev/video1

tom@ubuntufiechtl:/dev$ id

uid=1000(tom) gid=1000(tom) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(tom)

Any ideas as to getting the webcam working?

---

