---
title: "Installing wine"
date: 2013-07-31
forum: Wine
---

### Post by poncho2 on 2013-07-31
Howdy all, i'm having a little difficulty installing wine.


In Terminal
sudo add-apt-repository ppa:ubuntu-wine/ppa

You are about to add the following PPA to your system:
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpna1t60/secring.gpg' created
gpg: keyring `/tmp/tmpna1t60/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpna1t60/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK




From wine webpage
Installing Wine:
Once you have added the WineHQ PPA Repository, you are ready to install.
To get the most recent Wine 1.5 beta, click this link to install the wine1.5 package.
To install the older, stable Wine 1.4 version, click this link to install the wine1.4 package.

The address wasn't understood
       Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program.
  You might need to install other software to open this address.

from synaptic package manager

wine1.4-i386

E: /var/cache/apt/archives/linux-image-extra-3.5.0-37-generic_3.5.0-37.58_i386.deb: cannot copy extracted data for './lib/modules/3.5.0-37-generic/kernel/drivers/hid/hid-microsoft.ko' to '/lib/modules/3.5.0-37-generic/kernel/drivers/hid/hid-microsoft.ko.dpkg-new': unexpected end of file or stream
E: /var/cache/apt/archives/linux-headers-3.5.0-32_3.5.0-32.53_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2

wine1.5-i386
E: /var/cache/apt/archives/linux-image-extra-3.5.0-37-generic_3.5.0-37.58_i386.deb: cannot copy extracted data for './lib/modules/3.5.0-37-generic/kernel/drivers/hid/hid-microsoft.ko' to '/lib/modules/3.5.0-37-generic/kernel/drivers/hid/hid-microsoft.ko.dpkg-new': unexpected end of file or stream
E: /var/cache/apt/archives/linux-headers-3.5.0-32_3.5.0-32.53_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2


Any ideas?

---

### Post by kostkon on 2013-07-31
Maybe try
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install wine1.6
```

---

### Post by poncho2 on 2013-07-31
cheers, ill try that

Hmm.
thepope@thepope-Veriton-3900Pro:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
thepope@thepope-Veriton-3900Pro:~$


*ha, i had synaptic open..... beginning process again
thepope@thepope-Veriton-3900Pro:~$ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.5.0-32-generic : Depends: linux-headers-3.5.0-32 but it is not going to be installed
 linux-image-generic : Depends: linux-image-extra-3.5.0-37-generic but it is not going to be installed
 wine1.6 : Depends: wine1.6-i386 (= 1.6-0ubuntu1~ppa1) but it is not going to be installed
           Conflicts: wine1.4 but 1.4.1-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
thepope@thepope-Veriton-3900Pro:~$

---

### Post by poncho2 on 2013-07-31
Not sure what's happened now...

thepope@thepope-Veriton-3900Pro:~$ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.5.0-32-generic : Depends: linux-headers-3.5.0-32 but it is not going to be installed
 linux-image-generic : Depends: linux-image-extra-3.5.0-37-generic but it is not going to be installed
 wine1.6 : Depends: wine1.6-i386 (= 1.6-0ubuntu1~ppa1) but it is not going to be installed
           Conflicts: wine1.4 but 1.4.1-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
