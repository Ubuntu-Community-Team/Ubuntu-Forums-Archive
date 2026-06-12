---
title: "slow graphics on a strong machine"
date: 2005-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by timboo on 2005-03-18
Hello.
I have a problem with graphics, movies in particular, playing under fullscreen mode.

I have a Gateway 7422, 1gb ram, amd64 mobile 2200+ and a  ATI mobility 9550 card.

I tried running a divx coded movie on the mplayer package from multiverse, and in the small window mode it works really well. sound, graphics, everything. when i go into fullscreen the system becomes really slow and the movie plays slow.

i read in some forums to install the newest ati drivers, which i did. still the system plays slow.

from my feelings this shouldn't happen on a computer with the above specifications. but i don't know where to start looking for a solution. do i need to load the ati drivers specifically? anything else? any idea what could cause this?

every help will be appreciated. thank you.

---

### Post by Nadir on 2005-03-18
[QUOTE=timboo] 
I tried running a divx coded movie on the mplayer package from multiverse, and in the small window mode it works really well. sound, graphics, everything. when i go into fullscreen the system becomes really slow and the movie plays slow.
[/QUOTE]

Run xvinfo and post the ouput here.

Tristan

---

### Post by timboo on 2005-03-18
Hello,

here is the output of xvinfo in my machine:

X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 61
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 15
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 30)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
    "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SWITCHCRT" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GAMMA" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_COLORSPACE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
       guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)

---

### Post by timboo on 2005-03-18
sorry. even though i installed the fglrx driver, the module isn't running and the xorg.conf isn't properly configured. that's the problem. sorry for making a fuss about this before. i'll try to get the modules working now.

---

### Post by wmcbrine on 2005-03-18
Also make sure that MPlayer is using a sensible -vo. When I installed it from the Ubuntu package, it defaulted to x11, the worst choice (though, I suppose, the most broadly compatible). Someone had set it that way in /etc/mplayer/mplayer.conf. I changed this to xv, and MPlayer performs as expected.

I also turned on DMA for my DVD drive and multiple-sector reads for my hard disk for better video (and all-around) performance; these are set in /etc/hdparm.conf, but the DVD drive isn't available at the time the script runs, so you have to make another link in /etc/rcS.d -- I did "cp S07hdparm S99hdparm".

BTW, I'm using Hoary... unfortunately this forum has been moved to the Warty section, but I'm guessing this applies to either one.

---

