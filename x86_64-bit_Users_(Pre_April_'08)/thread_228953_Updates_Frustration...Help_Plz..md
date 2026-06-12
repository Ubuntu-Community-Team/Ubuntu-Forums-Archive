---
title: "Updates Frustration...Help Plz."
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by trogbot on 2006-08-03
OK, here's the skinny of it all.  First I'm fairly new to Linux, but am a seasoned computer OS/system user.  I've wanted to move from Windows for a number of years & finally decided to give Ubuntu Dapper Drake a go after all the glowing reviews.  Installation went without a hitch.  Got dual boot working, etc.  All looking good.  Last thing I needed to move completely off Win was to get locally attached printer visable to my Windows users on home network; they are totally virgins when it comes to computers and did not want any grips.  Tracked down all the guides, man pages, articles, forum threads, etc. and got CUPS/SAMBA running on my box with the printer available to the Win users and LIFE WAS GOOD:grin: All working & all happy.  Then a few days back I noticed an icon on the top bar which said "Updates Available".  Checked that the updates concerned base files, cups, etc. stuff & didn't think twice about applying them.  Big Mistake apparently#-o  I myself don't print much and when I do, everything works fine from my box.  Then yesterday; wife attempts to print from her Win box...nothing prints out.  Go into CUPS and check jobs; it shows her job completed, but nothing on printer.  Got to checking further and discovered her box is sending the job & apparently cups receives it, but nothing prints.  Same on my box now.  Checked through CUPS/SAMBA browser interface & all looks good (or at least it's the same as when I got it all working), but nothing printing.](*,)  Then today I notice more updates along the same line as the ones a few days ago.  Appyied them; but no help; problem still there:confused: To make matters worse; from Win box, my Ubuntu box does'nt even show on the network now, but Windows thinks the printer is still there & ready; thus sending stuff to it.  Can someone give this frustrated newbie a few hints on what may be wrong after all these updates were supplied:(  Any help greatly appreciated.

---

### Post by trogbot on 2006-08-03
Along with any help with the above:  Is there a way to back out the last 2 updates I've made to the OS?  Thanks.

---

### Post by najames on 2006-08-03
I don't think you can "back out" of updates.  I would either (a) try uninstalling the printer under system => administration => printing or (b) try looking to see if your old, working setting files are still there.  Linux updates ususally seem to rename them to .old or  dot.bak or something and write a new file.  Click on Places => home folder and the up arrow a couple times to see the etc directory.

/etc/samba/smb.conf
/etc/cups/cupsd.conf

Perhaps you can either copy the settings from the old ones or try renaming the new ones.

You might have to go to a terminal window under Applications => Acessories and issue a command like one of these

sudo gedit /etc/cups/cupsd.conf
sudo gedit /etc/samba/smb.conf

---

### Post by trogbot on 2006-08-03
I've already deleted and added the printer again after checking the various conf files for cups and samba.  The old ones appear the same as the newer ones; plus they looked the same as the ones I saved after getting everything working.  As far as I can tell, nothing has changed with cups or samba; but why doesn't my box show on the win network now? and what in the updates caused this problem](*,)

---

