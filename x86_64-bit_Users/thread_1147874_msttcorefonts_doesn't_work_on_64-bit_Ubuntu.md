---
title: "msttcorefonts doesn't work on 64-bit Ubuntu"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by gamblor01 on 2009-05-03
I am running Ubuntu 8.10 (i686) on my system and I am very happy with it.  I have been running Ubuntu (various versions) on a regular basis since 7.10 -- though I still boot up Fedora from time to time.  ;)

Today I decided to download the 9.04 amd64 iso and install it on my "test" partition.  Almost everything seems to be working fine, including, surprisingly, the alpha flashplayer10 for 64 bit.

What doesn't seem to work is the msttcorefonts package.  I installed it just like I did on the 32-bit version (sudo apt-get install msttcorefonts) which should automatically configure it for me as well.  However, I tried logging out and logging back in to gnome and the fonts didn't seem to take effect.  I then tried rebooting but still nothing.  I tried running "sudo fc-cache -fv" and then rebooted -- still nothing!

I don't appear to be the first person to discover this:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/960414.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/960414.html)


Anyone else having this problem?  If so, it looks like a bug report to Ubuntu might be in order.  I certainly won't be able to run the 64-bit version of this if I can't use the msttcorefonts package -- the default fonts just look too blurry and ugly to me.  :/

Anyone else had this issue and fixed it?  If so I would certainly appreciate knowing how you fixed it.  Thanks!

---

### Post by John.Michael.Kane on 2009-05-03
Unfortunately I am not able to reproduce the issue you have outlined.

Using 9.04, I simply installed msttcorefonts though synaptic, and then ran the below command.
```
sudo fc-cache -f -v
```

After which the fonts included with that package were readily available though System-->Preferences--->Appearance-->Fonts

---

### Post by Fir3chi3f on 2009-05-03
I tried installing the fonts and it looks like everything is working fine for me.

```
~$ sudo apt-get install msttcorefonts
[sudo] password for fir3chi3f: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ttf-mscorefonts-installer
The following NEW packages will be installed:
  msttcorefonts ttf-mscorefonts-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.2kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/multiverse ttf-mscorefonts-installer 2.6 [32.2kB]
Get:2 http://us.archive.ubuntu.com jaunty/multiverse msttcorefonts 2.6 [8030B]
Fetched 40.2kB in 0s (50.2kB/s)     
Preconfiguring packages ...
Selecting previously deselected package ttf-mscorefonts-installer.
(Reading database ... 109724 files and directories currently installed.)
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_2.6_all.deb) ...
Selecting previously deselected package msttcorefonts.
Unpacking msttcorefonts (from .../msttcorefonts_2.6_all.deb) ...
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-05-03 21:45:46--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/x-msdos-program]
Saving to: `./andale32.exe'

100%[======================================>] 198,384     42.9K/s   in 4.5s    

2009-05-03 21:45:51 (42.9 KB/s) - `./andale32.exe' saved [198384/198384]

--2009-05-03 21:45:51--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/x-msdos-program]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176     28.6K/s   in 5.5s    

2009-05-03 21:45:57 (30.1 KB/s) - `./arialb32.exe' saved [168176/168176]

--2009-05-03 21:45:57--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/x-msdos-program]
Saving to: `./arial32.exe'

100%[======================================>] 554,208     88.8K/s   in 6.5s    

2009-05-03 21:46:04 (83.0 KB/s) - `./arial32.exe' saved [554208/554208]

--2009-05-03 21:46:04--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/x-msdos-program]
Saving to: `./comic32.exe'

100%[======================================>] 246,008     87.7K/s   in 2.7s    

2009-05-03 21:46:07 (87.7 KB/s) - `./comic32.exe' saved [246008/246008]

--2009-05-03 21:46:07--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/x-msdos-program]
Saving to: `./courie32.exe'

100%[======================================>] 646,368      151K/s   in 4.8s    

2009-05-03 21:46:12 (132 KB/s) - `./courie32.exe' saved [646368/646368]

--2009-05-03 21:46:12--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/x-msdos-program]
Saving to: `./georgi32.exe'

100%[======================================>] 392,440     87.8K/s   in 6.9s    

2009-05-03 21:46:19 (55.2 KB/s) - `./georgi32.exe' saved [392440/392440]

