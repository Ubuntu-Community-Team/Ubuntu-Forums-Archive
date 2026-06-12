---
title: "City of Heroes - working great with Wine 0.9.54"
date: 2008-02-09
forum: Wine
---

### Post by deruberhanyok on 2008-02-09
I saw some old posts about CoH/CoV on Wine but nothing recent, so I figured I'd post this here in case it helps anyone.

The latest version of Wine as of this post is 0.9.55; I haven't installed it yet because it hasn't appeard as an update for me (I just use the package manager configured as per the instructions on WineHQ, I don't do any manual compile/installs).

System setup is Ubuntu Gutsy 64-bit (yes, 64-bit), the nvidia drivers from the repository (also verified working with the ones from nvidia's website), Wine 0.9.54 and Compiz is enabled. I have an ntfs partition that my games are installed on through Windows; that is just mounted at boot so I can access the game files.

I first tried running CoH directly by clicking on the "CityOfHeroes.exe" file in the game's install folder. This gives an error saying it needs to run through the updater, not directly, and the updater wouldn't run at first, giving an error about permissions.

So I ran the Wine config app (under the applications/wine menu if you've installed from their repository) and set up a few things:

Windows Version: XP
Drives:
    C (left alone at "../drive_c")
    D (my DVD drive, "/media/cdrom/", this was not needed for CoH/CoV but I put it there anyways)
    F (set for "/media/sdb1/", which is where that ntfs partition is mounted by Ubuntu)

No other settings were changed.

With this done I was able to run the updater. First I had to download the gecko rendering engine for Wine, this is an automatic process and I guess I hadn't done it on this system yet. When the updater asked where I wanted to install CoH I simply pointed it to "F:" and ran the program. It saw that I already had the game installed, verified the files in a minute or so, and then created a shortcut on my desktop (which Wine handily turned into a link that Ubuntu understood).

Now I can just run the game from that shortcut or click on the updater directly and it works fine. It looked as though, had I not set up the drives in Wine but gotten the updater to work, it would get confused and have to verify the install each time.

Anyways, my experience thus far has been great. I've noticed a couple things:

1.) even with the latest drivers from nvidia's website, the login screen will still say you are running outdated drivers. Ignore this; I think it's checking against a database and looking for a version number from the windows forceware drivers.

2.) On first run the game tried to run in 1024x768 but was forced into 1920x1200 (my desktop resolution) automatically.

3.) Once logged in, if you try changing the graphical settings from 'recommended' to 'quality' your screen may go completely white except for the game menus. This is due, I've found, to the anti-aliasing setting. If you want to turn up lots of details you'll have to enable the advanced settings menu and change the settings manually. I have not gotten anti-aliasing to work.

[edit]*update for 0.9.57* - Anti-Aliasing now works for me with this release.

4.) Highest shader quality I could select was "low (with world bumpmaps)". Water Effects, Depth of Field Effects, Bloom Effects, Bloom Amount and Desaturation Effects can not be selected. I don't know why this is unless something is lost in the translation between nvidia's windows and linux OpenGL drivers.

5.) You may experience a slight pause when talking to a contact before their text displays.

6.) If I type in a text box it seems to miss the first letter I type.

7.) cursor is distorted

8.) contact list loads slowly

[edit]*update for 0.9.57* - huge speedup with this.

Anyways, all things considered, they are pretty minor issues. The game runs well and was very easy to configure. Having it render without any problems even while using scale or the task switcher in compiz is pretty neat, too.

Hope this post is useful.

---

### Post by deruberhanyok on 2008-02-12
Well, this is weird. As of the patch released today, I now get a crash whenever I bring up the screen to switch costumes (this also happens in the ICON shop to edit costumes), although the using the command line to switch them works fine.

When 0.9.55 hits the repository I guess I'll try it again. Game still playable, at least.

---

### Post by theShaggy on 2008-02-12
That's not a new bug - the costume change crash has been around since the 9.40s, when the game became playable.

---

### Post by graabein on 2008-02-25
Anyone tried COH with the latest version 0.9.56 of Wine?

