---
title: "need some help / advice for drivers"
date: 2008-07-07
forum: x86 64-bit Users
---

### Post by spezticle on 2008-07-07
This is my motherboard:

[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2722&ProductName=GA-MA770-DS3](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2722&ProductName=GA-MA770-DS3)

I've installed ubuntu 8.01 or .04 (i forget which is the latest, you get the idea)
Everything seems to be working alright, but i was just wondering if there are drivers to get the most out of my hardware, or if the default drivers installed just 'work'

I have a nice nvidia card, and the drivers from nvidia, but gigabyte doesn't really help much with the linux aspect.

---

### Post by jocko on 2008-07-07
In linux, most of the drivers you need are already built in to the kernel.
One exception is nvidia graphics cards, but I see you already managed to get the proper drivers for that...
So, as long as everything is working, there is nothing you need to do. You have the best available drivers already.

And there is no "8.01" release, only 8.04 (which has that number because it was released in april 2008).

---

### Post by Sef on 2008-07-07
Unless you have some special hardware or need the latest driver for product x, the drivers in the kernel will do fine.  No need to update the kernel, especially on a production machine.

---

### Post by stchman on 2008-07-07
> **spezticle said:**
> This is my motherboard:

[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2722&ProductName=GA-MA770-DS3](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2722&ProductName=GA-MA770-DS3)

I've installed ubuntu 8.01 or .04 (i forget which is the latest, you get the idea)
Everything seems to be working alright, but i was just wondering if there are drivers to get the most out of my hardware, or if the default drivers installed just 'work'

I have a nice nvidia card, and the drivers from nvidia, but gigabyte doesn't really help much with the linux aspect.

Stick with what the kernel provides you.  If it works then use it.

---

### Post by spezticle on 2008-07-15
thanks everybody :)

one thing i don't understand though, is when i install my nvidia drivers, they work... until i reboot.

when the gdm starts up, i get a msg box that pops up 'you are running in low resolution mode' and my nvidia drivers don't seem to be working.

i reinstall the drivers, and it'll display fine... of course, only till i reboot again. i know my error must be somewhere in where the drivers setting are saved to or something along those lines...

any insight to this issue would be much appreciated :)

---

### Post by darkknight045 on 2008-07-17
I had this problem with my system as well.

All I did was install EnvyNG to get the correct Drivers in place, along with other steps that need to be taken to correctly install the drivers.
To Install:
```
sudo apt-get install envyng-gtk
```

or you can follow these steps (I haven't tried these but they appear to work):
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIAxxxx.run
Let driver configure the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx
```
sudo apt-get install build-essential
```

---

### Post by spezticle on 2008-07-18
> **darkknight045 said:**
> 
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIAxxxx.run
Let driver configure the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx


Actually, the way i DID install the drivers was with the second way, the way in which i have quoted. But.. i didn't follow up with the code part below:
```
sudo apt-get install build-essential
```

I'll see what happens, and also try your first suggestion. Thanks!

---

