---
title: "[SOLVED] OpenOffice beta 3 links broken"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by stormtrooprdave on 2008-09-23
[http://download.openoffice.org/3.0beta/]("http://download.openoffice.org/3.0beta/")

I am trying to download the OpenOffice3 beta but the 64 bit links don't work.  Does anyone have a working link to download the deb?

---

### Post by lonniehenry on 2008-09-23
see message #4 for corrected links
__________________

---

### Post by stormtrooprdave on 2008-09-23
The first link leads to an empty directory and the Tombuntu one is a 404 error

---

### Post by lonniehenry on 2008-09-23
Sorry they worked on Sunday.  Let me look around for the correct link.

[ftp://ftp.ussg.iu.edu/pub/openoffice/contrib/rc/3.0.0rc2/](ftp://ftp.ussg.iu.edu/pub/openoffice/contrib/rc/3.0.0rc2/)   
and the instructions :  
 1. Head to the download page and select the Linux (deb) or Linux 64 bit (deb) download. Decompress the archive to your desktop.
   2. Installing OpenOffice requires installing a large number of DEB packages. It&#8217;s easiest to install them using the terminal. Open a terminal, switch to the directory where you decompressed the download to, and install all the packages at once:
      cd ~/Desktop/OOO300_m7_native_packed-1_en-US.9354     
      sudo dpkg -i DEBS/*.deb
   3. That will not have added you any Application menu items. You can create one yourself using the menu editor (System->Preferences->Main Menu). Menu icon graphics are available in /usr/share/icons/hicolor/48×48/apps. Launch OpenOffice with this command:
      /opt/openoffice.org3/program/soffice
   4. You can delete the download from your desktop after the installation.

Want to remove OpenOffice 3? I&#8217;ve compiled this huge command (it&#8217;s all one line) to remove all of the OpenOffice 3 packages:
sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure

you may have to change the commands to match the version that you downloaded.

---

### Post by stormtrooprdave on 2008-09-23
Great it worked, thanks

---

### Post by JAwuku on 2008-09-25
Thanks for the directions Lonnie,

I was able to get to the ftp server, but had trouble downloading. I used the alternative site at Heanet in Ireland:

_**[http://ftp.heanet.ie/mirrors/openoffice.org/contrib/rc/3.0.0rc2/OOo_3.0.0rc2_20080920_LinuxX86-64_install_en-US_deb.tar.gz](http://ftp.heanet.ie/mirrors/openoffice.org/contrib/rc/3.0.0rc2/OOo_3.0.0rc2_20080920_LinuxX86-64_install_en-US_deb.tar.gz)**_

Or use the English mirror:

_**[http://www.mirrorservice.org/sites/download.openoffice.org/contrib/rc/3.0.0rc2/OOo_3.0.0rc2_20080920_LinuxX86-64_install_en-US_deb.tar.gz](http://www.mirrorservice.org/sites/download.openoffice.org/contrib/rc/3.0.0rc2/OOo_3.0.0rc2_20080920_LinuxX86-64_install_en-US_deb.tar.gz)**_

I then installed the debs in the unzipped directory DEBS.

You don't have to manually add the menu items, you will find a .deb file in the subdirectory DEBS/desktop-integration, which does that for you when installed.

---

### Post by lonniehenry on 2008-09-26
From the link in Open Offices site 
[http://download.openoffice.org/3.0beta/](http://download.openoffice.org/3.0beta/)

you can click extended mirrors and choose from several mirrors for the other versions. Sorry about sending out links that have kept changing.  Perhaps by staying close to the OO pages, we can get more people trying the new beta.

---

### Post by darco on 2008-10-04
I'm glad I found this thread. I am using Mint and couldnt get OO to load but now all good :D

thxs

darco

---

