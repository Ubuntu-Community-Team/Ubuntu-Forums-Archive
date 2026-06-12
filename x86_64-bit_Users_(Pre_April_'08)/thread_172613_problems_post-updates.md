---
title: "problems post-updates?"
date: 2006-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2006-05-09
After the relatively large number of updates about 4 days ago, I have noticed a few problems. One was the appearance of the Kubuntu logo in blue as my system loads before gdm. I have also recently noticed a problem with being unable to mount my usb flash drive. I looked through Synaptic and noticed that "The GNOME Desktop Environment, with extra components version 1:2.10.1ubuntu1" was no longer marked  as installed. I reinstalled it, but the blue Kubuntu logo remains. I did fix my  usb mounting problem by reinstalling hal and gnome-volume-manager. Another problem I have noticed is the update notifier behaving strangely. It would show that there are updates, but if I clicked on it, nothing would happen. I reinstalled it and now it  seems to be behaving better. Lastly, I think that Firefox 1.0.8 is not as stable. It seems more prone to quitting unexpectedly. I tried reinstalling it, but  haven't noticed any improvement.

Has anyone else noticed any problems after updates? Is it a common occurrence for packages to be deselected as updates take place? Is there a more stable version  of Firefox for ppc ubuntu?

I  have not been in the habit of re-installing programs when I have had problems. I think now that this might be a necessary activity to keep my system working smoothly, if that is really possible with ppc ubuntu.

---

### Post by ssam on 2006-05-09
the first problem is caused be having installed the kubuntu artwork, the change does not take effect until you next install a kernel. there is a thread somewhere that explains how to fix it.

its rare for stuff to break on an update. i am not sure what hapened.

installing firefox 1.5 in breezy is a problem, because lots of things require 1.0.x to be there. there are ways to manually install firefox, but i recommend you hang on till the dapper release at the start of june. that will have new versions of all the applications, and lots optimisations and bug fixes.

---

### Post by seatea on 2006-05-09
Thanks  for  the comments. The recommendation  for fixing the artwork  I received was "sudo update-alternatives --config usplash-artwork.so". The problem  seems to be that on my system now, there is no artwork for ubuntu. What happened to it is a mystery to me. The kubuntu logo appearing is no big deal from a practical stand point, my only concern  was that it might be  a symptom of an update that went wrong.

I am looking forward to the  final release of Dapper. I hope that Dapper will provide functionality to ppc ubuntu that is still lacking. I am starting  to feel a little discouraged about continuing to use ubuntu. I seem to have been putting a lot of time into fixing things that break or spending a lot of time on  trying to get various components  to work and being unsuccessful.

---

### Post by ssam on 2006-05-09
do you not have the ubuntu-artwork package installed, or did it get uninstalled.

i recomend that you do a backup and clean install of dapper rather than an upgrade. a clean start should clear any problems.

---

### Post by seatea on 2006-05-09
I had planned on doing  just that. It has been tempting to upgrade to Dapper beta, but  I am not in the mood to guess about what's wrong and what's beta related. I would do a clean install of Breezy, but it is so close to time for the Dapper release that I am waiting.

I checked  in Synaptic and ubuntu artwork is installed. I reinstalled it. What got my attention, however, was that ubuntu-desktop was not marked as installed. This has been a strange mess. I am reinstalling  it and will see what  happens on the next re-boot. I may have done a lot of things in Synaptic, but uninstalling ubunt-desktop is not one of them. Whether or not it is related to the updates is unknown, but this occurred without my input.

---

### Post by farruinn on 2006-05-10
[quote=seatea]...What got my attention, however, was that ubuntu-desktop was not marked as installed. ...I may have done a lot of things in Synaptic, but uninstalling ubunt-desktop is not one of them. Whether or not it is related to the updates is unknown, but this occurred without my input.[/quote]

The ubuntu-desktop package is a meta-package meaning it doesn't install any software itself. I is a dummy package with a ton of dependencies on other packages to provide a complete desktop. From the package description:

```
 It is safe to remove this package if some of the desktop system
 packages are not desired.  However, it is recommended that you keep
 it installed, because it is used to carry out certain upgrade
 transitions (such as adding new packages to the system).

```

Sometimes it is removed when you install a package that conflicts with one of it's dependencies.

---

### Post by seatea on 2006-05-10
Thanks. That makes  sense about the ubuntu-desktop package being  uninstalled.

I did reinstall ubuntu-desktop, but my system is still booting up as kubuntu. Maybe my  system will run  more smoothly now though.

---

### Post by farruinn on 2006-05-11
You get a kubuntu logo at the usplash screen? Maybe running 'sudo dpkg-reconfigure usplash' (I think that's the usplash package) will change it to using the ubuntu logo now that you have ubuntu-desktop installed.

---

