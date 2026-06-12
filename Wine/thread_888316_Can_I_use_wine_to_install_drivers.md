---
title: "Can I use wine to install drivers?"
date: 2008-08-13
forum: Wine
---

### Post by mahela007 on 2008-08-13
I have a canon ip6210d printer. Unfortunately there is no linux driver for this printer. Is there any way that I can istall the windows driver by using wine?

---

### Post by maxmanapple on 2008-08-13
use the software cd provided with the printer (or use a web driver from the printer's site) and see how it goes. If unsucessfull please post!

Hope i helped...

---

### Post by prshah on 2008-08-13
> **mahela007 said:**
> I have a canon ip6210d printer. Unfortunately there is no linux driver for this printer. Is there any way that I can istall the windows driver by using wine?

There's no need for this convoluted approach.

You can get the PPD file for the driver from the Windows driver files. Then, on your linux system, open a browser, and type the below address in the address bar.```
http://127.0.0.1:631
``` this will open up CUPS (Common Unix Printing System) administration page. From this page, add a printer, and choose to use a custom PPD file when prompted to select from a list of drivers. Point this to the PPD file you have recovered from the windows drivers. Once the install is completed, you can use the printer normally, including any printer specific settings!

Post back if you run into any difficulties in this.

---

### Post by mahela007 on 2008-08-13
thats the problem. This printer doesnt have a linux driver. How do i find the ppd driver?

---

### Post by maxmanapple on 2008-08-13
> **mahela007 said:**
> thats the problem. This printer doesnt have a linux driver. How do i find the ppd driver?

My research says that is available a PPD driver that is bundled on the Mac OS X Tiger instalation. So, what would I do in your situation is get acess to a Mac and copy the PPD driver into a removable driver (say, a pen drive). Then install it on Linux using the normal ways. You can give it a try, that's how i got my printer to work (Lexmark Z12 ColorFine).

Hope it helped...

---

### Post by mahela007 on 2008-08-13
thanks for your suggestion but I wont be gaining access to a mac any time soon. I sri lanka (thats my country) macs arent very popular yet

---

### Post by YokoZar on 2008-08-13
Regarding your original question:  support for printer drivers isn't functional yet in Wine.  It's possible to do (unlike support for low-level drivers like video cards), but it's not done yet.


Would make a great Google Summer of Code project: [http://wiki.winehq.org/Printing](http://wiki.winehq.org/Printing)

---

### Post by prshah on 2008-08-13
> **mahela007 said:**
> thats the problem. This printer doesnt have a linux driver. How do i find the ppd driver?

You don't need a "linux" driver. The PPD _file_ (_not_ driver) is included in the Windows drivers. Check all _files_ supplied with the Windows drivers. You don't need a mac.

---

### Post by mahela007 on 2008-08-13
thanks. sorry of my late replies but I am having a few computer problems (nothing serious:confused:) thanks for your help. I tried locating the PPD file with the tracker search tool in linux but i didnt find anything. I dont know how else to look .(i can so it manuall but there are tons of files heheheh). thanks everyone!

---

### Post by prshah on 2008-08-14
> **mahela007 said:**
>  I tried locating the PPD file with the tracker search tool in linux but i didnt find anything.

Use the following commands to search for files:```
find ~ -iname ppd
ls -lR ~ | grep -i ppd
```

Any one command is OK.

---

### Post by mahela007 on 2008-08-14
thanks. I will post back if I find it

---

### Post by tastefulasever on 2009-09-09
I found a .ppd file for the iP6210D.  You can download the MacOS X driver from the Canon website.  There is more than one driver, I think the right one is the one called:

ip6210dosxcp102600ea8-2.dmg

This is a disk image file.  I converted it to a .img file using a win32 tool in wine called dmg2img-1.6.1-win32

run the tool like this: 
```
wine dmg2img filename.dmg newname.img
```

The new .img file will be created in the working directory. Now mount the new .img file like so:

```
sudo mount -t hfsplus -o loop newname.img  mountpoint
```

Now browse the mountpoint directory for CanonIJiP6210D.ppd.gz

There is also an Archive.pax file

I cannot get the printer to work with this .ppd file.  

It says it's looking for a filter, presumably from the Archive.pax file, however, I cannot find the "filters" directory in the Archive.pax file, even though it seems it should be there.  To unpack the .pax file, install the "pax" utility.

```
sudo apt-get install pax
```

```
pax -rvf Archive.pax
```

Maybe someone else can make use of this information.

---

### Post by tastefulasever on 2009-09-09
Also, I've heard that the iP6210D worked out of the box on Intrepid.  I am running Jaunty now, and the printer did not work out of the box.  

Can anyone else tell me which driver Intrepid used for the Ccanon iP6210D?

---

### Post by mahela007 on 2009-09-09
thanks for showing me that resource... alas... my printer broke and I ended up buying a new one which works with ubuntu.. Thanks again. Hope you find what you are looking for..

---

