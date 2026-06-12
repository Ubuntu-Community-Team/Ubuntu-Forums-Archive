---
title: "Installing 32 bit windows in 64 bit ubuntu host"
date: 2007-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by emkman on 2007-06-11
Hello. I want to install Ubuntu and then run 32 bit windows xp in KVM. Will this be a problem if I choose AMD64 ubuntu? I have an AMD x2.

---

### Post by JAPrufrock on 2007-06-11
> **emkman said:**
> Hello. I want to install Ubuntu and then run 32 bit windows xp in KVM. Will this be a problem if I choose AMD64 ubuntu? I have an AMD x2.

I'm running 32 bit windows XP in VirtualBox on an AMD machine with 64 bit Feisty.

---

### Post by nxt on 2007-06-11
I am not sure about KVM, but VMWARE allows you to select the type of the guest os you want to install - 32 or 64bit.

---

### Post by lazyart on 2007-06-11
VMware Server here.  This weekend I net-installed Edubuntu in one VM using 256 megs of memory, checked out Kubuntu (which is nice looking) in another using 512 megs, while running a game in Windows XP (there is a linux alternative but it was written poorly) that used 192 megs.  This on Ubutnu AMD64, Athlon 4000+ with 1.5 gb.

Pedal to the metal.

---

### Post by capecove on 2007-06-11
I second the Virtualbox setup. Installing Virtualbox and Windows XP Home was cake. As easy and much faster than the regular WIndows XP install. :)

Give it a try, it is excellent!

---

### Post by emkman on 2007-06-11
Thanks. I had not heard of VirtualBox. I just looked into it. Looks good. 

Right now, I am running just windows XP. What general differences are there between running windows as the Host and ubuntu as the guest, and vice versa?

---

### Post by capecove on 2007-06-11
Wow... I guess I'll let somebody else who has had the experience running Ubuntu in a virtual machine speak for that. I would guess that, first of all, you couldn't run 64 bit Ubuntu in a virtualbox window. You would have to stick to 32 bit version. But, I can tell you that my installation went excellently, both Ubuntu and XP. I have multiple drives so left Windows on one (for now) and put Ubuntu on the other. Now, I run Wndows XP in a Virtualbox and it is very quick. I see very little performance decrease.

---

### Post by emkman on 2007-06-11
Ok, running 64 bit isnt necessary, I do more day to day stuff and development than encoding/computing complex math. 
How bout this ... Do I need to do a fresh install of windows for virtualbox or any other VM for that matter? I want to get a new SATA hard drive and make that my primary drive. On it I would install Ubuntu. Can I then use Virtualbox or something else to boot my existing windows installation located on my current hard drive? It would be nice to not have to reinstall windows and reconfigure everything since I will be running exactly the same hardware.

---

### Post by capecove on 2007-06-11
I currently use Ubuntu as the main OS and still have Windows XP on another drive. GRUB will allow me to choose which of the two I want to use. It's pretty slick. But, Virtualbox is much faster for regular stuff (2D). I have it setup for man y of my common apps that I would be hurting to do without and I don't have the expertise to setup in WINE yet.

Actually, I ran across some instructions for making Virtualbox function with an existing Windows install (this sounded a little dangerous to me)... Let me see if I can find them... Yup, here they are:

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

Hope that helps out...

---

### Post by emkman on 2007-06-11
Thanks. GRUB is another option but Id rather VM than dual boot. I really like the idea of just switching virtual desktops to go back and forth between linux and windows. I saw that link too, so I guess its doable. For some strange reason, I have the non ACPI Hal installed now. I still need to figure out how I turn my existing windows drive into an virtualbox image, im reading the manual. Thanks for your help.

---

### Post by capecove on 2007-06-11
Anytime, glad to do it... :D

Be sure to let us know how you work out...

---

### Post by Golyadkin on 2007-06-12
I am currently installing 32 bits Windows XP Pro in Virtualbox 1.4.0. for Feisty 64-bit edition. Everything going great at the moment, I will let you know if it worked for me. My processor is an AMD X2 4200+

---

### Post by Golyadkin on 2007-06-12
Well, that was incredibly easy. And fast too!

