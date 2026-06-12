---
title: "Generell Help"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by VforVendetta1988 on 2008-05-02
Hey folks,
my name´s Patrick I´m completely new to the Linuxcommunity,I gone so ******* mad @ Windows XP (well,all microsoft products suck) so I  made some research and finally found a nice alternative OS instead of using this huge piece of **** called Windows ;):):)

2 Minutes after Ubuntu was running I totally fell in love with it and everybody that makes Linux possible ;)

Well,although its running really nice I got some problems so I wanna know WHERE I can get the latest drivers for my new Linux OS
are there any famous sites for linuxusers?
How can I get computer games running?(In case its possible)

the most important thing for me is,a working graphic/audio driver 
got an Ati Radeon X1950X  and an Nforce 4 chipset

Hope ya guys can help me out with some URLs and of course some tips and tricks for me as a Ubuntu noob ;):lolflag:

PS: God bless the Linuxcommunity ;)

---

### Post by VforVendetta1988 on 2008-05-02
downloaded Ati Grpahics Driver for x86_64 and Nvidia Nforce driver...how do I get it running?
theres an message saying "have to be root user to install" but I already tried to login as root user...doesnt work...I dont know how to get a shell runing at all to be honest...any 1 knows how to?:confused:

nforce installer is kinda funny "have to be logged in a a super user" whatever that means ;) :lolflag:

---

### Post by herdivet on 2008-05-02
I'm no expert, but getting privileges under a terminal I can do.

Open the terminal, (Applications | Accessories | Terminal).  Type 'sudo su' and press enter.  Respond to the prompt with the password that you use (most likely you have one account, yours, that was created when you installed Ubuntu and it will have admin privileges available.  Use that password).  You will notice the > prompt changes to # - you now have root priviliges.  When you no longer need them, type 'exit' and you'll go back to > prompt.  Exit again will close the terminal.

You might want to try 

[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

for help on installing video drivers.

Good luck and watch for more knowledgeable responses that will probably be coming soon.

---

### Post by Sef on 2008-05-02
> How can I get computer games running?(In case its possible)

What games are you talking about?  Some have GNU/Linux versions, some will work under WINE or Cedega, and some won't work at all.

---

### Post by VforVendetta1988 on 2008-05-03
Well I´m talking about Games like
-Hitmen Blood Money
-Need for Speed
-Crysis

etc.

I mean,its no problem using Windows to play my games but...I just wanted to see how far Linux can hold up with Windows ;)

Btw,I tried to set root privilegs via Terminal but it didn´t work
does it depend on which version im running? (8.04 with AMD 64 chipset)

Sometimes my computer freezes while running ubuntu im tryin to find out if its my HDD that causes this probleme sometimes(well to be honest it happens almost dayly) my BIOS does not recognize the hard drive...dunno why...

well back to topic:

"ati-driver-installer-8-4-x86.x86_64.run" (need to run this installer as the super user)
"NFORCE-Linux-x86_64-1.0-0310-pkg1.run" (nforce installer need to be run as root)

how do I do that now? ;)

---

### Post by VforVendetta1988 on 2008-05-03
omg whats happening....cant get any admin/root rights,cant even open Admin Terminal no more....maaaan...so hard getting root rights?

come on help me,dont wanna get back to windows just because of handling problems..:(:confused:..

---

### Post by jocko on 2008-05-03
> **VforVendetta1988 said:**
> 
"ati-driver-installer-8-4-x86.x86_64.run" (need to run this installer as the super user)
"NFORCE-Linux-x86_64-1.0-0310-pkg1.run" (nforce installer need to be run as root)

how do I do that now? ;)

First of all:
There is a much easier way of installing graphics drivers than downloading from ati.
To install ati's drivers, just open up the restricted-manager (System --> Administration --> Hardware Drivers) and select "enable" to install and configure the drivers.
After a reboot everything should work.

Secondly:
You do not need any nforce drivers. Everything needed for nforce 4 is already built in to the linux kernel.
What you downloaded contain old sound and network drivers that are completely useless if you have an nforce 4 card (they will fail to install anyway as they do not support current linux kernels).

Lastly:
When you need to run anything with "root", "super user" or "admin" rights in ubuntu, you put the command "sudo" before the command.
That will ask you for your normal user password before the command is run.

---

