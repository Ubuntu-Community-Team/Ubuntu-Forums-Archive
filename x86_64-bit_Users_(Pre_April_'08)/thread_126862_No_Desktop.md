---
title: "No Desktop?"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by digitalbooyah on 2006-02-07
Hi there,

Just installed breezy on my new amd64 and the install went off without a problem. Chose mostly default settings and GDM comes up no problem, I type in my user name and password and a brown background comes up, and my mouse will move just fine, and I even hear like a start up sound, but nothing appears on the desktop. 

Hardware:

amd64 x2 3800+
nvidia 7800gt
asus a8n mobo
2gigs pc3200 ram, not sure what brand

anyone have any thoughts? I've never been a huge linux user but I have install countless distros, including gentoo, so i'm not a complete noob, just a little bit.

Thanks for the help.

Chris

---

### Post by ioannis on 2006-02-07
Hi,
I am not an expert, but I went through this 5 days ago. The problem is the nvidia card. What I did was boot in recovery mode, edited the xorg.conf file to change the Driver setting from nv or nvidia (I don't remember what was there) to "vesa". That way you'll get the graphical interface to boot. Then once that worked (although the resolution and refresh rate were horrible), I installed the new nvidia driver and re-set the xorg.conf file to "nvidia". I am sorry if the details are sketchy, but I am not sure of every step I did.

---

### Post by digitalbooyah on 2006-02-07
Thanks for the reply, I suppose I'll have to give this a shot. Irritating that it wasn't set to vesa by default if the driver is screwed up.

Thanks again.

---

