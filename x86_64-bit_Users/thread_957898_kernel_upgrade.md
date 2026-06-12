---
title: "kernel upgrade"
date: 2008-10-24
forum: x86 64-bit Users
---

### Post by Grant A. on 2008-10-24
Well, I updated the kernel like adept has said and now when I type:

"sudo apt-get <program>"

I get the thing saying this:

> 
The following packages were automatically installed and are no longer required:
  libghc6-quickcheck-dev libghc6-quickcheck-doc libreadline5-dev libgmp3-dev
  **libncurses5-dev** haddock **linux-headers-2.6.24-19** ghc6-doc libghc6-mtl-dev
  libghc6-mtl-doc libssl-dev haskell-utils ghc6 dwm-tools
  **linux-headers-2.6.24-19-generic** libgmpxx4ldbl libghc6-x11-dev
  libghc6-x11-doc
Use 'apt-get autoremove' to remove them.


Is it safe to run autoremove this time? Or will I end up with a useless system?

---

### Post by xen-uno on 2008-10-24
The update is the -21 kernel, correct? It's probably safe to do it that way but an alternative is to use Synaptic and search for **linux-image**. If 21 runs fine (mine does with all apps) and appears in your Grub boot list, then select all occurrences of the -19 kernel, then right click on each and select "Mark for Complete Removal". It will not remove -19 entries in the Grub boot list (menu.lst) if they still exist, as I recall, so you would have to do that manually.

---

