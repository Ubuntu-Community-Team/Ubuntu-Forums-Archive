---
title: "how to install and download itunes for ipod nano 3rd generation"
date: 2007-12-23
forum: Wine
---

### Post by famous3warriors on 2007-12-23
I have been looking and reading all the threads on this situation.  I bought my wife the ipod nano 4g i guess it is the 3rd generation and tried to make it work on amarok but for some reason It doesn't download the files correctly.  i am new to ubuntu and i am getting used to doing certain things but downloading and installing software to make things work has proven to be a little difficult.  Is there a solution to this problem?  Thanks for your help.

---

### Post by cogadh on 2007-12-24
iTunes does not work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9692](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9692)

---

### Post by DirtDawg on 2007-12-24
There's a tutorial here where the author claims to have gotten iTunes 7.3 to work:
[http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html)
I haven't tried it, so I can't tell you how well it works.

Otherwise, I know there's a proprietary piece of software that will run a very old version of iTunes(4.x?). I can't remember if it was Cedega or Winetools or something else altogether. It's old, but it will work until there's better support. 

It's too bad Linux has no support for those newest ipods yet. Rockbox doesn't either. 

Good luck. Let us know if it works.

---

### Post by famous3warriors on 2007-12-24
I am going to work on it in the morning thanks for your help and yes I will let you know if it works or not.

---

### Post by DirtDawg on 2007-12-24
Alright, I've spent the last couple hours attempting to get this to run with no success. I'm using Feisty with Wine 0.9.51. 

[COLOR="DarkRed"]### A Few Tips ###[/COLOR]
At one point, the tutorial says to install "richedit30 update" but doesn't provide a link. I found it here:
media.codeweavers.com/pub/crossover/office/support/richedit30.exe

Also, if you are like me and installed Wine a long time ago and have been updating ever since, you will need to remove your ~/.wine folder and run winecfg again. The files from my original install were old and caused a lot of trouble at the start. 

Wine was a little buggy for me trying to change the Libraries (richedit20, richedit32). When I selected them, the 'Add' button was grayed out. Just go back into the menu, select another library(whicheverone), then select the desired one again and for some reason the add button will be usable.

[COLOR="DarkRed"]### The Trouble Starts ###[/COLOR]
Following the tutorial, regardless of the operating system chosen in Wine, I get the following errors:
```
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8d7, disabling mixer
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\QTFont.for","c:\\windows\\QTFont.qfn",(null)): stub
```
I'm not sure what the Alsa mixer error is about, but the Wine sound test seems to work fine, so I don't think that's the problem.

I don't think the second error('htmlhelp') is the problem as the tutorial's author gets the same error on startup, but iTunes still runs for them.

So I think the third error is the issue. It has something to do with the QuickTime font. I have tried moving the font around to different folders, copying the font from my Windows partition, and changing the name of the font to QTFont.ttf.

None of these solutions have worked and I can't find anything of use on the internet. The people at #winehq were no help either.   

Anyone else gotten this to work or have a suggestion about what to try next?

Thanks and
[COLOR="Red"]Merry[/COLOR] [COLOR="SeaGreen"]Christmas![/COLOR]

---

### Post by amorangi on 2007-12-25
I'm not surprised iTunes doesn't work in Wine, it doesn't work in Windows either. What a pile of $#%^@&! How does anyone put up with it?
Off to search some threads on getting it to work in Amarok....

---

### Post by DirtDawg on 2007-12-28
To the OP:

I found another 3rd Generation Nano thread here:
[http://ubuntuforums.org/showthread.php?t=650094](http://ubuntuforums.org/showthread.php?t=650094)

Someone there suggests using the tutorial found here:
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

This is a way to apparently use your 3rd Gen iPod **without iTunes**, so it may not be exactly what you're looking for. Of course I haven't tried it, but the people from the thread that have seem pleased. 

Good Luck.

---

### Post by spegru on 2008-01-02
just tried the serenity link  you referred to
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)
with Nano 3G.

Works AOK!
Except you have to install the 

libgpod-dev_0.5.3+actually0.6.0-0.1_i386.deb
libgpod2_0.5.3+actually0.6.0-0.1_i386.deb

in the opposite order, as the author said later in the thread

Dont bother with wine or itunes!

---

### Post by ispy on 2008-01-03
Just use Amarok, interfaces nicely w/iPods.

---

