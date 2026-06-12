---
title: "screen goes grey, returns slow9.04"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by ken78724 on 2009-06-04
Solved +/- with kxstudio 10.04.02 ppa build / no screen problem

In 9.04 Jaunty, what can cause one's screen to go gray for example amidst a download, saving a doc, or using two programs at once. Have made a sys bug report but am curious whether others have found a way to solve this. :o

---

### Post by muecker on 2009-06-05
I think its the hard drive controller (software or hardware).  On my new desktop I'm having issues where the system will "pause" for minutes at a time.  This system has a built-in Intel fake raid hardware controller.  The grey screen is compiz signalling the window is not responding.

---

### Post by CadetD on 2009-06-06
Ever since Jaunty, I am having the same problem. 

Disabling Compiz does not help (with Compiz, you get the grey screen). There is a significant delay (up to 25secs) in whatever you open, move, click. 

I thought it was the ATI drivers (that's a whole different problem with the missing/bad fglrx drivers), but even with VESA, you get the same effect. 

System is a 2x Dual Core AMD Opteron (4 CPUs) with 4 GB RAM and 4TB of disk. Video is an ATI X1950 Pro. I don't think it is a resource issue as this did not happen with the previous releases. 

I will waste another 2 days at most on this then it is downgrade and hope for the best.

---

### Post by MG37221 on 2009-06-08
> **CadetD said:**
> Ever since Jaunty, I am having the same problem. 

Disabling Compiz does not help (with Compiz, you get the grey screen). There is a significant delay (up to 25secs) in whatever you open, move, click. 

I thought it was the ATI drivers (that's a whole different problem with the missing/bad fglrx drivers), but even with VESA, you get the same effect. 

System is a 2x Dual Core AMD Opteron (4 CPUs) with 4 GB RAM and 4TB of disk. Video is an ATI X1950 Pro. I don't think it is a resource issue as this did not happen with the previous releases. 

I will waste another 2 days at most on this then it is downgrade and hope for the best.

It is a 9.04 issue I´m pretty sure.  My video is nVidia 7600GT and am using a single Opteron dual core with 2GB so it is not your ATI drivers.  I am also experiencing it on a netbook with Intel video.

I can live with it but it isn´t convenient.  I prefer the machine wait on me and not the other way around.  I do think that, only because of this problem, I´ll be recommending 8.10 to a friend who is ready to make the jump though.

---

### Post by muecker on 2009-06-22
> **muecker said:**
> I think its the hard drive controller (software or hardware).  On my new desktop I'm having issues where the system will "pause" for minutes at a time.  This system has a built-in Intel fake raid hardware controller.  The grey screen is compiz signalling the window is not responding.
There may be a solution by following this post: [http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29)

I upgraded my kernel from 2.6.28-13 to 2.6.29-5 this morning and have not had my machine freeze since then.  Usually it happens when I have synchronize through Eclipse since it causes a lot of hard disk access but not today.  The nVidia driver automatically updated to the new kernel and everything else seems to be functioning normal.  I had one minor issue that my second monitor was flickering, I manually set the resolution and refresh rate and it cleared up.

I will post again if I have additional problems, but I think the kernel upgrade fixed the problem.

---

### Post by CadetD on 2009-06-22
Held my breath the whole day. Rushed home. Downloaded the 2.6.29-x kernel and...
....
Whahhhhhhh....!!!!!  :(
Same problem persists.

---

### Post by CadetD on 2009-06-22
Eureka!
I just noticed that one of my cores was being pegged by Xorg. So I Googled that. 
Lo and behold. Other folks have seen the same thing... with same sluggish behavior. 

The fix, add the following to your /etc/X11/xorg.conf file: 

Section "Device"
    Identifier  "Configured Video Device"
    Option "AccelMethod" "XAA"
EndSection

That's it! No more sluggish behavior.

---

### Post by ken78724 on 2009-07-25
CadetD, I've been using a PC with a different OS and am back. Alert me how you open the file: "/etc/X11/xorg.conf"? Would I begin with Administration> ? > ? > insert?

---

### Post by ken78724 on 2009-07-25
yes, my screen still goes grey; so instruct me; plus, am interested in the advantages provided with the latest kernel. should I add that too?

---

### Post by linux4me on 2009-07-25
> **ken78724 said:**
> CadetD, I've been using a PC with a different OS and am back. Alert me how you open the file: "/etc/X11/xorg.conf"? Would I begin with Administration> ? > ? > insert?
Try Applications->Accessories->Terminal, then in Terminal type:
```
sudo gedit /etc/X11/xorg.conf
```
to open xorg.conf in your text editor. (You'll be prompted for your password to allow access to the file.)

Make sure to save the file when you're done editing, then close the text editor. You'll probably need to restart to get it to take effect. The easiest way is to reboot.

---

### Post by ken78724 on 2009-07-25
Amidst closing for reboot. Many thanks!

---

### Post by philcamlin on 2009-07-25
> **CadetD said:**
> Eureka!
I just noticed that one of my cores was being pegged by Xorg. So I Googled that. 
Lo and behold. Other folks have seen the same thing... with same sluggish behavior. 

The fix, add the following to your /etc/X11/xorg.conf file: 

Section "Device"
    Identifier  "Configured Video Device"
    Option "AccelMethod" "XAA"
EndSection

That's it! No more sluggish behavior.

ahah thanks :popcorn:

---

### Post by ken78724 on 2009-07-26
philcamlin, the grey screen showed up once after following CadetEd's remedy; but I've been able to work about 3 hours w/o being slowed down. Let you know more. 

Thanks to each of you!! :)

---

### Post by ken78724 on 2009-10-27
CadetD, PhilCamlin or anyone who can guide me. 

I created a new problem. Grey screen had returned after doing ubuntustudio builds; came back here, opened xorg.conf did an incorrect edit, which killed my PC. 
Here's what I added following /etc/X11/xorg.conf 
   I cut and pasted the following on line 1 before 
Section "Device"
Identifier "Configured Video Device"
Option "AccelMethod" "XAA"
EndSection
   rather than after last entry, which would I believe be started on line 5 
   
Results:
I boot, get the Ubuntu Studio logo but screen goes into gyrations b4 I can login. Then I'm dumbfounded with no knowledge how to proceed or even do a bug report and cannot use that mirus PC with descript in my signature ???????:(  Yes, I am panicked.

Question: how do I create a bug report or rescue my PC?

---

### Post by CadetD on 2009-10-27
You can boot into "single" mode to fix the xorg.conf file. 
At boot menu (if you don't get the menu, start hitting ESC after BIOS POST), highligh the line for the version you want to boot. 
- type "e" (without quotes)
- on the BOOT line, go to end of line and add "single" (without quotes)
- hit enter or ESCape 
- type "b" (w/o quotes)
This will put you in a command line as ROOT and you can go fix the xorg file. 

---
On a different note. I reinstalled my Ubuntu Studion from latest .ISO and now everything is GREAT! Somehow the ATI drivers were still in there messing things up. 

Lessons learned: 
- Stick to the Open Source drivers!
- Don't buy from vendors who are not committed to true Linux support.

---

### Post by ken78724 on 2009-10-27
Friends, let me say follow CadetD's instructions carefully but if you do not do so and end up not being able to login, follow these graphic recovery methods: use Your ESC key during boot up,, let it take you to the generic kernel recovery mode, which allowed you to go to 1) root@kproductions where if you know how to work around, edit and save, you may "reorder" the command CadetD's change creates and save xorg.conf in the correct sequence; and then 2) to run Xfix which "recalibrats your graphics" and 3)  dkpg which "updates packages" and then 4) "return to reboot" and this automatically allowed you to login in as if you have a new PC. Whoopee!!!! This solved my dilemma. ;)

---

### Post by ken78724 on 2009-10-31
still seeing gray screen every once in a while. must diagnose but not sure xorg.conf and xfix did all that's needed.

---

