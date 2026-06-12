---
title: "NVidia - can't enable effects"
date: 2009-09-08
forum: x86 64-bit Users
---

### Post by oospill on 2009-09-08
I've got an HP2815nr laptop running Ubuntu-64.  Graphics are NVidia GeForce 7150m.

I've got the newest NVidia drivers (180), and the NVidia XSesrver settings seems to be working jusst fine, making me think that Ubuntu IS using the drivers.

but, I can't seem to enable desktop effects.  please help!!

thanks, oospill

---

### Post by Yellow Pasque on 2009-09-09
Start compiz from the terminal and post output:
```
compiz --replace
```

---

### Post by oospill on 2009-09-09
here goes:

-----
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 
-----

(Now I'm stuck without a prompt.)

---

### Post by chris1950 on 2009-09-10
I have a compaq with a gforce 6150 go. I went thur a bunch of suggested changes all of which did not work. Finally I just reinstalled - did all updates checking System>Device Drivers untill the nvidia 180 driver was listed, I activated the driver, rebooted. After reboot I went into terminal code compiz --replace , it showed the driver loaded I then activated effects on the desktop, Everything works fine.

Hope this helps -worked for me:)

---

### Post by oospill on 2009-09-10
when you say you reinstalled, I'm assuming you mean all of Ubuntu, not just the graphics stuff, right?  

if I do reinstall, do I have to wait for ubuntu to pop up with the updates, or is there a way I can make ubuntu update?

then you said to update until ubuntu downloads version 180 nvidia drivers, then activate them in 'hardware drivers' .. then run 'compiz --replace' .. what does 'compiz --replace' do?

thanks for the help, guys
oospill

---

### Post by Yellow Pasque on 2009-09-11
compiz --replace starts desktop effects from the command-line, so you can see why they're not starting.

In this case, I would try to reinstall the nvidia driver. You might also search the web for 'compiz segfault(ing)' or something like that. Good luck.

---

### Post by punkybouy on 2009-09-12
You could try installing the driver using ENVY.

---

