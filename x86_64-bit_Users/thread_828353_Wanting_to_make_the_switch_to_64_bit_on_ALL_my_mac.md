---
title: "Wanting to make the switch to 64 bit on ALL my machines."
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by stchman on 2008-06-13
Hello all,

I am almost ready to make the switch to 64 bit completely.

I have an Athlon 64 machine that I installed 64 bit Hardy and have gotten everything to work besides gDesklets.

I have a Core 2 Quad desktop and Core 2 Duo laptop that I want to convert over.  I do notice that on the Athlon 64 desktop that it does run noticably quicker using the 64 bit over the 32 bit.

The Java plugin thing works by installing Icedtea over a 32 bit SUN Java plugin.  The Flash plugin works very well in 64 bit.

The only thing is getting gDesklets to run.  The gDesklets package installs just fine but it freezes when I run it.  Any ideas?

Can I assume that if a PC runs 32 bit Hardy that it will run 64 bit Hardy just as flawlessly provided it has a 64 bit processor.

Anything I should be aware of when making the switch.  I am going ot assume that since all the drivers are in the kernel and since the 64 bit kernel is recompiled using a 64 bit compiler all the hardware should work just the same.

Thanks.

---

### Post by cjm5229 on 2008-06-13
Try using Screenlets instead of gDesklets. You can get the latest deb at getdeb.net. Works great.

---

### Post by Melk79 on 2008-06-13
As cjm5229 said, use Screenlets.  They work great for me.  Also, I'd say your assumption is good considering your Core 2 Duo statement.  I really haven't had any 32 vs 64 bit problems except for those jerks at Real/Rhapsody not offering a 64-bit plugin for Firefox.  Google Earth took a bit of caring, but there are posts here to cover that if you use it.

---

### Post by DizzyTech on 2008-06-13
Go for it, you'll enjoy it.  I concur with the other posts; use either Screenlets or Google Gadgets.

As well, if these computers are for personal use, definitely add the Medibuntu repositories.  That'll give you a codecs metapackage, w64-codecs, Google Earth, Skype, and Adobe Reader (and plugin) all working on 64-bit.

Be careful with some other repos, though.  My opinion is that Hardy is the first "really" stable 64-bit edition.

---

### Post by philinux on 2008-06-14
I've had next to zero major problems using 64 bit. Even running Tomb Raider Anniversay under wine and compiz.

Only nuisance is npviewer.bin crashing all the time and gvfs crashing. Both are bugged and I just ignore them as it makes no difference.

I wonder why gdesklets wont run? Might just install them and see if it crashes here too.

Edit - that was quick eh. Crashes and apport caught it. Says cant report as some packages obsolete.

---

### Post by philinux on 2008-06-14
Upgrade those packages and still crashed. There is a bug report.

---

### Post by JoshuaRL on 2008-06-14
You might search through the archive for this.  It's a problem with a python file, and can be fixed.

---

### Post by stchman on 2008-06-15
> **DizzyTech said:**
> Go for it, you'll enjoy it.  I concur with the other posts; use either Screenlets or Google Gadgets.

As well, if these computers are for personal use, definitely add the Medibuntu repositories.  That'll give you a codecs metapackage, w64-codecs, Google Earth, Skype, and Adobe Reader (and plugin) all working on 64-bit.

Be careful with some other repos, though.  My opinion is that Hardy is the first "really" stable 64-bit edition.

I found the gstreamer packages in the Hardy repos work for mp3, mpeg1/2/4, avi, wmv, etc.  I did use the libdvdcss2 from Medibuntu for encrypted DVD playback and also Google Earth.  I don't use Adobe very much as Evince doe the job.  There are times when Acrobat is needed but not that often.

I did have an issue with Hardy 64 with it losing all it's associations.  I did some reading and nothing.  I finally reinstalled and all is back to normal.  It actually took only about 1 hr to get it back up an running.

---

### Post by ken78724 on 2008-11-29
DizzyTech & stchman thanks for covering benefits you get using Medibuntu repositories. But, I'm not up to sweep. I'd like to benefit from Google Earth, Skype, and Adobe Reader on my 64-bit P5GC-MX, running hardy 8.04.1 (auto updated). Should I install Medibuntu repositories or am I misunderstanding altogether? 

Or would a hardy 8.10 beta install give me the same? :popcorn:

---

### Post by ken78724 on 2008-11-30
apologies, found a post regarding the mediubuntu repositories. + have 8.10 ubuntu studio beta 85 percent downloaded. will have to partition if I install as I want old files and to possibly dual boot 8.04.1. for me that means a lots of learning... 
]
thanks again. Kenneth

---

