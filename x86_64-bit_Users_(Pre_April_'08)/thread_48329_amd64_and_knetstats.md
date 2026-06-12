---
title: "amd64 and knetstats"
date: 2005-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ajkeys on 2005-07-12
I cant seem to figure out what packages I need to install in order to compile knetstats or if someone had a amd64 .deb file that would be good too. I'm almost positive its because I am missing some package, but I dont know. Also I'm kinda new at this. I can post the errors during compiling if need be. I have also tried other programs like knemo and gkrellm, but I just like the clean look of knetstats. Any help greatly appreciated.  ](*,)  Thanks.

Forgot to mention that I am using Kubuntu.

---

### Post by Jet2k5 on 2005-07-12
My guess is that if you want to compile any programs at all on Ubuntu you need the *build-essential*  package.

So do the following I'm guessing,

```
sudo apt-get install build-essential
``` 

Hope this is what you are looking for.

---

### Post by ajkeys on 2005-07-12
Thanks for your suggestion. I do have the build-essential package installed already, cause I can compile other programs. It uses "scons" to compile its package which I believe uses python which I also have installed (and the scons package also). I finally gave up and looked for an alternative and I found knemo which is great and looks clean too. Thanks for all your help anyways!

---

