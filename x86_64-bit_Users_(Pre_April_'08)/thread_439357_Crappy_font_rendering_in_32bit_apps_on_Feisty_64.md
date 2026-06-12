---
title: "Crappy font rendering in 32bit apps on Feisty 64"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_anjan on 2007-05-10
I have this strange problem. The font rendering in 32 bit apps (like Opera and Firefox32) installed on Feisty x64 is very bad. 

I have the packages to improve the subpixel font rendering from this thread: [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

The font rendering in the rest of Ubuntu is extremely good. Like the system menu and in nautilus, very good. In fact, even Firefox was extremely good, before I installed the 32 bit version. Even though I installed the 32 bit version separately, the font rendering in Firefox64 also degraded. I confirmed this fact by removing Firefox32 and then testing Firefox64. It was back to normal.

There is something wrong with the font rendering of these 32 bit apps. And it is starting to hurt the eyes. Please, does anyone have a clue as to what the problem could be?

I've uploaded 2 screenshots, one of Opera displaying the Ubuntu Forums home page, and another of Firefox 64 displaying the same page. I do not have Firefox 32 installed. If I have Firefox 32 also installed, the page looks bad even in the 64 bit version.

Note the font degradation even in the menus of Opera, not just the page display.

Firefox64:
[[IMG]http://img264.imageshack.us/img264/9605/firefox64bitis0.th.png[/IMG]](http://img264.imageshack.us/my.php?image=firefox64bitis0.png)

Opera:
[[IMG]http://img264.imageshack.us/img264/5092/opera32bitlm3.th.png[/IMG]](http://img264.imageshack.us/my.php?image=opera32bitlm3.png)

---

### Post by Cappy on 2007-05-10
Have you tried changing the font in the browsers? 
I personally changed all preferences from Bitstream Vera Serif to Bitstream Vera Sans.

In System --> Preferences --> Font I have the "Subpixel smoothing (LCD)" and in details I have Smoothing: LCD; Hinting: Full.

Maybe you could try replacing your i386 firefox with the AMD64 preferences (when installed alone) if it is only a setting issue.

---

### Post by Case_f on 2007-05-11
I can't really see from these screenshots that font rendering in 32bit/Opera is "very bad" compared to the 64bit screenshot, looks basically the same to me (and not that great, BTW), but it's probably due to my old CRT not being sharp enough to distinguish the difference.

However, as you say that you use patched subpixel rendering packages, I guess that's the problem - in 64bit, you are using the patched ones, whereas in 32bit you are of course just using the generic Feisty ones. So I think the solution would be to download the 32bit packages for improved subpixel rendering manually, extract their contents into some temporary directory (and I mean just EXTRACT, not try to install them using --force-architecture, that would be a VERY bad idea!) and then overwrite the appropriate 32bit libs (placed in /usr/lib32, as far as I remember - I don't have Ubuntu install available right now, so I can't verify) with the patched ones. That should solve it, IMHO.

---

### Post by t_anjan on 2007-05-13
Hey Case_f, I think what you say makes sense. BTW, you may not be noticing the difference in the screenshots because the browser may be resizing the images to fit the window. Please try looking at the images 1:1 size.

I'll try what you said and see if it makes a difference. Thank you.

---

### Post by Case_f on 2007-05-13
Sure, I was comparing the screenshots in 1:1, wouldn't make much sense otherwise :) And I DO see a difference there (the 32bit rendering is thinner), just nothing I would call "very bad" (especially considering that it doesn't look that great to me to begin with) . But hey, it's your config on your (very different from mine) monitor observed with your eyes, so who am I to judge anything, right? ;)

---

### Post by xstaticxgpx on 2007-05-14
I have the same problem, I'm currently using Swiftfox i686 and my fonts seem less smooth and crisp then in gnome. Sometime's it's like gnome, but most of the time it looks like it has no hinting.

---

### Post by t_anjan on 2007-05-14
> **Case_f said:**
> Sure, I was comparing the screenshots in 1:1, wouldn't make much sense otherwise :) And I DO see a difference there (the 32bit rendering is thinner), just nothing I would call "very bad" (especially considering that it doesn't look that great to me to begin with) . But hey, it's your config on your (very different from mine) monitor observed with your eyes, so who am I to judge anything, right? ;)

Does the Firefox64 screenshot also look bad to you? How have you configured your display? Anything special? To me, Firefox64 looks good only because I'm comparing it to Opera. Maybe there is something to make Firefox64 look even better?

---

### Post by t_anjan on 2007-05-14
> **xstaticxgpx said:**
> I have the same problem, I'm currently using Swiftfox i686 and my fonts seem less smooth and crisp then in gnome. Sometime's it's like gnome, but most of the time it looks like it has no hinting.

I have only Gnome and all my font rendering problems are on Gnome only. My 32 bit apps on Gnome look like they have hinting diabled or something like that.

---

### Post by Case_f on 2007-05-14
> **t_anjan said:**
> Does the Firefox64 screenshot also look bad to you? How have you configured your display? Anything special? To me, Firefox64 looks good only because I'm comparing it to Opera. Maybe there is something to make Firefox64 look even better?

It's not that bad, but I don't like the way for example s, a, W or M are rendered in your screenshot. They look distorted to me, like if they were hinted badly. May be font related, I guess.

> **xstaticxgpx said:**
> I have the same problem, I'm currently using Swiftfox i686 and my fonts seem less smooth and crisp then in gnome. Sometime's it's like gnome, but most of the time it looks like it has no hinting.

Hmm, could be that libfreetype is outdated in ia32-libs as compared with its 64bit counterpart and that it doesn't read /etc/fonts/fonts.conf and such correctly, therefore setting just the default hinting and rendering options? Just an idea, though. I'll probably check that later in Feisty (being on Arch 64 right now). But I remember that I was having this kind of problem on 64bit Linux before (outdated 32bit libfreetype), I just can't remember now what 64bit distro it was and what the lib versions were.
EDIT: No, that's not it, it works all right in Feisty, sorry for misleading you.

---

### Post by t_anjan on 2007-05-18
Hey Case_f, thanks a lot for that suggestion. I replaced three sets of files, namely libcairo, libfreetype and libxft in /usr/lib32 with the ones I extracted from 32 bit deb patched subpixel rendering packages. Then, I restarted Opera, and it looks great!

Here's a screenshot (compare it to the old one of Opera):
[[IMG]http://img19.imageshack.us/img19/4388/screenshottr7.th.png[/IMG]](http://img19.imageshack.us/my.php?image=screenshottr7.png)

---

### Post by Case_f on 2007-05-18
Glad it worked.

---

### Post by EatenByGrues on 2007-05-29
> **t_anjan said:**
> Hey Case_f, thanks a lot for that suggestion. I replaced three sets of files, namely libcairo, libfreetype and libxft in /usr/lib32 with the ones I extracted from 32 bit deb patched subpixel rendering packages. Then, I restarted Opera, and it looks great!

Where did you get the deb files with the patched versions of those libraries?

---

### Post by t_anjan on 2007-05-31
I just browsed the repos using my browser.

Go here: [http://www.telemail.fi/mlind/ubuntu/pool/fonts/](http://www.telemail.fi/mlind/ubuntu/pool/fonts/)

Download these files from their respective folders:

libcairo2_1.4.6-1~turner1_i386.deb
libfreetype6_2.3.4-0mlind1_i386.deb
libxft2_2.1.12-2~turner1_i386.deb

---

### Post by EatenByGrues on 2007-05-31
Thanks for the clarification on the debs. Still no improvement for my 32 bit firefox though, any ideas?

I may be splitting hairs with this but what would cause these differences?

64 bit Firefox:
[IMG]http://i129.photobucket.com/albums/p235/eatenbygrues/64bit2.png[/IMG]

32 bit Firefox:
[IMG]http://i129.photobucket.com/albums/p235/eatenbygrues/32bit2.png[/IMG]

---

### Post by t_anjan on 2007-06-04
You have scaled down the images, so can't really make out any details from them.

Anyway, if you have 32 bit firefox installed, then your 64 bit firefox will also look like the 32b version. I guess the 32b version makes even the 64b version read the font info from the 32b libraries. 

So I think your 32b and 64b versions of Firefox should be looking the same.

BTW, were you asked to replace the old files? What I mean to ask is, do you know for a fact that you replaced the old files ?

---

### Post by Case_f on 2007-06-04
> **EatenByGrues said:**
> Thanks for the clarification on the debs. Still no improvement for my 32 bit firefox though, any ideas?

I may be splitting hairs with this but what would cause these differences?

64 bit Firefox:
[http://i129.photobucket.com/albums/p235/eatenbygrues/64bit2.png](http://i129.photobucket.com/albums/p235/eatenbygrues/64bit2.png)

32 bit Firefox:
[http://i129.photobucket.com/albums/p235/eatenbygrues/32bit2.png](http://i129.photobucket.com/albums/p235/eatenbygrues/32bit2.png)

Although the screenshots are indeed resized and there's not much detail, I think it's clear that you are using different fonts in 64bit Firefox as opposed to the 32bit one. The question is why? Are the font preferences set the same? (Although I think it should both use the same settings files, unless you run the 32bit Firefox in chroot, shouldn't it?)

---

### Post by Kilz on 2007-06-04
> **t_anjan said:**
> You have scaled down the images, so can't really make out any details from them.

**Anyway, if you have 32 bit firefox installed, then your 64 bit firefox will also look like the 32b version. I guess the 32b version makes even the 64b version read the font info from the 32b libraries. **

So I think your 32b and 64b versions of Firefox should be looking the same.

BTW, were you asked to replace the old files? What I mean to ask is, do you know for a fact that you replaced the old files ?

This is wrong. Installing the 32bit Firefox should not effect the 64bit version in any way shape or form. They share 0 files. They are in separate directories and those directories are in separate directories. The deb files do not have any libraries installed to other directories.
What is possible is that you had the 32bit version open, then opened the 64bit version without closing the 32bit one first. Whenever you open another instance of firefox with one open you open the one already open.

---

