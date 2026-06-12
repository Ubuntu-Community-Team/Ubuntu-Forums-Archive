---
title: "windows app installed, works but still shows blank page"
date: 2008-10-28
forum: Wine
---

### Post by spidersilver on 2008-10-28
I've installed an application called 'micro niche finder' and as part of the installation prompted to have wine install gecko for me.
Now, the app works as it responds with different popup windows asking for captcha and such (that I can see and input data into), but the main app screen is blank.
I don't think the app uses any special font because I see no such file in the program files directory for the app. I've also tried different windows emulators within wine but I'm sticking with the XP one since it has the app working. It's just that blank screen that's driving me nuts so it might be a gecko thing.

I'm on Ubuntu 8.04 with gecko 1.0

I've finally moved to Ubuntu after wanting to do so for years so please regard me as a newbie on linux when you post your response.

Thanks

---

### Post by lunarcloud on 2008-10-28
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

try following that...

thats, open terminal 

Applications->Accessories->Terminal

copy paste

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add
```enter (type password at some point)

copy paste
```
 sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```
enter

copy paste```
sudo apt-get update || sudo apt-get dist-upgrade
```
This will upgrade you to the latest version of wine.Close out of Terminal now.***

try your application now. Might help.

Also, if desktop effects are turned on, that might be a problem. Try turning desktop effects off.

---

### Post by spidersilver on 2008-10-28
Thanks, but I'm already using the latest wine version 1.1.7
Again, the app works it's just that I can't see a thing since the app's main screen is blank.
It's more of a viewing problem than a getting an application to work type of a problem. That's why gecko is a suspect.

Anyone on how to get the latest gecko version and tweaks to it to get the screen to work?

---

