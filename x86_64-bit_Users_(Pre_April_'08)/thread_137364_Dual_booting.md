---
title: "Dual booting?"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Madman68 on 2006-02-27
Hello, just wanted to ask about dual booting Ubuntu with Mac os x on an iBook G4. I've herd some bad things about trying to dual boot this way. Just wanted to know how good this would woor and get some advice on how to properly do this. Thanks!

---

### Post by engla on 2006-02-27
I dual boot, but I don't boot into OS X that often so I don't think I have very much experience from it...

Installing the dual-boot should be easy, it doesn't really matter if you install OSX or ubuntu first.

Right now it seems to be impossible to use etx2 and ext3 disks in OS X Tiger -- in Panther I could even use one for my home directory with the proper add-on installed, but I upgraded to Tiger.
So if you want tight integration and ease of sharing files both ways you should probably go with OSX 10.3.. --if you don't desperately crave 10.4 (like I do, because of Quicksilver)

Please ask away with specific questions if you have more! By the way, I don't know what bad things people have said about dual-booting.. I havent heard much.

---

### Post by Madman68 on 2006-02-27
First of all, thanks. Secondly, I was just a little concerned that dual booting on the iBook would pose some problem with OS X seeing as I still want to be able to use all the features of OS X and of course I want to be able to use all the features of Ubuntu. I heard from an IT friend that sometimes there was an issue with booting into OS X when dual booting. I just don't want to screw up OS X. Thanks again!

---

### Post by linear on 2006-02-27
The only "issues" I know of: you need to edit yaboot.conf if you want OS X to be the default, and you shouldn't use the Startup Disk preference pane to choose a startup disk (messes up yaboot, but is fixable).

---

