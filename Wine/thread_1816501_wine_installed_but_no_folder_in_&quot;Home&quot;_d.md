---
title: "wine installed but no folder in &quot;Home&quot; directory."
date: 2011-08-02
forum: Wine
---

### Post by subehsharma on 2011-08-02
I had a problem uninstalling wine so i manually deleted the folder (.wine) from home directory and removed wine entry from main menu. I'm using ubuntu 10.10

now i've tried re-installing wine 4-5 times, rebooted the laptop after installing it but still i dont see any .wine folder in home directory and no wine in main menu. could somebody please help?

---

### Post by subehsharma on 2011-08-02
Tried doing this but no changes:

Places>Home Folder>Ctrl+H>.config>menus>applications.menu

<Menu>
<Name>wine-wine</Name>
<Deleted/>
</Menu>

Remove the <Deleted/> and save the document.

---

### Post by Elfy on 2011-08-02
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

[https://help.ubuntu.com/community/Wine#Initial%20Setup](https://help.ubuntu.com/community/Wine#Initial%20Setup)

moved to wine

---

### Post by subehsharma on 2011-08-02
Thanks. I've already ran wincfg and it does bring up the wine configuration window but still i don't see any menu entry.

---

### Post by akoskm on 2011-08-02
> **subehsharma said:**
> Thanks. I've already ran wincfg and it does bring up the wine configuration window but still i don't see any menu entry.

Try with
```

sudo dpkg-reconfigure wine

```
.

---

### Post by lkraemer on 2011-08-02
After you install wine, you need to open a Terminal Window (Console) and
run the following:
```

winecfg

```

Once winecfg runs, the .wine subdirectory is created and you may exit.

Then go to PLACES -> HOME and type CNTL H (CONTROL held Depressed plus H)
and you will see a subdirectory named .wine

CNTL H toggles the view for ALL Hidden (.allhiddensubdirectories) subdirectories ""ON" then "OFF".

Zit Zot......Done!


lk

---

### Post by subehsharma on 2011-08-02
> **lkraemer said:**
> After you install wine, you need to open a Terminal Window (Console) and
run the following:
```

winecfg

```

Once winecfg runs, the .wine subdirectory is created and you may exit.

Then go to PLACES -> HOME and type CNTL H (CONTROL held Depressed plus H)
and you will see a subdirectory named .wine

CNTL H toggles the view for ALL Hidden (.allhiddensubdirectories) subdirectories ""ON" then "OFF".

Zit Zot......Done!


lk

already done that. It does bring the .wine folder but no menu entry :(

---

### Post by 3rdalbum on 2011-08-02
Doesn't the Wine menu entry only appear after you've installed a program in Wine?

---

### Post by subehsharma on 2011-08-02
> **akoskm said:**
> Try with
```

sudo dpkg-reconfigure wine

```
.



strange output i get:

subsharm@subsharm:~$ sudo dpkg-reconfigure wine
/usr/sbin/dpkg-reconfigure: wine is not installed

i removed wine and re-installed it from synaptic, still same output.

---

### Post by subehsharma on 2011-08-02
> **3rdalbum said:**
> Doesn't the Wine menu entry only appear after you've installed a program in Wine?

Sadly,no!

---

### Post by UnnamedUzer on 2011-08-02
> **subehsharma said:**
> Sadly,no!

Try CTRL + H in HOME directory .. mb it will appear)

---

### Post by subehsharma on 2011-08-02
subsharm@subsharm:~$ winecfg
wine: created the configuration directory '/home/subsharm/.wine'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0x8fee90c, overlapped 0x8fee8f0): stub
wine: configuration in '/home/subsharm/.wine' has been updated.
subsharm@subsharm:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



Strangely it can't find wine that it just installed!!!

---

### Post by akoskm on 2011-08-02
> **subehsharma said:**
> strange output i get:

subsharm@subsharm:~$ sudo dpkg-reconfigure wine
/usr/sbin/dpkg-reconfigure: wine is not installed

i removed wine and re-installed it from synaptic, still same output.

Your wine definitely isn't installed, that could answer why there is no ~/.wine directory, anyway could you
```

apt-get update
apt-get check

```
then paste the output of:
```

dpkg-query -s wine

```.

---

### Post by subehsharma on 2011-08-02
> **akoskm said:**
> Your wine definitely isn't installed, that could answer why there is no ~/.wine directory, anyway could you
```

apt-get update
apt-get check

```
then paste the output of:
```

dpkg-query -s wine

```.

After i ran winecfg, .wine folder has come up in the home folder but the problem here is that the wine entry is not there in main menu.

---

### Post by subehsharma on 2011-08-02
> **akoskm said:**
> Your wine definitely isn't installed, that could answer why there is no ~/.wine directory, anyway could you
```

apt-get update
apt-get check

```
then paste the output of:
```

dpkg-query -s wine

```.

subsharm@subsharm:~$ winecfg
wine: created the configuration directory '/home/subsharm/.wine'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0x8fee90c, overlapped 0x8fee8f0): stub
wine: configuration in '/home/subsharm/.wine' has been updated.
subsharm@subsharm:~$ sudo su
root@subsharm:/home/subsharm# winecfg
root@subsharm:/home/subsharm# apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@subsharm:/home/subsharm# dpkg-query -s wine
Package: wine
Status: unknown ok not-installed
Priority: extra
Section: otherosfs
root@subsharm:/home/subsharm#

---

### Post by Elfy on 2011-08-02
Have you tried editing the menu and seeing if it just needs to be 'ticked' 

You made mention in post#2 of deleting the entry.

Assuming you not to be using 11.04 - right click the menu and then it'll start alacarte. If you are using unity then I'm afraid I have no idea.

Also - why are you running winecfg as root?

---

### Post by subehsharma on 2011-08-02
> **forestpiskie said:**
> Have you tried editing the menu and seeing if it just needs to be 'ticked' 

You made mention in post#2 of deleting the entry.

Assuming you not to be using 11.04 - right click the menu and then it'll start alacarte. If you are using unity then I'm afraid I have no idea.

Also - why are you running winecfg as root?


Umm..problem is solved. I needed to "tick" the wine entry on main menu. I don't know why this has happened as i've been using ubuntu for 5 years and this is the first time i've seen this problem

Anyways, thanks alot everyone for providing your suggestions! :)

---

