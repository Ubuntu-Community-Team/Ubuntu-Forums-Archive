---
title: "DVD Player for amd64"
date: 2009-03-10
forum: x86 64-bit Users
---

### Post by xich2011 on 2009-03-10
Hey... Is there a DVD-Player for a 64-bit version of ubuntu?  I tried looking at some forums and none of them helped.  I am also trying to get subtitles to work, so is there like a thorough compatible DVD Player that will also work with subtitles?

---

### Post by cybergalvez on 2009-03-10
I use VLC

---

### Post by xich2011 on 2009-03-10
How do you get that? can you show me the exact terminal command?

---

### Post by Yellow Pasque on 2009-03-10
Any open-source media player that works on 32-bit should work just as well on 64-bit (VLC, MPlayer, xine, Totem, MoviePlayer, etc.)

Make sure you have libdvdcss2 installed if you're having trouble with encrypted discs. Medibuntu makes it easy: [http://www.medibuntu.org/](http://www.medibuntu.org/)

For VLC:
```
sudo apt-get install vlc
```

---

### Post by xich2011 on 2009-03-10
> **Temüjin said:**
> Any open-source media player that works on 32-bit should work just as well on 64-bit (VLC, MPlayer, xine, Totem, MoviePlayer, etc.)

Make sure you have libdvdcss2 installed if you're having trouble with encrypted discs. Medibuntu makes it easy: [http://www.medibuntu.org/](http://www.medibuntu.org/)

For VLC:
```
sudo apt-get install vlc
```

Yes, but with *buntu, i386 programs will not be allowed to install on amd64.

---

### Post by Yellow Pasque on 2009-03-10
Technically, you can install and run 32-bit programs, but unless you have a closed-source program, you wouldn't want to.

---

### Post by stchman on 2009-03-10
> **xich2011 said:**
> Hey... Is there a DVD-Player for a 64-bit version of ubuntu?  I tried looking at some forums and none of them helped.  I am also trying to get subtitles to work, so is there like a thorough compatible DVD Player that will also work with subtitles?

I have a tutorial to get DVDs to play in Ubuntu.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by mcloser on 2009-03-10
ok do the updates and then REBOOT !

I downloaded alot of stuff and nothing worked until I had the bright idea to reboot like that OS which cannot be named.

now hollywood dvds play in all the video players.

thanks to stchman for the tutorial, it did help !

just add the point about rebooting.

---

### Post by Arup on 2009-03-11
VLC works fine, you also get hardware color control and subtitles plus good equalizer.

---

### Post by jespdj on 2009-03-11
> **xich2011 said:**
> Yes, but with *buntu, i386 programs will not be allowed to install on amd64.
You don't need an i386 program to play a DVD; all the mentioned programs are also available as 64-bit programs.

And you *can* run 32-bit programs on 64-bit too.

---

### Post by stchman on 2009-03-11
> **xich2011 said:**
> Hey... Is there a DVD-Player for a 64-bit version of ubuntu?  I tried looking at some forums and none of them helped.  I am also trying to get subtitles to work, so is there like a thorough compatible DVD Player that will also work with subtitles?

Yes, VLC will work for you.

```
sudo apt-get install vlc
```

You will need to tell Ubuntu to use it when a DVD is inserted by going to Edit--->Preferences and select the Multimedia tab in Nautilus.

---

### Post by freedomIndia on 2009-03-12
Wow! Lots of info on your page.
Thanks man.
I used VLC in Windows and Mac, so i prefer VLC on Ubuntu too.
But the video quality is blurred in Ubuntu?
Why is that?

---

