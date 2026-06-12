---
title: "A Little 64bit Help..."
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by GSF1200S on 2007-10-18
Ok, first off im currently running Feisty 32bit installed from the alternate CD with kde core on top.

All of my hardware currently works, including my wireless and video (video uses repos glx-new driver). Will I have any additional issues with the 64bit Gutsy version supporting my hardware? Im not concerned with the Java/Flash thing on Firefox- I will figure that out.

I have a ibuypower HEL80 with an Intel Core2Duo, an Atheros chipset wireless card (currently running on a restricted driver in the repos), and an Nvidia GeForce 7600. 

What do you guys think?

---

### Post by Coucouf on 2007-10-18
If you're only concerned about drivers you're good to go ! ^^
A vast majority of drivers, even proprietary, are provided in both 32-bit and 64-bit flavours (ATI and nVidia are, I can't say about the Wifi chip).

Maybe you can try the live CD and see if you can configured your wireless network with it ?

The tricky point might really be flash/java plugins installation.

---

### Post by Kilz on 2007-10-18
> **Coucouf said:**
> If you're only concerned about drivers you're good to go ! ^^
A vast majority of drivers, even proprietary, are provided in both 32-bit and 64-bit flavours (ATI and nVidia are, I can't say about the Wifi chip).

Maybe you can try the live CD and see if you can configured your wireless network with it ?

The tricky point might really be flash/java plugins installation.

java yes, if you want to run one with a security manager. Flash no, with Gutsy it should "just work"

---

### Post by GSF1200S on 2007-10-18
Yeah, im trying to torrent the desktop 64 Gutsy now.. I usually just install a command line, connect to wireless from there, and build the system with apt. Hopefully the wireless will work, but if the driver from the 32 bit repos works, than it should for 64 bit. I may have to copy the package of the driver over to my other partition and move it to /home from the command line worst case. Shouldnt be that bad.

Thats cool about Flash.. I thought that was going to be my biggest struggle. Javas a pain, huh? Ahhhh, if only it wasnt for Frostwire I wouldnt even need it. Its not impossible though, right? If its possible.. ill figure it out :)

**EDIT** What do you mean by "one with a security manager?" The one I currently have on this 32bit install is Java Runtime 5, and the only app I use is Frostwire. As it pertains to any other Java program, I dont care. I try to stay away from it- the overhead of Java isnt usually worth it..

---

### Post by Kilz on 2007-10-18
> **GSF1200S said:**
> Yeah, im trying to torrent the desktop 64 Gutsy now.. I usually just install a command line, connect to wireless from there, and build the system with apt. Hopefully the wireless will work, but if the driver from the 32 bit repos works, than it should for 64 bit. I may have to copy the package of the driver over to my other partition and move it to /home from the command line worst case. Shouldnt be that bad.

Thats cool about Flash.. I thought that was going to be my biggest struggle. Javas a pain, huh? Ahhhh, if only it wasnt for Frostwire I wouldnt even need it. Its not impossible though, right? If its possible.. ill figure it out :)

**EDIT** What do you mean by "one with a security manager?" The one I currently have on this 32bit install is Java Runtime 5, and the only app I use is Frostwire. As it pertains to any other Java program, I dont care. I try to stay away from it- the overhead of Java isnt usually worth it..

Java for frostwire shouldn't be an issue, a java plugin for a browser might. There is a 64bit plugin for java (icetea also called gjc), but it runs without a security manager. So if someone writes a malicious applet to say reformat your drive, or install a rootkit. It will just as soon as the applet loads in your browser. Frostwirwe will ise the ia32-java5 or ia32-java6 package, thats different that the 64bit plugin.
You can install a 32bit browser, flash, and java if you want for the few sites that use java. There is a link in the stickies.

---

### Post by GSF1200S on 2007-10-18
> **Kilz said:**
> Java for frostwire shouldn't be an issue, a java plugin for a browser might. There is a 64bit plugin for java (icetea also called gjc), but it runs without a security manager. So if someone writes a malicious applet to say reformat your drive, or install a rootkit. It will just as soon as the applet loads in your browser. Frostwirwe will ise the ia32-java5 or ia32-java6 package, thats different that the 64bit plugin.
You can install a 32bit browser, flash, and java if you want for the few sites that use java. There is a link in the stickies.

Oh, I forgot about the Java browser part. Ill try to get that running. Ill definitely stay away from the one without a security manager. Theres bound to be some threads in here on how to do it. Once again, if its not impossible, Ill figure it out.

Thanks alot for the help :)

---

### Post by tomdkat on 2007-10-18
> **Kilz said:**
> Frostwirwe will ise the ia32-java5 or ia32-java6 package, thats different that the 64bit plugin.I'm able to run FrostWire using the 64-bit Java runtime from Sun.  This is on Feisty Fawn (I'm upgrading to Gutsy Gibbon now).

Peace...

---

### Post by GSF1200S on 2007-10-18
Good news.. Wireless works out of the box on Gutsy 64 live, so setting up a network from the command line shouldnt be too hard. Uhhh... I just installed a fresh 32bit feisty- why is setting up Linux so fun?

Looks like I might need to run swiftweasel to get the java working.. id rather stick with a 64bit browser and fight with it till it works...

---

### Post by steveneddy on 2007-10-18
I'm waiting for the 64 bit java plugin myself. I'll wait because java isn't that important at the moment.

---

