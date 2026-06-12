---
title: "Flash problem"
date: 2007-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by sagivegh on 2007-12-12
Hi,

just finished to install ubuntu 7.10 64-bit, and I add flash plugin in the firefox, it's finish, I restart the firefox, and he ask me again to install the plugin, now after I try to install the plugin again he give me a message that: "flashplug-nonfree is installed" but no flash in the firefox...what should I do?

Thanks,
Sagi
:guitar:

---

### Post by John.Michael.Kane on 2007-12-12
Take a look over here  [Bug #173890 flashplugin-nonfree md5sum mismatch support thread]("http://ubuntuforums.org/showthread.php?t=636397")

Another option which may work is to install the 32bit browser, and plug-in. until the repo package is updated.
[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java")

---

### Post by bash on 2007-12-12
Did you run a 32bit system before? And had there firefox with flash in 32bit? If yes: I had the same problem. Upgraded from 32 to 64bit and suddenly no flash in 64bit.

Solution is easy: 

1. Shutdown Firefox
2. Go to your home and move the hidden .mozilla folder to your desktop. MOVE not COPY!
3. Start firefox. Got to some page requiring Flash. Say yay coz it works.
4. Close firefox. Copy hidden .mozilla folder back to your home folder.
5. Open firefox again and check if flash still works.

Oh and just for security back up your bookmarks and whatever else important you got in firefox before you do this or they might be gone.

---

### Post by Kilz on 2007-12-12
> **bash said:**
> Did you run a 32bit system before? And had there firefox with flash in 32bit? If yes: I had the same problem. Upgraded from 32 to 64bit and suddenly no flash in 64bit.

Solution is easy: 

1. Shutdown Firefox
2. Go to your home and move the hidden .mozilla folder to your desktop. MOVE not COPY!
3. Start firefox. Got to some page requiring Flash. Say yay coz it works.
4. Close firefox. Copy hidden .mozilla folder back to your home folder.
5. Open firefox again and check if flash still works.

Oh and just for security back up your bookmarks and whatever else important you got in firefox before you do this or they might be gone.

That shouldnt work for a number of reasons. 

1. You cant upgrade a 32bit install to 64bit.
2. Plugins are not stored in ~/.mozilla but in /usr/lib/mozilla/plugins
3. If this helped at all it would be undone by copying the folder back into place.

I am just trying to understand why it would work. If I am wrong would someone please point out why.

---

### Post by bash on 2007-12-12
> **Kilz said:**
> That shouldnt work for a number of reasons. 

1. You cant upgrade a 32bit install to 64bit.
2. Plugins are not stored in ~/.mozilla but in /usr/lib/mozilla/plugins
3. If this helped at all it would be undone by copying the folder back into place.

I am just trying to understand why it would work. If I am wrong would someone please point out why.

Well thank you for you theoratical thesis about what should or should not work. But let me rephase this for you: I works! 

And yes you can upgrade from 32bit to 64bit. If you have a seperate home partition. Just install the / 64bit partition over the old 32bit one. Works flawlessly. And it isn't undone by those steps. Because thats exactly what I did.

---

### Post by Kilz on 2007-12-12
> **bash said:**
> Well thank you for you theoratical thesis about what should or should not work. But let me rephase this for you: I works! 
Why does it work? What did it fix exactly? I am not asking you to suggest what you have done is correct, or that I am wrong, but others (with a lot of experience) to see if I am correct in my thinking. This is not an argument.
> **bash said:**
> And yes you can upgrade from 32bit to 64bit. If you have a seperate home partition. Just install the / 64bit partition over the old 32bit one. Works flawlessly. And it isn't undone by those steps. Because thats exactly what I did.
You did not "upgrade" a 32bit install then. You simply saved your home folder. This upgrades nothing.
But, moving a folder to one place, opening a program so that it recreates a settings folder. Then moving (or copying) the original folder back into place will overwrite the files you just created. To me the logic says that it will undo any good that may be done by moving it in the first place.

---

### Post by bash on 2007-12-12
Well it's "upgraded" in a way. I moved from 32bit to 64bit while keeping all my files and settings. Just needed to reinstall the apps.

And my problem was that the whenever I accessed a site containing a flash element, like youtube instead of the flash just a blank space would appear. Just image where there should be the Youtube video, there is just empty white space. Then I did what I discribed above and after that it work. Don't ask me why, but it did. So me was happy and didn't really care about the why.

Also what I just noticed now. I left my /home parition untouched. Meaning I didn't create a new one when I installed the 64bit version. So is the ext3 partition itself then 32bit, or doesn't it matter with filesystems. Because so far I had no problems and afaik it shouldn't matter. But now Im starting to doubt myself.

---

### Post by sagivegh on 2007-12-12
Thanks John,

the link with the bug help me to fix the problem.

Sagi

---

### Post by Afkpuz on 2007-12-12
Solution here for anyone still having problem

[http://ubuntuforums.org/showthread.php?t=639029](http://ubuntuforums.org/showthread.php?t=639029)

---

### Post by John.Michael.Kane on 2007-12-12
> **Afkpuz said:**
> Solution here for anyone still having problem

[http://ubuntuforums.org/showthread.php?t=639029](http://ubuntuforums.org/showthread.php?t=639029)

Thanks for your workaround. 

I used Kilz 32 bit Firefox with Flash guide as a workaround.While the bug in question is being worked on.

---

### Post by Kilz on 2007-12-12
> **John.Michael.Kane said:**
> Thanks for your workaround. 

I used Kilz 32 bit Firefox with Flash guide as a workaround.While the bug in question is being worked on.

I have just modified my [nspluginwrapper script]("http://ubuntuforums.org/showthread.php?t=476924") to install flash to Gutsy since the problem seems to be taking forever for the developers to fix. [Click here if you want to try it.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.2.tar.gz")

---

### Post by John.Michael.Kane on 2007-12-12
> **Kilz said:**
> I have just modified my [nspluginwrapper script]("http://ubuntuforums.org/showthread.php?t=476924") to install flash to Gutsy since the problem seems to be taking forever for the developers to fix. [Click here if you want to try it.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.2.tar.gz")

That script checks out. Firefox 64bit works with the flash site I tested.

Thanks.

---

### Post by bash on 2007-12-13
I had no problem installed flash just out of the repos. Actually even through the wizard in firefox itself. Wow, seems like Im one of the only ones that actually just worked for.

---

