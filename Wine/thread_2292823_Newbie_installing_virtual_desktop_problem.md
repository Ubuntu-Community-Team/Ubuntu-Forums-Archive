---
title: "Newbie installing virtual desktop problem"
date: 2015-08-31
forum: Wine
---

### Post by oatcruncher on 2015-08-31
Hi all,
This is my very first post, so if I do anything wrong please tell me. I went into the Software Center and downloaded Microsoft Windows Compatibility Layer. I then found Configure Wine and WineTricks in my installed apps. On opening the Configure app I was surprised to find not the screenshot that's shown in the Compatibility Layer download page, but just the small mult-tab box. I played around with this and in the process did something really stupid. I created a virtual desktop that was smaller than the Configure box, and am now unable to do anything because I can't get to the bottom of the box to confirm any action!! I'll try and attach a screengrab to illustrate what I mean. I tried uninstalling Compatibility Layer from the Center and then re-installing, but it had retained my stupid configuration.
Any help to get out of this really appreciated. After sorting this problem I'm fairly sure I'll have other questions about Wine, but I'll start a new thread.
Cheers
Max

---

### Post by flaymond on 2015-08-31
Type in terminal -

```
ls -a $HOME
```

then post the output.


If you find .wine directory in your home directory, delete it. Try to launch WINE again, and see if there's any difference.

---

### Post by v3.xx on 2015-08-31
As InterProg stated

Your configuration remained after the reinstall because of the hidden (.config) wine file in your home directory.

To remove the old configuration, open your file manager and press "Ctrl + H" to view your hidden files.

---

### Post by oatcruncher on 2015-08-31
Many thanks to both repliers! I entered the code into terminal and the attached file is what was shown. I also did what V3.xx said and found the hidden file .wine. However, before I delete it I must update you on something I've done since my original post. I've installed PlayOnLinux which appeared to install another (?) version of Wine. I was able to figure out how to use it quite quickly, and having copied an .exe file onto my desktop it installed without fuss - very impressive. I should say that the program was Adobe Audition3 which I honestly didn't expect to run.
Now, if I delete the .wine folder will it upset PlayOnLinux please? I should also add that I've just checked and the problem is still there.
Apologies if I'm being a pain here.
Cheers
Max

---

### Post by v3.xx on 2015-08-31
Playonlinux is a nice gui for wine.  If you delete a config file needed for playonlinux, it should regenerate.  Careful that you do not end up with two installed versions of wine, this will bork things.

[http://wiki.winehq.org/PlayOnLinux](http://wiki.winehq.org/PlayOnLinux)

[https://help.ubuntu.com/community/PlayOnLinux](https://help.ubuntu.com/community/PlayOnLinux)

[URL="https://www.playonlinux.com/en/"]https://www.playonlinux.com/en/


[/URL]

---

### Post by oatcruncher on 2015-08-31
How can I tell if I've got two versions please?

---

### Post by v3.xx on 2015-08-31
> **oatcruncher said:**
> How can I tell if I've got two versions please?

Open a terminal and enter:

```
apt-cache policy wine
```

> Adobe Audition3

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=13421](https://appdb.winehq.org/objectManager.php?sClass=version&iId=13421)

Not looking good :(

---

### Post by oatcruncher on 2015-08-31
Thanks for that link - it looks like it might have saved me a bit of trouble re the update which I'd intended to install!
I attach another dump and am puzzled by the 'none'?
Max

---

### Post by v3.xx on 2015-08-31
Thats odd, reinstall playonlinux.

```
sudo apt-get remove --purge playonlinux && sudo apt-get install playonlinux
```

---

### Post by oatcruncher on 2015-08-31
OK, did that, and this is what I get afterwards:

---

### Post by v3.xx on 2015-08-31
```
sudo apt-get install wine
```

See what happens next :)

---

### Post by oatcruncher on 2015-08-31
OK, well it appears to be there now! BUT, I've lost track, what do I do next?

---

### Post by v3.xx on 2015-08-31
Playonlinux should now be ready to go.

---

### Post by oatcruncher on 2015-08-31
OK, PlayonLinux appears to be as it should, but the wine Configure Wine problem is still there. Should I now try deleting the .wine folder?

---

### Post by v3.xx on 2015-08-31
I thought you already did that.  But yes.

---

### Post by oatcruncher on 2015-08-31
Brilliant, it's sorted!! I can't thank you enough for your help - I really appreciate you taking the time.
All the very best
Max

---

### Post by v3.xx on 2015-08-31
And welcome to the forums :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by flaymond on 2015-09-01
Good job, both of you +1

---

