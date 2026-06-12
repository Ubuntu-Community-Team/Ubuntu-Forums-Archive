---
title: "Problem After updates"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by Lilszamora on 2008-10-16
after the updates today, my computer no longer allows me to use the nvidia-settings as I usually do.

my screen with from being 1280x800 to 800x600

any thing that could help would be great.

---

### Post by steveneddy on 2008-10-16
As has been mentioned on many threads, just boot into the -19 kernel.

While booting, at GRUB hit the ESC key and select the kernel version ending in -19.

---

### Post by 4Play on 2008-10-16
I also has problems with the new kernel, but in a attempt to fix them, i reinstalled the nvidia drivers (this fixed the display perfectly, resolution back, compiz) but now I am having other problems, like VmWare Workstation wont start...and I really need it!
To my despair, the -19 kernel cant startX anymore...i think this is due to my nvidia driver re-installation on the new kernel. I can only log in on the -19 in text mode...and I don't know how to fix the display!

I understand the need to test new kernels, but seriously, I cant call a system reliable if after a update all these problems happen, and exactly on the one day that I really needed everything working. If it causes this many problems, it shouldn't be included in the standard updates.

Anyway, if someone can give me some tips on how to startx on the -19 kernel (or fix vmware on the new one :p ) I would be eternally grateful

**update: I fixed vmware on the new kernel, so I guess ill just forget about -19. Turns out I was incorrect in blaming the kernel update for my woes, as several programs require recompiling when the kernel is updated (i.e Vmware Workstation) [here]("https://help.ubuntu.com/community/VMware/Workstationware/Workstation") are instructions in case someone is interested. However, I still think that due to this required reconfiguration, the kernel update should be separated from the regular everyday updates, or at the very least provide a warning message informing that a kernel update is going to be downloaded, so this can be avoided at critical moments.

---

### Post by drchandra2 on 2008-10-20
I also made updates today and after the restart, I couldn't run Gnome anymore. After some random guesses what might have happened I issued:

sudo startx

and it worked, so the problem concerns my user account only..
So at least X can be started somehow. 

Hope to se a good solution from ubuntu support soon...

---

### Post by rmhamm on 2008-10-20
Same issues here.
Mine wouldn't let me get into xserver at all. I tried to fix with recovery mode but that said my xserver was missing or not installed. I figured it was screwed up so this is what I did and I don't recommend it because I don't know if it was the right course of action.

boot up and do a login
sudo apt-get remove xserver

then
sudo apt-get install xserver-xorg

Worked for me but I had to reinstall my nvidia drivers then also some other stuff got buggy like awn and compiz. Still can't figure out compiz but I'm sure I'll get it soon enough.

If anyone has a better method please let me know.

---

### Post by drchandra2 on 2008-10-21
It looks like a conflict between Gnome and KDE. I reinstalled KDE, setting Gnome as default, then logged to gnome, set gnome as default (again..) and login window as gnome. Now I can log in and I got my desktop, however with empty applications menu (so I had to copy the applications.menu file and other menu files from \etc\something). I still can't solve the problem with disappearing bars when I press "red shutdown button". Any ideas ?

-19 kernel makes no difference here

I've never had such problems with Suse an RedHat. I guess I'm going to say goodbye to Ubuntu. Two working days lost already.

---

