---
title: "Jaunty Fails to Shut Down"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by ursaminor on 2009-04-27
I'm running HP Pavilion a1228x desktop AMD64. Running Intrepid 8.10 gave me no problems on shut down. Jaunty on the other hand is not so jaunty. I have to shut down by pressing the power button a few seconds, not convenient. See attached jpeg to see where it hangs up.

I downloaded Kubuntu 9.04 to see if that would make any difference. It did not. Kubuntu showed the same screen which is attached below. must be a 9.04 problem.

---

### Post by John Jason Jordan on 2009-04-27
> **ursaminor said:**
> I'm running HP Pavilion a1228x desktop AMD64. Running Intrepid 8.10 gave me no problems on shut down. Jaunty on the other hand is not so jaunty. I have to shut down by unplugging my computer. See attached jpeg to see where it hangs up.

I have the same issue. I never had a problem with Ubuntu hanging on any version for the past several years, but Jaunty does not completely shut down. When it hangs I can get it to complete the shutdown by pressing Ctrl-Alt-Del, but it hangs right at the very end, so it's faster just to hold the power button down.

I am using a Thinkpd T61.

In my case the dist-upgrade script failed to complete properly and I discovered that the gnome panel and metacity were not loading (blank screen on booting). I suspect something else did not upgrade properly as well. I fixed the gnome panel and metacity problems, but I'm at a loss as to what else might not be getting loaded.

---

### Post by Chesh on 2009-04-30
Jaunty 64 bit,

Same problem here, same screen as op, I get a system beep when I shutdown and then that. Thinkpad W500.

---

### Post by Slurm on 2009-04-30
Just wanted to say that it hangs on my system also.  Jaunty causing some other bugs in rhythmbox,  Totem.. firefox... also.   I would have never thought that Ubuntu would release such buggy OS.

Good Luck to us all!

---

### Post by quixote on 2009-04-30
I was getting that symptom too.  Then all kinds of inode problems would show up during bootup.  I'd run fsck, e2fsck, get the system put back together, and then it would happen again.  One time when random junk was appearing on my drive, it clobbered gconf.  That was a bigger mess.  Fixed that, and then it clobbered grub and my partition table . . . .

This is not good, folks.

