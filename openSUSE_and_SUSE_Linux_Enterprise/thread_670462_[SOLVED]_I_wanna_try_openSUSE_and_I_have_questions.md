---
title: "[SOLVED] I wanna try openSUSE and I have questions."
date: 2008-01-17
forum: openSUSE and SUSE Linux Enterprise
---

### Post by b0rka7a on 2008-01-17
Hi all !
Get ready to answer to some very stupid questions ! :lol:
I'm installing openSUSE 10.3 right now. I have some questions about it.
**-1.** Is openSUSE based on Slackware ?
**-2.** Can I use Compiz-Fusion on it and how to install it ?
**-3.** I've installed KDE 3.5. Is it better than KDE 4 ?
**-4.** Is there an openSUSE forum ?
**-5.** Is there a difference  between openSUSE and SUSE :D
I'm new to openSUSE, so be gentle ;) Thanks in advance !
:lolflag:

---

### Post by Pandemic187 on 2008-01-17
1. I don't think so. I'm not sure but I've used it and it's pretty user-friendly, so I can't imagine it is.
2. Compiz Fusion is included in the latest release of openSUSE.
3. This question has been much-debated. Some like it, some don't. The one thing I can say for sure is that it is indeed very buggy, so I wouldn't suggest using it until a future release. If you'd like to see more about what people have said about it, this might be a good thread to look into: 

