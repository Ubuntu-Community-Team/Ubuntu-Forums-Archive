---
title: "CPU is running slower than it should"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by chainzz on 2006-06-03
I have just installed Ubuntu Dapper amd64 on my system. It's the first time I installed a 64 bit OS, I just wanted to do a little bit of experimenting. My CPU is an AMD Sempron 64 3000+ (Palermo). 

I just checked /proc/cpuinfo and my processor is running on 1100 Mhz, but it should be running on 1980 Mhz (I overclocked it a little bit). I also had this issue on the i386 version of Dapper but I solved it by uninstalling 'athcool' with Synaptic. This program clocked the CPU to lower speeds when you didn't use it very intensively, but it didn't work so well on my system, it only slowed things down.

I just tried to find 'athcool' with Synaptic on my new 64-bit Ubuntu Dapper to uninstall it, but I couldn't find it. Is there another program on the 64-bit version of Dapper that is doing the same thing as 'athcool' is doing on the 32-bit version?

---

### Post by chainzz on 2006-06-03
I just reinstalled the 32-bit version of Ubuntu Dapper because a lot of programs that I need aren't available for 64-bit. I tried to search for 'athcool' in Synaptic again but I still didn't find anything. It seems like it just disappeared since the official release of Dapper. But another program must have replaced it, because my processor just isn't running at it's top speed.

---

### Post by E@zyVG on 2006-06-03
Switch Off cool'n'quite in BIOS for CPU to run @full speed all time.

---

### Post by henriquemaia on 2006-06-03
[quote=chainzz]I have just installed Ubuntu Dapper amd64 on my system. It's the first time I installed a 64 bit OS, I just wanted to do a little bit of experimenting. My CPU is an AMD Sempron 64 3000+ (Palermo). 

I just checked /proc/cpuinfo and my processor is running on 1100 Mhz, but it should be running on 1980 Mhz (I overclocked it a little bit). I also had this issue on the i386 version of Dapper but I solved it by uninstalling 'athcool' with Synaptic. This program clocked the CPU to lower speeds when you didn't use it very intensively, but it didn't work so well on my system, it only slowed things down.

I just tried to find 'athcool' with Synaptic on my new 64-bit Ubuntu Dapper to uninstall it, but I couldn't find it. Is there another program on the 64-bit version of Dapper that is doing the same thing as 'athcool' is doing on the 32-bit version?[/quote]

Please have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=183996](http://ubuntuforums.org/showthread.php?t=183996)

You'll get the picture of what is happening. And it is good to be this way.

:)

---

### Post by chainzz on 2006-06-04
[QUOTE=E@zyVG]Switch Off cool'n'quite in BIOS for CPU to run @full speed all time.[/QUOTE]
There is no Cool 'n Quiet option in my BIOS.
[QUOTE=henriquemaia]Please have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=183996](http://ubuntuforums.org/showthread.php?t=183996)

You'll get the picture of what is happening. And it is good to be this way.

:)[/QUOTE]
I hope it is good this way, because I am planning to do some serious video editing with Cinelerra so I have to get maximum performance out of my system. I added the CPU Frequency Scaling Monitor to my GNOME panel and my frequency went higher when doing more intensive tasks so I think it's allright.

---

### Post by henriquemaia on 2006-06-04
[quote=chainzz]There is no Cool 'n Quiet option in my BIOS.

I hope it is good this way, because I am planning to do some serious video editing with Cinelerra so I have to get maximum performance out of my system. I added the CPU Frequency Scaling Monitor to my GNOME panel and my frequency went higher when doing more intensive tasks so I think it's allright.[/quote] 
I have that kind of response all the time. Like I said on that thread, I spoted that issue and dind't felt any performance lost. I now realize that there isn't any performance lost since the CPU just works full speed when needed. One thing to appreciate Dapper 64bit more.

Open an app, move a window franticly around the screen, compile stuff, and you'll see the scaling monitor go up to meet those needs.


