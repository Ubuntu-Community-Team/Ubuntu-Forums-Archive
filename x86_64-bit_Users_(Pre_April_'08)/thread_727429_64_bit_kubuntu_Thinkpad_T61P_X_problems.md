---
title: "64 bit kubuntu Thinkpad T61P X problems"
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by dokdoom on 2008-03-17
Hi everyone, I have a Thinkpad T61P that would love to run some Kubuntu gutsy. I want to use the 64 bit OS to take advantage of all my RAM. Here is my problem.

After the install is completed (Alternate CD) it spits out the CD, rebooted, but the screen was absolutely blank. X was broken, I wasn't worried because thinkwiki said this would happen. The nv driver will not work with this particular card (nVidia Corporation Quadro FX 570M) and that is why X will not start right up. It said to go into recovery mode and edit the xorg.conf to change the driver from nv to vesa. I did this but after rebooting, X will still not start. I checked my xorg.conf and the driver was still vesa. So everything saved. 

This leads me to believe thinkwiki's install guide was based on a 32 bit system. My question is, how do I get X to start if not with the vesa card. I have googled and searched through the forums here and haven't found anything helpful besides changing the driver from nv to vesa which I did already. Any help will be appreciated.

Thanks

dokdoom

---

### Post by dokdoom on 2008-03-17
I believe I solved my own problem. I booted up to recovery mode and ran 

sudo dpkg-reconfigure xserver-xorg

I rebooted thinking I was very clever and nothing happened. I booted back into recovery mode and just for S and G's I ran 

/etc/init.d/kdm start 

and what do you know... it started. I'll post back if I run into anymore problems.

---

### Post by dokdoom on 2008-03-17
With a working X I was able to install the nvidia restricted drivers. I plugged in my monitor and configured that with nvidia-settings and everything was looking pretty good. I restarted X several times to see if everything would come back and it did. Then I rebooted the machine and it went back into the black screen. So now why in the world with a working video driver would I still be getting the black screen? Any thoughts? 

/goes to check logs

---

### Post by prince_niceguy on 2008-03-18
wierd. but is your kdm starting? in the recovery console try to start the x server and see what error it is giving?

---

### Post by dokdoom on 2008-03-25
At first, I was able to start kdm with

/etc/init.d/kdm start

I configured my Monitor and with xinerama was feeling pretty good. But even with the restricted driver, when I reboot it went back to the black screen. For now I'm just using 32 bit, but when I get some time and read some more I'll give it anotherr try.

---

