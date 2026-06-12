---
title: "How to install Microsoft office 2010 ?"
date: 2013-12-04
forum: Wine
---

### Post by kiran1247 on 2013-12-04
Hi Friends,

Can someone please help me on how to install "microsoft office 2010" on my ubuntu 12.04 machine ?

Please let me show if we have any steps with screen shots , which helps me better to install.

Thanks for the help.

---

### Post by Y^2om&amp;#7sgP on 2013-12-04
Have you checked @

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

---

### Post by codenine75a on 2013-12-06
I don't want to be a stuffy, but why not use LibreOffice or OpenOfficer 4.x? I think you can save in office 2010 format.  I know it still has its quirks with file format conversions but it is free.

---

### Post by lah7 on 2013-12-06
Microsoft Office 2010 has no native Linux version as you may be aware. You'll need to run it as a Windows program in which you'll first need to install **Wine**, or a prefix manager like **PlayOnLinux**.

If you choose to install **Wine**, open the executable ("setup.exe" for instance) and it'll run like any other Windows program, check [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=31") for Office 2010 for any workarounds or known problems. You may also need **Winetricks** if people report in needing additional packages for Office to work properly.

If you install **PlayOnLinux**, open the Install menu and find Office 2010 from the list. This is a preconfigured script that'll install Office 2010 and prompt for the setup executable (whether it's the download version or setup.exe from the disc), if anything additional is extra, it'll download and install it for you.

It should be self-explanatory. If you have any problems, let us know.

---

### Post by deadflowr on 2013-12-06
> **kiran1247 said:**
> Hi Friends,

Can someone please help me on how to install "microsoft office 2010" on my ubuntu 12.04 machine ?

Please let me show if we have any steps with screen shots , which helps me better to install.

Thanks for the help.

I think you would need to upgrade the wine version to start with.
12.04 has, I think 1.4, which probably won't work so well with office 2010.

I don't know how playonlinux works in terms of installing newer versions of wine, but you can get it by adding the wine ppa here
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

But when do get it setup to install, look for the program uninstall wine software(or something with a name like that)
The click Install and then at the top at the dropdown, click it and go up to the MY Computer section.
The install disk for the office 2010 should show listed, navigate it and look for either the setup or install file and hit OK.
Then sit on pins and needles and hope for the best.

---

### Post by philinux on 2013-12-06
Try softmaker office free too.

---

