---
title: "unreal tournament lib and x probs"
date: 2007-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by nzadLithium on 2007-12-25
hey

i gots a problem if i launch the 32bit version of ut2004 i get this straight away
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: wrong ELF class: ELFCLASS64

i decided to copy and paste the lib from my 32 bit libs folder now it does kinda work but i would prefer to be running the 64bit binaries. It also centers across my dual screens (a few games seem to do this :S)

if i use the 64bit version i get the ut2004 loading or splash or whatever its called then it opens a window thats about 1/4 size of my screen then it dissapears and i get
WARNING: ALC_EXT_capture is subject to change!
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x186
  Serial number of failed request:  168
  Current serial number in output stream:  170

anyone know how to get the 64bit going?
anyone know how to make the game only go on one screen while in fullscreen? I could window it and move it but it isnt quite the same that way :S

any help with either is appreciated.

---

### Post by nzadLithium on 2007-12-25
i also just found out. i have no sound :S

---

### Post by Cappy on 2007-12-25
You'll need this: [http://www.gamershell.com/download_11985.shtml](http://www.gamershell.com/download_11985.shtml)
which contains a fix for 64-bit.

After installing the patch the 32-bit version probably won't work anymore so you'll need to edit part of /usr/local/bin/ut2004 to look like this:
```

# Let's boogie!
if [ -x "${UT2004_DATA_PATH}/ut2004-bin-linux-amd64" ]
then
        cd "${UT2004_DATA_PATH}/"
        exec "./ut2004-bin-linux-amd64" $*
fi

```

You'll probably want to soft link the UT directory's libSDL-1.2.so.0 to /usr/lib/libSDL-1.2.so.0 . Same for /usr/lib/libopenal.so.0 . If you're having sound trouble after that you should try changing your installed libSDL to the ALSA or OSS version as I've seen this fix posted.

---

### Post by nzadLithium on 2007-12-25
Cappy you da best man :D

I dunno why but soft links arent working. It just says that it cant find the library.
It could be something to do with my dodgy moving of the /usr directory
i moved it to my other disk which i just got then just soft linked it to /usr :S
dodgy way but i couldnt think of a better one that didnt involve repartitioning my disk lots of times :D

Anyway i got the files that those links would have pointed to stuck them into the UT2004 directory and then ran the 64 bit one. I gots sound and every thing now. Kinda stupid it didnt occur to me to try replacing the 64bit libs :D

ty for your help

---

### Post by nzadLithium on 2007-12-25
one other thing now. When i press exit in UT2004 it doesnt kill the process. I only noticed coz i've been running it through the terminal. I killed it by pressing ctrl + c but i dont want to have to go into the process manager every time i close UT just to make sure its not eating up the cpu. Any idea's on how to get it to quit? and how do i add thanks to ur stat counter?

---

### Post by nzadLithium on 2007-12-25
mmk maybe it does close off. i was playing just now i just checked process list and theres nothing there. must only happen when launched from terminal then :S

---

### Post by Perfect Storm on 2007-12-25
I have added it all now to 64 gaming guides:
[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004) 
Note: it's the DVD version.
Also that softlink didn't worked for me so I replaced them with symblink.
You'll also find other gaming guides - I'll test the others 32-bit guides to 64-bit, when I have time.

---

### Post by Cappy on 2007-12-25
> **Artificial Intelligence said:**
> I have added it all now to 64 gaming guides:
[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004) 
Note: it's the DVD version.
Also that softlink didn't worked for me so I replaced them with symblink.
You'll also find other gaming guides - I'll test the others 32-bit guides to 64-bit, when I have time.

There is a difference between softlinks and symlinks? I thought softlinks and symlinks were the same thing so I use the terms interchangeably.

---

### Post by nzadLithium on 2007-12-25
lol i thought they were the same too :S

---

### Post by Perfect Storm on 2007-12-25
Well, it could be me that had another understanding of softlink was :popcorn:
I always use the term symblink.

---

