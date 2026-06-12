---
title: "Safe to upgrade to Fiesty?"
date: 2007-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by nadamsieee on 2007-06-09
Is it safe to upgrade to Fiesty?

The Fiesty 7.04 LiveCD failed miserably for me. I believe the 7.04 LiveCD kernel is mis-configured for systems that mix PATA HDDs, SATA HDDs, and SATA DVDRWs. I ended up installing from the 6.06 LiveCD instead. So I was wondering if Fiesty **plus patches** has worked for anyone who had the same problem.

Here are my hardware specs:
[LIST]
[*][AMD Athlon 64 X2 4800+ Brisbane 2.5GHz]("http://www.amdcompare.com/us-en/desktop/details.aspx?opn=ADO4800IAA5DD") cpu
[*][Gigabyte GA-M55SLI-S4 mobo]("http://www.giga-byte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2310")
[*][Samsung SpinPoint SATA HDD]("http://www.samsung.com/Products/HardDiskDrive/SpinPointTSeries/HardDiskDrive_SpinPointTSeries_HD501LJ.asp?page=Features") (Ubuntu 6.06)
[*]120 GB PATA HDD (extra storage)
[*]60 GB PATA HDD (WinXP)
[/LIST]

Thanks!

---

### Post by Kobalt on 2007-06-10
As far as I know you cannot upgrade a 6.10 system using a LiveCD, you need the AlternateCD to do that. You should consider using this one... 
And you also need to have a fully up to date 6.10 Ubuntu in order to upgrade safely to 7.04. See [this]("https://help.ubuntu.com/community/UpgradeNotes") for more info.

---

### Post by nadamsieee on 2007-06-10
> **Kobalt said:**
> As far as I know you cannot upgrade a 6.10 system using a LiveCD, you need the AlternateCD to do that. You should consider using this one... 
And you also need to have a fully up to date 6.10 Ubuntu in order to upgrade safely to 7.04. See [this]("https://help.ubuntu.com/community/UpgradeNotes") for more info.

I wasn't planning on using a LiveCD, and I'm aware that I need to upgrade to 6.10 before attempting to jump on the 7.04 bandwagon.

My question is, **for those folks who had similar problems with Fiesty**, does Fiesty plus all of the latest updates work? Or will I be stuck with reverting back to 6.06?

Thanks!

---

### Post by Kilz on 2007-06-10
> **nadamsieee said:**
> I wasn't planning on using a LiveCD, and I'm aware that I need to upgrade to 6.10 before attempting to jump on the 7.04 bandwagon.

My question is, **for those folks who had similar problems with Fiesty**, does Fiesty plus all of the latest updates work? Or will I be stuck with reverting back to 6.06?

Thanks!

The question you should be asking imho, is is it worth upgrading to fiesty. What applications have improvements you will use. What new applications for your use are there. If there isnt a benefit. Then there may be no reason to upgrade. Dapper (6.06) is only a year old. It still has until 2009 for support and updates.

---

### Post by nadamsieee on 2007-06-10
> **Kilz said:**
> The question you should be asking imho, is is it worth upgrading to fiesty...

And yet... that's **not** the question I *am* asking. I appriciate everyone's opinions; feel free to send me yours in a private message. But I'm really just looking for data points:

If you:
[LIST=1]
[*]had the similiar install problems with Fiesty on an 64-bit machine with mixed PATA and SATA drives, and
[*]have since attempted to upgrade to Fiesty (plus patches)
[/LIST]

Please do speak up...

Thanks!

---

### Post by Kilz on 2007-06-11
> **nadamsieee said:**
> And yet... that's **not** the question I *am* asking. I appriciate everyone's opinions; feel free to send me yours in a private message. But I'm really just looking for data points:

If you:
[LIST=1]
[*]had the similiar install problems with Fiesty on an 64-bit machine with mixed PATA and SATA drives, and
[*]have since attempted to upgrade to Fiesty (plus patches)
[/LIST]

Please do speak up...

Thanks!

Feel free to use the search function and search the forum for data points. This is a SUPPORT forum. Do you have a problem? You will do much better looking at a linux hardware compatibility site. Use google to find one.

---

### Post by nadamsieee on 2007-06-11
> **Kilz said:**
> Feel free to use the search function and search the forum for data points.

I have searched. I see several posts by folks who have experienced the same problem with the Fiesty 7.04 **LiveCD**. However, I don't see any posts by people who have attempted the upgrade path I mention above.

> **Kilz said:**
> This is a SUPPORT forum. Do you have a problem?

My problem, as I've stated several times now, is that:
[LIST]
[*]the Fiesty 7.04 **LiveCD** doesn't work for 64-bit systems with mixed PATA and SATA drives,
[*]I want to upgrade from Dapper to Edgy to Fiesty (the latest version; this is **not** the same as the LiveCD), and
[*]I would like some data points from others who have tried it before I dive in.
[/LIST]

> **Kilz said:**
> You will do much better looking at a linux hardware compatibility site. Use google to find one.

