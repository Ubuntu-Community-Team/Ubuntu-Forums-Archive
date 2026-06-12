---
title: "dvdrip can't find installed tools?"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tink on 2006-01-25
Hi Guys,

It appears that dvd:rip from multiverse can't find transcode, imagemagick
or anything on my install, really, even though they're all installed.  Has 
anyone else come across this problem?



Cheers,
Tink

---

### Post by Hallavej on 2006-01-26
Yes it is a bug in the 64 bit version. Fortunately it is easy to work around it:
Go to: Edit->Preferences->Miscellaneous option.
And choose "Workaround transcode NPTL bugs"=No
Then it wont do the check that failes. Of course then you have to manually make sure that you have everything installed.

---

### Post by Tink on 2006-01-26
[QUOTE=Hallavej]Yes it is a bug in the 64 bit version. Fortunately it is easy to work around it:
Go to: Edit->Preferences->Miscellaneous option.
And choose "Workaround transcode NPTL bugs"=No
Then it wont do the check that failes. Of course then you have to manually make sure that you have everything installed.[/QUOTE]
Thanks, I'll check that out and post back ... 

An unrelated question:  for some reason my IDE devices don't get
DMA enabled on boot, even though the driver supports it, and I can
manually turn it on ... does ubuntu have an equivalent of rc.local that
you find in other distros?


Cheers,
Tink

---

### Post by Hallavej on 2006-01-26
Have a look at /etc/hdparm.conf
You need to add, eg:

/dev/hdc {
dma = on
}

/dev/hdc is where I have my cdrom. Yours may be different.

---

### Post by Tink on 2006-01-26
[QUOTE=Hallavej]Have a look at /etc/hdparm.conf
You need to add, eg:

/dev/hdc {
dma = on
}

/dev/hdc is where I have my cdrom. Yours may be different.[/QUOTE]
Excellent - that'll be hdc and hdd for me.

The switch **"Workaround transcode NPTL bugs"=No** unfortunately 
makes no difference, dvdrip will refuse to let me do anything.



Cheers,
Tink

---

### Post by Tink on 2006-01-28
Btw ... 
the modifications to hdparm.conf doesn't make a difference, either.

I'll just create a new script in init.d with the approprioate llinks... :/


Cheers,
Tink

---

