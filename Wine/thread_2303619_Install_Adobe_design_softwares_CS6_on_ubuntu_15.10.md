---
title: "Install Adobe design softwares CS6 on ubuntu 15.10"
date: 2015-11-20
forum: Wine
---

### Post by roni6 on 2015-11-20
Is that possiale? If so, how?

---

### Post by SlidingHorn on 2015-11-20
You'd have to run it through WINE.  This thread is from an older version of Ubuntu, but should be a good starting point.

[How to install photoshop cs6?]("http://askubuntu.com/questions/244795/how-to-install-photoshop-cs6/348280#348280")

---

### Post by Bucky Ball on 2015-11-20
> **SlidingHorn said:**
> You'd have to run it through WINE.

^^^
This.

And [HERE]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=25607") is its rating on WineHQ. You might also get some ideas there.

---

### Post by roni6 on 2015-11-20
I get this message...

---

### Post by yancek on 2015-11-20
The attached image isn't going to get any help.  Are you using the commands from the link posted above by slidinghorn?  If so, what output do you get after each of the commands?  Are there any warning/error messages?  If so, it would be a lot more useful if you posted any messages and what command you issued to get the result and maybe someone who uses wine would be able to help.

From the link posted by Buck Ball, if you do get it installed it probably won't work that well.

---

### Post by leunam12 on 2015-11-20
Try Playonlinux.

[https://www.playonlinux.com/en/app-2316-Adobe_Photoshop_CS6.html](https://www.playonlinux.com/en/app-2316-Adobe_Photoshop_CS6.html)

---

### Post by sandyd on 2015-11-20
> **roni6 said:**
> I get this message...
Which applications in Design & Web Premium do you need to get running - there are a number of them.

What you can do is tackle this one part as a time as some of the apps may have issues.

Since you have Design & Web Premium, you can simply download the trials for each app (Side note, a lot of developers test with the trial installer, no idea if that is any different than paid), and install each one according to the instructions on WineHQ

After the installation, signing into your adobe ID should automatically convert them into a non-trial product.

---

### Post by rocco6 on 2015-11-21
WAIT! That message is showing like that BUT IT WORKED!! It's only a bug!

---

### Post by oldos2er on 2015-11-21
Moved to Wine.

---

### Post by roni6 on 2015-11-22
I don't understand...
What do you mean? What should I do?
BTW, I used WINE...

---

### Post by Mike_Walsh on 2015-12-14
I don't know if this will help at all, but recently, I've installed Photoshop CS2 into Puppy Linux, under WINE 1.7.53. I know it's an older release, but I found you need to employ 'WineTricks' to download and install 3 items; ;'gecko' (which handles the HTML stuff); 'vcrun6' (which installs the C++ libraries that all the Photoshops are based around); and 'corefonts' ( the basic MS fonts, without which no version of Photoshop will run. Ever!)

**Edit**: Apparently, CS6 also requires 'gdiplus' to be installed through 'WineTricks'.

Hope that helps in some small way.


Regards,

Mike. ;)

---

