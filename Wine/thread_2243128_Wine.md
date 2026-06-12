---
title: "Wine"
date: 2014-09-06
forum: Wine
---

### Post by jenny8 on 2014-09-06
I am brand new to ubuntu/linux. I am not very computer savvy, my husband is but he's at work at the moment and he's also new to ubuntu. I know I'm needing Wine and I'm on the website for it and it's asking me to choose an application for the 1.6 version, what does that mean? What do I need to do?

---

### Post by EuclideanCoffee on 2014-09-06
Welcome to Ubuntu! :)

Wine is a way to use Windows binary for Linux! If that sounds confusing, don't worry. You're well on your way to learning. First, you should figure out what you need Wine for. If you just want to see what you can do, I recommend PlayOnLinux since it's easier to get started with.

Go to your Ubuntu Software Center. You should find it in your launcher (or something similar to your start button for Windows). The software center is often an orange shopping bag icon.

Once you are there, go to the search bar. Look up PlayOnLinux. Install it.

Once it is installed, you should be able to launch it either from the Software Center or from your launcher.

Here you will be able to install new software running with wine. Click on the install icon. Search the library. If there's something you need but can't find, you can google "winehq [software]" to find what you need to do to configure it. This might take a lot of time, but I'm sure you will figure it out.

Good luck!

---

### Post by adec2 on 2014-09-08
I second what ruze said Jenny...PlayOnLinux is a great way to get to terms with wine without being gazumped by jargon :) Plenty will help you here with wine if you need any help

---

### Post by Claus7 on 2014-09-08
Hello,

> **jenny8 said:**
> I am brand new to ubuntu/linux. I am not very computer savvy, my husband is but he's at work at the moment and he's also new to ubuntu. I know I'm needing Wine and I'm on the website for it and it's asking me to choose an application for the 1.6 version, what does that mean? What do I need to do?

in ubuntu trusty the version of wine I'm using by issuing the command:

```
wine --version
```
is:
> wine-1.6.2

So I guess that your husband wanted you to verify that the version of wine should be >1.6 in order for the application to run.

Regards!

---

### Post by Mark Phelps on 2014-09-09
> I know I'm needing Wine for what apps?

BEFORE you do a lot of work with Wine, go to the WineHq website, use the Application Compatibility tool and look up the apps and versions you want to use.  Anything not listed, or rated lower than Gold, is most likely NOT going to work well enough to be useful.  If none of your apps have Gold ratings or better, you're basically wasting your time installing Wine.

---

