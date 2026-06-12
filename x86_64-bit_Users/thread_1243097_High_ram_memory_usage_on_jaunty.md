---
title: "High ram memory usage on jaunty"
date: 2009-08-17
forum: x86 64-bit Users
---

### Post by Copitox on 2009-08-17
Hi! i don't know if this is the right place for this thread.

The thing is that i just installed Kubuntu Jaunty 64bits on my laptop (also installed KDE 4.3) and i noticed a high ram memory usage. When I first looked System Monitor it said system was using almost 900MiB of ram memory.. i also noticed that Xorg was consuming 100MiB! I reduced it by using Konqueror instead of Firefox (Konqueror is slower, though) and disableing a few desktop effects. My system is now using between 400 and 500 MiB depending on what i do.. i think that's very normal, but using almost 1GiB it's a lot!

What do you think? Is that normal? How can i improve Firefox performance on KDE?

PS:if this is not the right place, i'm truly sorry.
PS2: sorry for my bad english, i'm from southamerica

Thank you a lot!

---

### Post by minisori on 2009-08-18
Unless the ram use is due to memory leaks, the more use of ram the better is. And 1 GB or even more is completely normal in linux.

Another thing is firefox being a resources eater.. :S

---

### Post by Raffles10 on 2009-08-18
> **minisori said:**
> Unless the ram use is due to memory leaks, the more use of ram the better is. And 1 GB or even more is completely normal in linux.

Another thing is firefox being a resources eater.. :S

1gb RAM usage in Linux is not normal for a system at idle. How can you even state what is normal for Linux when it covers so many different distributions ? This kind of statement is just crazy.

KDE is resource hungry and my experience of Kubuntu 9.04 was that approx' 600mb RAM was normal on my system when it was idling. These are difficult generalisations to make because all our systems are different, but 1gb sounds excessive to me.

---

### Post by movieman on 2009-08-19
> **Raffles10 said:**
> 1gb RAM usage in Linux is not normal for a system at idle. How can you even state what is normal for Linux when it covers so many different distributions ? This kind of statement is just crazy.

Linux will use all the available free memory for disk cache, so if you have 1+GB of RAM then using 1+GB for programs and disk cache is both expected and normal after the OS has been running for a while to cache enough files to fill up the RAM.

I don't believe there's any way to limit the disk cache size, since file data which doesn't need to be written back to disk will just be thrown away when programs need more RAM.

---

### Post by Slim Odds on 2009-08-19
> **movieman said:**
> Linux will use all the available free memory for disk cache, so if you have 1+GB of RAM then using 1+GB for programs and disk cache is both expected and normal after the OS has been running for a while to cache enough files to fill up the RAM.

I don't believe there's any way to limit the disk cache size, since file data which doesn't need to be written back to disk will just be thrown away when programs need more RAM.

There is more confusion about RAM usage then just about any other topic.

You are correct about the disk cache.

The bottom line is this: unused RAM is wasted RAM.

So using it for cache which can be easily and quickly used for something else if needed is a good thing.

---

### Post by Raffles10 on 2009-08-19
I have 2gb RAM. Ubuntu no matter how long it has been running has never used more than 600mb.

---

### Post by minisori on 2009-08-19
> **Raffles10 said:**
> I have 2gb RAM. Ubuntu no matter how long it has been running has never used more than 600mb.

That always depends of the use you give to the computer and how things are configured.. mine is using around 2.5 GB at moment, also swapping can decrease the amount of used ram, but who wants to swap to hd when you have enough faster memory. I even have the tmp folder in ram.

---

### Post by uncleV on 2009-08-20
> **minisori said:**
> ... but who wants to swap to hd when you have enough faster memory. I even have the tmp folder in ram.

Would you describe please how to make the system use more of the ram instead of swap? Or point to a web source?
I tried with the swapping percentage (and now don't remember how I did it) from 0 to 100% but System Monitor always gave me the same amount of RAM used - of about 35% when I was with 512+256 on 9.04x32 and now 11% with 4 GB on 9.04x64. It will be a good thing to make the rest of the RAM work instead of hard disks.

---

### Post by minisori on 2009-08-20
> **uncleV said:**
> Would you describe please how to make the system use more of the ram instead of swap? Or point to a web source?
I tried with the swapping percentage (and now don't remember how I did it) from 0 to 100% but System Monitor always gave me the same amount of RAM used - of about 35% when I was with 512+256 on 9.04x32 and now 11% with 4 GB on 9.04x64. It will be a good thing to make the rest of the RAM work instead of hard disks.

Don't worry about if it uses more or less ram, it will be used as needed.

To change the swappiness edit /etc/sysctl.conf and change/add the line vm.swappines=10 for example, (the smaller the number is the less it will swap to hd, you will have to try values and see which one works better for you).

To put tmp folder in ram add to fstab, (change the size as you want, also note that you will have less ram avaliable):
none /tmp tmpfs size=1024M,noexec,mode=1777 0 0

---

### Post by uncleV on 2009-08-20
Thank you very much, [minisori]("http://ubuntuforums.org/member.php?u=63095")
I'll try it.
And I'm sorry for the little offtop.

---

### Post by Copitox on 2009-08-23
> **Slim Odds said:**
> There is more confusion about RAM usage then just about any other topic.

You are correct about the disk cache.

**The bottom line is this: unused RAM is wasted RAM.**

So using it for cache which can be easily and quickly used for something else if needed is a good thing.


So windows vista is a great system because it uses lots of ram?

---

### Post by theozzlives on 2009-08-23
> **minisori said:**
> To put tmp folder in ram add to fstab, (change the size as you want, also note that you will have less ram avaliable):
none /tmp tmpfs size=1024M,noexec,mode=1777 0 0

Cool, kinda like RAMDISK in DOS. I'm gonna see if it gives more speed, I can afford 1 GB RAM.

---

### Post by Slim Odds on 2009-08-23
> **Copitox said:**
> So windows vista is a great system because it uses lots of ram?

No, it wastes tons of RAM.

Did you actually have a point?

---

