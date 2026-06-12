---
title: "AMD64-Generic or AMD64-K8 Kernel?"
date: 2005-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by merc on 2005-01-07
The AMD64 Wiki for Debian says to use the K8 kernel if you have an AMD Athlon 64 cpu. And when I did a net install of Debian for AMD64, indeed it installed the k8 kernel. Then I tried Ubuntu, liked it better, and decided to keep it. But I notice that the kernel installed is the 'generic' type, not the 'k8'.

Should I go ahead and install the k8 kernel that Synaptic says I can get? Or just leave it with the generic one?

---

### Post by Dylanby on 2005-01-07
The k8 kernel should give better performance.

May be coincidental but when I went from generic to k8 some hotplug issues went away.

---

### Post by tweek! on 2005-01-12
When I upgraded, I booted into a gnome desktop with an empty panel and no right click menu... Any ideas why?

---

### Post by Gataca on 2005-01-13
I got the same problem. Here is the procedure I used to solve it.
Note : it worked for me but may be it's stroke of luke.

1. to enter in console mode on TTY1
    ```
Ctrl-Alt F1
```
2. To get rid of the gnome panel package (sudo to enter in 'root mode') 
    ```
sudo apt-get remove gnome-panel (answer 'yes' when confirmation asked)
```
3. To reinstall the gnome panel package
    ```
sudo apt-get install gnome-panel gnome-applets
```
4. To restart the gnome display manager (GDM)
    ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm stop
```
5. It should work again  :D 
6. restart the PC

Let me know if this help

Gataca

---

### Post by Gataca on 2005-01-13
At point 4, you should read :
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

Sorry  :oops: 

Gataca

---

### Post by jdong on 2005-01-13
err, **restart**?

But I guess if you LIKE all that typing, knock yourself out.

---

### Post by tweek! on 2005-01-14
Okay -  I'm stuck in a loop now... Here's what I did...

- Clean install of warty
- Upgrade to hoary
*- dpkg-reconfigure xserver-xorg, set up resolution etc
- Upgraded kernel to 2.6.10-1-amd64-k8
- Resolution went to 640x480, no panel menu
- Ctrl + Alt + F1
- sudo apt-get remove gnome-panel
- sudo apt-get install gnome-panel gnome applets
- sudo /etc/init.d/gdm restart
- booted into x, looked fine
- restarted, display all wonky (goto *)

Basically I'm either reinstalling gnome or tweaking my xorg... I either have menus at 640x480, or no menus at the correct resolution.... any ideas?

---

### Post by oracledarren on 2005-01-25
Hi

I cheated :)

get yourself a livecd iso of kanotix and boot from it and enter the following in your boot option - obviously replace the x y bits etc

xmodule=YOURGRAPHICSCARD (MINE IS SIS) screen=x,y vsync=z (z is your monitor frequency)

Then once booted copy the Xfree86-4 file from the /etc/X11 folder to a floppy.

Once you then boot into ubuntu copy the file to the same location and reboot.

When you finally get into gdm it might says to file doesnt match or something and which settings do you want to use X or Gnome so just select gnome and after that it will work as normal everytime :)

Hope this helps

Darren

---

