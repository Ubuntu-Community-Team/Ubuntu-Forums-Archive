---
title: "Please help? Last update killed my Kernal."
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by MiD-AwE on 2006-02-25
Please help?

I'm still very new with UBUNTU. I've been using Xandros 3 since I gave up Windows. But, I felt comfortable with debian so I decided to try Ubuntu after my dislike of the debian cog-like GUI. I love Ubuntu. But, after the last update my system said it needed to update the linux kernal, so I let it. Then it said I needed to reboot, so I did. But, in stead of rebooting after selecting Ubuntu in Xandros boot manager I recieved this error:

[INDENT]Preparing Ubuntu 5.10 on HDA3
Loading kernal... EBDA is Big;
  
kernal setup stack overlaps LILO second stage
  
[/INDENT] And, nothing more. I see a strip ate the top of the screen that is many colors but is unintelligible. The system hangs right there indefinitly I believe since I left it for a few hours incase it was doing something and I was unaware.

Is there any help? I don't want to lose all of my personal data if it can be helped. So, I'm using the live CD version now.

---

### Post by trigg on 2006-02-26
Sounds like Ubuntu tried to overwrite your boot manager - or your boot manager is calling the wrong kernel.  Do you still have access to your Xandros install?  It sounds like it uses lilo - so boot into Xandros, modify your /etc/lilo.conf file to update to the most recent Ubuntu kernel that was installed, run lilo again and reboot.  If you can't boot into any system, you will probably need a live cd (ubuntu works well), so you can get into the system to fix it.

---

### Post by MiD-AwE on 2006-02-26
Thanks, I've got it working.

---

