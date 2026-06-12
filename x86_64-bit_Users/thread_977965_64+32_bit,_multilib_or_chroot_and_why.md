---
title: "64+32 bit, multilib or chroot and why?"
date: 2008-11-10
forum: x86 64-bit Users
---

### Post by MNKyDeth on 2008-11-10
My machine is a Core 2 Duo E6750 running at 3ghz. 4gigs of ram, 500 gig hdd, 4gig Gigabyte I-ram, audigy2zs and a gtx260 896mb of ram.

I have been using 32bit based distro's for the fact I own nearly all available commercial games that are made for linux. Most all of these games work well even in multilib distro's like FC, opensuse and mandriva.

My problem is I believe I have settled down with my overall choice being ubuntu 32bit as I have tried 64bit ubuntu back in 7.x days. Back then 64bit ubuntu was just that, 64bit. It wasn't multilib or anything so it was immediately removed from my comp for something else.

Now, I really do enjoy 32bit 8.10 ubuntu and I think I may stick with it this time. But I still want a 64bit OS deep down because of all the ram that is wasted in my machine. I do other things than just game hence the I-ram for speeding along compiles or making quick test installs of different versions of linux, etc, etc.

1.) Is 8.10 of ubuntu still pure 64bit?
2.) Why hasn't ubuntu done a multilib version if so?
3.) How do people go about using pure 32bit apps? chroot?
4.) If so, on a 500gig hdd should we split the install of two differing OS's 50/50?
5.) How do you link between the two OS's so you don't have to constantly chroot?
6.) When installing proprietary software like drivers do you have to install the 32bit version and the 64bit version? (note: I know the nvidia binary blob installs the 32bit portion of the driver during the 64bit install if you say yes when prompted).
7.) Is there a way to make ubuntu 64bit multilib if it isn't from a fresh install?

TIA for anyone that can answer any of this.

---

### Post by Npl on 2008-11-10
1) From the getg-go - yes. Install the ia32-libs package and you get alot of popular 32 bit libraries (enough to run a good amount of 32-bit software).
2) dunno what you mean with multilib, the kernel can deal with 32-bit apps and you have 32-bit folders for libraries. Everything you need to get 32-bit apps working... but you still should try hunting down the native 64-versions.
3) run them just like 64-bit apps?
4) [ia32-libs takes ~100MB]("http://packages.ubuntu.com/search?keywords=ia32&searchon=names&suite=intrepid&section=all"), bu theres no need for seperate partition
5) No idea
6) The driver itself must fit your architecture. there are some additional libraries to allow 32-bits apps to use the card (opengl) but they arent necessarily the same as in the 32-bit package. 
7) see 1,2

---

### Post by Kilz on 2008-11-10
1. There is no way to install 32bit software with apt, but it is possible and some 32bit libraries are packaged.
2. Read answer to #1.
3. Chroot's are used only by those that want a lot of space used up for no good reason. 32bit applications are the rare exception, not a common need.
4. Only if you want to waste time, hard drive space, and like to make things hard on yourself for an imagined need.
5. That isnt what a chroot is. A chroot is an install within an install in essence doubling your install. 
6. Read answer to #5
7. Use Getlibs.

---

### Post by Shingoshi on 2009-06-05
If you're running a 64-bit kernel, you'll need to compile kernel modules in 64-bit. Then the 32-bit system will use those modules.

Shingoshi

---

