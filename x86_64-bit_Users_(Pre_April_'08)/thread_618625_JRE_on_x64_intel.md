---
title: "JRE on x64 intel"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by reportingsjr on 2007-11-20
I have looked through quite a few threads here and can't seem to get Java applets to work! I am completely new to linux so I don't have a great understanding of everything, although I do know the basics.

I tried kilz script, and I couldn't figure out how to install 32-bit firefox, so unless someone can guide me through that I can't use that option. (Yeah, I know, I have no clue what to do!)

I tried installing icedtea and that just made all applets white.

Any help appreciated!
Thanks!!

---

### Post by saru411 on 2007-11-20
if you used kilz script ( here ... [http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)) it should have asked you what version of firefox you wished to install, btw i prefer swift weasel.) i would also recommend uninstalling icedtea before doing this if you havent already. maybe you dont know exactly where the script is located in his thread. it is here ... [http://home.comcast.net/~ubuntume/ff32-3in1-6.2.2.tar.gz](http://home.comcast.net/~ubuntume/ff32-3in1-6.2.2.tar.gz)

> Browser Install Script (Updated 10/29/07)
This script allows you to choose the browser you want to install from the ones on this page. It also lets you choose if you want to install the plugins by asking before the plugin is installed. You only have to run this script once. The script needs to be ran from the folder that extracts. That folder should also be on your Desktop. After running this script once you can install any of the other browsers below by double clicking on its deb file.
*****I have just created a new script with all new versions, including Swiftweasel. The new script will work on Dapper, Edgy, Feisty, and Gutsy.


---

### Post by reportingsjr on 2007-11-20
Hmm, thanks for that link!

I ran it, did all the stuff it said, then went to terminal and typed firefox32. Firefox opened, but I went to a java applet and it gave me the toolbar of death. Said I needed a plugin again.

Any clue what I did wrong?

---

### Post by saru411 on 2007-11-20
no im unsure of why i will not work. my guess would be that you tried other methods to install java and they are in the way. if you know what you installed previously you could uninstall it then try again. im sure someone around here will be able to help you, but if you cannt wait you could always do a fresh install, get updates, reboot, then run the script. i tend to make a mess of things and find out most of the answers to my problems. then i make a fresh install and aplly what i learned. im not saying you have to do this, but its the method ive used while learning ubuntu.

you can always wait until someone who knows more comes around though. im sure kilz will see this post and help you out if he knows the answer.  

cheers

---

### Post by reportingsjr on 2007-11-20
Yeah, I did try to install a ton of java plugins before. I thought I had install most of them. (I'm guessing apt-get uninstall <list> will work? I still have the list of what I tried to install. So hang on!)

I've already un-installed then installed it once, and I would prefer not to do that again.

---

### Post by sawjew on 2007-11-20
The command to uninstall is ```
apt get remove <whatever>
```

and it is a good habit to get into to add ```
apt get remove --purge <whatever>
```

this will remove any configuration files as well which can interfere with new software installations.

I have found that iced-tea works for most java applets but not the iced tea from the ubuntu repositories.  You need to use this repository [here]("http://ubuntuforums.org/showthread.php?t=580792&highlight=iced+tea") in post number 9.

Most applets work but not all.

good luck!

---

### Post by dasunst3r on 2007-11-20
I hear that Sun is going to have a x86_64 version of their plugin in the next update of Java 6.  Can someone confirm or refute that?

---

### Post by reportingsjr on 2007-11-20
Sawjew, thanks for the command, I removed all of the java I had before.

I see the post, but how do I "upgrade & update"? Would be awesome to get java running!

dasunst3r, it would be awesome if they are coming out with one!!

---

### Post by sawjew on 2007-11-20
you update & upgrade like this;
```
sudo apt-get update
sudo apt-get upgrade
```

That is just to make sure your repository indexes and installed packages are up to date.

---

### Post by reportingsjr on 2007-11-20
Hmm, I added the two said lines, then did an update and upgrade, but when I went back to the applet it said to install the plugins again! What am I doing wrong?!?

---

### Post by sawjew on 2007-11-20
You may need to link the plugin so firefox can find it.  Try running the following command in a terminal;

```
sudo ln -s usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so /usr/lib/firefox/plugins/gcjwebplugin.so
```

Hopefully that will link the java plugin to the firefox plugins directory.  I am at work on Windows at the moment so I can't check my configuration until tonight.  Let me know if you have any more issues and I will see if I can help later.

NOTE:  make sure Firefox is completely shut down when you do this or it may not work.

When you have finished you can go [here ]("http://www.java.com/en/download/help/testvm.xml")to test the plugin.

---

### Post by vijirajan on 2007-11-20
> **dasunst3r said:**
> I hear that Sun is going to have a x86_64 version of their plugin in the next update of Java 6.  Can someone confirm or refute that?

Actually its planned for Java 7 not in Java 6.

---

### Post by reportingsjr on 2007-11-21
Hmm, I tried that line and I got this:
```

ln: creating symbolic link `/usr/lib/firefox/plugins/gcjwebplugin.so' to `usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so': File exists

```

But it still doesn't recognize it.

By the way, I'm on an intel.

---

### Post by saru411 on 2007-11-21
i think you misunderstood what he was saying...he gave you the commands to update your libraries. then you are to use the link to install the java. oh and amd64=intel core 2 duo. amd64 is only the architecture of the chip, not the brand itself.

---

### Post by dralokyn on 2007-11-21
i've given a thorough explanation on how to fix your sym links here:
[http://ubuntuforums.org/showthread.php?t=615722](http://ubuntuforums.org/showthread.php?t=615722)
in my example i used blackdown j2re, but the instructions will work for iced-tea if you substitute your folders and file names. this is because your sym links, although they exist, may point to the wrong location.

---

### Post by reportingsjr on 2007-11-21
Now I'm confused, I did the update & upgrade or whatever, re-installed iced tea, and ran that line. Was that wrong?

And OOOOHH. I always thought AMD was a brand. My bad!

---

### Post by reportingsjr on 2007-11-21
I already did that, just did it again though.

---

### Post by dralokyn on 2007-11-21
did you go through and delete all the current java symlinks? that's important.

---

### Post by reportingsjr on 2007-11-21
Yeah, I deleted all of the symlinks I could find. Still nothing.

---

### Post by Kilz on 2007-11-21
> **reportingsjr said:**
> Hmm, thanks for that link!

I ran it, did all the stuff it said, then went to terminal and typed firefox32. Firefox opened, but I went to a java applet and it gave me the toolbar of death. Said I needed a plugin again.

Any clue what I did wrong?

Did you by any chance have firefox (64bit) open when you opened firefox32?

---

### Post by reportingsjr on 2007-11-21
No, I have 64-bit closed like it said I would have to.

---

