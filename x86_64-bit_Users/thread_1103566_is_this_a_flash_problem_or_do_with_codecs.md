---
title: "is this a flash problem or do with codecs ??"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by tricia56 on 2009-03-22
Hi,

I have got my 64bit system working well, after religiously pouring over the howtos etc.  But I just have one further thing that I need help with, there is a particular web page that I am unable to live without or more particularly the videos therein - [http://bigpondvideo.com/nrl/113223](http://bigpondvideo.com/nrl/113223).  the videos begin loading, then it shows stopped and nothing further happens.  I have to go back to Windows to watch these vids.   I don't get any firefox alerts about this.  So, I dont know what is happening and it is hard to research if you don't even know what the problem is.

In about: plugins -

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21



muriel@manuka:~$ ls -al /usr/lib/mozilla/plugins/
total 9328
drwxr-xr-x 2 root   root      4096 2009-03-23 11:22 .
drwxr-xr-x 4 root   root      4096 2008-10-30 11:22 ..
-rwxr-xr-x 1 muriel muriel 9526312 2008-12-11 06:13 libflashplayer.so
lrwxrwxrwx 1 root   root        44 2009-03-18 09:15 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root   root        42 2009-03-18 09:15 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root   root        44 2009-03-18 09:15 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root   root        50 2009-03-18 09:15 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root   root        57 2009-03-23 11:03 npwrapper.libflashplayer.so -> /var/lib/flashplugin-non

 ls -al /usr/lib/firefox-addons/plugins
total 9924
drwxr-xr-x 2 root   root       4096 2009-03-23 11:29 .
drwxr-xr-x 5 root   root       4096 2008-10-30 11:20 ..
-rwxr-xr-x 1 muriel muriel 10131640 2009-02-03 15:06 libflashplayer.so
lrwxrwxrwx 1 root   root         60 2009-03-23 10:54 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

I am complete beginner, 2 weeks, so if someone can identify for me what the problem is, I can go off and research, but I don't know what is wrong!!

Other sites play videos fine.  Not sure what else to tell you.

Thanks, tricia

---

### Post by dcstar on 2009-03-23
> **tricia56 said:**
> Hi,

I have got my 64bit system working well, after religiously pouring over the howtos etc.  But I just have one further thing that I need help with, there is a particular web page that I am unable to live without or more particularly the videos therein - [http://bigpondvideo.com/nrl/113223](http://bigpondvideo.com/nrl/113223).  the videos begin loading, then it shows stopped and nothing further happens.
...........
Other sites play videos fine.  Not sure what else to tell you.

Thanks, tricia

This site is notorious for not supporting Linux and only working on Windows.

Add your complaint to the thousands of others that they have already ignored.

---

### Post by tricia56 on 2009-03-24
Oh is that right?  Thanks I would never have got to that, I had been fiddling with my system thinking it was me.  Thanks

---

### Post by Yellow Pasque on 2009-03-25
BTW, firefox shouldn't show two versions of Flash player. Search your file system for libflashsupport.so and make sure you only have one version.

---

