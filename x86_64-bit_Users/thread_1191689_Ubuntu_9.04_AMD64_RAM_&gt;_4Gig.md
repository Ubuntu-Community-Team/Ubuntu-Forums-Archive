---
title: "Ubuntu 9.04 AMD64 RAM &gt; 4Gig"
date: 2009-06-19
forum: x86 64-bit Users
---

### Post by tmwhitm on 2009-06-19
Hello,

Just looking to see if anyone had any insight as to why my Ubuntu 64-bit installation is not recognizing any memory over 4Gig.  Ubuntu is only reporting 3.5Gig when I have 8Gig installed.  I am running a Dell Dimension 5100 with the latest BIOS, (A03) and the BIOS is reporting 8Gig installed.  I have downloaded the installation twice and ran the checksum to confirm an accurate version.  Ubuntu reports that it is running the 64-bit version and for grins and giggles, I tried to install a 32-bit version of Virtualbox that failed.  I am pretty confident that I have a legitimate 64-bit version of Ubuntu yet it does not see any RAM over 3.5Gig.  Any insight or direction would be greatly appreciated.  Thank you in advance.

Tom

---

### Post by artsci2 on 2009-06-19
If you upgraded the laptop memory try removing and replacing the memory. I had a module not quite seated once and it only showed half the installed mem. After reseating, all the mem showed up.

---

### Post by m_duck on 2009-06-19
Try running the following from the terminal:```
uname -m
```If it is 64-bit, the output should be something to do with 64, ie x86_64. If it is definitely 64-bit I've no idea I'm afraid.

---

### Post by automaton26 on 2009-06-19
I googled your PC make/model, and the maximum memory is always quoted as 4Gb.

That machine is a few years old, and so it may not have been designed to support modules that big - possibly because they didn't exist, or weren't common at the time.

I've seen BIOSes before that can successfully report future modules, but still cannot make the memory accessible to the OS.

---

### Post by tmwhitm on 2009-06-19
The Dimension 5100 is a tower PC.  I have run the uname -m option and it did show the system using the 64-bit version.  I am going to try and re-seat the memory.  Both great suggestions, thank you.

---

### Post by tmwhitm on 2009-06-19
I did see that the model in some locations listed only a 4Gig max.  I bought the memory from crucial.com and they indicated I could install 8Gig.  When the BIOS reported the full 8Gig, I thought I was all set.  Unfortunately, I think you are going to be correct that the system just cannot hand more than 4Gig to the OS.

---

### Post by m_duck on 2009-06-19
It does seem so unfortunately - a quick google brought up [this](http://www.memoryx.net/dedi51me.html) which says "Maximum Memory 4GB".

---

### Post by Yellow Pasque on 2009-06-19
> I bought the memory from crucial.com and they indicated I could install 8Gig.
The cynic in me L'd his AO at this statement.

---

### Post by sanderj on 2009-06-19
> **tmwhitm said:**
> I did see that the model in some locations listed only a 4Gig max.  I bought the memory from crucial.com and they indicated I could install 8Gig.  When the BIOS reported the full 8Gig, I thought I was all set.  Unfortunately, I think you are going to be correct that the system just cannot hand more than 4Gig to the OS.

Yep, see Dell's info here: [http://support.dell.com/support/edocs/systems/dim5100/en/sm/specs1.htm#wp1052310](http://support.dell.com/support/edocs/systems/dim5100/en/sm/specs1.htm#wp1052310)

---

