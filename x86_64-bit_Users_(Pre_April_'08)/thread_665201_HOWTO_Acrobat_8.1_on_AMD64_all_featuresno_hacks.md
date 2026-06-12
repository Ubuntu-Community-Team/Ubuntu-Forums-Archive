---
title: "HOWTO: Acrobat 8.1 on AMD64 all features/no hacks"
date: 2008-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nuke Skyjumper on 2008-01-12
I'm still not sure if "HOWTO" is accurate since all the work is done already, but this is bound to help someone so I'll leave it in.

Adobe Acrobat Reader 8.1 for Linux is really feature filled, and we have to give Adobe credit for actually doing this. Unfortunately Adobe isn't on the 64bit bandwagon yet, so to get full functionality out of Acrobat on a 64bit distro we need a bunch of 32bit compatibility libs.

So I repackaged the 32bit libs to work on Gutsy 64bit. It's not hard to do, and I'll post a HOWTO on that too if nobody else has already.

Anyway, to do this, go to adobe.com under "Downloads", "Get Adobe Reader", and click "Different Language or Operating System". This will give you a pulldown menu where you can pick "Linux x86 (.deb)". Download that package and install with:
```
sudo dpkg -i --force-architecture AdobeReader_enu-8.1.1-1.i386.deb
```

Then install the compatibility libs:
[firefoxlibs32_2.0.0.11+2-0ubuntu0.7.10_amd64.deb]("http://nuklear.org/packages/firefoxlibs32_2.0.0.11+2-0ubuntu0.7.10_amd64.deb")
[lib32gsf-1-114_1.14.7-0ubuntu1_amd64.deb]("http://nuklear.org/packages/lib32gsf-1-114_1.14.7-0ubuntu1_amd64.deb")
[lib32nspr4-0d_4.6.6-3_amd64.deb]("http://nuklear.org/packages/lib32nspr4-0d_4.6.6-3_amd64.deb")
[lib32nss3-0d_3.11.5-3_amd64.deb]("http://nuklear.org/packages/lib32nss3-0d_3.11.5-3_amd64.deb")
[lib32rsvg2-2_2.18.2-1_amd64.deb]("http://nuklear.org/packages/lib32rsvg2-2_2.18.2-1_amd64.deb")
[lib32rsvg2-common_2.18.2-1_amd64.deb]("http://nuklear.org/packages/lib32rsvg2-common_2.18.2-1_amd64.deb")

This is all I needed to get Acrobat fully working under Gutsy 64bit. Good Luck!

---

### Post by pem725 on 2008-01-13
Thanks greatly for the tip.  The other tidbit that might be worthwhile to include is setting the libgtkembedmoz location after the initial startup.  Acrobat complains that it cannot find the darn library.  I initially set it as 

```
/usr/lib/firefox 
```

which would work just fine if I were using firefox64 but it does not work with Acrobat.  So I needed to specify the following instead:

```
/usr/lib32/firefox 
```

At any rate, thanks again.

---

### Post by clearsky on 2008-03-08
Thanks a lot for the info.:popcorn: It works like a charm for me. Now I have more reasons to use ubuntu.

---

### Post by aev on 2008-03-09
Thanks to all.

---

### Post by warp99 on 2008-03-11
I did this very different then the above post. Since I already had the ia32-libs installed from the universe repositories I downloaded the Adobe Reader tar file, then did the following:

```
tar -xf AdobeReader_enu-8.1.2-1.i486.tar.gz
```

then ran the installer

```
 cd AdobeReader && sudo ./INSTALL
```

The default install directory is /opt, but you can install this into another directory. I installed the Adobe Reader into /usr/local since all of my other manually installed programs reside there.

Now in order to use some of the online features you need to install libgtkembedmoz. I downloaded xulrunner directly from mozilla in order to get the proper libs:

[http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.1.3/contrib/linux-i686/xulrunner-1.8.1.3.en-US.linux-i686.tar.gz](http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.1.3/contrib/linux-i686/xulrunner-1.8.1.3.en-US.linux-i686.tar.gz)

```
tar -xf xulrunner-1.8.1.3.en-US.linux-i686.tar.gz
```

copy the directory into the same directory as Adobe Reader:

```
sudo cp -r xulrunner /usr/local
```

open Adobe Reader from the desktop then go to **Edit > Preferences > Internet** and fill in "Browser Executable" as firefox and libgtkembedmoz. as /usr/local/xulrunner, then restart Adobe Reader and viola, online PDF access. 

If you want to use the Adobe Reader plug-in do the following:

```
 cd /usr/local/Adobe/Reader8/Browser && sudo ./install_browser_plugin
```

and choose option 1 for system wide install. ;)

---

### Post by jlo_sandog on 2008-03-11
Sorry, don't mean to start a flame, but what's wrong with evince? or the many others?
The .pdf format hasn't changed in ages. I use acrobat at work (win32). I really don't see anything spectacular about it. Linux has its own pdf viewer.

---

