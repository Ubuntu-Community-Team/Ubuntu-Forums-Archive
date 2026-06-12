---
title: "Mouse periodically stops working"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by walterw on 2008-11-09
Hi all,

I updated to Ubuntu 8.10 and am now having mouse issues.  My mouse will stop functioning:

the pointer location on the screen is updated, but the buttons do not work and I cannot click on anything nor are any mouse overs working.

This usually happens several times throughout the day.

Has anyone else experienced something of this nature?


Walter

---

### Post by John Jason Jordan on 2008-11-09
> **walterw said:**
> Hi all,

I updated to Ubuntu 8.10 and am now having mouse issues.  My mouse will stop functioning:

the pointer location on the screen is updated, but the buttons do not work and I cannot click on anything nor are any mouse overs working.

This usually happens several times throughout the day.

I had this happen a long time ago - so long ago I don't remember what version of Ubuntu it was. It was at least as long ago as Feisty. And it happened only on my desktop, not my laptop.

I also do not remember the fix, but I do remember that it was discussed at length on these forums. I was not the only one with the problem. If you search the forums for "mouse clicks" you should turn up the thread.

---

### Post by walterw on 2008-11-09
Hi,

Thanks for you reply.  I just had it happen again within 30 minutes.  I executed dmesg, but didn't see any errors there.  I checked earlier for mouse click, but will try again.



Thanks,
Walter

---

### Post by jessed on 2008-11-09
I'm having the same thing happen on my 64-bit machine. I've confirmed that it happens when using Gnome, WindowMaker, and XFCE, so I think it's happening within X, not the window manager level. It's extremely irritating as the only thing I can do to get the mouse to work again is restart X with a ctrl+alt+backspace. The problem happens more frequently  when using rdesktop, but I'm at risk at all times. I don't have the issue when running 32-bit at all, only 64-bit.

   Unfortunately I am also unable to find any log entries that correspond to the issue occurring.  I'm running dual NVS 290 (nvidia) video cards with three monitors. The drivers are fully up to date. I'm not an expert with X, and so haven't yet found out how to enable verbose logging, etc... Right now it's just a bundle of pain for me. I'd love to hear any troubleshooting itdeas anyone has.



thanks,
--jesse

---

### Post by John Jason Jordan on 2008-11-09
There appears to be a duplicate thread on this issue here:

