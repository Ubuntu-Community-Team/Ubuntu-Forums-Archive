---
title: "Can't install Ubuntu [64bit] on Acer Aspire 5000"
date: 2006-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by komputes on 2006-06-23
:(  I really wanted to start using Ubuntu but here I am back on windows because the install did not work.

I downloaded Ubuntu 6.06, burned the .iso and rebooted and got booted into linux with a small hard drive icon saying install. First time, that would not open so I restarted again, this time i double clicked on the hard drive and put in my name and all and then it froze gain. I restarted. I double clicked on this hard drive icon once again and it finally gave me the chance to partition my drive. I made a 512mb swap and a 10gb ext3, then I was sure it was going to install. It satyed on the Installing... 0% screen all night.

I'm confused, did I do something wrong? Somebody please help me!

Komputes ](*,)

---

### Post by markino on 2006-06-23
try to download the alternate install cd and install from it.
it uses the old style text install method.

M@

---

### Post by Furry_Fighter_20x66 on 2006-06-23
I installed Ubuntu 64bit on my Acer Aspire 5002 (which is the 5000 with a little more ram and HD space, and the same crappy SiS video chipset I believe) and I had no problems.

There will be a few issues to correct once it has installed (namely making it use the correct video card driver and getting the wireless working) but during the install it was fine. If you haven't done so, try installing it again and see if it was just a strange instance where something crashed during the install.

---

### Post by vigleik on 2006-06-23
[QUOTE=komputes]
I'm confused, did I do something wrong? Somebody please help me!

[/QUOTE]

Just one question. Did you check if the CD is good? Either calculate the MD5 sum and compare, or choose "check CD" or something like that from the first menu you get when you boot from the CD. (I don't remember the exact text of the menu option.) A bad burn could explain why this is happening.

Vigleik

---

### Post by ntufar on 2006-07-03
I also have Acer Aspire 5000.
Installed Ubuntu without problems using ubuntu-6.06-alternate-amd64.iso	image, that is, text-based.

As Furry_Fighter_20x66 said, after installation edit /etc/X11/xorg.conf and change driver to "sis".

Wireless works only with ndiswrapper.

Could not enable OpenGL though. Anyone knows how to enable OpenGL on SiS 760 video adapter? I know that hardware acceleration is not supported. How do I enable software one?

---

### Post by GarethEvans on 2006-07-04
[QUOTE=Furry_Fighter_20x66]I installed Ubuntu 64bit on my Acer Aspire 5002 (which is the 5000 with a little more ram and HD space, and the same crappy SiS video chipset I believe) and I had no problems.

There will be a few issues to correct once it has installed (namely making it use the correct video card driver and getting the wireless working) but during the install it was fine. If you haven't done so, try installing it again and see if it was just a strange instance where something crashed during the install.[/QUOTE]

I have the same model, same issues and almost same experience.

For some reason the xorg settings didn't stick from the initial install (specifically the widescreen resolution settings); I had to run sudo dpkg-reconfigure xserver-xorg to get it going at 1280x800.  

Also, it was necessary for me to use vga=792 for a boot paramater to get framebuffer working correctly (I couldn't find the framebuffer vga code for 1280x800, 792 is actually the one for 1024x768 )

---

### Post by bluppfisk on 2006-07-11
> **ntufar said:**
> Could not enable OpenGL though. Anyone knows how to enable OpenGL on SiS 760 video adapter? I know that hardware acceleration is not supported. How do I enable software one?

No OpenGL here either on my Acer 5003. My driver is set to "sis" and all that, got the resolutions working, but no acceleration. And exactly that is what is needed to install WinE on my computer, which I desperately need to play starcraft! Help!

S

---

### Post by MasterHead on 2006-07-11
kubuntu 6.06 also failed to install on my computer, from what ive read in the forums it probably has to be with a problem with SATA2, so i tried the alternate distro wich has the clasical text installer ant it workedout perfectly.. :)

---

### Post by komputes on 2006-09-18
Hey guys, a few months since my last post and I was ready to try installing Ubuntu one more time. This time I downloaded ubuntu-6.06.1-desktop-amd64, hoping that the update since 6.06 would fix the installation problem. The same thing happened, I got as far as the disk partition manager, and then the computer simply froze. I tried this about 5 times, every time with the same result.

@markino: Why is it necesary to download another ISO of Ubuntu to get the text style installer. I've seen other distros that package  CLI and GUI installer interfaces on the same CD. So I'll try the alternate and report my findings afterwards, but I won't be happy while I do it.

@Furry_Fighter_20x66:What distro did you use 6.06 or 6.06.1? Did you use the amd64 or i386 iso? Did you use the alternate, desktop or server iso? Also do you have Windows XP installed on another partition or is it a dedicated ubuntu drive?  

@vigleik: I ran the MD5 and it checks out to: 50e3912c555f98f7bca56b2a0200b205 which is correct. On boot I went through the Check Disk and Memory Test and both of them confirmed that everything was ok. I doubt it's a bad burn since it verifies the info after burn and I tried burning it from another PC as well.

As I said I will try the alternate in the next few days(I hope I can specify the partition info "/" "ext3" "linux-swap" easily since I do  not have much experience in command line installs). Is anyone else with the same Acer 5000 havng the same issue with ubuntu-6.06.1-desktop-amd64.iso?

](*,) Komputes

