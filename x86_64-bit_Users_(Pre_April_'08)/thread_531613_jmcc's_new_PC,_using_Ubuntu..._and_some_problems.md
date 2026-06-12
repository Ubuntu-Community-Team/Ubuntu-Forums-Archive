---
title: "jmcc's new PC, using Ubuntu... and some problems"
date: 2007-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmcc1976 on 2007-08-21
Hi, this is my first post. I want to ask some questions about Linux because I installed Ubuntu 6.10 on my new PC a week ago.

I hope that, in the future, I will be capable to help others in these forums but by now I am starting with GNU/Linux. I am just a beginner and, on the other side, I have some money problems that will not let me to expand myself as much as I would like on this field (and others). I am 31 years old and I live in Venezuela, but my fathers are/were from Madeira, Portugal, so I feel like a Madeiran even taken in count that I have born in Caracas.

Remember that English is not my first language, so please excuse me for any possible mistake(s). I will now explain a bit of various things in part to provide another users with my own experiences. Maybe it will be useful for someone (but remember that I am not an expert with these things, I am only an amateur, so not take me as an example for nothing).

I have passed the last seven months buying a PC by parts, to build it later by myself. Why I did it that way? Because I wanted to buy every part brand new. Various stores here sell components without box and even without the software that should be with it. For example, when I tried to buy a DVD ±R/RW DL drive, LG brand, they first told me in the store that the product came without box, inside a plastic bag, only with a cable and a CD. I said &#8220;OK, I will take one&#8221;. A few moments later the same employee told me that the unit had no software and then he told me to wait some moments because &#8220;the unit was being tested by them to be sure that it works fine&#8221;. Then I said &#8220;No thanks&#8221; and &#8220;Good bay&#8221;.

That DVD drive was intended to be my second recorder because I already had one, Lite-On, but I wanted another or a DVD-ROM drive.

So I bought all my components boxed, with the exception of the hard disk drive (it came inside its respective anti electrostatic discharges silver bag).

This is the list of my PC components:

&#61485;- Core2 Duo processor E6400, 2.13 GHz, 1,066 MHz FSB, 2 MB L2 cache
&#61485;- Intel D946GZISSL motherboard
&#61485;- 1 Western Digital WD2500KS-00M hard disk drive, SATA II, 250 GB of capacity, having around 233 GB after formatted by Ubuntu during the installation process (but remember that the size units are measured differently by the HDD industry, so for them 1 MB = 1,000 KB, instead of 1,024 KB, like the rest of the computer industry)
&#61485;- 1 DDR2 module of RAM, 512 MB, 533 MHz, Kingston ValueRAM
&#61485;- 1 Lite-On DVD ±R/RW DL drive, model SHW-160P6S, IDE
&#61485;- 1 floppy drive, Sony, model MPF920-Z/161
&#61485;- 1 multicard reader, Sony, model MRW620-2/121
&#61485;- PSU: Thermaltake Toughpower 650W, model , ATX 2.2 compliant
&#61485;- Case Cooler Master Mystique RC-631-KKN1-GP, with two 12 cm fans and TAC 1.1 compliant
&#61485;- Creative basic speaker system, model SBS380, with subwoofer

Also I have an UPS unit, APC, model Back-UPS ES 750, but given the fact that my home's electric wiring is not grounded it will be almost not useful against surges and thunders. I have read that 95% of the population in Colombia have inadequate electric wiring installations. I assume that the situation is very similar in Venezuela and that percentage is high in all Latin America. My keyboard (Spanish language) and optical mouse are BenQ.

I started to buy components since November 2006 and around two weeks ago I bought the last crucial part needed to put my PC running, the power supply unit. It took me that much time by two reasons: the money and the difficulties I have confronted to locate the necessary parts for my system. Believe me, the things I was thinking would be the more easy to find ended being the most difficult, a PSU (it was needed an ATX 2.2 one for my motherboard) and a computer case TAC 1.1 compliant (needed to get a 38º C internal temperature for a good processor and system performance [the BIOS program shows me the internal temperature at 38-39º C when I start the PC]).

The assembly of the system was relatively easy. The most difficult part for me was to put the processor's fan on its place over the socket. The first three fasteners were easy but the last one I needed to press it four times until it finally did click. Maybe it happened because I was nervous after failing the first attempt and now I worry about that substance between the processor's top and the bottom of the fan (I don't know its English name)...

The case is tool-free. The CD and floppy drives are mounted by pressing a plastic accessory and hard disk drives have plastic adapters to put each one on the case (up to four in the Cooler Master Mystique 631). After installing Ubuntu I have noticed that the HDD is noisy like a Samsung 1.61 GB disk I had on my first computer years ago, and this is my major deception with this computer. Also, when I put a CD or DVD into its drive, and when the disk is running slow, it is usual to hear a noisy vibration from the DVD drive.

Believing that all I have said is enough to have an idea about my equipment, now I will explain my Linux experience. Since I have explained this on another forum, I will simply quote what was said there:

> **Installing Linux: My experience**

Hi to everyone.

I just want to comment that in the last night I installed Ubuntu on my computer and I want to share some thoughts. For me to install Linux was relatively easy and it could be even more easy if I had  followed the installation program defaults. Ubuntu is now working fine but some things were not as I imagined, in part because of me.

I have a 250 GB Western Digital SATA II HDD, but the 250 GB stated on the label ends in 232.88 GB for the operative system because the unit used by the HDD industry is different from the rest of the computer world [for them a MB is 1,000 KB and a GB is 1,000 MB, being for the rest a MB = 1,024 KB and a GB = 1,024 MB] and due to the file system too, I suppose.

I tried to create the partitions myself with the manual method because I wanted to divide the disk as follow:

&#61485;	a 2 GB swap partition, being this one the first partition
&#61485;	a 30 GB root partition (with reiserfs file system)
&#61485;	a 200 GB /home partition (in reiserfs too)

I decided to use reiserfs because I have read on one of my guides that it was better than ext3. Also on one of those guides I read that, since there is no limit for logic partitions on a HDD (primary partitions are limited to 4 on one hard disk), &#8220;normally&#8221; you will have no problems using logic partitions over an extended partition that is in the place of a primary partition.

Maybe it is a delicate matter but since the installation program said nothing in the automatic method of how will be the disk divided, I decided to go manual to manually add the 2 GB swap partition (thinking on the future because maybe I will get a second 512 MB RAM module [DDR2 533MHz] for this PC).

So I created an extended partition using all the space available on the disk and, inside of this partition, I created first the 2 GB swap partition, then the 30 GB root partition (&#8220;/&#8221;), and finally the /home partition with around 200 GB. After doing it all, I started the installation and the process ended normally, asking me at the end if I wanted to keep using the LiveDVD or just to restart the machine to start using the installed GNU/Linux Ubuntu OS.

I restarted the PC but when in the screen appeared the message &#8220;Please take out any CD from the CD-ROM drive, close the tray (if any) and press Enter&#8221; I did that but the Enter button didn't work. I tried it several times and nothing so I used the reset button :(

And the only thing I received was a message from the motherboard BIOS, something like &#8220;There is no bootable drive. Please insert the bootable media and restart&#8221;. I checked the BIOS options, all was fine but I tried putting the HDD as first boot device but nothing worked.

I was a bit frustrated so I choose to install it all again but using the automatic options of the Ubuntu installation program. When the program checked the disk, I found used space so the previous installation was apparently fine, but I choose to delete all the disk and install. At the end, when I was restarting, the same thing with the DVD (a Lite-On ±R/RW DL drive that appears on the Ubuntu equipment folders only as a ±R drive) happened, so I was in the need, again, of using the reset button :(

But after restarting things worked fine this time, as far as I am capable to detect. The default file system is ext3 so I am using it.

The thing that worries me a bit now is if I did bad reformatting the disk just immediately after a previous format process. I have heard that doing this is dangerous for the HDDs. Am I wrong?

Now let me think. I believe that it would be right to share some impressions about the GNU/Linux Ubuntu OS.

Well, the visual aspect is nice, very beautiful giving the fact that it is a free OS.

It is a bit more slow than Windows XP opening DVDs, CDs and diskettes, I believe. Another thing is that there is no refresh button on the system explorer, so if I want to know the capacity of my USB pen drive or diskette I need to unmount and mount it again (using secondary button menu), a bit frustrating thing.

Properties windows remain on top of everything and I don't know what to do to make then behave as normal windows (doing secondary click over the title bar there is an option named &#8220;On top&#8221;, but it is not activated and still the windows appear over all other windows).

And other things I don't remember now, except this: I have no video or audio file that can work in Ubuntu... I would like to know, if you can tell me, what programs you use to watch the movie trailers in your Linux computers, please. Also, Totem (the Ubuntu video player) don't reproduce any DVD. I know of course the free software philosophy of Ubuntu but I suppose that there is a way to reproduce all those video files on this OS. Mplayer? VLC? Because I need to reproduce at least the next file types: mov, avi, wmv, wma, mp3, mpg, DivX, Real media, vob, ts (HDTV) and other that maybe I don't remember. And DVDs too, of course! :)

After having found this I was upset, asking myself why I didn't installed Fedora Core 6 or openSuSE 10.2 (by the way, my Ubuntu is 6.10, I will upgrade as soon as possible). I even put the installation DVDs of both OS in the drive to see if I can extract packages from them but Fedora and openSuSE support RPM (Red Hat) packages and not DEB (Debian) packages as Ubuntu (I found the package for amarok in one of the disks).

I also tried to install both Fedora Core and openSuSE but I didn't found an option to install them together with Ubuntu and, since I didn't want to format the drive again, I left it with Ubuntu alone and meanwhile I will try to find a solution to avoid a reformat process of the drive again.

Another thing is that everything apparently is installed and working but on the Ubuntu's device manager utility I can found a lot of &#8220;Unknowns&#8221;. Also I can't find info about the processor or the fans or the internal temperature of the case.

I have used my USB pen drive, floppy (but now I have a 1.44 MB disquette on the unit and it only recognize half of the capacity and don't let me to delete or copy files to it and I have write access to the floppy) and DVD drive fine. By the way, how can I give format to a floppy disk with Ubuntu?

I have not burned a disc still and the DVD ±R/RW DL Lite-On burner I have is labeled as a CD DVD ±R drive alone.

The multicard reader was detected as 5 floppy or memory card drives but I don't have cards to try it (at least 2 of them are labeled as Sony, the brand of the device).

My provisional conclusion is that Ubuntu is beautiful but I have not used it enough to give a definitive opinion, but it looks really well.

I have installed in the past days the next programs: VLC media player (I downloaded it and all the dependencies in an internet café and then I use a pen drive to transport that data to my home) and XMMS (I believe it came on the Ubuntu LiveDVD, don't sure).

**About VLC 0.8.6**

Media playback is one of the areas I am specially interested. I need to check videos and to see documentaries on my PC and also I have collections of movie and game trailers, teasers, clips, featurettes, game videos and more in a huge variety of formats that I use.

I have had some problems with VLC. I choose this media player due to its good reputation (on Windows I use mainly MPC but I like to have VLC because sometimes some files that not work with Media Player Classic can work with VLC [MPC comes with K-Lite Mega Codec Pack]).

The &#8220;f&#8221; key not always work for fullscreen, and this is an usual error with my VLC/PC. Very frequently I press &#8220;f&#8221; and nothing happens, so I need to go to it through the menu. Also, pause and play commands, no matter if it is with the mouse on the GUI or with the space bar, always last around a second to be executed and it is specially frustrating because sometimes I want to stop the playback in a given moment to see something (specially in movie trailers, where some scenes are quick) and I just can't. The playback stops after a second and I can't get the desired moment I am looking for.

At the end of the playback VLC freezes over around one second too, showing the last scene frozen. I don't know why this happens neither.

Also I can't play high definition files in various formats, *.wmv and *.mov for example. I can play 0,
resolutions until 480p and sometimes one file in 720p will work, maybe without audio, but commonly 720p don't work and I have not played even one 1080p file. It is very curious because on the internet café they have AMD single core Athlon PCs at 1.6 GHz with 256 MB of DDR RAM and I can play 720p files, not smoothly but I can, and with my PC I can't do it almost all the times.

I have some *.ts files too and I can't reproduce those neither (the *.ts files are the source for *.vob files and in Windows VLC can play those). In the future I will have more *.ts files and I need to know how to play those.

The flash video files (*.flv) also are a problem. Only few work but the rest don't. There is another video file, from Shockwave I believe, that I would like to know what to do to play it too.

The DVD playback also don't work on my PC. I believed that this problem will be solved installing VLC but I was wrong. Can it be the region configuration of the drive? How I can check and solve it if that is the problem?

And finally, some not so old files can't be played. Those are *.mov, so can it be a codec problem?

**About XMMS**

I need to know if XMMS can support Winamp skins and how I can install those skins. The high quality *.wma files that you can record with Windows Media Player don't work on my PC. Has someone here any experience with those files, please?

**Some video related (I think) issues**

I have some problems with the video, I believe. For example, each time that the machine starts, just before Ubuntu's user and password window appears (which is the first high resolution working area that we see after putting on any PC), I can see a small area of video distortion occupying around the sixth part of the monitor, at the bottom. I believe I can't get a screenshot of it but it looks very similar (but bigger) to the pink distorted section that can be seen on the next images:

[[IMG]http://img501.imageshack.us/img501/9094/pantallazo3gb5.th.png[/IMG]](http://img501.imageshack.us/my.php?image=pantallazo3gb5.png)    [[IMG]http://img205.imageshack.us/img205/6615/pantallazo2wg4.th.png[/IMG]](http://img205.imageshack.us/my.php?image=pantallazo2wg4.png)

Also, all of the 3D screensavers don't work on my computer, so I don't know if I am needing a driver (screensavers that work are fiberlamp, galaxy, metaballs, penrose, for example). My video card is the integrated on the motherboard, Intel Graphics Media Accelerator 3000 (my motherboard is the Intel D946GZIS, as I said before). Do I need a driver for that and all the other features of my system?

For example, now fiberlamp is my screensaver but the screen in these moments only gets black and nothing more. Yesterday it was working but another day it was configured correctly at one minute and it never started to work.

Sure thing that you know that Intel has on its site, under this motherboard downloads section, some configuration and driver files for Linux users, but there is nothing specially for Ubuntu and the closest thing I have found are packages for Debian 3.1, but I don't know if those will work with Edgy Eft. Those packages cover the next areas: audio, graphics and network, with another file for Linux users with a size of more than 56 MB.

So, do I need those files and drivers located on the Intel website?

**Two small things**

1. My keyboard is Spanish. All the keys display correctly, as far as I know (I have not checked it all) but the dot in the numeric section at right on the keyboard appears on the screen as a comma. Can I change that?

2. What is the equivalent command/program on Ubuntu or Linux to defrag my HDD?

And some screenshots from the system monitor utility:

[[IMG]http://img205.imageshack.us/img205/1798/pantallazo2vo7.th.png[/IMG]](http://img205.imageshack.us/my.php?image=pantallazo2vo7.png)    [[IMG]http://img467.imageshack.us/img467/1142/pantallazo1tm1.th.png[/IMG]](http://img467.imageshack.us/my.php?image=pantallazo1tm1.png)    [[IMG]http://img386.imageshack.us/img386/1464/pantallazoay5.th.png[/IMG]](http://img386.imageshack.us/my.php?image=pantallazoay5.png)

Those are all the things I wanted to share with you and to ask you. Thanks a lot if you can help me. And sorry if I wrote quick.

jmcc

---

### Post by Kilz on 2007-08-21
2. What is the equivalent command/program on Ubuntu or Linux to defrag my HDD?

You dont need to defrag linux file systems. :)

You might want to try mplayer for media. It can play .wma and wmv files.

---

### Post by kuja on 2007-08-22
For information on DVD playback see this document: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

For playing back flash files I think Adobe has a standalone player that may work for you, check [www.adobe.com](www.adobe.com) under flash, it should be on there somewhere. 

You're not going to have any luck with shockwave. As of yet there has been no shockwave player for linux and it's looking like it's going to stay this way for quite some time. You have Adobe to thank for that.

With regards to using Winamp skins in XMMS I came up with these after a brief run on Google:
[http://www.codecoffee.com/tipsforlinux/articles/5.html](http://www.codecoffee.com/tipsforlinux/articles/5.html)
[http://gentoo-wiki.com/HOWTO_From_Winamp_to_XMMS](http://gentoo-wiki.com/HOWTO_From_Winamp_to_XMMS)

Concerning the Intel X3000 and later graphics adaptors you'll have to wait 'til Ubuntu Gutsy (7.10) which includes a new driver for the X3000 and newer adaptors. My laptop (which has an X3500)  is partially upgraded to Gutsy and the graphics issues seem to be all but gone. Now to hope the rest of my issues surrounding the laptop and a "stock" kubuntu install disappear by the time Gutsy is released ...

---

### Post by jmcc1976 on 2007-08-22
Thanks **kuja** and **Kilz**.

Another question I forget yesterday: Do any one have any idea of how to make *.lit files to work under Linux Ubuntu? *.lit files are the e-book format for Microsoft Reader program. I have various hundreds (more than 700) of free ebooks on that format and I would like to read those in Ubuntu.

---

