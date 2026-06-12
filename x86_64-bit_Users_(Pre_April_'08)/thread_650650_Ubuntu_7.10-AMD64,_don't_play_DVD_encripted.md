---
title: "Ubuntu 7.10-AMD64, don't play DVD encripted"
date: 2007-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by javaCachaca on 2007-12-26
Hi,
  I have a Ubuntu 7.10-AMD64 installed in my notebook.
  Well, 
    I can't play my DVDs(Encrypted DVD) of Power Ranger's.
    I follow this steps: [https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3](https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3) but I don't have success.

   I receive this log messages when I try play the DVD with VLC and Totem players:

**VLC: **

```

vlc -v
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Power Rangers Dino Thunder
libdvdnav: DVD Serial Number: 32ed7818
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/leandro/.dvdnav/Power Rangers Dino Thunder.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000224
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000224)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00010db0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00010db0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00325343
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003254d8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003254d8)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0032565e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x0032565e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00325701
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00325856
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x00325856)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003258f9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0032672b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003267ce
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003267ce)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00326883
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00326926
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00326926)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00326acf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00326b72
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00326b72)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00336c29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00336ccc
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x00336ccc)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0037a8a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x0037a8a0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0037a943
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 1

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```

**Totem: **

```

totem
libdvdnav: Using dvdnav version 1.1.8 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/leandro/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014f
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000224
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000224)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00010db0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00010db0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00325343
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003254d8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003254d8)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0032565e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x0032565e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00325701
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00325856
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x00325856)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003258f9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0032672b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003267ce
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003267ce)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00326883
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00326926
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00326926)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00326acf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00326b72
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00326b72)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00336c29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00336ccc
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x00336ccc)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0037a8a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x0037a8a0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0037a943
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 2
demux_wavpack: (open_wv_file:129) open_wv_file: non-seekable inputs aren't supported yet.
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
libdvdnav: Using dvdnav version 1.1.8 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/leandro/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000224
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000224)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00010db0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00010db0)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00325343
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003254d8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003254d8)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0032565e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x0032565e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00325701
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00325856
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x00325856)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003258f9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0032672b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003267ce
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003267ce)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00326883
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00326926
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00326926)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00326acf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00326b72
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00326b72)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00336c29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00336ccc
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x00336ccc)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0037a8a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x0037a8a0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0037a943
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 1
demux_wavpack: (open_wv_file:129) open_wv_file: non-seekable inputs aren't supported yet. 

```
  
Please, help-me. 
I need of my Power Ranger's Exercices.

---

### Post by Prospero2006 on 2007-12-26
Try the VLC Media Player.

Power Rangers Ho!

---

### Post by Kilz on 2007-12-26
> **javaCachaca said:**
> Hi,
  I have a Ubuntu 7.10-AMD64 installed in my notebook.
  Well, 
    I can't play my DVDs(Encrypted DVD) of Power Ranger's.
    I follow this steps: [https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3](https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3) but I don't have success.

   I receive this log messages when I try play the DVD with VLC and Totem players:

**VLC: **

  
Please, help-me. 
I need of my Power Ranger's Exercices.

The old ways sometimes are the best. Open a terminal and copy/past in these commands.
```

sudo apt-get install libdvdread3
```
then
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by javaCachaca on 2007-12-27
I did this, but no success.
I'm crazy with this problem.

---

### Post by BreathEasy on 2007-12-27
It's pretty simple. Open a terminal, type in the following line:

**sudo gedit /etc/apt/sources.list**

When the editor opens, enter the following line at the bottom:

**deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free**

Save the file and quit the editor. Now type in at the terminal:

**sudo apt-get update**

When it's done, type in

**sudo apt-get install libdvdcss2**

Run VLC, DVDs should now work.

---

### Post by Kilz on 2007-12-27
> **javaCachaca said:**
> I did this, but no success.
I'm crazy with this problem.

Do other DVD's work?

---

### Post by javaCachaca on 2007-12-27
Other DVD (not encrypted) work's fine. The problem is with encrypted DVD.

---

### Post by LowSky on 2007-12-27
I'm quoting myself here...lol from this thread

[http://ubuntuforums.org/newreply.php?do=newreply&p=4023043](http://ubuntuforums.org/newreply.php?do=newreply&p=4023043)

This should get all your codec fixed

Below are the instructions to add the Medibuntu repository to your system's list of APT repositories for Gusty if you need Fiesty look here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

Then, add the GPG Key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

then reinstall lidvdcss2
```
sudo apt-get install libdvdcss2

```

then install w64codecs
```
sudo apt-get install w64codecs

```

Then restart the machine

---

### Post by Kilz on 2007-12-27
> **javaCachaca said:**
> Other DVD (not encrypted) work's fine. The problem is with encrypted DVD.

The reason I ask is that some DVD's will not play. I know ones from Disney dont. So you have tried a few different dvd's you have?

---

### Post by motorheadabega on 2007-12-27
I was having the same problem. Howerver, after setting DVDCSS_VERBOSE=2 and running vlc again, It suggested that the problem was region related. Another thread suggested the following:

sudo apt-get install regionset
regionset

The Region Code was not previously set on my DVD drive. Setting it to my region (1) got all my encrypted DVDs playing fine.

This was never a problem for me before, so I'm speculating that this is new behaviour from libdvdcss.

hope it helps.
motorhead.

---

### Post by javaCachaca on 2007-12-27
> **motorheadabega said:**
> I was having the same problem. Howerver, after setting DVDCSS_VERBOSE=2 and running vlc again, It suggested that the problem was region related. Another thread suggested the following:

sudo apt-get install regionset
regionset

The Region Code was not previously set on my DVD  madrive. Setting it to my region (1) got all my encrypted DVDs playing fine.

This was never a problem for me before, so I'm speculating that this is new behaviour from libdvdcss.

hope it helps.
motorhead.

Hey man !, how to set DVDCSS_VERBOSE=2 ? how a environment variable ?

#-o

---

### Post by faffmeister on 2008-01-07
You may already have found this but have a look at the section: 

"Setting DVD Region Codes"

in: 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

This might help you set your region code.

---