---

### Post by komputes on 2006-09-18
So I downloaded the alternate 64-bit install. I checked the MD5, and I burned the iso to a disc. I booted in text mode and gor the following error:

[    38,5480920] agpgart: Apeture conflicts with pci mapping.


It then continued by showing me the text mode install which seems to be folded on itself. I'm pretty sure I can guess the cause of this. It's probably the SiS video driver which I might have to specify. 


Does anyone know how I can do this from the command line interface? I probably have to type F6 and add something to the boot options to specify my video driver to sis. Help anyone???



[IMG]http://www.uploadfile.info/uploads/4ce1e83c9f.jpg[/IMG]

---

### Post by komputes on 2006-09-18
:grin: Whoa! I'm happy to report that I am currently posing a response in Ubuntu using Firefox. We did it, thank you. I will share my knowledge with all so that future users witha Acer Aspire 5000 or more specific Acer Aspire 5002WLMi understand what they need to do to be able to install Ubuntu on their box.

1 )Download ubuntu-6.06.1-alternate-amd64.iso
2 )Download [MD5Checker]("http://www.softgears.com/WinMD5.html") Utility
3 )Run MD5 and make sure it equals to b9a5be3a5858ade278d664d41310a4ab (version specific) to make sure that your copy has not been tinkered with.
4 )Burn the iso disc image with your burn software of choice Nero/EasyCD/etc
5 )Reboot with the disc in the drive
6 )On the boot screen press F4 and select 640x400 instead of VGA
7 )Select Text install and follow the instructions for install
8 )At network configuration, plug in your ethernet and run DHCP (this will allow automatic updates)
9 )At Disk Partition Manager select your configuration (keep in mind 256MB swap[logical] and 2GB ext3[primary] are the min. requirements)
10 )Enjoy

Now to get NDISwrapper to work so that my wireless card works...
Also I've heard that the PCMCIA card slot doesn't work (no drivers). I hardly use it but I like to know that everything on my machine is compatible and working.

[CENTER]
:grin: Happy Happy, Joy Joy, Happy Happy, Joy :grin: [/CENTER]

---

### Post by komputes on 2006-09-18
> **ntufar said:**
> after installation edit /etc/X11/xorg.conf and change driver to "sis".

Wireless works only with ndiswrapper.


I went into the file and modified it 
**from this:**

[I]Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection[/I]


[B]
to this:[/B]
[I]
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection[/I]

Tried to save it but got the following error:

*You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.*

tried to go to properties to change permissions but the pwner of the file is root, do i need to log out and log back in as root? I only set up one user/password durring the install, do i use my pass but root as the user?
--

On another note, any tutorials on how to configure ndiswrapper properly. As well the PCMCIA, modem and bluetooth. (not that important because I never use them, but might need PCMCIA for a wireless card with a nub->anteanna).

---

### Post by Aquila62 on 2006-09-19
[QUOTE=komputes;1516298]I went into the file and modified it 
**from this:**

Tried to save it but got the following error:

*You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.*

tried to go to properties to change permissions but the pwner of the file is root, do i need to log out and log back in as root? I only set up one user/password durring the install, do i use my pass but root as the user?
-----------------

Hi, you just need to run your favourite editor in SUDO mode. EG: sudo nano /etc/X11/Xorg.conf  or something like that, then it will save ok.

---

### Post by komputes on 2006-09-19
> **Aquila62 said:**
> 
Hi, you just need to run your favourite editor in SUDO mode. EG: sudo nano /etc/X11/Xorg.conf  or something like that, then it will save ok.

Just gives me a white term window with the top having the name of the file and the bottom having options like ^R. I can't see what i'm editing (if it's even there...)

---

### Post by Aquila62 on 2006-09-19
Hi Again, strange as it usually works, but I had the same result here too, so I did >

1. **sudo nano** to open nano in su mode.
2. **^R** ( ^ = CTRL Key ) to Read file.
3. Type in the path & name of the file EG: **/etc/X11/xorg.conf**  at the bottom of the nano editor window, then press enter to load.
4. Edit to your  hearts content using cursor keys to navigate around.
5. Then press **^O** to write the file out.
6. Then press **^X** to exit nano.

Hope this helps & sorry that it did not work the first time.

---

### Post by kronictokr on 2008-04-20
to the guy who cant change his xorg file.

system>>administration>>login window
go to security, check that system administrator is allowed

then open a terminal, type

sudo passwd

then type in and REMEMBER your password twice

exit



go to switch users , when you log in type root, and your password, 
you should now be able to find and modify your file with no problems, dont to forget to switch back to normal user when done.

---

### Post by komputes on 2008-04-29
This was an error I had a few years ago with 6.06, it was fixed in subsequent releases. As for your advice on running as root, it is very insecure, but thanks for the thought. Just use 
```

#in the shell
sudo nano /etc/X11/xorg.conf

#using graphic text editor
sudo gedit /etc/X11/xorg.conf
```

---

