---
title: "New user, Gutsy frustrations"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by the_toaster on 2007-10-21
Hi,

I have recently decided to try linux again, having dual booted fedora core 5 a while ago.  I downloaded the 64bit ISO but no matter what i do i get  the following error:


Kernel alive
kernel direct mapping tables up to 10000000@8000-d000

I have browsed the forums for an answer, but nothing I have tried has worked. Below is the list of fixes I have tried:

1)  ran checksum checker on the ISO file.  it was fine.
2) put the disk in a friends computer, it started fine.
3) hit F6 at the first screen, and removed the word "splash"
4) hit F6 at the first screen, and added "nosplash noapic nolapic" to the end
5) same as #4 but with slashed between the words and no spaces
6) (this should be #3) inserted my windows disk and fixed the MBR, it was bad, now is good

These are all the solutions i could find, but none of them seemed to work.
My system is a:

AMD 3800 X2
ASUS M2N-E mobo
Nvidia gForce 7600gs (note 2 dvi outputs)
2 x512 Corsair DDR2 800 memory
1 80GB Western Digital HDD
Viewsonic Optiquest LCD plugged in through a VGA/DVI adapter

I appreciate your help!

P.S. I am downloading the 32bit ISO just in case

---

### Post by John.Michael.Kane on 2007-10-21
> **the_toaster said:**
> Hi,

I have recently decided to try linux again, having dual booted fedora core 5 a while ago.  I downloaded the 64bit ISO but no matter what i do i get  the following error:


Kernel alive
kernel direct mapping tables up to 10000000@8000-d000

I have browsed the forums for an answer, but nothing I have tried has worked. Below is the list of fixes I have tried:

1)  ran checksum checker on the ISO file.  it was fine.
2) put the disk in a friends computer, it started fine.
3) hit F6 at the first screen, and removed the word "splash"
4) hit F6 at the first screen, and added "nosplash noapic nolapic" to the end
5) same as #4 but with slashed between the words and no spaces
6) (this should be #3) inserted my windows disk and fixed the MBR, it was bad, now is good

These are all the solutions i could find, but none of them seemed to work.
My system is a:

AMD 3800 X2
ASUS M2N-E mobo
Nvidia gForce 7600gs (note 2 dvi outputs)
2 x512 Corsair DDR2 800 memory
1 80GB Western Digital HDD
Viewsonic Optiquest LCD plugged in through a VGA/DVI adapter

I appreciate your help!

P.S. I am downloading the 32bit ISO just in case
Kernel alive
kernel direct mapping tables up to 10000000@8000-d000

This is usually shown for a few seconds before the grub, and the machine boot. This is normal under 64bit. Your machine should boot as normal, and leave you at the gdm where you should be able to type in your name/pass

Unless your machine experiencing any issues during boot or other problems the kernel line is a non issue.

---

### Post by the_toaster on 2007-10-21
What happens on my system is that it never exits that screen.  I should have said that in my original post.  I tried leaving it go to see if it was just "thinking", but after 4 hours the screen had never changed.

---

### Post by Cappy on 2007-10-21
The ```
noapic nolapic nosplash
```
added onto the end (without removing anything!) is the fix for this problem (the noapic nolapic specifically). I use this myself for the same problem. I know you already tried it but you should try again.

---

### Post by the_toaster on 2007-10-22
I will try that again as soon as my 32bit ISO finishes downloading.

---

### Post by ACLerok on 2007-10-23
> **Cappy said:**
> The ```
noapic nolapic nosplash
```
added onto the end (without removing anything!) is the fix for this problem (the noapic nolapic specifically). I use this myself for the same problem. I know you already tried it but you should try again.

This didn't work for me when I tried it, I use acpi_use_timer_override, or acpi=off.  Both work for me.  Don't use them at the same time, however.

---

### Post by jonah1980 on 2007-11-04
i also get this kernel alive mapping tables thing appearing, are you sure it's normal to see this? seems a bit odd...

---

### Post by netbandit on 2007-11-04
My money is on this solution:

add this to the boot options:
acpi=off

-nb

---

### Post by nss0000 on 2007-11-04
It's pretty well known that the ASUS_m2nx mobos (like mine) display various "holes" in various Linux_version support. YMMV.

---

### Post by scotthammy on 2007-11-04
I Also have this screen show on my Asus a6km for about 3 sec on booting up..


Apart from that, Gutsy 64bit ROCKS!

---

### Post by ncarty97 on 2008-02-17
Hello everyone.  I'm running into this problem as well.  Get the "Kernal Alive", then "Kernal direct mapping..."

Then it waits for a little bit and reboots.

Here is my system:

Intel Core2Duo E8400 @ 3.0Ghz
Gigabyte EP35C-DS3R motherboard
2GB Corsair DDR2-800 (2 x1GB in dual channel mode)
160GB 8MB Cache Western Digital SATA 300
eVGA e-GeForce 880GT 512MB DDR3
Logitech Bluetooth Wave Keyboard and Mouse.

I am using the 64bit version (which I was a bit confused, I started from the ubuntu.com page, it says 64 bit is for Intel and AMD, but the actual iso file is labeled amd64)

I have tried the following fixes:

1) ACPI=off
2) removed 'splash' for the boot options
3) replaced splash with 'nosplash noapic nolapic'
4) acpi_use_timer_override

Always the same result.  Any help would be appreciated.

Thanks,

Nate

---

### Post by scotthammy on 2008-02-17
Hi Nate,

What model laptop are you running? Maybe your system is 32bit and not 64bit.

try donwloading the 32bit ISO

---

