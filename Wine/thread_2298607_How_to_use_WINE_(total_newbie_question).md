---
title: "How to use WINE? (total newbie question)"
date: 2015-10-12
forum: Wine
---

### Post by History Teacher on 2015-10-12
I'm not a technical person but I've installed WINE on my Lubuntu laptop.  How do I get WINE to run my powerpoint presentations and Word documents?  I've never used WINE before.  Thanks!

---

### Post by ian-weisser on 2015-10-12
Wine is not an office productivity suite, like MS Office or LibreOffice.
Wine merely provides a compatibility layer for you to install some Windows applications, like MS Word and Powerpoint, onto your Linux system.
That compatibility is not guaranteed - lots of applications don't work with Wine, or some break due to updates in Linux, Wine, or the Windows application.

Do you specifically need to use MS Word and Powerpoint? If so, you must install them onto your Linux+Wine system.
Or is the existing .doc/.docx/.ppt/.pptx compatibility provided by LibreOffice (which does not require Wine) adequate for your needs?

I find LibreOffice adequate for most simple ppt slides; complex slides don't work so well, but that's not LibreOffice's fault.
Also, beware fonts - they are different (even some with the same name!) between Linux and Windows.

---

### Post by yancek on 2015-10-12
If you have wine successfully installed then a simple way to open a word or pps is to right-click the icon and in the windows that opens you have an option "open with".  Type wine there in lower case letters and click OK.  I don't use either myself but from what I have read they probably won't work very well.  Better off trying Libre Office or using windows.

---

### Post by mystics on 2015-10-12
If you want to install an application, then go to the directory where the EXE file is, open up a terminal, and type 

```
wine <application name>
```

 Many applications will need some extra work to get working or may not work at all. If you want more information on that, I would advise looking at the Wine AppDB: [https://appdb.winehq.org/](https://appdb.winehq.org/)

The problem with PowerPoint is that, from what I can tell, it isn't well-supported on Wine. Some versions can get Gold status on certain distros, but that's about it. You should look at the different versions from the App DB linked. Just search for PowerPoint and it should lead you to the right pages for it.

If Wine's performance isn't suitable, you could always upload the presentation to OneDrive and use PowerPoint Online, which is free, to give the presentation. PowerPoint Online is more than adequate for just giving a presentation. The only issue is that you do have to have Internet access while giving it. Other than that, this would give the lowest chance of creating problems on Linux.

The other major option would be LibreOffice, but I've generally been very displeased with LibreOffice Impress, more so when it is trying to deal with stuff created in PowerPoint. Definitely make sure to review slides there before presenting them, as I've often found them prone to formatting errors (less so when created with Impress), some of which remove very important information entirely. LibreOffice Writer may be good and Calc passable, but I've just never found Impress to, well, impress.

In short, unless you have issues with not having Internet access, I would *highly* advise using PowerPoint Online if you want to stick with Linux for PowerPoint presentations. After that, you may want to use Windows to give presentations. If those aren't options, then you could always determine if PowerPoint using Wine or LibreOffice Impress is preferable.

---

### Post by howefield on 2015-10-12
Thread moved to the "*Wine*" forum.

---

### Post by MikeCyber on 2015-10-13
Newbies should use Playonlinux. It makes things easier. Anyway for word/powerpoint I only use libreoffice.

---

### Post by sudodus on 2015-10-13
> **History Teacher said:**
> I'm not a technical person but I've installed WINE on my Lubuntu laptop.  How do I get WINE to run my powerpoint presentations and Word documents?  I've never used WINE before.  Thanks!

It may be possible to convert your presentations to pdf files (depending on how advanced they are). And it is ***easier to run a pdf presentation*** on various platforms (operating systems, software etc).

---

### Post by mastablasta on 2015-10-13
> **MikeCyber said:**
> Newbies should use Playonlinux. It makes things easier. Anyway for word/powerpoint I only use libreoffice.

I second that. Office 2007 and 2010 should work ok and should be easy enough to install.

if oyu do not need to move the presentation or to use one made by others then it is inde3ed easier and faster to just use libre office. 

neither libre office nor WPS office do not have that good compatibility with Powerpoint. Libre office's compatibility is better. both can import power point files. you will see some things are off, but they are usually easy to fix.

---

### Post by oui on 2015-10-16
> **MikeCyber said:**
> Newbies should use Playonlinux. It makes things easier. Anyway for word/powerpoint I only use libreoffice. 
 
It is probably the best way as Linux covers this job using the free software libreoffice. He can elaborate and test them L under Windows, where Libreoffice is coming from (the German original software StarOffice was mainly used as cheap outsider by Windows dealers to add an licence free office to her computer! But this old situation is probably also a reason for a lot of people don't to use it: The cheap solution for my work ):P !)

Linux did have a nice own solution: Magicpoint. A Magicpoint test package was also available for Windows. Advantage from this test package: He was delivered with example not included in the original Linux installation and, for this reason, special easy to test and to modify!

A great inconvenient from Linux is that you can rarely buy some crash course to learn software being dedicated to become professional software! You need a teacher by your employer or have to follow the sometimes very hard way of decrypting some man pages (a great  mamelioration of the man page would be to use Magicpoint to present software and their use!!!). I can understand why History Teacher prefers Microsoft solutions used in all the world and being accessible through tons of best media!

To him:

You find the wine try of user directories in your home directories. The main directory of wine is an hidden one. Look for

/home/myHome/.wine

You will find 2 (or sometimes only, more) directories.

- one is the system
- the other contains only, usually, two links a/ to the precedent giving you a point C: for your fictive drive C: (the precedent directory) named as in Windows, and b/ a drive Z: . Z: is the complete drive where your partition is! In C: the organisation follow best the organisation from a real Windows drive. For best result (presentation) I would recommend to install windows fonts as in Windows (is not absolutely necessary: It is possible to use trough Wine the Linux fonts sets, but for presentations etc. it is not recommandable! You find adequate packages at the Debian or Ubuntu depository under  the nonfree's!). Using the file manager from Wine you can operate in wine as you would be in Windows and ignore completely that you are in Linux :lolflag: . Accept the proposition to install more (browser, mono, etc. if new propositions appears depending what you require from system; if not, wine will not be as complete as a normal Windows and you will probably not become happy! Yes, I know... Wine is now a mammoth system (as comparable situation, Linux within Windows! Yes divers solutions are existing for that like Cygwin, Andlinux etc... Cygwin is not really light, excepted the little set specially prepared to test and use Magicpoint in Windows: Less than 10 files did be enough...).

How to use your Wine
 
In diverse window manager from Linux, you can drag and drop the link C: prepared in /home/myHome/.wine on the desktop and use the command line interpreter to do more exactly as in a real Windows system, or, better. set by drag and drop an icon from you lovely Windows app's on the desktop!

The package "winetricks" make all that really more easy! Please install it and study the add's in your main menu as in your file manager menu! With it you can install and remove windows app's as you would operate quasi in Windows

Good luck!

---

### Post by monkeybrain20122 on 2015-10-16
> **MikeCyber said:**
> Newbies should use Playonlinux.

I don't believe so. The advantage of POL is that it allows you to install several versions of wine (bottles) I fail to see how it would be easier for someone having problems using one version.

---

