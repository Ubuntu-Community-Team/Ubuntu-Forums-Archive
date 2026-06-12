---
title: "Gutsy AMD64 recognizing 4GB of RAM as 3.2GB"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by GumbyX on 2008-03-31
Heyo. I am running into a slight problem after installing 4GB of RAM into my desktop running Gutsy AMD64. For some reason, the system only shows that 3.2GB is installed. After reading some other threads, this should only happen on a 32-bit system. I have checked everything i can think of with no luck.

Output from *free* command:
> gumby@gumby-linux-desktop:/boot$ free
             total       used       free     shared    buffers     cached
Mem:       3355360    1356556    1998804          0      47172     487048
-/+ buffers/cache:     822336    2533024
Swap:      2257092          0    2257092


I am running 2.6.22-14-generic, which I believe might be the problem. but I am not sure. I know its a AMD64 system,  but for some reason the kernel is generic. Do I need the AMD64 kernel (if one exists) or "roll my own"? Can anyone help me get my RAM back?

Note: The system originally had 1GB (512MB X 2) of RAM when I first installed Gutsy. It is has 4GB (1GB X 4). Not sure if that helps any, but thought I would mention it.

---

### Post by fjgaude on 2008-03-31
Your computer is a 64-bit AMD machine, and you are running 64-bit Gutsy, yes.

Your swap file is less than 4Gs but that would only come into play in Sleeping and if you ever run out of RAM.

Your motherboard allocates memory addressess to your video card. How much memory does your video claim to have?

---

### Post by GumbyX on 2008-03-31
> **fjgaude said:**
> Your computer is a 64-bit AMD machine, and you are running 64-bit Gutsy, yes.

Your swap file is less than 4Gs but that would only come into play in Sleeping and if you ever run out of RAM.

Your motherboard allocates memory addressess to your video card. How much memory does your video claim to have?

I am running a ATI PCI-E Video Card that should have 256MB of RAM. The system has an onboard video card that I do not sure, but is only takes 256MB of RAM at a max and I do not have it active (at least that is why my limited, HP BIOS says).

---

### Post by GumbyX on 2008-04-01
....... wha??? :confused:

Anyway:
Anyone got any ideas of whats up with my pc?

Also: Bad color choice, Ubuntuforums. Can't read any of the title threads on the forums pages. : sigh: Looks like I will be waiting till tomorrow for answers since no one will actually be able to SEE my thread.

---

### Post by stefangr1 on 2008-04-01
I believe that this has to do with your IO-board. You can possibly change this in the bios, with an option that has something to do with "remapping".

n.b.: In an almost similar post ([http://ubuntuforums.org/showthread.php?t=741941](http://ubuntuforums.org/showthread.php?t=741941)) I just answered the above, e.g. I think it has to do with your bios.

---

### Post by GumbyX on 2008-04-01
> **stefangr1 said:**
> I believe that this has to do with your IO-board. You can possibly change this in the bios, with an option that has something to do with "remapping".

n.b.: In an almost similar post ([http://ubuntuforums.org/showthread.php?t=741941](http://ubuntuforums.org/showthread.php?t=741941)) I just answered the above, e.g. I think it has to do with your bios.

I will have to take a look at it tonight when I get home . I don't remember seeing an option like when I checked the BIOS, but I wasn't looking for one. Also, the BIOS lists memory at 4096MB.

PS My board is a MSI MS-7184 OEM motherboard for HP Computers. It has a rather restrictive BIOS sadly. Don't know if that info will help or not, but I thought I would mention it since it seems people have this exact problem with this particular board for some reason.

---

### Post by GumbyX on 2008-04-01
: sigh: Checked out the BIOS, no options to remap or anything like that. : sighs: Thanks for the idea, stefangr1, but no luck. :(

I am going to talk with one of my co-workers tomorrow about it. He is more into computer hardware then I am, so me might have an idea. Sadly, he has no linux background, so if its a problem with the kernel, he won't be able to help.

Anyone else have any ideas?

---

### Post by dcstar on 2008-04-01
> **GumbyX said:**
> : sigh: Checked out the BIOS, no options to remap or anything like that. : sighs: Thanks for the idea, stefangr1, but no luck. :(

I am going to talk with one of my co-workers tomorrow about it. He is more into computer hardware then I am, so me might have an idea. Sadly, he has no linux background, so if its a problem with the kernel, he won't be able to help.

Anyone else have any ideas?

Do a full BIOS reset to default, because you added in RAM then it is possible that other motherboard resources are still mapped to address space that are now occupied by RAM - this might changes things.

---

### Post by marrugeek on 2008-04-01
The same happened to me. I have 4gb of RAM and I use Ubuntu 7.10 64 bit. Initially I only saw 3.2 GB of RAM. My motherboard is an Asus P5B Deluxe. I had to tweak an option in the BIOS. The change was the Following:

BIOS SETUP UTILITY -> Advanced -> Chipset -> North Bridge Configuration -> Memory Remap Feature

Setting that to [Enabled] solved the thing.

I hope that helps.

---

### Post by GumbyX on 2008-04-02
> **marrugeek said:**
> The same happened to me. I have 4gb of RAM and I use Ubuntu 7.10 64 bit. Initially I only saw 3.2 GB of RAM. My motherboard is an Asus P5B Deluxe. I had to tweak an option in the BIOS. The change was the Following:

BIOS SETUP UTILITY -> Advanced -> Chipset -> North Bridge Configuration -> Memory Remap Feature

Setting that to [Enabled] solved the thing.

I hope that helps.

As I said before, I can't find an option like that.
> **GumbyX said:**
> : sigh: Checked out the BIOS, no options to remap or anything like that. : sighs: Thanks for the idea, stefangr1, but no luck. :(

Thanks for the help, but my motherboard already shot it down :(

Update: I found a forum post ([http://www.wimsbios.com/phpBB2/topic7226.html](http://www.wimsbios.com/phpBB2/topic7226.html)) that gave an alternative BIOS firmware that *should* work with my board. I might try it if I get desperate enough. Also thinking of emailing HP about it to see if there is any voodoo I have do to get the full RAM access with the current firmware.

---

### Post by GumbyX on 2008-04-02
: Wants to scream out angrily AMT:

Think I found my problem:
[http://linux.derkeiler.com/Mailing-Lists/Fedora/2006-02/msg02498.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2006-02/msg02498.html)

Links says exactly what everyone told me to do (remapping), but with an added piece of info: My board most likely DOES NOT have this feature. Which means that because of HP being stupid as **** and lying about the board specs, I can't get full access to my RAM. 

: Sighs Sadly:
So I just wasted an extra $80+ on RAM I can't even really use.........

Am going to write to HP about this ASAP. For my luck, there is nothing I can do through them. I do have a warranty with Best Buy where I can probably go yell at them until they give up and do something like give me a new machine, but that probably won't happen either. For my luck installing Linux or my own RAM voids my warranty or something stupid like that.

If anyone can confirm this or help me find away around this MB issue, PLEASE help me out

---

