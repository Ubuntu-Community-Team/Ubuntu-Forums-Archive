---
title: "streaming videos"
date: 2006-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by rajeev1204 on 2006-12-29
hi

do any of u guys have any luck with the mplayer plugin for firefox to play streaming media over the net? or any other plugin?

i cant play real media , only quicktime and i hear windows media wont play on 64 bit unless u have a 32 bit mplayer.

i tried with automatix but its really bad quality.

why do these people use wmv and rm instead of mpeg or something for content?

the only thing i can play is dvd/vcd using gxine. 

its nice that atleast quicktime plays nice in all the players 

THANK GOD for FLASH .at least we can watch youtube


regards

rajeev

---

### Post by Gumper on 2007-01-01
How were you able to get flash to work with your AMD64 setup? I would really like to be able to go to websites that are flash enabled.

Thanks,

Gumper

---

### Post by rajeev1204 on 2007-01-01
hi

Read this [http://www.ubuntuforums.org/showthread.php?t=324690](http://www.ubuntuforums.org/showthread.php?t=324690)

Download flash 9 beta 2 from adobe . And follow the instructions in my thread exactly . Guaranteed to work

Let me know


regards

rajeev

---

### Post by Gumper on 2007-01-01
Hi Rajeev and thanks for the help

Gumper

---

### Post by Gumper on 2007-01-01
I tried to install as per the instructions in your link but i get the following error:

-desktop:~$ nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
nspluginwrapper: /usr/lib/firefox/plugins/libflashplayer.so is not a valid NPAPI plugin

I extracted the two files that i downloaded from adobe into the firefox/plugins folder. Was that correct?

any idea want would be causing this? 

Gumper

---

### Post by rajeev1204 on 2007-01-02
hi


u seem to be missing some lib32 libraries. Install linux32 from repositories and also some lib32 essentials . libgtk x11 .so resides in /usr/lib32.
[B]
U NEED TO INSTALL ia32-libs and ia32libs-gtk from the repos [/B]

Try these steps again.Iam assuming u downloaded the rpms for both player and viewer from the mozdev site.Also libflashplayer.so should be copied first. 


sudo alien -d nspluginwrapper-0.9.91.1-1.x86_64.rpm
sudo alien -d nspluginwrapper-i386-0.9.91.1-1.x86_64.rpm
sudo dpkg -i nspluginwrapper*.deb
sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper

Final step of installation 

nspluginwrapper -i /usr/lib/mozilla-firefox/plugins/libflashplayer.so


this will work. 


Just copy /paste the above lines after u have copied libflashplayer.so to /usr/mozilla-firefox/plugins ( I tried in usr/firefox/plugins - so u can try that also)




Let me know.



regards

rajeev


P.S . Maybe u dont need to repeat the steps. Installing ia32-libs and ia32libs-gtk should do the trick. Else repeat all steps

---

### Post by Gumper on 2007-01-02
Thanks Rajeev,

I will try your suggestions later tonight and let you know how i make out.

Gumper

---

### Post by Gumper on 2007-01-02
Well it's working Rejeev. I ran through all the steps that you outline again. I did already have the lib's installed. The only thing different is that i put the libflashplayer.so in /usr/lib/mozilla-firefox/plugins this time instead of /usr/lib/firefox/plugins. Maybe that was the problem?

Thanks again for all your help,

Kind Regards,

Gumper

---

### Post by rajeev1204 on 2007-01-03
hi

That is good to know . Well, it was either firefox or mozilla-firefox - i dont really remember haha. Anyways, glad to help.


By the way , flash works pretty well now doesnt it?

enjoy youtube !!


happy new year

regards
rajeev

---

