---
title: "cant seem to get sensors-applet working"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by gsrcrxsi on 2008-06-18
so i installed lm-sensors and configured it. then i installed sensors-applet. but when i try to add it to the panel "Hardware Monitor Sensors" is not in the list. i've tried rebooting and loging out and loging back in, but still its not there. any help would be appreciated!

---

### Post by Mizzou_Engineer on 2008-06-18
> **gsrcrxsi said:**
> so i installed lm-sensors and configured it. then i installed sensors-applet. but when i try to add it to the panel "Hardware Monitor Sensors" is not in the list. i've tried rebooting and loging out and loging back in, but still its not there. any help would be appreciated!

You need to have lm_sensors detect the sensors your system has. The way to do this:

1. Run "sudo sensors-detect"
2. Follow the detection prompts (basically, type in "yes"
 a few times and look for output.
3. The last question will be "should we put the modules in /etc/modprobe?" Answer "yes" to that so the sensors' modules get loaded at each boot.
4. Load the sensor modules: "sudo modprobe -a"
5. Restart lm_sensors (sudo /etc/init.d/lm_sensors restart) and restart the applet.

If any sensors were detected, they ought to be working at this point. If not, you can either hit Alt+F1, login, and type in "sudo telinit 1" and then hit Ctrl-D to go into and back out of single-user mode (which will restart almost all running services) OR you can restart your machine.

---

### Post by gsrcrxsi on 2008-06-18
thanks for the reply, lm-sensors has already been configured, and if i run sensors in the terminal, it outputs everything fine in the terminal window, im just trying to get the applet working. 

ive rebooted, doesnt help, the hardware sensors option is not in the list to add to the panel. thats my issue. lm-sensors already works.

---

### Post by gsrcrxsi on 2008-06-19
bump

---

### Post by philinux on 2008-06-19
Seems you might be missing an xfce plugin to get gnome applets to work.

[http://www.vincentkong.com/2008/03/monitoring-cpu-and-hard-drive-temperature-on-xubuntu/](http://www.vincentkong.com/2008/03/monitoring-cpu-and-hard-drive-temperature-on-xubuntu/)

Google is you friend and mine. :lolflag:

---

### Post by noshellswill on 2008-06-19
> **gsrcrxsi said:**
> so i installed lm-sensors and configured it. then i installed sensors-applet. but when i try to add it to the panel "Hardware Monitor Sensors" is not in the list. i've tried rebooting and loging out and loging back in, but still its not there. any help would be appreciated!
SENSORS does NOT work for many mobos. The site should have a list of those supported.

---

### Post by philinux on 2008-06-19
> **noshellswill said:**
> SENSORS does NOT work for many mobos. The site should have a list of those supported.

It works fine if he runs it in the terminal. He just needs the xfce plugin.

---

### Post by gsrcrxsi on 2008-06-19
yes, lm-sensors DOES work with my hardware. ive had it working under 7.10 ubuntu desktop same hardware. thanks phil ill check out that plugin :)

---

### Post by gsrcrxsi on 2008-06-19
thank you phil! everything works now :)

---