[[IMG]http://img362.imageshack.us/img362/9829/winxpinvirtualbox64bitzm6.th.png[/IMG]](http://img362.imageshack.us/my.php?image=winxpinvirtualbox64bitzm6.png)

---

### Post by emkman on 2007-06-12
Awesome, i have the 4200+ also, looks like we have the same plans. Glad to know it works well. Did you migrate an existing windows install, or do a fresh one?

---

### Post by JAPrufrock on 2007-06-12
There are some pretty nifty advantages to using virtual XP instead of dual-booting.  First of all, in VirtualBox ubuntu and XP can run simultaniously, so you can switch back and forth between the two.  So you can generate data from a program you need to run in XP, and then immediately input it into a program in Ubuntu.  Also, it is much harder for a virus to infect a virtual Windows OS than an actual Windows OS (because it runs inside Ubuntu it is much more secure).

Oh yeah, I forgot something.  The down side is that running a virtual OS is much more resource consuming (memory) because you're running 2 OS' at the same time.  I use an extra 200 megs of memory when I run virtual XP.

---

### Post by Golyadkin on 2007-06-13
@emkman: I did a new install, from an ISO I made of my Windows XP installation CD. So it copied the files from the harddrive and was superfast. 

Also, now I have the Guest Additions installed, I dont have to click inside the virtual machine window anymore to give it focus, whenever the mouse is over the window, it has focus. Very handy. For the things I use it for, like Photoshop and Office 2007 when I get files from university, I don't notice it to be any slower than a regular install. 
I have 1024MB of dual channel memory, but plan on adding another 2048MB in a few weeks.

---

### Post by dabl on 2007-06-13
I can run Win XP Pro in a VMWare Player window on my Ubuntu 64-bit system, when I need it which is rarely.

---

### Post by capecove on 2007-06-13
Dabl, why VMWare? Did you chose it for a specific reason or simply because Virtualbox was not ready when you need it? Just wondering why you would choose one over the other.

---

### Post by dabl on 2007-06-13
I have two Windows apps that I can't get along without, and that don't have satisfactory Linux substitutes -- TMG (a genealogy program) and Motorola PhoneTools.  My first method of running them under Linux was Win4Lin ($75 USD), but it doesn't see the USB bus (at least not mine), and so that was not a solution for the cell phone thing.  I tried Wine, but it won't run TMG -- lost an entire weekend on that adventure!  Lost another weekend trying to get Moto4Lin to see my Razr phone -- came up empty.

VMWare Player is free, and with some help that I got from a smarter guy than me, can run my USB printer, my USB scanner, can see my cell phone, and runs TMG 15% faster than Win4Lin.  So, that's my solution.

I hear good things about Parallels and VirtualBox. But, at this point, I'm happy with VM Player so that's what I'm using. :D

---

### Post by capecove on 2007-06-13
Excellent, I was wondering since Virtualbox is free as well why you didn't run that in your Kubuntu 32 bit install. I am pretty new myself and Virtualbox is my first attempt at a virtual machine in Ubuntu. It sure went super easy for me. :)

If I have any trouble with it however I will give VMWARE Player a try. Thanks again...

---

### Post by Golyadkin on 2007-06-13
I used to use VMware on Windows all the time, because Virtualbox didn't exist yet. Now I run Ubuntu I am loving Virtualbox, even though I tried VMware Server for a while. Virtualbox seems faster and has more configuration options like acting as a terminal server. It works a little easier, but I don't like having to add myself to this special group of vboxusers because for that I have to logout, which is a nuisance.

---

### Post by onero on 2007-06-14
> **Golyadkin said:**
> I used to use VMware on Windows all the time, because Virtualbox didn't exist yet. Now I run Ubuntu I am loving Virtualbox, even though I tried VMware Server for a while. Virtualbox seems faster and has more configuration options like acting as a terminal server. It works a little easier, but I don't like having to add myself to this special group of vboxusers because for that I have to logout, which is a nuisance.

You only have to add yourself to the vboxusers group once and then restart, after that it's ok. :) I love virtualbox as well; haven't really used VMWare recently but I had problems the last time I used it and virtualbox just seems easier to setup. :D

---

### Post by dabl on 2007-06-14
> **capecove said:**
> I was wondering since Virtualbox is free as well why you didn't run that in your Kubuntu 32 bit install. 

Actually, Kubuntu is where I run the VMWare Player all the time -- in Ubuntu 64-bit I do mostly audio work, so I use Linux apps for that, and don't need the Windows apps.  But I did check to see that the VMWare Player and Windows apps will work in Ubuntu if I happen to want them.  :)

---

### Post by Golyadkin on 2007-06-14
> **onero said:**
> You only have to add yourself to the vboxusers group once and then restart, after that it's ok. :) 

Yeah I know, but I never turn my computer off, so having to logout to make Ubuntu aware of the groups my user is part of is a bit too Windows-ish for my liking. :)  I don't like it when I have to close the programs I have open. 
I ran a RedHat server in a closet sometime for 674 days on end, with not a single reboot. :)

---