### Post by ncarty97 on 2008-02-17
I'm not running it on a laptop.  It's a desktop and it's defintely 64 bit, it's a Core Duo E8400.

Does the 64 bit only work on AMD 64 bit processors or something?

---

### Post by scotthammy on 2008-02-17
Hey, No its for intel as well, tho I have a AMD64 bit. never used intel.

---

### Post by ncarty97 on 2008-02-17
Well I did try the x86 version as well.  At first it was ok.  I did it more to see if it was a 64bit issue or an Ubuntu issue.  I am unsure of the results though.

I already had the regular x86 cd burned from a laptop installation I attempted a few weeks ago (didn't have 256MB ram though and had to go with Xubuntu).  It seemed to go well at first, but a screen popped up saying that it couldn't determine my video card and was using the basic settings.  That was fine, so I clicked OK.  Then it hung up and eventually rebooted without ever loading the LiveCD system.

I tried it again but this time tried install with safe graphics.  That got Ubuntu to load at least.  I was going to install it, but then decided if I can't do the 64bit, it's really not worth the bother. I don't feel like hamstringing my machine.  

If anyone has any suggestions how to get the 64bit running, I would be appreciative.

---

### Post by ncarty97 on 2008-02-18
Anyone?!?

---

### Post by Yellow Pasque on 2008-02-18
Have you tried the alternate install CD?
[http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-amd64.iso](http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-amd64.iso)

---

### Post by ncarty97 on 2008-02-18
yes, I did try that as well and received the same Linux kernal, etc. then reboot.

Is there a place to submit bugs like this since it doesn't seem any of the normal fixes worked?

---

### Post by ncarty97 on 2008-02-19
I hate to keep bumping threads, but I would appreciate any help!

---

### Post by jblackthorne on 2008-02-19
To address both posters, the problem is most likely the Nvidia graphics controller.  To be sure, type:

lspci -vv

On my machine, very similar to yours, address 01:00.0 is:

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])

There is a great deal of information out there about this issue.  Though, to summarize, Nvidia does not support all interrogation commands.  Hence, the error you see.  The good news is that if this is in fact your Nvidia chipset, then there is nothing to worry about and you may safely disregard the message.  Hopefully this issue will be addressed soon though.  It is rather disconcerting indeed.

Hope this helps.

P.S.

I highly recommend putting all the ACPI settings back.  Changing those was unnecessary and actually hurts a number of Gutsy's most valuable features.

---

### Post by ncarty97 on 2008-02-20
Thanks!  I'll try that when I get home tonight.

---

### Post by ncarty97 on 2008-02-20
Well, that didn't help, but I went ahead and installed by booting under the safe graphics mode.  I have basic functionality (doing the 32bit version for now) and will look to upgrade the video drivers this weekend when I have more time.

---

### Post by lonesomecrow on 2008-02-21
I think you dont have to do the "noapic" or "nolapic", on my system (DFI LANParty Expert, AMD64 X2 3800+) I only add "no" before the "splash". If you're booting the live CD, you can do this by highlighting the Start Ubuntu option, then press F6 and with the arrow keys move the cursor back to just right behind "splash" and type "no" (without quotes of course) so that it reads "nosplash" and press enter. I hope this helps you, as it did to me. Dont forget to let us know if it does!!

---

### Post by Kalus on 2008-02-22
Hello, I am i complete Linux newb and i am experiencing the same problems trying to install Linux (Gutsy Gibbon 7.10 and also Fiesty Fawn 7.04)!!

the problem initially started with v7.10 and i was recieving a - Unable to allocate resources - message, followed by computer inactivity. I read that this was a common issue with 7.10 and was recommended to try and install 7.04 to solve.

I am now recieving the same error - Kernal Alive  - followed by the other line (cant remember exactly but it the same as the 1st poster).

tried the;

Boot: live acpi=off thing and i had no luck.

i wanted to try and remove "splash" but im unclear as to what this actually means. Where do i remove it from? 

Thanks in Advance. Kalus



*edit* on further inspection this is answered above.. ;)

---

### Post by Kalus on 2008-02-22
nospash worked and fiesty fawn is now up and running. will try the same on the gutsy gibbon install. thanks for support !

---

### Post by Lucas32 on 2008-02-22
I managed to boot and install Gutsy 64bit on my Intel Core Duo E6750 by deleting the 'splash'  and 'quiet' part from the kernel line of Grub.  Nevertheless, the problem is back and no fix works consistently.  None of the previously mentioned fixes help.   The only one that seems to work is the 'nosplash' one but even that only works about 1 out of 5 times.  I tried to follow the boot messages to determine when things go sour and I have only been able to point point it to a line that starts out with "I/O scheduler...".   In fact, there are about 4 or 5 lines that begin with "i/o scheduler" but the system reboots itself about the 4th or 5th one.   If the computer doesn't reboot itself at the point than ubuntu ends up starting up successfully.
It seems that the successes and the failures are almost random, but I'm sure there's a method to this madness.   

**For reference, my computer is as such**:
intel core 2 duo e6750 processor
ati HD3870 pci-e video card
gigabyte GA-P35-DS3L motherboard
4GB RAM

---

### Post by audacity on 2008-04-24
Hey Lucas, 
    I had a similar problem, was able to install, but on reboot got the grand shut-out. Try removing splash and quiet, and adding vga=771 or some other mode. You won't see anything on boot, but the login screen should come up after a little while. Found in this thread:
[http://sudan.ubuntuforums.com/showthread.php?t=696795](http://sudan.ubuntuforums.com/showthread.php?t=696795)

---

