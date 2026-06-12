---
title: "kde"
date: 2006-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by bbbbbtony on 2006-09-21
i was wanting to install the kde desktop environment on my 64 bit machine so i could give it a try but i keep getting dependency errors from apt-get and synaptic. it'll say that kde depends on x, but x will not be installed. error broken package. is there another way to install kde easily?

---

### Post by kuja on 2006-09-21
That's very, very strange.

Can you show me the contents of your /etc/apt/sources.list file, as well as the exact error message that it gives you?

Also, I personally recommend skipping straight to kde 3.5.4.
You can do that by adding the following line to the aforementioned sources.list file:

deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

As per installing KDE, the way I would recommend would be to install the "kubuntu-desktop" package.

---

### Post by bbbbbtony on 2006-09-21
put sources as an attachment.
added the repo you suggested. ran apt-get update and it told me it couldn't get the gpg key for it. then tried sudo apt-get kubuntu-desktop and this is what it gives me:
bbbbbtony@laptop:/media/hda5/tideland$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: language-selector-qt but it is not going to be installed
E: Broken packages

---

### Post by kuja on 2006-09-21
for info about the key, see this page: [http://kubuntu.org/announcements/kde-354.php](http://kubuntu.org/announcements/kde-354.php)

This is quite unusual though. language-selector-qt is in the ubuntu dapper main repository. Try manually installing it and see what it tells you.
sudo apt-get install language-selector-qt

---

### Post by bbbbbtony on 2006-09-21
i tried that in synaptic and it kept going down the list of things it wasn't going to install. :/

---

