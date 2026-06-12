---
title: "[SOLVED] downloading speed in 64bit ubuntu is very very slow..."
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by luckyyyyyy on 2008-05-07
ok...i did it...means i have installed 64bit ubuntu on my Dell 6400...and i don't have any problem...same as like 32bit ubuntu...but more smooth than 32bit ubuntu...all drivers are 100% working...

but i felt one problem...actually not a problem but something wrong...in 32bit ubuntu...when i installed extra softwares from add/remove or from sympt then the downloading speed is very fast...1 mb/s, 2mb/s, etc...connection to ubuntu server is very fast...but in ubuntu 64bit that speed is very very slow...only 20kb/s , 10kb/s.......it takes very long time to connect with ubuntu server...i don't know whats the problem...i think LAN driver problem...but downloading speed from firefox is very fast...

may be ubuntu server for 64bit version is slow...

what is the problem...can anybody help me...why downloading speed from ubuntu server the is very slow...

thanks...

---

### Post by Jouke74 on 2008-05-07
There are many websites on the internet that can test your internet speed. Just pick one to check your connection speed under 64 bit. 

Furthermore, you write that your Firefox speed is fine, which indicates to me that the internet connection is fine as well. That leaves a slow Ubuntu server. Given that people are downloading Hardy and new updates, this might make the connection a bit slow (although your speeds are terrible). 

To solve this you can select a different server, and even ping for the best one. 

To do this start "Synaptic package manager" 

Then in the menu click on Settings > Repositories. 

Now on the Ubuntu Software tab click on pulldown menu of the server you are currently using. 

Select "Other"

This will bring a new menu.

Then click "select best server". 

Wait until all ping tests are finished and use the best one from now on. Keep in mind the next two in case you get a busy server again. Most likely the best server is also closest to home, but mileage may vary.

---

### Post by luckyyyyyy on 2008-05-07
thanks i have solved....best server for me is newzeland...

much thanks...

---

