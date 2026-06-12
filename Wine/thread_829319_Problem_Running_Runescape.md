---
title: "Problem Running Runescape"
date: 2008-06-14
forum: Wine
---

### Post by towerchihuahua on 2008-06-14
Whenever I try to run runescape using the signed default java applet, this is the error that I get. I am using the latest java build, just so that you know. What should I do to fix this? This is the readout that I get when I try to play the game in both low or high quality:

```
Error_loader_nocache - Unable to create cache directory.
Runescape was unable to find a suitable place to store its temporary files. To solve this please either:

# Login to your computer as an 'administator' user, and then try loading RuneScape again. This should give it sufficient access to create its temporary cache.

# Or, create a new directory called c:/rscache or /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.

# If you are unable to do either of the above, then as a last resort you can tell RuneScape not to store any files on the harddisk. When entering the site and choosing between high-detail/low-detail also select 'Unsigned Applet Using Default Java' from the dropdown scroll at the bottom of the detail select page. You will need to do this everytime you load the game. The disadvantage of this is the game will load slower, so if possible use one of the top two solutions instead.

If problems persist then please refer to our technical FAQ which can be found in the FAQ section of our website.
```

Any help at all would be appreciated. Using an unsigned applet is a pain to load every time, and the processor goes crazy with usage.

---

### Post by jamesstansell on 2008-06-14
Did you try creating an /rscache directory like the warning message suggested?

The phrase "latest java build" could mean many different things.  Do you know exactly which java plugin you are using?

For example, on Ubuntu 8.04 the default plugin is icedtea-gcjwebplugin, but it (as far as I understand) doesn't treat signed applets any differently than unsigned applets, so the homegrown runescape caching isn't likely to work with this version.

If you have any pull with runescape suggest for them to convert their applet to a web start application so that standard caching can be used. :)

If you have sun-java6-plugin installed then you might need to uninstall icedtead-gcjwebplugin for things to work.

---

### Post by doorknob60 on 2008-06-14
Meh, there needs to be a sticky about this, I've answered it quite a few times...Anyways, you're probably using OpenJDK, which just doesn't work with the signed applet (yet). You want the Sun Java:
```
sudo apt-get install sun-java6-plugin && sudo update-java-alternatives -s java-6-sun
```

That will install Sun Java and make it the default :)

---

### Post by towerchihuahua on 2008-06-15
Thank you both very much. Though your individual solutions didn't work, your suggestions combined did =) . Much thanks, once again.:lolflag:

---

### Post by DannyW on 2008-06-18
I can confirm in Ubuntu 8.04 I had to uninstall icedtea-gcjwebplugin for RuneScape to work as suggested by jamesstansell. I did not have to create /rscache, however.

I also ran the line given by doorknob60.

Thanks.

---

### Post by Nikayah on 2008-06-19
> **doorknob60 said:**
> Meh, there needs to be a sticky about this, I've answered it quite a few times...Anyways, you're probably using OpenJDK, which just doesn't work with the signed applet (yet). You want the Sun Java:
```
sudo apt-get install sun-java6-plugin && sudo update-java-alternatives -s java-6-sun
```

That will install Sun Java and make it the default :)
When i use that line (in Ubuntu 8.04) i get this error:```
-U:~$ sudo apt-get install sun-java6-plugin && sudo update-java-alternatives -s java-6-sun
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```
Can anyone give me a hand as i really do want to play runescape (Yes i did try to make rscache with full r/w permissions for all but it it still came up with that error)

---

### Post by jamesstansell on 2008-06-19
Nikayah, are running 64-bit?  There is no 64-bit plugin from sun, yet.

(I wonder if there is a 64-bit appletviewer, and if it can run runescape?)

Or, if you're on x86 then you might not have the multiverse repository enabled?

---

### Post by Nikayah on 2008-06-20
Im running 64 bit, I didn't learn that until after I posted.

---

