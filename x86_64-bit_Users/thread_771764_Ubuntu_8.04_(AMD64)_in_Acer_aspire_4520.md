---
title: "Ubuntu 8.04 (AMD64) in Acer aspire 4520"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by VishnuThejaJ on 2008-04-27
Hi :),

I have installed Ubuntu 8.04 (AMD64) in my laptop.

I have windows XP in one partition.

To my surprise it can detect the hardware in my laptop and installed the drivers for graphics, lan and wireless, with the help of internet i was able to download the drivers. Found graphics and lan are working fine and wireless is the only problem :(. Can any body can help me in getting this wireless installed properly. 

I am able to increase and decrease the sound through my laptop hardware and i can increase and decrease the resolution using the function key, but when i restart my laptop i need to set once again (settings are not persistant).

---

### Post by Naguz on 2008-04-29
Try this solution: [http://ubuntuforums.org/showpost.php?p=4829638&postcount=9]("http://ubuntuforums.org/showpost.php?p=4829638&postcount=9")

To set the resolution, you can download the nvidia-settings app. 
sudo apt-get install nvidia-settings (or just find "nvidia-settings" in synaptic)
then run the app with sudo priveliges (so it can overwrite the configuration file).
sudo nvidia-settings
make your changes, and press "Save to X Configuration File" then quit.

Also, you should change the title of the thread so people can see what your problem is without reading you post.

---

### Post by VishnuThejaJ on 2008-04-29
Thanks for your response, i tried to install ndiswrapper package with the help of add or remove programs it installed properly then i provided the .ini file to it then it was unable to detect my wireless adapter after restarting i got it but unable to find any wireless connections...

Just now found that when is used iwlist scan it is able to show the wireless connection available but no graphical dispaly and led is not working.

Still having problem with the backlight of the screen as this is not persistent need to set every time i restart

---

### Post by rodneymillerpca on 2009-03-30
This tut works perfect for the Aspire 4520 and Ubuntu. [http://www.hp2133guide.com/forums/viewtopic.php?p=10230](http://www.hp2133guide.com/forums/viewtopic.php?p=10230) It will have you up and running in 15 minutes or less.

---

