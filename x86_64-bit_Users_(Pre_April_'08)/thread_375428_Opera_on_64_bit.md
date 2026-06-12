---
title: "Opera on 64 bit"
date: 2007-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by omrsafetyo on 2007-03-03
I am running the AMD x86_64 Ubuntu 6.10 Edgy.

I installed Opera, because I thought it might be an easy way to get the flash plugin to work - but now I can't get opera to launch.  Its in the application menu - but it will not launch, even after reboot.  Any ideas?

---

### Post by John Jason Jordan on 2007-03-03
> **omrsafetyo said:**
> I am running the AMD x86_64 Ubuntu 6.10 Edgy.

I installed Opera, because I thought it might be an easy way to get the flash plugin to work - but now I can't get opera to launch.  Its in the application menu - but it will not launch, even after reboot.  Any ideas?
How did you install it? Details, please. :)

I should add that I have Opera 9.0 running fine on Edgy amd64, and Flash is working in it also. So it can be done. However, the method I used was haphazard and it worked sort of on accident. I was actually trying to get it to work in 64-bit Firefox. Actually, I succeeded in getting it to work in Firefox, with nspluginwrapper. And that also made Flash work in Opera. But nspluginwrapper was conflicting with other stuff, so I uninstalled it. Afterwards Flash wasn't working in either browser. Then I installed mozplugger, and Flash started working again in Opera, although not in Firefox.

---

### Post by omrsafetyo on 2007-03-03
I used the .deb downloaded off opera.com, and used 
```
sudo dpkg -i --force-all opera-static_9.10-20061214.1-qt_en_i386.deb
```

for the install.  Note, this is 9.1, and you are using 9.0.

Next, I installed open motif:
```
sudo dpkg -i --force-all openmotif_2.1.30-5_i386.deb
```

and finally, flash 9:
```

cd Desktop\Downloads\install_flash_player_9_linux
sudo cp libflashplayer.so /usr/lib/opera/plugins
sudo cp flashplayer.xpt /usr/lib/opera/plugins

```

Like I said, Opera shows up in the application menu - but it doesn't launch.  

Should I have installed libqt3-mt first??  I did not do that - and so far as I know, I don't have it installed.  And if so, should I download the i386, or the amd64 version?  Thanks.

---

### Post by John Jason Jordan on 2007-03-03
> **omrsafetyo said:**
> I used the .deb downloaded off opera.com, and used 
```
sudo dpkg -i --force-all opera-static_9.10-20061214.1-qt_en_i386.deb
```
That is all I did and it worked. I did not install Flash until much later. And I never installed openmotif. I don't even know what it is.

> **omrsafetyo said:**
> for the install.  Note, this is 9.1, and you are using 9.0.
Indeed, 9.0 v. 9.1 may be the root of the problem.

> **omrsafetyo said:**
> Should I have installed libqt3-mt first??  I did not do that - and so far as I know, I don't have it installed.  And if so, should I download the i386, or the amd64 version?  Thanks.
I have libqt3-mt installed. I don't recall installing it before or after installing Opera. As far as I know it was always installed.

You might see if you can figure out what packages and libraries Opera depends on. This can be done from the command line, but I am too new to Linux to know how. I always do it from Synaptic, but Opera will not show up in Synaptic (it doesn't in mine).

---

### Post by omrsafetyo on 2007-03-03
I think I needed open motif for flash.  installing open motif created the plugins directory in opera; then I copied the flash plugins to that folder.  

Perhaps I will try finding the 9.0 package.  I downloaded through a browser - the link available was the altest version of opera - I'll try using mget to download the 9.0 deb, and post back later.  But I will see what I can do about libqt3-mt first - I am not even sure if I have it installed.  I think Opera may depend on it, but I am not entirely sure.  Thanks.

---

### Post by Rooy on 2007-03-04
I'm pretty sure that opera-static doesn't require libqt3-mt, because it has Qt 3.3.5 bundled. Hence the name.
Just that the fonts are all ancient ones ( Helvetica, Times, Courier), don't lookas good as DejaVu.

You can try running Opera from a terminal and post the result here.
Do you have ia32-libs installed? We need that for 32-bit apps to run on x64

---

### Post by omrsafetyo on 2007-03-04
How would I go about launching opera from terminal?

I tried simple "opera" yesterday - and it gave me something to the effect of 
**/bin/opera/whatever/operasomething doesn't exist** 
or something along those lines.  I'll have to check it again before I know for sure, when I get home.  

I have not installed ia32-libs.  Where can I mget that from?  Or will **mget ia32-libs** work?

---

### Post by Colonel Kilkenny on 2007-03-04
Use aptitude in terminal.
"sudo aptitude install ia32-libs ia32-kde-libs" (I don't remember if the second one is needed..)

I had absolutely no problems making flash work in Opera. I installed Opera and all needed packages and then flash. Everything works. And this is with shared version instead of static one.

---

### Post by Nameless_one on 2007-03-04
I also had no problems getting flash to work with opera. I just installed it and it worked. 

However, after I installed the latest [Weekly build](http://my.opera.com/desktopteam/blog/), which didn't work at all, and reverting to an older version, flash doesn't work any more. 

I never meddled with open motif before, I am sure there is a way to get it to work again. Any help?

Edit: OK, another installation solved it. Don't mind me.

---

