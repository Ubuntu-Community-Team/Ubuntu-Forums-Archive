---
title: "Display Problems on Titanium PowerBook 550"
date: 2005-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by MichaelC on 2005-12-30
Hi

Installed Breezy on my PB 550.  Worked OK but only gave me the option of 640x480 screen resolution.  Read a couple of threads in the forums and tried reconfiguring my xserver.  It asked me a lot more questions than I expected and I tried to use the defaults for everything I wasn't sure about.  On reboot it got so far then the screen went psycodelic white-with-green patches.

Have tried booting from LiveCD and now get the same problem.  (Surely the LiveCD would use it's own display / xserver settings?)

Re-running install CD just gets me to the same point in boot before I get the same problem.

So, what can I do, or where and how in the boot process do I interrupt to get a text-only boot so I can reconfigure the xserver?

I guess a list of the safe choices for the xserver would be good too!

Thanks in advance

Michael

---

### Post by koni2005 on 2006-02-04
I have the same problem on my TiBook 1Ghz with ATI Radeon 9000 Graphics Card and one gig of memory.

Ubuntu & Kubuntu worked like a charm - dual booting with OS X Tiger. Until one day during ubuntu-booting somehow the graphics get wacky - I'm not an expert) I get weird graphic artefacts in the middle of the screen and the lower part of the screen.

When I boot / install with the option video=ofonly that does not happen and I can install the whole thing although afterwards I get a bloack screen instead of the log in window.

What is really weird is that I had no problem with ubuntu 5.10 at all until a few weeks ago - and not even a fresh install including completely repartitioning the hard disk will fix it.

Any suggestions?

Thanks

---

### Post by N8K99 on 2006-02-06
when you power up, try Control-Alt-F1 to get a getty screen, there should be  a login prompt. If you can login in then try sudo dpkg-reconfigure xorg.conf and then when you get to the screen resolution options you need to select 1185x758 (this was also what worked on the LiveCD for me). Good Luck.

---

### Post by koni2005 on 2006-02-08
Are we really the only ones with this problem?

Well, I tried rebooting again - and at the second try it worked!
Of course the next try wasn't succesfull anymore - and I ended up with those weird artifacts again.

But now I know exactly were the display crashes: If it does not crash, there is a message saying something like:

radeonfb: Invalid ROM signature 0 should be 0xaa55

although the numbers are different, I guess...

does this ring a bell with someone?

---

