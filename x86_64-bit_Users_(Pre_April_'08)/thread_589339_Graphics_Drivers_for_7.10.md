---
title: "Graphics Drivers for 7.10"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by dexter11 on 2007-10-24
I am a noob at Ubuntu - and am installed 7.10 64 - I am trying to get the sweet graphics running and am struggling - evern though it picked up some unsupported drivers. 


Even after this I am still running in low res as it failes to detet my card - Can anyone help 

I have a Saphhire HD 2600 XT - any help would be appreciated... 


Thanks

---

### Post by orange2k on 2007-10-24
Try to set your monitor from the screens and resolutions menu so you can set all resolutions your monitor supports.

If you can`t get proper video card drivers, you might want to try Envy...(I`m not sure what kind of chipset your card is: ATI or NVIDIA)

---

### Post by dexter11 on 2007-10-24
When i try to change the Res all i get is 800x600 so I am screwed in turns of getting some nice sharp graphics that i am used to on other platforms! 

Chipset is ATI - sorry to be a novice but are Envy a open sorce driver company?? 

I am desprate to get Ubuntu running as my full time OS

---

### Post by orange2k on 2007-10-24
> **dexter11 said:**
> When i try to change the Res all i get is 800x600 so I am screwed in turns of getting some nice sharp graphics that i am used to on other platforms! 

Chipset is ATI - sorry to be a novice but are Envy a open sorce driver company?? 

I am desprate to get Ubuntu running as my full time OS

Envy is a utility that you can use to install the right drivers for your card: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Have you chosen your monitor type from the **screens & graphics** preferences menu?
If so, other resolutions should be available...

---

### Post by dexter11 on 2007-10-24
Ill give that a go! 

I did look for my monitor which is an Acer 19 Farreri - could not find in the list though - not 100% on the model number!



Thanks for you quick responce!

---

### Post by orange2k on 2007-10-24
> **dexter11 said:**
> Ill give that a go! 

I did look for my monitor which is an Acer 19 Farreri - could not find in the list though - not 100% on the model number!



Thanks for you quick responce!

Try some similair monitor (it doesnt have to be a 100% match)  - that should do the trick - and all the resolutions should be available then...

---

### Post by aoanla on 2007-10-24
As far as I know, the HD series cards are only supported in the newer releases of the ATI fglrx driver.
Get hold of the 8.41.7 driver from here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.41.7-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.41.7-x86.x86_64.run)

and install it with this howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Hopefully, that version of the fglrx driver will work for you, and you will be able to access higher display resolutions.

(My advice is not to use the new 8.42.3 driver, as it seems to have issues with Ubuntu, especially on 64bit systems.)

---

### Post by dexter11 on 2007-10-24
Thanks for all you help guys  - I will give it a go! 

I wonder if you can answer another question - are you guys usig the terminal for most of your day to day stuff - I am not to hot on this and was wondering if you could pioint me in the direction of some easy to follow basic's to learn!?

---

### Post by orange2k on 2007-10-24
> **dexter11 said:**
> Thanks for all you help guys  - I will give it a go! 

I wonder if you can answer another question - are you guys usig the terminal for most of your day to day stuff - I am not to hot on this and was wondering if you could pioint me in the direction of some easy to follow basic's to learn!?

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

A very nice site with a user-friendly approach...


Well, I don`t really use the CLI that much, but I don`t mind using it. The power of the command line interface is enormous. There are some very nice command line programs like for instance Streamripper (its in the repository).
Example command for streamripper is: streamripper stream_url -l 300 -a stream.mp3

The meaning: -l parameter instructs streamripper to rip x number of seconds (in this case 300), -a instructs streamripper to rip to only one file named in this case stream.mp3

There are many other options, you can see them if you type only streamripper in the console...

---

