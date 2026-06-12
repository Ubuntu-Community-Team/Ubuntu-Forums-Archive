---
title: "Kindle for PC with WINE 1.3 (Ubuntu 11.10)"
date: 2011-10-17
forum: Wine
---

### Post by fgimelli on 2011-10-17
Hi all,

I am very much a Ubuntu newbie, so please keep that in mind if you are kind enough to help me out.

I have WINE 1.3 installed in my Ubuntu 11.10. I would like to run the latest (or at least any!) version of the Kindle for PC, but seem unable to do so. At first I managed to install the Kindle for PC Beta with WINE 1.2, but then tried to update to the latest version.

When I began installing Kindle a dialog box popped up telling me that a "serious error" had occurred and the installation could not continue. The dialog box referred me to report the error, but gave me no further details (see screenshot). It seems I could begin to run the application, but once again the same error dialog appeared.

Has anybody been able to install the latest version of Kindle for PC in 11.10? If so, could you kindly provide some assistance to a newbie such as myself?

I look forward to your responses.

Thank you!

---

### Post by ergo-proxy on 2011-10-17
Check here: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10597](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10597)

---

### Post by fgimelli on 2011-10-17
Thanks for the response. As I said I'm a complete newbie, i.e. not much of what that page says makes sense to me.

I did nevertheless rename the directory as specified, but the same error persists.

---

### Post by ergo-proxy on 2011-10-17
What varsion of kindle pc do you have? If kindle to pc was working with wine1.2 why did you upgrade it?:)

---

### Post by Miguelito Grande on 2011-10-17
Yesterday I was unable to get past the error you are receiving running under 11.10. Most versions of wine work fine under Ubuntu 11.04 and the Kindle for PC app was working for me with that system. Upgrading to 11.10 seems to have broken wine. Since I was also having longer boot times and 4 times lomger shut down times with 11.10, I removed 11.10 and did a clean install of 11.04. Kindle For PC works perfectly now. If not for th Kindle issue, I would have probably remained with 11.10 but is was very slow on shutdown for a Linux distro.

---

### Post by fgimelli on 2011-10-18
@Miguelito Grange: Unfortunately I have an Asus Eee PC 1215P and when I install 10.04 I can't get any of the network drivers to work, so I don't think switching back to it is an option for me.

@ergo-proxy: I could only get the Kindle Beta to work, but wanted to use a later version, if possible.

---

### Post by ergo-proxy on 2011-10-19
Try with to use both versions: the lastest stable 1.2.3 and the latest dev (both avaialble in wine repository)

---

### Post by n7cee on 2011-10-21
I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.

---

### Post by Idyll on 2011-10-22
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.


Wow, thanks for this tip.  I did the same and it seems to be working for me as well!  Would never have figured that out!

---

### Post by dnbremner on 2011-10-22
"I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine."

Thanks very much for the above tip which worked for me on Ubuntu 10.10 with Wine 1.3.30 and the latest version of Kindle from Amazon. I've spent three days trying to sort this out!

---

### Post by tlfcbb on 2011-10-22
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.

I have also been trying to get this sorted for some time.  It now works for me in 11.10 with wine 1.3 and the latest kindle app.  Great tip.

---

### Post by anacaona on 2011-10-22
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.

Wow!!! Thanks so much! I've been tripping up on this since 11.04 was released and erasing the manifests was the trick for me.

Thanks again!

---

### Post by Dy1anW on 2011-10-23
Strange. Okay, I'll admit first that I'm on Ubuntu 10.04, but I'm using Wine 1.3.30, and I haven't even been able to install Kindle 1.8.1. Deleting manifests didn't do anything.

---

