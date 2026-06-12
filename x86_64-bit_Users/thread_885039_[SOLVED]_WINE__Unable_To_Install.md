---
title: "[SOLVED] WINE : Unable To Install"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by andyharney on 2008-08-09
Hi, after numerous attempts I am unable to install WINE.

After following the instructions located here - [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

And running ```
sudo apt-get install wine
``` I get ```
andy@Andy-Laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
E: Broken packages
```

Ive looked for both > lib32asound2 & > ia32-libs In Synaptic and they wont install either.

[[IMG]http://img228.imageshack.us/img228/7671/screenshotsynapticlm7.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshotsynapticlm7.png)

[[IMG]http://img148.imageshack.us/img148/3610/screenshotsynaptic1av9.th.png[/IMG]](http://img148.imageshack.us/my.php?image=screenshotsynaptic1av9.png)

Im stumped, ive tried searching many forums but none provide a definitive answer.

Any help with this one will be greatly appreciated.

---

### Post by Kilz on 2008-08-09
Make sure the universe and multivers are enabled. Look in Synaptic then Settings then Repositories.
Can you look in synaptic and see what version of lib32asound2 is available?

---

### Post by doctorwho? on 2008-08-09
sounds like you godda go to the site bud 
these saved me from a world of trouble 
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by andyharney on 2008-08-10
Both Universe & Multiverse are enabled. The version of lib32asound2 available is "1.0.15-3ubuntu4" - ALSA Library (32 Bit).

Ive tried to install this but to no avail.

Following > sounds like you godda go to the site bud
these saved me from a world of trouble
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

I chose "Wine 1.1.2 amd64" Once downloaded I try to install but get the "Error: Cannot install 'ia32-libs'"

[[IMG]http://img84.imageshack.us/img84/6665/screenshotpackageinstalwz6.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshotpackageinstalwz6.png)

---

### Post by Kilz on 2008-08-10
> **andyharney said:**
> Both Universe & Multiverse are enabled. The version of lib32asound2 available is "1.0.15-3ubuntu4" - ALSA Library (32 Bit).

Ive tried to install this but to no avail.

Following 

I chose "Wine 1.1.2 amd64" Once downloaded I try to install but get the "Error: Cannot install 'ia32-libs'"

[[IMG]http://img84.imageshack.us/img84/6665/screenshotpackageinstalwz6.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshotpackageinstalwz6.png)

What version of Ubuntu are you running?

---

### Post by andyharney on 2008-08-10
Im using 8.04 HH - 64 Bit, up to date with updates.

---

### Post by YouSmeg118 on 2008-08-10
Hmmm... im running 8.04 Hardy 64bit and it installed fine for me...

Could it be hardware?

---

### Post by Kilz on 2008-08-10
> **andyharney said:**
> Im using 8.04 HH - 64 Bit, up to date with updates.

Here is the problem with the information you have given. In this screenshot from your first post we see this.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=81027&stc=1&d=1218401185[/IMG] 

It says that the libasound2 version needed by the wine file is 1.0.15-3ubuntu4 but that version isnt available, 1.0.16-0ubuntu0 is.
[If we look at the versions of libasound2 in the repositories]("http://packages.ubuntu.com/search?keywords=lib32asound2&searchon=names&suite=all&section=all") we see this
   
    *  dapper (libs): ALSA library (32bit)
      1.0.10-2ubuntu4: amd64
    * feisty (libs): ALSA library (32bit)
      1.0.13-1ubuntu5: amd64
    * gutsy (libs): ALSA library (32bit)
      1.0.14-1ubuntu8: amd64
    * hardy (libs): ALSA library (32bit)
      **1.0.15-3ubuntu4: amd64**
    * intrepid (libs): ALSA library (32bit)
     ** 1.0.16-2ubuntu1: amd64**

Hardy's libasound2 is 1.0.15, but Intrepid, the new version under development is 1.0.16. Are you sure you are not running Intrepid Ibex? If not, have you enabled the packages under development or testing in Synaptic?

---

### Post by andyharney on 2008-08-11
Im definately running Hardy. In Synaptic i can see the i have checked the boxes under Updates - Proposed Updates.

[[IMG]http://img210.imageshack.us/img210/5820/screenshotsoftwaresourcpb4.th.png[/IMG]](http://img210.imageshack.us/my.php?image=screenshotsoftwaresourcpb4.png)

Could that be the cause of all this?

---

### Post by Stunts on 2008-08-11
Well...
Can you show us what you've got under "Third-Party Software" in the software sources windows please?
Or just post the contents of the file "/etc/apt/sources.list"
I'm guessing that's where the problem might be.

---

### Post by Kilz on 2008-08-11
> **andyharney said:**
> Im definately running Hardy. In Synaptic i can see the i have checked the boxes under Updates - Proposed Updates.

[[IMG]http://img210.imageshack.us/img210/5820/screenshotsoftwaresourcpb4.th.png[/IMG]](http://img210.imageshack.us/my.php?image=screenshotsoftwaresourcpb4.png)

Could that be the cause of all this?

Most likely, first make sure that libasound2 1.0.16 is not already installed. Uncheck Proposed and Unsupported Updates, reload the package list, and try to install wine.

---

### Post by andyharney on 2008-08-11
Using Synaptic i found that libasound2 1.0.16 is the installed version.  Then using force version, downgraded back to libasound2 1.0.15.

Now it asks for winbind, i try to install this and that cannot install due to "samba-common" it requires 4.4 i have 4.5. When i try to force version, in packages removed it shows ubuntu-desktop.

[[IMG]http://img60.imageshack.us/img60/2748/screenshotsynaptic2te8.th.png[/IMG]](http://img60.imageshack.us/my.php?image=screenshotsynaptic2te8.png)

Will this cause a problem if i remove "ubuntu-desktop"?

Im still kinda new to linux & ubuntu.

---

### Post by Kilz on 2008-08-11
> **andyharney said:**
> Using Synaptic i found that libasound2 1.0.16 is the installed version.  Then using force version, downgraded back to libasound2 1.0.15.

Now it asks for winbind, i try to install this and that cannot install due to "samba-common" it requires 4.4 i have 4.5. When i try to force version, in packages removed it shows ubuntu-desktop.

[[IMG]http://img60.imageshack.us/img60/2748/screenshotsynaptic2te8.th.png[/IMG]](http://img60.imageshack.us/my.php?image=screenshotsynaptic2te8.png)

Will this cause a problem if i remove "ubuntu-desktop"?

Im still kinda new to linux & ubuntu.

Yes, that is the desktop package. If you remove it, you remove the gui.

I have made [a modified wine package]("http://home.comcast.net/~ubuntume/wine_1.1.2-mod-amd64.deb") that may help. I am uploading it now. All I did was change the requirement to allow libasound2 1.0.16. If sound does not work, you can always uninstall the moded wine package.

---

### Post by andyharney on 2008-08-11
Fantastic, that works!

It shows in the update manager that there are updates for WINE.  Would that be a bad thing to do?

[[IMG]http://img372.imageshack.us/img372/2699/screenshotupdatemanagerfs1.th.png[/IMG]](http://img372.imageshack.us/my.php?image=screenshotupdatemanagerfs1.png)

---

### Post by Kilz on 2008-08-11
> **andyharney said:**
> Fantastic, that works!

It shows in the update manager that there are updates for WINE.  Would that be a bad thing to do?

[[IMG]http://img372.imageshack.us/img372/2699/screenshotupdatemanagerfs1.th.png[/IMG]](http://img372.imageshack.us/my.php?image=screenshotupdatemanagerfs1.png)

Yes it would be a bad idea, because that package would fail to install. You have wine 1.1.2 installed with my package, its the latest version. Just lock the version in synaptic and the update notice will go away.

---

### Post by andyharney on 2008-08-12
Superb, cheers for the help Kilz.

WINE is now running fine.

---

### Post by Stunts on 2008-08-12
Don't forget to mark this thread as solved!
=-)

---

