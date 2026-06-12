---
title: "Having some problems with USB WLAN adapter, sound, monitor resolution, and dual boot"
date: 2006-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by darrellfjohnson on 2006-09-28
tried using Ubuntu 6.06 the other day, and it was kind of a disaster. When I booted the Live CD, I couldn't increase my resolution (it was stuck at 640x480), my wireless USB adapter wouldn't work (it froze when I tried to activate it, and I had to restart),I couldn't mount my hard drives that were formatted with NTFS (they were detected in the 'Computer' menu, but when I double clicked them an error message popped up.), and I had no sound from my Soundblaster X-Fi soundcard. 

Thinking that it was just that there were no drivers included with the Live CD, I went ahead and installed it. Well once it did its thing and I restarted I couldn't boot. It just said 'Error with Operating system' in the POST screens and wouldn't get past that. I could boot the CD, and then select Boot from hard drive from there, but I still had the same problems. I couldn't activate my USB wireless adapter, my resolution wouldn't increase any, I couldn't mount my NTFS formatted HDDs, and I still had no sound. Is this just a problem with unsupported hardware? Are there some drivers that I need to download? My specs are:

3500+ Athlon 64
Abit AN8 32x motherboard
1.0GB PC3200 RAM
160GB Seagate 7200.10 SATA II HDD (Ubuntu was installed on this)
2x Maxtor 200GB IDE HDD (NTFS formatted HDDs)
nVidia 7900GT PCI Express videocard
Viewsonic G90fb
Soundblaster X-Fi
Zonet ZEW2500P USB wireless adapter

