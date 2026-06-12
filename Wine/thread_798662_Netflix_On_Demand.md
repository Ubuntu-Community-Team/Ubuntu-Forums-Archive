---
title: "Netflix On Demand"
date: 2008-05-18
forum: Wine
---

### Post by DrTaylor on 2008-05-18
I would love to switch completely to Ubuntu, but there's a few things I need to do first. The biggest is to get Netflix on demand working, which I don't think will be easy. It works fine in Windows, but...

To watch instantly on your computer, you'll need a PC meeting the following minimum requirements:

    * Windows XP with Service Pack 2 or higher, or Windows Vista
    * Internet Explorer version 6 or higher
    * Windows Media Player version 11 (DRM version 5145) or later
    * An active broadband connection to the Internet
    * 1.0 GHz processor
    * 512 MB RAM
    * 3 GB free hard disk drive space

Anybody have any insight here? I can do all of it but the Vista, IE 6, and the WMP, but there's gotta be a way, right?

---

### Post by cogadh on 2008-05-19
The problem is Windows DRM, it relies on operating system functionality that Wine and Linux do not have (proprietary MS stuff). Unless NetFlix removes the DRM requirement, it will never work.

---

### Post by DrTaylor on 2008-05-19
Well, that's encouraging.

---

### Post by erik.osterholm on 2008-05-20
Depending upon your needs, you might use VirtualBox to run a copy of Windows.  You could also buy the Netflix set-top box.

---

