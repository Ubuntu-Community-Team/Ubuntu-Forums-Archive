---
title: "rar archives, which is best for 8.04?"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by digisoft on 2008-04-26
I just realized that all my archive files are rar's, Which is the best choice for working with rar files in 8.04? I saw there are a few to choose from but don't know which is the better choice.

Thanks!

---

### Post by tamoneya on 2008-04-26
just do ```
sudo apt-get install rar
```
Now you will be able to use your rar archives with the built in archive manager.

---

### Post by digisoft on 2008-04-26
excellent, exactly what I was hoping for. I had that one already set to install through synaptics but saw another choice so I decided to ask which was best before installing. As usual the help from people here has been incredible. Thanks to the helpful people here I've breezed through getting Ubuntu working great even with my broadcom wireless. 

Thanks!

---

### Post by tamoneya on 2008-04-26
glad to hear that at least one user is not having trouble with hardy.

---

### Post by digisoft on 2008-04-26
> **tamoneya said:**
> glad to hear that at least one user is not having trouble with hardy.

no real trouble, sure a few things needed a little adjusting or some files installed, but nothing any worse than what I'd go through with XP. Any OS you install will require some drivers downloaded or updated and things adjusted. The difference is in the fact that I don't expect ANY OS to install 100% perfect with no adjustments.

---

### Post by Lloyd09 on 2008-04-27
i tried the sudo apt-get install rar and this is waht i got:

bryan@bryan-desktop:~$ sudo apt-get install rar
[sudo] password for bryan: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bryan@bryan-desktop:~$ 

any suggestions, and i'll provide any info needed about my computer.

---

### Post by malathion on 2008-04-27
> **Lloyd09 said:**
> i tried the sudo apt-get install rar and this is waht i got:

bryan@bryan-desktop:~$ sudo apt-get install rar
[sudo] password for bryan: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bryan@bryan-desktop:~$ 

any suggestions, and i'll provide any info needed about my computer.

Some other application is accessing the database, mostlikely you are downloading updates or you have synaptic open. Wait for these apps to finish and close them, then try again.

---

### Post by digisoft on 2008-04-27
you can also install it from applications, add/remove programs. Just open it up and do a search for rar and you can install it easily.

---

### Post by helknight on 2008-08-03
It doesn't works on 64-bit Ubuntu.. I'm tired of installing it.. can you please rescue me..

---

### Post by dominiquec on 2008-08-03
Actually, I think what you want is unrar.

```
sudo apt-get install unrar
```

After that, you should be able to open your archives from the Archive Manager.

On the command line, it's:

```
unrar x myarchive.rar
```

---

### Post by Breepee on 2008-08-04
I recommend converting/switching to 7zip though. Compresses about as good as rar and it completely opensource and works everywhere, any architecture.

---

### Post by AlanAbbott on 2009-07-06
I'm installing a new machine with a base of UBUNTU 64 9.4, I ran "sudo apt-get install rar" and then directly from Places I extracted the contence of a multiple part rar file to a single iso. No need for "unrar". 7-zip is cmd line prg, usefull in scripts but not for random work with files, archives, datasets.

---

### Post by Elim_Garak on 2009-07-06
> **AlanAbbott said:**
> I'm installing a new machine with a base of UBUNTU 64 9.4, I ran "sudo apt-get install rar" and then directly from Places I extracted the contence of a multiple part rar file to a single iso. No need for "unrar". 7-zip is cmd line prg, usefull in scripts but not for random work with files, archives, datasets.

7 works with file roller, too.  I've never had any problems with it in Linux.  It's a little harder to set up on M$ boxes, but that's no surprise.  There, I found, you have to train Windoze as to which should be the default program to open .7z files.

I admit that in Linux, I, too, used rar a lot more than I should be, simply out of an age-old habit.  When I started using Windows, I was always using lha archives, from my Amiga habit, and now I have the rar inertia going.  There's nothing wrong with 7-zip, as long as I remember to use it, and it does tend to do a better job at compression.

---

