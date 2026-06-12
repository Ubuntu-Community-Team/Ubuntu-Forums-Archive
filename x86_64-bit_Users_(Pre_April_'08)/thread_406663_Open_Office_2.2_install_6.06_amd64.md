---
title: "Open Office 2.2 install 6.06 amd64"
date: 2007-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by rodmor on 2007-04-11
I recently installed Badger 6.06 LTS on my Athlon AMD64.  Open Office 2.0 which came with the installation worked fine.  Then I tried to install Skype following the instructions at [http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/](http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/)

Skype didn't work but worse than that, Open Office was broken.  The Open Office splash screen comes up and then dies.  I tried re-installation through Synaptic - no good.  Tried complete removal through Synaptic and complete re-install - no good.  Then tried to install Open Office 2.2 following the instructions at 
[http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml](http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml)

During the installation got a message on the terminal that packages for AMD64 not included (or maybe found).  So that installation also failed and I am left without Open Office. 

I have previously installed the ia32 etc packages necessary to run 32 bit applications on the AMD64

Seems that it was the attempted installation of Skype that caused the problem.  Appreciate any ideas on how I could get Open Office back on my system.  Thanks

---

### Post by Kilz on 2007-04-11
> **rodmor said:**
> I recently installed Badger 6.06 LTS on my Athlon AMD64.  Open Office 2.0 which came with the installation worked fine.  Then I tried to install Skype following the instructions at [http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/](http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/)

Skype didn't work but worse than that, Open Office was broken.  The Open Office splash screen comes up and then dies.  I tried re-installation through Synaptic - no good.  Tried complete removal through Synaptic and complete re-install - no good.  Then tried to install Open Office 2.2 following the instructions at 
[http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml](http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml)

During the installation got a message on the terminal that packages for AMD64 not included (or maybe found).  So that installation also failed and I am left without Open Office. 

I have previously installed the ia32 etc packages necessary to run 32 bit applications on the AMD64

Seems that it was the attempted installation of Skype that caused the problem.  Appreciate any ideas on how I could get Open Office back on my system.  Thanks

First I have a question, Did you install Breezy Badger 5.10 or Dapper Drake 6.06?

---

### Post by rodmor on 2007-04-11
Kliz

Thanks for answering.  My apologies for not getting the version straight.  It is Dapper Drake 6.06 LTS AMD 64.

Rod

---

### Post by Kilz on 2007-04-11
> **rodmor said:**
> Kliz

Thanks for answering.  My apologies for not getting the version straight.  It is Dapper Drake 6.06 LTS AMD 64.

Rod

So open office doesnt start at all. the only thing those instructions do that may cause a problem is force in libqt3-mt_3.3.6-1ubuntu6.1_i386.deb. Forcing libs is a bad idea, applications are not bad , but libs can cause problems. I usualy tell people to open them up and place them in /usr/lib32.
We can try reinstalling the 64bit libqt3-mt to see if it helps.

---

### Post by rodmor on 2007-04-12
With no Open Office installed, firstly from Synaptic Package manager removed and then re-installed libqt3-mt.  I don't know whether this is the 64 bit version but as it is listed under Synaptic for the 64 bit Dapper perhaps it is.  Then re-installed Open Office 2.0 from Synaptic (including ubuntu-desktop).  Same problem, brief OO 2.0 splash screen then nothing.

---

### Post by pay on 2007-05-02
Can you run it in the terminal ```
oowriter
```and post any error messages that may come up? Thanks.

---

