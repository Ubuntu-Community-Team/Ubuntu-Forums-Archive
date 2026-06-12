---
title: "gdesklets"
date: 2005-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mastor on 2005-02-14
hi!

i'm running ubuntu on a laptop with AMD64 and nforce2 and the lmsensor doesn't work i don't know why....
so i looked to another kind of display and i found the LTCandy group.
But when i try to load any module (except the clock -_-),  i've got these errors:

for CPU:
```
Traceback (most recent call last):
  File "/usr/lib/gdesklets/factory/SensorFactory.py", line 86, in create_sensor
    sensor = module.new_sensor(args)
  File "/usr/share/gdesklets/Sensors/LTVCpu/__init__.py", line 71, in new_sensor
    def new_sensor(args): return apply(LTVCpu, args)
  File "/usr/share/gdesklets/Sensors/LTVCpu/__init__.py", line 19, in __init__
    self.__model_name = libdesklets.cpu.get_model()
AttributeError: 'module' object has no attribute 'cpu'
```

and for HDD
```
Traceback (most recent call last):
  File "/usr/lib/gdesklets/factory/SensorFactory.py", line 86, in create_sensor
    sensor = module.new_sensor(args)
  File "/usr/share/gdesklets/Sensors/LTVDisk/__init__.py", line 83, in new_sensor
    def new_sensor(args): return apply(LTVDisk, args)
  File "/usr/share/gdesklets/Sensors/LTVDisk/__init__.py", line 36, in __init__
    for i in libdesklets.disk.get_partitions():
AttributeError: 'module' object has no attribute 'disk'
```

any ideas?
i think i'm missing some libs, but which?

---

### Post by Xian on 2005-02-14
[QUOTE=Mastor]i think i'm missing some libs, but which?[/QUOTE]
You didn't mention which version of gdesklets you are using, but any of the more recent releases absolutely do not work with the LTCandy group themes. In fact, to the best of my knowledge they are all but obsolete. Try some of the newer offerings and hopefully you will notice a change for the better.

To start gdesklets just issue the command "gdesklets start"
A daemon will appear in your taskbar if you have the notification area installed
Right-click and choose "Manage Desklets"

From there just use the menu items to install and run themes.

---

### Post by Mastor on 2005-02-15
[QUOTE=Xian]but any of the more recent releases absolutely do not work with the LTCandy group themes[/QUOTE]
Argh...

Well, thanks for the answer...
now i understand the problem ^^ (i've got the lastest gdesklets ... )

---

### Post by Tichondrius on 2005-02-18
Did you just say you're running AMD64 with nforce2 ?!?!?!? nforce2 is the chipset for athlon XP CPUs, which are not 64-bit. So you must mean nforce3 chipset with athlon 64, right ?

---

### Post by Mastor on 2005-02-20
oh, yes.... nforce3...  :-? 
i'm sorry, i was confused by lmsensor & i2c drivers... ^^

---

