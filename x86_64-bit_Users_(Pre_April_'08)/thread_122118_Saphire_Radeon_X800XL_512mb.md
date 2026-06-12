---
title: "Saphire Radeon X800XL 512mb"
date: 2006-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nitrous570 on 2006-01-26
Hello All, 

I am new to ubuntu, so new that I have not installed the os. I am just researching various forms of linux, to see what is the best for me. I HATE windows in all areas; from speed to reliability. Endless complaints. Anyway, I am running a AMD athlon x2 4400+ dual core processor with the stated video card above in the title. Now here is my question. I had to go through a lot of work downgrading the BIOS and then installing windows, then upgrading the BIOS again. Then I needed to go the the ati site and download the driver bundle. Then I needed to go to the amd site and download a patch for the processor to communicate properly for games. That is a lot of work, and I am wondering what  I would need to do to install unbutu linux on my machine. I have a dual core 4400+ processor, which a lot of things have some complications working with. 

Some questions that I would like help with are:
1) can i get the drivers required for my video card in ubuntu linux?
2) if i do not get cedega, can I still play [www.runescape.com](www.runescape.com), if it only uses a java applet in firefox?
3) Would i have to downgrade the bios and then upgrade it?
4) Where can i get info on installing unbuntu linux with the 4400+ processor and the x800xl 512 mb saphire video card?
5) and how do I get a cd to install ubuntu linux?

I'm sorry if these seem like "newb" questions, but I am very new to linux, any distribution. I am planning to switch from windows to linux, and I just thought  some guru's here could help me.

---

### Post by slavik on 2006-01-26
1. Yes, from the ATI site ... only way I know how.

2. Java is java ... why get anything to emulate to have java working? There is no 64bit version of the firefox plugin for java though, so you will need to install the 32bit version of firefox and the 32bit version of the JRE which has the proper plugin. The instructions are here: [http://ubuntuforums.org/showthread.php?t=112418](http://ubuntuforums.org/showthread.php?t=112418)

3. You should not have to downgrade anything ...

4. Umm ... there's really no specific info you need.

5. By going to the ubuntu.com page and then going to the download section ... [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by liquidcourage1 on 2006-01-26
Be careful.  If your board is PCI-e, you may have install problems.  I'm looking into how to get mine to properly install as well.  Everything goes fine until it begins to actually boot for the first time.  Then the X server can't display.  I guess the X server is what controls the graphics.  It doesn't come preloaded with drivers to recognize a PCIe board from what I've read so far.

---

### Post by ruudiculus on 2006-01-27
Why don't you download a live-cd first? You can then see how it works and which computer components are detected properly by default. Make a list of which ones are not detected by default and surf this forum/google/anywhere searching for HowTo's for it. Note that the Ubuntu live-cd probably uses some save mode for your video card in order to support most of the video cards out there. You have to look [www.ati.com](www.ati.com) to see whether the ati-driver (which is easy to install by the way) also includes your card. My Radeon Xpress 200M for example isn't.

Good luck!

---

### Post by Nitrous570 on 2006-01-29
[QUOTE=liquidcourage1]Be careful.  If your board is PCI-e, you may have install problems.  I'm looking into how to get mine to properly install as well.  Everything goes fine until it begins to actually boot for the first time.  Then the X server can't display.  I guess the X server is what controls the graphics.  It doesn't come preloaded with drivers to recognize a PCIe board from what I've read so far.[/QUOTE]


Ne one know how to get it to recognize pci-e??

---

### Post by ruudiculus on 2006-01-29
I've recently installed my card using the ATI driver. This is what the installer says:

```
==============================================================================
 ATI - FireGL - WORKSTATION GRAPHICS ACCELERATOR
==============================================================================

This program will create the ATI "xorg.conf" file
- based on your selections - for the following video cards...

         - ATI FireGL V3100 / V3200 / V5000 / V5100 / V7100
         - ATI FireGL X1 / X2 / X3 / Z1 / T2
         - ATI FireGL 8700 / 8800
         - ATI Mobility FireGL T2 / 9100 / V5000
         - ATI Mobility Radeon 9000 / 9200 / 9600 /9800
         - ATI Mobility Radeon X700
         - ATI Radeon 8500 / 9000 / 9100 / 9200
         - ATI Radeon 9500 / 9550 / 9600 / 9700 / 9800
         - ATI Radeon X300 / X600 / X700 / X800 / X850
         - ATI IGP Radeon 9100 / 9200/n  - ATI IGP Mobility Radeon 9000 / 9100/n

```

As said I've got a Radeon Xpress 200M isn't supported according to this list, but I think the core of the driver can "drive" all new ATI cards as well (maybe not with FULL support). After the installation there's a message saying that the installer couldn't find the videocard, so there's a MESA driver used instead of the ATI driver. But when you know the address (Bus-ID) of your PCI (PCI-e) card I ***_THINK!!!_*** you can manualy edit the /etc/X11/xorg.conf file and set the proper Bus-ID in the **Section "Device"** you could give it a try. If it doesn't work comment the line again and you should have your MESA driver back after restart. If it doesn't work I think the only thing you could do is wait for a while until ATI comes with a new driver...

Good luck!

---

### Post by Ribs on 2006-01-29
[QUOTE=slavik]2. Java is java ... why get anything to emulate to have java working? There is no 64bit version of the firefox plugin for java though, so you will need to install the 32bit version of firefox and the 32bit version of the JRE which has the proper plugin. The instructions are here: [http://ubuntuforums.org/showthread.php?t=112418](http://ubuntuforums.org/showthread.php?t=112418)[/QUOTE]

This is not true. Just install j2re1.4-mozilla-plugin from universe -- works just fine.

---

