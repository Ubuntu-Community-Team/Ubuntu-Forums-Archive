---
title: "Hooray for the Kubuntu Devs! Java, Flash + Plugins related"
date: 2007-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by RS3York on 2007-03-29
This showed up earlier today in the Feisty changes RSS feed.

 
```

kdebase (4:3.5.6-0ubuntu18)
 Add kubuntu_94_konqueror_nsplugins_amd64.diff: 
 Enables nsplugins support for AMD64 (Closes Malone #98551)

```

This means that nspluginwrapper will play nice with Konqueror with the next update to kdebase.  So flash, adobe and other 32-bit plugins should work via nspluginwrapper, full-featured browsing in a 64-bit browser here we come!  No more recompiling with the patch with every update to kdebase.  KDE/Konqueror already makes using Java in a 64-bit browser really easy compared to Firefox64 (yes, this is by default since AFAIK it's the only choice due to no plug-in, but it's not hard to set-up).

Instructions for Flash with nspluginwrapper can be found here [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

The repo that has nspluginwrapper is: 
deb [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) edgy-janvitus main-amd64

Janvitus has his own instructions here *be sure to install the dependencies from the link above first*.  [http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player](http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player)
(English instructions appear lower on the page).

Below I have the instructions for Java in Konqueror.  They've been adapted & simplified from this link: [http://www.ubuntuforums.org/showthread.php?p=497330](http://www.ubuntuforums.org/showthread.php?p=497330)

1. Install Sun's JRE from repos

2. Type the following in a terminal
```

sudo update-alternatives --config java

```
Pick the appropriate number for Sun Java

4. Open Konqueror. 
'Settings' Menu -->'Configure Konqueror'
Click 'Java and Javascript' on the left hand side
Change the 'Path to Java executeable, or 'java':' Setting to read '/usr/bin/java'
Click okay

5. Visit [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) 

6. Watch a dancing cartoon, along with information showing Sun's Java 1.5 or 1.6 is installed.

7.  Rejoice at having 64-bit browsing with 64-bit java


I hope this helps some folks.  I'll update the post when the package is built and available for everyone.

Thanks to Fritz Heinrichmeyer for posting the bug to Launchpad and Anthony Mercatante for applying the patch so we all could have it.  I love this community.

March 30, 2007 UPDATE:  The packages were uploaded and available last night (availability might have been different depending on your local mirror).
I can confirm that the packages work.  I tested it with YouTube.com, ign.com and the Adobe test page.  Oddly the embedded links in ign's flash work, but the links in Adobe's don't.  Not sure why this is, since both sites work with nspluginwrapper with Firefox64.  Could be a problem local to my machine.  Regardless, Konqueror is now the most functional 64-bit browser for Linux.  Have fun, things are slowly but surely getting better for *buntu64.

---

### Post by kuja on 2007-03-30
About time that patch got integrated.... I was sick of having to patch it myself too.

---

### Post by Altmenorg on 2007-04-01
For such issues, if that's not implemented in kubuntu, pinging us on #kubuntu-devel after posting the bugs to launchpad always helps to get the patch reviewed and uploaded.
Probably better solution than building your own kdebase...

---

