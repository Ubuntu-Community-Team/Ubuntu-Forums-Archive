---
title: "Powerpoint insert video error"
date: 2013-01-21
forum: Wine
---

### Post by breeky5 on 2013-01-21
Hi everyone,

    I have a problem inserting videos in powerpoint 2010 running on wine 1.5.21. The error says "*_Powerpoint cannot insert a video from the selected file. Verify that the necessary codec for this media format is installed, and then try again._*". This applies to all video format. Please help! Thanks

<Screenshot>
[IMG]https://www.dropbox.com/sh/27c9hxe5mhfq3oj/-OoR8OANso/Error%20Video%20Insert.jpg[/IMG]

---

### Post by Yougo on 2013-01-21
The message is pretty clear. PowerPoint doesn't know what to do with the file format you selected. What type of file is it?

MS PowerPoint uses windows media player for embedded videos. In a normal windows installation, most common codecs are preinstalled. In wine however, you have to install all of that yourself. Maybe even the mediaplayer (you could be lucky and ms office has it built in, I don't know)

You could try and install Windows Media Player and the needed codecs in Wine, or perhaps try if libreoffice in ubuntu does what you want. never hurts to try, right?

---

### Post by breeky5 on 2013-01-21
> **Yougo said:**
> The message is pretty clear. 

MS PowerPoint uses windows media player for embedded videos. In a normal windows installation, most common codes are preinstalled. In wine however, you have to install all of that yourself. Maybe even the mediaplayer (you could be lucky and ms office has it built in, I don't know)

You could try and install Windows Media Player in Wine, or perhaps try if libreoffice in ubuntu does what you want. never hurts to try, right?

Thanks for the reply Yougo :)

Yes i've tried to install wmp10 through winetricks, but still couldn't get it to work, maybe it's missing some codecs. Powerpoint crashes in the process and same goes with wmp while trying to play music or vids.

---

### Post by Yougo on 2013-01-21
Whoops I edited while you replied. 

What type of file is it? can you play it ok in an ubuntu video player like totem or vlc?

Can you open your presentation on a windows pc and try it there?
Can you open the presentation in libreoffice impress and try it there?

Where are you going to run the presentation? On another windows pc? Or on your own pc through wine?

My personal experience with PowerPoint and videos is that there are so many things that can go wrong, especially if you use a third computer to run it, like a school pc, I just don't bother embedding it, and start it separately in a media player

---

### Post by breeky5 on 2013-01-21
> **Yougo said:**
> 

What type of file is it? can you play it ok in an ubuntu video player like totem or vlc?

Can you open your presentation on a windows pc and try it there?
Can you open the presentation in libreoffice impress and try it there?

Where are you going to run the presentation? On another windows pc? Or on your own pc through wine?

Yes i can run the files (mp3, wmv, mpg, mp4 etc.) natively on vlc and impress. But I need to make it work on powerpoint because there are some complex things impress just can't do. I'll be using the same computer to run the presentation through wine. 

Thanks! :)

---

### Post by Yougo on 2013-01-21
below is a link to a thread in WineHQ forum:
[http://forum.winehq.org/viewtopic.php?p=16478](http://forum.winehq.org/viewtopic.php?p=16478)

it talks about an older version of powrpoint, but the problem is very similar.
i suggest installing Windows Media Player through Winetricks, and see if that helps Powerpoint along.

let me know if that worked

---

### Post by Mark Phelps on 2013-01-21
If you're relying on WMP to play the videos -- that could be the problem.  The WineHQ site shows Bronze for WMP 10 -- which is the worst rating you can get if something even runs!

If you can find it, there is a WMP Classic version out there that has been known to work (in Windows, that is) when newer versions of WMP do not.  

Problem is, those older versions are rated Garbage in WineHQ.

My personal experience is that Linux is a poor platform to use if you depend on MS Office apps, especially the newer versions.

---

### Post by breeky5 on 2013-01-21
Thanks for the replies!

I tried to install wmp using playonlinux and it worked well however it uses wine version 1.3 and therfore cannot be integrated to ms office that is installed on a different wineprefix w/c is the system default (wine 1.5.21). Any workaround ideas?

---

