---
title: "Trouble installing an old game"
date: 2008-06-11
forum: Wine
---

### Post by Jshaw on 2008-06-11
Well, not too old.

Anyway, my sister was wondering whether I could install Harry Potter and the Chamber of Secrets on the Ubuntu PC for her, initially, I told her that it was windows only, and it wasn't compatible, but then I remembered Wine. So I did a little research, and I found a website stating that the people who tested the same game on Wine found no problems at all. So I tried to do it, it installed fine, and it even showed the EA splash screen, but then, nothing. I waited for a loooong time, and finally restarted the computer, because for some reason when I tried to play the game, firefox couldn't play any sound. Can someone help me? Here's the link to the website talking about the game's compatability.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8845&iTestingId=21904]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8845&iTestingId=21904")

---

### Post by Jshaw on 2008-06-11
And just to let you know, I have a very basic version of wine. I can't even get the audio tab to open in the settings window, it just says that I picked a default audio driver for me or something like that.

---

### Post by cogadh on 2008-06-11
There really is no such thing as a "basic" version of Wine, there is just Wine. There are different release versions, but they are all the same application except for release date and code status.

Wine cannot actually choose a sound driver for you. The first time you run winecfg and click on the sound tab, it will tell you that no driver was selected and by default, ALSA will be checked, but you still have to manually apply that change for it to take effect, though if you cannot open the sound tab, I don't see how you could do that. Perhaps you could explain that a little more clearly, especially considering  you seem to have a related sound issue with Firefox when you try to use Wine.

Lastly, please try running the game with Wine from the terminal and post the output here. Wine will output its own error messages to the terminal window, which may help explain what is going on a bit more clearly.

---

### Post by Jshaw on 2008-06-12
> **cogadh said:**
> There really is no such thing as a "basic" version of Wine, there is just Wine. There are different release versions, but they are all the same application except for release date and code status.

Wine cannot actually choose a sound driver for you. The first time you run winecfg and click on the sound tab, it will tell you that no driver was selected and by default, ALSA will be checked, but you still have to manually apply that change for it to take effect, though if you cannot open the sound tab, I don't see how you could do that. Perhaps you could explain that a little more clearly, especially considering  you seem to have a related sound issue with Firefox when you try to use Wine.

Lastly, please try running the game with Wine from the terminal and post the output here. Wine will output its own error messages to the terminal window, which may help explain what is going on a bit more clearly.
What I meant by basic was I just did sudo apt-get install wine. I thought I had to add special addons and what not. I just updated to the latest release candidate, and the audio tab can now be opened. But I tried like you said to open it through the terminal, and no matter what I tried I couldn't get the terminal to go to the folder. I did the cd ~/ thing to try and get to the program files folder, but it says there's no such directory. I'm really needing some help.

---

### Post by cogadh on 2008-06-12
Wine doesn't require any add-ons, it comes ready to use and fully equipped with a (nearly) complete Windows-like API. Wine's "Program Files" directory can be found at /home/<username>/.wine/drive_c/Program Files. To get to it in the terminal, just run this:
```
cd .wine/drive_c/Program\ Files
```

---

### Post by Jshaw on 2008-06-12
> **cogadh said:**
> Wine doesn't require any add-ons, it comes ready to use and fully equipped with a (nearly) complete Windows-like API. Wine's "Program Files" directory can be found at /home/<username>/.wine/drive_c/Program Files. To get to it in the terminal, just run this:
```
cd .wine/drive_c/Program\ Files
```
Ah! I finally got the program to run through the terminal and this is the only thing it spat back at me...

> fixme:process:GetProcessWorkingSetSize (0xffffffff,0x32e838,0x32e834): stub

Any ideas?

---

### Post by cogadh on 2008-06-12
That was the only message you got from it? There really should have been much more. Did you wait until the application had fully launched and failed/hung up or is that just the very first thing it spit out?

If that was the only message you got, that is very unusual, especially since it is not actually an error. The "fixme" messages are just developer notes about incomplete or unimplemented functions in Wine. Every time you run Wine you can expect to see a few of those and you can usually ignore them. You can't actually fix them unless you plan on finishing the coding for the Wine devs.

---

### Post by Jshaw on 2008-06-12
I'll try again and wait longer this time.

---

