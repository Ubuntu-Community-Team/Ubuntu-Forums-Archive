---
title: "I am planning a dual OS"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by heatblazer on 2008-06-20
Here is what I am going to ask you:

 Recently I got a new PC: Intel C2DUO/e8400@3.0GHz(wolfdale); 6GB DDR2 800MHz ram and a new mainboard by GIGABYTE. So, I will get a new HDD 160 GB and I will install ubuntu 64 and VISTA for gaming. Is there any specific advice? First VISTA install then ubuntu, right(to avoid the LIVE CD boot and the manual sudo grub-install)? 
 Anyone to report or to share some expirience?

 Regards,
 ILIAN

---

### Post by ScaredNoob on 2008-06-20
Right.  When you do a normal install from livecd you will auto-install grub at the end, and it will have already saved a slot for booting into your Vista partition, grub defaults with a 10 second or so delay until Ubuntu will get the go-ahead, but this can be changed by text-editing the grub menu file.

---

### Post by Sef on 2008-06-20
Read [Psychocat's Ubuntu]("http://www.psychocats.net/ubuntu/").

---

### Post by rzrgenesys187 on 2008-06-20
Nice computer.  Don't have much more advice than what you already said.  Vista first then Ubuntu.  One thing that may save you time is to install Vista to a specific partition size before doing Ubuntu so that way you don't have to do a resize.  When I did this when I reinstalled Vista ran much better.

---

### Post by heatblazer on 2008-06-20
Well, thank you all. I`ll partition it 100 for vista 60 for ubuntu,  I think that the crapy Vista will have enough - 100GB. I hate that OS... only DirectX 10 and the new games are interesting to see :(.
 I`ll use GPARTED, I used it back when I had 5.10 and I`ll use it again :)

---

### Post by cod3rbro on 2008-06-20
Right, You should install Vista first, but to make it easy, do not format all disc capacity, spare some gygabytes empty disk for Ubuntu.
After you finished installing Vista then run The Ubuntu Live CD, just click the Installation icon. After some steps, then you will find option -> "use entire empty disc" (sorry I forgot the note), and the rest ubuntu will do it for you including grub installation, you no need command lines, I had try it on Gutsy and I think it will be same with your case.

---

### Post by pixel :-) on 2008-06-20
Optional

In ubuntu ,a partition for / and a partition for home.This way reinstalls will be much easier.You simply reformat / and reattach your old home as the new one.My home partition is over 2 years old. 

6GB of RAM? I think this is way to much,you 'll not need swap.

also give wine and a chance.

---

### Post by heatblazer on 2008-06-20
Say again? HOME directory in a separate HDD partition? Hmm... That`s an insteresting. I`ve been backing up HOME for now on CD/DVDs but now I`ll just give it a different location?

---

### Post by pixel :-) on 2008-06-20
This doesn't dispense you from continuing to back up.

Further more,you can control that / partition is kept away from 100% full,as a hard disk aproches 100%, it's acces speed diminishes.This should preserve the speed at witch programmes are loaded.

---

### Post by heatblazer on 2008-06-22
I did it. Well it`s much better to have the HOME in a separate HDD partition. By the way, if HOME from 32 is copied to 64 what will happen? I know there are just config files there, they must be the same for x32 and x64? 
 BTW I installed the VISTA, kind of a big crap. Eating a lot of HDD and quite possibly a big sucker :( And what is this?! They were doppleganging KDE :(

---

### Post by pixel :-) on 2008-06-22
32 is copied to 64 

I didn't have any problem when i did this.Just take in to account that occasionally you may need to delete a old incompatible config directory.because sometimes newer version change the way they save there configuration files, and this brake the application.If you manage to keep it for years you will be confronted to this.Specially with rapidly evolving software like wine.

---

