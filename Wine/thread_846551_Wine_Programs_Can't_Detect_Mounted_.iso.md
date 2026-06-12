---
title: "Wine Programs Can't Detect Mounted .iso"
date: 2008-07-01
forum: Wine
---

### Post by azurepancake on 2008-07-01
I've recently downloaded the program 'Rebirth RB-338' which is a synthesizer program normally ran on Windows. I've had the desire to run it with Wine, so I downloaded the .iso file from their website. The .iso is called 'rebirth.iso'.

So I type the following command to mount rebirth.iso to the '/media/rebirth' directory..

```
sudo mount -o loop ~/rebirth.iso /media/rebirth
```

The file mounts with no problems to the /media/rebirth directory. Using the CLI I can navigate to it and run the .exe installation file..

```
wine /media/rebirth/"Install ReBirth RB-338.EXE"
```

The program installs with no problems to it's default directory. A shortcut is put on my desktop.

Now, with the rebirth.iso file still mounted to /media/rebirth - I click on the icon. The application begins to start and prompts me with the following message..

```
Please insert the ReBirth RB-338 2.0 CD. Waiting for CD...
```

Am I doing something wrong here? I opened up winecfg and clicked on the 'Drives' tab and added drive G: as /media/rebirth to see if it worked, but no cigar.

I've tried this with other programs that are supposed to run with a .iso file as well, but they don't work either. If anyone can offer any kind of advice - I will greatly appreciate it.

Thank you.

---

### Post by cogadh on 2008-07-01
I think you need to add the isos mount point as a drive before you install it. Otherwise, just burn it to a CD and run it normally.

---

### Post by azurepancake on 2008-07-01
> **cogadh said:**
> I think you need to add the isos mount point as a drive before you install it. Otherwise, just burn it to a CD and run it normally.

Just gave that a shot and unfortunately no luck. I'll just burn it onto a CD then, thanks a lot for the advice.

---

### Post by kahlil88 on 2008-08-05
Burning the .iso is the easy way (assuming there are no copy-protect issues), but I like to take the more clever approach. I mount my disc images to **/mnt/iso**, and I added this as a CD-ROM mount point in Wine Config, and I think the problem *might* be that Wine can't yet autodetect the serial and label. Any ideas?

---

### Post by viktor4124 on 2008-09-20
I just posted the following answer to another post. Maybe it'll help you too.
Repost:

Hey,

I had a similar problem recently, which was solved the following way. Let's hope it will work for you too:

Wine manages a directory $HOME/.wine/dosdevices where symbolic links for mapping Windows-drives to locations in your filesystem are held. Just enter the directory in a terminal and examine it yourself (ls -l command).

There are links that have one colon (e.g. E:) which are refering to the mapping directory in your filesystem, and there drive-letters followed by two colons, which are used to point to a actual physical device (e.g. D: -> /dev/cdrom).
So I not only tried to loop-mount my iso and bind it to drive E:, but also to bind the "physical drive" E:: to the iso itself, so that the windows software may find the cd's serial and stuff. And guess what, it worked ;-) at least for me

```

$ sudo mount -o loop /home/viktor/image.iso /mnt/iso
$ cd $HOME/.wine/dosdevices
$ ln -s /mnt/iso e:
$ ln -s /home/viktor/image.iso e::
$ wine explorer

```

unfortunately I somehow couldn't start the software with
```

wine /mnt/iso/setup.exe

```
I had' to use wine explorer, navigate to drive E: and start setup.exe by double-clicking it.

good luck.

---

### Post by ^rooker on 2008-11-11
Thanks viktor!
This solved my problem.

Some thing however keeps puzzling me: On my old system, I didn't have to mount the ISO and it worked properly. 
In fact, the "D::" symlink could even point to an invalid drive or not exist at all. Only on my newly installed Ubuntu, I've had to link the ISO.

I think it's also related to wine not storing label/serial information properly (winecfg displays an empty value if you re-open it)

---

### Post by opensourcefan on 2009-01-07
hi viktor4124,
thank you very much for your input. it worked for me too, even on freebsd.
before i've read your posting i was googling for hours and experimenting quite much, but with no success.
after reading your posting it worked immediately! 

kind regards,
osf

---

### Post by jcb081584 on 2009-05-15
I tried this method and -o is not an option it says.  It gives me a long list of options and what they do but -o is not there and I can't think that any of the others would be useful for what I need it to do.  Anything else I can try?  I've also tried mounting in Gmount-iso and Wine still can't recognize the drive even if I refresh the drive listings in the settings.  Thanks in advance.

---

### Post by indigocat on 2011-10-01
Detail:

ln -s ~/...path-to-rebirth*.iso driveletter::

Here's a little tutorial:

[http://createdigitalmusic.com/2010/10/how-to-install-rebirth-in-linux-get-a-free-rack-of-beat-machines/](http://createdigitalmusic.com/2010/10/how-to-install-rebirth-in-linux-get-a-free-rack-of-beat-machines/)

Worked like a charm.

---

### Post by nc_jed on 2011-12-24
> **indigocat said:**
> detail:

Ln -s ~/...path-to-rebirth*.iso driveletter::

Here's a little tutorial:

[http://createdigitalmusic.com/2010/10/how-to-install-rebirth-in-linux-get-a-free-rack-of-beat-machines/](http://createdigitalmusic.com/2010/10/how-to-install-rebirth-in-linux-get-a-free-rack-of-beat-machines/)

worked like a charm.

+2 !

---

### Post by polarcheese on 2012-03-15
This didn't work for me, I followed all the instructions here.

Here is what comes up when I type ls -l while in ~/.wine/dosdevices

```
lrwxrwxrwx 1 david david 14 2012-03-15 13:40 a: -> /media/floppy0
lrwxrwxrwx 1 david david  8 2012-03-15 13:40 b:: -> /dev/fd0
lrwxrwxrwx 1 david david 10 2012-03-15 13:21 c: -> ../drive_c
lrwxrwxrwx 1 david david 14 2012-03-15 13:41 e: -> /media/rebirth
lrwxrwxrwx 1 david david 10 2012-03-15 13:21 e:: -> /dev/loop0
lrwxrwxrwx 1 david david 11 2012-03-15 13:40 h: -> /home/david
lrwxrwxrwx 1 david david  1 2012-03-15 13:21 z: -> /
```

rebirth installed fine, but I still get the waiting for cd message when I start it up.

thanks a lot

---

### Post by Toz on 2012-03-17
Hello and welcome to the forums polarcheese.

Try removing the /dev/loop0 entry and linking directly to the iso:
```

rm ~/.wine/dosdevices/e\:\:
ln -s /path/to/rebirth.iso ~/.wine/dosdevices/e\:\:

```

---

### Post by polarcheese on 2012-03-20
Thanks for the reply, I tried your fix, but unfortunately I still get the same error about needing the cd. 

when I type ls -l while in ~/.wine/dosdevices now this is what it looks like:
```

lrwxrwxrwx 1 david david 14 2012-03-15 13:40 a: -> /media/floppy0
lrwxrwxrwx 1 david david  8 2012-03-15 13:40 b:: -> /dev/fd0
lrwxrwxrwx 1 david david 10 2012-03-15 13:21 c: -> ../drive_c
lrwxrwxrwx 1 david david  8 2012-03-15 18:13 d:: -> /dev/sr0
lrwxrwxrwx 1 david david 14 2012-03-15 13:41 e: -> /media/rebirth
[COLOR=Red]lrwxrwxrwx 1 david david 20 2012-03-20 12:56 e:: -> /path/to/rebirth.iso[/COLOR]
lrwxrwxrwx 1 david david 14 2012-03-20 12:57 f: -> /media/rebirth
lrwxrwxrwx 1 david david 10 2012-03-20 12:57 f:: -> /dev/loop0
lrwxrwxrwx 1 david david 11 2012-03-15 13:40 h: -> /home/david
lrwxrwxrwx 1 david david  1 2012-03-15 13:21 z: -> /
``` The line highlighted in red above is also red in the terminal. 

If it helps I'm running ubuntu 11.10 with wine 1.4 rc2 

thanks again.

---

### Post by Toz on 2012-03-20
> lrwxrwxrwx 1 david david 20 2012-03-20 12:56 e:: -> /path/to/rebirth.iso

You need to change "/path/to" to be the actual path to the iso file. So, if your iso file is in your home directory and it is called rebirth.iso, it should read:
```
lrwxrwxrwx 1 david david 20 2012-03-20 12:56 e:: -> /home/david/rebirth.iso
```

---

### Post by polarcheese on 2012-03-20
Thanks so much, that was really silly of me. 

how would I change the path now that I have already linked it to the wrong place? Do I need to remove the old link?

thanks again

---

### Post by Toz on 2012-03-20
Yes, remove the existing link:
```
rm ~/.wine/dosdevices/e\:\:
```

---

### Post by polarcheese on 2012-03-21
Unfortunately that has still not solved the problem, when I type ls -l I now see:

```
lrwxrwxrwx 1 david david 14 2012-03-15 13:40 a: -> /media/floppy0
lrwxrwxrwx 1 david david  8 2012-03-15 13:40 b:: -> /dev/fd0
lrwxrwxrwx 1 david david 10 2012-03-15 13:21 c: -> ../drive_c
lrwxrwxrwx 1 david david  8 2012-03-15 18:13 d:: -> /dev/sr0
lrwxrwxrwx 1 david david 14 2012-03-15 13:41 e: -> /media/rebirth
[COLOR=Red]lrwxrwxrwx 1 david david 50 2012-03-21 10:34 e:: -> /home/david/downloads/rebirth_iso_installation.iso[/COLOR]
lrwxrwxrwx 1 david david 14 2012-03-20 12:57 f: -> /media/rebirth
lrwxrwxrwx 1 david david 10 2012-03-20 12:57 f:: -> /dev/loop0
lrwxrwxrwx 1 david david 11 2012-03-15 13:40 h: -> /home/david
lrwxrwxrwx 1 david david  1 2012-03-15 13:21 z: -> /
```

---

### Post by Toz on 2012-03-21
Hmmmm. Try removing the 2 f: drive links. Maybe they're interfering:
```

rm ~/.wine/dosdevices/f\:
rm ~/.wine/dosdevices/f\:\:
```

Also, what command/how are you starting the installation process?

---

### Post by polarcheese on 2012-03-21
Still no luck.

To start the program I'm double clicking the desktop icon created during installation.

---

### Post by Toz on 2012-03-21
> **polarcheese said:**
> Still no luck.

To start the program I'm double clicking the desktop icon created during installation.

Instead, try running the installation program like this:
```

wine "f:\Setup.exe"
```
...assuming that Setup.exe is the name of the installation setup file.

---

