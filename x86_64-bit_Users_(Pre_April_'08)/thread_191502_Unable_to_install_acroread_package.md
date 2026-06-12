---
title: "Unable to install acroread package"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by pratzabrat on 2006-06-07
I try this 
> sudo apt-get install acroread
The result is that no such package is found and a reference to acroread-debian-files is made. When I try that package, I get unmet dependency on acroread which cannot be installed. I am also unable to get the mozilla plugin package.

---

### Post by tonyr on 2006-06-07
The **acroread** packages are in the **multiverse** repositories.  You must add
those to the file **/etc/apt/sources.list**, then do **sudo apt-get update**, then
retry the install.  Read this: [https://wiki.ubuntu.com/AcrobatHowTo]("https://wiki.ubuntu.com/AcrobatHowTo")

---

### Post by John Jason Jordan on 2006-06-07
[QUOTE=tonyr]The **acroread** packages are in the **multiverse** repositories.  You must add those to the file **/etc/apt/sources.list**, then do **sudo apt-get update**, then retry the install.  Read this: [https://wiki.ubuntu.com/AcrobatHowTo]("https://wiki.ubuntu.com/AcrobatHowTo")[/QUOTE]
That URL says that it is for all versions of Ubuntu. I currently have Ubuntu-64 Breezy (reading the Dapper forums because I'm planning to upgrade soon) and the instructions do not seem to work for Breezy. I have multiverse enabled, but acroread does not appear in Synaptic. The mozilla-plugin is also not listed. From what I read here they will not be in Synaptic for Dapper-64 either.

---

### Post by Strangerdave on 2006-06-07
Why not just use evince?  Does the same thing does it not?

---

### Post by John Jason Jordan on 2006-06-08
[QUOTE=Strangerdave]Why not just use evince?  Does the same thing does it not?[/QUOTE]
Because I have to send PDF files to printers for (expensive) print jobs. If it comes out screwed up I get to pay for it. If it's Adobe Acrobat I can get the printer to shoulder the responsibility. It's the standard the print industry believes in. They may be misguided, but that's a world I have no choice but to live in.

However, I'd be happy to use Evince for browsing web sites. How do I hook it into Firefox on my Ubuntu-64 Breezy computer so web pages that are really PDFs will display in a tab in Firefox?

---

### Post by aysiu on 2006-06-08
According to this...

[http://packages.ubuntu.com/breezy/text/acroread](http://packages.ubuntu.com/breezy/text/acroread)

... there is no 64-bit package for *acroread*.

You might have to compile it from source:
[http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz)

---

### Post by Kilz on 2006-06-08
[QUOTE=aysiu]According to this...

[http://packages.ubuntu.com/breezy/text/acroread](http://packages.ubuntu.com/breezy/text/acroread)

... there is no 64-bit package for *acroread*.

You might have to compile it from source:
[http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz)[/QUOTE]
Aysiu that link is to the Adobe install package, it doesn't need to be compiled, it has a sh install script. :D  It works flawlessly to install 32 bit acrobat to 64 bit Ubuntu. :D

---

### Post by fragos on 2006-06-08
The package managers all refused ti install because my AMD64 was the wrong architecture.  This download,  [http://ardownload.adobe.com/pub/adob...-1.i386.tar.gz](http://ardownload.adobe.com/pub/adob...-1.i386.tar.gz)
with a sudo the enclosed INSTALL scrip successfully installed acroread for me thanks.  I'm new to Ubuntu had been a little confused by the deb package managers.  RPM managers I'm accustomed to never had this problem.

---

### Post by Conq on 2006-06-10
You can use the 32-bit version, but you have to force it, and it might require the 32-bit libraries:

```

wget http://mirror.freax.be/ubuntu/archive.ubuntu.com/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb

sudo dpkg -i --force-architecture acroread_7.0.1-0.0.ubuntu1_i386.deb

```

---

