---
title: "Need help with getting interent for VirtualBox"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by thenetduck on 2008-06-08
Hi 
I installed VirtualBox and Windows XP Pro in it so I could use iTunes with my ipod and maybe play a game now and then.

Windows XP installed just fine and I am happy except for two things: 
Thing 1: Networking doesn't work. I have an interest connection to my laptop but it doesn't go to my virtualmachine like it did with vmware. Is there any way to fix this? 

thing 2: USB doesn' show up. I can't seem to get my ipod to be reconized. I did the tutorial and even used the non os version but nothing?... any solutions for a 64 bit os? 

any help is welcome, 
Thanks 
The Net Duck

---

### Post by acrostic on 2008-06-10
Launch Virtual box

Select your windows Xp image -- should be powered off

Click on settings Icon

Select network in left pane in settings window

Check Enable Network Adapter (I have PCNet-FAST III) selected

Select "NAT" from drop down list of "Attached to"

If MAC Address feild is empty click generate

Click OK and boot virtual machine

Hope this works for you

---

