---
title: "I can't install Wine...and what is up w/ this?"
date: 2008-04-10
forum: Wine
---

### Post by gwoodard on 2008-04-10
[IMG]http://ubuntuforums.org/g/images/244102/large/1_Screenshotedit.png[/IMG]

can anyone tell me what is going on?!

---

### Post by tamoneya on 2008-04-10
you have to close synaptic package manager while you run apt-get in terminal.

---

### Post by cogadh on 2008-04-10
Just to expand on that, you cannot have two different package management processes running at the same. Each package manager needs to have exclusive access to particular files in order to work, and will attempt to lock access when run to prevent other applications from trying to use them. In your case, Synaptic was already open and had locked access to /var/lib/dpkg so that when apt-get tried to acess it, it couldn't.

---

### Post by transmeta on 2008-04-11
you can't run at the same time synaptic & apt-get or aptitude. You must close synaptic to get an up-date .

---

