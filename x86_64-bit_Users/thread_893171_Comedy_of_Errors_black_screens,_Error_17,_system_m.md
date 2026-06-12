---
title: "Comedy of Errors: black screens, Error 17, system menu not working"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by Anonymong on 2008-08-18
Three days ago I installed Kubuntu without any problems on my machine. Then yesterday I encountered a chain of possibly unrelated issues with Kubuntu that cascaded into one horrible mess.

1) The System Menu on the panel refused to work, instead of opening any folder (whether it is ‘Documents’, ‘System Media’, ‘Root’ and ‘User Home’; all of them) it asked me what program I wish to use to open them with? The System Menu option has also disappeared from my panel.

2) I rebooted the machine. After the log-in I was taken to a black screen. Could not see or do anything from here. The same happens after I picked the recovery mode from the GRUB menu after the next reboot.

3) After I rebooted the machine after what must have been a third or forth time, GRUB refuses to work. Instead of the menu where I could select my OS, I get a message that reads “GRUB loading please wait” then “Error 17”.

I’m using another computer to type all this, though I understand that I could have used my live CD to access the internet. 

I guess I must have foolishly jumped right into the deep-end; I cannot be sure what I’ve done to have gotten here. I think I’d prefer to remove Kububtu altogether from my machine, maybe start over another time, but would also lose the partition I’ve made? I have only one physical HD that was split into four virtual drives, Kububtu further divided two into one (possibly as a result of an accident on my part).

I’m a total newbie and utter moron, so please if you could help, explain in a way that myself and others would understand.

---

### Post by cariboo on 2008-08-18
You have probably screwed something beyond repair so you might as well reinstall, Just do the same thing you did when you originally installed kubuntu. Next time stop and ask questions before continuing on.:)

Jim

---

### Post by Anonymong on 2008-08-18
I haven't touched, edited, altered anything I haven't got 100% knowledge on what it's meant to do, so I did very little on Kubuntu, nothing I can think of that resulted in this. I cannot say the same about other people who use the machine, but since only I have access to the Kububtu OS; if it is the result of human error it would have to be done from Windows, but I cannot fathom how. 

If I did reinstall Kubuntu, would I be forced to make another partition on my HDD, is there an option to merely overwrite my current install? Any idea what might have caused these problems in the first place and would I still be able to access GRUB and my original OS?

---

### Post by Ehtetur on 2008-08-18
The black screen may be because it's not completing post..
And the fact that Error 17 is a grub error:
It usually means that it can't find the /boot folder or partition which has the kernel... Either menu.lst was modded or your partioning scheme changed since the install... Is this a dual-boot machine?

You can try this fix... but for a newb, it may be easier to just 
reinstall - especially if you got dual-boot set up...

Check where /boot is located 
> df /boot 
On my unit with SATA drive, /boot is located /dev/sda1 

Then have a peek at what's in menu.lst
> sudo less /boot/grub/menu.lst
Look for a line that doesn't begin with a # and also has this:
> root (hd0,0)
On a clean install using the entire hard drive, ubuntu's default location for /boot is hd0,0...

If your (hdx.x) is different, change it to have it properly point to /boot...

---

