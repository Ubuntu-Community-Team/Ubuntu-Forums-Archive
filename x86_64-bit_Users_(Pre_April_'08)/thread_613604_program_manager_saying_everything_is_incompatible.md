---
title: "program manager saying everything is incompatible"
date: 2007-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Duncan29 on 2007-11-15
ok i'm very new to linux, 
i recently downloaded and installed 64 bit ubuntu, only to find that the program manager said almost every program was incompatible with 64 bit ubuntu, along with a host of ati and wireless problems.....

i then downloaded 32 bit ubuntu and installed that to find it was the exact same, no aps would install because they were incompatible with the 32 bit ubuntu... and also the same ati and wireless problems.

i've seen plenty of help threads for dealing with ati and wireless, some specific to my laptop! so may main inquirey is how to get the program manager working properly and should i move back to 64 bit since it appears i'd have to put in a similar effort to get 32 working!!
cheers,
    Duncan
oh incase this helps, i'm using a dell inspiron 1501,
amd turion x2 1.6ghz
2gb ram
ati radeon xpress 1150

i'd assume if it is a hardare issue it comes down to the processor?

---

### Post by Jouke74 on 2007-11-15
:confused: You did download "programs" that are made for Linux right, you're not trying to install Windows drivers with "setup.exe"?
Windows programs (exe's) won't go on Linux (well... but that's another story). 

64 bit / 32 bit: For 64 bit you can use debian package files (.deb) file that are called *AMD64 or *ALL. For 32 bit programs you need to have the i386 debians. Also check out Synaptic package manager, your basic programs to install library. 

To install the ATI driver go to the menu and install the restricted driver. For now leave it there, and later try all the stuff in the forums when your linux knowledge is a bit bigger.

Wireless I can't figure out, because I don't know what chipset you have in there.

---

### Post by Duncan29 on 2007-11-15
thanks very much for the responce,
  it's ubuntu's own add remove program program, which is listing every program that is not installed as incompatible, if i select for example blender to be download, it will bring up an error box saying that it's not supported on 32 bit on the 32 bit os and not supported on AMD64 for 64bit. 
i have ran ubuntu before on a older laptop and had little to no trouble, though i had to set up wireless drivers on that as well so that will be a memory excersise!

thanks for the responce!

---

### Post by Jouke74 on 2007-11-15
Sorry I thought you were a complete newbie. It remains very strange. What happens if you apt-get the blender program in the terminal? 
And which Kernel of linux is installed on your laptop?

---

### Post by cjazz on 2007-11-15
Also, could you post your /etc/apt/sources.list file?

---

### Post by Duncan29 on 2007-11-15
ok i'm now back in ubuntu so i can paste an example of what it says.
 
AbiWord Word Processor

Canonical Ltd. provides technical support and security updates for AbiWord Word Processor
AbiWord Word Processor cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

then tick the box to install,

AbiWord Word Processor cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

it does the same with amd64 aswell.

as for my kernel: 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

the sources.list is attached to the post,

i'm not familiar enough with the console commands to try the apt-get install business,if you could post an example, from the what i think i've learned so far, i need to say apt-get install [url for blender or any ap]

thanks for all the replies!

---

### Post by Duncan29 on 2007-11-15
turns out sources.list can't be uploaded., so i've taken some screen shots of each tab.
hope it's of some use, i can post the save file, as that is text format.

---

### Post by cjazz on 2007-11-15
OK. First things first. Sources.list is a text file located in the /etc/apt folder. What I had in mind was for you to copy and post that file. But I'll try to deal with the repository screenshots from your Synaptic package manager.

It looks as though your Ubuntu main and Ubuntu multiverse repositories are not selected. In fact, the only repo you seem to have selected is universe. Is that by choice?

In Synaptic, try "ticking" or selecting the boxes beginning each line under the Ubuntu software tab. If you're going to continue to use the CD (in the space at the bottom), you might want to have the install CD in the drive when you do this. Otherwise, deselect the box for the CD drive. That's assuming you have a working Internet connection.

By the way, after you select the other repositories, you'll have to click the Synaptic reload button before you can use them. Please let me know if any of this fails to make sense.

---

