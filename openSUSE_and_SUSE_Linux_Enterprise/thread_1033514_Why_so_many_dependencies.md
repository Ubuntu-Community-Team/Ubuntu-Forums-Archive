---
title: "Why so many dependencies?"
date: 2009-01-07
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Frostmourne on 2009-01-07
I'm getting used to the Yast Software Manager but I don't like being forced to install so many extraneous packages with the packages I want. For example, if I try to install Seahorse (key manager) I am forced to install flash-player, bogofilter, audio codecs, and Openoffice templates as well. In Ubuntu I had a similar problem until I unchecked "Consider recommended packages as dependencies" in Synaptic. Is there a similar option in openSUSE?

---

### Post by Vince4Amy on 2009-01-07
> **Frostmourne said:**
> I'm getting used to the Yast Software Manager but I don't like being forced to install so many extraneous packages with the packages I want. For example, if I try to install Seahorse (key manager) I am forced to install flash-player, bogofilter, audio codecs, and Openoffice templates as well. In Ubuntu I had a similar problem until I unchecked "Consider recommended packages as dependencies" in Synaptic. Is there a similar option in openSUSE?

If you are using the LiveCD version and installed from there it will install these as they were not included on the livecd, they are specific to your setup and are one time only.

---

### Post by SunnyRabbiera on 2009-01-07
This is where Suse is seriously lacking, sure you can encounter dependancy issues with ubuntu but most of the time its solvable.

---

### Post by Vince4Amy on 2009-01-07
> **SunnyRabbiera said:**
> This is where Suse is seriously lacking, sure you can encounter dependancy issues with ubuntu but most of the time its solvable.

How is it lacking, because it's installing a few language packages and codecs for the system which couldn't possibly be included on a liveCD?

---

### Post by blazemore on 2009-01-07
I agree, not all users want to install the recommended packages. I think apt is the most powerful package management tool.
I tried OpenSuse for a week, and the reason I went back to Ubuntu is because of Ubuntu's straightforward management.

---

### Post by SunnyRabbiera on 2009-01-07
> **Vince4Amy said:**
> How is it lacking, because it's installing a few language packages and codecs for the system which couldn't possibly be included on a liveCD?

well the thing is that suse always seemed dependency heavy, thats why I dont use it.

---

### Post by Vince4Amy on 2009-01-07
> **SunnyRabbiera said:**
> well the thing is that suse always seemed dependency heavy, thats why I dont use it.

Any Distro with package management that has automatic dependency handling has always been dependency heavy for me which is one of the reasons I use Slackware.

---

### Post by RedDwarf on 2009-01-07
> **Frostmourne said:**
> For example, if I try to install Seahorse (key manager) I am forced to install flash-player, bogofilter, audio codecs, and Openoffice templates as well.
Like Vince4Amy explained these aren't Seahorse dependencies... they are selected just because of starting the YaST package manager.
It's the equivalent of "zypper install-new-recommends". They are just the "recommended" (soft dependencies) of the packages you already have installed. If you unselect them (from the "Installation Summary" filter) they will be permanently added to the /var/lib/zypp/SoftLocks file, and not automatically selected anymore.

> **Frostmourne said:**
> In Ubuntu I had a similar problem until I unchecked "Consider recommended packages as dependencies" in Synaptic. Is there a similar option in openSUSE?
For cases where the "problem" really are soft dependencies of a selected package "zypper install" has the "--no-recommends" switch. 
In the YaST package manager you will need to add "solver.onlyRequires = true" to /etc/zypp/zypp.conf.

But note that "recommended" dependencies aren't unrelated things like Seahorse and flash-player. If a package recommends another one it's because of a good cause (if isn't it's a packaging bug, report it).
openSUSE doesn't wants to force you to install the Openoffice templates, so they are in a separate package. But they are recommended by Openoffice since it's probable that an Openoffice user will want them. If they weren't installed automatically an user could easily think that Openoffice doesn't includes templates... the "recommend" dependency is a good compromise between both problems.

Note that on openSUSE the "recommend" dependency is used to:
- Automatically add language packages
If your system is in spanish and you install aspell, aspell-es will be automatically selected but no other languages. If you now add a secondary language, like catalan (also from a region of Spain) aspell-ca will be automatically selected.
At really Openoffice templates is such a case. If you use german OpenOffice_org-templates-de will be selected, if you use english OpenOffice_org-templates-en.
- Automatically add drivers
Connect a webcam that requires a driver from a separate package. When you start the YaST package manager the driver will be automatically selected (at really the updater applet will inform you about this when you connect the webcam, without a need to manually start YaST).

If you disable recommends you will lose these features.

I have recommended packages installed by default... the few specific cases where I don't want them I just let YaST add them to /var/lib/zypp/SoftLocks.

> **SunnyRabbiera said:**
> well the thing is that suse always seemed dependency heavy, thats why I dont use it.
99,99% of RPM dependencies are binary ones. Automatically obtained by rpmbuild from a "readelf". These dependencies are... well, dependencies. You NEED them or your software will fail to start with an "undefined reference" error.
About the other 0,01%... I could ask for a specific case where a dependency isn't really required, but I'm pretty sure I would obtain no answer.

---

### Post by Vince4Amy on 2009-01-07
> Note that on openSUSE the "recommend" dependency is used to:
- Automatically add language packages
If your system is in spanish and you install aspell, aspell-es will be automatically selected but no other languages. If you now add a secondary language, like catalan (also from a region of Spain) aspell-ca will be automatically selected.
At really Openoffice templates is such a case. If you use german OpenOffice_org-templates-de will be selected, if you use english OpenOffice_org-templates-en.
- Automatically add drivers
Connect a webcam that requires a driver from a separate package. When you start the YaST package manager the driver will be automatically selected (at really the updater applet will inform you about this when you connect the webcam, without a need to manually start YaST).

Yes that's exactly what I was referring to which is one of the great features of OpenSUSE and YaST to me.

---

### Post by quickshade on 2009-01-07
One of the things that they plan on doing for zypper during the next few months is rebuilding how it determines dependencies, thus making it much easier to configure and change what the system installs while still keeping everything usable.

---