thepope@thepope-Veriton-3900Pro:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libreadline5 linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.5.0-32 linux-image-extra-3.5.0-37-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-32 linux-image-extra-3.5.0-37-generic
0 upgraded, 2 newly installed, 0 to remove and 17 not upgraded.
3 not fully installed or removed.
Need to get 39.6 MB of archives.
After this operation, 149 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-image-extra-3.5.0-37-generic i386 3.5.0-37.58 [27.5 MB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-headers-3.5.0-32 all 3.5.0-32.53 [12.1 MB]
Fetched 39.6 MB in 3min 20s (197 kB/s)                                         
(Reading database ... 145120 files and directories currently installed.)
Unpacking linux-image-extra-3.5.0-37-generic (from .../linux-image-extra-3.5.0-37-generic_3.5.0-37.58_i386.deb) ...
Unpacking linux-headers-3.5.0-32 (from .../linux-headers-3.5.0-32_3.5.0-32.53_all.deb) ...
Setting up linux-image-extra-3.5.0-37-generic (3.5.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (3.5.0.37.53) ...
Setting up linux-generic (3.5.0.37.53) ...
Setting up linux-headers-3.5.0-32 (3.5.0-32.53) ...
Setting up linux-headers-3.5.0-32-generic (3.5.0-32.53) ...
thepope@thepope-Veriton-3900Pro:~$

---

### Post by poncho2 on 2013-07-31
Im usung Lubuntu by the way

---

### Post by GwL3eNC on 2013-07-31
Hi poncho2,

i thing it's all good now.

sudo apt-get install wine1.6 

tolds you to try apt-get -f install so solve the dependencies. You have done that right!
Because of the installed packages linux-headers-3.5.0-32 linux-image-extra-3.5.0-37-generic
the output shows:

Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (3.5.0.37.53) ...
Setting up linux-generic (3.5.0.37.53) ...
Setting up linux-headers-3.5.0-32 (3.5.0-32.53) ...
Setting up linux-headers-3.5.0-32-generic (3.5.0-32.53) ...

Thats normal in case of update.

Now you can do the sudo apt-get autoremove to remove all packages not needed.

---

### Post by poncho2 on 2013-07-31
hmm, so i can install it now?

thepope@thepope-Veriton-3900Pro:~$ sudo apt-get autoremove
[sudo] password for thepope: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libreadline5 linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
0 upgraded, 0 newly installed, 3 to remove and 17 not upgraded.
After this operation, 70.2 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162997 files and directories currently installed.)
Removing libreadline5:i386 ...
Removing linux-headers-3.5.0-17-generic ...
Removing linux-headers-3.5.0-17 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
thepope@thepope-Veriton-3900Pro:~$

---

### Post by GwL3eNC on 2013-07-31
Yo, it should be installed. 

With the 

sudo add-apt-repository ppa:ubuntu-wine/ppa 

you added the wine repository from which ubuntu downloads the application.
Normally in the next step you ask about updates to get the newest version. 
Its the

sudo apt-get update.

After that you install the application with

sudo apt-get install wine1.6.

But you got dependencies and solved that with

sudo apt-get -f install.

Try now sudo apt-get install wine1.6  

again. It should be installed.
Start ist from the Menu or enter wine in the terminal to start the emulator.

---

### Post by poncho2 on 2013-07-31
Well i'll be... it worked!
Thanks heaps  [**[COLOR=#000000]GwL3eNC[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841512")

Nice clear explination too. I think i might have been doing some things in the wrong order at least one point.

Wine is excellent!

---

### Post by Anders J on 2013-08-01
I am mpst eager to try wine 1.6, but it seems difficult to install, tried everything listed above

> sudo add-apt-repository ppa:ubuntu-wine/ppa

only results in

> $: command not found

---

### Post by CatKiller on 2013-08-01
The command should be ```
sudo apt-add-repository …
```

---

### Post by Anders J on 2013-08-02
Nope:

$ sudo apt-add-repository ppa:ubuntu-wine/ppa
$: command not found

---

### Post by CatKiller on 2013-08-02
> **Anders J said:**
> Nope:

$ sudo apt-add-repository ppa:ubuntu-wine/ppa
$: command not found

It's provided by software-properties-common, which is installed by default.

---

### Post by Anders J on 2013-08-03
My the Force be with me then, so that "command not found" dissolves... Eventually, the repositories will be updated one day and then I can try Wine 1.6.

---

### Post by GwL3eNC on 2013-08-04
Hi Anders J,

sorry for the command error in a thread above. I think there is another problem preventig you installation.
Can you add any another repositories? Please try, because

sudo apt-add-repository ppa:ubuntu-wine/ppa

must work!! I've tried it.

---

### Post by Anders J on 2013-08-05
So have I!

---

### Post by GwL3eNC on 2013-08-05
Dear Anders J,

please what do you have? Hopefully you want to tell me, that you now succesful installed wine1.6.
I dont know if i understand that right. If you can't add any other repositorie then i think there is something
broken at the apt command apt-add-repository. Is it even there?

which apt-add-repository 

My the Force be with you!

---

### Post by Haroon_Gilani on 2013-08-05
Try rebooting or reinstalling ubuntu on ur pc if the probel persists 


If not go to higher mods

---

### Post by Doomspark on 2013-08-06
I did a google search for "sudo add-apt-repository command not found" and got one hit:

[http://linuxg.net/how-to-fix-error-sudo-add-apt-repository-command-not-found/](http://linuxg.net/how-to-fix-error-sudo-add-apt-repository-command-not-found/)

---

