---
title: "skype on amd64 can't load libs"
date: 2005-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by KickYou... on 2005-08-11
Hello everyone,

i try to run skype under the alsa-oss emulation with aoss skype, but i get following error messages:

   */skype: error while loading shared libraries: /usr/lib/libaoss.so: cannot open shared object file: No such file or directory*

Like the same error with esddp skype:
   *skype: error while loading shared libraries: /usr/lib/libesddsp.so.0: cannot open shared object file: No such file or directory*

Can anyone help?

thx

---

### Post by DancingSun on 2005-08-11
Well, do those files actually exist? Can you do a file search for them?

---

### Post by KickYou... on 2005-08-12
yes, all files exists in the /usr/lib Directory.

thx

---

### Post by DancingSun on 2005-08-12
Hmm, someone in the "amd64 package" thread was able to install and run skype, but when she access any of the menu functions, nothing happens.  However, she did not get any error messages like you did...but you might want to check the thread out anyway.

Which package did you use to install skype?  And what's this part about alsa-oss emulation?  Did you have to use some special command to start skype?  Sorry, I'm not really a skype user, but I'm trying to help you help yourself :)

---

### Post by KickYou... on 2005-08-13
skype is working fine without sound. Only the audio properties are not usable bacause skype works only with oss (/dev/dsp) and i have alsa installed. So If i want to use skype with alsa i need the alsa-oss libs for oss emulation and then i get the  error messages. I think skype is ok, but can a 32bit Application use 64bit compiled libs ?

---

