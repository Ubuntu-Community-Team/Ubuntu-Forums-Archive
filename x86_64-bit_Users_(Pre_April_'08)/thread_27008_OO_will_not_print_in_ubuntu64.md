---
title: "OO will not print in ubuntu64"
date: 2005-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by cybodog on 2005-04-14
I can print from cups, I can print from nedit, gedit.  I can not yet print from firefox or Open Office.  I can print from spadmin in /usr/lib/openoffice. When I chose a printer in writer, I am given the defualt printer (same one in spadmin), but it never prints.  What gives?  OS is ubuntu64 installed.  This 64bit OS is like going back two years in usability. :???:

---

### Post by Crad on 2005-04-14
[QUOTE=cybodog]I can print from cups, I can print from nedit, gedit.  I can not yet print from firefox or Open Office.  I can print from spadmin in /usr/lib/openoffice. When I chose a printer in writer, I am given the defualt printer (same one in spadmin), but it never prints.  What gives?  OS is ubuntu64 installed.  This 64bit OS is like going back two years in usability. :???:[/QUOTE]

I had to setup a chroot environment to use open office.  AFAIK there are 64-bit issues with OOo.  Check out the chroot-32 howto thread to see how to do it.

---

### Post by cybodog on 2005-04-14
[QUOTE=Crad]I had to setup a chroot environment to use open office.  AFAIK there are 64-bit issues with OOo.  Check out the chroot-32 howto thread to see how to do it.[/QUOTE]

And that is what I hate about it.  why run 32bit software on a 64 bit platform?  So far I have gotten java to work on a 64bit os/browser.  I picked ubuntu, becuse it was suposed to just work.  I had this much with pure64.  Not your fault, btw :) just ranting about lack of 64 bit stuff.  I even here that win64 uses w32codecs and a compatability layer to play win .video files.  Thanks for responding.  Any other suggestions besides chroot?  I consider that NOT a cure, only a bad bad patch.

---

### Post by Casey on 2005-04-14
Are you running OO2 or OO?  If I recall correctly from gentoo OO won't compile in a 64 bit environment but the developers of OO wanted to get OO2 to compile in a 64 bit environment.  If you haven't tried out OO2 it should be in synaptec - you could give it a shot.

---

