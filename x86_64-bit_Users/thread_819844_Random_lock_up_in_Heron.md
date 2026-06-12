---
title: "Random lock up in Heron"
date: 2008-06-05
forum: x86 64-bit Users
---

### Post by Heartsease on 2008-06-05
(*I searched for this issue, and saw no posting.)*
I'm dual booting on my new computer, and everything was awesome for maybe three weeks.  I was in Heron (AMD64) for 95% of the time, and loved it.  Then the lock ups started.  I really wish I could trace it to something specific, but there seems to be no rhyme or reason.  The first time was in Firefox, next time I was updating (from the desktop, not terminal), then trying to update again (this time in terminal), spreadsheets, adding apps; you name it, I bet it'll lock up.  No warning.  I even got through an update, thought that might have fixed it, no luck.

I'd love some help; mind you, I do not have an extra computer, and am posting from Windows.  So I'll have to reboot into Heron to check things.

Rad, thanks

---

### Post by Sef on 2008-06-05
I'm wondering if it is a hardware problem.  First check your ram with a [memtest86]("http://www.memtest86.com/").  You need to let it run for a few hours to thoroughly check your system, so overnight is best.  

Upon start up, boot into GRUB and select the test.

---

### Post by razvi on 2008-06-06
I don't think it's a hardware problem.
Check "System-Administration-System log-ayth.log". If there is 'unable to solve host..' error message, then you have to add 'computer name' to hosts in network configuration (with 127.0.0.1 IP address).
I've had the same problem, no administrative programs worked out (mythtv control panel, synaptic packet manager, update manager,etc.).

---

### Post by Heartsease on 2008-06-06
Unfortunately, I forgot to run memtest while at work today.  I will do that tonight.

I checked the auth.log and did not see any error messages (then it locked up when I tried to come back here).
I restarted, and under the 'messages' in 'System Log', the last thing before it restarted was:
> 
message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.bus.get.nis_domain
message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.bus.get.nis_servers
message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.bus.get.interface_mtu


Also, when I boot, at the OS choice screen, I see this:
> 
Ubuntu 8.04, kernel 2.6.24-18 generic
Ubuntu 8.04, kernel 2.6.24-18 generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-18 generic
Ubuntu 8.04, kernel 2.6.24-18 generic (recovery mode)
Memtest (*some version, i didn't write that part down)*
Other operating systems:
Windows XP Professional 


seeing the double Ubuntu at the top is a little disconcerting.
I am new to linux, but really, really want to get in.

---

### Post by Heartsease on 2008-06-07
Well Memtest was the proof in the pudding.  After running for eight hours, Tests 0-4 were fine, test 5 had 103 errors, and tests 6 & 7 had two a piece.  I will be RMAing the RAM.  Thanks for your patience.  I wish there were an easier fix.

---

### Post by Sef on 2008-06-08
Just check out which ram piece or pieces it is.

---

### Post by bpl07 on 2008-06-08
> **Heartsease said:**
> 
seeing the double Ubuntu at the top is a little disconcerting.
I am new to linux, but really, really want to get in.

Those are different kernel options, you probably wrote the numbers down wrong.  When you update the kernel, it keeps the old one in case the new one doesn't work.  You can remove the extra entries from your grub list by removing them from your menu.lst file in /boot/grub

---

