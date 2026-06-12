---
title: "cannot make .deb for ndiswrapper-1.2"
date: 2005-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by OneSeventeen on 2005-06-29
after running "make deb" in the directory I downloaded the ndiswrapper-1.2 source into, I get tons of lines of code where ubuntu is doing it's magic, then:
> 
...
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
...


So in the end I am right back where I started.  :(

Any tips on how to get ndiswrapper made into a .deb file for my amd64 laptop?

---

### Post by NickB on 2005-06-29
I would suggest getting 1.1, as the wireless tools in hoary don't support all the features of 1.2 (or so it complains loudly every single time :)).

However, if you want to compile 1.2, edit the debian/control file and change the Architecture line to amd64.

nick

---

### Post by OneSeventeen on 2005-06-29
So do I do the same thing to get ndiswrapper-1.1 to work?

I heard rumor ndiswrapper was supposed to be included as part of hoary, but I haven't seen it anywhere...

I just downloaded ndiswrapper-1.1 so I'll let you know if I have any issues... expect a lot of questions on how to get apps to run on 64-bit version of hoary, so if you know a secret about how to make other apps work, lemme know.

So when I install apps, do I just force it to accept amd64?  If so, does that screw anything up as far as how it works? I mean, will it run in 64-bit mode, or just in 32?


**EDIT:**
So far I've got my wireless device supposedly installed, and ndiswrapper has been added to the end of /etc/modules
I've also set up my home wireless details, including WEP code, so here's hoping it will work when I get home tonight!!!

Are there any good gui interfaces for managing multiple WiFi networks?  I've got one at work I sometimes use as well.

---

### Post by ssck on 2005-06-29
[QUOTE=OneSeventeen]So do I do the same thing to get ndiswrapper-1.1 to work?

I heard rumor ndiswrapper was supposed to be included as part of hoary, but I haven't seen it anywhere...

I just downloaded ndiswrapper-1.1 so I'll let you know if I have any issues... expect a lot of questions on how to get apps to run on 64-bit version of hoary, so if you know a secret about how to make other apps work, lemme know.

So when I install apps, do I just force it to accept amd64?  If so, does that screw anything up as far as how it works? I mean, will it run in 64-bit mode, or just in 32?


**EDIT:**
So far I've got my wireless device supposedly installed, and ndiswrapper has been added to the end of /etc/modules
I've also set up my home wireless details, including WEP code, so here's hoping it will work when I get home tonight!!!

Are there any good gui interfaces for managing multiple WiFi networks?  I've got one at work I sometimes use as well.[/QUOTE]

here is a good wiki to get you started on compiling and setting up ndiswrapper 1.1

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

---

### Post by OneSeventeen on 2005-06-30
Actually that tutorial is what got all this started.  By following that tutorial I ran into the architecture problem, but then I just changed the debian/control files to use amd64 instead of i386 and all is well!

I was browsing on the web last night with no problems (other than no flash... I guess I'll just boot windows when I need my regualr dose of [Strongbad](http://www.homestarrunner.com/sbemail.html).  (and no, I don't plan on setting up a chroot'd 32 bit firefox... I'm too lazy!)

---

### Post by NickB on 2005-07-01
[QUOTE=OneSeventeen](other than no flash... I guess I'll just boot windows when I need my regualr dose of [Strongbad](http://www.homestarrunner.com/sbemail.html).  (and no, I don't plan on setting up a chroot'd 32 bit firefox... I'm too lazy!)[/QUOTE]
Considering how far you've come, it should be pretty easy to follow the chroot howto compared to what you've done so far ;)

Nick

---

### Post by doobit on 2005-07-28
Could you run through the proceedure you used for setting up for AMD64 for us noobees? Thanks!
I see there's a debian package inside the tar for ndiswrapper 1.2 now, but I wasn't able to make it work.

---

### Post by Tamir on 2005-07-28
You should edit the file: debian/control, and add "amd64" without quotes to the line - Architecture. You will see on this line only i386, add amd64 :)

---

