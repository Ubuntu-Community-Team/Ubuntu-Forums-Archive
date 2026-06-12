---
title: "Keyboard and Mouse Freeze"
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by LinkRJH on 2007-04-24
Hello,

This would be my third post regarding this issue without any help as of yet. I've installed Feisty and cannot use my computer for any significant amount of time before my keyboard, mouse, or both freeze. It seems to be one then the other and dependent upon how much I use them as to what will go first. I'll be surprised if I can finish typing this post before I lose my keyboard again.

Without the ability to use a mouse or keyboard, I have to do a hard power down with my computer with is potentially damaging to my hardware making Ubuntu a less and less friendly choice - as it may destroy my computer.

The mouse and keyboard are both USB, and based on what I have gathered from other sites I've read regarding these types of issues, this is the information you would need to assist me:

```
linkrjh@gigahertzog:~$ lsusb
Bus 002 Device 003: ID 413c:2005 Dell Computer Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
linkrjh@gigahertzog:~$
```

I am glad I haaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaa

---

### Post by xstaticxgpx on 2007-04-28
Same issue. Please someone actually help this guy (and me).

---

### Post by basementgeek on 2007-04-29
Did you install the official release or just update Dapper or Edgy?  I had the same problems after a bunch of updates on the Feisty beta, and couldn't find any answers.  After I did a clean install of the official release, no more freezes.  Might help you guys....

---

### Post by iggee85 on 2007-04-29
I also have this problem. I've been using the same wireless keyboard and mouse combo since Edgy. And I have a backup pair of wired keyboard and mouse since Breezy. And I've only encountered this problem in Feisty.

I've been having this problem since I tried Feisty beta (using wireless combo) and assumed it was something wrong in the beta. So I waited till release and did a clean install but the mouse still freezes on me. So I plug in my wired mouse but it also freezes in anywhere from a few minutes to a few hours. My keyboard still works though. 

Replugging either mouse does nothing so I end up having to reboot to get it to work. I already tried Disable Legacy USB in BIOS but  there's no option for it. I also tried adding the noapic workaround to the boot entry but it didn't work either. From other posts, it seems the only other option I can try is to buy a USB card or hub. But I would really rather get this problem fixed without spending money since I know I didn't have this problem in Edgy.

---

### Post by Max_Kbrown on 2007-04-29
I also had the same problem, what I ended up doing was getting a USB to PS/2 converter for my mouse. I haven't had any problems since... I know is just a work around the problem.. but it keeps me going without the mouse freezing. May be some time later on , somebody will come up with a permanent solution.

---

### Post by kuja on 2007-04-30
Did you have any trouble with Edgy? If not, maybe you'd have better luck running Edgy's kernel? (assuming it's a kernel problem, which it very well could be)

---

### Post by Minus0 on 2007-04-30
I'm having the same problem, usb mouse doesn't freeze though, but my PS/2 keyboard does.  I've tried two different keyboards, and neither work after gdm is launched.  Up until that point, I have full control over my keyboard.  I installed off of the alternate 7.04 cd (due to LVM).  If I boot off of that, it works fine.  I can enter the bios, switch terminals (ctrl-alt-F?) and everything all the way till the login screen.  If I boot into recovery mode, and go to the command line, I have the same problem once it comes time for me to login.  Up until that point, I have 0 problems.

---

### Post by Minus0 on 2007-04-30
I found the solution, at least for my problem.
[http://ubuntuforums.org/showthread.php?t=419861](http://ubuntuforums.org/showthread.php?t=419861)
Basically you should try to add pci=noapic to your boot config.

When you get the prompt to hit escape to get to the grub menu, hit esc.  
I'm not in front of my computer (no network access on that one), but there should be an option to edit the boot options (if I recall correctly, its "e".  Then there should be an option to add a new line (I highlighted the "quiet" line and hit "o"), do so.  Then add in the pci=noapic line and see if you have any luck.  Worked for me...

---

### Post by linebp on 2007-05-09
I am having the same problem I think  :(

I have a USB keyboard(Logitech G15) and mouse(Logitech LX5 Cordless Optical). My mouse freezes after a fairly short amount of time, I can still use the keyboard though. I am using a freshly installed Feisty Fawn, it even froze during the install, luckily you can do it all using only your keyboard. I didnt have this problem on my old Dapper Drake.

I can make "solve" the problem by turning of legacy USB support of in the BIOS, at least I can work for hours with no problems which i couldn't before, but that also gives my no keyboard support on the grub screen. 

Can someone please post a solution to this problem?

Output from lsusb:
linebp@Hex:~$ lsusb
```
Bus 002 Device 005: ID 046d:c222 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c221 Logitech, Inc. 
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 003: ID 046d:c223 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by dignaf on 2007-05-09
:)  I met the same problem many times actuallly when I was using the 6.10 Edition. And at that time I got an idea  from this forum, that is, to "Enable the Legacy usb device". Seems strange isnt it? But when I disabled this option, my usb mouse freeze as well. Then i tried to enable it, this problem was solved completely.
But after I installed the clean Feisty Fawn, the problem came back and this time the option of legacy usb device was not helpful at all......

---

