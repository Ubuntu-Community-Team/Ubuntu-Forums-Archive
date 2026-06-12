---
title: "Finale 2006 in WINE; installed but not running."
date: 2008-08-18
forum: Wine
---

### Post by NeilWards on 2008-08-18
I am running Hardy Heron and have successfully installed WINE, and though I have installed Finale 2006 in WINE, I can not use it. WINE recognizes that Finale is there, but I can not get it to run. When I try to run it, I get a tab in the bottom panel that says: Starting Finale 2006... then nothing.
I have been reading several related posts, but can not seem to solve this problem. I don't know how to proceed from here.
Any help would be greatly appreciated.
Thank you.

---

### Post by Oldsoldier2003 on 2008-08-18
one of the best places to start is the Wine Application Database.

[http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by Oldsoldier2003 on 2008-08-18
moved to Wine forum.

---

### Post by NeilWards on 2008-08-18
Running it in terminal gives me this:
 not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Finale 2006\\FINALE.EXE" failed, status c0000135
I have read the WINE AppDB, and it reports it as working, therefore I have not found a solution for my problem there.
I have also tried to work through the related how-to's but to no avail.
Thanks for responding.

---

### Post by merlyn on 2008-08-18
> **NeilWards said:**
> Running it in terminal gives me this:
 not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Finale 2006\\FINALE.EXE" failed, status c0000135
I have read the WINE AppDB, and it reports it as working, therefore I have not found a solution for my problem there.
I have also tried to work through the related how-to's but to no avail.
Thanks for responding.

I could be barking up the wrong tree here, however it's possible that, one, (or more) of the requirements for Finale is not being met.

Wine, "out of the box", does not include a "full" compliment of .dll files.

Usually, if a particular .dll file is required by an application, running the application via the command line will 'mention' the file by name.

In which case you simply copy the .dll file(s) from an existing Windows install, or download them from the net and paste them into the appropriate folders, typically .../Windows/System or .../Windows/System32.

I ran into a similar problem recently after installing an application under wine, and having it crash on me. The Wine app db indicated the program should run, (gold status), but the reviews failed to mention that a particular .dll needed to be installed first.

Also does Finale render documents, with XML or some such?

If so you could try installing the Wine Gecko engine, if you haven't already done so.

The instructions for this can be found in codagh's excellent "Stuff I've learned about Wine" post. Which can be found [here]("http://ubuntuforums.org/showthread.php?t=497332").

It would be a good idea to install the Gecko engine regardless.

As I mentioned at the beginning I might be barking up the wrong tree. Perhaps there is additional information provided in the error message?

If so could you please provide the error message in full.

Cheers.

---

### Post by NeilWards on 2008-08-19
I think you are, in fact, barking up the right tree.
Here is why (the error report):

err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Finale 2006\\FINALE.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Finale 2006\\FINALE.EXE" failed, status c0000135

I didn't realize that I hadn't cut/pasted the entire error message.

I will investigate this further. If it is a dead-end, then at least you gave me something to try. I will see if I have the missing .dll file in my old Windows backup of the hard drive that Finale was on (as I am currently not running a dual-boot system). Thanks also for the links.
Much obliged.:)

---

### Post by merlyn on 2008-08-19
> **NeilWards said:**
> I think you are, in fact, barking up the right tree.
Here is why (the error report):

err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Finale 2006\\FINALE.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Finale 2006\\FINALE.EXE" failed, status c0000135

I didn't realize that I hadn't cut/pasted the entire error message.

I will investigate this further. If it is a dead-end, then at least you gave me something to try. I will see if I have the missing .dll file in my old Windows backup of the hard drive that Finale was on (as I am currently not running a dual-boot system). Thanks also for the links.
Much obliged.:)

If you are unable to obtain a copy of msvcp60.dll from your old Windows back up drive you'll be able to obtain a copy from [www.dll-files.com]("http://www.dll-files.com").

Here is a direct link to download msvcp60.dll itself.

[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)

I'm not sure if you'll find these links of use or not but I did a quick search earlier on and found the following,

[Editing music scores with free software]("http://www.linux.com/feature/118302"), and 

[MuseScore: Music Scorewriter]("http://mscore.sourceforge.net/en/idx.php").

Cheers.

---

### Post by NeilWards on 2008-08-19
Thank You very much Merlyn!
I am now running Finale 2006 in Ubuntu (we'll see how well). Your help was clear and easy to implement.
As to the free native Linux music editing software, I have already been experimenting with them, and hope to become skilled enough in Lily pond to replace Finale outright.
Until then... I now can use Finale without Windows! :)

---

### Post by merlyn on 2008-08-19
> **NeilWards said:**
> Thank You very much Merlyn!
I am now running Finale 2006 in Ubuntu (we'll see how well). Your help was clear and easy to implement.
As to the free native Linux music editing software, I have already been experimenting with them, and hope to become skilled enough in Lily pond to replace Finale outright.
Until then... I now can use Finale without Windows! :)

You're welcome mate.

---

### Post by BaffledMusician on 2008-12-27
Just found this thread, which is very helpful.

I downloaded Wine yesterday and I'm trying to use it to run PrintMusic (cheapo version of Finale) on an Acer Aspire One.  

I used the tips on .dll files to supply the ones that were missing.  So far so good.

From Terminal, I now get the following error message when I try to run PrintMusic:

"[user@localhost drive_c]$ wine printmusic.exe

ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0

ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0"


Any ideas what I need to do next?  (I know I'm running Linpus Lite, not Ubuntu but this thread is the only one I've found which gives good, clear advice on using Wine with Finale-family software!)  NB I'm very new to Linux and easily confused by techno-speak!!

---

### Post by NeilWards on 2008-12-27
I don't have the answer to your specific problem, but you might find that it is not worth the effort.
I also have an Acer Aspire One. If your luck with Finale (or print music) under WINE is anything like mine, I think you'll find that the strain on system resources renders it almost unusable. I have run Finale 2006 under WINE on my hotrod desktop with 6 times the ram of an AAO and found it so aggrivating that I re-installed a Windows XP partition on my hard drive.
I would recomend that you try NtEd or MuseScore (if you can find the .RPMs and resolve the dependencies).
Good Luck.

---

### Post by BaffledMusician on 2008-12-30
> **NeilWards said:**
> I don't have the answer to your specific problem, but you might find that it is not worth the effort.
I also have an Acer Aspire One. If your luck with Finale (or print music) under WINE is anything like mine, I think you'll find that the strain on system resources renders it almost unusable. I have run Finale 2006 under WINE on my hotrod desktop with 6 times the ram of an AAO and found it so aggrivating that I re-installed a Windows XP partition on my hard drive.
I would recomend that you try NtEd or MuseScore (if you can find the .RPMs and resolve the dependencies).
Good Luck.

Thanks!  I have actually got PrintMusi running, now, having copied over the missing .dll files.  Only problem is, midi doesn't seem to work, so I can't play back my files (or play midi files at all, in fact).  I've Googled, and it looks like this might be an issue with Fedora/Linpus Linux, rather than specific to PrintMusic or Wine.

Any ideas??

---

