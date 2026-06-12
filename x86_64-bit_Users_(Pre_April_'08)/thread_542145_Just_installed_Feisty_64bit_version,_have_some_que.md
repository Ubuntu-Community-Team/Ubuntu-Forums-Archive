---
title: "Just installed Feisty 64bit version, have some questions"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Starrfoxx on 2007-09-03
I have a 500gb SATA drive.  Most of it is being used for XP for games and other software I use.  I partitioned 20 gig aside for Ubuntu Feisty 64 bit, so that I can give it a try with my Dual Core Athlon XP processor.  I wanted to ask a few questions:

1)  When installing, there was 8 gig of unused/unpartitioned space on my hard drive.  I've noticed that there is always some bit of unused amount that can't be put together with the rest of the partitions.  Ubuntu was able to see this, and I could use it as a swap file.  Hopefully this will be okay.  I'm not exactly what a swap file is.  I thought it was to transfer files back and forth between Ubuntu and Windows, but I think upon further reading it has something to do with memory.

2)  I can't seem to figure out how much drive space I have left on the partition I used for Ubuntu.  It doesn't show up in Windows, and on Ubuntu I just get the drives that are over on Windows.

3)  I managed to get Flash working in Firefox, but YouTube doesn't work perfectly.  I can play a movie, but I can't seem to scroll the little play bar at the bottom or "click" to fast foward through it.

4)  I've got MP3's to play, but I'm having trouble getting DVD's to play.  I installed the MPlayer Movie Player, but no luck on playing DVD's.


I'm taking things a little at a time, since I'm new to Linux.  If I can get the above working, then I can try some other things out.  I wanted to try Ubuntu because it's safe to surf the internet than Windows.  I get tired of all the spyware, etc over on Windows, so I want to keep Windows just for games and leave the surfing to Ubuntu.  I'm using Ubuntu to type this for the moment.  Thanks for the help.

---

### Post by trim17 on 2007-09-03
> **Starrfoxx said:**
> Ubuntu was able to see this, and I could use it as a swap file.  Hopefully this will be okay.  I'm not exactly what a swap file is.  I thought it was to transfer files back and forth between Ubuntu and Windows, but I think upon further reading it has something to do with memory.


The swap file is like having the system "borrowing" part of your hard drive as memory. RAM is many times faster than the fastest hard drives, so it's always good to have plenty, but the swap file is needed when you run out of memory. It basically copies what you haven't used in the RAM to the hard drive. When you need that data again, it's copied from the hard drive to the RAM for the CPU to use. 

For example, if you've got a lot of programs open, but you're using one that is particularly memory intensive (such as The GIMP or Cinelerra), the memory used by the other applications will be copied to the swap file and be used for the app at hand. Once you go back to your other applications, the data will be copied back into RAM.

I hope that explains some things. There are many useful links on the[ wikipedia page on virtual memory]("http://en.wikipedia.org/wiki/Virtual_memory").

> **Starrfoxx said:**
> 2) I can't seem to figure out how much drive space I have left on the partition I used for Ubuntu. It doesn't show up in Windows, and on Ubuntu I just get the drives that are over on Windows.

Maybe I'm oversimplifying this, but try running this in a terminal:
```
df -h
``` [i]edit: science damn it, I meant df, not du
> 3) I managed to get Flash working in Firefox, but YouTube doesn't work perfectly. I can play a movie, but I can't seem to scroll the little play bar at the bottom or "click" to fast foward through it.

Not sure what the problem might be here. Did you use the ndiswrapper script to use a 32-bit Flash plugin? Not really something I'm familiar with, sorry.

---

### Post by Harpoon on 2007-09-04
You say you can't get dvds to play, but what exactly is the problem?  It may be that you need to install a utility called libdvdcss2 (use apt-get or the package manager or automatix) ;  it may be that you are missing some codecs that are required to play the dvd (I know THE Ubuntu folks hate this, but install and run automatix and have it install the codecs for you).

---

### Post by gnusci on 2007-09-04
Hey friend,

I will also recommend you to give a look to some useful introduction to the Linux shell, they will be very helpful for those many simple but very important things everyone need at any time, and also you will have a lot of fun. Here some links:

Tutors:
[http://vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf](http://vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf)

Basic:
[http://www.freesoftwaremagazine.com/articles/command_line_intro](http://www.freesoftwaremagazine.com/articles/command_line_intro)
[http://www.freesoftwaremagazine.com/articles/beginner_intro_cli_part_2](http://www.freesoftwaremagazine.com/articles/beginner_intro_cli_part_2)
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)
[http://users.aims.ac.za/~lisa//linux-commands.html](http://users.aims.ac.za/~lisa//linux-commands.html)
[http://www.howtoforge.com/useful_linux_commands](http://www.howtoforge.com/useful_linux_commands)
[http://www.linux.ie/newusers/beginners-linux-guide/](http://www.linux.ie/newusers/beginners-linux-guide/)

Reference:
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
[http://www.er.uqam.ca/nobel/r10735/unixcomm.html](http://www.er.uqam.ca/nobel/r10735/unixcomm.html)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

---

### Post by Yellow Pasque on 2007-09-04
If you're more comfortable with a GUI, there's also the Disk Usage Analyzer under the Accesories menu.

---

### Post by gtdaqua on 2007-09-05
try VLC Media Player for most common videos- its the best around. 

```

sudo apt-get install vlc-nox

```

It can pick up subtitles automatically (if you have them).

If you are using gnome desktop environment (default for Ubuntu) u can get the "Gstreamer" plugins which will install all DVD, DivX, XviD, mp3 codecs for you to play. You can search them using Synaptic Package Manager. Type "Gstream" and you wud get the results. Normally, you wud need to select the 3 plugins. In ubuntu, they can be installed automatically the first time you run an avi or mp3 file.

---

