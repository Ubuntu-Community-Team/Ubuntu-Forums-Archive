---
title: "[SOLVED] Configure and Apps Display Too Large"
date: 2008-05-28
forum: Wine
---

### Post by Stoppelmonster on 2008-05-28
I am n00b at Ubuntu and Linux all together. I am trying Ubuntu out because i am tired of Microsoft. I want to make the full switch but one prog i want to use isn't functioning properly.

I jsut installed Wine and my main concern is not being able to get rid of my over sized windows opened through wine, like the Wine Configure and Buzzmachines.
 Here's a [screen shot]("http://www.blanktheartist.com/8sf6eheD99je6hd7/Screenshot.png"). 

As soon as I am able to get the Wine Configure to open properly, then I could get Buzzmachines to work, or so I have [read]("http://flavor8.com/index.php/2005/10/15/buzz-tracker-on-linux/"), then I'd be a happy camper. and maybe then work on getting WOW, hehe. but Wine and Buzz first.

Buzzmachines seems to work properly as far as opening and closing, switching from table to table, etc;..., even in it's distorted appearance.

Anyhow, someone help me out, convert me. Tell this nub how to make his Wine Configure Window fit to screen.

---

### Post by schtufbox on 2008-05-28
In your /home/YOURUSERNAMEHERE/.wine folder (which is a hidden folder) you need to open system.reg file in a text editor like gedit ( MAKE SURE YOU MAKE A COPY OF THE FILE FIRST JUST IN CASE ) you can also open it directly by typing 
```
 gedit /home/YOURUSERNAMEHERE/.wine/system.reg [CODE]

Obviously, change YOURUSERNAMEHERE to your actual user name :)

Find the part below either by a search within the text editor or scrolling til you find it :
[CODE]
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]

```

under that there should be a "LogPixels"  entry, edit it so it is the same as below:

```

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]
"LogPixels"=dword:00000060

```

You want to make sure that the log pixels entry is as above, this will reset wine to use 96dpi for fonts.
Then save and run winecfg to check it worked.

The "00000060" is actualy in hex - 0x60 = 96

---

### Post by Stoppelmonster on 2008-05-28
Awesome! It worky! That was a lot easier than i thought. Much thanks, schtufbox. Can you tell me of any image editing programs similar to Adobe Photoshop?

---

### Post by schtufbox on 2008-05-28
No problem, cogadh and I seem to be the ones that answer your problem the most I have noticed :D
As for image editing, the only one's I have used in Linux are the Gimp, and Photoshop (under WINE)
Thinking of compiling the new version of Gimp later, has some nice updates.

---

### Post by Stoppelmonster on 2008-07-03
So, I tried Gimp and did some research, I recently installed the Gimp Shop expansion or shell, I am not sure which one to call it, but, Gimp stopped working. So, I's thinking I should uninstall it, and start over.

---

### Post by Chazzymagill on 2008-07-19
Hey guys, iv got the same problem, and i followed the advice above but everytime i run wine config again the file just resets itself to "LogPixels"=dword:000001e0

any ideas?

Thanks

---

### Post by Stoppelmonster on 2008-07-24
I had the same problem, so i jsut deleted the copy, and edited the original and saved it. Skipping the copying of the file completely. (^_^) This is unsafe, if you do not trust your self to do such things, don;t do it.> i followed the advice above but everytime i run wine config again the file just resets itself to "LogPixels"=dword:000001e0


---

