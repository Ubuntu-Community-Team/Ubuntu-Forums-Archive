---
title: "Patching Anarchy online error messages"
date: 2007-12-02
forum: Wine
---

### Post by Just-trevor on 2007-12-02
EEK
I followed the Howto here [http://ubuntuforums.org/showthread.php?t=291330&highlight=anarchy](http://ubuntuforums.org/showthread.php?t=291330&highlight=anarchy)
but I can't install the patches, and I can't find where I installed it...
I installed it a second time... at C:/home/trevor-max/Anarchy Figuring it might work
but when I try to install the patches I get "an unsupported operation was attampted" and "Unable to save settings in C:/home/trevor-max/anarchy/prefs/prefs.xml. Make sure you have sufficient permissions to write this file."
And now my mouse is made of dots.
What am I to do???

---

### Post by cogadh on 2007-12-02
First thing you should do is log out and restart the X server to get rid of the mouse issue. You might want to click on the "Stuff I've learned about Wine" link in my sig for some basic information on how to use Wine. Then you should install the game back in the default location. Once you have the game back where it should be, try patching again.

The directory that Wine installs things to is a hidden directory in your home folder named ".wine" (the period on the beginning makes it hidden). You can view hidden files by pressing CTRL-H in the file browser.

---

### Post by Just-trevor on 2007-12-02
I deleted the old one and reinstalled it but I got the same error messages.
:(
The worst thing is that Im llike almost there, I can open up anarchy online and type in the sign in thing but it wont patch..  :(

---

### Post by Just-trevor on 2007-12-02
help anyone?
Im an ubuntu noob so i really don't get much of this.

---

### Post by Just-trevor on 2007-12-02
I have the game downloaded, but I can't patch it.
I get the error "Unsupported operation was attempted"
when I enter my 
I went into the anarchy folder and tried to run the "Anarchy Patcher.exe, but I get 
"'Version.id' is missing. Please reinstall"
and I've gotten that error each of the three times I reinstalled it.
This is pretty frustrating :(

---

### Post by cogadh on 2007-12-02
You have to manually download and apply patches, the client can't do it automatically when used through Wine.

---

### Post by cogadh on 2007-12-02
Why did you create a second thread for this? It was not necessary.

I just answered your question in the first one, you need to manually download and apply the patches. The automatic update features don't work through Wine.

---

### Post by hikaricore on 2007-12-02
merged threads.   don't do this again.

---

### Post by Psy-Q on 2008-10-29
There's a workaround that lets you run and patch AO normally.

Basically, you install ies4linux (which gets you IE 6.0 without messing up your WINE install) and then run AO with that specific instance of IE6 as HTML renderer. Then the patcher works:

[http://rca.vmk.zhdk.ch/blog/articles/2008/10/29/running-newer-anarchy-online-under-wine/](http://rca.vmk.zhdk.ch/blog/articles/2008/10/29/running-newer-anarchy-online-under-wine/)

---

### Post by loudog23 on 2009-02-13
Hi everyone!

I run Anarchy Under POL (PlayOnLinux).
What i do is: i patch the game with ies4linux and then run it with POL

I was wondering if there is a way to start AO inside POL with ies4linux prefix?

ty

---