--2009-05-03 21:46:19--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/x-msdos-program]
Saving to: `./impact32.exe'

100%[======================================>] 173,288     65.4K/s   in 2.6s    

2009-05-03 21:46:22 (65.4 KB/s) - `./impact32.exe' saved [173288/173288]

--2009-05-03 21:46:22--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/x-msdos-program]
Saving to: `./times32.exe'

100%[======================================>] 661,728      161K/s   in 4.5s    

2009-05-03 21:46:27 (143 KB/s) - `./times32.exe' saved [661728/661728]

--2009-05-03 21:46:27--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/x-msdos-program]
Saving to: `./trebuc32.exe'

100%[======================================>] 357,200      105K/s   in 3.3s    

2009-05-03 21:46:31 (105 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2009-05-03 21:46:31--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/x-msdos-program]
Saving to: `./verdan32.exe'

100%[======================================>] 351,992     92.6K/s   in 3.7s    

2009-05-03 21:46:35 (92.6 KB/s) - `./verdan32.exe' saved [351992/351992]

--2009-05-03 21:46:35--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/x-msdos-program]
Saving to: `./webdin32.exe'

100%[======================================>] 185,072     35.4K/s   in 5.1s    

2009-05-03 21:46:40 (35.4 KB/s) - `./webdin32.exe' saved [185072/185072]

andale32.exe: library not compiled to support large files.
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: library not compiled to support large files.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: library not compiled to support large files.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: library not compiled to support large files.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: library not compiled to support large files.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
georgi32.exe: library not compiled to support large files.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: library not compiled to support large files.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
times32.exe: library not compiled to support large files.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
trebuc32.exe: library not compiled to support large files.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
verdan32.exe: library not compiled to support large files.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
webdin32.exe: library not compiled to support large files.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up msttcorefonts (2.6) ...

```

Try reinstalling them and see if you get any errors back.

---

### Post by gamblor01 on 2009-05-03
My apologies -- it appears that I am indeed, an idiot.  I first took a screenshot from my "working" system (the 8.10 32-bit system) and then rebooted.  After booting into my new 9.04 64-bit partition I went to System -> Preferences -> Appearance -> Fonts.  I compared the picture to the default settings in 9.04...it looks like everything was installed properly but the defaults were different for 9.04 than they were in 8.10 (this likely has nothing to do with 32 vs. 64-bit).

It appears that in 8.10 the defaults after installing msttcorefonts are:

-Best Shapes
-Details
---> Grayscale
---> Medium
---> RGB


On 9.04 however, the defaults were:

-Subpixel Smoothing (LCD)
-Details
---> Subpixels (LCDs)
---> Slight
---> RGB


This could be something related to my system.  I'm guessing that in 9.04 there is some new code that (properly) detects my display as an LCD.  However, it unfortunately used that information to set the fonts in such a way that I was not pleased with.  It's just a hunch but it seems plausible.

In any case, I changed it from the default values to the values from my 8.10 and now everything looks exactly like I want it!  This is the first time I have ever really considered running with the amd64 arch as my main distro.  Looks like it might be time to make the switch!

---

### Post by Yellow Pasque on 2009-05-04
> My apologies -- it appears that I am indeed, an idiot.
No need to apologize. I thought Jaunty looked somewhat blurry as well and you provided the solution. Thank you.

---

### Post by gamblor01 on 2009-05-04
Cool, glad that this helped someone else!  And I'm glad I'm not the only one who thinks the default fonts are unreadable.  ;)

---

### Post by nucleuskore on 2009-05-05
> **gamblor01 said:**
> Cool, glad that this helped someone else!  And I'm glad I'm not the only one who thinks the default fonts are unreadable.  ;)

Have you tried Liberation fonts, these are a set of serif, sans-serif and monospaced fonts from Red Hat with exactly the same metrics as the (non-free) Microsoft Times, Arial and Courier fonts. Can be installed through Synaptic/apt.

---

### Post by Arup on 2009-05-05
> **nucleuskore said:**
> Have you tried Liberation fonts, these are a set of serif, sans-serif and monospaced fonts from Red Hat with exactly the same metrics as the (non-free) Microsoft Times, Arial and Courier fonts. Can be installed through Synaptic/apt.

Liberation fonts are installed by default in Jaunty.

---

### Post by nucleuskore on 2009-05-05
> **Arup said:**
> Liberation fonts are installed by default in Jaunty.

Ok I did not know, I use Intrepid.

[img]http://s269.photobucket.com/albums/jj44/visio159/Unismilies/34large.png[/img]

---