List of bugs and comments: [http://appdb.winehq.org]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980")

---

### Post by deruberhanyok on 2008-03-03
So I realize this post is a couple of weeks old but I wanted to post again quickly.

Thanks for the info shaggy. I wasn't aware of that; actually didn't even bother to check the appdb at Wine HQ since I got it working pretty much right away. It's likely I just hadn't brought up the costume change screen under Linux yet... I only have one character with multiple costumes, I'm still a newbie to CoH. :)

graabein- haven't tried with 0.9.56 yet; repository is still at 0.9.55 for me. Although I'm running 64-bit, so maybe the 32-bit one has been updated with it already.

Discounting the costume change thing (which I now know isn't a new problem), it seems to run the same on 0.9.55 as it did on 0.9.54.

I also, for the heck of it, tried disabling compiz to see if that would get the anti-aliasing to work, or to get some of those extra effects to show up in the graphics menu. It had no effect.

I'll check into the appdb and see if I have anything to add to it, but I figured some Ubuntu users might head straight for this forum.

---

### Post by theShaggy on 2008-03-03
Not a problem.  The way I got it working was to run to the CohUpdater.exe in Wine's "c_drive" directory, let it create a folder, and then symlink that folder to the older installation on my old NTFS drive.  Now, when I run it (or Cedega; I have it set up on both), I just tell it to read that directory with the symlink, and it works fine.

For some reason, it doesn't want to run the updater off of the NTFS drive, though.  Some weird permissions problem.

Anyway, I'm still waiting on 9.56 myself.  Nothing much has changed since the game really got working back in the 40s, but they're saying a bunch of graphics bugs are being fixed for .56 - I can only hope we get that costume change thing fixed.  That at the chat bug are the main problems facing it right now (because outside of a few little things like my contacts having to show up one at a time - being at level 35 that takes me upwards of 10 minutes, making the game unusuable - the game looks SO much better than on Cedega), and once they're gone it'll be kick ***.

Anyway, I'm running 64-bit, too.  Waiting on the repos, which are now 10 days late for the second release in a row.  I get that people are doing this on their own time, but we're getting releases one back for no real reason.

Hey, what server are you on?  I kick around Pinnacle most of the time.

---

### Post by deruberhanyok on 2008-03-09
I'm on Champion mostly. I have a villain on Freedom but I haven't played there in months.

Incidentally I just tried out some things with the latest nvidia drivers and Wine 0.9.57. I can now enable 2x/4x FSAA without any problems. Maybe this is a result of the 'opengl pixel formats' they added in the latest version.

The other issues are still present, but that's good progress in my book. Really nice to have this game work so well with so little effort required on the end-user side.

---

### Post by theShaggy on 2008-03-10
That is good progress, however I'm finding the past few releases to actually seem a bit buggier - my computer is crashing far more that before.

These new OpenGL Pixel formats now also fixes my contacts problem - they still load slowly, but about 50x faster than before (I now wait 30 seconds for all my contacts at lvl 35 to load, not 10 minutes).  The costume problem still exists, as does the chat bug and this issue with mouse-grabs... with a TV-Out screen, my pointer will still switch to it when mouse-looking, and that causes me issues.

Still, getting better.

---

### Post by graabein on 2008-03-17
It's like the Beatles song from Sgt. Pepper, keeps on getting better all the time. I can hardly wait for the day we can play COH bug free on GNU/Linux. Couple that with a tv-out/xorg.conf editor that works 100% and it's a bye bye Microsoft!!


As it is now I have to log out to get tv-out and if I put the television set as screen1 on the left of the monitor then it messes up both menu panels, desktop icons, awn, compiz, you name it... But I'm patient. Ubuntu's come a long way since Hoary, when I first got into GNU/Linux.

---

### Post by sookster54 on 2008-03-19
I've been playing CoH/V on Wine 0.9.57 for a while now, it runs as if I'm playing the game in Windows and I don't seem to be missing any video setting options.  I haven't had any performance hits yet.

I've been a long time Linux user but have been absent from it for a few years and I see now that it has come a long ways and will soon be very capable of running nearly any game out there.  I picked up Frontlines FOW the other day and hope someday that'll be playable but it isn't right now.

---

### Post by deruberhanyok on 2008-03-21
sookster - that's interesting. I wonder if the missing video settings on my menu are due to something different in the nvidia driver for my 7950GT compared to your 8800GT (assuming that was the system you were talking about, I mean).

Have you run it on both of the systems in your sig?

I saw that animated cursors was something they wanted to have working by the 1.0 release, that might fix the weird cursor graphic in-game.

And graabein, there's a new display config menu in Ubuntu 8.04, I think, that might work better for multiple displays. Dunno if that will help your TV out issue though. I've been meaning to try out multi monitor support in 7.10 but I'm too lazy to dig a spare monitor out of my closet and hook it up. Heh.

---

### Post by graabein on 2008-04-22
I upgraded to Wine 0.9.59 yesterday. It seems most bugs are still there, except bringing up the contact list is really fast now.

There's still issues with entering and leaving chat window and I suppose the costume screen still crashes the game. I didn't try it. 

Another thing I noticed is the right and middle clicking of mouse button was really slow when I wanted to rotate the camera and my toon. Not all the time, but some times. This might have something to do with Compiz Fusion, which works perfect for me on Ubuntu 7.10 and a GeForce 6600GT.

I sure hope they get rid off these bugs soon!! 

[-o<

Off topic: 
About the dual monitors I just want one desktop monitor (screen0) and a separate xscreen on my telly (screen1) to show fullscreen video.

---

### Post by graabein on 2008-06-15
Hey by the way one can vote for bugs on Wine. Just register your e-mail address on the [Wine Bugzilla]("http://bugs.winehq.org/") look up the [City of Heroes bugs]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980"), click them and vote.

---

