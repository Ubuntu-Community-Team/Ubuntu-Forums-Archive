---
title: "Intrepid Update Hoses X"
date: 2008-11-14
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2008-11-14
I have a desktop computer with nVidia GeForce 6150 and a Samsung SyncMaster 206BW monitor, both of which used to run just fine in Hardy at 1680 x 1050 using the nvidia-glx-new driver. After upgrading to Intrepid I was not able to get better than 1024 x 768 (VESA). I kept trying different things based on posts I found here in the forums, and everything I did made things worse. Right now the best I can get is 800 x 600 and the keyboard and mouse are dead; or I can boot to Recovery mode > Root terminal and get at least the keyboard working. However, I can't do much because the network is also dead. I would reinstall from scratch but there are several dozen programs installed on the computer and in Virtualbox guest OSs - reinstalling them would take at least eight hours of work. Besides, fixing the broken installation is more educational. :(

A large part of my problem is that when I search the forums I find all kinds of posts about this problem, but none of the posters ever say if they are using 32-bit or 64-bit Intrepid. Thus, I can't be sure they advice they suggest is correct. Therefore, I have decided to post my problem here in the 64-bit forum in the hopes that someone can tell me what to do to fix my broken 64-bit desktop computer.

---

### Post by inobe on 2008-11-14
your xserver is hosed bad !

might try to reconfigure it, i hope this helps.

```
sudo dpkg-reconfigure xserver-xorg
```

do that and reboot

---

### Post by John Jason Jordan on 2008-11-14
> **inobe said:**
> your xserver is hosed bad !

might try to reconfigure it, i hope this helps.

```
sudo dpkg-reconfigure xserver-xorg
```

do that and reboot

I already tried that earlier, but I tried it again just now and still no luck. If I boot to the normal Grub menu option it comes up in 800 x 600 but the mouse and keyboard are dead. If I boot in recovery mode I can get the keyboard at the command line. But the network is also dead, so the command line doesn't help me fix anything.

Thanks for the suggestion, though.

---

### Post by inobe on 2008-11-14
```
gksudo gedit /etc/X11/xorg.conf
```

see if that brings up org, i am wondering if you may have a working backup in there ?

edit: the purpose of that command is to open your xorg.conf in hopes that you can overwrite it with a backup in /X11, if you have one !

---

### Post by John Jason Jordan on 2008-11-15
> **inobe said:**
> ```
gksudo gedit /etc/X11/xorg.conf
```

see if that brings up org, i am wondering if you may have a working backup in there ?

First, I cannot do anything in the GUI. Remember, I said that if I boot to the regular Grub boot option X comes up at 800 x 600, but the mouse and keyboard are dead. The only way I can boot is to the Recovery mode "Drop to root shell prompt."

From the root shell prompt I find numerous versions of xorg.conf. All appear to be backups made when I tried to use -reconfigure to fix the X server. I know none of these will work because I wouldn't have changed them if they were working. However, there are three possibilities:

xorg.conf.backup
xorg.conf.dist-upgrade-200811132004
xorg.conf.failsafe

I renamed xorg.conf to xorg.conf.myold, then renamed each one of the above in turn to xorg.conf and tried to boot. No go. Each time when I boot to the first Grub boot menu X comes up but the keyboard and mouse are dead.

The problem is more than the fact that X is hosed. The new X.org thing that Intrepid is using moved the mouse and keyboard out of xorg.conf into someplace else. I don't know where "someplace else" is, and wherever it is, it is not working. 

I should add that the mouse and the keyboard are both Logitech USB wireless devices. And I don't have any wired keyboards or mice to try for troubleshooting.

If I can just get the mouse and keyboard working in the GUI!

---

### Post by inobe on 2008-11-15
i fell your pain and don't know if its possible getting them to work considering they don't work at all.

if you still have a possibly working conf file' have you ever done

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

i am running out of ideas, i only have a few left.

one being grab a cheap mouse and keboard at wallmart for 10 bucks, this will at least help you navigate, you can also modify your current org to get a higher resolution.

---

### Post by John Jason Jordan on 2008-11-15
> **inobe said:**
> i fell your pain and don't know if its possible getting them to work considering they don't work at all.

