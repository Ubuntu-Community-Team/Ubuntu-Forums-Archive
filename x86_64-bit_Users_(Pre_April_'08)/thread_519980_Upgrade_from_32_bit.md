---
title: "Upgrade from 32 bit"
date: 2007-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by PurposeOfReason on 2007-08-07
From what I've read it isn't possible to just upgrade from the 32bit version to the 64bit version without a fresh install. So while I would prefer to try out the 64bit version as I have the hardware for it, I don't feel like losing all my files and whatnot. Basically a large music, movie, and school paper type files. So is there a way to upgrade or do a fresh install while still keeping all of these? 

And if I upgrade will the following things still work just fine?
-Compiz fusion
-AWN
-Thunderbird
-AcidRip
-Deluge

---

### Post by rsambuca on 2007-08-07
All of the programs you have listed will work perfectly with the 64-bit version.  If they aren't in the standard repositories, there are amd64 debs available.

With respect to your documents, movies, etc, you will have to back those up unless they are already on a separate partition.

---

### Post by PurposeOfReason on 2007-08-07
So would it work to say(right now my only partition is Ubuntu), partition everything so I'd have one 32bit partition and one 64bit. Then drag and drop the files over. Then deleting the 32bit and making the 64bit take the full space?

---

### Post by John.Michael.Kane on 2007-08-07
> **PurposeOfReason said:**
> From what I've read it isn't possible to just upgrade from the 32bit version to the 64bit version without a fresh install. So while I would prefer to try out the 64bit version as I have the hardware for it, I don't feel like losing all my files and whatnot. Basically a large music, movie, and school paper type files. So is there a way to upgrade or do a fresh install while still keeping all of these? 

Theres no known way to upgrade from 32bit ubuntu to 64bit.

Your best bet is to back up the data you want to save to some for of media, and do a fresh install.

> **PurposeOfReason said:**
> And if I upgrade will the following things still work just fine?
-Compiz fusion
-AWN
-Thunderbird
-AcidRip
-Deluge

Compiz fusion: unknown might have to build from source. You can try asking in the thread below.
[How To: Compiz Fusion on Ubuntu 7.04]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion+64bit")

AWN: Again unknown. I have not seen any 64bit debs. You might have to build from source.

Thunderbird: Checks out just fine, and is installable via synaptic,However. If you want the latest you will have to use the third party repo listed below.
[Thunderbird 2 feisty backport]("http://ubuntu.iuculano.it/dists/feisty/thunderbird/")

AcidRip: Is installable via synaptic, and works last i tested it.

Deluge: Is not in the repo,however.  Deluge can found at the link below.
[Deluge]("http://www.getdeb.net/search.php?keywords=Deluge")

---

### Post by tgm4883 on 2007-08-07
> **PurposeOfReason said:**
> So would it work to say(right now my only partition is Ubuntu), partition everything so I'd have one 32bit partition and one 64bit. Then drag and drop the files over. Then deleting the 32bit and making the 64bit take the full space?

Partition 10-15 GB for /,  Make a /home partition with the rest of your space.

---

### Post by incubus on 2007-08-07
I agree with SD-Plissken and tgm4883.  If I was in your position, I would really backup everything and re-design the partitions.  Having your data files separated from the system ones gives you a lot of flexibility -- being able to easily fresh-install an OS is just one example.  Take some time to think about the partition scheme (how many, what sizes, what for, etc).

Now, if for some strong reason you absolutely cannot proceed that way, you could use some live CD with gparted (or any  tool you trust) to repartition on the fly.  I've done it before and I really recommend *against* it, because it's a lot of risk.

Having backups is always good anyway.

incubus

---

### Post by PurposeOfReason on 2007-08-07
Well I just did it. I actually went out and got a external harddrive because I know eventually I'll need one. Put everything onto that, then the really important ones on my ipod, and then still kept that partition, just make it a hell of a lot smaller. So far the only thing to give me lip, surprisingly, is conky. It complains when I try to run the exact same weather scrips I did before but eh, it's just conky. Next I'm thinking I'm going to try to get flash and all that for firefox. IT does get installed with the 64bit version, right?

---

### Post by rsambuca on 2007-08-08
> **PurposeOfReason said:**
> Well I just did it. I actually went out and got a external harddrive because I know eventually I'll need one. Put everything onto that, then the really important ones on my ipod, and then still kept that partition, just make it a hell of a lot smaller. So far the only thing to give me lip, surprisingly, is conky. It complains when I try to run the exact same weather scrips I did before but eh, it's just conky. Next I'm thinking I'm going to try to get flash and all that for firefox. IT does get installed with the 64bit version, right?

There is two choices for flash in the 64bit environment - nspluginwrapper with the 64 bit browser, or 32 bit browser with the 32bit libraries installed.  (Actually there may be a third option involving an opensource flash-type plugin, but I haven't tried it.

I have used both methods, and find the 32bit browser the better way to go for now as you can also run java quite easily.  Both are very easy to set up, and you just have to follow the excellent how-tos or even use the scripts provided:

[[COLOR="Red"]32-bit browser with flash and java[/COLOR]]("http://ubuntuforums.org/showthread.php?p=1174435#post1174435")
[[COLOR="Red"]nspluginwrapper for 64-bit[/COLOR]]("http://ubuntuforums.org/showthread.php?t=476924")

---

