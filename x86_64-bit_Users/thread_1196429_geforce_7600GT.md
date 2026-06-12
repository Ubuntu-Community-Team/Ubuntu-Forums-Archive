---
title: "geforce 7600GT"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by hammergil on 2009-06-24
Ok, I am trying to switch over from Debian to Ubuntu except one issue.  I can't get my video card working!  I got it working using "the debian way" instructions under debian.  But, I have read and read and tried methods that worked for others but can't get it to work right.  I am wondering if it has to do with my kernel and kernel headers not matching, but i don't understand how to tell.  It doesn't seem like the headers use the same exact numbering for the kernel.  Under Debian they were exactly the same so it was easy to match up.  That may not be my issue at all...anybody with enough patience able to help me?

---

### Post by keplerspeed on 2009-06-24
It appears that the nvidia-glx-180 package supports the GF9600GT.

So go to system>administration>hardware drivers. The 180 nvidia driver should appear there. Simply active and reboot!

---

### Post by hammergil on 2009-06-25
it is no longer there.  that was the first option I tried, but it didn't work.  brought my resolution down to 640 x 480.  I deleted everything nvidia and tried to install driver from nvidia's website.  That didn't work either.  I never saw an nvidia splash screen with either method.

---

### Post by keplerspeed on 2009-06-25
You shouldnt see a nvidia splash screen, I dont, and I am using the nvidia-180 driver. Go to synaptic and install nvidia-glx-180 then try hardware drivers.

---

### Post by hammergil on 2009-06-25
should i install nvidia-glx or nvidia-glx-dev

---

### Post by hammergil on 2009-06-25
185.18.14 is the driver that i am running.  the nvidia x server settings tool is behaving weird.  when i try to click on a button, the window moves.

---

### Post by hammergil on 2009-06-25
Wow!  Finally got it done!  Here is what i did (I am a newb, so some of this may be unnecessary...):
1)  Got rid of my old linux-header and my old linux-image (don't know if that was part of the problem or not.)
2)  Downloaded the 180.60 driver from NVIDIA's website to my desktop instead of the current 185.18.14 (apparently the newest driver was the culprit)
3)  right clicked on the file and selected preferences.  Then checked the box enabling it to be run as an executable file.  Closed window.
4)  control+alt+F1 
5)  Logged in and entered password
6)  logged out of X and gnome by typing:  sudo /etc/init.d/gdm stop
7)  changed directory to Desktop:  cd Desktop
8)  to select nvidia driver file:  sudo ./N(then hit tab to auto-fill the rest of the file name)
9)  enter to execute
10)  Affirmative to all of the prompts including to rewrite X config (default on that is no)
11)  once back to a command prompt type:  sudo /etc/init.d/gdm start
12)  should see an NVIDIA splash screen and you are done!!
13)  Hope it works for you too!:D

---