if you still have a possibly working conf file' have you ever done

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

i am running out of ideas, i only have a few left.

one being grab a cheap mouse and keboard at wallmart for 10 bucks, this will at least help you navigate, you can also modify your current org to get a higher resolution.

OK, borrowed a PS/2 keyboard and mouse from a neighbor. Still dead if I boot to the normal GUI. So the problem is not that the keyboard and mouse are USB devices. Something more fundamental is wrong. I need to find out where the mouse and keyboard went after they were moved out of xorg.conf.

---

### Post by inobe on 2008-11-15
okay, looks like we need to reinstall xserver !

the problem, no network.........

this command would have done this

makes a backup of source list

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
```



```
sudo apt-cdrom add
sudo apt-get install --reinstall xserver-xorg
```

tell us about your connection ?

edit: source backup command and apt cdrom added

this is strictly experimental, i have no idea what the ramifications are, i would wait for other suggestions before attemping.

good luck :)

---

### Post by John Jason Jordan on 2008-11-15
> **inobe said:**
> okay, looks like we need to reinstall xserver !

the problem, no network.........

this command would have done this

makes a backup of source list

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
```



```
sudo apt-cdrom add
sudo apt-get install --reinstall xserver-xorg
```

tell us about your connection ?

edit: source backup command and apt cdrom added

this is strictly experimental, i have no idea what the ramifications are, i would wait for other suggestions before attemping.

good luck :)

OK, I am currently downloading the Alternate install CD-ROM to my laptop (which is still running fine with Hardy). After it downloads I will burn it, then put it in the CD drive on the broken desktop and see if I can use it to reinstall xserver with the above syntax. Please keep your fingers crossed for me. :)

---

### Post by inobe on 2008-11-15
you may want to include the type of connection you are using, this will at least help us to understand why your connection isn't working in root shell.

---

### Post by John Jason Jordan on 2008-11-15
> **inobe said:**
> you may want to include the type of connection you are using, this will at least help us to understand why your connection isn't working in root shell.

The network interface is:

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

My home network is cable, connected to a router whose address is 196.168.0.1. All connections are wired ethernet (wired in the walls). I do not have home wireless network; it's all ethernet.

---

### Post by John Jason Jordan on 2008-11-15
> **inobe said:**
> okay, looks like we need to reinstall xserver !


```
sudo apt-cdrom add
sudo apt-get install --reinstall xserver-xorg
```


Sadly, this did not work:

root@Devil6:~# sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for discs ...
Please insert a Disc in the drive and press enter
Mounting CD-ROM
modprobe: FATAL: Could no load /lib/modules/2/6/24-19-generic/modules.dep: No such file or directory
modprobe: FATAL: Could no load /lib/modules/2/6/24-19-generic/modules.dep: No such file or directory
E: Failed to mount the cdrom.

I copied that over by hand so I hope there are no typos.

The problem may lie in the fact that the desktop computer has two identical DVD drives.

---

### Post by inobe on 2008-11-15
at this point i would use the live cd and mount that drive to grab important data.

thats all i have, ran out of ideas

we tried:)

---

### Post by John Jason Jordan on 2008-11-15
> **inobe said:**
> at this point i would use the live cd and mount that drive to grab important data.

thats all i have, ran out of ideas

we tried:)

Thanks for the suggestions. Maybe someone else can add some ideas.

---

### Post by tenmoi on 2008-11-15
I am running ibex 64 upgraded from 8.04. no problem. 

I don't think you can reinstall from a cd because the cdrom file versions may not be as uptodate as those on your current system.

but I suggest you mount the iso file then try apt-cd'ing it. Your burned cd may be corrupt.

1. sudo apt-cdrom add

Open a new terminal and
2. sudo mount -t iso9660 /path to your iso /media/cdrom

Now return to step 1 and hit enter

3. sudo apt-get install --reinstall xserver-xorg

Post back if you encounter any more errors.

---

### Post by John Jason Jordan on 2008-11-15
> **tenmoi said:**
> I am running ibex 64 upgraded from 8.04. no problem. 
I don't think you can reinstall from a cd because the cdrom file versions may not be as uptodate as those on your current system.
but I suggest you mount the iso file then try apt-cd'ing it. Your burned cd may be corrupt.

