---
title: "Had to reinstall Ubuntu (same version) now Wine won't install..."
date: 2012-10-17
forum: Wine
---

### Post by formerflyboy on 2012-10-17
I'm running 12.10 and whenever I attempt to install wine I get the following:

[Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.]

It doesn't give me any ideas as to what, exactly, the issue is so I'm hoping someone here may have an idea.

Odd thing is, I had wine running fine a few weeks ago but Ubuntu had some issues so I did a fresh install and now wine is a problem.

Thanks for any ideas...

---

### Post by lite1979 on 2012-10-17
Give us the output of a few things that might help you. Try these three and let us know what you get.

```
lite@lite-desktop:~$ which wine
/usr/bin/wine
lite@lite-desktop:~$ wine --version
wine-1.5.15
lite@lite-desktop:~$ whereis wine
wine: /usr/bin/wine /usr/bin/X11/wine /usr/local/lib/wine /usr/share/wine /usr/share/man/man1/wine.1.gz
lite@lite-desktop:~$ 

```Also, how are you installing wine this time around? I'm guessing that you're using ubuntu software center, or one of the gui methods according to the error you're receiving. If that's the case, would you mind taking a screenshot and posting it here (for a screenshot, just press "Print Screen," and Ubuntu should display a dialog box that allows you to save the picture [usually as a .png]. Go to a host like tinypic.com and upload it there, then copy the forum code. It'll look like [noparse][img]somethingsomething[/img][/noparse]).

If you were installing via terminal, whether through apt-get or by compiling and installing, your error would probably be a lot more verbose.

---