### Post by gbgustafson on 2011-10-24
> **Dy1anW said:**
> Strange. Okay, I'll admit first that I'm on Ubuntu 10.04, but I'm using Wine 1.3.30, and I haven't even been able to install Kindle 1.8.1. Deleting manifests didn't do anything.
Wine 1.3.30 killed the SUMATRA PDF viewer in ubuntu 10.04. I installed wine 1.3.28 to revert and that fixed the problem. 
Instructions to revert: go to [http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)
and then download the wine 1.3.28 version required for your hardware.
For example, I downloaded the file
[http://wine.budgetdedicated.com/archive/binary/wine1.3_1.3.28-0ubuntu1~ppa1~maverick1_i386.deb](http://wine.budgetdedicated.com/archive/binary/wine1.3_1.3.28-0ubuntu1~ppa1~maverick1_i386.deb)
Then in a terminal window, type this command line:
  sudo dpkg -i XXX.deb
where XXX stands for the file name downloaded. Let ubuntu remove the 1.3.30 version and revert. 
Then uninstall whatever windows program failed, and install it fresh.
The synaptic manager can lock the version of wine, preventing unwanted upgrades.

---

### Post by ecarter on 2011-10-28
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.

Very many thanks - works a treat in 11.10

---

### Post by abraxas666 on 2011-10-28
perhaps a little off topic, but with Chromium it's possible to access the [Kindle Cloud Reader]("https://chrome.google.com/webstore/detail/icdipabjmbhpdkjaihfjoikhjjeneebd")

actually I'm not a Wine fan

---

### Post by shoffm on 2011-11-09
> **abraxas666 said:**
> perhaps a little off topic, but with Chromium it's possible to access the [Kindle Cloud Reader]("https://chrome.google.com/webstore/detail/icdipabjmbhpdkjaihfjoikhjjeneebd")

actually I'm not a Wine fan


The Cloud Reader is awful for navigation and looks terrible. I've been struggling trying to use it for my textbooks.

My Kindle app worked fine until I upgraded to 11.10. I've tried everything, multiple versions of Kindle with both Wine 1.3 and 1.2, deleted the files another user mentioned, toyed with the version of Windows was set to (this worked for me previously). I still can't get Kindle working, and I really need it. Reading my textbooks on my phone is NOT working.

---

### Post by dmflad on 2011-11-21
Running wine 1.3.32 and Kindle for PC 1.8.1. Running Ubuntu 11.10 64bit.

Can register and see my books. Able to do rt-click|download okay on some books but unable to open/read book. Most of the time clicking on any book gives "kindle.exe has encountered serious problem and must close". Screen grays-out and "force close" is only choice. Removing manifest files done and still no-go.

Changing to diff Ubuntu not option, rm wine and using diff version would be ok. Book most need to read off of LT I also have thru OReilly Safari library so I'm just reading thru browser. Would be nice to have Kindle for PC work though for other books in my queue.

---

### Post by jdggra on 2011-11-21
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine  1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make  it executable. The install runs fine, but Kindle for PC crashes on  first run. I deleted the files in  ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs  fine.

Kudos, great advice... Worked great for Oneiric!

---

### Post by hudson36 on 2011-12-11
Hi!

Complete beginner, here. I have the kindle app and WINE installed and noticed people talking about deleting files from here

~/.wine/drive_c/windows/winsxs/manifests/

How do I find this directory? I really need kindle and am seriously struggling here.

Thanks

---

### Post by howefield on 2011-12-11
> **hudson36 said:**
> Hi!

Complete beginner, here. I have the kindle app and WINE installed and noticed people talking about deleting files from here

~/.wine/drive_c/windows/winsxs/manifests/

How do I find this directory? I really need kindle and am seriously struggling here.

Thanks

Open your file manager in your home directory and press Ctrl + H keys to show hidden folders, then navigate to ~/.wine/drive_c/windows/winsxs/manifests/

The period before wine in the above path denotes the folder is hidden.

---

### Post by hudson36 on 2011-12-12
Thank you.

I found the directory, deleted the files but it still does not work.
I hope I do not need to rely on Kindle Cloud forever!

---

### Post by sprintexec on 2011-12-13
> **hudson36 said:**
> Thank you.

I found the directory, deleted the files but it still does not work.
I hope I do not need to rely on Kindle Cloud forever!

@hudson36 I have just upgraded to 11.10 and had been having the problems that everyone has been describing. I had removed and reinstalled kindle before finding this post! 

Like you I navigated to the hidden file where the manifests were held, deleted all of them and then started kindle. It worked fine, first time. 

Don't despair, retrace your steps and I'm sure it will all com good. AJ  :guitar:

I should also say thank you to @howefield and previous post-makers for pointing the way! :)

---

### Post by hudson36 on 2011-12-13
SORTED!!!!!

@Howefield, thanks for the help finding the files.

@ all previous posters, thanks for the information and tips.

I have no idea why but yesterday I tried this probably 30 times nothing worked at all. Today, I thought I'd give it one more shot and it worked first time!

Thanks all. One happy Kindle bunny!

---

### Post by Ishipaco on 2011-12-22
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.

Excellent! After an entire day trying to get the newest Kindle for PC download to run without the "serious error" msg, I found your fix. I had tried all kinds of tricks, installs/uninstalls, google searches, etc. When I simply changed the name of the Manifest folder to something different (instead of deleting it!) after the install, as you mentioned...bingo! It all worked. Thanks so much. BTW, the latest version of Kindle for PC looks much cooler than the one I've been using for quite awhile. Also note: I'm still using Ubuntu 10.10.

---

### Post by rjf1 on 2011-12-25
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.

This did it for me, too -- just wanted to say a big THANK YOU!

---

### Post by pracrichard on 2011-12-26
Originally Posted by **n7cee**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11376337#post11376337")                 
                 *I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine. *

Many thanks n7cee can I join your fan club?