1. sudo apt-cdrom add

Open a new terminal and
2. sudo mount -t iso9660 /path to your iso /media/cdrom

Now return to step 1 and hit enter

3. sudo apt-get install --reinstall xserver-xorg

Post back if you encounter any more errors.

I can't open a second terminal because I have no GUI. All I can do is boot to Recovery mode and then to a root prompt, or if I boot to the GUI I can shell to a command line and then use Ctrl-Alt-F1 to shell. The login window won't accept keyboard inputs, so I can't log in via the GUI. I am stuck unless there is a way to create a second terminal without the GUI.

Additional stuff:

As I noted previously, the GUI does not accept keystrokes, nor does the mouse work. Well, I found this on the Intrepid Release Notes page: sudo dpkg-reconfigure console-setup. Indeed, it seemed to work from the command line where the keyboard is working. It even recognized the keyboard (Logitech EX110). But after going through the console setup I still have no keyboard in the GUI. When the login screen comes up it won't accept keystrokes, with the exception of Ctrl-Alt-F1.

More stuff:
I think I misunderstood the use of the Alternate x86_64 CD that I burned. I downloaded the ISO and then burned the image to a CD as one always does when making a bootable CD. And, indeed, it will boot to the Alternate CD. But then it occured to me that I should have just copied the ISO file to the CD. But when I tried it I still couldn't mount the CD from the command line.

---

### Post by tenmoi on 2008-11-15
> **John Jason Jordan said:**
> I can't open a second terminal because I have no GUI. All I can do is boot to Recovery mode and then to a root prompt, or if I boot to the GUI I can shell to a command line and then use Ctrl-Alt-F1 to shell. The login window won't accept keyboard inputs, so I can't log in via the GUI. I am stuck unless there is a way to create a second terminal without the GUI.

Additional stuff:

As I noted previously, the GUI does not accept keystrokes, nor does the mouse work. Well, I found this on the Intrepid Release Notes page: sudo dpkg-reconfigure console-setup. Indeed, it seemed to work from the command line where the keyboard is working. It even recognized the keyboard (Logitech EX110). But after going through the console setup I still have no keyboard in the GUI. When the login screen comes up it won't accept keystrokes, with the exception of Ctrl-Alt-F1.

More stuff:
I think I misunderstood the use of the Alternate x86_64 CD that I burned. I downloaded the ISO and then burned the image to a CD as one always does when making a bootable CD. And, indeed, it will boot to the Alternate CD. But then it occured to me that I should have just copied the ISO file to the CD. But when I tried it I still couldn't mount the CD from the command line.

Ok. So you can do a normal boot then contrl-shift-f1. 
so your Alternate Ubuntu Cd is without defects, isn't it?
now suppose you have just done Contrl+SHift+f+F1, then you can do a COntrl+shift+f2 to get another console and do a 'mount -t iso9660 /dev/cdrom /media/cdrom'. if it should spit out an error, you can add '-o loop' to the end of the mount command above. To switch between consoles you can alternate the Alt+fx, with x being replaced with 1 or 2.

P.S
Use the bootable Alternate Cd.
and if you have nothing to risk you can sudo apt-get --reinstall ubuntu-desktop.

---

### Post by John Jason Jordan on 2008-11-15
> **tenmoi said:**
> Ok. So you can do a normal boot then contrl-shift-f1. 
so your Alternate Ubuntu Cd is without defects, isn't it?
now suppose you have just done Contrl+SHift+f+F1, then you can do a COntrl+shift+f2 to get another console and do a 'mount -t iso9660 /dev/cdrom /media/cdrom'. if it should spit out an error, you can add '-o loop' to the end of the mount command above. To switch between consoles you can alternate the Alt+fx, with x being replaced with 1 or 2.

P.S
Use the bootable Alternate Cd.

Thanks. I'll try that later. But I just discovered something else that may be the entire source of the problem. I posted it here just a few minutes ago:

