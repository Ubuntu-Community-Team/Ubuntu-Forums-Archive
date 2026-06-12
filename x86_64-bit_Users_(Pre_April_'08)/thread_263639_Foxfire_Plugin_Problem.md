---
title: "Foxfire Plugin Problem"
date: 2006-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2006-09-23
I am struggling to get multimedia working on my new  64 build.  I installed an Audigy card last night and now have sound working on Dapper.  I ran the script listed in Kilz Foxfire "How To" but still get a missing plugin message each time I try and play video or music.  I ran both the Foxfire script to load Java, and mplayer as well as the embedded mplayer script within the "how to"  Everything seems to work correctly with no errors other than the ones noted in the "how to".  I notice when I open Foxfire Edit/Preferences/View and Edit Actions that there are no file types or associated plugins listed.  This leads me to believe that the actions being performed by the scripts are not being saved to FoxFire. The scripts left many file folders on my Desktop.  One Mozilla-mplayer-3.17.1 contains ERROR: wrong architecture 'i386".  Any suggestions on how I can isolate my problems?  Before I ran any scripts I enabled both universe and multiverse.

---

### Post by Kilz on 2006-09-23
> **j0eb0b said:**
> I am struggling to get multimedia working on my new  64 build.  I installed an Audigy card last night and now have sound working on Dapper.  I ran the script listed in Kilz Foxfire "How To" but still get a missing plugin message each time I try and play video or music.  I ran both the Foxfire script to load Java, and mplayer as well as the embedded mplayer script within the "how to"  Everything seems to work correctly with no errors other than the ones noted in the "how to".  I notice when I open Foxfire Edit/Preferences/View and Edit Actions that there are no file types or associated plugins listed.  This leads me to believe that the actions being performed by the scripts are not being saved to FoxFire. The scripts left many file folders on my Desktop.  One Mozilla-mplayer-3.17.1 contains ERROR: wrong architecture 'i386".  Any suggestions on how I can isolate my problems?  Before I ran any scripts I enabled both universe and multiverse.

That shouldnt have happened. The script should have deleted all folders when it was done. To make sure 32bit firefox was installed go to Applications >Internet and see if there is a Firefox32 Web Browser to click on.

---

### Post by samlalani on 2006-09-23
I had installed firefox using the following command:

    sudo apt-get install firefox

and then I installed Java from Sun, which works because when I type java -version, it gives me version 1.5_06 which is what I installed.  I also put into the firefox/plugins directory a symbolic link to libjavaplugin_oji.so but I still get that no plugins are installed.

Is there a difference between the firefox I installed and the Firefox32 you are referring to?  Also, could it be that I installed Java 1.5 instead of the Java 1.4 which is in the script?

---

### Post by Kilz on 2006-09-23
> **samlalani said:**
> I had installed firefox using the following command:

    sudo apt-get install firefox

and then I installed Java from Sun, which works because when I type java -version, it gives me version 1.5_06 which is what I installed.  I also put into the firefox/plugins directory a symbolic link to libjavaplugin_oji.so but I still get that no plugins are installed.

Is there a difference between the firefox I installed and the Firefox32 you are referring to?  Also, could it be that I installed Java 1.5 instead of the Java 1.4 which is in the script?

Yes if you have a 64bit version of Ubuntu/Kubuntu/Xubuntu. By default it installs a 64bit firefox. That firefox is not compatible with some of the 32bit plugins like flash, etc.
I long ago saw this as a problem. So I created an installable 32bit firefox package for the 64bit version of Ubuntu/Kubuntu/Xubuntu. There is an howto and automated setup script that also installs the plugins in the correct locations. The link to its page can be found in my signature.

---

### Post by j0eb0b on 2006-09-23
I'm making progress.  There are now both 32 and 64 bit foxfire browsers in the internet-applications directory.  The 32 bit version has plugins installed and i am able to play Google video so that much works.  I haven't been able to get internet radio streams to play yet but will keep playing with things. If I'm still having problems tomorrow I'll post back.

Thanks for your help.

Joe

---

### Post by floydwaferfield on 2006-09-23
It's Firefox. Not Foxfire. Firefox.

---

