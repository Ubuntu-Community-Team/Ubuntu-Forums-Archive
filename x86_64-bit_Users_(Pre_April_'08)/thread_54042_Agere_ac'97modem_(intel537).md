---
title: "Agere ac'97modem (intel537)"
date: 2005-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by eolo999 on 2005-08-03
hi guys,
someone can help me with ac'97 "modem". I receive this with "lspci":

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 80)

so my system recognize the chip but still i don't have the "modem" working...
help.

---

### Post by heimo on 2005-08-03
Just links:

[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)
[http://www.linmodems.org/](http://www.linmodems.org/)

---

### Post by eolo999 on 2005-08-03
Thanks Heimo,
the only probl. is I have amd 64 kernel so i can't use packages from debian!!! Now i'll try to compile the amd 64 version form smart link source....

only i386!!!!
i receive errors:
/usr/bin/ld: warning: i386 architecture of input file `dsplibs.o' is incompatible with i386:x86-64 output

---