[http://ubuntuforums.org/showthread.php?t=975769&highlight=mouse+click](http://ubuntuforums.org/showthread.php?t=975769&highlight=mouse+click)

I know I solved this problem, but I can't remember how I did it - it was well over a year ago. I am searching my ancient Ubuntu forum posts to see if I can find the thread.

---

### Post by John Jason Jordan on 2008-11-09
OK, y'all, I finally found where I had discussed this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

If you read the entire thread you will find various possible solutions.

---

### Post by walterw on 2008-11-10
I looked over the posts and see that the problem should have been fixed with a kernel upgrade.  That post is over a year old and I'm running the latest software.  I will use the virtual terminal switching to see if that fixes the focus issue.  I have also disabled apic and acpi to see if that helps.

I don't believe I had this issue in 8.04.

Walter

---

### Post by mrbrice on 2008-11-10
I have the exact same issue, and disabling apic and acpi hasn't helped. 

Mouse clicks will randomly stop. I can't seem to reproduce the error intentionally. I'll be doing random things and all of a sudden mouse clicks or mouse-overs will no longer work. 

The mouse is able to move around, but I cannot click on anything. 

Navigation and full use of the keyboard stays, but as some of you know, this is quite annoying.


Lenovo T61 - Ubuntu 8.10  x64


I'm at a loss where to go from here, as it seems there are some people with similar issues, but no resolution. 

I had no issues what-so-ever with my mouse or anything else with Hardy. 

Lets keep the ideas coming.

---

### Post by John Jason Jordan on 2008-11-10
> **mrbrice said:**
> 
Lenovo T61 - Ubuntu 8.10  x64

I had no issues what-so-ever with my mouse or anything else with Hardy.

I have no further suggestions other than the Launchpad link that I posted previously. I also have a Lenovo T61, but I have not upgraded from 8.04 to 8.10 yet.

When I experienced it over a year ago it was on a new desktop computer that had an Abit motherboard. Because of problems with the SATA controller on that motherboard I changed to an Asus motherboard and the mouse problem disappeared.

What happens if you switch desktops? What happens if you drop to a command line with Ctrl-Alt-F1 and back with Ctrl-Alt-F7?

---

### Post by null_pointer_us on 2008-11-10
I had a similar mouse problem with 8.10 although 8.04 was fine. My mouse would randomly move to a certain area of the screen, sometimes many times per minute. Mouse clicks would stop registering. Soon, it got so bad that I was unable to do anything except get updates (with lots of patience).

Eventually, the problem because clear: Ubuntu 8.10 decided that my USB gamepad, which has two analog joysticks, was a second mouse. With no "deadzone" configured, the gamepad's joysticks would "drift" and give false readings that would override my mouse's input. All I have to do now is press the Digital button on the gamepad to stop the erratic readings.

Maybe you could try unplugging nonessential input devices, i.e. pen+tablet, gamepads, joysticks, etc. in case they are interfering?

Also, have you tried the irqpoll boot option?

---

### Post by zackiv31 on 2008-11-10
I indeed also have all USB peripherals... this is EXTREMELY annoying by this stage as I use this for development of websites...  can someone please advise?

The Ctrl-Alt-F1   Ctrl-Alt-F7 doesn't fix anything for me... is there something on the command line I can type to get my mouse working again?

---

### Post by mrbrice on 2008-11-11
different window managers does the same. it seems to be an xorg thing, or something else.

ctrl-alt+f* and back to *f7 doesn't solve anything.

---

### Post by John Jason Jordan on 2008-11-11
> **mrbrice said:**
> different window managers does the same. it seems to be an xorg thing, or something else.

Has anyone in this thread filed a bug report for this issue?

---

### Post by mrbrice on 2008-11-11
> **John Jason Jordan said:**
> Has anyone in this thread filed a bug report for this issue?


I haven't, but i would be happy to look into that. Never done one before though, so if you can link me to documentation on how to proceed, that'd be cool.

---

### Post by phlembob on 2008-11-11
Hi everyone with mouse maladies.  I know this is not the effects on every machine.  My computer didn't have this problem with 8.10, but it had other problems.  I will only suggest that everyone with problems place their brand of mouse to see if they have  relationships.  If you have different mice available, you may want to try different mice.  Issues like this are common with new releases, but they will be fixed.  Drivers for mice are abundant, but it takes a little more than just a driver to make things function.

Keep on Jammin :guitar:

---

### Post by mrbrice on 2008-11-11
> **phlembob said:**
> Hi everyone with mouse maladies.  I know this is not the effects on every machine.  My computer didn't have this problem with 8.10, but it had other problems.  I will only suggest that everyone with problems place their brand of mouse to see if they have  relationships.  If you have different mice available, you may want to try different mice.  Issues like this are common with new releases, but they will be fixed.  Drivers for mice are abundant, but it takes a little more than just a driver to make things function.

Keep on Jammin :guitar:


On my T61, the touchpad has the same issue, and I've tried multiple different USB mice, from multiple Microsoft mice, to Dell mice, Logitech, etc. 

i should have stayed with Hardy for a bit since this is my work laptop, but it was just too tempting. hehehe

---

### Post by zackiv31 on 2008-11-11
Same here... tried 3 different mice... straight USB, USB wireless, and USB Bluetooth (this one had a hell of a lot more problems, but thats for another thread)...

It's not particular to mice I feel... if someone posts a bug report or info for us to post one please update this thread accordingly so we can all follow up.  I've never filed a bug report, but with all these Intrepid issues I've been having, would love to know how to go about it!

---

### Post by Jouke74 on 2008-11-12
Did anyone try a USB to PS2 converter? Logitech used to deliver those green things with their mice.

Another workaround would be to prevent the UHCI from loading (USB 2.0) and use the EHCI only (USB 1.1). Note that you will loose almost all speed from USB transfers in this case. 

To test it first you can enter the command: 

"sudo modprobe -r uhci-hcd" 

in the terminal (without quotes of course). 
This might however stop USB devices from working at all, so please safe first. 
If this occurs, reboot.

If it helps add "uhci-hcd" to the blacklist file.

OR!

If it still loads after blacklisting (older bug) add 
"modprobe -r uhci-hcd" to /etc/rc.local.

To restore these edits to the original system state; remove the entered lines from blacklist OR rc.local again.

A bug report sounds very useful :-)

---

### Post by walterw on 2008-11-12
Hi,

I just had another mouse incident.  Switching from the GUI on vt7 to vt1 through 6 didn't help anything.  Logging out and logging back in solves it just as rebooting does.

I didn't have any issues with this setup on 8.04, I would be surprised if a new bug was introduced with USB.

I do have ehci and uhci loaded.  The uhci is for my USB mouse and keyboard and disabling uhci causes my mouse and keyboard to not work.

I think you have UHCI and EHCI backwards, UHCI is 1.1 and EHCI is 2.0:
[http://en.wikipedia.org/wiki/USB](http://en.wikipedia.org/wiki/USB)

For the most part, I only use USB 1.1, so this may be a temporary fix, but I have an external hard drive as well as thumbdrives I use to offload data.


Walter

---

### Post by John Jason Jordan on 2008-11-12
> **mrbrice said:**
> On my T61, the touchpad has the same issue, and I've tried multiple different USB mice, from multiple Microsoft mice, to Dell mice, Logitech, etc. 

i should have stayed with Hardy for a bit since this is my work laptop, but it was just too tempting. hehehe

Mrbrice, 

I note that several have tried different window managers without success. Yet others have tried various mice - even bluetooth -and no change in the problem. From the posts here it appears to be something deep inside Intrepid that was changed. 

I have a T61 also, although I am still using Hardy x86_64. However, I know I had problems with various other things until I upgraded the BIOS. Lenovo has an ISO with the latest BIOS that you can download and burn to a CD. Then you just boot to the CD and it will give you some instructions and a button to push to upgrade the BIOS. Scary, but it works great. If, as I suspect, the problem lies deep inside Intrepid it might be a good idea to try the latest BIOS.

---

### Post by zackiv31 on 2008-11-12
Found numerous bug reports posted today about this problem, I decided to put my two cents into this bug... everyone please follow up here.. I'm guessing the more we have the faster this will get resolved!

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167)

---

