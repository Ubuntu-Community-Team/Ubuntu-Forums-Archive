---
title: "Java 1.7.0 64 bit binary! Need help!"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kyran1 on 2007-12-27
OK people, this is the low down. I have gotten the pre-jre 7 binary files for the amd64 os of linux. I need help to create a plugin for firefox 64 bit browser. I currently run Ubuntu 7.10 x64 amd. I am new to linux, but have managed to install the jre-7.jar using jre-6 with the java -jar *.jar command. I then overwrote the jre directory with the files from the install (couldn't for the life of me figure out how to link and all the crap...lol). after some tinkering, I got it to work... at least I think I did. It shows up under java -version, so I assume it works.

out put is:
```
java version "1.7.0-ea"
Java(TM) SE Runtime Environment (build 1.7.0-ea-b24)
Java HotSpot(TM) 64-Bit Server VM (build 12.0-b01, mixed mode)
```

would it be possible to use the plugin from, say java-6, for the attachment of java to the browser?
If I can get some help on this I will release the info that I have once I know it works and will not damage some ones os (think of me as a guinea pig).

Thanks for the help.

---

### Post by noshellswill on 2007-12-28
I believe the x64browser plugin is a very different ( and non-existant ) beast.

---

### Post by Kyran1 on 2007-12-28
Well, as far as I knew, there wasn't java support for 64 bit machines. just java in 32 bit. Or am I wrong? This is java 64 bit (1.7.0 jre se) for 64 bit machines.

---

### Post by Kilz on 2007-12-28
> **Kyran1 said:**
> Well, as far as I knew, there wasn't java support for 64 bit machines. just java in 32 bit. Or am I wrong? This is java 64 bit (1.7.0 jre se) for 64 bit machines.

There is already java in the repositories, what there isnt is a 64bit Sun Java plugin for your browser. you can run java programs, but you cant see java in websites. There are a few plugins that are not from sun (gcj, icedtea, and blackdown) but they dont work for every site. But it is possible to run 32bit sun java and a 32bit broswer

---

### Post by Kyran1 on 2007-12-28
> **Kilz said:**
> There is already java in the repositories, what there isnt is a 64bit Sun Java plugin for your browser. you can run java programs, but you cant see java in websites. There are a few plugins that are not from sun (gcj, icedtea, and blackdown) but they dont work for every site. But it is possible to run 32bit sun java and a 32bit broswer
 
I see. How would one create a plugin? I might give it a try....
I have looked in the repos, but what I have are the sun-java7-jre files that are not in the repos. Do you thing it would be possible to edit the known plugin for 32 bit for 64 bit intergration?

---

### Post by Kilz on 2007-12-28
> **Kyran1 said:**
> I see. How would one create a plugin? I might give it a try....
I have looked in the repos, but what I have are the sun-java7-jre files that are not in the repos. Do you thing it would be possible to edit the known plugin for 32 bit for 64 bit intergration?

No, it wouldnt be possible to make the 32bit plugin 64bit by editing. If that was all it took it would have been done long ago. I really have no clue on how to make the plugin either. You might want to look for a support forum where you got the files. Perhaps they can give you info on how to compile it, or a link to more info.

---

### Post by somegirl on 2007-12-29
Why don't you just manually install it?

That's how I did my java, because it just works better (like, games on pogo.com are not choppy at all). Granted it's not the same file.. but it should work the same.

I followed the directions here: [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

It takes a little negotiating to ubuntu, but, it's figureoutable.

---

### Post by Kilz on 2007-12-29
> **somegirl said:**
> Why don't you just manually install it?

That's how I did my java, because it just works better (like, games on pogo.com are not choppy at all). Granted it's not the same file.. but it should work the same.

I followed the directions here: [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

It takes a little negotiating to ubuntu, but, it's figureoutable.

If you look at the link you gave , in the first section (download) you will see this.

Linux x64 RPM *  filesize: 16.82 MB 	Instructions
* Please use the 32-bit version for Java applet and Java Web Start support.

What this tells us is that there is no 64bit plugin available from Sun. 64bit users have unique issues sometimes. This is one of them. 
But there are options. There are plugins that are not from Sun (icedtea, Gnash, gcj, and Blackdown) but they dont work for every site. 
We can also install [a 32bit browser and plugins from Sun ]("http://ubuntuforums.org/showthread.php?t=202537"). This is a good way to have the best of both worlds. A 64bit install, and a functional browser. Since browsers get little or no performance gain from 64bit because they are not number crunching applications its what I do.

---

### Post by loupy on 2007-12-29
Have you tried installing Icedtea and the icedtea plugin from this repo?


deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

---

### Post by Kilz on 2007-12-29
> **loupy said:**
> Have you tried installing Icedtea and the icedtea plugin from this repo?


deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

You are aware that icedtea is in the ubuntu repositories right? That there is no need to install a third party repository. Besides why would someone interested on building Sun Java want to install icedtea? Icedtea is ok, but it isnt Sun Java, it still has issues.

---

### Post by somegirl on 2007-12-29
> **Kilz said:**
> If you look at the link you gave , in the first section (download) you will see this.

Linux x64 RPM *  filesize: 16.82 MB 	Instructions
* Please use the 32-bit version for Java applet and Java Web Start support.

What this tells us is that there is no 64bit plugin available from Sun. 64bit users have unique issues sometimes. This is one of them. 
But there are options. There are plugins that are not from Sun (icedtea, Gnash, gcj, and Blackdown) but they dont work for every site. 
We can also install [a 32bit browser and plugins from Sun ]("http://ubuntuforums.org/showthread.php?t=202537"). This is a good way to have the best of both worlds. A 64bit install, and a functional browser. Since browsers get little or no performance gain from 64bit because they are not number crunching applications its what I do.

I understand 64 bit users have some difficulty. I was merely suggesting a manual install the same way you'd manually install the 32 bit version because it's a binary file. 
For whatever reason, the manual install on top of adding the mozilla plug-in from the repository just works better than doing it all automated. I know the automated method does not create the /usr/java folder (at least, not that I can remember). 
Speaking of plug-ins, if what you have doesn't have a mozilla plug-in, you might just have to use the java 6 plug-in. And in that case.. I'm not sure if it'd work right.

---

### Post by Kilz on 2007-12-29
> **somegirl said:**
> I understand 64 bit users have some difficulty. I was merely suggesting a manual install the same way you'd manually install the 32 bit version because it's a binary file. 
For whatever reason, the manual install on top of adding the mozilla plug-in from the repository just works better than doing it all automated. I know the automated method does not create the /usr/java folder (at least, not that I can remember). 
Speaking of plug-ins, if what you have doesn't have a mozilla plug-in, you might just have to use the java 6 plug-in. And in that case.. I'm not sure if it'd work right.

The automatic install script installs the ia32 java 5 deb package from the Ubuntu repository. It does not create /usr/java. The Ubuntu developers chose /usr/lib/jvm instead. The manual howto is much older than the script (and not safe for Gutsy) it places files directly from a downloaded tarball. One advantage of using a deb package from the repositories vs a tarball is the deb package gets automatic updates.

---

### Post by loupy on 2007-12-30
> **Kilz said:**
> You are aware that icedtea is in the ubuntu repositories right? That there is no need to install a third party repository. Besides why would someone interested on building Sun Java want to install icedtea? Icedtea is ok, but it isnt Sun Java, it still has issues.

Yes I am aware that IcedTea is available in the official repos.  I also have never had the official repo's IcedTea actually work for me.  And as the original poster was looking for help with a java plugin - I was trying to be helpful as opposed to being on a high horse chastising without actually providing help.

---

### Post by dakini on 2007-12-30
The reason for using the third party repository is simple - it works.  On my machine, the official icedtea packages don't and the browser cannot detect the installed plugin.  Nor could I use Azureus.

As soon as I installed the third party package, everything worked.

---

### Post by Kilz on 2007-12-30
> **loupy said:**
> Yes I am aware that IcedTea is available in the official repos.  I also have never had the official repo's IcedTea actually work for me.  And as the original poster was looking for help with a java plugin - I was trying to be helpful as opposed to being on a high horse chastising without actually providing help.

Help is pointing out that the packages are in an unofficial 3rd party repository with a lone page and no idea who is making the package. Are you even aware of the risks that poses?

---

### Post by julipanno on 2008-01-03
> **loupy said:**
> Have you tried installing Icedtea and the icedtea plugin from this repo?


deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/


This worked wonders for me. Thanks!

---