ps: about this "Switch Off cool'n'quite in BIOS for CPU to run @full speed all time.", I have switched off on my bios and still have scalling. I Guess Linux kernel is more clever than my BIOS. :)

---

### Post by gratefulfrog on 2006-06-04
[QUOTE=chainzz]

I hope it is good this way, because I am planning to do some serious video editing with Cinelerra so I have to get maximum performance out of my system. [/QUOTE]

I've been running cinelerra heavily for a year on my AMD64. Except for rendering, you should never need much CPU. RAM is far more important. When rendering, you'll never have enough CPU with a single machine to see a significant difference, IMHO.

I'd be interested in hearing your cinelerra experiences, though. Are you an expert user? If not, I've put some beginners hints on my homepage [http://gratefulfrog.net]("http://gratefulfrog.net").

Cheers,
gf

---

### Post by chainzz on 2006-06-04
[QUOTE=gratefulfrog]I've been running cinelerra heavily for a year on my AMD64. Except for rendering, you should never need much CPU. RAM is far more important. When rendering, you'll never have enough CPU with a single machine to see a significant difference, IMHO.

I'd be interested in hearing your cinelerra experiences, though. Are you an expert user? If not, I've put some beginners hints on my homepage [http://gratefulfrog.net]("http://gratefulfrog.net").

Cheers,
gf[/QUOTE]
No, I'm not an expert user, but I really want to learn to use the program. However, I want to use the CVS version but I'm having trouble compiling it, check my topic: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264). First I tried to install it from the Ubuntu repositories found on [http://cvs.cinelerra.org](http://cvs.cinelerra.org), but it didn't work because it couldn't install libopenexr2c2. What version are you using by the way, the CVS version or the version from heroinewarrior.com? I installed the version from heroinewarrior.com by converting the RPM to a Debian package with alien, but I read that the CVS version is better and more stable. Your site seems to be down by the way..... I really would like to read your beginners hints.

---

### Post by chainzz on 2006-06-04
By the way, I found the program that scales down the frequency when your CPU isn't used intensively: it's powernowd. I uninstalled it and now my CPU is running on full speed all the time.

---

### Post by henriquemaia on 2006-06-04
[quote=chainzz]By the way, I found the program that scales down the frequency when your CPU isn't used intensively: it's powernowd. I uninstalled it and now my CPU is running on full speed all the time.[/quote]

You don't need to uninstall it. You can disable it with BUM.  Even better, you can kill powernowd when you want a full speed CPU and leaving in the initd to restart next time you boot (to kill powernowd, just use **sudo killall powernowd**)

Just an idea.

---

### Post by gratefulfrog on 2006-06-05
[QUOTE=chainzz]Your site seems to be down by the way..... I really would like to read your beginners hints.[/QUOTE]

Yes, I just found that my site is down, those domain people... try this direct link to my cinelerra page: [http://home.tiscali.be/asld0009/PhotoAndVideo/HowToDvd.html]("http://home.tiscali.be/asld0009/PhotoAndVideo/HowToDvd.html")

I built my own from source, but it wasn't straightforward.  But I'm a professional sw developer...

Again, if I were you I'd just start with any version of cinelerra you can find, install and **configure** it, and play with it. You may be surprised at how often it crashes, yet  since this problem has been there forever, there is good built in crash protection - you never lose any work, just patience.  

Forget about all that CPU frequency stuff, that is of no importance for your use.

Again, the main source of help for cinelerra is the IRC channel.

Keep me posted you can always send me a message at the my account on the ubuntu forums!

Ciao,
GF.

---

### Post by chainzz on 2006-06-06
Thank you, your cinelerra page is very helpful!

---

### Post by gratefulfrog on 2006-06-06
It's my pleasure! Keep me/us informed of your progress!
Ciao,
gf_at_gratefulfrog_dot_net

---

### Post by chainzz on 2006-06-07
I finally found the solution and now I can compile Cinelerra-CVS succesfully. Please check my other thread for the solution: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)

---

