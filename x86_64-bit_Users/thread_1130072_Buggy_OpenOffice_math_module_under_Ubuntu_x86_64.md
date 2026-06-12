---
title: "Buggy OpenOffice math module under Ubuntu x86 64"
date: 2009-04-19
forum: x86 64-bit Users
---

### Post by Carlos Sevcik on 2009-04-19
I am running Jaunty with OpenOffice.org 3.01 in 3 different machines, a Dell Workstation with dual Xeon processors, an HP laptop with a dual Centrino processor, and a small HP laptop with a dual AMD Turion64.

For some time now I have noticed that when I write a document with lots of equations in it, which look OK in the OO writer or its printouts, the digits (1,2,...,0) get more or less randomly distorted (replaced by a phony symbol) when the document is exported to pdf format. I first thought that it might have something to do with the fonts used (changing from Bitstream Vera Sans to Dejavu Sans or Nimbus Roman 9 makes no difference), but this was not the case. By more or less random I mean it might change from one conversion to the next, or appear only after page 13, while the equations from 1 to 12 might be OK (at least most of the times for that document).

But I recently realized that the bug appears only when I export to pdf in my small laptop (HP Pavillion tx1230la with memory expanded to 4 gB, AMD Turion64x2) and does not happen when exporting the same document using the same version of Ubuntu and OO in neither of the two other machines. The OO version installed in the 3 machines was installed using the Synaptic Package Manager provided by Ubuntu and from Ubuntu's repositories.

Furthermore, today I downloaded OO 3.0.1 from the OpenOffice.org site (Debian packages for x86-64 systems) and installed everything in the DEBS subdirectory using

sudo dpkg -i *

and to my surprise the conversions to pdfs in my HP Pavilion tx1230la seem to be working perfectly when I use the OO writer downloaded from the OO site directly.

**_My conclussion: There is a bug in the Ubuntu for x86-64 OO version which does not exists in the packages downloaded directly from the [www.OpenOffice.org](www.OpenOffice.org) site._**

Furthermore, I have the feeling that the bug is not new, I observed distorted digits in some of my manuscripts exported to pdf using Ubuntus's OO 2.x as early as 2 years ago, but was unable to pinpoint the problem as I did now. As said is a somewhat random problem.

---

### Post by ptn107 on 2009-04-20
Please search launchpad* to see if your bug has been reported before.  If not please report as a new bug.

*[https://bugs.launchpad.net/ubuntu/+source/openoffice.org](https://bugs.launchpad.net/ubuntu/+source/openoffice.org)

---

### Post by John Jason Jordan on 2009-04-20
> **Carlos Sevcik said:**
> I am running Jaunty with OpenOffice.org 3.01 in 3 different machines, a Dell Workstation with dual Xeon processors, an HP laptop with a dual Centrino processor, and a small HP laptop with a dual AMD Turion64. ...
Furthermore, today I downloaded OO 3.0.1 from the OpenOffice.org site (Debian packages for x86-64 systems) and installed everything in the DEBS subdirectory ...
and to my surprise the conversions to pdfs in my HP Pavilion tx1230la seem to be working perfectly when I use the OO writer downloaded from the OO site directly.

**_My conclussion: There is a bug in the Ubuntu for x86-64 OO version which does not exists in the packages downloaded directly from the [www.OpenOffice.org](www.OpenOffice.org) site._**

I have somewhat opposite experiences.

I have used OOo for years on Ubuntu. Due to various problems I have had over the years I have often tried the version from OOo, only to find that it is even worse than the Ubuntuized version. 

Right now I am using 3.0.1 on Intrepid. The version I am using is from the PPA repositories. I have lots of problems with formulas, although not exactly the same as yours. My formulas are for linguistics use and really simple, but require scalable brackets. The brackets print very faint on a black and white laser, as though they were colored (but they are not). As a workaround I applied bold to the brackets. Consider a formula created with the following syntax:

font Sans bold left [  font Serif nbold { alignl stack { +CORONAL~ # +anterior # + strident # &#8209;voice } } right ] 

Add another item to the stack and the brackets become even bolder. The more items I add to the stack the bolder the brackets on screen. But when I print I get a simple bold bracket, except that about 15% of the time one side of the brackets will print extra fat. 

This happens on 2.4.1 also, which I have installed on another computer. And if I use the Jaunty live CD with 3.0.1 there is no change. Furthermore, I can boot to live CDs of other distros with various versions of OOo and I get the same bug. It also happens with KDE distros (even Kubuntu). This bug is in OOo, not Ubuntu.

The problem is that there are few people who use the formula feature of OOo. As a result it is not well tested before a new version is released. The developers assume that no news is good news.

While my bug is in OOo, your bug may lie in Ubuntu. I simply wanted to point out that not all bugs with OOo can be blamed on Ubuntu.

---

### Post by Carlos Sevcik on 2009-04-20
JJJ:

Right now I am using 3.0.1 on Intrepid. The version I am using is from the PPA repositories. I have lots of problems with formulas, although not exactly the same as yours. My formulas are for linguistics use and really simple, but require scalable > brackets. The brackets print very faint on a black and white laser, as though they were colored (but they are not). As a workaround I applied bold to the brackets. Consider a formula created with the following syntax:

font Sans bold left [ font Serif nbold { alignl stack { +CORONAL~ # +anterior # + strident # &#8209;voice } } right ]

Curiously when I include your line in my OO I have the same printing problem you explain but then exporting to pdf and printing the pdf file, The brackets are extrabold!



[QUOTE]While my bug is in OOo, your bug may lie in Ubuntu. I simply wanted to point out that not all bugs with OOo can be blamed on Ubuntu.

I am not blaming anything on Ubuntu, but pointing out that I am getting a bug in the Ubuntu version of OO under an AMD processor that vanishes when I use the [www.openoffice.org](www.openoffice.org) original files for this processor. My guess is that the Ubuntu version are compiled from sources and something is wrong there, when compiling for 64 bit AMD processor at Ubuntu. I am an Ubuntu evangelist, but I have seen several (sometimes severe) Ubuntu made bugs.

---

### Post by Carlos Sevcik on 2009-04-20
ptn107

Thanks, I just found the bug there, but there was no mention of the difference I find between OO downloaded from Ubuntu repositories and from [www.openoffice.org](www.openoffice.org) original AMD64 files.

---

