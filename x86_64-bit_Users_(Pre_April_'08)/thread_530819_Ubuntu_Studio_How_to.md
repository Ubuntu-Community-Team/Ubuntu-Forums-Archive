---
title: "Ubuntu Studio How to??"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by uncleclinto on 2007-08-20
Hey Peeps,

I finally got a new computer that's fast enough to run Ubuntu Studio and a Win2k Virtual box for my Macromedia Studio 8!  I was so excited until I started looking for the 64 bit install dvd that doesn't exist. So, my search began.  How do I install Ubuntu Studio on 64 bit.  

I searched the forums and found the following posts:
[http://ubuntuforums.org/showthread.php?t=445831](http://ubuntuforums.org/showthread.php?t=445831)
[http://ubuntuforums.org/showthread.php?t=459352](http://ubuntuforums.org/showthread.php?t=459352)

These are leads... sort of, but they're not really answers. What I need is a step by step "how to" on this process.  Once I install 64 bit Feisty, what repositories must I add to my list?  What do I type to add the packages?  What if I want the theme (I really want the theme)?  

Can anyone help a quasi-noob to Ubuntu and a total noob to 64 bit with this process?  What I really want  is:
[LIST]
[*]The Ubuntu Studio Theme
[*]The Ubuntu Studio Graphics Package
[*]To get rid of Vista ASAP
[/LIST] 

Feeling Lost in York,
Clinto

---

### Post by stmiller on 2007-08-20
Pretty much you just install all of the audio or graphics apps that you need. For audio or video work, install the low-latency kernel. (It's in apt-get.)

Ubuntu Studio has repos for updated software, but it is only 32bit. 

Also check out this project:

[http://www.64studio.com/](http://www.64studio.com/)

---

### Post by John.Michael.Kane on 2007-08-21
As stmiller said U-studio is 32bit only or you can use [http://www.64studio.com/](http://www.64studio.com/) ,however. if you still want to run it.

Heres a step by step for installing u-studio.

Run these two commands inside the terminal:
```
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
```

```
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

Run this to install UbuntuStudio.
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video ubuntustudio-artwork ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-session-splashes ubuntustudio-sounds ubuntustudio-screensaver ubuntustudio-theme ubuntustudio-wallpapers usplash-theme-ubuntustudio wired 
```

If you have a nvidia card you will also need this
```
sudo aptitude install linux-restricted-modules-2.6.20-15-lowlatency
```

The above method should also work from a base install eg:command line/server install.

---

### Post by uncleclinto on 2007-08-21
Awesome, thanks.  How do I find out whether I have a nvidia card?

---

### Post by uncleclinto on 2007-08-21
Never mind...  I have a Intel Graphics Media Accelerator 950/945GM.  Do I still need the low latency thing??

---

### Post by spintel on 2007-08-22
I updated Feisty to Studio and my wireless doesn't work anymore.

I tried using NDSIWrapper but it didn't display my wireless card as being installed.  When I tried to install it again it said "card already installed".

My wireless was working fine in Feisty but when I switched to Studio it's only recognizing the hardwire card.

---

### Post by John.Michael.Kane on 2007-08-22
> **uncleclinto said:**
> Never mind...  I have a Intel Graphics Media Accelerator 950/945GM.  Do I still need the low latency thing??

No you don't have to install linux-restricted-modules-2.6.20-15-lowlatency.

---

### Post by spintel on 2007-08-22
> **spintel said:**
> I updated Feisty to Studio and my wireless doesn't work anymore.

I tried using NDSIWrapper but it didn't display my wireless card as being installed.  When I tried to install it again it said "card already installed".

My wireless was working fine in Feisty but when I switched to Studio it's only recognizing the hardwire card.

Ok, when Grub loads I have a option of low latency and my regular ubuntu option is still there; the wireless card will not work in the low latency mode but will in the regular mode.

---

### Post by MetalMusicAddict on 2007-08-22
> **spintel said:**
> Ok, when Grub loads I have a option of low latency and my regular ubuntu option is still there; the wireless card will not work in the low latency mode but will in the regular mode.

Install whatever you have for -lowlatency that you have for -generic kernel-wise.

---

### Post by spintel on 2007-08-22
Also, how would I go about reverting back to regular Ubuntu?  Do I have to go through the package manager and uninstall each program?

---

### Post by John.Michael.Kane on 2007-08-22
> **spintel said:**
> Ok, when Grub loads I have a option of low latency and my regular ubuntu option is still there; the wireless card will not work in the low latency mode but will in the regular mode.

What kind of card is it eg: maker/model. 

what errors msg's are given if any. 

What is the output of the below command.
```
lspci
```

Note: Looking over the kernel numbers their low latency kernel seems behind ubuntu's standard kernel. Thus may not have the support needed for your card,however. that is only a guess.

You can see if theres a way to install u-studio while using the standard kernel.

---

### Post by John.Michael.Kane on 2007-08-22
> **MetalMusicAddict said:**
> Install whatever you have for -lowlatency that you have for -generic kernel-wise.

MetalMusicAddict just the guy I was hoping to chime in on this. The u-studio guys did not make any adjustments to the kernel that would remove support for certain cards right?

All that was done was to patch the kernel for lowlatency. I ask as seemed odd that the member wifi stop working after moving to your kernel.

---

### Post by MetalMusicAddict on 2007-08-23
> **SD-Plissken said:**
> MetalMusicAddict just the guy I was hoping to chime in on this. The u-studio guys did not make any adjustments to the kernel that would remove support for certain cards right?
No. Nothing is removed. The -lowlatencey kernel is exactly the sam as -generic other than [THIS]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022755.html"). So things  have only been added.
> All that was done was to patch the kernel for lowlatency. I ask as seemed odd that the member wifi stop working after moving to your kernel.
It shouldn't. Also, we had very little to do with -lowlatency. We have had a more active role in the upcoming -rt kernel though. :)

Where most people mess up with using the other kernels is that they forget to grab the restricted modules. 9/10 its just user error.

Best package to grab is **linux-lowlatency** and for the new -rt **linux-rt**. That will grab everything needed for the desired kernel.

---

