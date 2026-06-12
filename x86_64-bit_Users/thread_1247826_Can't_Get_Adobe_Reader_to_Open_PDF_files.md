---
title: "Can't Get Adobe Reader to Open PDF files"
date: 2009-08-23
forum: x86 64-bit Users
---

### Post by SteveTheRed on 2009-08-23
Hello,

Until about a week or so ago, I was able to open pdf files using Adobe Reader. It looks like they have moved acroread out of the medibuntu repo and I suspect that my problem started around the same time.

The problem is that when I attempt to open a pdf, nothing happens. This is true regardless of whether I use the command line or gnome. If I type acroread -v, it displays "9.1.3".

acroread is installed on my laptop, which has an amd64 processor running 64 bit Intrepid. I had to reinstall Intrepid after upgrading to Jaunty because Jaunty doesn't play nice with my "old" ATI video card.

I've tried uninstalling the ubuntu version of acroread and installing the Debian version (after adding the debian repo). That didn't work. I've done a lot of Googling, but haven't found any good answers yet.

I need Adobe Reader because I open a lot of complex pdfs, use fill-in forms and have trouble getting evince to print correctly. I know it is bloatware, but I have to use the tool that works best for me. I don't use Windows (except at work) anymore, so there's no solution in that direction.

TIA for any pointers in the right direction.

---

### Post by drs305 on 2009-08-23
Verify you still have acroread installed:
```
*which acroread*
```
should return */usr/bin/acroread*

You should also be able to start Acrobat Reader by typing: *acroread*

If this is correct, open your file browser to display a .pdf file. Right click on it, Properties, Open With Acrobat Reader. If you don't see Acrobat Reader, select Properties, Open With, select Acrobat Reader, or Add, Use Custom Command and navigate to */usr/bin/acroread* and select Open.

---

### Post by SteveTheRed on 2009-08-23
Thanks for your suggestions. The which command does indeed point to /usr/bin/acroread. I tried your other suggestions but, alas, they don't work either.

I take the fact that acroread prints out the version number with the -v flag as a sign that it is installed. I just can't open acroread, with or without passing it a filename. It fails to open but does not throw an error to stderr. The context menu does contain an acroread entry and does point to the right place.

---

### Post by drs305 on 2009-08-23
For intrepid, try installing this version of acroread I tracked down in the launchpad site. The deb package to download is on the bottom left:
[https://launchpad.net/ubuntu/+source/acroread/9.1.3-1intrepid1/+build/1148441]("https://launchpad.net/ubuntu/+source/acroread/9.1.3-1intrepid1/+build/1148441")

---

### Post by SteveTheRed on 2009-08-23
drs305:

I appreciate your help. Unfortunately, that didn't work either.

---