Uhm, thanks, but no. I know that my hardware is compatible *if the kernel, etc are configured correctly*. The 6.06 install worked great on my hardware, remember? My support question is specific to Ubuntu. I'm in the right place.

Thanks!

---

### Post by Kilz on 2007-06-11
> **nadamsieee said:**
> I have searched. I see several posts by folks who have experienced the same problem with the Fiesty 7.04 **LiveCD**. However, I don't see any posts by people who have attempted the upgrade path I mention above.



My problem, as I've stated several times now, is that:
[LIST]
[*]the Fiesty 7.04 **LiveCD** doesn't work for 64-bit systems with mixed PATA and SATA drives,
[*]I want to upgrade from Dapper to Edgy to Fiesty (the latest version; this is **not** the same as the LiveCD), and
[*]I would like some data points from others who have tried it before I dive in.
[/LIST]


Uhm, thanks, but no. I know that my hardware is compatible *if the kernel, etc are configured correctly*. The 6.06 install worked great on my hardware, remember? My support question is specific to Ubuntu. I'm in the right place.

Thanks!

If you dont like the answers you get. Demand a FULL refund!

---

### Post by nadamsieee on 2007-06-11
> **Kilz said:**
> If you don't like the answers you get. Demand a FULL refund!

Kilz, This reply combined with the rant you sent via private message tells me that you need to relax and just let it go. The support question I'm asking doesn't apply to you; no big deal! Move on; be happy. :)

If you do happen to purchase a new machine, attempt to install Fiesty, run into the same problem I had, and then figure out how to upgrade from Dapper to Edgy to Fiesty, then please come back and let us know.

Its not like I asked **you** personally to answer my question, so don't take it personally that you're not in a situation to answer it! Just be happy that you're not having these problems. ;)

Thanks!

---

### Post by samadams on 2007-06-11
Per your question - no I haven't gotten it to work yet.  I do have a working version of Fiesty via the upgrade path through Edgy from Dapper as you are attempting to do, however, I only get about 15 minutes of uptime before my hardrive spins non-stop and X locks up.  I think it is more of a memory problem though.  I have only 256MB of RAM.  I tried watching a DVD last night and I got about 2 minutes in before it froze.  So perhaps there is a problem with the memory manager or the swap partition is too small for Fiesty.  Which is why I tried to do a clean install.  (I also wanted to make separate partitions for /home and /var)  But I keep getting the error I described in my thread.  I also am looking for more RAM but Dell seems to have disowned the Opti-Plex GX110 on their site so I can't find out the specs.

---

### Post by capecove on 2007-06-11
samadams...

About the GX110, what about this site?

[http://support.dell.com/support/edocs/systems/opgx110/](http://support.dell.com/support/edocs/systems/opgx110/)

Seems that all you would need to know is if you have a slotted or socketed processor. Service manuals seem to be present. May actually help...

Good luck...

---

### Post by nadamsieee on 2007-06-11
> **samadams said:**
> Per your question - no I haven't gotten it to work yet.  I do have a working version of Fiesty via the upgrade path through Edgy from Dapper as you are attempting to do,

Thanks. I think I will try it tomorrow night perhaps and post back here my success or failure.

> **samadams said:**
> I also am looking for more RAM but Dell seems to have disowned the Opti-Plex GX110 on their site so I can't find out the specs.

[http://www.crucial.com/store/listparts.aspx?model=OptiPlex+GX110+Series]("http://www.crucial.com/store/listparts.aspx?model=OptiPlex+GX110+Series")

Crucial is your friend. Even if they don't have the best prices sometimes, the RAM selection tool rocks. :)

---

### Post by nadamsieee on 2007-06-12
I successfully updated to Edgy Eft...

---

### Post by nadamsieee on 2007-06-12
I've updated to Fiesty Fawn, but the 2.6.20-16 kernel seems to hang. The 2.6.17-11 kernel boots just fine, but now I can't use the nvidia blob. So close...

---

### Post by samadams on 2007-06-16
Thanks!  I'll check those guys out!  And I finally did get Fiesty to clean install and it's working great.

Here's my original thread with the solution that worked for me as well as some links to other possibilities.

[http://ubuntuforums.org/showthread.php?t=469580](http://ubuntuforums.org/showthread.php?t=469580)

good luck!

---

### Post by samadams on 2007-06-16
Thanks!  I'll check that out!

---

### Post by Mr_bleu on 2007-06-16
> **samadams said:**
>  I also am looking for more RAM but Dell seems to have disowned the Opti-Plex GX110 on their site so I can't find out the specs.

Have you tried Crucial's website?. [www.crucial.com](www.crucial.com)  
They can tell you what type of Ram you need, if the price isn't what you're looking for you can always google it.  (I like newegg, but I've found other sites can be cheaper for same brands.)

---

### Post by samadams on 2007-06-17
Thanks, but they don't have any for my computer.  I found some on another site though.

---

