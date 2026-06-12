---
title: "Problem with sound system"
date: 2007-06-29
forum: openSUSE and SUSE Linux Enterprise
---

### Post by hermesrules on 2007-06-29
I hope that this post will get some attention, but the Ubuntu forums are, IMHO, by far the best linux forum on the net, hence my hope to get some ideas from here.

I'm a former Kubuntu user, but for half a year, I've been using OpenSuse 10.2. Just a couple of days ago I had to do a reinstall of the whole system, mostly due to issues of my aging laptop. I have the /home folder on an external hdd partition, connected via usb, but did some rearranging of the partitions on my internal hard drive prior to the reinstallation. Anyway, everything mounts and works properly, so this is not what I am concerned with.

After I reinstalled, I can't get any sound within my user account (only in yast while setting up my sound card, which is an oboard Ali5451, if I am not wrong), can't play movies or any music due to "error with xine-part. Initially I thought it was a xine-related error, but then I figured it was something related to the setup of my sound card. When I use KMix, it just starts up blank, and lists no mixers in the combobox. If I do this as root, however, everything works fine.

In the Sound System module in KDE Control Center, everything looks normal, until I try to test the sound. Then I get repeating artsd crash messages, but without a valid trace, which pop up so quickly on the screen that I can hardly keep up closing them. In the background, I see the message saying "Restarting Sound System", and unless I manage to press the cancel button, it keeps restarting, and restarting, while artsd keeps crashing and crashing. I can confirm this does not happen if I run KControl as a root user from within my normal user account. But does that mean I should run kaffeine as root to watch a movie or amarok to listen to music? I hope not.

Can someone suggest how I can perhaps clean my user-related setup (I don't know where that stuff is kept on the disk), and let OpenSuse configure my sound card (or sound system) properly? It does not work through Yast, or through alsaconfig (which I can only run as root anyway, and then it finds no problems)...

Thanks! And oh, I use KDE 3.5.7...

---

### Post by hermesrules on 2007-06-30
After a day of postings to different forums, I was offered one really easy solution - just to add my user account to the audio group in Yast... I had never even thought about it. But it worked, and now things are playin' :)

---

