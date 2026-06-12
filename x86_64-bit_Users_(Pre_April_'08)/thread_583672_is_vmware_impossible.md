---
title: "is vmware impossible?"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-20
How is it possible to run VMware Server in Ubuntu 7.10?

---

### Post by ryanVickers on 2007-10-20
no - it won't run on anything - try VirtualBox! ;)

---

### Post by go_beep_yourself on 2007-10-20
virtual box = virtual crap. it has no networking and gives more errors than ive seen in a lifetime.

---

### Post by ryanVickers on 2007-10-20
It has worked perfectly with beautiful networking and sharing, no errors, saved sessions, and it renders 3D just as fast as 'real' windows. VMware  on the other hand has trouble moving a window or scrolling at even close to 10% of normal speed!

---

### Post by go_beep_yourself on 2007-10-20
I'm trying VBox again. What should these settings be?

---

### Post by mb0108 on 2007-10-20
I have VMWare Workstation and Player running perfectly on my Gutsy. 

Michael

---

### Post by FredB on 2007-10-20
> **go_beep_yourself said:**
> I don't believe FreeDOS is going to run any nicer than Minix 3 or RHLE5 in Virtualbox, so let me ask my original question again.

Is it impossible to run VMware in Ubuntu 7.10 64 bit.

So, explain me how I am using right now a VMWare - workstation but the start is the same - in my Gutsy AMD64 :)

[LIST=1]
[*]Just grab last vmware server / workstation from vmware website.
[*]Install linux headers matching your kernel version, xinetd and build-essential
[*]unpack the software
[*]run sudo ./vmware-install.pl
[*]follow the guid[/LIST]

---

### Post by masingerz on 2007-10-20
I got my vmware player running on gutsy 7.10

