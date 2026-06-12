---
title: "Ubuntu Intrepid 64 bit. Flash 10. It's installed, but Firefox says it's not."
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by Roasted on 2008-11-01
Basically what the title says. I'm trying to watch YouTube, but it says I have no flash plugin installed.

I ran sudo apt-get install flashplugin-nonfree, it's already installed. Did a complete removal in synaptic, reinstalled, but still won't work.

How do I fix this?

---

### Post by chaoswings on 2008-11-01
try installing flash this way instead, it will also install java, truetype fonts etc. I believe. Make sure firefox is closed when you do this....
[B]
sudo apt-get install ubuntu-restricted-extras[/B]

---

### Post by krsnendu on 2008-11-01
Flash 10 is installed on my system and I can see Google videos and others, but not Youtube. Youtube just shows a white box. 

Can idea how to fix this?

---

### Post by acm321 on 2008-11-02
> **krsnendu said:**
> Flash 10 is installed on my system and I can see Google videos and others, but not Youtube. Youtube just shows a white box. 

Can idea how to fix this?
First, try refreshing the page a couple times to see if that works.
If not, I think I know what your problem is, but first you need to check something.

Go to your home folder, and make sure you can see hidden files (View>Show hidden files OR alt+.)

Then go to ./mozilla

Is there a folder that's called plugins? If yes, go into it and see if there is a file called libflashplayer.so
If no, go to the firefox folder and check for a plugins folder with libflashplayer.so

If you didn't find a plugins folder with libflashplayer.so, then I know how to fix it.

---

### Post by dagadetman on 2008-11-02
Hey acm321 - you've just described what I see on my system - what's the fix?

---

### Post by Roasted on 2008-11-02
I just had to uninstall flashplugin-nonfree and also remove ubuntu-restricted-extras, then install ubuntu-restricted-extras again.

Works now!

---

### Post by dagadetman on 2008-11-02
Thanks for the suggestions, but unfortunately I'm not quite there yet.  I've done the "uninstall/reinstall" thing but it didn't work for me.  Synaptic shows flashplugin-nonfree and ubuntu-restricted-extras as installed. 

When browsing to one of my daughter's favorite sites ([www.abc.net.au/children](www.abc.net.au/children)) I still get this message:

[FONT="Arial"][INDENT][COLOR="Blue"]FLASH PLAYER DETECTION FAILED.

You don't have the latest Flash Player installed, or else you have Javascript disabled.
Flash Player 9 (or greater) is required to view this site.

You can get the latest Flash Player here.[/COLOR][/INDENT][/FONT]

When I do an "about: plugins" flash doesn't appear.  Also, the "plugins" folder under .mozilla/firefox (as described earlier in this thread) doesn't exist on my system.

I found that "gnash" and "swfdec" seem to play flash movies - but don't seem to allow interaction for flash games.
[B]
My system:[/B]
Freshly installed Intrepid AMD64, Core2 Duo 6420, Nvidia 7900GS, 2GB RAM

Any other suggestions?

---

### Post by Roasted on 2008-11-02
Did you remove flashplugin-nonfree as well as ubuntu-resticted-extras, THEN reinstall ubuntu-restricted-extras? That's what I had to do to get it to work. Remove both, then add the extras.

---

### Post by acm321 on 2008-11-02
> **dagadetman said:**
> Hey acm321 - you've just described what I see on my system - what's the fix?

Sorry for the wait- first you need to download the following file from adobe: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz").

Then you need to make a plugins folder in the .mozilla and and firefox folders. Then extract libflashplayer.so into both plugins folders, restart firefox and it should work fine. (it did for me anyway)

---

### Post by Sef on 2008-11-02
1) > Freshly installed Intrepid AMD64, Core2 Duo 6420, Nvidia 7900GS, 2GB RAM

Any other suggestions? 	

Since you have AMD 64-bit software, did you read [**Adobe Flash install information for AMD64  **]("http://ubuntuforums.org/showthread.php?t=772490")?

2) Moved to 64-bit forums.

---

### Post by pixies7 on 2009-01-31
This did it for me. Thx acm321

---

### Post by Jimro on 2009-01-31
I had to uninstall swfdec before the Adobe flash product would work in Firefox.  Don't know why, but it worked for me.

Jimro

---

### Post by acm321 on 2009-02-01
> **pixies7 said:**
> This did it for me. Thx acm321

You're welcome.

---

### Post by sena-sena on 2009-04-29
I've been having a similar problem (just got a white box where the video should have been or it didn't show at all or crashed firefox).
I tried lots of the "fixes" and none of them worked. 
Until I tried uninstalling swfdec like Jimro and it works fine now. 
Thanks Jimro :D

---

