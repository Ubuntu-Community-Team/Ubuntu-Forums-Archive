---
title: "Weird Wine error while installing?!"
date: 2012-07-04
forum: Wine
---

### Post by frash23 on 2012-07-04
Hello ubuntu forums, i have a new question!
I followed this tutorial:
[http://linuxforums.org.uk/index.php?topic=10003.0](http://linuxforums.org.uk/index.php?topic=10003.0)
But when i run ./configure (i tried ./tools/wineinstall too)
i get this error:
[IMG]http://i.imgur.com/t6WMT.png[/IMG]

Can somebody help? :S

I am using ubuntu 10.04, installed with the minimal CD, and installed gnome-desktop-enviroment package.

Thanks in advance!

How i solved it!
msammels' post worked, its just below :)

---

### Post by msammels on 2012-07-04
I'm assuming you're trying to build it from source. It might be easier for you to install from the repos if you don't need to the latest:

```
sudo apt-get install wine
```

However, if you do want to build from source, do:

```
sudo apt-get build-dep wine
```

That should get most if not all dependencies, including X.

---

### Post by frash23 on 2012-07-04
Will this work with wine 1.5.8?

---

### Post by msammels on 2012-07-04
No, the above commands will install the latest version of WINE, which I believe is well into the 2.x now.

---

### Post by dino99 on 2012-07-04
> **frash23 said:**
> Will this work with wine 1.5.8?

you can get 1.5.8 here

[https://launchpad.net/~ricotz/+archive/staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal](https://launchpad.net/~ricotz/+archive/staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal)

---

### Post by Elfy on 2012-07-04
*Thread moved to **Wine**.*

---

### Post by frash23 on 2012-07-04
The command from msammels does work!
And btw, wine 1.5.8 was release today :/

---

### Post by frash23 on 2012-07-04
If possible, please let a mod close this thread, since it is solved!

---

