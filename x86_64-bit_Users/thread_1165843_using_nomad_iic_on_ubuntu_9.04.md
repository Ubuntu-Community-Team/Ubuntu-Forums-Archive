---
title: "using nomad iic on ubuntu 9.04"
date: 2009-05-21
forum: x86 64-bit Users
---

### Post by donkyhotay on 2009-05-21
I found my old nomad iic MP3 player the other day which I lost about 5 years (before I migrated to linux). The device still  works perfectly but I'm having problems getting it to communicate with ubuntu so I can update my music on it. I found installation instructions [here](https://help.ubuntu.com/community/Nomadii) however when I try to convert the RPM with alien I get version mismatch errors (RPM is for i386 and I have x86_64) and if I try to compile from source I get error:
```

low_level.c:31:23: error: linux/usb.h: No such file or directory 
low_level.c:40: warning: ‘packed’ attribute ignored                                                                                                                     
low_level.c: In function ‘nomadII_read_command’:                                                                                                                        
low_level.c:55: error: ‘USB_DIR_IN’ undeclared (first use in this function)                                                                                             
low_level.c:55: error: (Each undeclared identifier is reported only once                                                                                                
low_level.c:55: error: for each function it appears in.)                                                                                                                
low_level.c: In function ‘nomadII_write_command’:                                                                                                                       
low_level.c:69: error: ‘USB_DIR_OUT’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_read’:
low_level.c:85: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_write’:
low_level.c:118: error: ‘USB_DIR_OUT’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_send_command’:
low_level.c:151: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_send_command_nowait’:
low_level.c:210: error: ‘USB_TYPE_VENDOR’ undeclared (first use in this function)
low_level.c:210: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c:210: error: ‘USB_RECIP_OTHER’ undeclared (first use in this function)
low_level.c:220: error: ‘USB_ENDPOINT_XFER_CONTROL’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_reset_pipes’:
low_level.c:292: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c:300: error: ‘USB_DIR_OUT’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_ctl_msg’:
low_level.c:323: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘requesttype’
low_level.c:323: error: ‘USB_TYPE_VENDOR’ undeclared (first use in this function)
low_level.c:323: error: ‘USB_RECIP_OTHER’ undeclared (first use in this function)
low_level.c:324: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘request’
low_level.c:325: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘value’
low_level.c:326: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘index’
low_level.c:327: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘length’
make[1]: *** [low_level.o] Error 1

```
even after installing every libusb*-dev package available in the repos. I know that it's probably too old/proprietary to bother messing with but I'd like to start using it again if I can.

---

### Post by pixel :-) on 2009-05-21
Thats old!!!!

1)The easy way:
Download a hard disk image of feisty and run it in virtual box. If you are happy with this solution, you are donne.

2)Maybe but i doute it, you'll find out:
It would be possible to run it in the native system, but since it must conect to the usb, i don't know. It probably needs a compatible kernel, if its a kernel module.

extract the binary by hand

rpm2cpio nomadII-utils-0.8-2.i386.rpm > file

then open it with archive manager

collect by hand all the old libs that are required (in the link you provided), extract them and put then in a folder in your home. Including "libreadline.so.4" (32bit of feisty). You may need to dig down in the dependencies. "ldd" will tell you what libs it depends on, remember you must collect the old libs, any dependency that is rezolved isn't good for you.

run the executable with the associated folder of libs, and pray that it works

/lib/ld-linux.so.2 --library-path PATH EXECUTABLE

Don't use getlibs, it will install modern libraries.

3)Compilation:
I think it want linux header "linux/usb.h" I think

sudo apt-get build-dep linux

will fix some of the errors

---

### Post by donkyhotay on 2009-05-22
Thanks for the suggestions but I think I'm going to throw in the towel on this one. I went so far as to actually install XP on a VM and found out that while the drivers are still available to download the proprietary music manager program required for the device to migrate data to/from a PC can not be found anywhere. Create doesn't offer it since they consider the device obsolete and no one else can give it away because of the copyright. I'll just chalk it up as yet another example as how proprietary formats hurt consumers. I'll just be more discriminating when I next buy a portable music player so that I won't have to worry about getting stuck with a paperweight just because some company decides I need to buy something new.

---

### Post by xt8088 on 2009-09-19
I'm trying to do the same thing.  I gave this MP3 player to a friend of mine and she keeps asking me to update the music for her on the player.

Anyways, I got through the alien proceedure, but in the end nomadii doesn't see the player...

Everything else installed as per the instructions on [the same page]("https://help.ubuntu.com/community/Nomadii")

Any help?

BTW I'm using 32bit 9.04

:confused:

> **donkyhotay said:**
> I found my old nomad iic MP3 player the other day which I lost about 5 years (before I migrated to linux). The device still  works perfectly but I'm having problems getting it to communicate with ubuntu so I can update my music on it. I found installation instructions [here](https://help.ubuntu.com/community/Nomadii) however when I try to convert the RPM with alien I get version mismatch errors (RPM is for i386 and I have x86_64) and if I try to compile from source I get error:
```

low_level.c:31:23: error: linux/usb.h: No such file or directory 
low_level.c:40: warning: ‘packed’ attribute ignored                                                                                                                     
low_level.c: In function ‘nomadII_read_command’:                                                                                                                        
low_level.c:55: error: ‘USB_DIR_IN’ undeclared (first use in this function)                                                                                             
low_level.c:55: error: (Each undeclared identifier is reported only once                                                                                                
low_level.c:55: error: for each function it appears in.)                                                                                                                
low_level.c: In function ‘nomadII_write_command’:                                                                                                                       
low_level.c:69: error: ‘USB_DIR_OUT’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_read’:
low_level.c:85: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_write’:
low_level.c:118: error: ‘USB_DIR_OUT’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_send_command’:
low_level.c:151: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_send_command_nowait’:
low_level.c:210: error: ‘USB_TYPE_VENDOR’ undeclared (first use in this function)
low_level.c:210: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c:210: error: ‘USB_RECIP_OTHER’ undeclared (first use in this function)
low_level.c:220: error: ‘USB_ENDPOINT_XFER_CONTROL’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_reset_pipes’:
low_level.c:292: error: ‘USB_DIR_IN’ undeclared (first use in this function)
low_level.c:300: error: ‘USB_DIR_OUT’ undeclared (first use in this function)
low_level.c: In function ‘nomadII_ctl_msg’:
low_level.c:323: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘requesttype’
low_level.c:323: error: ‘USB_TYPE_VENDOR’ undeclared (first use in this function)
low_level.c:323: error: ‘USB_RECIP_OTHER’ undeclared (first use in this function)
low_level.c:324: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘request’
low_level.c:325: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘value’
low_level.c:326: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘index’
low_level.c:327: error: ‘struct usbdevfs_ctrltransfer’ has no member named ‘length’
make[1]: *** [low_level.o] Error 1

```
even after installing every libusb*-dev package available in the repos. I know that it's probably too old/proprietary to bother messing with but I'd like to start using it again if I can.

---

