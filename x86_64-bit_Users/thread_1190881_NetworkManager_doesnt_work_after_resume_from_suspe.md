---
title: "NetworkManager doesnt work after resume from suspend"
date: 2009-06-18
forum: x86 64-bit Users
---

### Post by khamil8686 on 2009-06-18
In Jaunty Jackalope off a clean install i Network Manager works just fine, but then if i suspend and resume it stops responsing and i have to reboot for Network Manager to work again. I use wicd for Ubuntu 8.10 and upgrading to Jaunty if i install wicd it lets me suspend and then resume but on resume the suspend and hibernate functions disappear and if i try to do anything but shut down to turn off the computer so i can start it back up again it goes to a black screen with a bunch of text and then usually freezes and doesnt shut down unless i do a hard reboot so wicd and hal dont get along with jaunty for some reason. any help is appreciated :)

---

### Post by AClark on 2009-06-18
Sounds a lot like the same problem I had.

The solution using SUSPEND_MODULES described here: 
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780)
 fixed it for me.

You need to know what driver your WiFi adapter is using in order to implement this fix.

depending on your adapter 
```
lshw -C network
```
will give you that info.

In my case it was rt61pci that was causing the trouble - in my searching for the solution it seems there are several that have about the same effect.

For me there were all kinds of strange things that happened after resuming from suspend including the exact thing you described.

I haven't had any problems since I created the file with the SUSPEND_MODULES statement 

I also use WiCd and prefer it.

EDIT: My profile says Hardy but this problem occurred on a clean install of Jaunty 64

---

### Post by khamil8686 on 2009-06-18
that command lists my driver as rt61pci, exact same driver that had problems in that thread you posted a url of. im reading and testing it out now :)

---

### Post by khamil8686 on 2009-06-18
*kicks self* ive been working on this problem [http://ubuntuforums.org/showthread.php?p=7481730#post7481730](http://ubuntuforums.org/showthread.php?p=7481730#post7481730) for months now and had tons of times staying up late messing w computer to no avail and finally figured it out, wicd didnt play nice with my comp and suspend/resume. so i use network manager instead and find that wireless doesnt work after suspend, but i can suspend at least, but then have to reboot, now i posted this thread hoping for a fix in the next week or so and i get it that night! ... YAY ... words cannot describe how ecstatic i am. all ridiculously hard problems have simple solutions. :P :) thank you AClark! :)

---

### Post by AClark on 2009-06-19
I'm glad to hear your problem is solved.

I have found these forums to be an incredible resource and have been helped so many times here - It feels good to be able to help some one else for a change. 

It's amazing to me how many times I have been able to resolve some issue with one of my Ubuntu boxes just by cruising these forums without even posting a question.

---

