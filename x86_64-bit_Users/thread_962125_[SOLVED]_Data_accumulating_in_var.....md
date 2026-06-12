---
title: "[SOLVED] Data accumulating in /var...."
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by Cariboo1938 on 2008-10-28
Hello all,
I tried for quite a while to use "remastersys' to create a LiveDVD from my Heron-8.04-amd64 (fully updated until today) installation. 
I always got the message that "squashfs" exceeded 4 GB in size. The .iso file was never generated.
I noticed that data accumulated in the **_/var/cache/apt/archives_** directory.
By the time I checked there where about 290 .gz files.
What are they needed for?  and 
can they be deleted without harming the installation?
Any reply is appreciated.
Thanks
Cariboo

---

### Post by forger on 2008-10-28
The command:
```
sudo apt-get autoclean
```
..clears every package downloaded before that cannot be found in Ubuntu repositories anymore.

Also consider:
```
sudo apt-get autoremove --purge
```
Removes packages that were automatically installed as dependencies for some other package, safe to remove if they're listed here (means that the package/packages that were using them are no longer installed, so they aren't used) :)

---

### Post by Cariboo1938 on 2008-10-29
Thanks for the response..
I tried both commands and there are still *.deb and *.gz files from latest updates/installations and downloads/installations in /var/cache/apt/archives.
How save is it to remove them?
How can they be removed?

---

### Post by roelpeeters on 2008-10-29
> **Cariboo1938 said:**
> Thanks for the response..
I tried both commands and there are still *.deb and *.gz files from latest updates/installations and downloads/installations in /var/cache/apt/archives.
How save is it to remove them?
How can the be removed?
What you may want to try is the following:
```

sudo apt-get clean

```

This command will clean your /var/cache/apt/archives directory completely.

Roel

---

### Post by roelpeeters on 2008-10-29
Sorry, double post.

Roel

---

### Post by forger on 2008-10-29
well it's really safe to use either autoclean or clean, but I thought you wanted the apt packages to make a dvd with remastersys :)
my bad, I misunderstood what you were doing

---

### Post by Cariboo1938 on 2008-10-29
> **roelpeeters said:**
> What you may want to try is the following:
```

sudo apt-get clean

```
This command will clean your /var/cache/apt/archives directory completely.
Roel
Yes, that helped....thank you all for the input...:)

---

### Post by Fragadelic on 2008-10-30
Remastersys used to have "apt-get clean" in it until a user got really upset about it so I took it out.

I'd highly recommend cleaning the packages out before backup especially if you have a fast internet connection.

---

