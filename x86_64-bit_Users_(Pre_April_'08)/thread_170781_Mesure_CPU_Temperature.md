---
title: "Mesure CPU Temperature"
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by mpthree on 2006-05-05
Hello I'm not a fulltime Ubuntu user but I have tried the Ubuntu 5.1 Live-CD sometimes. As you all probably know in Mac OS X Tiger you can't mesure the temperature of your CPU if you use a mac with a G4 (PPC 7400) Well I still use a G4 and I want to know what my CPU temperature. So I wonder if it's possible for me to boot using the Ubuntu Live-CD that I got and simply install a software that can mesure my CPU temperature. Is this possible, if it is tell me what to do and how to install. Linux isn't my cup of tea, yet ;)

It's my first post to!

---

### Post by henriquemaia on 2006-05-05
Hi,

I'm not sure if there are better ways of doing it, but you can read this thread ([http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors)](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors)). Although this can be a bit confusing for a begginer. 

If you got that part of the configuration right, than you go to **System** --> **Administration** --> **Synaptic Package Manager** and install **sensor-applet** package.

After that, you right click on the panel bar and choose **Add to Panel**. Select the sensor applet. If everything is working ok with sensors, you'll get the temperature of your CPU.

Those were the steps I followed. Hope this helps.

---

### Post by mpthree on 2006-05-05
Man you where fast!
Okay I will try that now, stay tuned...

---

### Post by Entity on 2006-05-05
Maybe this will work for you : [http://ubuntuforums.org/showthread.php?t=161352](http://ubuntuforums.org/showthread.php?t=161352)

---

### Post by mpthree on 2006-05-07
[QUOTE=henriquemaia]Hi,

I'm not sure if there are better ways of doing it, but you can read this thread ([http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors)](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors)). Although this can be a bit confusing for a begginer. 

If you got that part of the configuration right, than you go to **System** --> **Administration** --> **Synaptic Package Manager** and install **sensor-applet** package.

After that, you right click on the panel bar and choose **Add to Panel**. Select the sensor applet. If everything is working ok with sensors, you'll get the temperature of your CPU.

Those were the steps I followed. Hope this helps.[/QUOTE]
I tried this today and it didn't work out so well. I don't understand what I should do on step 2-C, could anyone explane what to do?

But when I runed sensors-detect it actually found 5 sensors (smbus) so this must be good. So I made to step 4 after that it's getting complicated.

**Edit**: I aslo don't understand what I should do after running the sensor-detect. It says *Then, run /etc/init.d/module-init-tools*?

---

