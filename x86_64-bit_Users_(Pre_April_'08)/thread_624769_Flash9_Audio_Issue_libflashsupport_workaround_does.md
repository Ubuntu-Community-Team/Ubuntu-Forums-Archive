---
title: "Flash9 Audio Issue: libflashsupport workaround does not work on Gutsy amd64"
date: 2007-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Master One on 2007-11-27
I was playing around with it the whole afternoon, but it's definitely not working. I tried several different ideas on how to get audio working for flash9 content, but still nothing.

The explanations found on the net and ubuntuforums are all about libflashsupport on a Gutsy i386 installation, but he workaround with libflashsupport just does not seem to be working on amd64 architecture.

BTW I am running Edubuntu Gutsy with LTSP5 setup, the audio gets to the thin clients by pulseaudio, so it's about getting flash9 to somehow work with a virtual alsa device.

---

### Post by squirage on 2007-11-27
Hi,

  I don't have a solution but I just wanted to chime in about how much this problem sucks. I had more or less fixed all of my audio issues in Feisty but upon upgrading to gutsy I am back to having no audio whatsoever.

  I also don't understand why the latest releases of firefox, 2.0.0.8 and 2.0.0.10, still have issues with flash. For me Youtube either doesn't play or crashes firefox altogether.

  I won't even go into how the linux version of FF makes some pages display horribly. I am really puzzled as to why it would work better on the MS platform than on linux.

  I am not opposed to working out system specific tweeks, but I am getting pretty irritated by the amount of 2 to 3 year old bugs that persist and none of the "fixes" seem to work.

Sorry for the rant.

---

### Post by Tuxi on 2007-11-27
I have flash 9 working just fine in kubuntu 7.10.  

1) Remove the plugin that's not working.

2) install nspluginwrapper
 ```
sudo apt-get install nspluginwrapper
```

3) download flashplayer 9 for linux and untar
```
tar xzvf install_flahsplayer_9_linux.tar.gz
```

4) in the directory from which you untarred flashplayer 9 execute 
```
nspluginwrapper -i install_flash_player_9_linux/libflashplayer.so

```

This will put the plugin in your .mozilla/plugins directory and should work just fine.

---

### Post by Martin Braure de Calignon on 2008-01-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/180008](https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/180008) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				see [http://jean-christophe.dubacq.fr/index.php?post/2007/07/17/adobe-on-amd64-without-chroot-acrobat-flash](http://jean-christophe.dubacq.fr/index.php?post/2007/07/17/adobe-on-amd64-without-chroot-acrobat-flash) for a solution with pulseaudio

---

### Post by Yellow Pasque on 2008-01-04
Compile the file from scratch.
Get the .c file here: [http://www.kaourantin.net/flashplayer/flashsupport.c](http://www.kaourantin.net/flashplayer/flashsupport.c)
Get necessary packages
```
sudo apt-get install gcc gcc-4.1 gcc-4.1-base gcc-4.1-multilib make build-essential binutils linux-headers-`uname -r`
```
Open the file with a text editor (and root access) and comment out the #define OPENSSL line by putting two '/'s' in front of it. Make sure #define OSS does not have anything in front of it (if you're just using ALSA, you shouldn't need this file at all). Save and close. Navigate to the directory where you have the file.

Compilation step. Note the -m32 flag, because we're building for the 32-bit Flash plugin. This works because of the gcc-multilib package, no chroot is necessary. :)
```
sudo cc -shared -O2 -Wall -Werror -m32 flashsupport.c -o libflashsupport.so
sudo cp libflashsupport.so /usr/lib
```

Create symbolic links in /usr/lib/firefox/plugins & /usr/lib/mozilla/plugins:
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```

---

### Post by Nuke Skyjumper on 2008-01-05
You might also want to look at [http://ubuntuforums.org/showthread.php?t=655825](http://ubuntuforums.org/showthread.php?t=655825)

Should be an easy drop-in solution.

Good Luck

---

