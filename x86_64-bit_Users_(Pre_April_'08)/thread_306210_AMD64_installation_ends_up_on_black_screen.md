---
title: "AMD64 installation ends up on black screen"
date: 2006-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by thebjoern on 2006-11-24
Hi everyone,

I am an absolute newbie to Ubuntu (and Linux in general), have recently for the first time installed Ubuntu on a 32bit system at work, and as I liked it so much decided to install it at home too. 

I got an AMD32 3200+, 1GB RAM, ATI 9800XT system, I downloaded the "64-bit PC (AMD64) desktop CD", burnt a CD image, booted from it, got to the first menu, and chose "start or install ubuntu".

From there it started loading, with the ubunte logo and some progress bar (this logo was black&white however - is it supposed to be coloured?), then after a while it looks like the screen resolution is changed to something else, and the screen goes black, and stays there forever, I can press whatever I want (also tried like ctrl-alt-f4 and lots of other combos) and still nothing happens (also interesting is that the num-lock led status doesnt change at all when I press num-lock).

Unfortunately -like I said before- I dont have any Linux experience really (aside from playing around for like a day or so at work), so I dont really know what to do... but I would really love to install Ubuntu here :( 

Anyone got any ideas on how a newbie can get that going without too much pain/hassle? :confused: 

Thanks!
Bjoern

---

### Post by incubus on 2006-11-24
hey Bjoern,

Would you be willing to try the non-graphical installer? It's pretty much the same thing, but I bet it wouldn't hang up.

By the way, when the screen freezes is the system still working? If you press Num Lock, for example, does the keyboard LED flash?

incubus

---

### Post by thebjoern on 2006-11-25
Hi Incubus,
thanks for your reply.

Yes, I would be willing to try anything, provided a newbie like me can handle it ;)

Like I said, the num-lock key doesnt seem to work anymore, the LED status doesnt change...

thanks!
Bjoern

---

### Post by wonneil on 2006-11-25
I have the exact same problem! i'm a newb to this too.
It works on my desktop but I want to install ubuntu on my laptop which is an acer aspire intel pentium 2.0 GHz.

I have also just tried Mandriver 2007 and that does exactly the same thing, starts loading fine then the screen just goes blank!

Thanks 

Neil

---

### Post by wonneil on 2006-11-25
Update

Mine works in safe graphics mode, what do I need to do now?

Thanks again.

---

### Post by thebjoern on 2006-11-25
For me its actually the same when I try with safe graphics mode... any idea anyone?

---

### Post by John.Michael.Kane on 2006-11-25
The black and white ubuntu splash is a known issue [http://ubuntuforums.org/showthread.php?t=304673](http://ubuntuforums.org/showthread.php?t=304673)

As to the screen goes black issue you can try to install from the alternate text mode cd

Or 

After booting your current install try pressing Ctrl-Alt-F2 this should bring you to a text screen. 

Once your loged in try typing

sudo nano /etc/X11/xorg.conf from here you can scroll down to this section.

Section "Device"
	
Edit this--->Driver	"vesa" yours may sat ati or something else change to vesa
	
press  Ctrl X you will be ask do you wish to save answer y. exit

Reboot

---

### Post by incubus on 2006-11-25
Hey guys,

How far have you got?  You said safe mode worked, but did you get to install Ubuntu?

incubus

---

### Post by thebjoern on 2006-11-25
HI SD-Plissken,
thanks for your reply. The problem is that I haven't even got to install it yet, I put in the CD that I burnt, and I choose "start or install ubuntu" (or also tried "start ubuntu in safe graphics mode"), and then it shows the black&white logo for a while, then after a while it seems to switch to a different resolution, and from then on I can't do anything. Numlock doesnt work anymore (ie LED doesnt change), and combinations like ctrl-alt-f2 or f4 dont do anything either.

So the problem is not that it doesnt boot an already installed ubuntu, but rather that I can't even install it at all...

Any newbie friendly way to fix that?

thanks for all your help,
Bjoern

---

### Post by incubus on 2006-11-25
Hi Bjoern,

From what I read from the links above, this problem seems to be pretty serious. My suggestion to you is to try the non-graphical installation CD.  Unfortunately, you will have to download it.  When you get to the download page, grab the "alternate" install for amd64.

It's not as fancy as the live cd, but it always worked for me.

Let me know if you need help through the installer.

incubus

---

### Post by thebjoern on 2006-11-25
Ok, I will download that, will have to wait till monday though with that (as at home I have almost run out of my download limit argh, so I need to do it at work)

thanks, and I will let you know how it goes :)

Any hints/tips beforehand? Things that I should know before trying that installer?

---

### Post by incubus on 2006-11-25
Yes:
1. Have a backup of your files.
2. Don't get thrown off by the interface.  It works.  : )

Just so you know what you're gonna see, here are some pictures:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10?](http://www.howtoforge.com/perfect_setup_ubuntu_6.10?)

3. Plan in advance how you will set up the partitions (order, size, and file system types).

4. Good luck.

incubus

PS: That link is about Ubuntu Server, you want the Alternative Installation CD.

---

### Post by Paulo Wageck on 2006-11-25
i always install the server version
after the instalation i just do a:
[I]
sudo apt-get install gnome-desktop kde-desktop[/I]



cheers!

---

### Post by mm2000y on 2006-11-25
May be that your installing the amd64 version on an amd32 chip. Try the 386 version. I believe the amd64 bit version is made for a 64 bit processor, not a 32 bit processor.

---

### Post by thebjoern on 2006-11-26
@incubus:
Thanks for the link, I will try that in a couple days when I got the CD downloaded... if I have further questions/problems I will post again :)

