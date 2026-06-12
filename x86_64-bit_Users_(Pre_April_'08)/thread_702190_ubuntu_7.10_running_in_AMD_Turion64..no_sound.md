---
title: "ubuntu 7.10 running in AMD Turion64..no sound"
date: 2008-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by fragilelappy on 2008-02-20
i installed ubuntu 7.10 on my notebook with AMD Turion64 processor but have trouble on sound. the speaker cannot produce sound when playing mp3 or wav audio files.though i installed codecs but the phe roblem still exist.
i even tried to install vlc player but no avail.
i suspect the driver for my sound card. by the way mine is a Realtek high definition audio, not sure with the model.
i even tried to download package from here:

[http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs) 

and tried to install it automatically but still no improvement.

should anyone could help me.. greatly appreciated.

thanks a lot.

---

### Post by felker2 on 2008-02-20
Which Ubuntu 7.10 have you installed: the 32-bit or the 64-bit version? You can that check by typing 

```

uname -a

```

on the commandline. If it says something with i386 it's 32-bit, and not 64-bit related and your question is better off in another forum.

---

### Post by fragilelappy on 2008-02-20
here's what i got uname -a command:

Linux fragilelappy 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by felker2 on 2008-02-20
> **fragilelappy said:**
> here's what i got uname -a command:

Linux fragilelappy 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

The "i686" means you're running the plain 32-bit version. Nothing wrong with that, but you're better off asking your question in the mainstream forum.

On 64-bit you would get something like

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

```

Note the "x86_64", meaning 64-bit

---

### Post by fragilelappy on 2008-02-20
oh i see.
thanks.i thought ubuntu 7.10 is only 64bit.

---

### Post by konungursvia on 2008-02-24
Also, try installing the backports for the sound drivers.

---

