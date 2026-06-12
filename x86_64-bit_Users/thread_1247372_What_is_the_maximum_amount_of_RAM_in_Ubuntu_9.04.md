---
title: "What is the maximum amount of RAM in Ubuntu 9.04?"
date: 2009-08-22
forum: x86 64-bit Users
---

### Post by YMS_1975 on 2009-08-22
I recently purchased a new computer (thanks to the power surges due to the thunderstorms we've been having here in Southern Ontario coupled with the fact that I didn't have a surge protector [I know, I know....that's MY fault]). It's a [Gateway Intel Core i7 920 2.66GHz Computer (FX6801-09H)]("http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10124869&catid=27564").

I just wanted to find out what's the maximum amout of RAM Ubuntu 9.04 (64 bit) will recognize.

Anybody?

---

### Post by Jimmyfj on 2009-08-22
I'm not all that sure. But I've read somewhere that if you run 64 bit with EXT3 file system the upper limit **for an open file is** 4GB. In EXT4 the max. file-size is 16 TB (for 4k block file system). From that I guess that the max amount of physical RAM must be the equivalent to those numbers. Feel free to correct me if I'm wrong. :P

---

### Post by lensman3 on 2009-08-23
If you do a "more /proc/cpu*" from a command line, the cpu-info (at least on mine) shows you how much memory the it can access.  Mine is a 64 bit but the best it can do is:

address sizes	: 36 bits physical, 48 bits virtual

so 2 raised to 48 is the largest program+data that can be accesses, except your PC motherboard can't have more than 2^36 on it.

---

### Post by movieman on 2009-08-23
> **Jimmyfj said:**
> I'm not all that sure. But If you run 64 bit with EXT3 file system the upper limit for an open file is 4GB.

Not true: you can have files much larger than 4GB on ext3.

Maximum RAM should be at least 64GB, I didn't see a definitive number on the Ubuntu site.

---

### Post by Jimmyfj on 2009-08-23
Okay - It's late at your place. LOOK at his question, dude. He aksed for the max amount of RAM in 9.04 - I know you can have files of up to 2TB on EXT3 and up till max 1EXB, (1 Exa-byte) on EXT4. That ISN'T the same as the amount of RAM Ubuntu 9.04 is able to handle. I believe that is up to the kernel how much physical RAM can bee adressed. The upper file system limit in EXT3 being 2TB, and 1EXB in EXT4. Thus the max file size=Max file system size minus the bytes used for the system itself. Where's the math in that? (1X=1X-U).

Edit:

The amount of physical installed RAM is not just limited by the kernel. Your mobo is the bottleneck in that matter. If your OS is capable of handling say 64GB of RAM that factor is worth nothing if your motherboard is capable of supporting only 8GB physically. That combined with the upper limit of the OS' "Max size of one open file=" You do not have just one factor in the matter.

---

### Post by 3rdalbum on 2009-08-23
> **YMS_1975 said:**
> I recently purchased a new computer (thanks to the power surges due to the thunderstorms we've been having here in Southern Ontario coupled with the fact that I didn't have a surge protector [I know, I know....that's MY fault]). It's a [Gateway Intel Core i7 920 2.66GHz Computer (FX6801-09H)]("http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10124869&catid=27564").

I just wanted to find out what's the maximum amout of RAM Ubuntu 9.04 (64 bit) will recognize.

Assuming that you've told us about the computer for a reason :-)  Ubuntu 9.04 supports more memory than you can fit into your computer. Much more.

---

### Post by P.KO on 2009-08-23
Hi,

The amount of RAM supported by your system depends on several thing.

First of all the processor , OS , MOBO , filesystem support and finally physical RAM.

My processor e.g supports 40 bit physical 2^40 (1,073.741824 GB) and virtuel 2^48 (274,877.906944 GB).
OS supports 2^64.
MOBO typical less than 64 GB.
A good overview of ext3 file system [http://www.howtoadvice.com/Ext3Max/](http://www.howtoadvice.com/Ext3Max/) (There is no 4 GB limit!)
And finally the HW-producer needs to build RAM-circuits supporting these limits.

---

### Post by Jimmyfj on 2009-08-23
I feel that I need to correct some things on this issue. I *never* claimed anywhere that the EXT3 file system has a limit of 4GB file(s). If you read my posting above, my first post, I say MUST be equivalent to. Not that the limit IS. (read my second post). In my second post I say that the upper limit depends on many factors, including, but not limited to your motherboard. I even mentioned that your motherboard is the bottleneck in this matter. Then again - Why install more than 8 GB of RAM? I doubt there's any "every-day-software" out there that is able to take advantage of anything above 4 GB, if they even get that high, unless you have some powerful, specialized software for handling 3D animation/movies etc.etc.

---

### Post by P.KO on 2009-08-23
Hi,

Well if you write something like this :guitar:

> But I've read somewhere that if you run 64 bit with EXT3 file system the upper limit for an open file is 4GB. In EXT4 the max. file-size is 16 TB (for 4k block file system).

then it is misinterpreted by many as you mixe things.

Please correct your sentence not to mislead others.

---

### Post by interval1066 on 2009-08-23
In my experience its not really useful to ask how much RAM an os will support, they usually support much more than the hardware will. A better question would be "How much RAM will my mobo support?"

---

### Post by YMS_1975 on 2009-08-23
> **interval1066 said:**
> In my experience its not really useful to ask how much RAM an os will support, they usually support much more than the hardware will. A better question would be "How much RAM will my mobo support?"


As per my initial post, you'll notice a link to the computer I purchased. The computer comes with 12 GB of physical RAM installed.

So this is definitely not a matter of hardware, since my motherboard, CPU & the RAM itself were designed to run together.

---

### Post by YMS_1975 on 2009-08-23
> **lensman3 said:**
> If you do a "more /proc/cpu*" from a command line, the cpu-info (at least on mine) shows you how much memory the it can access.  Mine is a 64 bit but the best it can do is:

address sizes	: 36 bits physical, 48 bits virtual

so 2 raised to 48 is the largest program+data that can be accesses, except your PC motherboard can't have more than 2^36 on it.

I haven't installed Ubuntu on it yet. I don't want to install it until I know how much RAM the OS will support.

See the tower has the Windows OS installed on another partition. No physical CD/DVD's were included in the package. So if I need to reinstall the Windows OS, I will run a Windows application that will access the separate partition and it'll reinstall the Windows OS.

I'd like to know how much Ubuntu 9.04 can handle (maximum) before I mess around with the OS that's on there right now (especially since I have no CD/DVD's). I'm fairly sure, Ubuntu will be able to handle it but I just want to make sure before I mess with anything.

---

### Post by YMS_1975 on 2009-08-23
> **3rdalbum said:**
> Assuming that you've told us about the computer for a reason :-)  Ubuntu 9.04 supports more memory than you can fit into your computer. Much more.


Yes, I included the link for a reason indeed. The physical RAM that comes pre-installed is 12 GB. Just want to make sure that if I install the 64-bit of Ubuntu, it'll recognize the full 12 GB of RAM. 

That's all.  :P

---

### Post by P.KO on 2009-08-23
Hi,

It will support your 12 GB!

The OS supports up to 2^64 (18,014,398,509.481984 GB) compared to a 32 bit OS which supports 4,194304 GB.

---

### Post by YMS_1975 on 2009-08-23
Can anybody else second that?  :)

Sorry if I seem nervous. Not having those CD/DVD's is a bit worrisome (for me anyways).

I wonder why Ubuntu doesn't have this in their documentation. I visited the official Ubuntu site, but couldn't find it anywhere.
Oh well...

---

### Post by mjwalfredo on 2009-08-23
Yes, a 64 bit kernel, which is what Ubuntu 9.04 64 bit has, will support way more than the  12GB of memory on your new machine.

---

### Post by P.KO on 2009-08-23
Hi,

If you are so nervous for your MS system, just install a dualboot and test.

During installation Ubuntu can resize the NTFS partitions. Just have them defragmented before trying to install Ubuntu.

Or simply try the Live CD without installing the system. You are offered this option during launch.

---

### Post by mjwalfredo on 2009-08-23
> **P.KO said:**
> Hi,
Or simply try the Live CD without installing the system. You are offered this option during launch.

Good point.  Just use the live CD to see for yourself.  That way there are no worries about the state of your existing filesystem.

---

### Post by YMS_1975 on 2009-08-23
Thanks for all the help people! I appreciate it.

As for the Live CD option, I totally forgot that this was an option. One of the added benefits of going Ubuntu.  :)

---

### Post by YMS_1975 on 2009-08-26
Hmmm.....just a side note/observation. Ubuntu Live CD seems to recognize my 12 GIGS of Ram, but it lists it as 11.6, and Windows lists it as 12 GB evenly.

Any idea(s) as for why the discrepancy?  :)

---

### Post by tuxxy on 2009-08-26
You have to consider that some of the memory will already be assigned to peripherals, video, sound card etc

That value off 11.6 in Ubuntu will be free available memory and your Windows OS may state it has 12GB but that doesn't mean it has that much memory free.

---

### Post by Slim Odds on 2009-08-26
> **YMS_1975 said:**
> Hmmm.....just a side note/observation. Ubuntu Live CD seems to recognize my 12 GIGS of Ram, but it lists it as 11.6, and Windows lists it as 12 GB evenly.

Any idea(s) as for why the discrepancy?  :)

Could be they just round it.

PI is 3

---

### Post by YMS_1975 on 2009-08-27
> **tuxxy said:**
> You have to consider that some of the memory will already be assigned to peripherals, video, sound card etc

That value off 11.6 in Ubuntu will be free available memory and your Windows OS may state it has 12GB but that doesn't mean it has that much memory free.

That's not it. At least I don't think it is. Under the system settings, it says : 235 MiB (2%) **of** 11.6 GIB. So...it's taking into account what's already being used of the total available ram. 

In other words, my interpretation of that statement is 11.6 GB is being recognized as the _total amount of ram_, and after the 235 MB used by the system, that would bring it to approximately 11.2 GB remaining.

The flip side to this (proving my theory incorrect) would be, 11.6 GB is a sub-total _not including the 235 MB used by the system_. In which case, we'd add up the 235 MB to the 11.6 GB to total an approximate of 11.8 GB (bringing it much closer to the actual 12 GB of ram). But the problem I have with this interpretation is the statement Ubuntu makes in the System settings where it said "235 MiB (2%) **of** 11.6 GIB" That to me says it's only seeing 11.6 GiB.

I'm sorry if I'm making this into an issue. I'm just trying to better understand how Ubuntu see's the memory and how it addresses the memory (I.E: limitations on the OS, hardware, etc.) On a side note, I do find it interesting that Ubuntu abbreviates gigabyte as "GiB". I'm used to seeing it as either "GB" or "GIG". :)

I think [COLOR="Red"]Slim Odds[/COLOR] is onto something with the rounding of the numbers. But what a weird way to round it ; from 12 to 11.6??? :confused:

---

### Post by souse on 2009-08-27
I installed ubuntu 9.04 on a machine running i7-920, Gigabyte mobo and 6GB Triple-channel DDR3 RAM. It detected only 5.8GB. If 11.6GB is detected for 12GB, it seems proportionate deduction of 66.7MB per 1GB of RAM. As i7-920 & Gigabyte can support max of 24GB, I think ubuntu can detect maximum of 23.2GB.

---

### Post by P.KO on 2009-08-27
Hi,

Have a look at this article at [wikipedia]("http://en.wikipedia.org/wiki/Gibibit") to find out the difference between GB and GiB.

---

### Post by dk06 on 2009-08-27
For 32bit Arch w/PAE, 64GB RAM (I think the true performance w/PAE is questionable but there it is for 32bit) [http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/) Non-PAE = 4 GB (About 3.5 actually usable) ____________________________________________________ 

>  A 64-bit computer will be able to address up to 16.8 million TB (16 exabytes) although constraints are in place that limit this to around 1TB.  [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit) 

============================================= 

So... 

[LIST]
[*]32bit = about 4GB (64GB w/PAE)
[*]64bit = around 1TB
[/LIST]

---

### Post by Slim Odds on 2009-08-27
> **YMS_1975 said:**
> I think [COLOR=Red]Slim Odds[/COLOR] is onto something with the rounding of the numbers. But what a weird way to round it ; from 12 to 11.6??? :confused:

I was talking about Windows rounding 11.6 to 12

---

### Post by YMS_1975 on 2009-08-27
> **Slim Odds said:**
> I was talking about Windows rounding 11.6 to 12


Isn't that the same thing I said (although I said it vice versa)?
I would think rounding up or down, is still in line with the theory.

Unless I'm misunderstanding what you mean.

---

### Post by YMS_1975 on 2009-08-27
> **P.KO said:**
> Hi,

Have a look at this article at [wikipedia]("http://en.wikipedia.org/wiki/Gibibit") to find out the difference between GB and GiB.

I read this; thanks for the link. It was interesting, but a Giga-**bit** confusing. <----- My bad joke of the day.  :)

---

### Post by YMS_1975 on 2009-08-27
> **dk06 said:**
> For 32bit Arch w/PAE, 64GB RAM (I think the true performance w/PAE is questionable but there it is for 32bit) [http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/) Non-PAE = 4 GB (About 3.5 actually usable) ____________________________________________________ 

 [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit) 

============================================= 

So... 

[LIST]
[*]32bit = about 4GB (64GB w/PAE)
[*]64bit = around 1TB
[/LIST]

Thanks for the link. I just finished reading the page. It's very clear, but it still doesn't answer why it shows up as 11.6 GiB.
But I did understand Ubuntu's capabilities of addressing RAM a lot more better (thanks to the links you guys have been providing me with).

Oh well....:guitar:

---

### Post by Martje_001 on 2009-08-27
> **YMS_1975 said:**
> That's not it. At least I don't think it is. Under the system settings, it says : 235 MiB (2%) **of** 11.6 GIB. So...it's taking into account what's already being used of the total available ram. 
Windows calculates its numbers differently than Ubuntu.

Ubuntu says: One kilobyte is 1024 bytes (KiB).
Windows says: One kilobyte is 1000 bytes (KB).

So if your computer can store 12,000,000,000 (12 GB) bytes in memory, Windows would say it can store 12 GB, Ubuntu would say 11,2 GB.

So, after writing all this, I came to the conclusion that this is not the problem :P.

I think Windows just rounds it up. Like 11,6 GB --> 12 GB, 11,4 GB --> 11 GB.

---

### Post by YMS_1975 on 2009-08-27
> **Martje_001 said:**
> Windows calculates its numbers differently than Ubuntu.

Ubuntu says: One kilobyte is 1024 bytes (KiB).
Windows says: One kilobyte is 1000 bytes (KB).

So if your computer can store 12,000,000,000 (12 GB) bytes in memory, Windows would say it can store 12 GB, Ubuntu would say 11,2 GB.

So, after writing all this, I came to the conclusion that this is not the problem :P.

I think Windows just rounds it up. Like 11,6 GB --> 12 GB, 11,4 GB --> 11 GB.

That seems to be the general consensus; that Ubuntu and Windows treats or sees RAM slightly differently.

Oh well, I'm satisfied with all the answers I've received and will be installing it on my system. Initially, I was a bit nervous in doing so but as long as it sees all of my RAM (and I'm convinced now that it does) I'm good to go!  :P

---

### Post by terabyte1 on 2009-08-27
Dear me! I guess the question than needs to be answered is, if your computer (assuming it is 64-bit and you are journaling at Ext4) can handle more than 8 gigabyte in Ram. I think the answer is yes it can handle more ram but most computers today aren't supplied with sufficient Ram Strips to support a terabyte let alone any other size factor of ram because of manufacturing difficulties at the present time.


If that seems wrong correct me :P

Whether people can *afford* to install a terabyte or more of ram is more the point AND finding a ram-strip (of up to *1 terabyte*) that will fit into one of the usual 4 slots usually occupied by ram that may (or may not) be available at the present time.

Cheers!:lolflag::guitar:

Personally I'm just happy with the status quo and my 8 gig of ram!

---

### Post by mystmaiden on 2009-08-31
Maybe I misunderstood, but if I spent that much on a computer I'd have no trouble asking the retailer to supply me with the OS cds or dvds.. even after the fact and they should be happy to do that for a good customer...

---

### Post by chris1950 on 2009-09-01
> **Jimmyfj said:**
> I feel that I need to correct some things on this issue. I *never* claimed anywhere that the EXT3 file system has a limit of 4GB file(s). If you read my posting above, my first post, I say MUST be equivalent to. Not that the limit IS. (read my second post). In my second post I say that the upper limit depends on many factors, including, but not limited to your motherboard. I even mentioned that your motherboard is the bottleneck in this matter. Then again - Why install more than 8 GB of RAM? I doubt there's any "every-day-software" out there that is able to take advantage of anything above 4 GB, if they even get that high, unless you have some powerful, specialized software for handling 3D animation/movies etc.etc.

It may not be that any software will use that much. But if you use virtual machines each machine open takes away from the amount of RAM assigned to it thus if you want to run multiple machines at the same time then a large amount of RAM is needed.

---

### Post by Penguinista on 2009-09-04
> **YMS_1975 said:**
> Thanks for the link. I just finished reading the page. It's very clear, but it still doesn't answer why it shows up as 11.6 GiB.
But I did understand Ubuntu's capabilities of addressing RAM a lot more better (thanks to the links you guys have been providing me with).

Oh well....:guitar:

It shows up at 11.6 because Linux uses a different unit to detail your memory size than Windows does. As an analog, think of the difference between imperial miles (the American / British system) and kilometers (Metric). It's 1 mile, or 2.2 (approximately) kilometers. Both describe the same physical distance, just in different units.

---

