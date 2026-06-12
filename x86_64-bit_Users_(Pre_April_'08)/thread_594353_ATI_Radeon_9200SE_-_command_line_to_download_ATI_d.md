---
title: "ATI Radeon 9200SE - command line to download ATI driver"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by gimmy_bond on 2007-10-27
My desktop freezes just after few minuets of play. I saw an ATI drive on the ubuntu repository. Unfortunately the system freezes before the download and installation is complete. 
What is the correct command command line. ?
(I tried sudo apt-get install ATI. it gives me an error message.)

thanks

---

### Post by amadeus266 on 2007-10-28
You shouldn't need a proprietary driver for that card. The one supplied by Ubuntu IS the latest one that supports your card. I have an ATI AIW 9200 myself. Most of compiz-fusion works well on my system.

---

### Post by gimmy_bond on 2007-10-28
unfortunately my screen still freezes after few moments of display.  Perhaps downloading the ATI driver could help.

If someone will write the command line for me I would appreciate it. At least its worth the try.

---

### Post by Yellow Pasque on 2007-10-28
Try:
```
sudo apt-get install xorg-driver-fglrx
```

After that installs, do:
```
sudo aticonfig --initial -f
```

---

### Post by aefaradien on 2007-12-18
thanks for the CLI install command - exactly what i needed!

---

### Post by dramek on 2007-12-20
If you want the proprietary drivers for ATI, or Nvidia, you can use a program called envy.  

To install. 
```
sudo apt-get envy
```

It works via command line so you can easily use it to install it on a system where X doesn't load.  It will download the driver, install and configure it and prompt you for reboot.  to use just type

```
sudo envy
```

---

### Post by esteckis on 2008-01-04
ATI has released a new driver dated 12/20.

There is also another post to install the ATI driver,
Envy site [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

1/3/08 The NEW Envy program installed the new ATI dated 12/20/07 driver and special effects and compiz both work. The only thing with the new ATI driver for me is the screen slightly flickers when the screen saver is running. Out of 12 times of trying to get the ATI installed, special effects to take and Compiz working, this NEW ENVY version worked for me.

ATI 1250 series onboard video using UBUNTU Gutsy 64 bit version

---

### Post by neno1984 on 2008-04-10
thanks very much

---

### Post by Yellow Pasque on 2008-04-10
wget is another useful program when you have internet working, but you're stuck in the terminal.

For example, to get the latest ATI driver (Catalyst 8.3):
```
wget --no-check-certificate https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-3-x86.x86_64.run

```

---

