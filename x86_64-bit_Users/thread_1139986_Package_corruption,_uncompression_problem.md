---
title: "Package corruption, uncompression problem"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by Basurero on 2009-04-27
Hi,
I've been having problems updating Ubuntu packages and downloading large files (see [bug #297766]("https://bugs.launchpad.net/ubuntu/+source/command-not-found/+bug/297766")).
It all boils down to this: I get to install the system perfectly (both i386 and amd64 versions) but when it comes to updating the system (using either "synaptic" or "apt-get") I am unable to consistently get a good repository download (for spanish speakers, check my [blog entry]("http://www.codexion.com/wpblog/2009/04/ubuntu-jaunty-no-funciona/")).
The compressed files seem to download correctly but when decompressing they fail with a bzip2 error. The thing is; it's not always the same file.
Sometimes changing the repository location helps, but that also is random because it ends up failing too. And when I eventually get no errors downloading the repository information, the packages I want to install get corrupted somehow.
At first I thought it had to be a hardware failure, but this already happened in October when I tried Ubuntu 8.10 and I have been running Opensuse 11.1 perfectly since then.
My specs:
[LIST]
[*] Motherboard GIGABYTE GA-M56S-S3
[*] Processor AMD Athlon X2 2000
[*] Memory KINGSTON DDR2 2 GB @ 667MHZ
[*] Graphics card NVIDIA GEFORCE PCI- EXPRESS FX 8400GS 512MB
[*] Hard drive SEAGATE 320GB SATA 3,5” 8MB 7200
[/LIST]
Any clues?
Thanks in advance

---

