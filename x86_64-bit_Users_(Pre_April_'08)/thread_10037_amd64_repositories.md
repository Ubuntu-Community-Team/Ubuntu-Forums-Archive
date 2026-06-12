---
title: "amd64 repositories"
date: 2005-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by hkctr on 2005-01-04
I installed x86_64 version and don't know what the repositories are for amd64.  Can someone let me in on the secret?

---

### Post by jdong on 2005-01-04
Which ones are you talking about? Official Ubuntu? Unofficial, 3rd party?

---

### Post by hkctr on 2005-01-04
Jdong - Any and all repositories please.  

Perhaps I should have asked a different question.  How does apt distinguish between the different archs of Ubuntu.  How does it know that it should only update the x86_64 debs?

---

### Post by Hazycrazy on 2005-01-17
I would also like to know if there are any AMD64 friendly repos out there?

What are those of you using x86_64 Ubuntu using for apt-get?

---

### Post by valadil on 2005-01-17
The only one I've added (well after universe and multiverse of course) is for the newest versions of xfce, my DE of choice.

deb-src [http://www.os-cillation.de/debian](http://www.os-cillation.de/debian) source/
deb [http://www.it-weber.net/debian/xfce4/](http://www.it-weber.net/debian/xfce4/) ./

Mostly I've just learned to use apt-get source for things that aren't in the amd64 repository yet.  The mplayer-mozilla plugin works great if you get the source and edit the rules file to let it install if you have mplayer-amd64.

---

### Post by smdeep on 2005-02-02
[QUOTE=valadil]The only one I've added (well after universe and multiverse of course) is for the newest versions of xfce, my DE of choice.

deb-src [http://www.os-cillation.de/debian](http://www.os-cillation.de/debian) source/
deb [http://www.it-weber.net/debian/xfce4/](http://www.it-weber.net/debian/xfce4/) ./

Mostly I've just learned to use apt-get source for things that aren't in the amd64 repository yet.  The mplayer-mozilla plugin works great if you get the source and edit the rules file to let it install if you have mplayer-amd64.[/QUOTE]

I have the very same question. Could you plesae post you apt sources list here. I am also using AMD64. I would like to use only packages for AMD64.

Thanks in advance.
Bob

---

### Post by Dylanby on 2005-02-02
I think I understand what you're asking.
Well I can't explain it technically 'cause I don't know.

APT "knows" which architecture it's installed on (your APT package is an amd64 package after all).

When it goes to [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) or wherever it's going to search for binaries/sources for the appropriate arch. You don't have to specify amd64.

If you look in [http://archive.ubuntu.com/ubuntu/pool/main/a/abiword/:](http://archive.ubuntu.com/ubuntu/pool/main/a/abiword/:)
```
**Index of /ubuntu/pool/main/a/abiword**

    * Parent Directory
    * abiword-common_2.0.7+cvs.2004.05.05-1ubuntu3_amd64.deb
    * abiword-common_2.0.7+cvs.2004.05.05-1ubuntu3_i386.deb
    * abiword-common_2.0.7+cvs.2004.05.05-1ubuntu3_powerpc.deb
    * abiword-common_2.2.2-1ubuntu2_all.deb
    * abiword-doc_2.0.7+cvs.2004.05.05-1ubuntu3_all.deb
    * abiword-doc_2.2.2-1ubuntu2_all.deb
    * abiword-gnome_2.0.7+cvs.2004.05.05-1ubuntu3_amd64.deb
    * abiword-gnome_2.0.7+cvs.2004.05.05-1ubuntu3_i386.deb
    * abiword-gnome_2.0.7+cvs.2004.05.05-1ubuntu3_powerpc.deb
    * abiword-gnome_2.2.2-1ubuntu2_amd64.deb
    * abiword-gnome_2.2.2-1ubuntu2_i386.deb
    * abiword-gnome_2.2.2-1ubuntu2_ia64.deb
    * abiword-gnome_2.2.2-1ubuntu2_powerpc.deb
    * abiword-help_2.0.7+cvs.2004.05.05-1ubuntu3_all.deb
    * abiword-help_2.2.2-1ubuntu2_all.deb
    * abiword-plugins-gnome_2.0.7+cvs.2004.05.05-1ubuntu3_amd64.deb
    * abiword-plugins-gnome_2.0.7+cvs.2004.05.05-1ubuntu3_i386.deb
    * abiword-plugins-gnome_2.0.7+cvs.2004.05.05-1ubuntu3_powerpc.deb
    * abiword-plugins-gnome_2.2.2-1ubuntu2_amd64.deb
    * abiword-plugins-gnome_2.2.2-1ubuntu2_i386.deb
    * abiword-plugins-gnome_2.2.2-1ubuntu2_ia64.deb
    * abiword-plugins-gnome_2.2.2-1ubuntu2_powerpc.deb
    * abiword-plugins_2.0.7+cvs.2004.05.05-1ubuntu3_amd64.deb
    * abiword-plugins_2.0.7+cvs.2004.05.05-1ubuntu3_i386.deb
    * abiword-plugins_2.0.7+cvs.2004.05.05-1ubuntu3_powerpc.deb
    * abiword-plugins_2.2.2-1ubuntu2_amd64.deb
    * abiword-plugins_2.2.2-1ubuntu2_i386.deb
    * abiword-plugins_2.2.2-1ubuntu2_ia64.deb
    * abiword-plugins_2.2.2-1ubuntu2_powerpc.deb
    * abiword_2.0.7+cvs.2004.05.05-1ubuntu3.diff.gz
    * abiword_2.0.7+cvs.2004.05.05-1ubuntu3.dsc
    * abiword_2.0.7+cvs.2004.05.05.orig.tar.gz
    * abiword_2.2.2-1ubuntu2.diff.gz
    * abiword_2.2.2-1ubuntu2.dsc
    * abiword_2.2.2.orig.tar.gz
``` 

You see .debs for different arch's: AMD64, i386 & PPC...
APT installs .deb's which match the arch it's installed on.

---

### Post by azelter on 2005-02-02
Hi all,
So the conclusion is we can have all the standard apt lines in our /etc/apt/sources.list. However, as was aluded to above, there are several packages that seem to be available for i386 but are not yet available for amd64. Given that the amd64 can run i386 binaries no problem, I wander what the vbest way to get these packages is. For example, I want to have acroread. It isn't available for my amd64, but is available to my i386 box. I could just get the deb files and do dpkg --force all -i acroread.deb 
Does anyone know af a better way of doing this. Is there a way to tell apt that it's ok to install i386 files if no amd64 files are available, and to upgrade when the are available, or something to that effect. I can see it getting quite messy if I'm installing i386 packages by hand the whole time ...
Cheers,
Alex

---

### Post by Nadir on 2005-02-02
The solution doesn't exist yet. It is called multiarch and the Debian devs are working on it at the moment. Should be ready soon.

---

### Post by azelter on 2005-02-02
Ah thanks.  Looks interesting. I guess I'll just do stuff by hand until then.
Cheers,
A

---

### Post by Tichondrius on 2005-02-04
[QUOTE=Dylanby]I think I understand what you're asking.
Well I can't explain it technically 'cause I don't know.

APT "knows" which architecture it's installed on (your APT package is an amd64 package after all).

When it goes to [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) or wherever it's going to search for binaries/sources for the appropriate arch. You don't have to specify amd64.
[/QUOTE]

You're right, apt "knows" the current architecture by using 'uname -m' (just like any other program which has architecture dependant behavior), so it only shows binary packages for that architecture. Source packages are not architecture specific.

---

### Post by showbeest on 2005-07-30
[QUOTE=Nadir]The solution doesn't exist yet. It is called multiarch and the Debian devs are working on it at the moment. Should be ready soon.[/QUOTE]

Has a solution already been developped?

---

