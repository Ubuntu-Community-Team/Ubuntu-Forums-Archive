---
title: "canon pixma mp600 to work in 64bit"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by teetee on 2007-05-10
Hi.

I would like to make mp600 to work with my 64bit Feisty. How?

I downloaded drivers from here: [http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx]("http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx")
But these seems to be 32bit versions... (right?)

Is there some other drivers that would work correctly? Or can I make these to work (these are from Canon, so I guess these would be best ones...)? 

Thank you!

---

### Post by zero-9376 on 2007-05-10
Hi, I just want to thank you for pointing out these drivers, I now have scanning functionality with my MP510 on ubuntu, I was in the process of setting up VMware to do it but you have saved me the trouble by pointing out these drivers. I haven't tried the printer drivers yet but will do so tomorrow, I used a package called alien to convert the .rpm (redhat package format) files to .deb (ubuntu/debian package format) by using the command
alien packagename.rpm --to-deb --scripts

I also had to apt-get install/ synaptic/add remove libpng3. libtiff4 might also be needed (i already had it installed). 

Hope this helps you and thanks again for pointing out the site, hopefully I will be able to remove turboprint (an exellent tool if your printer isn't supported and you dont need high res printing by the way). 
Excellent to see a major manufacturer now supporting linux (even if there aren't debs yet).

---

### Post by teetee on 2007-05-10
Glad if I could help. Got to check if those would help. Thanks.

---

### Post by teetee on 2007-05-10
Alien says:
> tt@kone:~/asennus/mp600$ sudo alien -d cnijfilter-common-2.70-1.i386.rpm 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cnijfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Virhe 1
find: cnijfilter-common-2.70: No such file or directory


So, what to do to be able to make those rpm:s to dev?

Where can I get thos required libcups stuff? (Did I see somewhere something about them? Got to check, still if anyone knows what I should do, please tell me...)

---

### Post by teetee on 2007-05-10
I downloaded licups.so.2 with this help:
[http://ubuntuforums.org/showthread.php?t=438073]("http://ubuntuforums.org/showthread.php?t=438073")

Didn't help... Alien says same as before.

---

### Post by zero-9376 on 2007-05-10
just tried the printer driver and it didnt work, the alien process didnt cause me any problems as you have above. i installed the printer using the default config and pointing to the ppd file (/usr/share/cups/model/cannomp510.ppd), it added fine but wont print anything, i sent test pages and they say they are printing, but the printer just sits and does nothing. i dont have the knowledge or time to try and get this to work maybe someone else will but in the meantime its back to turboprint, the scanner driver/app is still a good find for tonight. goodluck, and if you can't get it to work just use turboprint and change the quality setting to medium so you dont get their logo.

your problem might have something to do with 64bit? what i did was 
sudo alien cnj* --to-deb --scripts
which gave no errors and did both the common and mp510


UPDATE: you need to install libxml1, then try cngpij -P MP510 ~/Desktop/test.txt which should bring up an ugly printer dialog, again printing just fails but getting further...
tried looking at cngpijmonmp510 which i assume is a monitoring tool but it just says unknown printer

---

### Post by zero-9376 on 2007-05-10
another suggestion might be to get the source package src.rpm and see what you can do with that, you should be able to extract the contents using archive manager and read the instructions that they will hopefully have provided...good luck
if all else fails, or you can't be bothered stuffing around i suggest [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) which apparently supports 64 bit. It works great for me with documents and diagrams etc. i think its really only photo printing that might be a problem, remember to change quality to medium so you dont get the logo..it doesnt tell you until you put the quality back to high. also you could pay for the software and then have full quality printing.

---

### Post by teetee on 2007-05-10
> then try cngpij -P MP510 ~/Desktop/test.txt 

What is that cngpij?

I can't make rpm to deb... I got the error message (log) I earlier sent.

And by the way, I want to print photos. That is the whole idea.

---

### Post by zero-9376 on 2007-05-11
cngpij is a command line printing program but you need to install the software to get that far. as i said you may have more luck using the source package and compilining the software yourself because of the 64bit thing. unfortunately i can't help you with this.

i downloaded and converted these on my machine, dont know if it will work but you can try, right click save link as 

[http://homes.jcu.edu.au/~jc135464/cnijfilter-mp600_2.70-2_i386.deb]("http://homes.jcu.edu.au/~jc135464/cnijfilter-mp600_2.70-2_i386.deb")

[http://homes.jcu.edu.au/~jc135464/cnijfilter-common_2.70-2_i386.deb]("http://homes.jcu.edu.au/~jc135464/cnijfilter-common_2.70-2_i386.deb")

---

### Post by teetee on 2007-05-11
I cannot install them, because them are on i386 architecture, not amd64...

But thanks anyway. So, does anyone know how to install i386 on amd64? Is it possible and if is, then is it easy?

I cannot use alien on src-package either. It says again that amd64 architecture isn't supported. And there is some problems with libcups also.

> tt@kone:~/asennus/mp600$ sudo alien -c cnijfilter-common-2.70-1.src.rpm
mkdir: hakemiston "cnijfilter-common-2.70" luominen ei onnistu: File exists
mkdir: hakemiston "cnijfilter-common-2.70/debian" luominen ei onnistu: File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cnijfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Virhe 1
find: cnijfilter-common-2.70: No such file or directory


Well today I will take this printer to it's owner. I borrow it again some other time and try to fix it (not printer, but problems with installing one).

---

### Post by teetee on 2007-05-11
I am not sure have Ubuntu recognized my printer. It is USB printer (like most are these days?). How could I check does Ubuntu know that there is printer plugged?

Edit: Well not MY printer, but printer I am using.

---

### Post by teetee on 2007-05-11
> lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 001 Device 001: ID 0000:0000  


So I guess Ubuntu doesn't recognize my printer?

---

### Post by zero-9376 on 2007-05-11
sorry should have been more clear i didnt mean convert the source package, rather you should uncompress it and use the source to compile the software for yourself on your machine, perhaps try and find a guide on installing from source for ubuntu im sure there are plenty of them out there. software sources usually come in .tar.gz format but the uncompressed src.rpm should? be the same as uncompressed tar.gz, or maybe contain the tar.gz. anyway good luck, maybe someone with a bit more experience can help you out with this, or you could even try contacting canon to see if 64bit is supported, check if people are using these drivers sucessfully on 64bit fedora or suse (OSes that rpms are made for)

---

### Post by zero-9376 on 2007-05-16
lsusb gives me:
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04a9:1717 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 004 Device 003: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

I think you should at least be getting a bus ID for the printer, I sometimes have problems with usb devices and it takes a restart to fix them.

---

