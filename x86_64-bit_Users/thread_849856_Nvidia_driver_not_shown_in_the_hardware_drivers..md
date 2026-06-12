---
title: "Nvidia driver not shown in the hardware drivers."
date: 2008-07-04
forum: x86 64-bit Users
---

### Post by greythorne on 2008-07-04
Dear All,

I am having problems installing Nvidia drivers in Ubuntu-8.04 x64.

I clicked on the hardware drivers so that the Nivida restricted drivers would be listed but it was not listed.

Any ideas how to resolve this issue.

Thanks

---

### Post by Sef on 2008-07-05
What NVidia card do you have?

---

### Post by greythorne on 2008-07-05
> **Sef said:**
> What NVidia card do you have?

Its ASUS EN9600GT 512mb.

---

### Post by Sef on 2008-07-05
I found this on [Computer Shopper]("http://computershopper.com/reviews/asus_en9600gt"):

> The Asus EN9600GT is one of the first graphics cards to use nVidia's new GeForce 9600 GT chipset. 

I don't know if NVidia drivers will work with your card.  I will let someone else answer that.

---

### Post by greythorne on 2008-07-05
> **Sef said:**
> I found this on [Computer Shopper]("http://computershopper.com/reviews/asus_en9600gt"):



I don't know if NVidia drivers will work with your card.  I will let someone else answer that.


Thank you.

I must mention that i did install manually by downloading from Nvidia website. But after a shutdown and restart i got an error saying that Ubuntu is working in a lower resolution so what i did was to uninstall the nvidia driver and for the time being using Ubuntu with graphics driver.

Any help on this is much appreciated.

Thank you once again.

---

### Post by nikgare on 2008-07-05
Maybe the drivers didn't install properly?
You can install via the repos by selected either:

nvidia-glx-new 
  (-new in my case, but thare are others there)

envyng-gtk

both of these will get you an (fairly) up to date nvidia driver installed

---

### Post by tenmoi on 2008-07-05
Maybe the repo driver doesn't support your card just yet. So the only way is to install manually. Your first attempt at it failed may be because you hadn't had everything set up well in advance.

1. sudo apt-get update && upgrade && sudo apt-get remove --purge nvidia-* linux-restricted-modules*

2. sudo apt-get install build-essential libxft-dev.

3. Ctrl + ALt + F1

4. sudo /etc/init.d/gdm stop

5. sudo sh /path to your file .run

6. ok/accept.

7. sudo /etc/init.d/gdm restart.

Hope this'll help.

---

### Post by Tomatz on 2008-07-05
Envy will allow you to install the latest nvidia drivers with ease:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by MepisReign on 2008-07-05
I would go with tenmoi's directions, I have an 8800GT and definitely I had better results with the driver directly downloaded and installed from the Nvidia site. I'm not saying that the Alberto's script is bad, its just that my games are performing better now.

Just my opinion

Best Regards,

MepisReign

---

### Post by Tomatz on 2008-07-05
> **MepisReign said:**
> I would go with tenmoi's directions, I have an 8800GT and definitely I had better results with the driver directly downloaded and installed from the Nvidia site. I'm not saying that the Alberto's script is bad, its just that my games are performing better now.

Just my opinion

Best Regards,

MepisReign

I agree :)

Envy is just easy for new users.

---

### Post by Ghone on 2008-07-05
I also had problems with my nVidia card on Hardy x64.  Mine's an 8500 GT.  The restricted drivers wouldn't work out of the box.  Installing the drivers from the nVidia web site just made things worse and I was stuck in low res mode at that point.  EnvyNG got it all sorted out in a flash.  EnvyNG is in the repositories so it is easy to get it up and running.

---

