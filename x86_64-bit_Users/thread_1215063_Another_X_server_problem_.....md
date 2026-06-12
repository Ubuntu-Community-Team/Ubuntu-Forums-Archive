---
title: "Another X server problem ...."
date: 2009-07-16
forum: x86 64-bit Users
---

### Post by dd1linux on 2009-07-16
Hi everyone, sorry to be such a linux noobie, but I'm learning slowly.  Anyway i had ubuntu 8 for awhile and then updated to 9.04 and everything was working awesome for almost 4 months until one day my X server wouldn't start.  I figured no big deal, and did a fresh install.  Then I did the update manager thing, and restarted.  Next, I wanted to get my graphics working (I have two 8500GT;s).  So i did what i did the time before that by going to the restricted drivers thing and downloading and installing the recommended 180 driver.  now i get no x server. Error message is as follows:

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
(EE) No devices detected

Fatal Error:
No screens found

please consult at  yada yada yada
also check log at yada yada

I am not a complete beginner and like i said i have done this before and even ran into almost the same problem and fixed it but ive been workin on this one for two or three days and have made no progress.  Please help me, either on here or email me at [email]dd1123@txstate.edu[/email].  I would be so appreciative!

P.S.: I'm sure more details will be needed to solve the problem, so let me know anything that could be of assistance.

---

### Post by dagrump on 2009-07-16
Look for "GUI doesn't load after installing nvidia" it's about 4 pages deep, that might help.

---

### Post by dd1linux on 2009-07-16
alright I read all that, but the problem still persists.  I tried:

sudo /etc/init.d/gdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get update
sudo apt-get install envyng-core
sudo envyng -t
sudo nvidia-xconfig
 - then hit 1 to install the 180 driver (again i suppose?)
 - then restarted the computer with no luck

did i miss something in the link you directed me to?

P.S.:  I tried a few more things, and got rid of a few errors the only one that is still there is no screens found and [EE] no devices detected

---

### Post by dagrump on 2009-07-16
Are the cards in SLI? If so I explain how to set them up part way down the page.

---

### Post by dd1linux on 2009-07-16
Well, i tried what you said and it didnt work out.  I got the same error message.  However, I tried the older kernel and voila! i have perfect picture.  I forgot to mention I have been in this situation once before (that probably would have been useful, i know ...)  Anyway, can you help me make it so it works on the newer kernel as well.  I dont understand why one would work and the other would not, they both use the same xorg.conf, right?

P.S.:  Although I do have an SLI setup, both monitors are plugged into the same card.  I dont know if that is useful.

P.S.S:  after rebooting, graphics wont come up on either kernel..   :( please help

---

### Post by dd1linux on 2009-07-16
I am willing to start over from scratch, if anyone will tell me how to get my graphics working again.  I had ubuntu running GREAT for atleast 4 months and loved it, now im just confused ....

---

### Post by dagrump on 2009-07-19
Did you get this sorted out? I see you started a new thread with no takers. I'm sure if you treat this 2 separate issues it will be easier. 
1. install & configure the drivers.
2. figure out xorg mods for twinview.

---

### Post by dd1linux on 2009-07-20
yes i did get the problem solved!  I edited my xorg.conf by finding a few random examples on the internet.  Slowly, over the course of three or four days i elimated error by error. the final one was that there was a kernel mismatch, so i downloaded an earlier version of the nvidia driver to match my kernel module version and it worked.  Next, i upgraded to the 180 driver and everything worked!! hooray!  linux is crazy, but im determined to not need windows anymore (except for netflix watch instanty).  Thanks for asking though, I wasn't receiving much help.  

P.S. Im about to start a new topic on getting fruity loops 7 working in wine (I have the program running, but it's not reading most of the wav files, they are in red) if you could help with that, that would be awesome.

---