[http://ubuntuforums.org/showthread.php?t=663866&highlight=KDE4](http://ubuntuforums.org/showthread.php?t=663866&highlight=KDE4)

4. Of course! Although I don't know which one is the best. Here's one that seems to be popular:

[http://suseforums.net/](http://suseforums.net/)

You can always Google to find different forums, of course.

5. No. There is no difference; the real name for it is openSUSE because it is an open-source operating system, but people call it SUSE for short.

Hope this helps!

---

### Post by b0rka7a on 2008-01-17
Thank you very much for the answers :)

---

### Post by b0rka7a on 2008-01-17
Another question that I forgot to ask:
How to install a package ? :D  Is there something like apt-get ?

---

### Post by Pandemic187 on 2008-01-17
I know one of the main ways to install packages on SUSE is called YaST, but I forget how it works.

---

### Post by b0rka7a on 2008-01-17
Okay, I'll look in the SUSE forum.

---

### Post by jken146 on 2008-01-17
Hi there.  Coincidentally I've just installed openSUSE today, just to see what it's like.  You can change the compiz settings by going to Computer > Control Centre > Look and Feel > Desktop Effects.

Click on Computer > Install Software to install more packages.  You may also want to add the Packman and VideoLAN repos as per [http://opensuse-community.org/Repositories/10.3](http://opensuse-community.org/Repositories/10.3) .

I think SUSE is Red Hat based, originally.

---

### Post by RebounD11 on 2008-01-17
> **b0rka7a said:**
> Hi all !
Get ready to answer to some very stupid questions ! :lol:
I'm installing openSUSE 10.3 right now. I have some questions about it.
**-1.** Is openSUSE based on Slackware ?
**-2.** Can I use Compiz-Fusion on it and how to install it ?
**-3.** I've installed KDE 3.5. Is it better than KDE 4 ?
**-4.** Is there an openSUSE forum ?
**-5.** Is there a difference  between openSUSE and SUSE :D
I'm new to openSUSE, so be gentle ;) Thanks in advance !
:lolflag:

1. I don't think it's based on anything, it's developed by Novell and the openSuSE community, and it's free, it comes only with open-source apps and stuff no proprietary software included, just like Ubuntu, and I've answered this way to question 5 too :D SuSE is the commercial distribution that Novell developes (it has everything you need and only fully tested and stable apps are included - that means that anything unstable, let alone bleeding edge is left out).

2. follow these instructions [http://en.opensuse.org/Compiz_fusion](http://en.opensuse.org/Compiz_fusion) and you will have a very nice compiz-fusion installed :D (use the 1-click install it's great, but be careful to have your video card configured, anyway it's all there better than I can explain it :D)

3. KDE 3.5 is more stable and polished, however you can try KDE4 in parallel to 3.5 and check it out, it looks great but you'll need time to get accustomed, it different, in a good way I believe (Compiz Fusion doesn't work on it, but it doesn't need it it looks great)

4. suseforums.net - but it's not as good as the Ubuntu Forums, not as friendly but can come in handy

As for package management you can use Yast (great tool for configuration of all sort - puts the terminal away :D and it can be used to install software) although it's rather slow compared to Synaptic. There's also SMART graphical and command line package management (a little faster) and zypper (command line only but very fast, like apt-get). You can also install with 1-click install from here:
[http://software.opensuse.org/search](http://software.opensuse.org/search)
or download the RPM package and install using: 
```

su
(enter root password)
rpm -Uvh <path&name-of-RPM-package>
```
I forgot to mention, it's a RPM-based distro ... to find RPM's suitable (compatible) for openSuSE you can search here:
rpm.pbone.net - click advanced search and select only OpenSuSE and SuSE 10.3 and 10.2 others may not be compatible

Also like any other distro you can compile from source if you have the source with the classic:
```

./configure
make
su
(enter root password)
make install
make clean  //optional
```

I hope this covers all that you want to know about OpenSuSE 10.3.

I recommend it from the bottom of my heart, it's great stable and fast. 
PS: Recommendation: Install from DVD, takes longer but saves you a lot of configuring afterwards.

---

### Post by FreakTech on 2008-01-17
Novell actually takes openSuse and refines it into Suse Professional for enterprise desktops and laptops

---

### Post by RedDwarf on 2008-01-17
> **b0rka7a said:**
> 
**-1.** Is openSUSE based on Slackware ?
Yes.
[http://en.wikipedia.org/wiki/Suse#History](http://en.wikipedia.org/wiki/Suse#History)
[http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png](http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png)

---

### Post by Pandemic187 on 2008-01-17
> **RedDwarf said:**
> Yes.
[http://en.wikipedia.org/wiki/Suse#History](http://en.wikipedia.org/wiki/Suse#History)
[http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png](http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png)
openSUSE may have been based on Slackware originally I suppose, but it has changed a lot. Slackware's package management system does not check for dependencies, whereas SUSE's does. I couldn't imagine myself attempting to use a package management system that does not resolve dependencies. I can understand wanting to play around with code, but I having to manually resolve dependencies sounds like OS suicide to me.

---

### Post by Incense on 2008-01-17
> **b0rka7a said:**
> Another question that I forgot to ask:
How to install a package ? :D  Is there something like apt-get ?

OpenSUSE like ubuntu, has a few ways to install packages. You can install from YaST by clicking on software management, and searching for software  in there. 

You can install from the command line by typing (as root) 

```
zypper install package_name
```

You can also use the One Click Install from the OpenSUSE build service by searching for packages from the site below. 

[http://software.opensuse.org/search]("http://software.opensuse.org/search")

The best way IMO, is to install and use the SMART package manager. It's very fast and nice. You can get that by running the following commands as root. 

```
zypper sa -r http://download.opensuse.org/repositories/smart/openSUSE_10.3/smart.repo
zypper ref smart
zypper install smart
smart channel --add http://linux01.gwdg.de/~pbleser/files/smart/opensuse-10.3.txt
smart mirror --add http://linux01.gwdg.de/~pbleser/files/smart/mirrors-eu.txt
smart update
smart install smart-gui
```

You can then install from the CLI by typing 

```
smart install package_name
```

Or using the GUI by running SMART from your application menu. I hope you are enjoying your openSUSE experience.

---

### Post by Incense on 2008-01-17
> **Pandemic187 said:**
> openSUSE may have been based on Slackware originally I suppose, but it has changed a lot. Slackware's package management system does not check for dependencies, whereas SUSE's does. I couldn't imagine myself attempting to use a package management system that does not resolve dependencies. I can understand wanting to play around with code, but I having to manually resolve dependencies sounds like OS suicide to me.

LOL, yeah openSUSE has really strayed far from it's Slackware roots. I don't think many openSUSE users really know their roots. Not quite the same as the Ubuntu Debian relationship.

---

### Post by lespaul_rentals on 2008-01-18
Tell us how you like it.  I think YaST2 is very good and it manages dependencies very well.

---

### Post by b0rka7a on 2008-01-18
I like it, but I'm back to Ubuntu :( I've installed my nvidia drivers but they wrecked my SuSE and GRUB also. I couldn't boot in Ubutnu and now I'm only on Ubuntu. Someday when I have time I should try it again.

---

