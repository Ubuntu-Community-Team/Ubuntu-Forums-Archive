---
title: "Geforce 6150 / Nforce 430"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mago on 2006-02-06
Hi. I'm new to linux (yet another once-on-the-dark-side-of-the-force-and-finally-awakening-pc-user) and after some days of intense googling and playing with a halfway installed kubuntu breezy, i got it somewhat running. I found a lot of helpful advices in this forum, so I decided to take it further and join :p . Well, i'm on an Asus A8n-vm csm with an a64 3000+ venice. I'm having the same problems as many others with this chipset and linux... can't install nvidia video driver (8178 patched), nor nforce adudio and ethernet driver. After a lot of reading (and learning) i managed to boot with the vesa driver, just when i was ready to give dapper a try (which will be delayed). The thing is that without internet, getting things for linux is not an easy task. For the nvidia driver i got as far as installing gcc-3.4 (and exporting it), getting the headers and source and then hard linking them (ln -s & -sf) after install to /usr/src/linux but installer crashes even with --kernel-source-path=/usr/src/linux option with a friendly "./linux/version.h does not exist... you newbie are not configuring your kernel source files (which i don't know how to do)" message (uname -r=2.6.12-9-amd64-generic). Nforce driver (0310) is less picky, simply stating that the kernel source files are missing (though i do have them, linked and everything). Oh, by the way, there's something wrong with apci, but that is Asus fault (still no bios update). I found over the net a workaround to this, but it doesn't look easy and this isn't too much of a problem anyway (other than some error messages at boot).
I tried so many things that i'm kinda lost now. Where should i be looking? What am i doing wrong? 
Any help will be greatly appreciated.
Oh, and sorry for my english (or the lack of it)... :cry:

---

### Post by Mago on 2006-02-06
sorry for the double post :???: . It gave me some weird error the first time...

---