[http://ubuntuforums.org/showthread.php?t=983486]("http://ubuntuforums.org/showthread.php?t=983486")

---

### Post by 081105jk on 2008-11-16
&#22240;&#20026;&#19987;&#19994;&#25152;&#20197;&#31934;&#36890;&#65292;&#22240;&#20026;&#31934;&#36890;&#25152;&#20197;&#26356;&#19987;&#19994;&#12290;&#20027;&#35201;&#39033;&#30446;&#26377;:&#21271;&#20140;&#31649;&#36947;&#30095;&#36890;&#65292;&#30095;&#36890;&#31649;&#36947;&#65292;[**&#30095;&#36890;&#39532;&#26742;**](http://www.bjjjjgd.cn/stmt.htm)&#30095;&#36890;&#65292;&#19979;&#27700;&#36947;&#30095;&#36890;&#65292;&#30095;&#36890;&#19979;&#27700;&#36947;&#65292;[**&#30095;&#36890;&#39532;&#26742;**](http://www.bjjjjgd.cn/stmt.htm)&#39640;&#21387;&#28165;&#27927;&#65292;&#39640;&#21387;&#27700;&#23556;&#27969;&#28165;&#27927;&#65292;&#39640;&#21387;&#28165;&#27927;&#31649;&#36947;,&#20462;&#29702;&#39532;&#26742;,&#20462;&#29702;&#19979;&#27700;&#36947;,&#28165;&#27927;&#31649;&#36947;,&#28165;&#27927;,&#38450;&#27700;,&#22581;&#28431;,&#38450;&#27700;&#22581;&#28431;                                                                     &#12288;&#12288; A&#12289;&#21270;&#23398;&#28165;&#27927;                         [**&#30095;&#36890;&#39532;&#26742;**](http://www.bjjjjgd.cn/stmt.htm)&#21270;&#23398;&#28165;&#27927;&#26159;&#37319;&#29992;&#21270;&#23398;&#33647;&#21058;&#21644;&#19968;&#23450;&#30340;&#24037;&#33402;&#25163;&#27573;&#23545;&#24037;&#19994;&#35774;&#22791;[**&#30095;&#36890;&#19979;&#27700;&#36947;**](http://www.bjjjjgd.cn/stxsd.htm)&#12289;&#31649;&#36947;&#23481;&#22120;&#31561;&#36827;&#34892;&#38500;&#27833;&#12289;&#38500;&#38152;&#38500;&#22434;&#12289;&#38500;&#28966;&#30899;&#31561;&#28165;&#27927;&#36807;&#31243;&#12290;&#20013;&#25299;&#31649;&#28165;&#27927;&#24037;&#31243;&#20844;&#21496;&#20174;&#20107;&#27833;&#30000;&#27880;&#27700;&#31649;&#32593;&#30340;&#21270;&#23398;&#28165;&#27927;&#12289;&#31934;&#39311;&#22612;&#38500;&#28966;&#28845;&#28165;&#27927;&#12289;&#38271;&#36755;&#31649;&#32447;&#27833;&#25913;&#27668;&#21270;&#23398;&#28165;&#27927;&#12289;[**&#30095;&#36890;&#19979;&#27700;&#36947;**](http://www.bjjjjgd.cn/stxsd.htm)&#24037;&#19994;&#35774;&#22791;&#24320;&#36710;&#21069;&#28165;&#27927;&#31561;&#22810;&#31181;&#21270;&#23398;&#28165;&#27927;&#39033;&#30446;&#65292;&#24182;&#30740;&#21046;&#20986;H2S&#25233;&#21046;&#21058;&#12289;&#22810;&#21151;&#33021;&#32531;&#34432;&#21058;&#12289;WQ&#20004;&#30456;&#22411;&#21407;&#27833;&#28165;&#27927;&#21058;&#31561;&#28165;&#27927;&#20135;&#21697;&#65292;&#33021;&#22815;&#38024;&#23545;&#19981;&#21516;&#30340;&#35774;&#22791;&#12289;&#31649;&#36947;&#21046;&#23450;&#30456;&#24212;&#30340;&#25216;&#26415;&#26045;&#24037;&#26041;&#26696;&#65292;&#36798;&#21040;&#26368;&#22909;&#30340;&#28165;&#27927;&#25928;&#26524;&#12290;

---