First I assumed I had a failing hard drive, but just for the hell of it I installed intrepid in its own partition, after I fixed the last problem with testdisk.  That seems to be running okay.  (It's the OS that was on there before.)

So, it seems to be jaunty.

Very, very, very NOT GOOD.  As Slurm said, I wouldn't have thought Ubuntu would release such a buggy OS.  Sure is beautiful and fast when it runs.  But having to reinstall every couple of hours is a kind of high price to pay.  :(

---

### Post by Guilden_NL on 2009-05-02
Add me to the list with an HP HDX18.  It didn't do it the first two days.  I am mentally going back to what I changed from the upgrade and on this machine, the only thing I can think of is that I made a change to get the sound to work.  I will backtrace what I did, remove it and see if that fixes the problem.  I'll post the results back here.

---

### Post by Guilden_NL on 2009-05-02
Quick answer is that didn't make any difference.  Strange, I upgraded and everything worked perfectly, with the exception of no sound (I didn't notice that right away, I don't hear so well anymore due to many years of rock n roll...)

I haven't changed anything else.

It smells to me like a graphics card issue where it's not dropping the orgX server session.  I am going to try backing out the NVidia driver and then see what happens.

---

### Post by ndee_at on 2009-05-02
Hi guys,

having the same issue for 2 days now. Shutdown hangs, had even a system hang during idle time.

Upgraded to Jaunty on approx. 26th of April. After upgrade to Jaunty and new nvidia drivers there was always a flickering with some colors on the black screen on shutdown - which was not the case with 8.10.

platform amd64
ubuntu 9.04
lenovo TP R61

greets

---

### Post by Guilden_NL on 2009-05-02
[LIST=1]
[*]Dropped back to NVidia driver 177, didn't help
[*]Dropped to the Open Source version, didn't help
[/LIST]
Now checking Advanced Power settings, that's literally the only other thing that I may have changed since upgrading earlier this week and not having the shut down problem until yesterday.  But upon checking those, it appears that I haven't changed anything.  Will try to set logs to show what's going on.

---

### Post by Sollus on 2009-05-02
+1

ASUS G1S; it was working fine after the initial install but now there are issues with hibernate, sleep, and shutdown. 

Anyone filed a bug report yet?

---

### Post by Guilden_NL on 2009-05-02
I see nothing in the logs that appears to affect the shutdown or reboot.  I did find previous bugs from 2004 & 2005 that appear to be identical in behaviour to this problem.

I will file a bug report and see if we get anywhere with it.  

It's certainly strange that everything works fine for two days post-upgrade, then with almost no changes (hey it worked perfectly!) it regresses into mess.

---

### Post by lisati on 2009-05-02
I had a shutdown problem when I had 64-bit Jaunty on my Toshiba M200 laptop. I remember reading in another thread while researching it (don't have a link at the moment) that for some people, there seemed to be a connection with their WiFi card: leave the card switched on and the system would hang on shutdown; turn off the WiFi card and it would shut down normally.

(I've temporarily gone back to Interpid on my machine that was affected.)

---

### Post by cprofitt on 2009-05-02
I have filed a bug report...

I also found that running the following in console immediately before shutdown helped me.

```

sudo ifconfig wlan0 down

```

the bug report is here - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302452](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302452)

---

### Post by JJ_Kame_R on 2009-05-03
+1
Same here on my ASUS x57 notebook.
It's damn annoying.

I have noticed that it happends always when on battery power and randomly when connectet to the power plug.

It's surely something ACPI/Hardware poweroff related.
I will try the lan down command to see if it helps.

And yes... I agree that this Jackalope seems too buggy compared to any previous release.

---

### Post by jespdj on 2009-05-03
This is not the first thread about this problem.

See [this thread](http://ubuntuforums.org/showthread.php?t=1134201) for workarounds.

The problem seems to be with the wireless driver. By adding a script that stops the wireless driver at shutdown you can workaround the problem.

---

### Post by Guilden_NL on 2009-05-03
Thanks jespdj, the workaround did it for me. [[COLOR="RoyalBlue"]**Found here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1134201&page=3")  I also updated bug report #302452 - this is a kernel problem that goes way back. It was fixed, then slipped back in.

What I find maddening is that it didn't hit this system for two days after upgrading from Intrepid.  No updates to the system either, so it's not like they slipped it into an update.  It's ***very*** strange.

With that, I think I'll wander off to listen to Cud's Rich and Strange...
[[COLOR="RoyalBlue"]Rich and Strange[/COLOR]]("http://www.last.fm/music/CUD/_/Rich+and+Strange/+lyrics")
[IMG]http://tbn1.google.com/images?q=tbn:Ug8hsIZXejiO0M:http://ecx.images-amazon.com/images/I/219VE68G4KL._SL500_AA120_.jpg[/IMG]

---

### Post by Xiborg on 2009-05-06
Hi

I have a similar problem. After shutdown the screen turns black, but the mouse cursor is still there and responsive.
I used CTRL-ALT-BACKSPACE to restart X-Server which leads me back to the login screen. From there shutdown works.

regards
Xiborg

---

### Post by ashutoshdighe on 2009-05-06
Hi,

I upgraded from 8.10 to 9.04 and did not have any problems initally. I started having this problem 3 days back and the only thing I remember is that there was an upgrade and I think the netwwork manager was also upgraded in the same process.

Anyways... to get to the point, the way I use to get around this issue is to use powertop. During this time, there is a suggestion to implement wireless power saving, and after implementing the power saving, there is no issue with the shutdown.

Hope this helps.

Specs
Toshiba Satellite M115-S3144
Intel T5200

Thanks,
Ashutosh.

---

### Post by blitzer on 2009-05-07
Same problem here I hit the space bar and it shuts down ?  Wireless seems to be the culprit ?

---

### Post by jeezum crow on 2009-05-17
I had the same problem. Reinstalled Kubuntu 9.04 3 times, still wouldn't reboot after the install, then I replaced my onboard ATI Ratheon 200 video  with NVIDIA GeForce 6500 PCI Express. Reinstalled Kubuntu 9.04. Reboots/shuts down every time.

---

