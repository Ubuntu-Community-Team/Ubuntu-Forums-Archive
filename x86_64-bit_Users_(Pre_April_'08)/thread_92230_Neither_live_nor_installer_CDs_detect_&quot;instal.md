---
title: "Neither live nor installer CDs detect &quot;installer components&quot;"
date: 2005-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by echapin on 2005-11-19
I am coming from a mostly redhat/fedora core background and wanted to give (K)Ubuntu a shot on my new AMD 64bit machine since fedora was giving me a headache.

I downloaded and burned the Kubuntu 5.10 x86_64 ISOs (from the "Europe" mirror if I remember correctly), having first verified the MD5SUMS. 

I started up the live CD, hit return, chose language / location / keyboard and it appeared to be doing its thing. I believe it stated that it was doing hardware detection (appeared to go OK). Then I got this message "Unable to load Installer Component". Basically I seem to be getting the same thing as in another post: [http://www.ubuntuforums.org/showthread.php?t=87844](http://www.ubuntuforums.org/showthread.php?t=87844)
Unlike that post, I am using the live cd, not the installation cd - so the answer to that post (ubuntu doesn't want to overwrite an existing linux distro) shouldn't apply?

For reference there is currently a Fedora Core 3 distribution on my hard disk (which I plan to wipe), as well as Windows XP. In case it may be helpful:

1. I first installed fedora core 3 32bit temporarily. Had issues updating the system.

2. Tried installing Fedora Core 4 - interestingly the install CDs also had problems with the CD drive (couldn't detect it - I checked the media etc. and everything looked OK) - the most likely explanation seemed to be that I had my CD drive as a primary IDE slave device (no master primary IDE - my hard disk is SATA). Tried changing the jumper to make the CD the master, but no improvement. I gave up with 64bit FC4 at this point.

3. Went back to Fedora Core 3, this time trying the 64bit version, was able to install the system, but on the first boot X puked (frozen screen). I have an nvidia video card, and I suspect that by getting the nvidia kernel module I can get it to work, but I thought it would be fun to try a different distro...

Any suggestions? Is there any other diagnostic information that would be helpful?

thanks

---

### Post by gsus777 on 2005-11-20
I had the same issue and solved it by using "expert" mode and when getting prompted for hdparm entering "-d 1 /dev/hda1". This turns DMA on. In some dvd drives this is required to work with the linux driver. Benq and Plextor are affected, others I don't know.[COLOR="DarkOrange"][/COLOR]

---

### Post by n00b on 2006-01-18
> I had the same issue and solved it by using "expert" mode and when getting prompted for hdparm entering "-d 1 /dev/hda1". This turns DMA on. In some dvd drives this is required to work with the linux driver. Benq and Plextor are affected, others I don't know.

Ok at what point in expert mode does this happen? Can somebody walk this trough with me. I've been as far as i can go with expert mode but still get the error "Unable to load Installer Component" at one point of the install it says that it sucessfully mounted the CDRom but clearly this is not the case. 

I'm so keen to try out (k)ubuntu. I hope this annoyance doesn't stop me.

---

