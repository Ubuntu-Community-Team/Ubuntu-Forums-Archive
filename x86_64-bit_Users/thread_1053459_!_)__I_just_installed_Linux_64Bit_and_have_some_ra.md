---
title: "! :)  I just installed Linux 64Bit and have some ramdom questions"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by concerto on 2009-01-28
I just bought a Laptop and it came with Vista 64 so I decided to partition the hard drive and install UBUNTU AMD 64. Now I had some beginner start up questions if you don't mind.


Question 1. When I power the computer on I now have many boot options. I have 2 different ways to boot into vista (one being a safe mode) but four ways to boot into Ubuntu.

One option is...
Ubuntu 8.10, kernal 2.6.27-9
The other option is...
Ubuntu 8.10, kernal 2.6.27-7
They both seem to do the same thing, Are they the same?  I don't want one to be like ROOT or something and mess everything up.

I know I have only 2 partitions, one for vista and one for Linux.
Whats the difference in these Linux boot options? 


Question 2. No sound but It seems like everyone has this problem that has my same computer so, my question is, Is it likely that it may be fixed one day in the future maybe even in the next coming months?  Can I help by reporting this issue to anybody?     The computer is a HP DV4

Question 3. Is their an easy command line way to install VLC Media Player?
Does anyone know the code?

Question 4. Any Suggested updates I should do? and how.


Thanks everyone.!.!

---

### Post by dasunst3r on 2009-01-28
1. They're different versions of the kernel, which is basically the core upon which everything else runs.  You might be seeing the same thing, but differences are going to be tiny bits of optimization and bug fixes.  If you want, you can go ahead and remove the 2.6.27-7.

2. I seem to be unable to find your computer's model.  Can you please give me further information, like a picture of the computer, the model number found on some label on the bottom of the machine (NOT the serial number :)), etc.

3. You should add Medibuntu's repository: [www.medibuntu.org](www.medibuntu.org)  Afterwards, just *sudo apt-get install vlc*

4. I'm personally glad to see that you're playing around with Linux.  By being here and asking questions, you are on the right track -- keep it up!  Expect to be frustrated and expect to have your patience tested.  I update once a week, but you can update whenever you want.

---

### Post by gettinoriginal on 2009-01-28
1. Your multiple boot options under ubuntu are different kernels, the one ending in .9 being newer than .6.  Both take you to the same thing, and the only difference being that the newer one has some updates to libraries, etc.  Under the Ubuntu kernel boots, you also have Recovery mode which helps in auto fixing things if they break ;).  You cannot hurt the system by running recovery, but if nothing is wrong, it won't change anything.

2. Try this for the sound:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

3. For installing VLC;
```
sudo apt-get install vlc
```

---

### Post by cdtech on 2009-01-28
> Question 1. When I power the computer on I now have many boot options. I have 2 different ways to boot into vista (one being a safe mode) but four ways to boot into Ubuntu.
To understand the GRUB boot menu you could read this site:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
This will explain most of the GRUB's boot loader options found within the /boot/grub/menu.lst. You basicly have two choices for each kernel image that's installed: normal boot (GUI) and a recovery mode (no GUI, command line only). The kernel images are numbered such as in your case (kernal 2.6.27-9 and kernal 2.6.27-7) and you have two versions installed (probably from a previous update). It's always a good idea to keep the backup (previous) kernel image until you are certain the newly installed kernel image is operating properly.
> Question 3. Is their an easy command line way to install VLC Media Player? Does anyone know the code?
Always try to use the "Synaptic Package Manager" when you install or uninstall packages. The manager can be found at "System > Administration > Synaptic Package Manager".

Hope this helps ya........

---

### Post by concerto on 2009-01-28
**_Dasunst3r_**

I don't think the sound can be fixed.  When I do a search on this forum for HP DV4 it seems like many people have the same problem as I do.

But if you can help me find a fix I would owe you my life.

The computer is a HP Pavilion DV4-1155se Special edition.

With an AMD TURION Ultra X2 Processor
and an ATI Radeon graphics card
It's just an average Laptop thats ruining my life because it doesn't like Linux.

---

### Post by gettinoriginal on 2009-01-28
Seems there is a fix here:
[http://ubuntuforums.org/showthread.php?t=984538](http://ubuntuforums.org/showthread.php?t=984538)

---

### Post by concerto on 2009-01-28
The fix did not work for me.  :(  I'm really mad at myself.  I should have done research on the laptop before I bought it.

---

### Post by Kilz on 2009-01-29
One point on removing kernel entries in grub. For safety it is suggested that you leave in at least 2 versions. That way if there is a problem with oue after an upgrade you can boot into the other.

---

### Post by concerto on 2009-01-29
Hey again,  I just want to thank everyone for their input and time.  I'm going to mark this thread as closed.

I never got my sound to work but I'm sure it will have a fix soon.

Thank You so much Everybody!

It's such a weird feeling having people you don't know working with you until your issues are resolved.  It's such a positive environment.  Thanks again.

---