Well I finally was able to boot (for some reason I had to change the boot order of my HDDs so that the NTFS formatted hard drives boot before the SATA II that Ubuntu is actually on.

I also kind of managed to fix the USB WLAN adapter.  By changing some options, then rebooting I was able to configure it w/o the system locking up on me.  The only problem is that the internet still doesn't work.  I can't ping, I can't traceroute, no websites load, nothing.  I tried this with both static IPs and DHCP.  I know that the information I put in was correct because I'm typing this from a Windows computer that is connected to my wireless network right now.

But that's not even the biggest problem, I can't boot into Windows now.  When I restart the GRUB bootloader starts and gives me a couple of options:

Ubuntu
Ubuntu safe mode (not exactly this but something like this)
Memtest86
Microsoft Windows XP Pro

When I choose XP Pro, this is shown on screen, then the computer just freezes there and doesn't do anything:

```
Booting 'Microsoft Windows XP Professional'
root (hd2,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
map(hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

So now my machine is completely unusable since my Ubuntu installation can't connect to the web, and the low resolution and refresh rate kills my eyes, and my Windows installation won't boot.  I'm seriously considering just formatting and reinstalling Windows, but I really want to learn to use Linux, and I want to like it.  But this is a lot of stuff to have to go through to get the very basics of a usuable computer system...

Thanks in advance for any help...

---

### Post by kuja on 2006-09-28
I think I've heard stories of Ubuntu install troubles when You have a mixture of both SATA and IDE hard drives. It simply isn't compatible with linux. Does Ubuntu still boot right now? I'm going to look around for a solution to that for you.

You mentioned an SoundBlaster X-Fi soundcard. I'm sorry to inform you that it's not compatible with Linux at all. (Don't blame me. Don't blame Linux. If you want to blame somebody, blame Creative, the makers of the card.)

It will take a little work to get the NTFS drives to mount - [see this wiki page.]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite") A friend of mind has had luck with method two, take your pick.

To get your screen resolution to a state of normality, execute this command in a terminal:```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you for your password, then, ask  you a series of other questions, among them, your desired screen resolution.

---

### Post by darrellfjohnson on 2006-09-28
I think I've heard stories of Ubuntu install troubles when You have a mixture of both SATA and IDE hard drives. It simply isn't compatible with linux. Does Ubuntu still boot right now? I'm going to look around for a solution to that for you.

> You mentioned an SoundBlaster X-Fi soundcard. I'm sorry to inform you that it's not compatible with Linux at all. (Don't blame me. Don't blame Linux. If you want to blame somebody, blame Creative, the makers of the card.)

It will take a little work to get the NTFS drives to mount - see this wiki page. A friend of mind has had luck with method two, take your pick.

To get your screen resolution to a state of normality, execute this command in a terminal:
Code:
sudo dpkg-reconfigure xserver-xorgIt will ask you for your password, then, ask you a series of other questions, among them, your desired screen resolution

Thanks so much for the help.  To answer your first question, I assume it would but I already went ahead and formatted the HDD.  I didn't give up, I was Googling around and found a tutorial for a good way to set up partitions for Ubuntu (and I guess other Linux distros too).  This should help setup partitions to be easier to use.  Plus, I can use a FAT32 partition to share files between Windows and Linux.

Once I reinstall Ubuntu I will disable my IDE drives and see if that works.

I also found about the Soundblaster not working right in Linux.  I'm gonna email Creative about that because there really is no excuse for it.  But I can live with integrated sound in Linux.

I will try that code for the resolution.  It looks like it should work, but I probably won't know until I install Ubuntu again tomorrow.

Also, I would like to add a question.  From looking around on this forum, it seems like the 64 bit version of Ubuntu isn't up to snuff compared to the 32bit version.  How severe is this?  Would it affect me if I plan to use Ubuntu normally?  I won't be programming or anything, just playing music, watching movies, using the internet, writing papers, that sort of thing.

Thanks again for the help.

---

### Post by kuja on 2006-09-28
Good idea, I doubt they (creative) will ever do anything unless they're getting feedback like that.

Personally, I wouldn't use a Fat32 partition that size, even though you can. What I would do is use ext2, and install an ext2 filesystem driver in Windows. ext2 is sufficiently more advanced, handles large partitions better (I think Fat32 is inefficient for anything bigger than about 20GB, if I remember right.). Besides, you wouldn't have to worry about defragmenting the drive then either. Just my thought.

The problems with x64 really aren't severe as they're made out to be. I wouldn't worry too much about it.

---

### Post by darrellfjohnson on 2006-09-28
What would happen if I installed an ext2 driver on my ntfs formatted drives?  Would I be able to read from my ntfs partitions easier or something?

And I wasn't planning on making the fat32 partition that big, only about 12 GB.  I was going to transfer files that I know I will use a lot like my Word files, Firefox passwords, maybe my music, stuff like that.  But if I can just install a ext2 driver on my ntfs drives and use them, then I won't worry about.

Sorry about adding more questions but I have one more.  What partitions am I supposed to make for Ubuntu and how should they be formatted?  I know that I need one for /, one for the swap, and one for home right?  How are they supposed to be formatted?

---

### Post by darrellfjohnson on 2006-09-28
> **kuja said:**
> I think I've heard stories of Ubuntu install troubles when You have a mixture of both SATA and IDE hard drives. It simply isn't compatible with linux. Does Ubuntu still boot right now? I'm going to look around for a solution to that for you.

You mentioned an SoundBlaster X-Fi soundcard. I'm sorry to inform you that it's not compatible with Linux at all. (Don't blame me. Don't blame Linux. If you want to blame somebody, blame Creative, the makers of the card.)

It will take a little work to get the NTFS drives to mount - [see this wiki page.]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite") A friend of mind has had luck with method two, take your pick.

To get your screen resolution to a state of normality, execute this command in a terminal:```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you for your password, then, ask  you a series of other questions, among them, your desired screen resolution.

Well I tried entering that command, went through the prompts and still nothing.  I couldn't edit or change any of the options, but the options were there.  But once I finished with the prompts I still couldn't change resolution or refresh rate.

Is it because I can't change any options with a Live CD?  Or is it something else?

All these problems are getting kind of frusterating but I still want to try...

---

### Post by darrellfjohnson on 2006-09-28
Well after installing it, my resolution problems are now fixed, I have a functional dual boot, and I know how to get my WLAN working (need to download ndiswrapper, I'll hook the computer up to the router by Cat5 and download it there.\

Thanks for all the help.

---

