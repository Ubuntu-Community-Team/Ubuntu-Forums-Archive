---
title: "Printer Install Brother HL-2040"
date: 2007-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by P3RH4PS on 2007-10-05
Well I found drivers and all but they give me the "Error: Wong architecture 'i386'" message.  Can I force them to work?  I read about this somewhere...  can't remember.  I'm really new to all of this, if you know how can you show me in good detail?

[Here is the Brother printer drivers site.]("http://solutions.brother.com/linux/en_us/index.html")  I went to install the LPR drivers first.  I have no idea what LPR or CUPS are if someone could explain that would be a bonus.

For the Brother HL-2040

Thanks for your time!

---

### Post by dcstar on 2007-10-05
> **P3RH4PS said:**
> Well I found drivers and all but they give me the "Error: Wong architecture 'i386'" message.  Can I force them to work?  I read about this somewhere...  can't remember.  I'm really new to all of this, if you know how can you show me in good detail?

[Here is the Brother printer drivers site.]("http://solutions.brother.com/linux/en_us/index.html")  I went to install the LPR drivers first.  I have no idea what LPR or CUPS are if someone could explain that would be a bonus.

For the Brother HL-2040

Thanks for your time!

Yes, the dpkg command has a "force" option just for this situation:

```
sudo dpkg -i --force-architecture brhl2040lpr-2.0.1-1.i386.deb
sudo dpkg -i --force-architecture cupswrapperHL2040-2.0.1-2.i386.deb
```

LPR is a Linux print device, **C**ommon **U**nix **P**rinter **S**ystem allows control of print jobs etc.

I also have this printer.

---

### Post by P3RH4PS on 2007-10-05
Thanks for the help!

---

