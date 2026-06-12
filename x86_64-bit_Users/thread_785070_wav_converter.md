---
title: "wav converter"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by stockster on 2008-05-07
Looking for application that would convert and re-sample wav files.

Tried audacity; the saved re-sampled files  have the original sampling rates; it does not work.

Also tried sound converter; but there is no option for re-sampling wav files.


Appreciate any help

thanks.

---

### Post by jespdj on 2008-05-07
Audacity can certainly resample audio. You must have been doing something wrong.

Have a look at the Audacity documentation: [http://audacity.sourceforge.net/help/](http://audacity.sourceforge.net/help/)

---

### Post by vanadium on 2008-05-07
Indeed, you must set the proper project sampling rate for Audacity to produce resampled output. From the command line, sox can do the conversion.

---

### Post by stockster on 2008-05-07
solved.

The project sample rate had to be changed instead of the resample option in menu.

---

### Post by galaha on 2008-09-02
I try this piece of software under ubuntu 8.04(with apt-get install audacity). It crash while i'm doing export wav file after stereo to mono. segment fault.

---

