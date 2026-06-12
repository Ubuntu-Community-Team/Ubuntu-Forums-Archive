---
title: "Wine not installing my game. :("
date: 2013-05-10
forum: Wine
---

### Post by malikge on 2013-05-10
Hi,

I have made an ISO image of my **Need For Speed Most Wanted **dvd and wanting to install it on Ubuntu 12.04 x64.

I have installed wine and using **Furius ISO Mount Tool **I have mounted that iso image,
but when I run the file **speed.exe** to run the setup. It gives an error that:
> Please Insert the correct DVD-ROM, select OK and restart application

I have also tried what is explained on this site, but still no luck.
[http://piotr.gabryjeluk.pl/blog:playing-need-for-speed-most-wanted-on-ubuntu](http://piotr.gabryjeluk.pl/blog:playing-need-for-speed-most-wanted-on-ubuntu)

Any help, how can I install it?
Thanks

---

### Post by Argyboy on 2013-05-10
I usually use the PlayOnLinux tool to install games in Wine. Need for Speed Most Wanted is listed in the wizard so maybe try that and see how you get on.

---

### Post by Perfect Storm on 2013-05-10
Moved to Wine Section.

---

### Post by malikge on 2013-05-10
@Argyboy thank for the reply.
I have installed[COLOR=#000000] PlayOnLinux and installed Need For Speed Most Wanted. 
But when I try to run it give the following error (screenshot attached)

Any help on that?
Thanks[/COLOR]

---

### Post by Argyboy on 2013-05-10
> **malikge said:**
> @Argyboy thank for the reply.
I have installed[COLOR=#000000] PlayOnLinux and installed Need For Speed Most Wanted. 
But when I try to run it give the following error (screenshot attached)

Any help on that?
Thanks[/COLOR]

I believe that error occurs when there's a mix of 32 bit and 64 bit files in your wine installation. You may need to delete your .wine directory and start again but you'll lose everything in that directory obviously, if you do that.

[http://www.linuxquestions.org/questions/slackware-14/wine-error-948084/](http://www.linuxquestions.org/questions/slackware-14/wine-error-948084/)
[http://forums.opensuse.org/english/get-technical-help-here/applications/447971-wine-not-working.html](http://forums.opensuse.org/english/get-technical-help-here/applications/447971-wine-not-working.html)

I'm not the best person to ask with Wine errors to be perfectly honest, so hopefully someone else will jump in here and help :) Sorry

---

### Post by malikge on 2013-05-14
Hi,

I have installed wine-1.5.29 and PlayOnLinux 4.2.1.

When in PlayOnLinux I run the AutoRun.exe the setup starts.

After that it show the message that:

The game cannot be installed, because it requires DirectX 9.0c or higher.

By following [this tutorial]("http://www.dedoimedo.com/games/wine-directx.html") I tried to install DirectX 9.

Every thing work well, until I try to test the directX

> 
lenovo@G580-desktop:~$ wine ~/.wine/drive_c/windows/system32/dxdiag.exe

wine: cannot find L"C:\\windows\\system32\\dxdiag.exe"


Any help on this...
Thanks.

---

### Post by malikge on 2013-05-16
For me 
```
wine "application.exe" -opengl
```
solves the problem.

Reference:
[http://ubuntuforums.org/showthread.php?t=345037&p=2057416#post2057416](http://ubuntuforums.org/showthread.php?t=345037&p=2057416#post2057416)

---

