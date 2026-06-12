---
title: "Hauppauge WinTV HVR-1250"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by daverab on 2008-11-07
I'm trying to get a new PCI-E HVR-1250 working under Ubuntu.

I have found quite a few guides out there for getting it to work. I grabbed the newer v4l drivers and ran a modprobe line for the kernel module to be loaded.

I can find a /dev/dvb/adapter0 folder which I assume is pointing to the digital 'side' of the card. What program can I use to watch the digital channels? I've tried xawtv, me-tv and mythtv with out much luck. Mythtv and xawtv refuse to see it, and I have no clue what profile to use for channels in the setup for me-tv.

I'm using 8.10 64 bit edition, and I'm located in Central Florida east of Orlando using cable. My tv with an atsc tuner and I can get a few digital channels like NBC, CBS, etc on the x-x format of channels (NBC is 2-1).

From what I've read the analog tuner isn't going to be usable as is.

Any help would be appreciated.

---

### Post by cariboo on 2008-11-07
Is the driver module loaded when you boot up? Could you post the output of:

```
sudo lshw -C multimedia
```

So we can see whether the correct modules are being loaded.

Jim

---

### Post by daverab on 2008-11-08
*-multimedia            
       description: Multimedia video controller
       product: CX23885 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0 module=cx23885

That's it for the tv card. I know it's the cx23885 chipset from other resources. Am I missing stuff?

---

### Post by daverab on 2008-11-11
I hate to do this, but "bump".

I realized I forgot to tag it, so this may get lost regardless.

---

### Post by jakeman66 on 2009-01-09
I have the same card.  You ever get yours working?

---

### Post by xebian on 2009-01-09
> **daverab said:**
> I hate to do this, but "bump".

I realized I forgot to tag it, so this may get lost regardless.

Use kaffeine. I have a Kworld PlusTV HD120 which uses the CX2388, and Kaffeine works very well.

---

### Post by jakeman66 on 2009-01-09
> **xebian said:**
> Use kaffeine. I have a Kworld PlusTV HD120 which uses the CX2388, and Kaffeine works very well.

Tried it and doesn't work.  system see's the card, but none of the tv viewers do..  I've tried all the big ones so far.

---

### Post by xebian on 2009-01-09
> **jakeman66 said:**
> Tried it and doesn't work.  system see's the card, but none of the tv viewers do..  I've tried all the big ones so far.

sorry but I can't help you much.  I'm assuming you have set it up properly to load the drivers/firmware in sequence?

Even without the firmware/drivers, my system can see the card. 

I have to extract the proper firmware and put in lib/firmware.  then set up blacklist some modules to control the loading.  These I got from LinuxTV.org.  Maybe try checking your card from there.

---

### Post by snowman63 on 2009-05-07
Anyone get this working. I have the same card and I can't get anything working. I've followed every setup and suggestion I've found in this forum and nothing works. Kaffeine does not scan any channels . Me-tv says scanning is only available for dvb-c or dvb-t. Mythtv doesn't find the channels either. Can't even get a scan going correctly. 

I'm on 9.04 Jaunty

---

### Post by nodiesop1 on 2009-06-03
I seem to have this working -- sort of.

Quick specs: Using **mythtv** with an **HVR-1250** on **Jaunty** 9.04 AMD **x64**

When I scan with **Frequency Table: Cable High** and **Modulation: Cable (QAM:256)** , I pick up some channels numbered 80 and above (Also seems to work with QAM 64).  These seem to only be the local channels, but I was hoping to see all the channels from my cable provider.  I'm wondering if I rescan after June 12 when the US goes digital, if I won't pick up more channels.  

I was having another probably unrelated problem with nothing happening when I clicked **Watch TV** on the frontend.  This seems to have been resolved by removing the root user's mysql password.  (After I removed the password, I uninstalled/re-installed the mythtv packages, but I think this may have been unnecessary)

Hope this helps somebody else.  I'll post more if anything significant happens after June 12.

---

### Post by Levander on 2009-08-14
I'm trying to get this HVR 1250 working now.  I just popped it in a box and installed Mythbuntu Jaunty on it.  I've got pretty much the same output for 'sudo lshw -C multimedia' as daverab does.  I check lspci too, it's also in there.

In mythtv setup, where I get to where I'm supposed to be configuring my capture cards, for "Card Type" I think you're supposed to set it "DVB DLV capture card (v3.x)".  But, when you set it to that, just down below in the "Frontend ID" field, you get "Could not get card info for card #0". 

There's only one in there, so I'm pretty sure it's card #0.

Just googling around trying to figure out if I can fix this.

---

### Post by NTolerance on 2009-08-15
> **Levander said:**
> I'm trying to get this HVR 1250 working now.  I just popped it in a box and installed Mythbuntu Jaunty on it.  I've got pretty much the same output for 'sudo lshw -C multimedia' as daverab does.  I check lspci too, it's also in there.

In mythtv setup, where I get to where I'm supposed to be configuring my capture cards, for "Card Type" I think you're supposed to set it "DVB DLV capture card (v3.x)".  But, when you set it to that, just down below in the "Frontend ID" field, you get "Could not get card info for card #0". 

There's only one in there, so I'm pretty sure it's card #0.

Just googling around trying to figure out if I can fix this.

Can you paste the output of this command please?

```
lspci | grep Conexant

```

---

### Post by Levander on 2009-08-15
Hey, funny you replied.  I already found your thread where you had the same problem I did and fixed it:  [Here]("http://ubuntuforums.org/showthread.php?t=1234274")

It was the same thing. I had bought a newer version of the card than the v4l drivers in Jaunty are for, so had to download and compile v4l drivers, like you said...

Thanks for having posted that.  I'm sure it saved me quite a bit of time in having to figure it out myself!

Thing is, now that I got the card working, Googling around for info on how to fix it, I started reading about how aggressive Comcast is getting about blocking QAM channels.  Tomorrow I have to research solutions for the best way to tie a Comcast set-top-box to my Myth box.  I may have to return the damn thing!

---

### Post by NTolerance on 2009-08-15
> **Levander said:**
> Hey, funny you replied.  I already found your thread where you had the same problem I did and fixed it:  [Here]("http://ubuntuforums.org/showthread.php?t=1234274")

It was the same thing. I had bought a newer version of the card than the v4l drivers in Jaunty are for, so had to download and compile v4l drivers, like you said...

Thanks for having posted that.  I'm sure it saved me quite a bit of time in having to figure it out myself!

Thing is, now that I got the card working, Googling around for info on how to fix it, I started reading about how aggressive Comcast is getting about blocking QAM channels.  Tomorrow I have to research solutions for the best way to tie a Comcast set-top-box to my Myth box.  I may have to return the damn thing!

AFAIK the only way to get HD content from a set-top box is to have some sort of component input on your PC or maybe a firewire connection.  I could be wrong.  

If Comcast is anything like Time-Warner cable, all the HD channels are compressed at a disgusting rate.  You may want to look into getting a good antenna and picking up some ATSC channels.  

Look [here](http://www.silicondust.com/hdhomerun/channels) to see which QAM and ATSC channels are available in your area.

---