@mm2000y:
I got an Athlon64 3200+, so it actually is a 64bit processor... and I have tried the 32 bit installer before, with the same result (I tried 32bit before I knew there was a different installer, I thought it was all bundled on that CD that I got from work...)

anyway, thanks everyone so far, your help is much appreciated! 
I will report back when I have tried again :)

---

### Post by vladf on 2006-11-26
Same problem with an ATI Radeon X800 GTO. Motherboard ASUS A8N-E (chipset nForce 4 Ultra). Processor Athlon 64 3200.

I am install Ubuntu 6.06.1 in text mode. Then find in /etc/X11/xorg.conf

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
```

and change "vesa" to "radeon" (not "ati"!). Graphics start work, but with low resolutions. My video card have 2 ports: DVI (there plug in my monitor) and D-Sub (void). And system set this small resolution because of this void port. So, I am add string

Option "MonitorLayout" "TMDS,NONE"

to "Device" section. Its work fine ;)

Also you can try use official ATI drivers. 

PS: I think, this is serious problem in Ubuntu distribution...

---

### Post by thebjoern on 2006-11-28
Thanks vladf, good to hear you were able to solve the same problem..

Meanwhile I have downloaded the 64bit alternate version, but probably wont get around to installing it before the weekend...

---

### Post by thebjoern on 2006-12-01
Ok, so I installed this alternate x64 version today, and it all worked and went smooth (the installation process), then in the end it asked me if I wanted to install GRUB in the master boot sector, which I did, then it told me to reboot, but it never even gave me a choice and just booted straight to Windows.... :-k 

Any ideas anyone, on what I did wrong? 

I went and started the installation again, in the "rescue mode", and again that seemed to have worked fine, again it asked me to install GRUB to the master boot and again I said yes, and again it just wouldnt give me a choice, but just boot to Windows.

So I thought maybe it went for the wrong disk or so? Cause I got two SATA drives and one old IDE drive in my PC, my Windows boots from my bigger SATA drive with 320 GB, and thats where I created another partition for Linux (one with about 25 GB for Ubunutu, one with about 2 GB for swap and one with abuot 10 GB as a shared FAT32), but all on the same disk as the Windows which it boots...

Hmmm.. dont really know what to do, and am a real Linux newbie, like I said before :confused: 

Any help would be much appreciated! Thanks!

---

### Post by thebjoern on 2006-12-01
Oh no, I have tried to do it again, and now it doesnt boot Windows anymore :( I dont think I have damaged Windows itself, but I cant get it to boot anymore... can anyone help me please, I am quite desperate now... I have tried installing Ubuntu a couple times (like I said before), but it always booted to Windows without giving me a choice, now it doesnt boot at all anymore... 

Thanks for your help!

:confused:

---

### Post by shartke on 2006-12-01
I was having the same problem with the live cd version with my AMD64 bit processor.  I was able to boot into the live cd environment by hitting f6 on the main install screen.   At the end of all the kernel arguments type noapic and then hit enter.  I then booted into the graphical install live cd.  As far as the windows problem you may be able to re-install grub from within linux to get your windows partition back.  Or try editing your /boot/grub/menu.lst and see if that has windows in it.

---

### Post by thebjoern on 2006-12-02
To enter that noapic, which mode do I have to use? Install in text mode? Or Rescue a broken system?

Btw when I try to "Boot to first hard drive" I end up on a text mode screen saying "GRUB" and a prompt, but cant do or enter anything...

Anyone maybe willing to help me in a "live session" via ICQ or MSN?

](*,)

---

### Post by thebjoern on 2006-12-02
Ok, I tried using that LILO, when I reboot, it still doesn't give me a choice, but it tries to boot to Ubuntu now (rather than Windows - I hope I can rescue my windows! :() and then when loading the Linux files, it then seems to try to switch to another screen mode, and then I have the same problem that I had before -> I end up on a black screen, where I cant see or do anything (Numlock doesnt work either)

:confused:

---

### Post by thebjoern on 2006-12-02
Anyone? Ideas?

---

### Post by jellomoto on 2006-12-02
The boot sector needs to be fixed.  Find the windows installation disc for your computer and boot with it in.  Go to the recovery console and type fixboot and press enter.  That should fix the boot partition to load windows again.

---

