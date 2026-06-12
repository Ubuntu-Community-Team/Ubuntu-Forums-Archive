---
title: "[SOLVED] Java questions"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Baby Boy on 2007-10-21
I'll get straight to it:

1.) Gutsy offers me to install IcedTea Java plugin. Can you give me some info on it and on what does it do actually - I tried it in Gutsy Beta and no Java apps worked.

2.) I was trying to get FrostWire (or LimeWire) to run in Gutsy 64bit but to no avail. When I clicked on the icon nothing happened. Nothing helped [link]("http://ubuntuforums.org/showthread.php?t=571671")

So before I start installing a whole bunch of Javas like I did the last time, does anyone have the definite answer as to what exact version of Java do I need to get FrostWire running in Gutsy64 and how do I install it?

Thanks ;)

---

### Post by rsambuca on 2007-10-21
You just need to install Frostwire from the .deb file on the site.  For the java part, you need the ia32 version:```
sudo apt-get install ia32-sun-java6-bin 
```  Then run ```
sudo update-alternatives --config java
```and select the ia32 version.

---

### Post by Baby Boy on 2007-10-22
FrostWire starts now, but there is another problem: I can't type anything in the search box! :confused:

---

### Post by Baby Boy on 2007-10-22
That's OK, I got it. Phew! :)

[http://ubuntuforums.org/showthread.php?t=519683](http://ubuntuforums.org/showthread.php?t=519683)

---

### Post by johnnybirdman on 2007-10-22
> **rsambuca said:**
> You just need to install Frostwire from the .deb file on the site.  For the java part, you need the ia32 version:```
sudo apt-get install ia32-sun-java6-bin 
```  Then run ```
sudo update-alternatives --config java
```and select the ia32 version.

I don't know if this is a similar problem or not, but when trying to view a webmin page that is a file manager where java is used, it won't open/view.  In the past I would have Firefox 32 installed but am wondering if I can avoid that.  I attempted this solution (above) but it did not work.  Do you know if there is a work around for this.  Let me know if you think I should start a new thread.

Thanks,
John

---

### Post by rsambuca on 2007-10-22
> **johnnybirdman said:**
> I don't know if this is a similar problem or not, but when trying to view a webmin page that is a file manager where java is used, it won't open/view.  In the past I would have Firefox 32 installed but am wondering if I can avoid that.  I attempted this solution (above) but it did not work.  Do you know if there is a work around for this.  Let me know if you think I should start a new thread.

Thanks,
John

You need to install the java plugin.  You will need to install the blackdown java, but it has some security issues, so be careful.

---

### Post by johnnybirdman on 2007-10-22
> **rsambuca said:**
> You need to install the java plugin.  You will need to install the blackdown java, but it has some security issues, so be careful.

Thank you for the prompt response.

Before I got your response I found this thread, [http://ubuntuforums.org/showthread.php?t=580792&highlight=blackdown+java]("http://ubuntuforums.org/showthread.php?t=580792&highlight=blackdown+java") . Don't know if blackdown or this solution is more risky,  seems to be some success with that and also shows others having blackdown problem. 

Thanks again,
J

---