Since my Kindle died two months ago after a wine upgrade I have been watching wine bugs and seeing them bemoan the problem with no solution except that it was on the fix list. 

I finally did what I should have done before and visited this forum.

Now I can finish reading the book I started in october.

Once again many thanks.

Richard

---

### Post by yyl on 2011-12-30
Thanks **n7cee**,  solved the issue for me

---

### Post by Flanmaster on 2011-12-30
@gbgustafson If you are still following this thread, did you reboot after the reversion and before uninstalling the windows program (kindle). and exactly how did you uninstall the windows program?  Did you revert to gnome classic and then try to find the windows uninstaller or did you find the kindle uninstaller through unity some how?  I've just upgraded and am having the same problems.  I have run the appropriate deb file and am now ready to try to uninstall the windows program.  Thanks for any suggestions.  > **gbgustafson said:**
> Wine 1.3.30 killed the SUMATRA PDF viewer in ubuntu 10.04. I installed wine 1.3.28 to revert and that fixed the problem. 
Instructions to revert: go to [http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)
and then download the wine 1.3.28 version required for your hardware.
For example, I downloaded the file
[http://wine.budgetdedicated.com/archive/binary/wine1.3_1.3.28-0ubuntu1~ppa1~maverick1_i386.deb](http://wine.budgetdedicated.com/archive/binary/wine1.3_1.3.28-0ubuntu1~ppa1~maverick1_i386.deb)
Then in a terminal window, type this command line:
  sudo dpkg -i XXX.deb
where XXX stands for the file name downloaded. Let ubuntu remove the 1.3.30 version and revert. 
Then uninstall whatever windows program failed, and install it fresh.
The synaptic manager can lock the version of wine, preventing unwanted upgrades.

---

### Post by Flanmaster on 2011-12-30
an update on my efforts.  after running the deb file I rebooted, chose gnome classic on log in.  uninstalled kindle using the kindle uninstaller.  reinstalled kindle. It did not run.  deleted the contents of the manifest file. it did not run.  It shows the initialize on the bar but then just disappears.  So I checked the version of kindle and it is 1.8.3.  I could not find a download of 1.8.1 but I still have an installer from 1.6.3 so I uninstalled kindle. installed from the older installer that I have. it did not work.  checked the manifest file. still empty.  Uninstalled again, ran install from command prompt and got a bunch of "fixme" errors.  ran kindle.exe from command prompt (all through wine) and got windows common control error.  If any one has any suggestions I would appreciate it.  I have ubuntu 11.10 and have tried reverting to the older version of wine according to the posted instructions all with no luck.  I am considering trying to download a much older version of wine to see if this works.    I had this same problem in ubuntu 11.04 using wine 1.2 so it's not specific to just the latest versions of wine.  I am using an asus n53sv intel core i7.  Thank you again

---

### Post by pracrichard on 2012-01-06
I have ubuntu 11.04 

I ran the auto update today as it was offered and Firefox was having trouble. During the update Wine also updated itself and reinstalled all the files I had deleted last time. Kindle of course broke again. Renaming the folder 'manifests' cured the problem. 

I am now curious as to what the files in this folder do and what part of Wine will be upset by deleting them. I don't currently run any other Windows software but would quite like I tunes to view some lectures a friend told me about. Can I get away with just deleting one file?

Any ideas?

Regards

Richard:)

---

### Post by apswartz on 2012-01-20
Yes, same issues here. Simply deleting that manifest directory didn't work for me. I also had to downgrade Wine AND delete the manifest directory to get the program to run.

Don't you hate feature regressions! :o

---

### Post by cmcanulty on 2012-01-21
Wow I have been working on this with no luck. Can you explain how you figured fix out so we all can learn. Can you explain how to get a shortcut to it in menu. With the new wine none of my wine programs show in menu and I can't find them in bin, sbin, etc.Thanks

---

### Post by apswartz on 2012-01-21
> **cmcanulty said:**
> Wow I have been working on this with no luck. Can you explain how you figured fix out so we all can learn. Can you explain how to get a shortcut to it in menu. With the new wine none of my wine programs show in menu and I can't find them in bin, sbin, etc.Thanks

Yes. I downloaded this file...
```
wget http://wine.budgetdedicated.com/archive/binary/wine1.3_1.3.28-0ubuntu1~ppa1~maverick1_i386.deb
```

Then install the package...
```
sudo dpkg -i wine1.3_1.3.28-0ubuntu1~ppa1~maverick1_i386.deb
```

Then, I deleted the manifest directory contents...
```
rm ~/.wine/drive_c/windows/winsxs/manifests/*
```

Finally, I reinstalled the Kindle Reader...
```
wine KindleForPC-installer.exe
```

That did it for me.

---

### Post by apswartz on 2012-01-26
Aaaaarrrrrgh!!!

After yesterday's updates, my Kindle installation is broken again!

---

