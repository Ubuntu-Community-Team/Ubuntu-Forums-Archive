---
title: "Problem installing wine on 20.04 LTS because of dependcies"
date: 2021-08-23
forum: Wine
---

### Post by arno772 on 2021-08-23
When trying to install Wine I get the following message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dconf-gsettings-backend : Depends: dconf-service (>= 0.36.0-1)
                           Depends: dconf-service (< 0.36.0-1.1~)
 winehq-stable : Depends: wine-stable (= 6.0.1~focal-1)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Could anyone help?

---

### Post by mastablasta on 2021-08-24
which wineversion?

you would install wine using software center or via command line using

sudo apt install wine

if you want a GUI, there are Playonlinux or Lutris.

---

### Post by arno772 on 2021-08-24
Thanks for your reply.

I tried it via software center as well as via command line. 

Via command line I tried to install Wine 6.

Software center says it is version 5.0-3ubuntu1.

In both cases I get messages about unmet dependencies.

---

### Post by monkeybrain20122 on 2021-08-28
where did you get winehq-stable? You have added a ppa that has unmet dependencies. Use ppa-purge to get rid of it (or just remove it if you haven't installed anything successfully from it)

If you want a different version of wine use playonlinux which allows you to install multiple versions of wine. For example you can install wine 6 from it.

---

### Post by adambond on 2021-10-24
This should help.   [https://tecadmin.net/how-to-install-wine-on-ubuntu-20-04/](https://tecadmin.net/how-to-install-wine-on-ubuntu-20-04/)

---

### Post by arno772 on 2022-01-07
Hi adambond, thanks for the hint. (Sorry for the late response but I was out for a while.)

When following the procedure you point at, I get at some point the following:

*****************
Resolve these dependencies by hand? [N/+/-/_/:/?] R
The following ESSENTIAL packages will be BROKEN by this action:
 perl-base : Conflicts: perl-base:i386 but 5.30.0-9ubuntu0.2 is to be installed
 perl-base:i386 : Conflicts: perl-base but 5.30.0-9ubuntu0.2 is installed

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":
*****************

At that point U abort because I do not know exactly what I am doing and I don't want to break the system.
Frankly, I don't know what to do.

---

### Post by arno772 on 2022-01-07
hi monelybrain20122, thanks for the tip (and sorry for the late reply, but I was out for some reasons).

I tried to install playonlinux via Ubuntu software center and have the same issues "Unable to install PlayOnLinux: The following packages have unmet dependencies"

Any help is very much appreciated.

---

