---
title: "Wine won't install"
date: 2008-01-16
forum: Wine
---

### Post by Nordfjord on 2008-01-16
I'm pretty new to all this, and a fair amount of what I do involves copying stuff from guides (like 
[http://ubuntuforums.org/showthread.php?t=624644]("this sticky post") and [http://www.winehq.org/site/download-deb]("the one on the Wine page")). So I hope I'm not just making an idiot out of myself. Anyways, when I use
```
true@ubuntu-iBook:~$ sudo apt-get update
```
I get (at the end of a very long block of text)
```
Failed to fetch http://wine.budgetdedicated.com/apt/dists/feisty/Release  Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Is there not a ppc version of wine? Is it hidden away? What's going on?

Any help would be greatly appreciated. Thanks.

---

### Post by luisromangz on 2008-01-17
I don't think there is a Wine version for PPC architectures, not because of Wine itself, but because there isn't Windows software for PPC, as Windows is an x86 only OS. So you aren't able to run Windows apps without emulating one instruction set in another architecture, which is fairly slow and because of that useless. Also it would be against WINE's philosophy, as Wine Is Not an Emulator :P

---

### Post by Nordfjord on 2008-01-19
Thanks, I can see what you mean. I don't think my little g3 ibook could manage running an emulator and wine and the windows apps, so I guess i'll just deal with it. Thanks for the reply.

---

