---
title: "How do I adjust the speeds of my fan? 8.10 x64"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by teixidoj on 2009-04-26
Hi,

 Does anyone know the command process to adjust the speeds of my fans?

Regards,

John...

---

### Post by John.Michael.Kane on 2009-04-26
You can try setting up lm-sensors. [SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto")

```
sudo aptitude install lm-sensors
```

Then try to run.
```
sudo pwmconfig
```

---

### Post by teixidoj on 2009-04-27
Thank you, but I get the following message:

File /var/run/fancontrol.pid exists. This typically means that the
fancontrol deamon is running. You should stop it before running pwmconfig.
If you are certain that fancontrol is not running, then you can delete
/var/run/fancontrol.pid manually.

 How do I stop the fancontrol deamon?

---

### Post by Jive Turkey on 2009-04-27
This is just a shot in the dark

```
sudo /var/run/fancontrol.pid stop
```

I set up my fan speeds in the bios.

---

### Post by Arup on 2009-04-28
The fan speed is auto adjusted via BIOS in case of newer Intel C2D, QC and i7 as well as AMD dual cores and Phenom. Its temperature dependant, if you turn off the feature in BIOS it would stay on full speed.

---

