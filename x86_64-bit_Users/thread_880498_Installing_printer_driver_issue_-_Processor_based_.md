---
title: "Installing printer driver issue - Processor based I believe"
date: 2008-08-05
forum: x86 64-bit Users
---

### Post by dai_vernon on 2008-08-05
I have a Samsung ML-2510 laser printer and I am having issues installing the driver.  I insert the CD and choose autorun and nothing happens.  Running the Autorun script via terminal (as root, to make sure), gives this error message:

```
root@taylorh-laptop:/home/taylorh# '/media/cdrom0/autorun' 
/media/cdrom0/Linux/install.sh: 1167: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted
```

There is a folder several levels down in the CD called x86_64 so it should be able to be installed on an amd64, right?  What's the matter?

---

### Post by dai_vernon on 2008-08-05
Never mind - a quick google search gave me [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting) which solved my problem promptly.

I'd just like to say that, in my opinion, Linux, and Ubuntu in particular, is one of the more enjoyable communities to be a part of, and that any frustration that I have had since adopting linux as my primary operating system of choice has paled in comparison to any windows-based frustration I have previously encountered.

---

### Post by Sef on 2008-08-05
Thank you for posting the solution to your problem, so that others may benefit.

---

