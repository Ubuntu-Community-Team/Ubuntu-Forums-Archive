---
title: "nvidia driver issue"
date: 2009-03-10
forum: x86 64-bit Users
---

### Post by g2k556 on 2009-03-10
I've just installed the latest version of 64 bit ubuntu. The install all went smoothly. I wanted to get the advanced graphics and compiz to work. So activated the restricted drivers. when I restarted, it opened in command line, I don't know any command line at all, I'm still pretty new to linux. I've enjoyed ubuntu for a while now, and I prefer gui over command line. So how would I go about getting the gui back and getting the drivers to work so I can use compiz. I believe i used version 157. any help will be much appreciated, thanks in advance.

---

### Post by klemens on 2009-03-11
you can just enable the restricted driver from the taskbar if i'm not mistaken. No terminal needed as far as i remember.

If it ain't in the taskbar just go to system -> administration it should also be there.

---

### Post by Kevbert on 2009-03-11
Try booting in Recovery Mode. You will get an option to fix X (you may need to scroll down to find xfix, if its available).  It may be that you've installed the wrong restricted display driver as you may get the option to install one of three drivers (one should be recommended). What version of Ubuntu are you using ? Intrepid or Jaunty ? What nvidia display adapter are you using ? You can get this by going to terminal and typing in
```
lshw -C display
```

---

### Post by g2k556 on 2009-03-11
I'm using the latest 8.10. It boots in command line, i login command line, i spoke with a friend yesterday, and i went and tried repair with no success. i also tried to remove the drivers, he gave me a few lines to try, still didn't work. i'm thinking i may have to reinstall it, it only takes 20/30 minutes to do. and when i installed the driver in the beginning, i went system>administrator>hardware drivers, then enabled the recommended driver.

---

