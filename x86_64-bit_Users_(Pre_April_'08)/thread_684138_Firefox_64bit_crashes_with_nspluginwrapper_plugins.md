---
title: "Firefox 64bit crashes with nspluginwrapper plugins"
date: 2008-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by edantes on 2008-01-31
I was hoping all Firefox plugins would work in 64-bit  by processing them with *nspluginwrapper*.   That was my impression after reading this page in the mozilla site: [http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)

Oh well, not so.  I tried with the RealPlayer and Acrobat plugins, but using them crashes Firefox-64.

Did I do something wrong?  As an example, this is what dir for the Acrobat plugin:

```

wget http://packages.medibuntu.org/pool/non-free/a/acroread/mozilla-acroread_8.1.1-0medibuntu3_i386.deb
sudo dpkg --force-architecture -i mozilla-acroread_8.1.1-0medibuntu3_i386.deb
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/nppdf.so

```

Would it be simpler to just install the 32bit  Firefox?

---

### Post by Kilz on 2008-01-31
> **edantes said:**
> I was hoping all Firefox plugins would work in 64-bit  by processing them with *nspluginwrapper*.   That was my impression after reading this page in the mozilla site: [http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)

Oh well, not so.  I tried with the RealPlayer and Acrobat plugins, but using them crashes Firefox-64.

Did I do something wrong?  As an example, this is what dir for the Acrobat plugin:

```

wget http://packages.medibuntu.org/pool/non-free/a/acroread/mozilla-acroread_8.1.1-0medibuntu3_i386.deb
sudo dpkg --force-architecture -i mozilla-acroread_8.1.1-0medibuntu3_i386.deb
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/nppdf.so

```

Would it be simpler to just install the 32bit  Firefox?

Nspluginwrapper is a good application, but it is under development. Looking at the [Nspluginwrapper site]("http://gwenole.beauchesne.info/en/projects/nspluginwrapper") it applears that the 8.1.1 version of acrobat isnt listed as compatible. Also please contact the developer and let him know of your bugs.
But if you want to , it is possible to install a 32bit firefox and acrobat. [I have a script and howto ]("http://ubuntuforums.org/showthread.php?p=1174435")that can help you if thats the way you want to go.

---

### Post by macaholic on 2008-02-01
I have the Acrobat 8.1 plugin working via nspluginwrapper, I forced the deb, removed the plugin it installed, and used nspluginwrapper on /opt/Adobe/Reader8/Browser/intellinux/nppdf.so, or wherever it installed Acrobat, and it works like a charm.
P.S. The deb i used was from adobe's site, the medibuntu one didnt work for me, you can het it [here]("http://www.adobe.com/products/acrobat/readstep2_allversions.html"), just select the linux x86 .deb. Hope this helps, if you encounter any issues just post and ill try to help.

---

### Post by edantes on 2008-02-01
**macaholic**  is right!!!  Thanks. With the Adode distribution plus   *nspluginwrapper*  the plugin works perfectly. 

It  turns out the problem was not related to  *nspluginwrapper*, but with the medibuntu installation of Acroread.  Their plugin does not work with Fireforx32 (SwiftWeasel32 in my case) either.  What could it be?  A missing 32bit  library?

> **macaholic said:**
> I have the Acrobat 8.1 plugin working via nspluginwrapper, I forced the deb, removed the plugin it installed, and used nspluginwrapper on /opt/Adobe/Reader8/Browser/intellinux/nppdf.so, or wherever it installed Acrobat, and it works like a charm.
P.S. The deb i used was from adobe's site, the medibuntu one didnt work for me, you can het it [here]("http://www.adobe.com/products/acrobat/readstep2_allversions.html"), just select the linux x86 .deb. Hope this helps, if you encounter any issues just post and ill try to help.

---

### Post by drs305 on 2008-02-29
> **macaholic said:**
> I have the Acrobat 8.1 plugin working via nspluginwrapper, I forced the deb, removed the plugin it installed, and used nspluginwrapper on /opt/Adobe/Reader8/Browser/intellinux/nppdf.so, or wherever it installed Acrobat, and it works like a charm.

Would you mind explaining the exact steps/commands required to do this

---

### Post by macaholic on 2008-02-29
> **drs305 said:**
> Would you mind explaining the exact steps/commands required to do this
Sure, I did
```
wget http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb
sudo dpkg -i --force-architecture AdobeReader_enu-*
nspluginwrapper -i /opt/Adobe/Reader8/Browser/intellinux/nppdf.so
```
Hope that helps.

---

### Post by alexrudd on 2008-03-01
[This new .deb](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/179882/comments/17) worked for me.

---

