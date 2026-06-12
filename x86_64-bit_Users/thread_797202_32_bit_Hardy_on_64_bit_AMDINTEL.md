---
title: "32 bit Hardy on 64 bit AMD/INTEL"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by cyclouno on 2008-05-17
All of my friends have got an i386 archi based processor but I got a 64 bit. Now they all keep installing those 32 bit distros and I am left troubled hunting for a 64 bit version of each distro [hardy in my case]

So I would like to know if it is possible to get 32 bit editions of linux distros working on my AMD athlon 64 bit??:confused:

I came to know about the x86 - 64 compatibility on wikipedia - and it says any 64 bit processor can act as a 32 bit cpu in Long Legacy mode. But will i have to enable something in my BIOS to make sure that my pc doesn't crash and yet install 32 bit editions??:confused:

ALso remember that I am not trying to emulate ubuntu as a virtual machine [VMWARE or something].. it's from the scratch bootable disk installation with GRUB boot loader... 

Thanks.:KS

---

### Post by cyclouno on 2008-05-17
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by Cappy on 2008-05-17
The 32-bit OS will run without any tweaks.

The 64-bit OS is easy to find; it's right next to the 32-bit Ubuntu option on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Just click option "64bit AMD and Intel computers" for the 64-bit version of Ubuntu.

---

### Post by cyclouno on 2008-05-17
@cappy

thanks man.. its not about finding the 64 bit version. its about downloading the dvd iso with packages for installation.. too less are the so called broadband bandwidth in india... money eaters... i've got the 32 bit edition installed without any problem on a 32 bit machine... but waitin to get it to work on my 64 bit... so now will give it a shot.. thanks..

---

### Post by Cappy on 2008-05-17
DVD version:
[http://www.google.com/search?&rls=en&q=ubuntu-8.04-dvd-amd64.iso&ie=utf-8&oe=utf-8](http://www.google.com/search?&rls=en&q=ubuntu-8.04-dvd-amd64.iso&ie=utf-8&oe=utf-8)

Direct link:
[http://cdimage.ubuntu.com/releases/hardy/release/ubuntu-8.04-dvd-amd64.iso](http://cdimage.ubuntu.com/releases/hardy/release/ubuntu-8.04-dvd-amd64.iso)

Torrent:
[http://cdimage.ubuntu.com/releases/hardy/release/ubuntu-8.04-dvd-amd64.iso.torrent](http://cdimage.ubuntu.com/releases/hardy/release/ubuntu-8.04-dvd-amd64.iso.torrent)

---

### Post by cyclouno on 2008-05-17
@cappy.

Thanks man..just curious to know how you are so sure that I can work with 32 bit on a 64 bit cpu....? any links

---

### Post by jespdj on 2008-05-17
> **cyclouno said:**
> Thanks man..just curious to know how you are so sure that I can work with 32 bit on a 64 bit cpu....? any links
Why do you need special confirmation? Read the Wikipedia article about x86-64 (link in one of the posts above). Most people are running 32-bit operating systems on their new 64-bit processors.

Read the [sticky](http://ubuntuforums.org/showthread.php?t=765428).

By the way, why do you want to run the 32-bit version? Why not just install the 64-bit version? It doesn't matter that your friends are running 32-bit operating systems. Note that 32-bit software also runs on the 64-bit version.

---

### Post by Sef on 2008-05-17
> Note that 32-bit software also runs on the 64-bit version.

Most GNU/Linux software has a 64-bit version now.  However there are some that don't, so you can use getlibs to make sure the 32-bit software works on your 64-bit system.

---

### Post by cyclouno on 2008-05-17
@jespdj

well why 32bit cause none of my frnds have a 64bit version and due to bad broadband bandwidth I couldn't download the dvd version [3days or so for a dvd iso] - it's a matter of availability and not downloadability.!!

and thanks for letting me know that I could run 32 bit softwares also..

@Sef

i haven't gone that far - newbie man.. so am sticking to the basics... and I definetely am lovin' ubu tux.. lovely it is.. jus showin off compiz to my sis & bro... :)

---

### Post by Xiong Chiamiov on 2008-05-17
> **cyclouno said:**
> @cappy.

Thanks man..just curious to know how you are so sure that I can work with 32 bit on a 64 bit cpu....? any links
I have an Athlon X2 (64-bit) and I haven't installed a 64-bit OS yet.

---

### Post by in_flu_ence on 2008-05-17
32bit is confirmed to work very neatly in 64bit computers. I have 2 64bits computers and both were running fine. The reason I use 'were' is because i have upgraded both into the 64bit OS to fully utilise what I have.

If you are in the general PC use, 32bit might be more easy-to-configure option due to the good availibility of plugins and etc (Java, flash and other  media related). If you are into the serious computing use, 64bit will certain give you the boost.

Good Luck. I think there are also some indian vendor that sells 64bit DVD (if i didn't remember wrongly) where you can just buy from store.

---

### Post by Kilz on 2008-05-17
> **in_flu_ence said:**
> 32bit is confirmed to work very neatly in 64bit computers. I have 2 64bits computers and both were running fine. The reason I use 'were' is because i have upgraded both into the 64bit OS to fully utilise what I have.

If you are in the general PC use, 32bit might be more easy-to-configure option due to the good availibility of plugins and etc (Java, flash and other  media related). If you are into the serious computing use, 64bit will certain give you the boost.

Good Luck. I think there are also some indian vendor that sells 64bit DVD (if i didn't remember wrongly) where you can just buy from store.

32bit os is not guaranteed to work on 64bit hardware. It does in a lot of situations,[ but its not perfect.]("http://ubuntuforums.org/showthread.php?t=395164")

The plugins for your browser are easily fixed. The only one that isnt avilable for the 64bit browser is Sun Java, but there is icedtea, and othe open source versions. Flash works, vlc plugin works, mplayer works, ect. If you absolutely must have sun java, it takes all of 2 minutes of answering a few yes/no questions[ to install a 32bit browser.]("http://ubuntuforums.org/showthread.php?t=202537")

---

### Post by in_flu_ence on 2008-05-17
Probably you are right , kilz. I shouldn't be too generalised that 32bit works for me means works for all.

For the plugins, that's what i feel from the post in the 64bit forum. That always pop up every time besides the hardwire driver posts about 64bit compatibility.

I have no doubt about using the 64bit OS myself since i converted. I taking a longer term view that I spend some time to get things smooth and I am confident that Ubuntu, Linux and my system will work for me when I need it to.

my 2 cents

---

### Post by cyclouno on 2008-05-17
@Xiong Chiamiov

good to know that some are really running them.

@in_flu_ence

yp came to know that some vendors do sell 64bit os also have asked a few of my friends to get one for me.

@kilz

thanks for lettin us all know that probs do exist with 32 bit on 64 bit cpus - you just logged tons of complaints I guess. And i went on to install 32 bit ubuntu hardy on my 64 bit AMD dell lappy and it works fine for me just like my pc.also didn't find any problems till now or just that I am not noticing them. Had a bad time with the "White Screen of Death" with Nvidia drivers but fixed them with the beta versions.

Thanks mates.

---