### Post by n4pgw on 2012-02-02
**[[SIZE=1]Getting Amazon Kindle for PC running in Ubuntu under Wine[/SIZE]]("http://www.redshirtlinux.com/?p=163")**

I found the article above to work for me, first time.  I followed the instructions and it worked first time. 



I hope this helps some of you.


Buck

---

### Post by Flanmaster on 2012-02-03
> **n4pgw said:**
> **[[SIZE=1]Getting Amazon Kindle for PC running in Ubuntu under Wine[/SIZE]]("http://www.redshirtlinux.com/?p=163")**

I found the article above to work for me, first time.  I followed the instructions and it worked first time. 


Problem loading page.  so I went to the main website, problem loading page.  :(

---

### Post by orionds on 2012-02-18
> **Miguelito Grande said:**
> Yesterday I was unable to get past the error you are receiving running under 11.10. Most versions of wine work fine under Ubuntu 11.04 and the Kindle for PC app was working for me with that system. Upgrading to 11.10 seems to have broken wine. Since I was also having longer boot times and 4 times lomger shut down times with 11.10, I removed 11.10 and did a clean install of 11.04. Kindle For PC works perfectly now. If not for th Kindle issue, I would have probably remained with 11.10 but is was very slow on shutdown for a Linux distro.

I hope you get to see this. To restore quick shutdown in 11.10, open the Software Center or Synaptic Manager. Search for "wicd" (without the quotes). install it and then search for "network-manager" and uninstall it. Reboot, wicd should take over from network-manager and shutdown will be restored to 3 or 4 seconds.

Network-manager refuses to close politely and Ubuntu waits for about 15 seconds before killing it. In 12.04 alpha (at this point in time), this bug is still there.

---

### Post by Flanmaster on 2012-03-14
I found this SIMPLE STABLE solution browsing the winehq page for kindle

Install (via wine) The Microsoft Visual C++ 2008 SP1 Redistributable Package (x86)

worked for me when all the "jerry rig" solutions I found here did not work

info and download link:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15314&iTestingId=36217](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15314&iTestingId=36217)

THis solution should hold good even after updates :P

I had already installed kindle with the crashing issues.  I downloaded the redist pack via the link from the above wine page, clicked on it and selected the wine option for opening. it installed, I tried kindle, worked perfect.

---

### Post by scottro on 2012-04-24
Much later, (April 2012), on Fedora 17, I had the same issue and the solution in post 11 worked for me. Delete all files in ~/wine/drive_c/windows/winsxs and then Kindle installed and worked for me.  Many thanks.

---

### Post by fjmwheel on 2012-05-05
Hi all,

Just wanted to say thank you as this thread solved my problems with Kindle on Ubuntu 11.10.

---

### Post by bejinx on 2013-01-04
> **n7cee said:**
> I have Kindle for PC 1.8.1 working with Wine 1.3.28 on Kubuntu 11.10. After downloading Kindle for PC installer, make it executable. The install runs fine, but Kindle for PC crashes on first run. I deleted the files in ~/.wine/drive_c/windows/winsxs/manifests/, and now Kindle PC runs fine.

^^ this worked for me, thank you. (linux mint 11 + wine 1.3 + kindle for pc downloaded 1/4/2013)

---

### Post by nickww4 on 2013-02-13
> **Flanmaster said:**
> I found this SIMPLE STABLE solution browsing the winehq page for kindle

Install (via wine) The Microsoft Visual C++ 2008 SP1 Redistributable Package (x86)

worked for me when all the "jerry rig" solutions I found here did not work

info and download link:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15314&iTestingId=36217](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15314&iTestingId=36217)

THis solution should hold good even after updates :P

I had already installed kindle with the crashing issues.  I downloaded the redist pack via the link from the above wine page, clicked on it and selected the wine option for opening. it installed, I tried kindle, worked perfect.
Thanks mate, this worked for me with Wine 1.4. Just come back to Linux with my new netbook, nice to see the community still giving great help and advice!

---

### Post by ageofsteam on 2013-04-02
> **Flanmaster said:**
> I found this SIMPLE STABLE solution browsing the winehq page for kindle

Install (via wine) The Microsoft Visual C++ 2008 SP1 Redistributable Package (x86)

worked for me when all the "jerry rig" solutions I found here did not work

info and download link:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15314&iTestingId=36217](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15314&iTestingId=36217)

THis solution should hold good even after updates :P

I had already installed kindle with the crashing issues.  I downloaded the redist pack via the link from the above wine page, clicked on it and selected the wine option for opening. it installed, I tried kindle, worked perfect.

Seconding this solution.  It worked for me, too- on WINE 1.4 & Kindle vers 1.10.5.  I've been trying to fix this problem for WEEKS, and this is the only thing that worked!!  Thank you!  I never would have thought of it without your post. :)

---

