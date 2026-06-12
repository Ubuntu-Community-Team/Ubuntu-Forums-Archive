---
title: "Nvidia Problem"
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by SlashX1896 on 2008-06-01
Ok i searched around for help on this problem and found nothing that helped me.

i installed drivers manually and tried using Envy to install the drivers.
The drivers install with no problem, but then my resolution goes from 1024x768 to like 640x* and everything is huge, and its hard to do a lot of things. and i have no ability to change it back to 1024x768 unless i uninstall the drivers.
im new with linux, so please spare me lol. been with windows for the past like 8 years.
if it helps i have a geforce 8800GT

---

### Post by lamborghiniwang on 2008-06-01
I have similar problem with the 169.12 driver. The native resolution of my LCD is 1400x1050, which I can select in the nvidia-settings, but I can not see the 1024x768 or 800x600 resolutions. In my case, the bug has something to do with the 169.12 driver which is said to have "a regression that caused invalid EDIDs to be detected for the internal display device on some notebooks.".

  I suggest you follow the [instruction]("http://www.nvnews.net/vbulletin/showthread.php?t=46678") to generate the ***nvidia-bug-report.log*** file and see if it is the reason.

  PS: It is said that the new 173.141.05 driver has fixed this bug, however it seems EnvyNG has not included this new driver yet, so you will have to wait unless you want to install the nvidia driver manually.

---

### Post by SlashX1896 on 2008-06-01
Ive tried installing the drivers manually. and it didnt solve my resolution problem

im completely new with linux/ubuntu so im assuming i did something wrong. at the moment so my resolution is good i have no drivers installed.

also i tryed doing ctrl alt f1, and installing the drivers downloaded to my desktop using sudo sh.

and it says "Sh can not open this file"

---

### Post by Cappy on 2008-06-01
When you have the proprietary nvidia drivers installed use
```
gksudo nvidia-settings
```
and you can change your resolution and then click "Save to X Conf" (or something like that) at the bottom right.

---

### Post by SlashX1896 on 2008-06-01
i tryed that, and theres only 2 options 640x480 and 320x240
both wya to big for me.

how do i add more resolutions?

ctrl alt f1 isnt even working for me.. nothing happens and when in terminal  it just does ;7P

---

### Post by athaki on 2008-06-01
I have an 8400GS Nvidia card and I just downloaded the drivers using the renamed restricted drivers manager in system > settings (I think). I'm not at my Ubuntu box right now but you could try that if you haven't already. I hope I'm helpful but if I'm not I'm becoming quite the pest to people.

---

### Post by lamborghiniwang on 2008-06-02
> **SlashX1896 said:**
> 
ctrl alt f1 isnt even working for me.. nothing happens and when in terminal  it just does ;7P

For the Ctrl-Alt-F1 issue, have you tried to add the option "vga=xxx" into your kernel boot line? (modify the file /boot/grub/menu.lst, and add vga=xxx to the end of the line that starts with "kernel".the value of xxx depends on your monitor, but usually vga=791 would set a resolution of 1024x768 for the command line mode)
Here is the example:
```

...
title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.24-17-generic root=UUID=716b71e8-f52a-432d-b54e-0c62fb382bee ro vga=791
initrd          /initrd.img-2.6.24-17-generic
quiet
...

```

---

### Post by SlashX1896 on 2008-06-02
im not on my box right now so il give that a try.


and lamborghiniwang il try that, but idk exactly how to

remember i just installed ubuntu for the first time on saturday.

---

### Post by lamborghiniwang on 2008-06-02
> **SlashX1896 said:**
> im not on my box right now so il give that a try.


and lamborghiniwang il try that, but idk exactly how to

remember i just installed ubuntu for the first time on saturday.

It is easy:
boot your computer, if you see the GRUB menu that allows you to use up and down keys to select kernel options, you may skip the following step 1:
1) On start-up, when you see the text "GRUB Loading stage 1.5. GRUB loading, please wait..., Press 'ESC' to enter the menu.." followed by a number that is counting down: press the ESC key
2) Now you should be in the GRUB menu where you can select different boot options using up and down keys. The line says "Ubuntu 8.04, kernel 2.6.24-16-generic" should be highlighted by default(if it is not, use up/down key so that it is highlighted).
3) Press the key 'E' so that you can edit this boot option, this will bring you into another screen which looks like the following 
```

root            (hd0,1)
kernel          /vmlinuz-2.6.24-17-generic root=UUID=716b71e8-f52a-432d-b54e-0c62fb382bee ro quite splash
initrd          /initrd.img-2.6.24-17-generic
quiet

```
4) Again use the up/down key so that the second line (the one starts with "kernel") is highlighted, press 'E' again to edit this line
5) Press the 'End' key on your keyboard so that you move the cursor to the end of this line, and type in ' vga=791' (so the end of this line should reads something like "splash vga=791"). Press RETURN key. It will bring you back to the previous screen where you see other lines like "root (hd0,0)" etc
6) press 'B' to boot with this kernel option. You will start to see the Ubuntu splash screen.


The steps described above only affect the current boot session, which means that it will be lost after reboot, so if the value 791 doesn't work on your machine or you later find a better option value for your monitor, you may change it during your future reboot. But if you want GRUB to remember this option, you may edit the file /boot/grub/menu.lst by click Alt-F2 key and type in
```

sksu gedit /boot/grub/menu.lst

```
and add the option vga=xxx permanently.

PS: One way to find the value of xxx that fits your monitor is to run in terminal:
```

sudo apt-get install hwinfo
sudo hwinfo --framebuffer

```
This will show you different mode that with the corresponding HEX vga value. In my case, my LCD supports maximum resolution of 1400x1050, one line in my hwinfo output reads:
```

  Mode 0x0349: 1400x1050 (+5600), 24 bits

```
Here the HEX value is 0x0349 (=841), so my kernel has the boot option "vga=841".

---

### Post by Cappy on 2008-06-02
> **SlashX1896 said:**
> i tryed that, and theres only 2 options 640x480 and 320x240
both wya to big for me.

how do i add more resolutions?


I just bought a new monitor today and did this:

I went to System --> Administration --> Screens and Graphics

In "Model" my 22" screen wasn't available in the list so I just went to generic and clicked "LCD Panel 1680x1050"

I clicked "Okay".

I did Alt+Control+Backspace to restart X.

Then I used ```
gksudo nvidia-settings
``` and selected my correct refresh rate and resolution.

---

