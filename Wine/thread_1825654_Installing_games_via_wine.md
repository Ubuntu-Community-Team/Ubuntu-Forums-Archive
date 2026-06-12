---
title: "Installing games via wine"
date: 2011-08-15
forum: Wine
---

### Post by CarlP89 on 2011-08-15
I've been trying to install an old game of mine, but any time I try to run the .exe, I get a message saying the program isn't marked as executable. When I try to mark it as executable, I get a message saying I don't have the permission to do that. Any help?

Im on 10.4

---

### Post by WyleECoyote on 2011-08-15
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

with PlayOnLinux you can run any version of wine, it is somewhat complicated to setup and install games/apps but you can register for their support forum where someone may be able to help you through most installs, they also have some pre-installed scripts that will install the most commonly used apps/games but some things just will never work with wine

---

### Post by CarlP89 on 2011-08-15
It seems the servers are no longer available while using PlayonLinux

It says:

Download failure

Following Server is no longer available

-ftp.eidos-france.fr

Is there any way to install Deus Ex without PoN?

I've also tried mounting the ISO directly to my Hard drive, but it says I need the CD, even when the CD is in the tray.

---

### Post by WyleECoyote on 2011-08-15
to be honest I have very little luck with wine so I rarely use it, the only thing I use it for is ripping/shrinking my dvd's so the kids don't ruin the originals.

but when I installed CoD years ago I opened terminal and did something like this:

$ wine /media/cdrom/setup.exe

then after first cd was finished I did:
$ wine eject

to get the first cd out then put in next cd I really don't remember how I installed Directx but it worked, don't forget you also have to get a nocd/nodvd fix and apply it. other than that I am of no help and I am running PoL right now with no issues of server failure

---

### Post by thatguruguy on 2011-08-15
> **CarlP89 said:**
> I've been trying to install an old game of mine, but any time I try to run the .exe, I get a message saying the program isn't marked as executable. When I try to mark it as executable, I get a message saying I don't have the permission to do that. Any help?

Im on 10.4

Is the file saved somewhere in your home directory (or a sub-directory thereof)? If so, you should appear as the owner of the file if you check the permissions in Nautilus.  If not, open a terminal and navigate to where the file is.  Then, assuming your user name for your computer is "carl" and the name of the file is "foo.exe", the command you'd use is:
```
sudo chown carl:carl foo.exe
```

You'll be prompted for your password.  Then, you can right-click on the file name in Nautilus to check the permissions, and this time you should be able to check the box to "Allow executing the file as a program".

---

### Post by CarlP89 on 2011-08-16
Thanks guys, got it working.

The only problem is that the audio sometimes cuts out, but it's easily fixed with a quicksave/load

---

