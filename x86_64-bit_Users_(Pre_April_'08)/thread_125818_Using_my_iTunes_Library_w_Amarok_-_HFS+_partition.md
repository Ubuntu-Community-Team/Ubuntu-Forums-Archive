---
title: "Using my iTunes Library w/ Amarok - HFS+ partition"
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by spaceballl on 2006-02-04
Hi there,

So i'm slowly adapting to this whole PPC linux thing. I have OS X on my other partition, and I'd really like to use my iTunes Music Library as Amarok songs. However, once I mount the HFS+ partition, a bunch of the folders are locked. If I type "sudo su", then I can access the folders, but I don't know how to do that from within Amarok. ANy ideas? Thanks!

-Kevin

---

### Post by Protex on 2006-02-05
Just a though, could you try running Amarok as root?

I'm assuming that would give you access to protected folders.

---

### Post by spaceballl on 2006-02-05
Well, I sorta tried. Under menu editor, I added "sudo" before the command and then it didn't start up. When it said "run as different user," i tried checking the box and typing in root, but still no cigar.

---

### Post by autocrosser on 2006-02-05
I've posted the answer to this one before---in OSX-get info your iTunes folder & set it up with no permisions (depends on the version of OSX as to where in get info the checkbox is) --the long term answer is to have iTunes in a seperate partition so you can add-delete music from both operating systems.

---

