---
title: "Mounting &quot;.vdi&quot; files in 64 bit 8.04 Ubuntu"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by fuzzylunkinz on 2008-06-25
Hello there,

I've been using Ubuntu for quite some time now - although not avidly, as I still use Windows for stuff (Allegiance).  I recently installed the amd64 version of Ubuntu 8.04 and everything works great.  I installed Virtual Box and I was wondering how I would go about mounting the ".vdi" files that Virtual Box creates.

I found several links, and went onto the main Ubuntu channel, and found someone to help me out.  But he could only do so much, as he was running a 32 bit install.  I found (and several others recommended) this link:  [http://muralipiyer.blogspot.com/2008/02/mounting-virtualbox-vdi-disk-authentic.html](http://muralipiyer.blogspot.com/2008/02/mounting-virtualbox-vdi-disk-authentic.html)

I get to the part where I have to ldd 'vditool' and this happens:
```

user@computer:~/Desktop$ ldd vditool
    linux-gate.so.1 =>  (0xffffe000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f1d000)
    libuuid.so.1 => /usr/lib32/libuuid.so.1 (0xf7f1a000)
    librt.so.1 => /lib32/librt.so.1 (0xf7f10000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf7f0c000)
    VBoxDD.so => not found
    VBoxRT.so => not found
    libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0xf7e52000)
    libm.so.6 => /lib32/libm.so.6 (0xf7e2c000)
    libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7e21000)
    libc.so.6 => /lib32/libc.so.6 (0xf7cd2000)
    /lib/ld-linux.so.2 (0xf7f49000)

```***NOTE:**  Originally libuuid.so.1 was not found, also.  I searched and found 'libuuid1_1.38-2ubuntu2.1_i386.deb' and extracted the needed file to /usr/lib32 (I remember finding a topic that explained what to do).*

So, I went searching the internet for VBoxDD.so and VBoxRT.so.  I found them in a RPM package.  I downloaded this package, installed alien, and tried to convert it, which ended unsuccesfully.  For a while I just gave up.  This was when I logged onto the main Ubuntu IRC channel.

I had to wait a while, but eventually _ASULutzy_ acknowledged me.  He asked me if I had searched my filesystem for those two files.  :oops: I hadn't, of course.  So I searched for these files, and they showed up in /usr/lib.  When *he* had searched for these files, he found them in /usr/lib/virtualbox.  All he had to do was copy them to /usr/lib, and it went fine and dandy for him (remember, he's using 32 bit).

I tried copying mine to /usr/lib/virtualbox, which didn't work (I hadn't expected it to, either).  I have no clue where it's trying to look for these two files.

If anyone could help me out with this specific problem, that would be great.  But, I know it's not necessary, as it seems all I really need is to find the offest number to mount the file with.

In conclusion, I would like to:
1)  Know how to fix the problem that I'm having with 'vditool'.
2)  Find a different, possibly easier way to mount ".vdi" files.

Thanks,
Fuzz

---

### Post by fuzzylunkinz on 2008-06-26
No one has even the slightest tip?  It seems this is a tough problem :(.

---

### Post by Cappy on 2008-06-26
```
sudo cp /usr/lib/VBoxDD.so /usr/lib32/VBoxDD.so
```
```
sudo cp /usr/lib/VBoxRT.so /usr/lib32/VBoxRT.so
```

There's a 64-bit package of virtual box too.

---

### Post by fuzzylunkinz on 2008-06-26
I actually tried that before.  No progress.

This is the 64 bit version of Virtual Box.

---

### Post by Cappy on 2008-06-26
Oh .. this vditool is something you downloaded individually .. it's the vditool that is 32-bit and the rest of virtualbox is 64-bit. vditool can't use the 64-bit libraries and thus you have the problem.

You have two options:
Download [http://http.us.debian.org/debian/pool/main/v/virtualbox-ose/virtualbox-ose_1.6.2-dfsg-1_amd64.deb](http://http.us.debian.org/debian/pool/main/v/virtualbox-ose/virtualbox-ose_1.6.2-dfsg-1_amd64.deb) (which I've included in the code below: )
> 
wget [http://http.us.debian.org/debian/pool/main/v/virtualbox-ose/virtualbox-ose_1.6.2-dfsg-1_amd64.deb](http://http.us.debian.org/debian/pool/main/v/virtualbox-ose/virtualbox-ose_1.6.2-dfsg-1_amd64.deb)
dpkg -x virtualbox-ose_1.6.2-dfsg-1_amd64.deb virtualbox_vditool
sudo mv virtualbox_vditool/usr/lib/virtualbox/vditool /usr/lib/virtualbox/vditool; sudo ln -s /usr/lib/virtualbox/vditool /usr/bin/vditool


The other option is to install the 32-bit library, in which case what you need to do is download the 32-bit (x86) ubuntu library.
Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and use
```
getlibs --build -i insert_debian_files_name_here.deb
```

---

### Post by fuzzylunkinz on 2008-06-26
Hmmm . . . .

Yeah, I tried looking for a 64 bit version of vditool.  Oh well.

I will try the former when I have more time - thanks!

---

### Post by scottfree on 2008-08-18
I had a similar problem when trying to convert a VMware image to a VirtualBox image.  I found the solution [here]("http://liquidat.wordpress.com/2007/11/23/howto-transform-a-qemu-image-to-a-virtualbox-image/").  Basically, you replace vditool with VBoxManage.  VBoxManage has a 64-bit version and is in the current version.

HTH

---

### Post by mkmm on 2008-08-20
I have solved this problem regarding vditool on my 64bit machine with a little workaround without any extra software. All you need is to find the beginning of the ntfs partition in the vdi image. It has an unique signature.

Here is my script called mntvdi:
```
#!/bin/sh
# mount a virtualbox image to /mnt/vdi
# usage: mntvdi drive.vdi (include the complete path)

# find the offset where the ntfs partition begins (0xeb52904e544653)
# in the first 1000 kB of the vdi image
DOUBLE=`dd if=$1 bs=1024 count=1000 2> /dev/null | xxd -p -c 256 | \
sed -e ":a" -e "$ s/\n//g;N;b a" | grep -b -o eb52904e544653 | \
sed -e "s/:.*//"`
OFFSET=`awk "BEGIN { print $DOUBLE/2 }"`

# mount it
sudo mkdir -p /mnt/vdi
sudo mount -t ntfs-3g -o loop,ro,offset=$OFFSET,iocharset=utf8,dmask=022,fmask=133 $1 /mnt/vdi

#unmount it with "sudo umount /mnt/vdi"
```

---

### Post by dbreese on 2008-09-08
You can also just export your "LD_LIBRARY_PATH" which is used to find libraries.

$ export LD_LIBRARY_PATH=/usr/lib/virtualbox
$ ldd vditool

Beats copying stuff around and messing with lib dirs.

I'm still having issues with mounting the VDI -- it complains that it "failed to read last sector (31439141): Invalid argument".  Further searching around looks to indicate that I'm trying to mount a dynamic (not fixed) drive, so I wonder if it is trying to seek to the end of the dynamic grow-as-you-go file and it doesn't yet exist.

---

