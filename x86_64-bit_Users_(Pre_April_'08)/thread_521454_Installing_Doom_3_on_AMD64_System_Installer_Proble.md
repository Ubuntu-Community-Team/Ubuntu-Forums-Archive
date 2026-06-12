---
title: "Installing Doom 3 on AMD64 System: Installer Problems"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by GenuineXP on 2007-08-09
So I was very excited to learn that there are Doom 3 binaries for Linux. Just for kicks, I tried out the installer on an older laptop (that could never hope to run Doom 3) and it worked as expected. However, now that I have Ubuntu (x86_64) on my desktop, the installation fails! Here's the output:

sudo sh ./doom3-linux-1.3.1.1304.x86.run
Verifying archive integrity... All good.
Uncompressing Doom 3... (many ellipses)
./setup.sh: 279: /home/sean/.setup6159: not found
./setup.sh: 290: /home/sean/.setup6159: not found

I don't get it. I read that the x86 version should run on an AMD64 platform. Is .setup6159 some temporary directory the installer is supposed to create? I think I managed to somehow simply extract the files, but I'm not sure how to get them to work. I'd like to have it installed correctly. Not only that, but whenever I attempt to run the binaries I found, the terminal claims the files don't exist even though I can ls them!

Any help is appreciated!

---

### Post by Cappy on 2007-08-09
First, make sure you have the 32-bit packages installed
```

sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk lib32asound2 lib32stdc++6 libc6-i386
```

Maybe try
```

sudo su
./doom3-linux-1.3.1.1304.x86.run

```
or
```

sudo sh doom3-linux-1.3.1.1304.x86.run

```

---

### Post by GenuineXP on 2007-08-09
Thanks for the reply. Actually, I figured out I needed some other 32-bit libraries after I installed them to get Flash working. After that, everything just seemed to work without a problem.

---