Downloaded vmware player 2.02 from the vmware website:
[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

then Ï installed using this manual
[http://www.vmware.com/pdf/vmware_player200.pdf](http://www.vmware.com/pdf/vmware_player200.pdf)

I had some existent vmx files from the past when I had feisty, I had downloaded those from:

[http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by go_beep_yourself on 2007-10-20
I've got it working now. Thanks. I thought I would need a 64 bit version of vmware, but I was wrong.

---

### Post by FredB on 2007-10-21
> **go_beep_yourself said:**
> I've got it working now. Thanks. I thought I would need a 64 bit version of vmware, but I was wrong.

There is a 64 bit version of both player and workstation... And it works great ;)

---

### Post by Macinux on 2007-10-21
VMware server doesn't run in 7.10? hmm, I guess I'll remove it then... no wait, the latest VMware Server installed perfectly on my system, Ubuntu 7.10 amd64. Once it was installed I setup a new server and installed Windows XP Pro, that installed without one error. After that was installed I set to full screen mode, set resolution to 1280x800 and installed my trial CD of Microsoft Office 2007 (I just installed Powerpoint, Word, and Excel). It took a little longer to install than normal but it installed without a hitch none-the-less.

I'm running a MacBook Core 2 Duo, 2gb ram, 160gb HD, 1.8ghz (white). I'm so very pleased with Ubuntu, to go from 7.04 running for 1 day then to upgrade an entire OS (7.10) and not have an issue is just remarkable.

---

### Post by go_beep_yourself on 2007-10-21
> **Macinux said:**
> VMware server doesn't run in 7.10? hmm, I guess I'll remove it then... no wait, the latest VMware Server installed perfectly on my system, Ubuntu 7.10 amd64. Once it was installed I setup a new server and installed Windows XP Pro, that installed without one error. After that was installed I set to full screen mode, set resolution to 1280x800 and installed my trial CD of Microsoft Office 2007 (I just installed Powerpoint, Word, and Excel). It took a little longer to install than normal but it installed without a hitch none-the-less.

I'm running a MacBook Core 2 Duo, 2gb ram, 160gb HD, 1.8ghz (white). I'm so very pleased with Ubuntu, to go from 7.04 running for 1 day then to upgrade an entire OS (7.10) and not have an issue is just remarkable.

You installed Winblows Xp professional? You could have installed Viruses, Infections, Spyware, Trojans, and Adware (VISTA) instead. Why don't you install something worthy of disk space such as Minix 3 or Plan 9?

---

### Post by fjgaude on 2007-10-21
> **go_beep_yourself said:**
> I've got it working now. Thanks. I thought I would need a 64 bit version of vmware, but I was wrong.

You got the server working? Pray tell us how. Thanks.

---

### Post by tmcmulli on 2007-10-21
My 32-bit Gutsy works great, but getting this error on VMPlayer in 64-bit Gutsy, any ideas??

---

### Post by go_beep_yourself on 2007-10-21
> **fjgaude said:**
> You got the server working? Pray tell us how. Thanks.

Download from
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
sudo apt-get install build-essential linux-headers-`uname -r` xinetd
tar -xf vmware.tar.gz (substitute name of downloaded file)
cd vmware-server
sudo ./vmware-install.pl
Push enter most of the time for the default answers.

---

### Post by go_beep_yourself on 2007-10-21
> **tmcmulli said:**
> My 32-bit Gutsy works great, but getting this error on VMPlayer in 64-bit Gutsy, any ideas??

[http://www.google.com/search?q=%22Error+while+powering+on%3A+Failed+to+connect+to+peer+process.%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=%22Error+while+powering+on%3A+Failed+to+connect+to+peer+process.%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Macinux on 2007-10-21
> **go_beep_yourself said:**
> You installed Winblows Xp professional? You could have installed Viruses, Infections, Spyware, Trojans, and Adware (VISTA) instead. Why don't you install something worthy of disk space such as Minix 3 or Plan 9?

I needed Office 2007 for the college courses I'm taking, and I didn't want to go through the whole ordeal with setting it up under WINE if it would even work under WINE. So instead I setup a VM and loaded XP Pro and installed Office 2007.

As far as getting a virus, trojan, etc etc.. Okay so it effects the virtual machine. It still won't effect Ubuntu install, and if anything like that ever happened, like adware, etc etc. It would effect only the script config files that VMware loads the VM into, nothing else, I would remove the VM and reinstall it again. The only thing I use it for is loading Excel 2007 for my spreadsheet class now, once I'm done with the class first week of December I'm removing XP VM anyway.


But yea for those having issues, go to VMwares website and download the latest VMserver for your architecture and follow the install directions. I done that and it worked fine, and I'm a novice with Linux.

---

### Post by fjgaude on 2007-10-21
> **go_beep_yourself said:**
> Download from
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
sudo apt-get install build-essential linux-headers-`uname -r` xinetd
tar -xf vmware.tar.gz (substitute name of downloaded file)
cd vmware-server
sudo ./vmware-install.pl
Push enter most of the time for the default answers.

Thanks man, worked like a charm. All is well with 64-bit and VMware Server running guest WinXP.

---

### Post by tmcmulli on 2007-10-21
> **go_beep_yourself said:**
> [http://www.google.com/search?q=%22Error+while+powering+on%3A+Failed+to+connect+to+peer+process.%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=%22Error+while+powering+on%3A+Failed+to+connect+to+peer+process.%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Thanks for the tip, applied the patch, but the update doesn't run... blog notes that the new vmware packages shouldn't need this update...

I'll keep plugging away...

---

### Post by ltiger_hun on 2007-10-21
> **go_beep_yourself said:**
> Download from
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
sudo apt-get install build-essential linux-headers-`uname -r` xinetd
tar -xf vmware.tar.gz (substitute name of downloaded file)
cd vmware-server
sudo ./vmware-install.pl
Push enter most of the time for the default answers.

I get stuck at the vmware-config.pl script :( :

```
#sudo perl /usr/bin/vmware-config.pl
[sudo] password for tiger:
Making sure services for VMware Server are stopped.

sh: /etc/init.d/vmware: Permission denied
sh: /etc/init.d/vmware: Permission denied
Unable to stop services for VMware Server

Execution aborted.

```

---

### Post by fjgaude on 2007-10-21
> **ltiger_hun said:**
> I get stuck at the vmware-config.pl script :( :

```
#sudo perl /usr/bin/vmware-config.pl

```

You are in the vmware server directory? If you do as it was suggested, exactly, it works, at least for me.

---

### Post by caen1944 on 2007-10-23
Hi Folks,

I found this thread that fixed all my problems (with vmware server and ubuntu 7.10, i have plenty of other problems)

[http://ubuntuforums.org/showthread.php?t=337040](http://ubuntuforums.org/showthread.php?t=337040)

No problem with vmware server after this. I am using AMD64 version of ubuntu 7.10. Although I must say that the ubuntu 7.10 updater pretty much destroyed my 7.04 installation when I tried to update. It half finished then crashed, leaving a complete mess. I had to do a fresh install of 7.10. 

I'm still slowly recovering from this mess (hence the new install of vmware)

Good luck

---

### Post by bschopman on 2007-10-23
> **masingerz said:**
> I got my vmware player running on gutsy 7.10
[http://www.easyvmx.com/](http://www.easyvmx.com/)

Excellent!
Will try this today... :popcorn:

---

