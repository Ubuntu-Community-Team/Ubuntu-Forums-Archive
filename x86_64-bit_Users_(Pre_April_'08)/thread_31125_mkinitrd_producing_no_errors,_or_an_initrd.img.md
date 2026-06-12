---
title: "mkinitrd producing no errors, or an initrd.img"
date: 2005-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by rsw on 2005-05-01
Anyways notice this? 

It doesn't give any errors, but doesn't create the initrd.img file! I've done this with the x86 version of ubuntu without a problem, however it just isn't making an image in the amd64 version. Am I alone here?

For instance, here's the command I'm giving it:

# mkinitrd -o initrd.img-2.6.11.8-amd64 2.6.11.8-amd64 


And to answer the obvious questions:

# ls -1 /lib/modules
2.6.10-5-amd64-generic
2.6.11.8-amd64


# dpkg -l | grep initrd-tools
ii  initrd-tools   0.1.77ubuntu3  tools to create initrd image for prepackage

---

### Post by rsw on 2005-05-01
installed this binary pkg: [http://packages.debian.org/testing/utils/initrd-tools](http://packages.debian.org/testing/utils/initrd-tools)

it seems to create an initrd.img :) it's 0.1.78 as opposed to ubuntus' 0.1.77

---

