---
title: "Screen resolution and refresh rate nightmare"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by kabel_kabel on 2008-04-25
I have several questions to ask because there is no official help for ubuntu 8.04.

-	How I can get to nvidia’s configuration GUI (in 7.10 was ‘nvidia-settings’)
-	When the official documentation is going to be up and running
-	I used ‘Hardware Drivers’ option from System --> Administration menu to install the nvidia drivers, so this shows that the nvidia drivers are installed and running
-	The reason why i’m asking for nvidia’s configuration GUI utility is that i have problems with the screens refresh rate, it seats at 50 Hz no matter what i’m doing to increase it. I had the same problems with 7.10, i was using nvidia’s gui to set the proper screen resolution (Hanns.G 28” 1920x1200) and refresh rate; on the next restart back on 1440x900 and 50 Hz; tried with modifying xorg.conf, on next restart back on 1440x900 and 50 Hz again. I decided to wait on improvements with 8.04, i made clean install of 8.04 and now the resolution is correct but the refresh rate seats at 50 Hz.

Thank you in advance
Kabel

---

### Post by milosz.galazka on 2008-04-25
You can type in console:
```
sudo apt-get install nvidia-settings
```
to install nvidia settings utility.

---

### Post by kabel_kabel on 2008-04-25
Thank you milosz.galazka, i will try that.
Another thing, what is the difference between nvidia-settings and nvidia-xconfig. In the past I have tried nvidia-settings command from the terminal which opens up the gui for changing some parameters of your video card, but not nvidia-xconfig.

Kabel.

---

### Post by milosz.galazka on 2008-04-25
nvidia-xconfig is to help you change X configuration to use nvidia driver (look [here]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/chapter-03.html"))
nvidia-settings just to tune resolution and settings.

I used nvidia-settings to set my X resolution and [changed]("http://ubuntuforums.org/showpost.php?p=4791059&postcount=2") /etc/X11/xorg.conf file to get right resolution at login screen.

---

### Post by kabel_kabel on 2008-04-25
Very good sir! Thank you again!

Kabel.

---

### Post by crgutierrez on 2008-04-25
thank you!! I just got into toruble after the update to 8.04, but now I remember I had the same question when I made the first 64bit installation..... How can UBUNTU help the people like me, that NEVER remember those small details and fall into panic again and again????

---

### Post by kabel_kabel on 2008-04-26
Alright,

Just to let you know what is going on with my &#8220;Screen resolution and refresh rate nightmare&#8221;. I did not know that 'nvidia-settings' is separate package in 8.04 x64. I thought that this should be part of the graphic card drivers and this explains why I could not run 'nvidia-settings' command in terminal.

About my previous problems with setting proper screen resolution and refresh rate (ubuntu 7.10 x64), now with 8.04 x64 part of the problem is fixed. When I change the screen resolution on 1920x1200 and refresh rate from auto to 60 Hz with nvidia's gui utility and when I restart X server nvidia-settings GUI utility reports 1920x1200 and 60 Hz, which means that is not going back on 1440x900 and 50Hz. Ta-da!
When I start gnome's 'Screen Resolution' (System --> Preferences --> Screen resolution) GUI utility, I can see that is still reporting 50 Hz refresh rate with correct resolution. I thought p*** on it, I can live with it. My monitor is showing that 'nvidia-settings' is reporting correct refresh rate and I do not have time to investigate why gnome's 'Screen Resolution' is showing 50 Hz. Hopefully with next release this problem will be fixed (I do not know if my monitor can last that long :))

Thank you all,
Kabel

---

### Post by mamanga on 2008-04-26
[http://ubuntuforums.org/showpost.php?p=4803958&postcount=17](http://ubuntuforums.org/showpost.php?p=4803958&postcount=17)

---

### Post by ingvildr on 2008-04-26
Looks like your having a similar problem with the gnome display configuration tool as i was, [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/222516]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/222516"), the tool works just seems to report the wrong refresh rates with the nvidia driver.

---

### Post by kabel_kabel on 2008-04-26
Thank you guys letting me know about this bug. It seems like it is inherited from previous evolutions of Ubuntu. Lets hope for fix.

Thank you all.

---