### Post by VTshredder on 2008-05-22
This was also a question i had...i thought maybe there was a way around it if i installed IE (which i didn't want to do). Must have windows it seems.
But, small sacrifice.  I can deal with not having Netflix Instant anymore.  Sucks because i was enjoying watching the Munster's reruns when i had my insomniac moments.  The only issue with the new Netflix Roku box is that the library (at this time) is much smaller than the watch instantly currently available online.  SO not really worth forking out $99 yet.

---

### Post by spookyg on 2008-06-15
I just ordered the set-top box and plan to input it via s-video into my pchdtv 5500.  I'll let you know if it works.  They said 1-2 weeks before it even ships, so check back someday.

Spooky

---

### Post by jrusso2 on 2008-06-15
> **DrTaylor said:**
> I would love to switch completely to Ubuntu, but there's a few things I need to do first. The biggest is to get Netflix on demand working, which I don't think will be easy. It works fine in Windows, but...

To watch instantly on your computer, you'll need a PC meeting the following minimum requirements:

    * Windows XP with Service Pack 2 or higher, or Windows Vista
    * Internet Explorer version 6 or higher
    * Windows Media Player version 11 (DRM version 5145) or later
    * An active broadband connection to the Internet
    * 1.0 GHz processor
    * 512 MB RAM
    * 3 GB free hard disk drive space

Anybody have any insight here? I can do all of it but the Vista, IE 6, and the WMP, but there's gotta be a way, right?

Evidently you can do it with Myth TV and a plugin

[http://www.mythtv.org/wiki/index.php/MythFlix_README](http://www.mythtv.org/wiki/index.php/MythFlix_README)

[https://help.ubuntu.com/community/MythTV_Edgy_Plugins](https://help.ubuntu.com/community/MythTV_Edgy_Plugins)

I have also run XP in Virtual Box and watched netflix on that and it works.

---

### Post by cogadh on 2008-06-16
That just allows you to monitor and adjust your NetFlix queue through an RSS feed on MythTV, it doesn't allow you to play the NetFlix On Demand service. Sorry, but there is absolutely no way to run NetFlix On Demand movies without Windows DRM.

---

### Post by braddcadd on 2008-06-25
I just talked with someone at the customer service hotline.  She said they want to support mac and linux.  But they are competitors to mac (itunes & ivideo) so apple won't allow it.  She thinks the story is the same for linux, even though I doubt it.

If they really do want to support linux, we need to get a linux guru talking to NetFlix.  I don't think they realize how the DRM rule handcuffs linux users.

I'd love to watch movies instantly on my laptop, but I'm not willing to go back to window$ to do it.

---

### Post by timcredible on 2008-06-25
i'm in the same boat - it's aggravating that i pay for netflix but don't get all the use out of it.  i contacted them and they basically told me to shove off.  i've tried blockbuster, but it takes them twice as long to get me the dvds and half of them are broken, so until someone comes up with an equivalent service to netflix, i guess i'll keep it.

---

### Post by jrusso2 on 2008-06-25
> **cogadh said:**
> That just allows you to monitor and adjust your NetFlix queue through an RSS feed on MythTV, it doesn't allow you to play the NetFlix On Demand service. Sorry, but there is absolutely no way to run NetFlix On Demand movies without Windows DRM.

MythDVD plays them.  Also the Netflix box runs Linux.

---

### Post by braddcadd on 2008-06-25
Is MythDVD a software app that runs natively on Linux and plays NetFlix on demand movies?

What is Netflix box?

---

### Post by cogadh on 2008-06-26
> **jrusso2 said:**
> MythDVD plays them.  Also the Netflix box runs Linux.
Huh? MythDVD is just an interface for DVD playing/ripping on MythTV, it doesn't have anything to do with online streaming media. 

The Netflix Roku box does not have the same library as the "Watch Instantly" website feature for a reason; the movies it plays do not have DRM attached to them. The Roku box is a closed system, so it does not need Windows DRM like Netflix and the movie studios believe the browser-based streaming service does. The Roku box won't have the same library as "Watch Instantly" does until Netflix can successfully negotiate for more DRM free versions of the films they already offer through the website.

> **braddcadd said:**
> Is MythDVD a software app that runs natively on Linux and plays NetFlix on demand movies?

What is Netflix box?
MythDVD is an interface plugin that is part of [MythTV](http://www.mythtv.org/), a Linux-based media center.
 You can find info on the Netflix box [here](http://www.netflix.com/NetflixReadyDevices?lnkctr=wnph_nfrd&lnkce=nrdwiphpra).

---

### Post by Dewey_Oxberger on 2008-07-10
Anybody using VirtualBox running XP to watch the movies?  Is the video throughput on VirtualBox high enough to work?

As for DRM I really don't see why one of the open source DRM systems couldn't be used.  I don't want to copy the movies, I just want to download them, watch them, and delete them.

---

### Post by MaindotC on 2008-07-15
I run a copy of XP and Vista in VirtualBox and it's very choppy - not worth viewing.  Here's my hardware:

[Abit AV8]("http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=175")
[ATI x850]("http://ati.amd.com/products/radeonx850/index.html")
4 GB of memory
250 Maxtor SATA

I tried amd64-Hardy and everything ran well except Wine, NHL96 in Dosbox, and Netflix in XP and Vista in VirtualBox.  I tried installing the recent ATI driver that was released and followed the directions but it ended in horrific results [here]("http://ubuntuforums.org/showthread.php?t=858900") and [here]("http://ubuntuforums.org/showthread.php?t=828797") for the the third time.  I am now using 32-bit Hardy and everything is working fine except the video is extremely choppy in Netflix.  I have 128MB of video ram dedicated and 2GB regular memory in VirtualBox but it's still no-go.

Right now I just have an old Dell Dimension 8100 that is slow as crap, running XP, and I switch it into my monitor when I wanna watch movies.  I can't believe with my hardware that there's no way to kick up the power.  The x850 is old but it's sure fast enough to handle Netflix.

I read some other posts about VirtualBox and the word on the street is that as of yet there's no way to get really decent graphics in a VM, just enough to view the desktop.

---

### Post by Richie086 on 2009-12-29
> **jrusso2 said:**
> Evidently you can do it with Myth TV and a plugin

[http://www.mythtv.org/wiki/index.php/MythFlix_README](http://www.mythtv.org/wiki/index.php/MythFlix_README)

[https://help.ubuntu.com/community/MythTV_Edgy_Plugins](https://help.ubuntu.com/community/MythTV_Edgy_Plugins)

I have also run XP in Virtual Box and watched netflix on that and it works.


MythTV does not support anything other than viewing your netflix queue with those plugins it looks..

The first link goes to a blank wiki article..
The 2nd link takes you to a page explaining the MythTV plugins and says
[MythFlix]("https://help.ubuntu.com/community/MythFlix") allows you to monitor your Netflix dvd rental queue.

---

