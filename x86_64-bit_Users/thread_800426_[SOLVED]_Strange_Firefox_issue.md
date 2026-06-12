---
title: "[SOLVED] Strange Firefox issue"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by jazzman65 on 2008-05-19
I'm sure this doesn't have anything to do with 64 bit, so I apologize if I'm posting this in the wrong forum.  I'm using 64 bit, so I thought I'd try here first.

Last night, I executed "sudo firefox" in the terminal, just to check for updates.  I guess I shouldn't have gone that route because now, every time I start Firefox (I'm using the FF 3 Beta 5), all my settings are gone.  Even when I change something, for instance, setting my home page, when I restart FF, the settings have reverted back to default.

Very strange and I'm just not sure what I've done by using the "sudo firefox" command to start it.  Anyone else ever had this problem?  I should also mention I've uninstalled and reinstalled FF about 3 or 4 times from the repository to no avail.

Thanks!

---

### Post by Ahadiel on 2008-05-19
If you load firefox as root (via sudo) then your settings are saved in your root accounts home folder. (ie. /root) Therefore the settings you changed while running firefox with sudo are saved under /root as opposed to /home/username/. Also, you should never run firefox as root. Updates for firefox will be made available through apt (Synaptic Package Manager, Update Manager, etc) when the Ubuntu repo managers get around to adding them.

---

### Post by jazzman65 on 2008-05-19
I didn't actually make any changes while running FF as root.  All I did was start it, check for updates, and then shut it down.  I've done that before and I've never had this problem before.  I certainly understand what you're talking about, but it just seems strange that this has never happened before.

Thanks for your input!

---

### Post by jazzman65 on 2008-05-26
Well, my solution turned out to be a clean re-install of 64 bit Hardy.  I'm sure I messed up the permissions of a file somewhere, but I never could quite figure out where.  Anyway, I had a dual boot of 32 and 64 bit and was ready to go with 64 bit 100%, so I didn't mind doing a clean install. 

I learned my lesson though:  I'll never "sudo" start firefox again!

---

### Post by Zorael on 2008-05-28
I'd wager your [FONT="Courier New"]~/.firefox[/FONT] directory had its permissions changed so you couldn't write to it. :>
```
$ sudo chown *user:group* ~/.firefox
```

---

### Post by aaron.d on 2008-05-28
> **Zorael said:**
> I'd wager your [FONT="Courier New"]~/.firefox[/FONT] directory had its permissions changed so you couldn't write to it. :>
```
$ sudo chown *user:group* ~/.firefox
```

thats it. Just running:

```
sudo firefox
``` 

will NOT take roots environment, but use your ~/.firefox or ~/.mozilla and in turn, change the ownership of anything it touches, making those files useless to your regular user.

---

### Post by jazzman65 on 2008-05-28
I agree.  However, that's exactly what I did:  sudo firefox.  I had done it before to enable the "Check for Updates" and had never had a problem until this time.  I nuked it with the clean install, but I never could exactly figure how I managed to change permissions.

Now, I'm currently trying to figure out why HH 64 only sees 3 of my 4 GB ram.  Overall, I remain a very enthusiastic user and supporter of Ubuntu!  :)

---

