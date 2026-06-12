---
title: "Hoary update questions"
date: 2005-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by tranceConscious on 2005-03-08
I have my pc at home with the amd64 hoary installed.
At home there is no internet.
At the office I have 1Mbit cable.

Can someone describe the steps I have to take to be able to update my packages at home??? (Where and what to download, where to put it at home and how to tell synaptic where to look)

---

### Post by Slapdash on 2005-03-08
I was about to ask a simmilar question but didnt you maybe post this in th Wrong Thread? I see that you have a AMD 64 but maybe it would get answered sooner in another thread. Just a thought.
Anyway also interested to know if / how one can do this.

I am in the same predicament as you.

---

### Post by mips on 2005-03-08
Download the Array6 ISO ! It requires minimum updates unlike array5(300+MB) and it fixes the Nvidia gfx problems.

I downloaded the array6 today and was pleasantly supprised as to how little updates it actually pulled from the net when I installed it about 10mins ago.

I would not know which updates they were (language & something else).

Why dont you take your home PC to work for a day, plug it in and do the install at work ?

So far it is looking goooooooddddddddddd  \\:D/  :grin: 

Cheers
mips

PS. In future post in the AMD64 forum.

---

### Post by tranceConscious on 2005-03-09
I had warty installed

I downloaded the array6 iso

I tried to install hoary but installation failed a couple of times.

So I installed warty once more

and then

put the hoary cd in the drive and do an apt-cdrom add

then used synaptic to do a smart upgrade using the new cd repository added to the list by apt-cdrom

Actually I never waited for synaptic to finish, had to leave so I switched my pc off, so I can't tell you if that worked or not.

My question now is a little complex.

I have the asus a8v deluxe mb that has an extra via sata raid controller used as plain sata (not raid) with one 80gb hd used as my primary drive for my linux and the promise witch has an array of two 120mb hd's merged as one from the promise array config utility.

Warty only see's the via controller and gives my hd the name of sda. Installs fine and works fine.

Hoary on the other hand does something weird.

Recognizes the promise controller and the via controller.

sees the two 120gb hard disks as seperate disks !!!???!?!!?!?!?!

and names the drives as this

promise #1 120gb drive  sda
promise #2 120gb drive  sdb

via 80gb drive                  sdc


what a mess.

So the question now is this.

If I have warty installed (which sees as my boot drive sda)
and I upgrade (with the process I described in the beginning) to hoary,

will my system work?

what will happen with the drive name changes?

I'm confused.

I'll give it a try tonight and let you know tomorrow how it went.

How will I be able to access my raid drive (the two 120gb, 240gb) as one???

---

### Post by tranceConscious on 2005-03-10
My fears came true.

Everything got f*$% up.

The system won't boot.

It's trying to find ubuntu at sda which now is not the disk it was originaly installed to and eventually goes into kernel panick.

---

### Post by Pse on 2005-03-10
First of all, you shouldn't have switched your PC off in the middle of the process (if that was the case).
Secondly, you can always pass to the kernel the option root=/dev/sdxx at boot to show it where the root folder is located.
If you're NOT installing Ubuntu on the Promise disks, try disabling the BOOT ROM of the Promise controller from the system's BIOS. That may prevent Hoary from touching those drives (at least until it loads the kernel module). On the other hand, if you go into expert mode during the installation, you can choose which modules to load during it... If you manage to avoid loading the Promise controller module during the installation process, the installer will NOT be able to do anything to those drives until you boot into Ubuntu for the first time. I think Promise's module is named pdcxxxxxx. Where the Xes are numbers and other characters...Just look for a module that starts with "pdc..." and disable it when it asks you about loading certain modules or not.

[EDIT] BTW, what error are you getting when installing Hoary?

---

### Post by tranceConscious on 2005-03-10
Thanx. Much apreciated help man.

But the problem is that i need to have access to the promise disks.

I'm not sure if it had to do with a bad download of the iso, but when the installation starts it tells me that it cannot access the cdrom or something like that.

I also got that problem when upgading from warty with apt from the hoary cd.

I'm just downloading the iso again, and I'll try it again...

---

### Post by tranceConscious on 2005-03-11
I finally managed to install hoary without errors.

What I did was this.

I ghosted/cloned my serial ata 80gb windows xp hd to my serial ata 80 gb hd.

And installed hoary on the serial ata 80gb disk.

Installation completed succesfully with no errors this time.

Now I have five questions.

1) Why does System -> Administration -> Device Manager
opens and closes imediatelly when I click on it?

2) How can I get the latest available packages from the repositories at home?
I have a zoom usb modem at home and till I replace it with a normal serial modem
or manage to make it work I have no internet....

3) Why does grub NOT boot windows when I choose to? (It just displays the commands and stays there)

4) How will I manage to see my two 120gb hd's on the promise controler as one drive? (I have configured it in the controller as a 2+0 stripped array)

5) What packages do I need to install in order to be able to compile apps that come in sources?

---

