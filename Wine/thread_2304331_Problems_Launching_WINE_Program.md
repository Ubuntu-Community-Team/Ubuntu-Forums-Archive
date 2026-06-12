---
title: "Problems Launching WINE Program"
date: 2015-11-26
forum: Wine
---

### Post by shock2 on 2015-11-26
Hey everyone, first time poster here. I've got what is probably a very simple issue that I hope someone could help me with.
  I'm trying to launch Blade And Soul, the new NA version. Problem is  that if you try to launch it directly from client.exe, it'll tell you to  launch it from the launcher. If you try to just launch from the  launcher, it gives you an error code.
  After a little research, I found out that the error code could be  eliminated by adding the proper commands in with the launcher as  required in Windows throughout all regions, including Japan and Taiwan's  clients.
  I was hoping that someone could tell me in the most simplistic way  possible how I could add this launcher option into PlayOnLinux or WINE so that  it launches as it would within Windows.

This is the way the link looks in Windows. "C:\Program Files (x86)\NCWest\NCLauncher\NCLauncher.exe" /LauncherID:"NCWest" /CompanyID:"12" /GameID:"BnS_CBT" /LUpdateAddr:"[updater.nclauncher.ncsoft.com]("http://updater.nclauncher.ncsoft.com/")"

I need it to try to launch with those parameters within WINE or PlayOnLinux either one. If anyone could help me out with this, I would greatly appreciate it as I'm fairly new to Ubuntu and want to get some of my basic games and programs good to go before I begin diving further into the unknown. Thank anyone willing to help.

---

### Post by Bucky Ball on 2015-11-26
*Thread moved to **Wine**.*

---

### Post by mastablasta on 2015-11-26
you can create a shortcut (launcher) and add the additional command there.

wine database shows two servers tested and looks like one is rated platinum the other one bronze (which is quite bad): [https://appdb.winehq.org/objectManager.php?sClass=application&iId=13926](https://appdb.winehq.org/objectManager.php?sClass=application&iId=13926)

if oyu plan to use more windows programs then it is better to stay on windows rather that struggling with Linux to make them work. you can always dualboot or run Linux in virtualbox.

---

### Post by shock2 on 2015-11-26
I know it's easier to stick with Windows but I'm determined to make the switch. I like everything about it so far, including the community. If you could just explain to me how to create that shortcut with those actual commands in there, I would really appreciate it. Tell me as if I were a child you were trying to explain it to.

Another thing I noticed was that in those tests, someone said that you an alternative way to get it working was to add a command like /LaunchByLauncher or something of the sort. Where would I add that command if I went that route instead?

---

### Post by sweldon001 on 2016-01-04
just read this section ok .. [Wine Ubuntu Documentation ]("https://help.ubuntu.com/community/Wine")otherwise you right click on launch pad /desk top menu pop-up then select create desktop luancher / luancher then add as follows :
wine "c:\Program Files\NCsoft\BladeandSoul\Client.exe"
this sould basically create a launcher on your launch pad to run it  it pretty much is command to be run statement i  launcher creation to run file from win virtual c: \ location of Client.exe file.

---