### Post by Kilz on 2008-03-11
> **jlo_sandog said:**
> Sorry, don't mean to start a flame, but what's wrong with evince? or the many others?
The .pdf format hasn't changed in ages. I use acrobat at work (win32). I really don't see anything spectacular about it. Linux has its own pdf viewer.

There is nothing wrong with evince. It works great. Some people are just more comfortable with acrobat. Sometimes when moving to linux we need a security blanket.
But now that I have posted here. The title of this thread is a little deceptive. It says no hacks. When in fact it asks you to install hacked packages from an relatively unknown source. They might be safe, but new users should take caution when installing anything that is not from the Ubuntu repositories.

---

### Post by warp99 on 2008-03-11
> **jlo_sandog said:**
> Sorry, don't mean to start a flame, but what's wrong with evince? or the many others?
The .pdf format hasn't changed in ages. I use acrobat at work (win32). I really don't see anything spectacular about it. Linux has its own pdf viewer.

Some of the PDFs if they have certain DRM features, well if you can call it a "feature" :lolflag:, will only open correctly with Adobe. An Example would be PDFs that have fill in the form dialog. I downloaded some of these PDFs from the IRS and they would not open properly in evince, only in Acrobat Reader.

---

### Post by ze_otter on 2008-03-11
Adobe Reader 8 also supports 3D PDF, which isn't supported on other Linux PDF readers (I deal with technical documentation, and 3D PDF is useful there). Reader 8 is also otherwise pretty decent; it's faster and has a much cleaner UI than the previous versions. Adobe has made a mess of many things, but Reader is actually usable these days (now it only needs a native 64-bit version).

---

### Post by bash on 2008-03-11
Do you also manage to get it to open PDFs inside Firefox in Acrobat? Because if I try to open a PDF inside Firefox it just opens evince.

---

### Post by warp99 on 2008-03-11
> **bash said:**
> Do you also manage to get it to open PDFs inside Firefox in Acrobat? Because if I try to open a PDF inside Firefox it just opens evince.

Is the Adobe plug-in installed? In the URL box of Firefox type: [HTML]about:plugins[/HTML]The Adobe Reader should be the first plug-in installed. If not you need to locate the plug-in for your particular install of Adobe, file name is nppdf.so, and place a copy into your firefox/plugins directory.

If this is a single user machine you can install the plug-in under the /home/<user>/.mozilla/plugins directory. :)

---

### Post by chrism66 on 2008-03-11
[PHP]The Adobe Reader should be the first plug-in installed. If not you need to locate the plug-in for your particular install of Adobe, file name is nppdf.so, and place a copy into your firefox/plugins directory.[/PHP]

nppdf is in my plugin directory and still not working in firefox, and Swiftweasel. I had the plugin working with ndiswapper but when opened a pdf it hogged system resourses so, it was not acceptable to me. I need to print off pdf's for school and envince would never print reliably.

---

### Post by adi_8079 on 2008-03-20
> **Nuke Skyjumper said:**
> I'm still not sure if "HOWTO" is accurate since all the work is done already, but this is bound to help someone so I'll leave it in.

Adobe Acrobat Reader 8.1 for Linux is really feature filled, and we have to give Adobe credit for actually doing this. Unfortunately Adobe isn't on the 64bit bandwagon yet, so to get full functionality out of Acrobat on a 64bit distro we need a bunch of 32bit compatibility libs.

So I repackaged the 32bit libs to work on Gutsy 64bit. It's not hard to do, and I'll post a HOWTO on that too if nobody else has already.

Anyway, to do this, go to adobe.com under "Downloads", "Get Adobe Reader", and click "Different Language or Operating System". This will give you a pulldown menu where you can pick "Linux x86 (.deb)". Download that package and install with:
```
sudo dpkg -i --force-architecture AdobeReader_enu-8.1.1-1.i386.deb
```

Then install the compatibility libs:
[firefoxlibs32_2.0.0.11+2-0ubuntu0.7.10_amd64.deb]("http://nuklear.org/packages/firefoxlibs32_2.0.0.11+2-0ubuntu0.7.10_amd64.deb")
[lib32gsf-1-114_1.14.7-0ubuntu1_amd64.deb]("http://nuklear.org/packages/lib32gsf-1-114_1.14.7-0ubuntu1_amd64.deb")
[lib32nspr4-0d_4.6.6-3_amd64.deb]("http://nuklear.org/packages/lib32nspr4-0d_4.6.6-3_amd64.deb")
[lib32nss3-0d_3.11.5-3_amd64.deb]("http://nuklear.org/packages/lib32nss3-0d_3.11.5-3_amd64.deb")
[lib32rsvg2-2_2.18.2-1_amd64.deb]("http://nuklear.org/packages/lib32rsvg2-2_2.18.2-1_amd64.deb")
[lib32rsvg2-common_2.18.2-1_amd64.deb]("http://nuklear.org/packages/lib32rsvg2-common_2.18.2-1_amd64.deb")

This is all I needed to get Acrobat fully working under Gutsy 64bit. Good Luck!

Worked great for me! Thanks! :guitar:

---

