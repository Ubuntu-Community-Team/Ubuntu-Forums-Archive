---
title: "Failed to start the x server, API mismatch. Nvidia kernel module version"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jagdave on 2007-11-08
When booting ubuntu 7.10 after a seemingly correctly installed new nvidia driver.
With blue background and a white window with the text:
"Failed to start the x server. Would you like to see output"
Then it tells me Error: API mismatch: this nvidia driver component has v 100.14.19
but the nvidia kernel module's version does not match.
Failed to initialize nvidia kernel module!

Ok, now I will explain. This happened when I followed a howto for uninstalling old
nvidia driver and then using nvidias own setup to install it. Because i heard it was the way to do it.
I did not use envy. 

I can startx if I write sudo modprobe -r nvidia but the same problem happens everytime i
boot into ubuntu. And when I do this and get into x i get hindered by errors popups saying stuff like "Failed to run /usr/sbin/synaptic '--hide-main-window' -- bla bla - Unable to copy the user's Xauthorization file. So for example I cant run update manager.

I've tried to sudo rm /lib/linux-restricted-modules/ but it says it can't since it's a directory.
I am at a total loss. Since this happened I have stopped using ubuntu indefinately, nowhere ive looked brings me an easy to follow guide to fix this problem.
I have read alot of the posts dealing with this or similar problems but they are dead and/or did not help me.

If someone have time and are willing, I would be greatly thankful for some direct help.

---

### Post by kiepmad on 2007-11-08
try to uninstall the nVidia driver: type in the consol
```

sudo apt-get remove nvi

```

press tab to find the correct entry.

after that, install a new driver by typing in the console:
```

sudo apt-get install nvidia-glx-(legacy/new)

```

If your graphic chip is geforce2 or older, use the 'legacy' driver, otherwise use 'new' driver.
to enable the driver, type:
```

sudo nvidia-glx-config enable

```

Good luck!

---

