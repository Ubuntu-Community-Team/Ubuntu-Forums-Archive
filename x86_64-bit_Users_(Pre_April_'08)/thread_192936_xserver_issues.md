---
title: "xserver issues"
date: 2006-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Princey on 2006-06-09
Hi, I've spent the last 3 hours scouring through the forums in hope of finding a solution to my problem. I initially had a few questions as posted in this post [http://www.ubuntuforums.org/showthread.php?t=185915]("http://www.ubuntuforums.org/showthread.php?t=185915") However, I did a fresh install on my new machine of the text based AMD64 Kubuntu LTS and much of what I got on the LiveCd surfaced. As in the above linked post, I had an ATI X600 SLI graphics card. After installation, I'm greeted with a partial blank screen saying Kubuntu and a blue bar just under it but nothing else. I followed the tips in this post [http://www.ubuntuforums.org/showthread.php?t=190036]("http://www.ubuntuforums.org/showthread.php?t=190036") but with no such luck. I'd have posted there but it's a Ubuntu post so I rather start a new one, no harm intended. 

What's weird is I use the live i386 CD to install by mistake. I could boot in the "limited graphics" option and install. When loaded, the os loads to the GUI without a hitch. Popped in the amd64 alternate disc and install, but no such luck. Here's the outline of my installation:

4.56 GB Swap
18.6 GB / (root)
20.6 GB /usr
111.4 GB /home

Following the post just referenced, I entered pressed > CTRL+ALT+F1 and entered as directed ```
sudo dpkg-reconfigure xserver-org
``` and got the message > package 'xserver-org' is not installed and no info is available
use dpkg --info (=dpkg-deb --info) to examine archive files and dpkg --contents (=dpkg-deb --contents) to list their contents
/usr/sbin/dpkg-reconfigure : xserver-org is not installed

I tried the next tip ```
sudo pico /etc/x11/xorg.conf
``` but when nano opened, it said at the bottom > new file

I take it to mean that the file also doesn't exist. Is it because my /usr directory is on a separate partition? Then I proceed to the other advice given: ```
sudo apt-get install xorg-driver-fglrx
``` with the result > package not found I guess because my wireless card isn't set up properly it can't connect to download the file.

My question is, what next should I do to get a bootable gui?](*,) :confused:

---

### Post by miggl on 2006-06-09
You mention that you are using the Live CD. I had some quirkiness with that as well. Have you tried from the text-only installation CD? If not, I guess the next step would be to try that.
Oh, and another question: are you able to boot into the Live CD and run KDE from the CD, or does that fail as well? (I forget if you said you did or not.)

---

### Post by Princey on 2006-06-09
[QUOTE=miggl]You mention that you are using the Live CD. I had some quirkiness with that as well. Have you tried from the text-only installation CD? If not, I guess the next step would be to try that.
Oh, and another question: are you able to boot into the Live CD and run KDE from the CD, or does that fail as well? (I forget if you said you did or not.)[/QUOTE]


Yes, as I stated my install was from the Text CD. Yes again to being able to boot from the live cd only if I chose "default graphics mode" or whatever it says. I can't remember right now as I'm running off that CD at the moment.

---

### Post by Princey on 2006-06-10
_Update_

After how many unsuccessful attempts, I finally got to reconfigure xserver. Turned out I was committing typo errors and that X11 is case sensitive (was typing 'x11' not 'X11'.

However, I've reconfigured xserver, changed 'ati' to 'vesa'. 

Result: NO LUCK!!

Edited xorg.conf inserting the line ```
Options "MonitorLayout" "LUDS,Auto"
``` as outlined in [http://www.ubuntuforums.org/showpost.php?p=1102736&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=1102736&postcount=4")

Saved and restarted kdm and got > updating upsplash Stayed a few seconds then returned to the comand line text screen I had with the last two outputs at > shutting down kdm
restarting kdm

Rebooted, still greeted with the same screen as before--a black screen with blue Kubuntu and the blue bar underneath. 

Is there away to force the system to boot using "safe graphic mode drivers" by editing grub just as it's done on the live CD? I still can't get to use my desktop install of Kubuntu. I can't do everything I want to do off the live CD. Any help would be appreciated.

If anything, I've got a Princeton 17" LCD Monitor using a standard VGA connection.

---

### Post by miggl on 2006-06-10
Wow, sorry to hear that you're having so much bad luck. :( Are you going with Kubuntu for any specific reason? I'm wondering if you may not have better luck with Ubuntu? Even just to see if you can successfully boot into GDM. At least then you might have a temporary solution until you can get Kubuntu running.

---

### Post by Princey on 2006-06-10
> Wow, sorry to hear that you're having so much bad luck. :( Are you going with Kubuntu for any specific reason? I'm wondering if you may not have better luck with Ubuntu? Even just to see if you can successfully boot into GDM. At least then you might have a temporary solution until you can get Kubuntu running.

There's no real reason save that I just prefer KDE over Gnome. Anyhow, thanks for the advice. 

-------------------------------
_**Update**_

I decided seeing I had success when I accidentally installed the 32bit edition of Kubuntu to try the live CD of Kubuntu AMD 64. Success:-D  I didn't try it before and seeing I had the CD booting from to access the forums while I dug around to find a solution, I gave it a go. Yes, there's a sort of black/greying screen that momentarily comes up, but that disappears quickly enough to be a non-issue. Now, I'm wondering will upgrading to k8 will undo my settings or should it go without a hitch?

---

### Post by kuja on 2006-06-10
> package 'xserver-org' is not installed and no info is available
 use dpkg --info (=dpkg-deb --info) to examine archive files and dpkg --contents (=dpkg-deb --contents) to list their contents
 /usr/sbin/dpkg-reconfigure : xserver-org is not installed

Humm, I do believe that this should be "xserver-xorg", could this somehow be related to the problem. If so, try sudo apt-get install xserver-xorg, and also try reconfiguring that.

---

### Post by Princey on 2006-06-10
[QUOTE=kuja]Humm, I do believe that this should be "xserver-xorg", could this somehow be related to the problem. If so, try sudo apt-get install xserver-xorg, and also try reconfiguring that.[/QUOTE]

I did state in a later post that I got around that issue as I was typing in the wrong command. However, I got the problem solved as stated in the post [http://ubuntuforums.org/showpost.php?p=1122018&postcount=6]("http://ubuntuforums.org/showpost.php?p=1122018&postcount=6") by doing a clean install using the live CD instead. Thanks for the suggestion though.

---

