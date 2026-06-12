---
title: "Well, I'm going to switch..."
date: 2008-09-13
forum: openSUSE and SUSE Linux Enterprise
---

### Post by TheMaxzilla on 2008-09-13
I'm going to switch tonight, over to openSUSE 11, KDE 4, and I have a few questions...


1. Is there a Graphical Package manager?

2. Can I use apt-get from the command line, or does openSUSE have another story...

3. Is Skype a workable Application in openSUSE?

4. What about Virtualbox - Windows XP, and Pidgin?


That's about it for now... If anyone has a good guide for eye candy, I'd be glad to have a look.

---

### Post by 67GTA on 2008-09-13
1. Yes, Yast

2. Yes, but not out of the box. Suse uses zypper. It is very similar. zypper refresh instead of apt-get update. zypper update instead of apt-get upgrade. zypper install <package name> More here: [http://en.opensuse.org/Zypper/Usage](http://en.opensuse.org/Zypper/Usage)

3. Don't know. I don't use it. You can get a rpm package from the skype website.

4. Virtualbox OSE is in the repos. It doesn't have USB support. If you need USB support, you can download the package from the virtualbox website for 10.3. For USB support go here: [http://en.opensuse.org/Virtualbox_USB_Support](http://en.opensuse.org/Virtualbox_USB_Support) Just be sure to add the mount -a option at the bottom of the page. You also need to add yourself to the vboxusers group through Yast. Pidgin is in the repos.

Opensuse is an awesome distro, but it will have a slight learning curve if you are used to Ubuntu. There are several third party repos. Once you get it installed, go to Menu>System>Configuration>Yast. Then click on "Software Repositories". Then choose "ADD" in the bottom left corner. Then choose "Community Repositories". From here you can add more repos to equal the same amount of software as Debian/Ubuntu. Yast also has an annoying habit of updating all of the repos everytime you open the graphical package manager. It is annoying because it takes a while. While you have the repositories window open, click on each repo and in the left bottom corner you can uncheck the box for "Automatically Refresh". If there is a package you can't find in the repos, you can search the third party repos here: [http://packages.opensuse-community.org/](http://packages.opensuse-community.org/) It will have a "one click" install button for each package.

---

### Post by 67GTA on 2008-09-13
I forgot to mention that Yast is more than just a package manager. You really need to dig around in there. It has a graphical way to configure just about anything on your system. KDE4 is still a little buggy, and not as feature rich as KDE3. You might enjoy KDE3 more if this is your first time using Opensuse. Just my 2 cents.

---

### Post by TheMaxzilla on 2008-09-13
Well, I haven't started it yet, so I'll try KDE3 first

Can I upgrade from KDE3 to KDE4? Or, easily?

---

### Post by 67GTA on 2008-09-13
I wouldn't try upgrading from 3 to 4. Do you have the live CD, or the DVD? The DVD has both 3 and 4 as options. The live CD is only KDE4. Opensuse has packaged them so that they will run side by side. You could actually run them both if you wanted. I usually buy a DVD from OnDisk.com. There is about 4GB of software on there. You can use it as a repository. The DVD also has repair and update abilities. You can update from one release to another with the DVD.

---

### Post by exploder on 2008-09-13
I just recently tried OpenSuse, it is very nice to look at but getting all multimedia working is challenging. Perhaps you will have better luck but I found that many of the repos had conflicting packages.

OpenSuse needs scripts like Fedora has to make multimedia setup less painful and frustrating.

Just my opinion. If you find a way of getting all multimedia working, please share it!

---

### Post by lisati on 2008-09-13
> **67GTA said:**
> 
3. Don't know. I don't use it. You can get a rpm package from the skype website.


There's also a .deb package for Skype that can be used with *ubuntu

---

### Post by 67GTA on 2008-09-13
> **exploder said:**
> I just recently tried OpenSuse, it is very nice to look at but getting all multimedia working is challenging. Perhaps you will have better luck but I found that many of the repos had conflicting packages.

OpenSuse needs scripts like Fedora has to make multimedia setup less painful and frustrating.

Just my opinion. If you find a way of getting all multimedia working, please share it!

What are you having trouble with?

---

### Post by exploder on 2008-09-13
I was having troubles with gstreamer bad and ugly and DVD playback. I had the packman repo enabled. At one point I had most multimedia working but it was conflicting with the update process.

OpenSuse needs something like Easy Life for Fedora to get things set up properly. I liked the tools in OpenSuse and the look of the Gnome version is very professional and polished.

On one install I tried a script that someone had made but it caused me some problems, mainly the system would hang at boot and Firefox was crashing frequently. 

I would defiantly give OpenSuse another shot if I could work out the multimedia issues.

---

### Post by 67GTA on 2008-09-13
Did you try the "one click" install? [http://opensuse-community.org/Restricted_Formats/11.0](http://opensuse-community.org/Restricted_Formats/11.0) Opensuse adheres to the free software philosophy, so their multimedia is crippled. The packman repos will replace packages from the Opensuse repos. That is usually where the trouble starts. Yast will complain about it. The packman repos will also contain newer versions of the same packages than Opensuse has, so if Yast complains, just tell it to "change vendors" and it will be fine. Opensuse 11 has a new feature that will let you set priorities for each repo. You can set the packman repo to a higher priority, and it should always prefer that version if two packages are conflicting.

---

