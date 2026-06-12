---
title: "Getting started with the guide"
date: 2005-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by trommas on 2005-05-28
The unofficial ubuntu guide for getting started is genious! But why is there not a version for A64?

I have several problems witch can be solved by this guide, but the arc. is wrong... Should I simply reinstall the 32-bit version. Pros and cons?

---

### Post by ::DoGG:: on 2005-05-28
Exactly, have some little problems that can`t be solved through 32-bit guide too..

---

### Post by jiyuu0 on 2005-05-28
I don't own a amd64 machine... so i can't do the testing

am waiting for volunteer to edit + test it just like the powerpc version

---

### Post by Optimal Aurora on 2005-05-28
the only problems I had where in the [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main and the same but in the testing main... and this is because when you go to that ftp site you will only find binary-i386 files in the 'stable main' and the 'testing main'...

But still most of the things I need where in the 'unstable main'...

---

### Post by ::DoGG:: on 2005-05-28
Yeah, same here when trieed to install Mplayer for amd64 from marillat, i downloaded them myself though and installed by hand (with deps...)

---

### Post by jiyuu0 on 2005-05-28
i've just updated the entire guide to not use marillat except (acroread and transcode)

check the sources.list in the extra repositories section

not sure going to affect any other arch...but x86 seems fine

---

### Post by trommas on 2005-05-28
[QUOTE=::DoGG::]Yeah, same here when trieed to install Mplayer for amd64 from marillat, i downloaded them myself though and installed by hand (with deps...)[/QUOTE]
 How did you do that? My main concern is not being able to watch movies, because I can't get codecs for Totem working...

---

### Post by ::DoGG:: on 2005-05-28
Yeah, totem was a pain for me too. To get Mplayer up and runnig on Your machine go to 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) /
then search for mplayer, once found for your amd64 platform download it and install by:
```
dpkg -i mplayer_package
```
and of it will complain about any dependences findo that packages there too and install.
I had to change audio output to esound and video to xv to get mplayer working. Crashed in the other settings when try to play video files.

---

### Post by Nequeo on 2005-05-28
You might want to take a look at this website:

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

While the focus is on Cedega, you may find a 32bit Chroot useful, even if you don't use Cedega. I was mainly using it to convert ix86 RPMS to .debs with Alien, as this would normaly fail. I would then install the generated .debs normally with dpkg --force-architecture.

It's also apparently the only way to get Macromedia flash going. The swf player in the Ubuntu AMD64 repository doesn't work properly (for me). 

But just last night I finally gave up, gave in, and installed the x86 version of Ubuntu. All of a sudden, all these annoying little problems I'd been having went away. A boot error involving the hardware clocked vanished. All my Gnucash crashes went away. I can now use MPPE-128 encryption without freezing my system. I can run OpenOffice  Beta (previously javaldx couldn't detect a JRE - even though I had one installed). Etc, etc... 

Perhaps most interestingly, on a clean boot my system now only uses about 22% RAM, as opposed to 35% or so I was seeing under AMD64. 

I do feel like I've sold out a little, but over all I'm a lot happier now than I was 24 hours ago.

---

### Post by Optimal Aurora on 2005-05-29
Thanks, that helps a whole lot better... Thanks again for updating the ubuntuguide Later...

---

### Post by Optimal Aurora on 2005-05-29
> 

It's also apparently the only way to get Macromedia flash going. The swf player in the Ubuntu AMD64 repository doesn't work properly (for me). 


No offense but Macromedia doesn't have a flash player that is capable of running on any 64bit linux... And you can't trick the system into installing, or at least I haven't been successful. It installs and you go to use it and it just don't work... Even on some other forum people that use 64 bit linux severely complained to macromedia that they wouldn't ever use it in any OS if they didn't make it for use AMD64 and IA-64 users...

Just wanted to let you know, because this has been since 2003 and till this day the one you get from Macromedia doesn't work... I think it is the same with Sun's Java

---

### Post by ::DoGG:: on 2005-05-29
Yeah, exactly. I runned couple times flash player on Konqueror, using Fedora x86_64 since only Konqueror uses 32 bit libraries but all the other stuff son`t work for me. Only 32  bit chroot environment. Damn Macromedia...

---

### Post by trommas on 2005-05-29
[QUOTE=jiyuu0]I don't own a amd64 machine... so i can't do the testing

am waiting for volunteer to edit + test it just like the powerpc version[/QUOTE]
 I'll help you out!

Just contact me if there's anything I can help you with regarding this issue :)

---

