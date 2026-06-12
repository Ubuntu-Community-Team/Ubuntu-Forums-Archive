---
title: "ubuntu 7.10 x64 wine install prob."
date: 2007-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by laph on 2007-11-06
Ok, I have been trying to install wine on my system for last 48hour and all the wine install faq, walk throughs and what not have not been able to get me going yet, I even ended up having to reinstall ubuntu 7.10 cause I messed up package dependency's some how :D.  Here is what I get
wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: ia32-libs (>=1.6) but it is not installable
 Depends: lib32asound2 (>1.0.14) but it is not installable
 Depends: libc6-i386 (>=2.6-1) but it is not installable

tried to install the packages by them self and install all the dependencies and that was how I hade a broken package, which caused me to have to reinstall cause it wanted to delet 2 gigs worth of others to fix the 1 that broke, at least I broke it good eh?  Anyway  So far I like what I have seen with this system moving over from slackware/Slamd 64 to this and hoping that i can get this all worked out.
Thanks for the help even if it is a simple fix that only a noob like my self would over look :)

---

### Post by sawjew on 2007-11-06
Wine is in the repositories so you should just need to do ```
sudo apt-get install wine
```

or through synaptic if you prefer the graphical method.

If you want the latest wine go to this page [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb") and add the repositories as directed then apt-get install wine.

The other way is to install Automatix and use it to install wine.  It will add the repositories for you.

---

### Post by laph on 2007-11-06
Done all of that, Didn't work that is where I got that errors from.  any more Ideas?  I even tried installing the packages it needed by downloading them 1 at time and install, but still didn't work.
Thanks for the help.

---

### Post by sawjew on 2007-11-06
Are you using any other repositories other than the default ones?  Are you trying to install wine from the Ubuntu repositories or from the wine repositories?  If you have any other repositories than the official Ubuntu ones try commenting them out, updating the index and then install wine from the official repository.

---

### Post by laph on 2007-11-07
Tried Officail and tried non, still can't get it to go.  I even did all the updates hoping that would get it to install.  it is making me feel stupid, though going to packages would make it that much easier to install and keep uptodate on stuff but just to get wine, and now Teamspeak to install is driving me up the wall... there has to be something simple I am missing that is keeping these libraries from installing what I need. am almost ready to install the 32bit os and try that.
Thanks for the help again.

---

### Post by sawjew on 2007-11-07
I am at work now so I can't really spend too much time helping but I'll see what I can work out later.  In the meantime there are several things you can try;

[LIST]
[*]Make sure you have the universe and multiverse repositories enabled
[*]uninstall anything that didn't come from the official repositories and then try again
[*]dowload and install automatix from the automatix web site and try using it to install wine
[/LIST]

It sounds like you are having a problem with the version of the packages so maybe a later version has been installed from another source.  The other thing would be to try building from source using apt.

I've gotta go now, good luck.

---

### Post by mosaic2s on 2007-11-07
have installed wine on 64 bit. no problems. however can not install ie4 linux - tar command does not work, alien is not working to convert tar.gz to .deb mode.

---

### Post by sawjew on 2007-11-07
mosaic2s
> however can not install ie4 linux - tar command does not work, alien is not working to convert tar.gz to .deb mode

The tar.gz file is not a package, as in an installation package, it is just an archive, like a zip archive.  Alien is for converting Installation packages not archives.  All you need to do is right click on it and select "Extract Here". You then open the resultant folder and run the install script inside it.

Another way to install IE is to go here [http://www.wine-doors.org/wordpress/?page_id=3]("http://www.wine-doors.org/wordpress/?page_id=3") and get Wine Doors which will configure your wine directory for you and can install a range of software, including IE, just by selecting it from a list.  It actually uses ies4linux to install wine but you can do it all graphically.

laph
Make sure you have the universe repositories enabled as a couple of those packages are in universe.  If you use Add/Remove from the applications menu it should enable all the repositories you need to install wine.  Just type wine in the search bar and it will show up as "Wine Windows Emulator".  Just make sure you have selected to show "All available applications" from the drop down next to the search box.

---