### Post by Mago on 2006-02-08
Never mind, i got it fixed. I downloaded linux-source instead of linux-image. Video and network are working nicely now. Still no sound, but i haven't found a way to fix this with a 2.6.12 kernel (there's a hack for 2.6.15 and above kernels). Anyway here is a helpful page for those with this board [http://quaggaspace.org/a8nvm/](http://quaggaspace.org/a8nvm/)

---

### Post by fbg111 on 2006-02-12
Thanks for the update and link Mago, much appreciated.

---

### Post by geek.de.nz on 2006-08-26
OK, I'm not new to Linux nor (K)Ubuntu. But I cannot get my LAN card to work in (K)Ubuntu 64 bit (Dapper). I know how to setup a gateway etc. So, LAN settings are not the problem. It just doesn't work. Sound, video etc worked out of the box which is nice, but LAN is actually more important because like this I have to do everything from CD/DVD.

My new! Motherboard is a 
Asus M2NPV-MX
Northbridge: NVIDIA GeForce 6150 GPU
Southbridge: NVIDIA nForce 430 MCP

As far as I know, that is quite new Hardware, so I might have to install a bleeding edge distro like edgy. i will give that a shot, but might not succeed.

So far, I've tried to install the drivers manually, which gave me the error:
package binutils missing!

I checked and a (static) package of binutils (binutils-static) was installed. The installer (NFORCE-Linux-x86_64-1[1].0-0311-pkg1.run) from the Asus install CD (woohoo, they actually ship with Linux drivers now) gave me another error:
tool ld not found.

I checked and searched for the ld tool. There was a file called /bin/ld_static, and I thought: "bingo!", made a symbolic link to it (#ln -s /bin/ld_static /bin/ld) and restarted the install. This time I got a slightly different error:
ERROR: Unable to find the system utility 'objcopy'; 
please make sure you have the package 'binutils' installed. 
If you do have binutils installed, 
then please check that 'objcopy' is in your PATH.

          OK 

By the way, the LAN card is actually installed in the sense that I can see a device eth0 if I do '#ifconfig' and stuff like that, but it just doesn't work. Now I have to always work from CD on that machine and that's definitely not an option. Bugger, I knew this would happen. Linux is always bad with new hardware.

(see [http://ubuntuforums.org/showthread.php?p=1423919#post1423919](http://ubuntuforums.org/showthread.php?p=1423919#post1423919) for a similar post)

---

### Post by fbg111 on 2006-08-26
I'm afraid I don't have an answer for you, I wrestled with Asus's predecessor to your board, the A8N-VM-CSM for six months, and couldn't get Dapper, Gentoo 2006.0, FC5, or FreeBSD 6.1 completely working at all.  The best I could achieve was Ubuntu and Gentoo with networking but no Nvidia drivers, and the standard software display drivers just don't cut it for everyday work.

I just purchased one of the last [MSI K8NGM2-FID]("http://forums.anandtech.com/messageview.aspx?catid=29&threadid=1803985&enterthread=y") boards I could find to replace it.  It's apparently the best 6150/430 board for Linux, but it's discontinued now in favor of an AM2 replacement.  Newegg is out of stock, but I found one at PCAlchemy.com.  I also considered a newer AM2 version, but my primary goal is to have Gentoo or Ubuntu running and I figured newer hardware would simply extend my problems.  The first gen AM2 6150/430's don't offer much better performance anyway, just support for AM2 cpu's (Pacifica, soon to be 65nm w/ less wattage) and the 6150b chip handles hdtv a little better.  

I'm also a bit put out with Asus, since they've always been one of my top choices for quality and features.  I figured I could buy an Asus without worrying about 'will it work'?  How wrong I turned out to be.  And the fact that MSI got it so right at least shows it can be done.

Anyway, here are a couple links you might find useful.  First, in addition to this forum, and if you haven't already, I recommend searching the following forums for '6150 AM2' or something similar:

[NVNews.net: motherboard/cpu forum]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=3")
[AVS Forum: Home Theater Computers]("http://www.avsforum.com/avs-vb/forumdisplay.php?f=26")

Second, that [link I posted above]("http://forums.anandtech.com/messageview.aspx?catid=29&threadid=1803985&enterthread=y"), while specific to the MSI board, includes your board in its comparison, and may have some further discussion on it.  I only read the OP, not the following 11 pages.

Finally, in case you're interested, the M2NPV-VM version of your board is [reported to run Solaris]("http://www.sun.com/bigadmin/hcl/data/sol/systems/details/1925.html").  (I can't find the difference b/t the two boards anyway...)

Byron

---

### Post by geek.de.nz on 2006-08-26
Thanks for the reply.
Just a status update:
There are Linux drivers for the Asus board(s). And actually I'm quite happy that Asus actually provides them (open source).

They only need the right kernel header files installed for the running kernel plus a few development tools (build-essentials etc). I downloaded several packages from launchpad and installed them. Had to iterate because of dependencies and further needed packages by the installer. That took me all day yesterday. :confused:

I got to the point where it almost installed, but then it was complaining that my header files don't match the running kernel. ](*,)

Now I'm trying my luck with compiling my own kernel. I've done this before and it should work fine once I have all the right packages installed. I wanted to do this anyway, because I like suspend2 (hibernate). Downloading the DVD iso now, so I can apt-get the necessary packages, because manually downloading all the .deb packages with considering all the dependencies takes far too much time and I have other stuff which I have to do (assignments). I rather let it running for 10 hours while I implement my DBMS buffer manager 8-).

Well, I guess I could take out my LAN card out of this machine and install it in the AM2, but yeah, I started the download and I can't be bothered to be honest.

If I have time and get it running, hopefully I'll have time to write something like a howto, so that other people don't go through such a hassle.

---

### Post by fbg111 on 2006-08-29
Good luck, if you do get it going, let us know.  

Also, for anyone reading this, I may be wrong about the MSI board being discontinued right now, it appears [Newegg is scheduled to get more in 9/4]("http://www.newegg.com/Product/Product.asp?Item=N82E16813130529"), though with AM2 versions out now it probably won't be long.

---

### Post by anaconda on 2006-11-01
> **geek.de.nz said:**
> 
By the way, the LAN card is actually installed in the sense that I can see a device eth0 if I do '#ifconfig' and stuff like that, but it just doesn't work. Now I have to always work from CD on that machine and that's definitely not an option. Bugger, I knew this would happen. Linux is always bad with new hardware.

Hmm.. 
Sounds familiar. I had the same problem, and a temporary solution was to go to "networking" (Sorry I am now in winblows, but it is in the same place than synaptic..) and select your LAN, disable it and then activate it. This should make your LAN work until the next reboot..

There was a more permanent solution (which didn't need recompiling the kernel), but cant remember it.. sorry.

---

### Post by anaconda on 2006-11-01
This might be the permanent solution:
[https://help.ubuntu.com/community/NvNetInstallation](https://help.ubuntu.com/community/NvNetInstallation)

---

### Post by super.roz on 2007-06-19
I'm planning to upgrade my existing computer (AMD athlon 800 MHz) to something produced in this millennium.

I was planning to stick with an AMD processor due to cost, but I was unsure which chipset/integrated graphics is supported better in Ubuntu.  Basically I want to choose between AMD(ATI) and Nvidia.

I'm considering two different boards:
M2NPV-VM (Geforce 6150/Nforce 430)  or...
M2A-VM (ATI Radeon Xpress 1250/AMD 690G/ATI SB600)

I've used the nvidia binary drivers in the past and have had pretty good success but that was with much older hardware.  Any suggestions?  Which of these two boards is better supported in Ubuntu?

---

### Post by geek.de.nz on 2007-06-19
Take the M2NPV-VM. NVIDIA is much better supported on Linux.
I have the same motherboard and everything works fine, SATA, Network, AUDIO, Graphic Accel, ...
I think that's the one i've got. If it s the one which came out last year? 

Generally, when hardware came out before an Ubuntu release, you can use it with that release, so in my case Ubuntu Feisty Fawn 7.04.

I had tried the 64 bis version of Dapper 6.06 but that did not work well. I'm sure that with a custom kernel etc. I could have gotten it to work, but it was a hassle. 64 bit Feisty should be fine, but I haven't tried it yet.

---

### Post by super.roz on 2007-06-19
Thanks for that suggestion.  I was already leaning towards the NVIDIA solution.  That helps solidify it.

Yes, this is the same board that came out last year.  I'm trying to stay economical and largely following the suggestions from arstechnica's budget system guide.

---

### Post by geek.de.nz on 2007-06-20
Yeah, I should have done it that way. I bought my new computer last year and the hardware didn't work in Ubuntu and I didn't have enough time then to sort it out because of study and work. Now everything just works. One should always wait at least 6 months after hardware has come out to buy it.

---

