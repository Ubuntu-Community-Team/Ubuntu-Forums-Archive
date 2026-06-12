---
title: "32bit libcups.so.2"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ectospasm on 2007-05-10
I'm trying to install my printer, a Lexmark X1150,  using ppd files and libraries supplied by Lexmark.  I've installed the Lexmark shared libraries in /usr/lib32, but still the cups error_log (with debugging turned on) show that libcups.so.2 is missing.  Checking for /usr/lib/libcups.so.2 shows results, and symlinking the 64bit lib into /usr/lib32 gives an ELF error.  So, I've determined I need the 32bit version of libcups.so.2.  I just have no idea where to get it.  

Any clues?

---

### Post by ectospasm on 2007-05-10
I've figured out the long list of 32bit shared libraries I need, but now I get the message "Cannot Process Raster" in the cups error_log when I try to print.  I think this has something to do with the /usr/lib/cups/filter/rastertoz600 file, but I'm stumped there.

---

### Post by kuja on 2007-05-10
Download the i386 deb for libcupsys2, run 

dpkg -x packagename.deb ./libcups; 
cd libcups/usr/lib; 
sudo mv * /usr/lib32

---

### Post by ectospasm on 2007-05-10
> **kuja said:**
> Download the i386 deb for libcupsys2, run 

dpkg -x packagename.deb ./libcups; 
cd libcups/usr/lib; 
sudo mv * /usr/lib32

I already figured that part out.  Now I've got a different error, "Cannot Process Raster".

---

### Post by kuja on 2007-05-10
Sorry,  looks like you replied sometime while I was typing :P

I've got no idea about this new problem though. It is still possible that you're missing a file and it just doesn't feel like telling you about it. Apart from that I've got no  better ideas than consulting Google with some really good search terms.

---

### Post by ectospasm on 2007-05-10
I figured it out.  There was a laundry list of missing 32bit libs, which I painstakingly installed.  Of course, even after that it wouldn't work.  I ended up having to extract all of the header and utility files found in the rpms in the Lexmark supplied driver.  All in all a very tedious task, but I somehow found the process to be fun. (-:

Thanks for your suggestions.

---

