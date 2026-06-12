---
title: "Sudden reboots every so often"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by danfluidmind on 2007-03-14
I've got 64-bit 6.10 on an HP Pavilion d4500e (Athlon 64 X2). It will usually run for a month or so without problems. But then it will suddenly reboot. No warning. No graceful shutdown. I'll just be working along and BAM!...system startup screen. Just today I had restarted the system after a bunch of updates. The only app I was running was VMware Workstation 5.5. I was installing another copy of Ubuntu into a VM. I hit CTRL-ALT-F1 to get to the console. I saw the console for about 3 seconds and SLAM...startup screen.

Anyone have any idea what would cause such a thing? I've never had this happen before with ANY linux, much less Ubuntu.

Thanks
--Dan

---

### Post by milton1 on 2007-03-14
That kind of sudden restart usually means a power supply issue.

---

### Post by John.Michael.Kane on 2007-03-14
it could a number of factors.

Bad psu
Bad memory
Overheating
A program taking up to much resources Ie: memory leak.

try runing the machine on one stick of ram,and run memtest on it. if it passes pull it out run the next stick do this till all the sticks are checked.

Once that done run them all together,and run memtest again.

another option is to run the machine on another distro to see if the same issue happens.

---

### Post by danfluidmind on 2007-03-15
Thanks guys. I just ram Memtest86 and there were no errors. But both of you are suggesting that it must be some kind of hardware problem. We have a spare of this computer (10 of us use them here) so I'm gonna put my hard drive in the spare and see if it does the same thing.

Thanks
--Dan

---

### Post by John.Michael.Kane on 2007-03-15
Like i said you can always download another distro,and run it through. This will allow you to see if it does the same things with regards to ramdom rebooting.

I'm not trying to say that the problem could not be software based,however. if it was you should see some errors on rebooting or in your /var/log/crash reports folder.

---

