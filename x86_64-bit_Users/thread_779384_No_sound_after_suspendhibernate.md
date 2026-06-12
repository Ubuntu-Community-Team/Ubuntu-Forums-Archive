---
title: "No sound after suspend/hibernate"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by amrlima on 2008-05-02
Hi all,

I have a athlon 2Core with a Geforce 6100 running hardy. After suspend and hibernate sound does not work. It used to go just fine on Gutsy and Debian Lenny. Anyone experiencing the same?

---

### Post by knight.rider on 2008-05-03
> **amrlima said:**
> Hi all,

I have a athlon 2Core with a Geforce 6100 running hardy. After suspend and hibernate sound does not work. It used to go just fine on Gutsy and Debian Lenny. Anyone experiencing the same?

I am.

Still looking for a solution. I don't remember if the same happened in Gutsy...

---

### Post by soxs on 2008-05-03
Same for me, this keeps bothering me since edgy -.-

---

### Post by studo77 on 2008-05-03
me too... gutsy was the same.

The solution, i think, will not come. So many have problems with the suspend/hibernate, and for a long time. Best solution: Find hardware where it works.

---

### Post by formanner on 2008-05-03
I can't take credit for it, but googling around, I found this. It worked on my Toshiba A215. It's instructions on creating a script that runs before and after sleep that will properly shut down the sound and restart it correctly.

[www.faker.com]("http://www.fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/")

---

### Post by El_Perro_Perduto on 2008-09-10
Same problem.  Hibernate disables sound.
I'm running Hardy on my Toshiba Sattelite AMD 64 x2.  :mad:

I don't like having to reboot all the time.

---

### Post by captain_rob on 2008-10-29
I had the same problem and got mad of rebooting everytime. Now I use this workaround: type or copy in terminal after suspend/hibernate:
#sudo /sbin/alsa force-reload

---

### Post by philinux on 2008-10-29
Yep I've been using

```
sudo alsa force-reload
```

for some time now. The only thing is it crashes firefox if it's running so I use the above as soon as I wake the machine up. If I remember. :)

---

### Post by fabbaz on 2008-11-05
> **formanner said:**
> I can't take credit for it, but googling around, I found this. It worked on my Toshiba A215. It's instructions on creating a script that runs before and after sleep that will properly shut down the sound and restart it correctly.

[www.faker.com]("http://www.fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/")


this worked great, thanks for the link!
just one problem left: when coming back from suspend, the metacity theme is changed, into the theme normally used only when starting an app with sudo. also, the icons are set to gnome theme. i have no clue how this can be related, but this always happens also when restarting alsa manually.
it curiously is automatically fixed when opening the theme-settings.
i use xfce, but tried and have the same problem in gnome.

---

