---
title: "That hoary ATI thing (again)"
date: 2005-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by chryz on 2005-02-07
Trying to get 3d acceleration working on ATI Mobility 9700, and following the XXX numbers of guides don't seem to go very far - I get as far as the following error when loading the module:

```
[fglrx:firegl_stub_register] *ERROR* Unable to the open some already present DRM kernel module!
``` 

I have the restricted modules, and I am using the latest kernel - 2.6.10-2-amd64-generic. Any way to making this work without recompiling the kernel manually to get rid of the builtin DRM thingy - any kernel without it to be seen in the near future?

Please comment if I'm attacking this problem from the wrong angle - ie. error is caused by something else.  ](*,)

---

### Post by chryz on 2005-02-12
Solved the problem for myself, but thought I'd include the information people might need to reproduce the solution I used. First off - they changed a lot of DRM code in the newer kernels, and the recently released drivers won't work with the precompiled kernels. The driver you can get from ATI won't compile out of the box, and needs to be altered.  ](*,) 

Fetch the kernel source package via apt-get (2.6.10) seem to work. Use the config from the folder /boot as a template, but since I don't know how to make initrd work you need to alter it: compile in support for ide chipset as well as the filesystems you use (probably ext2 as fallback with ext3 actually used - include both to be safe). Make sure to remover all support for Direct Rendering Manager (DRM) as it's incompatible with ATI binary drivers. Remember to make a symlink called /usr/src/linux pointing to the kernel source. Compile bzImage and modules. Install modules, and copy bzImage to /boot. Make an entry in /boot/grub/menu.lst either above or below the area marked automagic. Use one of the entries allready there as a template, but remove the initrd-part. Reboot and verify that everything's working. You'll see a LOT of warnings when compiling, but just ignore them.

Download the xorg rpm from ATI.com, unpack it using any tool necessary - you can do this directly from the filebrowser. Find the unpacked file called "agpgart_be.c", and replace the word "pci_find_class" with "pci_get_class". Compile and install like all other guides posted here.

---

