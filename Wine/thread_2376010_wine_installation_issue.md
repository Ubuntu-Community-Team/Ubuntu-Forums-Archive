---
title: "wine installation issue"
date: 2017-10-29
forum: Wine
---

### Post by garong on 2017-10-29
[IMG]http://i65.tinypic.com/2jcha43.png[/IMG]


why i can not install bitvise client application
I've tried wine to winehq,
Please help.
I am using ubuntu 16.04

---

### Post by Kirboosy on 2017-11-01
Hi Garong. I'm not sure why you are wanting to install Bitvise on Ubuntu with Wine. Linux has native SSH support which can be used in the terminal.

```
ssh <username>@<IPaddress>
```

If you want a GUI so you can store all the different SSH servers you connect to there is a port of PuTTY SSH Client in the Ubuntu repositories!
```
sudo apt install putty
```

Caboose

---

### Post by Kirboosy on 2017-11-01
If you insist on installing Bitvise you can install it with the following.

```
sudo apt install wine
```
```
winecfg
```
Add the installer program under the applications. For Windows Version choose Windows XP. Click "Apply" and then "OK". After that in your terminal run the following
```
wine <pathToInstaller>/BvSshClient-Inst.exe
```

After Bitvise is installed it should automatically launch. It can also be found under your Dash as well.

Caboose

---

